---
layout: default
title: Index
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resting Heart Rate Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #fce4ec; /* Light pink background */
            color: #333; /* Dark text color */
        }

        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #fff; /* White container background */
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Shadow effect */
            text-align: center;
        }

        input[type="number"] {
            width: 100px;
            padding: 10px;
            margin: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        button {
            background-color: #ff4081; /* Pink button background */
            color: #fff; /* White button text color */
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ff80ab; /* Lighter pink on hover */
        }

        p#result {
            font-size: 18px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Resting Heart Rate Game</h1>
        <p>Guess the average resting heart rate for your age!</p>
        <label for="ageInput">Enter your age:</label>
        <input type="number" id="ageInput" min="1" max="120">
        <button onclick="playGame()">Guess</button>
        <p id="result"></p>
    </div>

    <script>
        function playGame() {
            var age = parseInt(document.getElementById('ageInput').value);
            var averageHeartRate = calculateAverageHeartRate(age);
            var userGuess = parseInt(prompt("Guess the average resting heart rate for your age:"));
            
            var resultParagraph = document.getElementById('result');
            if (userGuess === averageHeartRate) {
                resultParagraph.textContent = "Congratulations! You guessed it right!";
            } else {
                resultParagraph.textContent = "Sorry, the average resting heart rate for your age is " + averageHeartRate + " bpm.";
            }
        }

        // Function to calculate average resting heart rate based on age
        function calculateAverageHeartRate(age) {
            if (age >= 0 && age <= 10) {
                return 100;
            } else if (age >= 11 && age <= 20) {
                return 90;
            } else if (age >= 21 && age <= 30) {
                return 80;
            } else if (age >= 31 && age <= 40) {
                return 75;
            } else if (age >= 41 && age <= 50) {
                return 70;
            } else if (age >= 51 && age <= 60) {
                return 65;
            } else if (age >= 61 && age <= 70) {
                return 60;
            } else if (age >= 71 && age <= 80) {
                return 65;
            } else if (age >= 81 && age <= 90) {
                return 70;
            } else if (age >= 91 && age <= 100) {
                return 75;
            } else {
                return 80; // Default value
            }
        }
    </script>
</body>
</html>
