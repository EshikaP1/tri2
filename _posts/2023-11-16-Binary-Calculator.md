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
        <label for="num1">Base 10 Number 1:</label>
        <input type="text" id="num1" placeholder="Enter decimal number">
        <br>
        <label for="num2">Base 10 Number 2:</label>
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
        <!-- Generate number buttons from 0 to 9 for num1 and num2 -->
        <?php for ($i = 0; $i <= 9; $i++) { ?>
            <button onclick="addToInput('<?php echo $i; ?>')"><?php echo $i; ?></button>
        <?php } ?>
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
            var onesComplementNum2 = ~num2;
            var twosComplementNum2 = (onesComplementNum2 + 1) & 0xFFFFFFFF;
            return num1 + twosComplementNum2;
        }

        function decimalToBinary(decimalNum) {
            if (decimalNum < 0) {
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
            }
        }
</script>
</body>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Christmas Dots</title>
    <style>
        body, html {
            width: 100%;
            height: 100%;
            margin: 0;
            overflow-x: hidden; /* Hide horizontal scrollbar */
            scroll-behavior: smooth; /* Add smooth scrolling behavior */
        }
        .dot {
            width: 10px; /* Fixed dot size */
            height: 10px; /* Fixed dot size */
            border-radius: 50%;
            background-color: red;
            animation: colorFade 2s infinite alternate;
        }
        @keyframes colorFade {
            0% {
                background-color: red;
            }
            100% {
                background-color: green;
            }
        }
        .dot-container {
    position: absolute;
    top: 5vh; /* Adjusted top value to fit better on the screen */
    left: 1vw; /* Shifted the left side 5% to the left */
    width: 90%; /* Set width to 90% */
    display: grid;
    grid-template-columns: repeat(auto-fill, 20px); /* Fixed column size for dots */
    gap: 20px; /* Fixed gap size for dots */
    overflow: visible;
    border: 5px solid #333; /* Adjusted border size for responsiveness */
}

</style>
</head>
<body>
    <div class="dot-container"></div>
    <script>
        function createDots() {
            const dotContainer = document.querySelector('.dot-container');
            for (let i = 0; i < window.innerWidth / 20; i++) {
                createDot(dotContainer, i * 20, 0); // Top row
                createDot(dotContainer, i * 20, window.innerHeight - 20); // Bottom row
            }
            for (let i = 1; i < (window.innerHeight - 20) / 20; i++) {
                createDot(dotContainer, 0, i * 20); // Left column
                createDot(dotContainer, window.innerWidth - 20, i * 20); // Right column
            }
        }
        function createDot(container, x, y) {
            const dot = document.createElement('div');
            dot.className = 'dot';
            dot.style.top = y + 'px';
            dot.style.left = x + 'px';
            container.appendChild(dot);
        }
        createDots();
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