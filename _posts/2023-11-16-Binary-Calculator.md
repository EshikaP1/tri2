---
toc: false
comments: false
layout: post
title: Binary Calculator
description: "For our calculator, we aim to feature various backgrounds and themes. Leveraging SASS, we will establish a primary theme characterized by a rainbow background and calculator buttons in a shade approximating #ADD8E6. Upon activating the switch button to access the graphing calculator, the color scheme will transform into monochromatic tones, featuring a black background with the same blue buttons.We plan to develop the calculator by associating each number with its binary representation. The implementation will involve HTML and JavaScript to create the functional calculator, offering features comparable to a standard calculator. Initially, it will function as a basic four-operation calculator. However, we intend to incorporate a toggle switch that, when activated, transforms it into a graphing calculator with additional capabilities."
type: ccc
courses: { csp: {week: 13} }
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        input {
            width: 150px;
            padding: 5px;
            margin: 5px;
        }
        button {
            padding: 8px;
            margin: 5px;
            cursor: pointer;
        }
        .keyboard {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 5px;
            margin-top: 20px;
        }
    </style>
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
    <!-- Generate number buttons from 0 to 9 -->
    <script>
        for (var i = 0; i <= 9; i++) {
            document.write("<button onclick=\"addToInput('" + i + "')\">" + i + "</button>");
        }
    </script>
</div>

<script>
    function performOperation(operation) {
        var num1 = document.getElementById("num1").value;
        var num2 = document.getElementById("num2").value;
        var resultField = document.getElementById("result");

        // Convert input numbers to binary
        var binaryNum1 = decimalToBinary(parseInt(num1, 10));
        var binaryNum2 = decimalToBinary(parseInt(num2, 10));

        switch (operation) {
            case 'add':
                resultField.value = decimalToBinary(binaryToDecimal(binaryNum1) + binaryToDecimal(binaryNum2));
                break;
            case 'subtract':
                resultField.value = decimalToBinary(binaryToDecimal(binaryNum1) - binaryToDecimal(binaryNum2));
                break;
            case 'multiply':
                resultField.value = decimalToBinary(binaryToDecimal(binaryNum1) * binaryToDecimal(binaryNum2));
                break;
            case 'divide':
                resultField.value = decimalToBinary(Math.floor(binaryToDecimal(binaryNum1) / binaryToDecimal(binaryNum2)));
                break;
            default:
                resultField.value = "Invalid operation";
        }
    }

    function decimalToBinary(decimalNum) {
        return (decimalNum >>> 0).toString(2); // Using ">>> 0" to treat the input as a 32-bit unsigned integer
    }

    function binaryToDecimal(binaryStr) {
        return parseInt(binaryStr, 2);
    }

    function addToInput(number) {
        var activeInput = document.activeElement;

        if (activeInput.tagName === "INPUT" && activeInput.type === "text") {
            activeInput.value += number;
        }
    }

    
</script>

<style>
        /* Updated CSS Styles to make the calculator pink */

        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f7e6e6; /* Light pink background color */
        }

        input {
            width: 150px;
            padding: 5px;
            margin: 5px;
            background-color: #ffe3e3; /* Light pink input background color */
            border: 1px solid #ffcccc; /* Light pink border color */
        }

        button {
            padding: 8px;
            margin: 5px;
            cursor: pointer;
            background-color: #ffcccc; /* Pink button background color */
            border: none;
            color: #fff; /* Text color for buttons */
        }

        .keyboard {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 5px;
            margin-top: 20px;
        }

        h1 {
            color: #ff4d6b; /* Pink color for heading text */
        }
    </style>

    <script src="{{site.baseurl}}/assets/js/three.r119.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.halo.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.birds.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.net.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.rings.min.js"></script>

<script>
// setup vanta scripts as functions
var vantaInstances = {
  halo: VANTA.HALO,
  birds: VANTA.BIRDS,
  net: VANTA.NET,
  rings: VANTA.RINGS
};

// obtain a random vanta function
var vantaInstance = vantaInstances[Object.keys(vantaInstances)[Math.floor(Math.random() * Object.keys(vantaInstances).length)]];

// run the animation
vantaInstance({
  el: "#animation",
  mouseControls: true,
  touchControls: true,
  gyroControls: false
});


// Variables
$primary-color: #ff6b6b; // Pink color
$secondary-color: #fff; // White color
$button-bg-color: #ffb8b8; // Light pink for button background
$button-hover-color: #ff9999; // Lighter pink for button hover effect

// Calculator container
.calculator {
  background-color: $secondary-color;
  border-radius: 10px;
  padding: 20px;
  width: 300px;
  margin: 0 auto;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  font-family: Arial, sans-serif;
  text-align: center;
  
  // Calculator display
  .display {
    background-color: $primary-color;
    color: $secondary-color;
    padding: 10px;
    border-radius: 5px;
    margin-bottom: 15px;
    font-size: 24px;
  }
  
  // Calculator buttons
  .buttons {
    display: grid;
    grid-gap: 10px;
    grid-template-columns: repeat(4, 1fr);
    
    button {
      background-color: $button-bg-color;
      color: $primary-color;
      padding: 15px 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 18px;
      transition: background-color 0.3s ease;
      
      &:hover {
        background-color: $button-hover-color;
      }
      
      &.equal {
        grid-column: span 2;
      }
      
      &.clear {
        grid-column: span 3;
      }
    }
  }
}
</script>
</body>
</html>
