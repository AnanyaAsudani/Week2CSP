---
toc: true
comments: false
layout: post
title: Factorial Calculator
description: My version of a factorial calculator. This portrays both an input and output.
type: hacks
courses: { compsci: {week: 3} }
---


<html>
<head>
    <title>Factorial Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }

        #calculator {
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            width: 300px;
            background-color: #f5f5f5;
            border-radius: 5px;
        }

        label {
            font-weight: bold;
        }

        input[type="number"] {
            width: 100%;
            padding: 5px;
            margin-bottom: 10px;
        }

        button {
            background-color: #007bff;
            color: #fff;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }

        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div id="calculator">
        <h1>Factorial Calculator</h1>
        <label for="number">Enter a number:</label>
        <input type="number" id="number">
        <button onclick="calculateFactorial()">Calculate Factorial</button>
        <div id="result"></div>
    </div>

    <script>
        function calculateFactorial() {
            const numberInput = document.getElementById('number');
            const resultDiv = document.getElementById('result');
            const number = parseInt(numberInput.value);

            if (isNaN(number) || number < 0) {
                resultDiv.textContent = 'Please enter a non-negative integer.';
                return;
            }

            let factorial = 1;
            for (let i = 2; i <= number; i++) {
                factorial *= i;
            }

            resultDiv.textContent = `Factorial of ${number} is: ${factorial}`;
        }
    </script>
</body>
</html>

