---
layout: default
title: Login
---

## User Login
// Define variables
$primary-color: #3498db;
$secondary-color: #2ecc71;

// General styles
body {
  font-family: Arial, sans-serif;
  background-color: #ecf0f1;
  color: #333;
  margin: 0;
  padding: 0;
}

h1 {
  color: $primary-color;
}

form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

// Form styles
label {
  display: block;
  margin-bottom: 8px;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
}

input[type="submit"] {
  background-color: $primary-color;
  color: #fff;
  cursor: pointer;
}

// Additional styles for validation
input:valid {
  border-color: $secondary-color;
}

input:invalid {
  border-color: #e74c3c;
}

// Responsive styles
@media (max-width: 600px) {
  form {
    max-width: 100%;
  }
}



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Information Form</title>
</head>
<body>

<h1>User Information Form</h1>

<form action="submit_form.php" method="post">
        <!-- Username -->
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required>
        <br>

<!-- Password -->
<label for="password">Password:</label>
        <input type="password" id="password" name="password" required>
        <br>

<!-- Age -->
<label for="age">Age:</label>
        <input type="number" id="age" name="age" required>
        <br>

<!-- Email -->
<label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <br>

<!-- Submit Button -->
<input type="submit" value="Submit">
    </form>

</body>
</html>
