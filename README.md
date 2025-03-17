# Hybrid-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hybrid Trader</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Navbar -->
    <nav class="navbar navbar-dark bg-dark">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">🚀 Hybrid Trader</a>
            <div class="d-flex">
                <span class="text-success me-3">Balance: $<span id="balance">10,000</span></span>
            </div>
        </div>
    </nav>

    <!-- Tabs -->
    <div class="container mt-4">
        <ul class="nav nav-tabs">
            <li class="nav-item"><a class="nav-link active" data-bs-toggle="tab" href="#stocks">Stocks</a></li>
            <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#crypto">Crypto</a></li>
            <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#staking">Staking</a></li>
        </ul>

        <!-- Tab Content -->
        <div class="tab-content mt-3">
            <!-- Stocks Tab -->
            <div class="tab-pane fade show active" id="stocks">
                <!-- ... (same as previous HTML) ... -->
            </div>

            <!-- Crypto Tab -->
            <div class="tab-pane fade" id="crypto">
                <!-- ... (same as previous HTML) ... -->
            </div>

            <!-- Staking Tab -->
            <div class="tab-pane fade" id="staking">
                <!-- ... (same as previous HTML) ... -->
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="app.js"></script>
</body>
</html>
:root {
    --primary: #2d2d2d;
    --secondary: #1a1a1a;
    --profit: #00ff00;
    --loss: #ff0000;
}
body { background: var(--secondary); color: white; }
.card { background: var(--primary); margin: 10px; }
.nav-tabs .nav-link { color: #00ff00 !important; }
#stockChart, #cryptoChart { height: 300px; }
// API Client
const API = axios.create({ baseURL: 'https://your-render-backend-url.onrender.com/api' });

// Stock Trading
async function executeStockOrder(type) {
    const token = localStorage.getItem('token');
    const stock = document.getElementById('stockSelect').value;
    const qty = parseFloat(document.getElementById('stockQty').value);
    
    await API.post('/stocks/order', { symbol: stock, qty, action: type }, {
        headers: { Authorization: `Bearer ${token}` }
    });
    alert('Order placed!');
}

// WebSocket Connection
const ws = new WebSocket('wss://your-render-backend-url.onrender.com');
ws.onmessage = (event) => {
    const data = JSON.parse(event.data);
    updateStockPrices(data.stocks);
    updateCryptoPrices(data.crypto);
};
require('dotenv').config();
const express = require('express');
const { Pool } = require('pg');
const WebSocket = require('ws');
const app = express();
const cors = require('cors');

app.use(cors());
app.use(express.json());

// PostgreSQL
const pool = new Pool({ connectionString: process.env.DB_URL });

// WebSocket Server
const wss = new WebSocket.Server({ port: 8080 });

// API Routes
app.post('/api/stocks/order', async (req, res) => {
    const { symbol, qty, action } = req.body;
    const price = Math.random() * 1000; // Mock price
    await pool.query(
        `INSERT INTO stock_orders (symbol, qty, price, action) 
         VALUES ($1, $2, $3, $4)`,
        [symbol, qty, price, action]
    );
    res.json({ success: true });
});

// Start Server
app.listen(3000, () => console.log('Server running on port 3000'));