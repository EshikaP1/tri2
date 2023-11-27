---
layout: home
search_exclude: true
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Logical Gates Simulator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
.container {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }
.gate-container {
            display: flex;
            align-items: center;
        }
.button-container {
            margin: 10px;
        }
.button {
            padding: 10px 20px;
            font-size: 16px;
        }
svg {
            margin: 0 20px;
        }
 .output-icon {
            font-size: 30px;
        }
.and-bulb {
            color: red;
        }
.or-bulb {
            color: orange;
        }
.nor-bulb {
            color: blue;
        }
.xor-bulb {
            color: green;
        }
.gate-label {
            font-size: 18px;
            margin-right: 10px;
            fill: white; /* Change text color to white */
        }
    </style>
    <!-- Include Font Awesome CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-Bw+irXzAGYTW3oIUcI+5B3c5AcXKXtwJU6dRfkaOTpAupzWC8FX6C9AjbV8AGj8G/oPfOj0lg/9hbo+KwIzA4A==" crossorigin="anonymous" referrerpolicy="no-referrer" />
</head>
<body>

<div class="container">
    <!-- AND Gate -->
    <div class="gate-container">
        <div class="button-container">
            <button id="andButton1" class="button" onclick="toggleButton('and', 1)">1</button>
        </div>

 <div class="button-container">
            <button id="andButton2" class="button" onclick="toggleButton('and', 2)">0</button>
        </div>

 <svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">AND</text>
            <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2"/>
            <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2"/>
            <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2"/>
            <circle id="andGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

 <div class="button-container">
            <i id="andOutputIcon" class="fas fa-lightbulb output-icon and-bulb"></i>
        </div>
    </div>

 <!-- OR Gate -->
<div class="gate-container">
        <div class="button-container">
            <button id="orButton1" class="button" onclick="toggleButton('or', 1)">1</button>
        </div>

<div class="button-container">
            <button id="orButton2" class="button" onclick="toggleButton('or', 2)">0</button>
        </div>

<svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">OR</text>
            <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2"/>
            <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2"/>
            <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2"/>
            <circle id="orGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

 <div class="button-container">
            <i id="orOutputIcon" class="fas fa-lightbulb output-icon or-bulb"></i>
        </div>
    </div>

 <!-- NOR Gate -->
<div class="gate-container">
        <div class="button-container">
            <button id="norButton1" class="button" onclick="toggleButton('nor', 1)">1</button>
        </div>

 <div class="button-container">
            <button id="norButton2" class="button" onclick="toggleButton('nor', 2)">0</button>
        </div>

  <svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">NOR</text>
            <circle id="norGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

 <div class="button-container">
            <i id="norOutputIcon" class="fas fa-lightbulb output-icon nor-bulb"></i>
        </div>
    </div>

<!-- XOR Gate -->
 <div class="gate-container">
        <div class="button-container">
            <button id="xorButton1" class="button" onclick="toggleButton('xor', 1)">1</button>
        </div>

 <div class="button-container">
            <button id="xorButton2" class="button" onclick="toggleButton('xor', 2)">0</button>
        </div>

  <svg width="150" height="70">
            <text x="35" y="60" font-size="12" fill="white">XOR</text>
            <circle id="xorGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2"/>
        </svg>

 <div class="button-container">
            <i id="xorOutputIcon" class="fas fa-lightbulb output-icon xor-bulb"></i>
        </div>
    </div>
</div>

<script>
    let andButtonStates = [0, 0]; // Initial states of the AND gate buttons (0 is OFF, 1 is ON)
    let orButtonStates = [0, 0]; // Initial states of the OR gate buttons (0 is OFF, 1 is ON)
    let norButtonStates = [0, 0]; // Initial states of the NOR gate buttons (0 is OFF, 1 is ON)
    let xorButtonStates = [0, 0]; // Initial states of the XOR gate buttons (0 is OFF, 1 is ON)

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
