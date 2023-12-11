---
toc: false
comments: false
layout: post
title: Binary Calculator
description: "A binary calculator to teach people about binary and math"
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
<<<<<<< HEAD



git pu
git
=======
>>>>>>> 44f74c8bf1dc36a14d49f3675280507598290b7a
</head>
<body>
<h1>Binary Calculator</h1>
<<<<<<< HEAD


=======
>>>>>>> 44f74c8bf1dc36a14d49f3675280507598290b7a
<form id="BinaryCalculator">
    <label for="num1">Number 1:</label>
    <input type="text" id="num1" placeholder="Enter decimal number">
    <br>
    <label for="num2">Number 2:</label>
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
    <!-- Generate number buttons from 0 to 9 for num1 -->

 <script>
        for (var i = 0; i <= 9; i++) {
            document.write("<button data-input-id='num1' onclick=\"addToInput('" + i + "')\">" + i + "</button>");
        }
    </script>
</div>
<script>
    function performOperation(operation) {
        var num1 = parseInt(document.getElementById("num1").value, 10) || 0;
        var num2 = parseInt(document.getElementById("num2").value, 10) || 0;
        var resultField = document.getElementById("result");
<<<<<<< HEAD

=======
>>>>>>> 44f74c8bf1dc36a14d49f3675280507598290b7a
        switch (operation) {
            case 'add':
                resultField.value = decimalToBinary(num1 + num2);
                break;
            case 'subtract':
<<<<<<< HEAD
                resultField.value = decimalToBinary(num1 - num2);
=======
                resultField.value = decimalToBinary(subtractWithOnesComplement(num1, num2));
>>>>>>> 44f74c8bf1dc36a14d49f3675280507598290b7a
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
<<<<<<< HEAD
        return (decimalNum >>> 0).toString(2);
    }

    function addToInput(number) {
        var activeInput = document.activeElement;

        if (activeInput.tagName === "INPUT" && activeInput.type === "text") {
            activeInput.value += number;
=======
        if (decimalNum < 0) {
            // Convert negative numbers to binary using 32 bits
            return (decimalNum >>> 0).toString(2);
        } else {
            return decimalNum.toString(2);
        }
    }
    function addToInput(number) {
        var activeElement = document.activeElement;
        if (activeElement.tagName === "INPUT" && activeElement.type === "text") {
            // If the active element is an input, append the number to its value
            activeElement.value += number;
        } else if (activeElement.tagName === "BUTTON") {
            // If the active element is a button, find the corresponding input and append the number
            var inputId = activeElement.dataset.inputId;
            var targetInput = document.getElementById(inputId);
            if (targetInput) {
                targetInput.value += number;
                targetInput.focus(); // Focus on the input
            }
>>>>>>> 44f74c8bf1dc36a14d49f3675280507598290b7a
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


//snowflake
document.addEventListener('DOMContentLoaded', function () {
    const snowflakes = [];

    function createSnowflake() {
        const diameter = Math.floor(Math.random() * 16) + 5; // Random diameter between 5px and 20px
        const speed = Math.floor(Math.random() * 20) + 10; // Random speed between 10px/sec and 30px/sec
        const positionX = Math.random() < 0.5 ? // Random position within the leftmost or rightmost 17% of the screen
            Math.floor(Math.random() * window.innerWidth * 0.17) : // Leftmost 17%
            Math.floor(Math.random() * window.innerWidth * 0.17) + (window.innerWidth * 0.83); // Rightmost 17%
        const positionY = Math.floor(Math.random() * window.innerHeight) + 1; // Random position within the window height

        const snowflake = document.createElement('div');
        snowflake.className = 'snowflake';
        snowflake.style.width = `${diameter}px`;
        snowflake.style.height = `${diameter}px`;
        snowflake.style.left = `${positionX}px`;
        snowflake.style.top = `${positionY}px`;
        document.body.appendChild(snowflake);

        snowflakes.push({
            element: snowflake,
            diameter,
            speed,
            positionX,
            positionY,
        });
    }

    function updateSnowfall() {
        for (const snowflake of snowflakes) {
            snowflake.positionY += snowflake.speed / 10;
            if (snowflake.positionY > window.innerHeight) {
                snowflake.positionY = -10;
            }
            snowflake.element.style.top = `${snowflake.positionY}px`;
        }

        requestAnimationFrame(updateSnowfall);
    }

    function initializeSnowfall() {
        for (let i = 0; i < 20; i++) {
            createSnowflake();
        }

        updateSnowfall();
    }

    initializeSnowfall();
});

  
</script>