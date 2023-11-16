<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toggle Buttons</title>
    <link rel="stylesheet" type="text/css" href="Nighthawkpages-styles.scss">
</head>

<body>
    <button id="Gate1">0</button>
    <button id="Gate2">0</button>

<script>
        // Wrap the code in a window.onload function
        window.onload = function () {
            // Get the button element by its id
            var button1 = document.getElementById("Gate1");

            // Initialize a variable to store the current state
            var g1 = false;

            // Add a click event listener to the button
            button1.addEventListener("click", function () {
                // Toggle the value between true and false
                g1 = !g1;

                // Update the button text to reflect the current value
                button1.textContent = g1 ? "1" : "0";

                // Log the current value to the console (you can replace this with your own logic)
                console.log("Gate1 Current value:", g1);
            });

            // Get the button element by its id
            var button2 = document.getElementById("Gate2");

            // Initialize a variable to store the current state
            var g2 = false;

            // Add a click event listener to the button
            button2.addEventListener("click", function () {
                // Toggle the value between true and false
                g2 = !g2;

                // Update the button text to reflect the current value
                button2.textContent = g2 ? "1" : "0";

                // Log the current value to the console (you can replace this with your own logic)
                console.log("Gate2 Current value:", g2);
            });
        };
    </script>
</body>

</html>

