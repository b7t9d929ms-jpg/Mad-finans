<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mad Finans Pro</title>

  <style>
    body {
      margin: 0;
      font-family: Arial;
      background: #0b0f1a;
      color: white;
    }

    header {
      padding: 20px;
      text-align: center;
      background: #11182a;
      font-size: 22px;
      font-weight: bold;
      color: #00d4ff;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      padding: 20px;
    }

    .card {
      background: #11182a;
      padding: 15px;
      border-radius: 12px;
      border: 1px solid #1f2a44;
      text-align: center;
    }

    .price {
      font-size: 22px;
      color: #00d4ff;
      margin-top: 10px;
    }

    .news {
      padding: 20px;
    }

    .news-item {
      background: #11182a;
      margin-bottom: 10px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #1f2a44;
    }

    .chart {
      padding: 20px;
    }

    iframe {
      width: 100%;
      height: 400px;
      border: none;
      border-radius: 10px;
    }

    .alert {
      text-align: center;
      padding: 10px;
      background: #1a2a44;
      margin: 10px;
      border-radius: 8px;
      color: #00ff99;
    }
  </style>
</head>

<body>

<header>📊 MAD FİNANS PRO DASHBOARD</header>

<div class="alert">
  🔔 Sistem aktif - fiyatlar 10 saniyede güncellenir
</div>

<div class="grid">
  <div class="card">
    <h3>Bitcoin</h3>
    <div id="btc" class="price">...</div>
  </div>

  <div class="card">
    <h3>Ethereum</h3>
    <div id="eth" class="price">...</div>
  </div>

  <div class="card">
    <h3>Solana</h3>
    <div id="sol" class="price">...</div>
  </div>
</div>

<div class="chart">
  <h2 style="text-align:center;">📈 Bitcoin Grafik</h2>
  <iframe src="https://www.tradingview.com/embed-widget/mini-symbol-overview/?symbol=BINANCE:BTCUSDT"></iframe>
</div>

<div class="news">
  <h2>📰 Kripto Haberleri</h2>

  <div class="news-item">📌 Bitcoin yükseliş trendine girdi</div>
  <div class="news-item">📌 Ethereum ağ güncellemesi geliyor</div>
  <div class="news-item">📌 Altcoin piyasasında hareketlilik</div>
</div>

<script>
async function getPrices() {
  try {
    const res = await fetch("https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana&vs_currencies=usd");
    const data = await res.json();

    document.getElementById("btc").innerHTML = "$ " + data.bitcoin.usd;
    document.getElementById("eth").innerHTML = "$ " + data.ethereum.usd;
    document.getElementById("sol").innerHTML = "$ " + data.solana.usd;
  } catch (e) {}
}

getPrices();
setInterval(getPrices, 10000);
</script>

</body>
</html>
