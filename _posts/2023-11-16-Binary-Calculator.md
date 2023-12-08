---
toc: false
comments: false
layout: post
title: Binary Calculator
description: "For our calculator, we aim to feature various backgrounds and themes. Leveraging SASS, we will establish a primary theme characterized by a rainbow background and calculator buttons in a shade approximating #ADD8E6. Upon activating the switch button to access the graphing calculator, the color scheme will transform into monochromatic tones, featuring a black background with the same blue buttons.We plan to develop the calculator by associating each number with its binary representation. The implementation will involve HTML and JavaScript to create the functional calculator, offering features comparable to a standard calculator. Initially, it will function as a basic four-operation calculator. However, we intend to incorporate a toggle switch that, when activated, transforms it into a graphing calculator with additional capabilities."
type: ccc
courses: { csp: {week: 13} }
---


<style>
    body {
        font-family: Arial, sans-serif;
        margin: 20px;
    }
    h1 {
        text-align: center;
    }
    form {
        max-width: 400px;
        margin: 0 auto;
    }
    label {
        display: block;
        margin-bottom: 5px;
    }
    input {
        width: 100%;
        padding: 8px;
        margin-bottom: 10px;
    }
    button {
        display: inline-block;
        padding: 10px;
        margin: 5px;
        width: 48%;
        box-sizing: border-box;
    }
    .keyboard {
        max-width: 400px;
        margin: 20px auto;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 10px;
    }
</style>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Calculator</title>
</head>
<body>
<h1>Binary Calculator</h1>
<form id="BinaryCalculator">
    <label for="num1">Decimal Number 1:</label>
    <input type="text" id="num1" placeholder="Enter decimal number">
    <br>
    <label for="num2">Decimal Number 2:</label>
    <input type="text" id="num2" placeholder="Enter decimal number">
    <br>
    <button type="button" onclick="performOperation('add')">Addition (+)</button>
    <button type="button" onclick="performOperation('subtract')">Subtraction (-)</button>
    <button type="button" onclick="performOperation('multiply')">Multiplication (*)</button>
    <button type="button" onclick="performOperation('divide')">Division (/)</button>
    <br>
    <label for="result">Result (Binary):</label>
    <input type="text" id="result" readonly>
</form>
<div class="keyboard">
    <!-- Generate number buttons from 1 to 9 -->
    <script>
        for (var i = 1; i <= 9; i++) {
            document.write("<button onclick=\"addToInput(" + i + ")\">" + i + "</button>");
        }
        document.write("<button onclick=\"addToInput(0)\">0</button>");
    </script>
</div>
<script>
    function performOperation(operation) {
        var num1 = parseInt(document.getElementById("num1").value, 10) || 0;
        var num2 = parseInt(document.getElementById("num2").value, 10) || 0;
        var resultField = document.getElementById("result");
        switch (operation) {
            case 'add':
                resultField.value = decimalToBinary(num1 + num2);
                break;
            case 'subtract':
                resultField.value = decimalToBinary(subtractWithOnesComplement(num1, num2));
                break;
            case 'multiply':
                resultField.value = decimalToBinary(num1 * num2);
                break;
            case 'divide':
                resultField.value = decimalToBinary(Math.floor(num1 / num2));
                break;
            default:
                resultField.value = "Invalid operation";
        }
    }
    function subtractWithOnesComplement(num1, num2) {
        // Calculate the ones complement of num2
        var onesComplementNum2 = ~num2;
        // Add 1 to the ones complement to get the two's complement
        var twosComplementNum2 = (onesComplementNum2 + 1) & 0xFFFFFFFF;
        // Perform addition using two's complement to get the subtraction result
        return num1 + twosComplementNum2;
    }
    function decimalToBinary(decimalNum) {
        if (decimalNum < 0) {
            // Convert negative numbers to binary using 32 bits
            return (decimalNum >>> 0).toString(2);
        } else {
            return decimalNum.toString(2);
        }
    }
    function addToInput(number) {
        var activeInput = document.activeElement;
        if (activeInput.tagName === "INPUT" && activeInput.type === "text") {
            activeInput.value += number;
        }
    }
</script>
</body>
</html>

## Number Guessing Game

Welcome to the Number Guessing Game!

I'm thinking of a number between 1 and 100. Try to guess the number.

### Rules:
- You have a maximum of 10 attempts to guess the number.
- After each guess, you'll receive hints: "Too high" or "Too low."

### How to Play:
1. Enter a number between 1 and 100 in the input field provided.
2. Submit your guess.

### Guess the Number:
<input type="text" id="userGuess" placeholder="Enter your guess...">
<button onclick="checkGuess()">Submit Guess</button>

<div id="hint"></div>

<script>
  let secretNumber = Math.floor(Math.random() * 100) + 1;
  let attempts = 0;
  const maxAttempts = 10;

  function checkGuess() {
    let userGuess = parseInt(document.getElementById('userGuess').value);
    attempts++;

    if (attempts <= maxAttempts) {
      if (userGuess === secretNumber) {
        document.getElementById('hint').innerHTML = `Congratulations! You've guessed the number ${secretNumber} in ${attempts} attempts!`;
      } else if (userGuess < secretNumber) {
        document.getElementById('hint').innerHTML = 'Too low! Try a higher number.';
      } else {
        document.getElementById('hint').innerHTML = 'Too high! Try a lower number.';
      }
    } else {
      document.getElementById('hint').innerHTML = `Sorry, you've reached the maximum number of attempts. The number was ${secretNumber}.`;
    }
  }
</script>