<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Loan Calculator</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h2>Loan Calculator</h2>
    <form id="loan-form">
      <div>
        <label for="amount">Loan Amount:</label>
        <input type="number" id="amount" required>
      </div>
      <div>
        <label for="interest">Interest Rate (in percentage):</label>
        <input type="number" id="interest" step="0.1" required>
      </div>
      <div>
        <label for="years">Loan Duration (in years):</label>
        <input type="number" id="years" required>
      </div>
      <div>
        <button type="submit" class="btn">Calculate</button>
      </div>
    </form>
    <div id="results" class="hidden">
      <h3>Results</h3>
      <p id="monthly-payment"></p>
      <p id="total-payment"></p>
      <p id="total-interest"></p>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
