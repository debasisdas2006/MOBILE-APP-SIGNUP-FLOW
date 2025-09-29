<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Signup Page</title>
  <style>
    body {font-family: Arial, sans-serif; background-color: #eef2f3; display: flex; justify-content: center; align-items: center; height: 100vh;}
    .container {background: white; padding: 25px; border-radius: 12px; box-shadow: 0 0 15px rgba(0,0,0,0.1); width: 340px;}
    h2 {text-align: center; margin-bottom: 15px;}
    input, button, select {width: 100%; padding: 10px; margin: 8px 0; border-radius: 5px; border: 1px solid #ccc; font-size: 14px;}
    button {background-color: #4CAF50; color: white; border: none; cursor: pointer; font-weight: bold;}
    button:hover {background-color: #45a049;}
    .footer {text-align: center; font-size: 14px; margin-top: 12px;}
    .error {color: red; font-size: 13px; display: none;}
  </style>
</head>
<body>
  <div class="container">
    <h2>Create Your Account</h2>
    <form id="signupForm">
      <input type="text" id="name" placeholder="Full Name" required>
      <input type="email" id="email" placeholder="Email Address" required>
      <input type="tel" id="phone" placeholder="Phone Number" pattern="[0-9]{10}">
      <select id="interest">
        <option value="">Select Interest</option>
        <option value="sports">Sports</option>
        <option value="music">Music</option>
        <option value="tech">Technology</option>
      </select>
      <input type="password" id="password" placeholder="Password" required>
      <input type="password" id="confirmPassword" placeholder="Confirm Password" required>
      <div class="error" id="passwordError">Passwords do not match</div>
      <label><input type="checkbox" id="terms" required> I agree to the Terms</label>
      <button type="submit">Sign Up</button>
    </form>
    <div class="footer">Already have an account? <a href="#">Login</a></div>
  </div>  <script>
    document.getElementById("signupForm").addEventListener("submit", function(event) {
      event.preventDefault();
      let password = document.getElementById("password").value;
      let confirmPassword = document.getElementById("confirmPassword").value;
      let email = document.getElementById("email").value;
      let errorDiv = document.getElementById("passwordError");

      // Email validation
      let emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailPattern.test(email)) {
        alert("Enter a valid email address.");
        return;
      }

      // Password match validation
      if (password !== confirmPassword) {
        errorDiv.style.display = "block";
        return;
      } else {
        errorDiv.style.display = "none";
      }

      if (password.length < 6) {
        alert("Password must be at least 6 characters long.");
        return;
      }

      alert("Account created successfully! Welcome, " + document.getElementById("name").value + "!");
      this.reset();
    });
  </script></body>
</html>
