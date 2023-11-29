---
layout: home
search_exclude: true
---
<!-- Metadata section -->

<!-- HTML document structure -->
<html lang="en">
<head>
    <!-- Metadata for character set and viewport -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
<!-- Title of the webpage -->
<title>Logical Gates Simulator</title>
    
<!-- Styling for the webpage -->
<style>
        /* Global styles for the body */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }

        /* Container styling for layout */
        .container {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        /* Styling for each gate container */
        .gate-container {
            display: flex;
            align-items: center;
        }

        /* Styling for button containers */
        .button-container {
            margin: 10px;
        }

        /* Styling for buttons */
        .button {
            padding: 10px 20px;
            font-size: 16px;
        }

        /* Styling for SVG elements */
        svg {
            margin: 0 20px;
        }

        /* Styling for output icons */
        .output-icon {
            font-size: 30px;
        }

        /* Styling for AND gate bulb */
        .and-bulb {
            color: red;
        }

        /* Styling for OR gate bulb */
        .or-bulb {
            color: orange;
        }

        /* Styling for NOR gate bulb */
        .nor-bulb {
            color: blue;
        }

        /* Styling for XOR gate bulb */
        .xor-bulb {
            color: green;
        }

        /* Styling for gate labels */
        .gate-label {
            font-size: 18px;
            margin-right: 10px;
            fill: white; /* Change text color to white */
        }
    </style>
    
<!-- Include Font Awesome CSS for icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-Bw+irXzAGYTW3oIUcI+5B3c5AcXKXtwJU6dRfkaOTpAupzWC8FX6C9AjbV8AGj8G/oPfOj0lg/9hbo+KwIzA4A==" crossorigin="anonymous" referrerpolicy="no-referrer" />
</head>
<body>

<!-- Main content container -->
<div class="container">
    <!-- AND Gate -->
    <div class="gate-container">
        <!-- Button 1 for AND gate -->
        <div class="button-container">
            <button id="andButton1" class="button" onclick="toggleButton('and', 1)">1</button>
        </div>

<!-- Button 2 for AND gate -->
<div class="button-container">
            <button id="andButton2" class="button" onclick="toggleButton('and', 2)">0</button>
        </div>

<!-- SVG representation of AND gate -->
<svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">AND</text>
            <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2"/>
            <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2"/>
            <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2"/>
            <circle id="andGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

<!-- Output icon for AND gate -->
<div class="button-container">
            <i id="andOutputIcon" class="fas fa-lightbulb output-icon and-bulb"></i>
        </div>
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
<svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">OR</text>
            <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2"/>
            <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2"/>
            <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2"/>
            <circle id="orGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

<!-- Output icon for OR gate -->
<div class="button-container">
            <i id="orOutputIcon" class="fas fa-lightbulb output-icon or-bulb"></i>
        </div>
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
<svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">NOR</text>
            <circle id="norGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

<!-- Output icon for NOR gate -->
<div class="button-container">
            <i id="norOutputIcon" class="fas fa-lightbulb output-icon nor-bulb"></i>
        </div>
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
<svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">XOR</text>
            <circle id="xorGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

<!-- Output icon for XOR gate -->
<div class="button-container">
            <i id="xorOutputIcon" class="fas fa-lightbulb output-icon xor-bulb"></i>
        </div>
    </div>
</div>

<!-- JavaScript script for gate functionality -->
<script>
    // Initial states of the buttons for each gate
    let andButtonStates = [0, 0];
    let orButtonStates = [0, 0];
    let norButtonStates = [0, 0];
    let xorButtonStates = [0, 0];

    // Function to toggle the state of a button for a specific gate
    function toggleButton(gateType, buttonNumber) {
        if (gateType === 'and') {
            andButtonStates[buttonNumber - 1] = 1 - andButtonStates[buttonNumber - 1];
            document.getElementById(`andButton${buttonNumber}`).innerText = andButtonStates[buttonNumber - 1];
            updateAndOutput();
        } else if (gateType === 'or') {
            orButtonStates[buttonNumber - 1] = 1 - orButtonStates[buttonNumber - 1];
            document.getElementById(`orButton${buttonNumber}`).innerText = orButtonStates[buttonNumber - 1];
            updateOrOutput();
        } else if (gateType === 'nor') {
            norButtonStates[buttonNumber - 1] = 1 - norButtonStates[buttonNumber - 1];
            document.getElementById(`norButton${buttonNumber}`).innerText = norButtonStates[buttonNumber - 1];
            updateNorOutput();
        } else if (gateType === 'xor') {
            xorButtonStates[buttonNumber - 1] = 1 - xorButtonStates[buttonNumber - 1];
            document.getElementById(`xorButton${buttonNumber}`).innerText = xorButtonStates[buttonNumber - 1];
            updateXorOutput();
        }
    }

    // Function to update the output for the AND gate
    function updateAndOutput() {
        const andResult = andButtonStates[0] & andButtonStates[1]; // AND logic gate
        const andOutputIcon = document.getElementById('andOutputIcon');
        const andGateOutput = document.getElementById('andGateOutput');

        if (andResult === 1) {
            andOutputIcon.style.color = 'red';
            andGateOutput.setAttribute('fill', 'red');
        } else {
            andOutputIcon.style.color = '#ccc';
            andGateOutput.setAttribute('fill', 'white');
        }
    }

    // Function to update the output for the OR gate
    function updateOrOutput() {
        const orResult = orButtonStates[0] | orButtonStates[1]; // OR logic gate
        const orOutputIcon = document.getElementById('orOutputIcon');
        const orGateOutput = document.getElementById('orGateOutput');

        if (orResult === 1) {
            orOutputIcon.style.color = 'orange';
            orGateOutput.setAttribute('fill', 'orange');
        } else {
            orOutputIcon.style.color = '#ccc';
            orGateOutput.setAttribute('fill', 'white');
        }
    }

    // Function to update the output for the NOR gate
    function updateNorOutput() {
        const norResult = !(norButtonStates[0] | norButtonStates[1]); // NOR logic gate
        const norOutputIcon = document.getElementById('norOutputIcon');
        const norGateOutput = document.getElementById('norGateOutput');

        if (norResult) {
            norOutputIcon.style.color = 'blue';
            norGateOutput.setAttribute('fill', 'blue');
        } else {
            norOutputIcon.style.color = '#ccc';
            norGateOutput.setAttribute('fill', 'white');
        }
    }

    // Function to update the output for the XOR gate
    function updateXorOutput() {
        const xorResult = xorButtonStates[0] ^ xorButtonStates[1]; // XOR logic gate
        const xorOutputIcon = document.getElementById('xorOutputIcon');
        const xorGateOutput = document.getElementById('xorGateOutput');

        if (xorResult) {
            xorOutputIcon.style.color = 'green';
            xorGateOutput.setAttribute('fill', 'green');
        } else {
            xorOutputIcon.style.color = '#ccc';
            xorGateOutput.setAttribute('fill', 'white');
        }
    }
</script>

</body>
</html>
