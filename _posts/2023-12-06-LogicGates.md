---
toc: true
comments: false
layout: post
title: Logic Gates (Final)
description: N/A
type: ccc
courses: { csp: {week: 13} }
---
<html lang="en">
<!--Aditi>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--scales the code to the dimensions of the computer-->
</head>

<body>
    <!-- Main content container -->
    <div class="container">
        <!-- AND Gate -->
        <div class="gate-container">
            <!-- Button 1 for AND gate -->
            <div class="button-container">
                <button id="andButton1" class="button" onclick="toggleButton('and', 1)">1</button>
                <!--andButton1 provides a unique identifier for this button that helps connect it to other funcitons, like the dots and the color changing icons-->
            </div>
            <!-- Button 2 for AND gate -->
            <div class="button-container">
                <button id="andButton2" class="button" onclick="toggleButton('and', 2)">0</button>
            </div>
            <!-- SVG representation of AND gate -->
            <svg width="150" height="70"> <text x="35" y="60" font-size="12" fill="white">AND</text> <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2" /> <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2" /> <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2" /> <circle id="andGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
</svg>
            <!-- Output icon for AND gate -->
            <div class="button-container">
                <i id="andOutputIcon" class="fas fa-lightbulb output-icon and-bulb"></i>
            </div>
            <!-- Dot for AND gate light -->
            <div class="dot" id="dotAnd" style="top: 70px; left: 25px;" onclick="changeDotColor('dotAnd')"></div>
        </div>

<!-- OR Gate -->
<div class="gate-container">
            <!-- Button 1 for OR gate -->
            <div class="button-container">
                <button id="orButton1" class="button" onclick="toggleButton('or', 1)">1</button>
            </div>
            <!-- Button 2 for OR gate -->
            <div class="button-container">
                <button id="orButton2" class="button" onclick="toggleButton('or', 2)">0</button>
            </div>
            <!-- SVG representation of OR gate -->
            <svg width="150" height="70"> <text x="35" y="60" font-size="12" fill="white">OR</text><line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2" /><line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2" /><line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2" /><circle id="orGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
</svg>
            <!-- Output icon for OR gate -->
            <div class="button-container">
                <i id="orOutputIcon" class="fas fa-lightbulb output-icon or-bulb"></i>
            </div>
            <!-- Dot for OR gate light -->
            <div class="dot" id="dotOr" style="top: 70px; left: 95px;" onclick="changeDotColor('dotOr')"></div>
        </div>

<!-- NOR Gate -->
<div class="gate-container">
            <!-- Button 1 for NOR gate -->
            <div class="button-container">
                <button id="norButton1" class="button" onclick="toggleButton('nor', 1)">1</button>
            </div>
            <!-- Button 2 for NOR gate -->
            <div class="button-container">
                <button id="norButton2" class="button" onclick="toggleButton('nor', 2)">0</button>
            </div>
            <!-- SVG representation of NOR gate -->
            <svg width="150" height="70"><text x="35" y="60" font-size="12" fill="white">NOR</text><circle id="norGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
</svg>
            <!-- Output icon for NOR gate -->
            <div class="button-container">
                <i id="norOutputIcon" class="fas fa-lightbulb output-icon nor-bulb"></i>
            </div>
            <!-- Dot for NOR gate light -->
            <div class="dot" id="dotNor" style="top: 70px; left: 170px;" onclick="changeDotColor('dotNor')"></div>
        </div>

<!-- XOR Gate -->
<div class="gate-container">
            <!-- Button 1 for XOR gate -->
            <div class="button-container">
                <button id="xorButton1" class="button" onclick="toggleButton('xor', 1)">1</button>
            </div>
            <!-- Button 2 for XOR gate -->
            <div class="button-container">
                <button id="xorButton2" class="button" onclick="toggleButton('xor', 2)">0</button>
            </div>
            <!-- SVG representation of XOR gate -->
            <svg width="150" height="70"> <text x="35" y="60" font-size="12" fill="white">XOR</text> <circle id="xorGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" /> </svg>
            <!-- Output icon for XOR gate -->
            <div class="button-container">
                <i id="xorOutputIcon" class="fas fa-lightbulb output-icon xor-bulb"></i>
            </div>
            <!-- Dot for XOR gate light -->
            <div class="dot" id="dotXor" style="top: 70px; left: 245px;" onclick="changeDotColor('dotXor')"></div>
        </div>
<!-- Eshika -->
 <!-- Tree -->
<div class="tree">
            <div class="trunk"></div>
        </div>
    </div>

 <!-- Font Awesome (icons) (the lights) -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
        integrity="sha384-9a2a2PZMZJ4fuXRiK7ujL3IOIRcm6SjFayZBS1G3uMMLr5Z/2q5U1dd2Yiz5Mlks"
        crossorigin="anonymous">

<!-- JavaScript for gate logic -->
<script>
        // Gate state variables
        let andGateState = [true, false];
        let orGateState = [true, false];
        let norGateState = [true, false];
        let xorGateState = [true, false];

        // Toggle button state and update gate logic
function toggleButton(gate, button) {
    const index = button - 1; // Adjust index
    const buttonElement = document.getElementById(`${gate}Button${button}`);
    
    // Toggle button value between 1 and 0
    buttonElement.textContent = buttonElement.textContent === '1' ? '0' : '1';

    // Update gate logic based on the new button value
    switch (gate) {
        case 'and':
            andGateState[index] = buttonElement.textContent === '1';
            updateAndGate();
            break;
        case 'or':
            orGateState[index] = buttonElement.textContent === '1';
            updateOrGate();
            break;
        case 'nor':
            norGateState[index] = buttonElement.textContent === '1';
            updateNorGate();
            break;
        case 'xor':
            xorGateState[index] = buttonElement.textContent === '1';
            updateXorGate();
            break;
    }
}

        // Update AND gate logic and display
        function updateAndGate() {
            const output = andGateState[0] && andGateState[1];
            document.getElementById('andGateOutput').setAttribute('fill', output ? 'red' : 'white');
            document.getElementById('andOutputIcon').classList.toggle('and-bulb', output);
            document.getElementById('dotAnd').style.backgroundColor = output ? 'red' : 'white';
        }

        // Update OR gate logic and display
        function updateOrGate() {
            const output = orGateState[0] || orGateState[1];
            document.getElementById('orGateOutput').setAttribute('fill', output ? 'orange' : 'white');
            document.getElementById('orOutputIcon').classList.toggle('or-bulb', output);
            document.getElementById('dotOr').style.backgroundColor = output ? 'orange' : 'white';
        }

        // Update NOR gate logic and display
        function updateNorGate() {
            const output = !(norGateState[0] || norGateState[1]);
            document.getElementById('norGateOutput').setAttribute('fill', output ? 'blue' : 'white');
            document.getElementById('norOutputIcon').classList.toggle('nor-bulb', output);
            document.getElementById('dotNor').style.backgroundColor = output ? 'blue' : 'white';
        }

        // Update XOR gate logic and display
        function updateXorGate() {
            const output = xorGateState[0] !== xorGateState[1];
            document.getElementById('xorGateOutput').setAttribute('fill', output ? 'green' : 'white');
            document.getElementById('xorOutputIcon').classList.toggle('xor-bulb', output);
            document.getElementById('dotXor').style.backgroundColor = output ? 'darkgreen' : 'white';
        }

// Cindy

// Function to calculate dot positions relative to the top of the page
function calculateDotPositions() {
    const containerWidth = document.querySelector('.container').offsetWidth; // Get the width of the container
    const containerHeight = document.querySelector('.container').offsetHeight; // Get the height of the container

    // Calculate positions for each dot
    const dotOR = containerHeight * 1.49; // Top of the container
    const dotAND = containerWidth * 0.80; // 5% from the left of the container
    const dotNOR = containerWidth * 0.76; // 10% from the left of the container
    const dotXOR = containerWidth * 0.82; // 15% from the left of the container

    // Set positions for each dot
    document.getElementById('dotOr').style.top = `${dotOR}px`;
    document.getElementById('dotAnd').style.top = `${dotAND}px`;
    document.getElementById('dotNor').style.top = `${dotNOR}px`;
    document.getElementById('dotXor').style.top = `${dotXOR}px`;

    // Set positions for each dot horizontally
    document.getElementById('dotOr').style.left = `${containerWidth * 0.0565}%`; // Adjusted for consistency
    document.getElementById('dotAnd').style.left = `${containerWidth * 0.055}%`;
    document.getElementById('dotNor').style.left = `${containerWidth * 0.057}%`; // Adjusted for consistency
    document.getElementById('dotXor').style.left = `${containerWidth * 0.0586}%`;

}

// Calculate positions when the page loads
window.onload = function () {
        calculateDotPositions();
        updateAndGate(); // Set initial state for AND gate
        updateNorGate(); // Set initial state for NOR gate
        updateXorGate();
        updateOrGate();
    };
// Snowfall
document.addEventListener('DOMContentLoaded', function () {
    // Array to store information about each snowflake
    const snowflakes = [];

    // Function to create a new snowflake
    function createSnowflake() {
        // Random diameter between 5px and 20px
        const diameter = Math.floor(Math.random() * 16) + 5;

        // Random speed between 10px/sec and 30px/sec
        const speed = Math.floor(Math.random() * 20) + 10;

        // Random position within the leftmost or rightmost 25% of the screen
        const positionX = Math.random() < 0.5 ?
            Math.floor(Math.random() * window.innerWidth / 4) : // Leftmost 25%
            Math.floor(Math.random() * window.innerWidth / 4) + (window.innerWidth * 0.75); // Rightmost 25%

        // Random position within the window height
        const positionY = Math.floor(Math.random() * window.innerHeight) + 1;

        // Create a new div element for the snowflake
        const snowflake = document.createElement('div');

        // Set the class for styling (CSS styling required for appearance)
        snowflake.className = 'snowflake';

        // Set width and height based on the random diameter
        snowflake.style.width = `${diameter}px`;
        snowflake.style.height = `${diameter}px`;

        // Set the initial position of the snowflake
        snowflake.style.left = `${positionX}px`;
        snowflake.style.top = `${positionY}px`;

        // Append the snowflake to the body of the document
        document.body.appendChild(snowflake);

        // Store information about the snowflake in the array
        snowflakes.push({
            element: snowflake,
            diameter,
            speed,
            positionX,
            positionY,
        });
    }

    // Function to update the position of each snowflake and create the falling effect
    function updateSnowfall() {
        for (const snowflake of snowflakes) {
            // Update the vertical position based on the speed
            snowflake.positionY += snowflake.speed / 10;

            // If the snowflake goes below the window, reset its position to the top
            if (snowflake.positionY > window.innerHeight) {
                snowflake.positionY = -10;
            }

            // Set the updated top position for the snowflake
            snowflake.element.style.top = `${snowflake.positionY}px`;
        }

        // Request the next animation frame to continue the animation
        requestAnimationFrame(updateSnowfall);
    }

    // Function to initialize the snowfall by creating multiple snowflakes
    function initializeSnowfall() {
        // Create 30 snowflakes
        for (let i = 0; i < 30; i++) {
            createSnowflake();
        }

        // Start the animation
        updateSnowfall();
    }

    // Call the initialization function when the DOM content is fully loaded
    initializeSnowfall();
});

</script>
    
</body>

</html>