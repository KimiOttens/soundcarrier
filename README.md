# soundcarrier
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SoundCarrier</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://unpkg.com/html5-qrcode/minified/html5-qrcode.min.js"></script>
    <style>
        body {
            background: linear-gradient(120deg, #1DB954, #191414);
            color: white;
            font-family: 'Arial', sans-serif;
        }
        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
        }
        .btn-custom {
            background-color: #1DB954;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1.2em;
            border-radius: 30px;
            transition: 0.3s;
        }
        .btn-custom:hover {
            background-color: #1ed760;
        }
        #qr-reader {
            width: 300px;
            height: 300px;
            margin-top: 20px;
            border: 2px solid #1DB954;
            border-radius: 10px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="main-container">
        <h1>Welcome to SoundCarrier</h1>
        <p>Scan a QR code to play the hidden song!</p>
        <button class="btn btn-custom" onclick="startQRScanner()">Scan QR Code</button>
        <div id="qr-reader"></div>
    </div>

    <script>
        function startQRScanner() {
            const qrReader = document.getElementById('qr-reader');
            qrReader.style.display = 'block';

            const html5QrCode = new Html5Qrcode("qr-reader");

            html5QrCode.start({ facingMode: "environment" }, {
                fps: 10,
                qrbox: { width: 250, height: 250 }
            }, qrCodeMessage => {
                alert(`QR Code detected! Redirecting to: ${qrCodeMessage}`);
                window.open(qrCodeMessage, '_blank');
                html5QrCode.stop();
            }).catch(err => {
                console.error("Error starting QR Code scanner:", err);
            });
        }
    </script>
</body>
</html>
