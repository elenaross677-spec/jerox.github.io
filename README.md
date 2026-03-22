# franchiseopportunities.us.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jerox Invest</title>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: #0f172a;
  color: white;
}

/* Layout */
.container {
  display: flex;
}

/* Sidebar */
.sidebar {
  width: 220px;
  background: #020617;
  height: 100vh;
  padding: 20px;
}

.sidebar h2 {
  color: #22c55e;
}

.sidebar button {
  width: 100%;
  margin: 10px 0;
  padding: 10px;
  background: #22c55e;
  border: none;
  cursor: pointer;
}

/* Main */
.main {
  flex: 1;
  padding: 20px;
}

/* Topbar */
.topbar {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

/* Cards */
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}

.card {
  background: #020617;
  padding: 20px;
  border-radius: 10px;
}

/* Buttons */
.btn {
  background: #22c55e;
  padding: 10px;
  border: none;
  cursor: pointer;
  margin-top: 10px;
}

/* Input */
input {
  width: 100%;
  padding: 10px;
  margin-top: 10px;
}

/* Auth */
#auth {
  text-align: center;
  margin-top: 100px;
}
</style>
</head>

<body>

<!-- AUTH -->
<div id="auth">
  <h1>Jerox Invest</h1>
  <input type="email" id="email" placeholder="Email"><br>
  <input type="password" id="password" placeholder="Password"><br>
  <button class="btn" onclick="signup()">Sign Up</button>
  <button class="btn" onclick="login()">Login</button>
</div>

<!-- DASHBOARD -->
<div class="container" id="dashboard" style="display:none;">

  <!-- SIDEBAR -->
  <div class="sidebar">
    <h2>Jerox</h2>
    <button onclick="showSection('home')">Dashboard</button>
    <button onclick="showSection('invest')">Invest</button>
    <button onclick="showSection('stake')">Stake</button>
    <button onclick="showSection('deposit')">Deposit</button>
    <button onclick="logout()">Logout</button>
  </div>

  <!-- MAIN -->
  <div class="main">

    <!-- TOP -->
    <div class="topbar">
      <h3 id="userEmail"></h3>
      <h3 id="balance">Balance: 0 BTC</h3>
    </div>

    <!-- HOME -->
    <div id="home" class="section">
      <div class="cards">
        <div class="card">
          <h3>Total Balance</h3>
          <p id="balanceCard">0 BTC</p>
        </div>

        <div class="card">
          <h3>Active Plan</h3>
          <p id="plan">None</p>
        </div>

        <div class="card">
          <h3>Wallet Address</h3>
          <input id="btcAddress" readonly>
          <button class="btn" onclick="copyAddress()">Copy</button>
        </div>
      </div>
    </div>

    <!-- INVEST -->
    <div id="invest" class="section" style="display:none;">
      <h2>Investment Plans</h2>
      <div class="cards">
        <div class="card">
          <h3>$400 Plan</h3>
          <button class="btn" onclick="invest(400)">Invest</button>
        </div>
        <div class="card">
          <h3>$800 Plan</h3>
          <button class="btn" onclick="invest(800)">Invest</button>
        </div>
        <div class="card">
          <h3>$1200 Plan</h3>
          <button class="btn" onclick="invest(1200)">Invest</button>
        </div>
      </div>
    </div>

    <!-- STAKE -->
    <div id="stake" class="section" style="display:none;">
      <h2>Staking</h2>
      <div class="cards">
        <div class="card">
          <h3>$300 / 14 days</h3>
          <button class="btn" onclick="stake(300,14)">Stake</button>
        </div>
        <div class="card">
          <h3>$200 / 28 days</h3>
          <button class="btn" onclick="stake(200,28)">Stake</button>
        </div>
      </div>
    </div>

    <!-- DEPOSIT -->
    <div id="deposit" class="section" style="display:none;">
      <h2>Deposit BTC</h2>
      <input id="btcAddress2" readonly>
      <button class="btn" onclick="copyAddress()">Copy Address</button>
      <br><br>
      <img id="qr">
    </div>

  </div>
</div>

<script>
function showSection(id) {
  document.querySelectorAll(".section").forEach(sec => sec.style.display = "none");
  document.getElementById(id).style.display = "block";
}

function copyAddress() {
  let input = document.getElementById("btcAddress") || document.getElementById("btcAddress2");
  input.select();
  document.execCommand("copy");
  alert("Copied!");
}

function invest(amount) {
  document.getElementById("plan").innerText = "$" + amount + " Plan Active";
}

function stake(amount, days) {
  document.getElementById("plan").innerText = "Staked $" + amount + " for " + days + " days";
}
</script>

</body>
</html>
