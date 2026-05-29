# Maram-Project
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Premium Platform</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">

<style>
:root {
  --bg: #f7f9fa;
  --card: #ffffff;
  --text: #1c1d1f;
  --muted: #6a6f73;
  --primary: #a435f0;
}

body.dark {
  --bg: #121212;
  --card: #1e1e1e;
  --text: #ffffff;
  --muted: #aaaaaa;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Inter', sans-serif;
}

body {
  background: var(--bg);
  color: var(--text);
  transition: 0.3s;
}

.header {
  display: flex;
  justify-content: space-between;
  padding: 15px 30px;
  background: #1c1d1f;
  color: white;
}

.toggle {
  cursor: pointer;
}

/* Login */
.login {
  max-width: 350px;
  margin: 100px auto;
  background: var(--card);
  padding: 30px;
  border-radius: 10px;
  text-align: center;
  animation: fade 0.8s;
}

.login input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
}

.btn {
  background: var(--primary);
  color: white;
  border: none;
  padding: 12px;
  cursor: pointer;
  width: 100%;
  border-radius: 6px;
  transition: 0.2s;
}

.btn:hover {
  transform: scale(1.03);
}

/* Dashboard */
.dashboard {
  display: none;
}

.hero {
  text-align: center;
  padding: 50px 20px;
  animation: fade 1s;
}

.pricing {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
  padding: 20px;
}

.card {
  background: var(--card);
  padding: 25px;
  border-radius: 10px;
  text-align: center;
  transition: 0.3s;
  animation: fadeUp 0.6s;
}

.card:hover {
  transform: translateY(-5px);
}

.price {
  font-size: 30px;
  margin: 10px 0;
  color: var(--primary);
}

.footer {
  text-align: center;
  padding: 20px;
  margin-top: 40px;
  background: #1c1d1f;
  color: white;
}

@keyframes fade {
  from {opacity: 0;}
  to {opacity: 1;}
}

@keyframes fadeUp {
  from {opacity: 0; transform: translateY(20px);}
  to {opacity: 1; transform: translateY(0);}
}
</style>
</head>

<body>

<div class="header">
  <div>MyPlatform</div>
  <div class="toggle" onclick="toggleDark()">🌙</div>
</div>

<!-- Login -->
<div class="login" id="loginBox">
  <h2>Login</h2>
  <input type="text" id="username" placeholder="Username">
  <input type="password" id="password" placeholder="Password">
  <button class="btn sound-btn" onclick="login()">Login</button>
  <p id="error" style="color:red;"></p>
</div>

<!-- Dashboard -->
<div class="dashboard" id="dashboard">

  <div class="hero">
    <h1>Welcome, Maram 👋</h1>
    <p>Select your plan</p>
  </div>

  <div class="pricing">

    <div class="card">
      <h3>Starter</h3>
      <div class="price">$10</div>
      <button class="btn sound-btn" onclick="pay()">Pay</button>
    </div>

    <div class="card">
      <h3>Standard</h3>
      <div class="price">$50</div>
      <button class="btn sound-btn" onclick="pay()">Pay</button>
    </div>

    <div class="card">
      <h3>Premium</h3>
      <div class="price">$100</div>
      <button class="btn sound-btn" onclick="pay()">Pay</button>
    </div>

    <div class="card">
      <h3>Ultimate</h3>
      <div class="price">$250</div>
      <button class="btn sound-btn" onclick="pay()">Pay</button>
    </div>

  </div>

  <div class="footer">
    Secure payments via PayPal
  </div>

</div>

<!-- SOUND FILES -->
<audio id="hoverSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3"></audio>
<audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-09.mp3"></audio>

<script>
function login() {
  let user = document.getElementById("username").value;
  let pass = document.getElementById("password").value;

  if (user === "Maram" && pass === "maram1234") {
    document.getElementById("loginBox").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
  } else {
    document.getElementById("error").innerText = "Wrong username or password";
  }
}

function pay() {
  playClick();
  setTimeout(() => {
    window.location.href = "https://www.paypal.com";
  }, 150);
}

function toggleDark() {
  document.body.classList.toggle("dark");
}

/* SOUND LOGIC */
const hoverSound = document.getElementById("hoverSound");
const clickSound = document.getElementById("clickSound");

function playHover() {
  hoverSound.currentTime = 0;
  hoverSound.play();
}

function playClick() {
  clickSound.currentTime = 0;
  clickSound.play();
}

document.querySelectorAll(".sound-btn").forEach(btn => {
  btn.addEventListener("mouseenter", playHover);
  btn.addEventListener("click", playClick);
});
</script>

</body>
</html>
