---
toc: false
comments: false
layout: post
title: Binary Calculator
description: "For our calculator, we aim to feature various backgrounds and themes. Leveraging SASS, we will establish a primary theme characterized by a rainbow background and calculator buttons in a shade approximating #ADD8E6. Upon activating the switch button to access the graphing calculator, the color scheme will transform into monochromatic tones, featuring a black background with the same blue buttons.We plan to develop the calculator by associating each number with its binary representation. The implementation will involve HTML and JavaScript to create the functional calculator, offering features comparable to a standard calculator. Initially, it will function as a basic four-operation calculator. However, we intend to incorporate a toggle switch that, when activated, transforms it into a graphing calculator with additional capabilities."
type: ccc
courses: { csp: {week: 13} }
---



<!DOCTYPE html>
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

<form id="binaryCalculator">
    <label for="num1">Binary Number 1:</label>
    <input type="text" id="num1" readonly>
    <br>

    <label for="num2">Binary Number 2:</label>
    <input type="text" id="num2" readonly>
    <br>

    <button type="button" onclick="performOperation('add')">Addition (+)</button>
    <button type="button" onclick="performOperation('subtract')">Subtraction (-)</button>
    <button type="button" onclick="performOperation('multiply')">Multiplication (*)</button>
    <button type="button" onclick="performOperation('divide')">Division (/)</button>
    <br>

    <label for="result">Result:</label>
    <input type="text" id="result" readonly>
</form>

<div class="keyboard">
    <!-- Generate number buttons from 1 to 1001 -->
    <?php
    for ($i = 1; $i <= 1001; $i++) {
        echo "<button onclick=\"addToInput($i)\">$i</button>";
    }
    ?>
</div>

<script>
    function performOperation(operation) {
        var num1 = document.getElementById("num1").value;
        var num2 = document.getElementById("num2").value;
        var resultField = document.getElementById("result");

        switch (operation) {
            case 'add':
                resultField.value = addBinary(num1, num2);
                break;
            case 'subtract':
                resultField.value = subtractBinary(num1, num2);
                break;
            case 'multiply':
                resultField.value = multiplyBinary(num1, num2);
                break;
            case 'divide':
                resultField.value = divideBinary(num1, num2);
                break;
            default:
                resultField.value = "Invalid operation";
        }
    }

    function addBinary(binNum1, binNum2) {
        var decimalSum = parseInt(binNum1, 2) + parseInt(binNum2, 2);
        return decimalSum.toString(2);
    }

    function subtractBinary(binNum1, binNum2) {
        var decimalDiff = parseInt(binNum1, 2) - parseInt(binNum2, 2);
        return decimalDiff.toString(2);
    }

    function multiplyBinary(binNum1, binNum2) {
        var decimalProd = parseInt(binNum1, 2) * parseInt(binNum2, 2);
        return decimalProd.toString(2);
    }

    function divideBinary(binNum1, binNum2) {
        var decimalQuotient = Math.floor(parseInt(binNum1, 2) / parseInt(binNum2, 2));
        return decimalQuotient.toString(2);
    }

    function addToInput(number) {
        var num1Input = document.getElementById("num1");
        var num2Input = document.getElementById("num2");

        // Check which input field is active and add the number to it
        if (num1Input === document.activeElement) {
            num1Input.value += number.toString(2);
        } else if (num2Input === document.activeElement) {
            num2Input.value += number.toString(2);
        }
    }
</script>

</body>
</html>