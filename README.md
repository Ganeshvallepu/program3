<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Interactive Form with Validation</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f4f4f4;
    }
    .container {
        max-width: 500px;
        margin: 50px auto;
        background: #fff;
        padding: 20px;
        border-radius: 5px;
        box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.1);
    }
    input[type="text"],
    input[type="email"],
    input[type="password"] {
        width: 100%;
        padding: 10px;
        margin: 5px 0 15px 0;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
    }
    input[type="submit"] {
        background-color: #4CAF50;
        color: white;
        padding: 10px 20px;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        transition: background-color 0.3s;
    }
    input[type="submit"]:hover {
        background-color: #45a049;
    }
    .error {
        color: red;
        margin-bottom: 10px;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Interactive Form with Validation</h2>
    <form id="myForm" onsubmit="return validateForm()">
        <label for="name">Name</label>
        <input type="text" id="name" name="name" placeholder="Your name">

        <label for="email">Email</label>
        <input type="email" id="email" name="email" placeholder="Your email">

        <label for="password">Password</label>
        <input type="password" id="password" name="password" placeholder="Your password">

        <input type="submit" value="Submit">
    </form>
</div>

<script>
function validateForm() {
    var name = document.getElementById('name').value.trim();
    var email = document.getElementById('email').value.trim();
    var password = document.getElementById('password').value.trim();

    var nameError = document.getElementById('nameError');
    var emailError = document.getElementById('emailError');
    var passwordError = document.getElementById('passwordError');

    var isValid = true;

    // Reset previous error messages
    nameError.innerHTML = '';
    emailError.innerHTML = '';
    passwordError.innerHTML = '';

    // Validate Name
    if (name === '') {
        nameError.innerHTML = 'Name is required';
        isValid = false;
    }

    // Validate Email
    if (email === '') {
        emailError.innerHTML = 'Email is required';
        isValid = false;
    } else if (!isValidEmail(email)) {
        emailError.innerHTML = 'Please enter a valid email address';
        isValid = false;
    }

    // Validate Password
    if (password === '') {
        passwordError.innerHTML = 'Password is required';
        isValid = false;
    } else if (password.length < 6) {
        passwordError.innerHTML = 'Password must be at least 6 characters long';
        isValid = false;
    }

    return isValid;
}

function isValidEmail(email) {
    var re = /\S+@\S+\.\S+/;
    return re.test(email);
}
</script>

</body>
</html>
