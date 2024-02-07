---
layout: default
title: Index
---
<div class="login-container">


<form action="javascript:login_user()">
    <label for="uid"><b>Username</b></label>
    <input type="text" id="uid" placeholder="Enter Username" name="uid" required>
    <label for="password"><b>Password</b></label>
    <input type="password" id="password" placeholder="Enter Password" name="password" required>
    <button class='button'>Log in</button>
    <div>
    <span class="psw">Need an account? <a href="{{site.baseurl}}/signup"> Sign Up</a></span>
    <span class="psw2">Want to delete an account? <a href="{{site.baseurl}}/delete"> Delete</a></span>
    </div>
    <div>
    <div id="error-message" style="color: red;"></div>
    <!-- <span class="psw">Want to delete? <a href="{{site.baseurl}}/delete"> Delete</a></span> -->
    </div>

</form>
<script type="module">
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    function login_user(){
        const url = uri + '/api/users/authenticate';
        const body = {
            uid: document.getElementById("uid").value,
            password: document.getElementById("password").value,
        };
        const authOptions = {
            ...options, 
            method: 'POST', 
            cache: 'no-cache', 
            body: JSON.stringify(body)
        };
        fetch(url, authOptions)
        .then(response => {
            if (!response.ok) {
                const errorMsg = 'Login error: ' + response.status;
                console.log(errorMsg);
                document.getElementById("error-message").innerText = errorMsg; // Display error on the screen
                return;
            }
            window.location.href = "{{site.baseurl}}/snake";
        })
        .catch(err => {
            console.error(err);
        });
    }
    window.login_user = login_user;

</script>