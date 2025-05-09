<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GilCoin (GILC) - Memecoin World</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(120deg, #fff0f5, #fef5f9); /* ultra-soft pink */
      color: #333;
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    h1 {
      color: #8e24aa;
    }
    input, button {
      padding: 10px;
      margin: 5px 0;
      width: 100%;
      font-size: 16px;
      border: none;
    }
    button {
      background-color: #8e24aa;
      color: white;
      font-weight: bold;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #6a1b9a;
    }
    .log {
      background: #ffffff;
      color: #000000;
      border: 1px solid #ccc;
      padding: 15px;
      margin-top: 20px;
      height: 200px;
      overflow-y: auto;
    }
    .balance {
      background: #e1bee7;
      padding: 10px;
      margin-bottom: 10px;
    }
    .intro {
      background: #f3e5f5;
      padding: 15px;
      border-left: 5px solid #ce93d8;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>
  <h1>GilCoin (GILC) - Welcome to GilCoin World!</h1>

  <div class="intro">
    <h3>🚀 Launch Message:</h3>
    <p>GilCoin (GILC) is a bold, ridiculous, completely simulated memecoin born out of student genius. It doesn’t run on blockchain — it runs on ambition. With 1,000,000 GILC in circulation, we invite you to explore token transfers, track balances, and learn the magic behind memecoins — all in a safe, offline sandbox.</p>
    <p><strong>GilCoin:</strong> It’s not real, but it’s really smart.</p>
  </div>

  <div class="balance">
    <strong>Supplier Address:</strong> <span id="owner">0xSUPPLIER123</span><br/>
    <strong>Balance:</strong> <span id="ownerBalance">1000000</span> GILC
  </div>

  <h3>Send GilCoin</h3>
  <input type="text" id="recipient" placeholder="Recipient Address" />
  <input type="number" id="amount" placeholder="Amount to Send" />
  <button onclick="sendGilCoin()">Send GILC</button>

  <div class="log" id="log">
    <em>Transaction log will appear here...</em>
  </div>

  <script>
    let balances = {
      '0xSUPPLIER123': 1000000
    };

    function sendGilCoin() {
      const recipient = document.getElementById('recipient').value.trim();
      const amount = parseFloat(document.getElementById('amount').value);
      const log = document.getElementById('log');

      if (!recipient || isNaN(amount) || amount <= 0) {
        alert('Please enter a valid address and amount.');
        return;
      }

      if (!balances['0xSUPPLIER123'] || balances['0xSUPPLIER123'] < amount) {
        alert('Insufficient balance in supplier account.');
        return;
      }

      balances['0xSUPPLIER123'] -= amount;
      balances[recipient] = (balances[recipient] || 0) + amount;

      document.getElementById('ownerBalance').textContent = balances['0xSUPPLIER123'];

      const time = new Date().toLocaleTimeString();
      const entry = document.createElement('div');
      entry.innerHTML = `
        <strong>[${time}]</strong><br>
        Sent <strong>${amount} GILC</strong> to <code>${recipient}</code>.<br>
        New balance of recipient: <strong>${balances[recipient]} GILC</strong><br><br>
      `;
      log.prepend(entry);

      document.getElementById('recipient').value = '';
      document.getElementById('amount').value = '';
    }
  </script>
</body>
</html>
# gilcoin-website
