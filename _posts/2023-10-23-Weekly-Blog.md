from flask import Blueprint, jsonify, request
import pandas as pd
import yfinance as yf
import plotly.graph_objs as go
from datetime import datetime
from flask_restful import Api, Resource
import numpy as np
from flask_cors import CORS
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers
import random

stock_api = Blueprint('stock_api', __name__, url_prefix='/api/stocks')
api = Api(stock_api)

CORS(stock_api)


def get_stock_graph(stock_name):
    end_date = datetime.now()
    start_date = end_date - pd.Timedelta(days=4856)

    df = yf.download(stock_name, start=start_date, end=end_date)

    graph = go.Figure(data=go.Candlestick(x=df.index,
                                          open=df['Open'],
                                          high=df['High'],
                                          low=df['Low'],
                                          close=df['Close'],
                                          name=stock_name))
    graph.update_layout(title=f'{stock_name} Stock Price',
                        xaxis_title='Date',
                        yaxis_title='Price')

    graph_data = graph.to_dict()
    graph_data['data'][0]['x'] = graph_data['data'][0]['x'].astype(
        str).tolist()
    graph_data['data'][0]['open'] = graph_data['data'][0]['open'].tolist()
    graph_data['data'][0]['high'] = graph_data['data'][0]['high'].tolist()
    graph_data['data'][0]['low'] = graph_data['data'][0]['low'].tolist()
    graph_data['data'][0]['close'] = graph_data['data'][0]['close'].tolist()

    return graph_data





class _ReadStockGraph(Resource):
    def get(self, stock_name):
        graph = get_stock_graph(stock_name)
        return graph


class _GetLatestStockData(Resource):
    def get(self, stock_name):
        try:

            stock = yf.Ticker(stock_name)
            latest_data = stock.history(period="1d")

            if latest_data.empty:
                return jsonify({'error': 'No data found for the provided stock ticker.'}), 404

            latest_data = latest_data[['Open', 'High', 'Low', 'Close']]
            latest_data = latest_data.rename(
                columns={'Open': 'open', 'High': 'high', 'Low': 'low', 'Close': 'close'})

            latest_data_dict = latest_data.to_dict(orient='records')[0]

            for key, value in latest_data_dict.items():
                if isinstance(value, (float, int)):
                    latest_data_dict[key] = round(value, 2)

            return jsonify(latest_data_dict)
        except Exception as e:
            return jsonify({'error': str(e)}), 500


api.add_resource(_GetLatestStockData, '/latest_data/<string:stock_name>')

api.add_resource(_ReadStockGraph, '/stock_graph/<string:stock_name>')


def train_stock_prediction_model(stock_name):
    end_date = datetime.now()
    start_date = end_date - pd.Timedelta(days=4856)

    df = yf.download(stock_name, start=start_date, end=end_date)

    # preprocess the data
    df['Close'] = df['Close'].pct_change()  # calc daily returns
    df = df.dropna()

    X = df[['Open', 'High', 'Low', 'Close']].values
    y = (df['Close'] > 0).astype(int)  # 1 if price increaseds 0 if decreased

    model = keras.Sequential([
        layers.Dense(64, activation='relu', input_shape=(4,)),
        layers.Dense(32, activation='relu'),
        layers.Dense(1, activation='sigmoid')
    ])
    model.compile(optimizer='adam', loss='binary_crossentropy',
                  etrics=['accuracy'])
    model.fit(X, y, epochs=10)

    return model


def get_stock_recommendation(stock_name, model):
    end_date = datetime.now()
    start_date = end_date - pd.Timedelta(days=1)

    df = yf.download(stock_name, start=start_date, end=end_date)

    if df.empty:
        return {'error': 'No data found for the provided stock ticker.'}, 404

    df['Close'] = df['Close'].pct_change().iloc[-1]

    X = df[['Open', 'High', 'Low', 'Close']].values
    prediction = model.predict(X)

    recommendation = 'Buy' if prediction > 0.5 else 'Don\'t Buy'
    reason = f'This is based on the current data'

    return {'recommendation': recommendation, 'reason': reason}


class _AnalyzeStock(Resource):
    def get(self, stock_name):
        try:
            model = train_stock_prediction_model(stock_name)
            recommendation = get_stock_recommendation(stock_name, model)
            return jsonify(recommendation)
        except Exception as e:
            return jsonify({'error': str(e)}), 500


api.add_resource(_AnalyzeStock, '/analyze/<string:stock_name>')