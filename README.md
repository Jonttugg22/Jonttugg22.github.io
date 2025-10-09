<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Miun nettisivu</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #000000;
            animation: fadeIn 2s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        header {
            background-color: #b22a2a;
            color: rgb(255, 255, 255);
            text-align: center;
            padding: 20px 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        h1 {
            margin: 0;
            animation: slideDown 1s ease-out;
        }

        @keyframes slideDown {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .content {
            max-width: 900px;
            margin: 30px auto;
            background-color: #ffffff;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
            animation: popUp 1s ease-in-out;
        }

        @keyframes popUp {
            from { transform: scale(0.95); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        img {
            width: 180px;
            height: auto;
            display: block;
            margin: 15px auto;
            border-radius: 10px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        img:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        a {
            color: #4CAF50;
            text-decoration: none;
            font-weight: bold;
            transition: color 0.3s ease;
        }

        a:hover {
            color: #388E3C;
            text-decoration: underline;
        }

        #loginOverlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.85);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        #loginBox {
            background-color: white;
            padding: 30px 40px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 0 20px rgba(0,0,0,0.5);
            animation: fadeIn 0.5s ease;
        }

        #loginBox input {
            padding: 10px;
            width: 200px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 16px;
            margin-top: 10px;
            outline: none;
        }

        #loginBox button {
            margin-top: 15px;
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
        }

        #loginBox button:hover {
            background-color: #388E3C;
        }

        #errorMsg {
            color: red;
            margin-top: 10px;
            display: none;
        }

        /* Crypto chart section */
        .crypto-section {
            background-color: #0d0d0d;
            color: white;
            padding: 30px;
            margin-top: 30px;
            border-radius: 10px;
        }

        .crypto-title {
            text-align: center;
            font-size: 24px;
            margin-bottom: 20px;
            color: #f2a900;
        }

        .chart-container {
            display: flex;
            flex-direction: column;
            gap: 40px;
        }

        .tradingview-widget-container {
            height: 500px;
        }

    </style>
</head>
<body>

    <!-- Login Overlay -->
    <div id="loginOverlay">
        <div id="loginBox">
            <h2>Salasana:</h2>
            <input type="password" id="passwordInput" placeholder="Password">
            <br>
            <button onclick="checkPassword()">Sivulle</button>
            <div id="errorMsg">Väärä Salasanan. Nisti Yritä uusiks.</div>
        </div>
    </div>

    <header>
        <h1>Miun netti sivu Vittuu</h1>
    </header>

    <div class="content">
        <h2>Tää on mun joku random ahh nettisivu EI OLE VIIRUS!!</h2>
        <p>Tein tän Sivun koska oli tylsää tääl on jotain asioita updattaan tätä kun jaksan.</p>

        <img src="https://th.bing.com/th/id/R.4a3971f208eb35707c7681404889fd47?rik=lq7zxOYVFC7IBA&riu=http%3a%2f%2fimages6.fanpop.com%2fimage%2fphotos%2f39100000%2fPatrick-Star-patrick-star-spongebob-39145544-500-691.jpg&ehk=OnW2FLCZEKRKil2RjMS5RxWPyFjvmDr1RUxTRMrkZUw%3d&risl=&pid=ImgRaw&r=0" alt="Patrick Star">

        <p>Go on to <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0" target="_blank">SezyGirlPics</a> for more 👦🏿🍗🏀.</p>
    </div>

    <!-- Crypto Chart Section -->
    <div class="crypto-section">
        <div class="crypto-title">Crypto Osa</div>
        <div class="chart-container">
            <!-- Bitcoin -->
            <div class="tradingview-widget-container">
                <div id="tradingview_btc"></div>
                <script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>
                <script type="text/javascript">
                    new TradingView.widget({
                        "width": "100%",
                        "height": 500,
                        "symbol": "BITSTAMP:BTCUSD",
                        "interval": "1",
                        "theme": "dark",
                        "style": "1",
                        "locale": "en",
                        "toolbar_bg": "#000000",
                        "enable_publishing": false,
                        "hide_legend": false,
                        "save_image": false,
                        "container_id": "tradingview_btc"
                    });
                </script>
            </div>

            <!-- Dogecoin -->
            <div class="tradingview-widget-container">
                <div id="tradingview_doge"></div>
                <script type="text/javascript">
                    new TradingView.widget({
                        "width": "100%",
                        "height": 500,
                        "symbol": "BINANCE:DOGEUSDT",
                        "interval": "1",
                        "theme": "dark",
                        "style": "1",
                        "locale": "en",
                        "toolbar_bg": "#000000",
                        "enable_publishing": false,
                        "hide_legend": false,
                        "save_image": false,
                        "container_id": "tradingview_doge"
                    });
                </script>
            </div>
        </div>
    </div>

    <script>
        // Password protection
        const correctPassword = "12345"; // change this if you want

        function checkPassword() {
            const input = document.getElementById("passwordInput").value;
            const errorMsg = document.getElementById("errorMsg");

            if (input === correctPassword) {
                document.getElementById("loginOverlay").style.display = "none";
                setTimeout(() => {
                    alert("Niga boyyyyy!");
                }, 1000);
            } else {
                errorMsg.style.display = "block";
            }
        }

        // Disable right-click
        document.addEventListener("contextmenu", event => event.preventDefault());
    </script>

</body>
</html>
