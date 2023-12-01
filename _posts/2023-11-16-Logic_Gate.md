
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

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

        /* Tree styles */
        .tree {
            position: relative;
            width: 0;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-bottom: 100px solid green;
            margin-top: 30px;
        }

        .trunk {
            position: relative;
            width: 27px;
            height: 40px;
            background-color: brown;
            top: 100px;
            left: -15px;
        }
        </style>
 <style>       
/* Dot styles */
.dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    cursor: pointer;
}

/* Dots for the Green Triangle */
#dotGreen1 {
    position: absolute;
    top: 630px;
    left: 670px;
    background-color: #CFD3CF;
}

#dotGreen2 {
    position: absolute;
    top: 660px;
    left: 680px;
    background-color: #CFD3CF;
}

#dotGreen3 {
    position: absolute;
    top: 710px;
    left: 700px;
    background-color: #CFD3CF;
}

#dotGreen4 {
    position: absolute;
    top: 700px;
    left: 700px;
    background-color: #CFD3CF;
}

</style>

    </style>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
        integrity="sha512-Bw+irXzAGYTW3oIUcI+5B3c5AcXKXtwJU6dRfkaOTpAupzWC8FX6C9AjbV8AGj8G/oPfOj0lg/9hbo+KwIzA4A=="
        crossorigin="anonymous" referrerpolicy="no-referrer" />
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
                <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2" />
                <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2" />
                <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2" />
                <circle id="andGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
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
            <svg width="150" height="70">
                <text x="35" y="60" font-size="12" fill="white">OR</text>
                <line x1="0" y1="25" x2="50" y2="25" stroke="white" stroke-width="2" />
                <line x1="70" y1="15" x2="70" y2="35" stroke="white" stroke-width="2" />
                <line x1="50" y1="25" x2="70" y2="25" stroke="white" stroke-width="2" />
                <circle id="orGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
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
            <svg width="150" height="70">
                <text x="35" y="60" font-size="12" fill="white">NOR</text>
                <circle id="norGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
            </svg>
            <!-- Output icon for NOR gate -->
            <div class="button-container">
                <i id="norOutputIcon" class="fas fa-lightbulb output-icon nor-bulb"></i>
            </div>
            <!-- Dot for NOR gate light -->
            <div class="dot" id="dotNor" style="top: 0; left: 30px;" onclick="changeDotColor('dotNor')"></div>
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
                <circle id="xorGateOutput" cx="0" cy="25" r="5" fill="white" stroke="white" stroke-width="2" />
            </svg>
            <!-- Output icon for XOR gate -->
            <div class="button-container">
                <i id="xorOutputIcon" class="fas fa-lightbulb output-icon xor-bulb"></i>
            </div>
            <!-- Dot for XOR gate light -->
            <div class="dot" id="dotXor" style="top: 0; left: 105px;" onclick="changeDotColor('dotXor')"></div>
        </div>

        

 <!-- Tree -->
<div class="tree">
            <div class="trunk"></div>
        </div>
    </div>

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
        updateDotColor(andResult, 'dotAnd');
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
        updateDotColor(orResult, 'dotOr');
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
        updateDotColor(norResult, 'dotNor');
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
        updateDotColor(xorResult, 'dotXor');
    }

    // Function to update the color of a dot based on gate result
    function updateDotColor(gateResult, dotId) {
        const dot = document.getElementById(dotId);
        const blueLight = document.getElementById('blueLight');
        const randomColor = getRandomColor();

        if (gateResult === 1) {
            dot.style.backgroundColor = randomColor;
        } else {
            dot.style.backgroundColor = 'transparent';
        }

        // Change the blue light color if the dotId is dotBlue
        if (dotId === 'dotBlue') {
            blueLight.setAttribute('fill', randomColor);
        }
    }


</script>

<!-- Dots for the Green Triangle -->
<div class="gate-container">
    <!-- Dot 1 for the Green Triangle -->
    <div class="dot" id="dotGreen1" style="top: 580px; left: 675px; background-color: #CFD3CF;" onclick="changeDotColor('dotGreen1')"></div>
    <!-- Dot 2 for the Green Triangle -->
    <div class="dot" id="dotGreen2" style="top: 610px; left: 685px; background-color: #CFD3CF;" onclick="changeDotColor('dotGreen2')"></div>
    <!-- Dot 3 for the Green Triangle -->
    <div class="dot" id="dotGreen3" style="top: 640x; left: 695px; background-color: #CFD3CF;" onclick="changeDotColor('dotGreen3')"></div>
    <!-- Dot 4 for the Green Triangle -->
    <div class="dot" id="dotGreen4" style="top: 650px; left: 645px; background-color: #CFD3CF;" onclick="changeDotColor('dotGreen4')"></div>
</div>
<!-- Existing JavaScript code above -->

<script>
    // Function to update the color of a dot based on gate result
    function updateDotColor(gateResult, dotId) {
        const dot = document.getElementById(dotId);

        // Change the color of the dot based on the gate result
        switch (dotId) {
            case 'dotAnd':
                dot.style.backgroundColor = gateResult === 1 ? 'red' : '#ccc';
                break;
            case 'dotOr':
                dot.style.backgroundColor = gateResult === 1 ? 'orange' : '#ccc';
                break;
            case 'dotNor':
                dot.style.backgroundColor = gateResult === 1 ? 'blue' : '#ccc';
                break;
            case 'dotXor':
                dot.style.backgroundColor = gateResult === 1 ? 'green' : '#ccc';
                break;
            case 'dotGreen1':
            case 'dotGreen2':
            case 'dotGreen3':
            case 'dotGreen4':
                dot.style.backgroundColor = gateResult === 1 ? 'red' : '#ccc';
                break;
            // Add more cases for other dots if needed
        }
    }

    // Function to update the dots for the Green Triangle based on AND gate result
    function updateGreenDots() {
        const andResult = andButtonStates[0] & andButtonStates[1]; // AND logic gate
        updateDotColor(andResult, 'dotGreen1');
        updateDotColor(andResult, 'dotGreen2');
        updateDotColor(andResult, 'dotGreen3');
        updateDotColor(andResult, 'dotGreen4');
    }

    // Function to update the dots for other gates based on their results
    function updateOtherDots() {
        // Update dots for OR gate
        const orResult = orButtonStates[0] | orButtonStates[1]; // OR logic gate
        updateDotColor(orResult, 'dotOr');

        // Update dots for NOR gate
        const norResult = !(norButtonStates[0] | norButtonStates[1]); // NOR logic gate
        updateDotColor(norResult, 'dotNor');

        // Update dots for XOR gate
        const xorResult = xorButtonStates[0] ^ xorButtonStates[1]; // XOR logic gate
        updateDotColor(xorResult, 'dotXor');
    }

    // Function to toggle the state of a button for a gate and update the dots
    function toggleButtonAndUpdateDots(gateType, buttonNumber) {
        toggleButton(gateType, buttonNumber);
        switch (gateType) {
            case 'and':
                updateGreenDots();
                break;
            case 'or':
            case 'nor':
            case 'xor':
                updateOtherDots();
                break;
            // Add more cases for other gates if needed
        }
    }

    // Event listeners for AND gate buttons
    document.getElementById('andButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('and', 1);
    });

    document.getElementById('andButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('and', 2);
    });

    // Event listeners for other gate buttons
    document.getElementById('orButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('or', 1);
    });

    document.getElementById('orButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('or', 2);
    });

    document.getElementById('norButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('nor', 1);
    });

    document.getElementById('norButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('nor', 2);
    });

    document.getElementById('xorButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('xor', 1);
    });

    document.getElementById('xorButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('xor', 2);
    });
</script>

<!-- Existing JavaScript code below -->
<!-- Existing JavaScript code above -->

<script>
    // Map each dot to its corresponding gate and color
    const dotGateMapping = {
        'dotGreen1': 'and',
        'dotGreen2': 'or',
        'dotGreen3': 'nor',
        'dotGreen4': 'xor',
    };

    // Function to update the color of a dot based on its associated gate result
    function updateDotColorByGate(gateResult, dotId) {
        const dot = document.getElementById(dotId);
        const gateType = dotGateMapping[dotId];

        // Change the color of the dot based on its associated gate result
        switch (gateType) {
            case 'and':
                dot.style.backgroundColor = gateResult === 1 ? 'red' : '#ccc';
                break;
            case 'or':
                dot.style.backgroundColor = gateResult === 1 ? 'yellow' : '#ccc';
                break;
            case 'nor':
                dot.style.backgroundColor = gateResult === 1 ? 'blue' : '#ccc';
                break;
            case 'xor':
                dot.style.backgroundColor = gateResult === 1 ? 'darkgreen' : '#ccc';
                break;
            // Add more cases for other gates if needed
        }
    }

    // Function to update the dots for the Green Triangle based on AND gate result
    function updateGreenDots() {
        const andResult = andButtonStates[0] & andButtonStates[1]; // AND logic gate
        for (const dotId in dotGateMapping) {
            updateDotColorByGate(andResult, dotId);
        }
    }

    // Function to update the dots for other gates based on their results
    function updateOtherDots() {
        // Update dots for OR gate
        const orResult = orButtonStates[0] | orButtonStates[1]; // OR logic gate
        for (const dotId in dotGateMapping) {
            updateDotColorByGate(orResult, dotId);
        }

        // Update dots for NOR gate
        const norResult = !(norButtonStates[0] | norButtonStates[1]); // NOR logic gate
        for (const dotId in dotGateMapping) {
            updateDotColorByGate(norResult, dotId);
        }

        // Update dots for XOR gate
        const xorResult = xorButtonStates[0] ^ xorButtonStates[1]; // XOR logic gate
        for (const dotId in dotGateMapping) {
            updateDotColorByGate(xorResult, dotId);
        }
    }

    // Function to toggle the state of a button for a gate and update the dots
    function toggleButtonAndUpdateDots(gateType, buttonNumber) {
        toggleButton(gateType, buttonNumber);
        switch (gateType) {
            case 'and':
                updateGreenDots();
                break;
            case 'or':
            case 'nor':
            case 'xor':
                updateOtherDots();
                break;
        }
    }

    // Event listeners for AND gate buttons
    document.getElementById('andButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('and', 1);
    });

    document.getElementById('andButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('and', 2);
    });

    // Event listeners for OR gate buttons
    document.getElementById('orButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('or', 1);
    });

    document.getElementById('orButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('or', 2);
    });

    // Event listeners for NOR gate buttons
    document.getElementById('norButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('nor', 1);
    });

    document.getElementById('norButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('nor', 2);
    });

    // Event listeners for XOR gate buttons
    document.getElementById('xorButton1').addEventListener('click', function() {
        toggleButtonAndUpdateDots('xor', 1);
    });

    document.getElementById('xorButton2').addEventListener('click', function() {
        toggleButtonAndUpdateDots('xor', 2);
    });
</script>

<!-- Existing JavaScript code below -->

</body>

</html>
