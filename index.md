---
layout: default
title: Login
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
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

        input[type="text"],
        input[type="password"],
        button {
            padding: 10px; /* Add padding to inputs and button */
            margin: 5px; /* Add margin to inputs and button */
            border-radius: 5px; /* Add border radius */
            border: none; /* Remove default border */
        }

        button {
            background-color: #ff4081; /* Pink button background */
            color: #fff; /* White button text color */
            cursor: pointer; /* Change cursor to pointer on hover */
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ff80ab; /* Lighter pink on hover */
        }

        a {
            color: #ff4081; /* Set link color to pink */
            text-decoration: none; /* Remove underline */
        }

        #error-message {
            margin-top: 10px; /* Add some space above error message */
            color: red; /* Set error message color to red */
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Login</h1>
        <form>
            <label for="uid"><b>Username</b></label><br>
            <input type="text" id="uid" placeholder="Enter Username" name="uid" required><br>
            <label for="password"><b>Password</b></label><br>
            <input type="password" id="password" placeholder="Enter Password" name="password" required><br>
            <button type="button" onclick="login_user()">Log in</button><br>
            <div>
                <span>Need an account? <a href="{{site.baseurl}}/signup">Sign Up</a></span><br>
                <span>Want to delete an account? <a href="{{site.baseurl}}/delete">Delete</a></span>
            </div>
            <div id="error-message"></div>
        </form>
    </div>

    <script>
        function login_user() {
            const uid = document.getElementById("uid").value;
            const password = document.getElementById("password").value;

            const url = "{{site.baseurl}}/api/users/authenticate";
            const authOptions = {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ uid, password })
            };

            fetch(url, authOptions)
                .then(response => {
                    if (!response.ok) {
                        throw new Error('Login error: ' + response.status);
                    }
                    // Redirect or do something upon successful login
                    window.location.href = "{{site.baseurl}}/welcome";
                })
                .catch(error => {
                    document.getElementById("error-message").innerText = error.message;
                });
        }
    </script>
</body>
</html>
