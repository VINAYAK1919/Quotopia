<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Quotopia - Infinite Quotes</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f7f9fc;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      padding: 20px;
      text-align: center;
    }
    #quote {
      font-size: 1.6rem;
      color: #333;
      margin-bottom: 20px;
      max-width: 600px;
    }
    #author {
      font-size: 1.2rem;
      color: #666;
      margin-bottom: 30px;
    }
    button {
      padding: 10px 20px;
      font-size: 1.2rem;
      background: #28a745;
      border: none;
      border-radius: 5px;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #218838;
    }
  </style>
</head>
<body>
  <h1>Welcome to Quotopia</h1>
  <div id="quote">Loading quote...</div>
  <div id="author"></div>
  <button onclick="getQuote()">Get New Quote</button>

  <script>
    async function getQuote() {
      try {
        const response = await fetch('https://zenquotes.io/api/random');
        const data = await response.json();
        document.getElementById('quote').textContent = "${data[0].q}";
        document.getElementById('author').textContent = — ${data[0].a};
      } catch (error) {
        document.getElementById('quote').textContent = "Oops! Couldn't fetch a quote.";
        document.getElementById('author').textContent = "";
      }
    }

    // Load one quote on page load
    getQuote();
  </script>
</body>
</html>