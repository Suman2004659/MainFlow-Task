<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Registration & Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            height: 100vh;
            justify-content: center;
            align-items: center;
            background-color: #f0f2f5;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 350px;
        }
        .container h2 { text-align: center; }
        .form-group { margin-bottom: 15px; }
        label { display: block; margin-bottom: 5px; }
        input[type="text"], input[type="email"], input[type="password"] {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button { 
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover { background-color: #45a049; }
        .link { text-align: center; margin-top: 10px; }
    </style>
</head>
<body>
    <div class="container" id="registerContainer">
        <h2>Register</h2>
        <form action="register.php" method="POST">
            <label>Username:</label>
            <input type="text" name="username" required>
        
            <label>Email:</label>
            <input type="email" name="email" required>
        
            <label>Password:</label>
            <input type="password" name="password" required>
        
            <button type="submit">Register</button>
        </form>        
        <div class="link">
            <a href="javascript:void(0)" onclick="showLoginPage()">Already have an account? Login here</a>
        </div>
    </div>

    <div class="container" id="loginContainer" style="display:none;">
        <h2>Login</h2>
        <form action="login.php" method="POST">
            <label>Username:</label>
            <input type="text" name="username" required>
        
            <label>Password:</label>
            <input type="password" name="password" required>
        
            <button type="submit" href="success.html">Login</button>
        </form>         
        <div class="link">
            <a href="javascript:void(0)" onclick="showRegisterPage()">Don't have an account? Register here</a>
        </div>
    </div>

    <script>
        let userData = {};

        function registerUser() {
            const username = document.getElementById("username").value;
            const email = document.getElementById("email").value;
            const password = document.getElementById("password").value;

            if (username && email && password) {
                userData = { username, email, password };
                alert("Registration Successful!");
                showLoginPage();
            } else {
                alert("Please fill all the fields.");
            }
        }

        function loginUser() {
            const loginUsername = document.getElementById("loginUsername").value;
            const loginPassword = document.getElementById("loginPassword").value;

            if (loginUsername === userData.username && loginPassword === userData.password) {
                alert("Login Successful! Welcome " + userData.username);
            } else {
                alert("Invalid username or password.");
            }
        }

        function showLoginPage() {
            document.getElementById("registerContainer").style.display = "none";
            document.getElementById("loginContainer").style.display = "block";
        }

        function showRegisterPage() {
            document.getElementById("registerContainer").style.display = "block";
            document.getElementById("loginContainer").style.display = "none";
        }
    </script>
</body>
</html>
