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
