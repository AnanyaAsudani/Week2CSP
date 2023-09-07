---
toc: true
comments: false
layout: post
title: Calculator
description: Just a basic calculator
type: hacks
courses: { compsci: {week: 2} }
---


<html>
<head>
    <title>Calculator</title>
    <style>
        .calculator {
            width: 200px;
            border: 1px solid #ccc;
            padding: 10px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <table>
            <tr>
                <td><button onclick="appendToDisplay('7')">7</button></td>
                <td><button onclick="appendToDisplay('8')">8</button></td>
                <td><button onclick="appendToDisplay('9')">9</button></td>
                <td><button onclick="appendToDisplay('/')">/</button></td>
            </tr>
            <tr>
                <td><button onclick="appendToDisplay('4')">4</button></td>
                <td><button onclick="appendToDisplay('5')">5</button></td>
                <td><button onclick="appendToDisplay('6')">6</button></td>
                <td><button onclick="appendToDisplay('*')">*</button></td>
            </tr>
            <tr>
                <td><button onclick="appendToDisplay('1')">1</button></td>
                <td><button onclick="appendToDisplay('2')">2</button></td>
                <td><button onclick="appendToDisplay('3')">3</button></td>
                <td><button onclick="appendToDisplay('-')">-</button></td>
            </tr>
            <tr>
                <td><button onclick="appendToDisplay('0')">0</button></td>
                <td><button onclick="clearDisplay()">C</button></td>
                <td><button onclick="calculate()">=</button></td>
                <td><button onclick="appendToDisplay('+')">+</button></td>
            </tr>
        </table>
    </div>
    
    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            var expression = document.getElementById('display').value;
            var result = eval(expression);
            document.getElementById('display').value = result;
        }
    </script>
</body>
</html>


<html>
<head>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }
    
    #game {
      margin-top: 50px;
    }
  </style>
</head>
<body>
  <h1>Guess the Number Game</h1>
  <div id="game">
    <p>Guess a number between 1 and 100:</p>
    <input type="number" id="guessInput">
    <button onclick="checkGuess()">Submit</button>
    <p id="message"></p>
  </div>
  
  <script>
    const secretNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    
    function checkGuess() {
      const guessInput = document.getElementById("guessInput");
      const message = document.getElementById("message");
      const guess = parseInt(guessInput.value);
      
      if (isNaN(guess)) {
        message.textContent = "Please enter a valid number.";
        return;
      }
      
      attempts++;
      
      if (guess === secretNumber) {
        message.textContent = `Congratulations! You guessed ${secretNumber} in ${attempts} attempts.`;
        message.style.color = "green";
        guessInput.disabled = true;
      } else if (guess < secretNumber) {
        message.textContent = "Try a higher number.";
        message.style.color = "blue";
      } else {
        message.textContent = "Try a lower number.";
        message.style.color = "blue";
      }
      
      guessInput.value = "";
      guessInput.focus();
    }
  </script>
</body>
</html>>