
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sleep Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        #container {
            text-align: center;
            margin-top: 50px;
        }
        #sleep-input {
            padding: 10px;
            font-size: 16px;
        }
        #submit-button {
            background-color: #FF69B4;
            color: white;
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="container">
        <h2>How many hours of sleep did you get last night?</h2>
        <input type="number" id="sleep-input" placeholder="Enter hours of sleep">
        <br><br>
        <button id="submit-button">Submit</button>
        <p id="result"></p>
    </div>

    <script>
        document.getElementById("submit-button").addEventListener("click", function () {
            const hoursOfSleep = parseInt(document.getElementById("sleep-input").value);
            let message;

            if (hoursOfSleep < 7) {
                const statements = [
                    "You should try to get more sleep tonight.",
                    "Getting enough sleep is important for your health.",
                    "Try going to bed earlier tonight.",
                    "Too little sleep makes you irritable."
                ];
                const randomIndex = Math.floor(Math.random() * statements.length);
                message = statements[randomIndex];
            } else if (hoursOfSleep >= 7 && hoursOfSleep <= 9) {
                const facts = [
                    "Did you know that adults should aim for 7-9 hours of sleep per night?",
                    "Great job! Establishing a regular sleep schedule can improve your sleep quality.",
                    "A comfortable mattress and pillow can help you get better sleep.",
                    " A bed that is too soft can actually harm your back, as there is not enough support for your spine."
                ];
                const randomIndex = Math.floor(Math.random() * facts.length);
                message = facts[randomIndex];
            } else {
                message = "Getting too much sleep can also have negative effects on your health. Try to maintain a consistent sleep schedule.";
            }

            document.getElementById("result").textContent = message;
        });
    </script>
</body>
</html>
