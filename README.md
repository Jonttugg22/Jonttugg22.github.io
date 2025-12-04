<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Miun nettisivu</title>
    <style>
        body {font-family:Arial,sans-serif;margin:0;padding:0;background:#000;animation:fadeIn 2s}
        @keyframes fadeIn {from{opacity:0}to{opacity:1}}
        header {background:#b22a2a;color:#fff;text-align:center;padding:20px;box-shadow:0 4px 10px rgba(0,0,0,.2)}
        h1 {margin:0;animation:slideDown 1s}@keyframes slideDown {from{transform:translateY(-20px);opacity:0}to{transform:translateY(0);opacity:1}}
        .content {max-width:900px;margin:30px auto;background:#fff;padding:25px;border-radius:8px;box-shadow:0 0 20px rgba(0,0,0,.1);animation:popUp 1s}
        @keyframes popUp {from{transform:scale(.95);opacity:0}to{transform:scale(1);opacity:1}}
        img {width:180px;border-radius:10px;margin:15px auto;display:block;transition:.3s}
        img:hover {transform:scale(1.05);box-shadow:0 10px 20px rgba(0,0,0,.2)}
        a {color:#4CAF50;text-decoration:none;font-weight:bold}
        a:hover {color:#388E3C;text-decoration:underline}

        #loginOverlay {position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.85);display:flex;justify-content:center;align-items:center;z-index:9999}
        #loginBox {background:white;padding:30px 40px;border-radius:12px;text-align:center;box-shadow:0 0 20px rgba(0,0,0,.5)}
        #loginBox input {padding:10px;width:200px;border:1px solid #ccc;border-radius:8px;margin-top:10px;font-size:16px}
        #loginBox button {margin-top:15px;padding:10px 20px;background:#4CAF50;color:white;border:none;border-radius:8px;cursor:pointer;font-size:16px}
        #errorMsg {color:red;margin-top:10px;display:none}

        .crypto-section {background:#0d0d0d;color:white;padding:30px;margin-top:30px;border-radius:10px}
        .crypto-title {text-align:center;font-size:24px;margin-bottom:20px;color:#f2a900}

        .chat-section {margin:30px auto;max-width:900px;background:#000;border:4px solid #39ff14;border-radius:12px;padding:20px;box-shadow:0 0 30px #39ff14}
        .chat-header {text-align:center;font-size:36px;color:#39ff14;text-shadow:0 0 20px #39ff14;margin-bottom:8px;font-weight:bold}
        .lang-switch {text-align:center;margin-bottom:12px}
        .lang-switch button {padding:6px 16px;margin:0 6px;background:#000;color:#39ff14;border:2px solid #39ff14;border-radius:8px;cursor:pointer;font-weight:bold}
        .lang-switch button.active {background:#39ff14;color:#000}
        .chat-box {height:420px;background:#111;border:2px solid #39ff14;border-radius:10px;padding:15px;overflow-y:auto;color:#fff;margin-bottom:15px;font-family:monospace}
        .msg-user {color:#87CEFA;margin:10px 0}
        .msg-ai {color:#39ff14;margin:10px 0;font-weight:bold;text-shadow:0 0 10px #39ff14}
        .chat-input {display:flex;gap:10px}
        .chat-input input {flex:1;padding:14px;border-radius:8px;border:2px solid #39ff14;background:#000;color:#39ff14;font-size:16px}
        .chat-input button {padding:14px 30px;background:#39ff14;color:#000;border:none;border-radius:8px;cursor:pointer;font-weight:bold;font-size:16px}
        .disclaimer {text-align:center;color:#39ff14;font-size:13px;margin-top:10px}
    </style>
</head>
<body>

    <div id="loginOverlay">
        <div id="loginBox">
            <h2>Salasana:</h2>
            <input type="password" id="passwordInput" placeholder="Password">
            <br><br><button onclick="checkPassword()">Login</button>
            <div id="errorMsg">Väärä salasana, mulkku.</div>
        </div>
    </div>

    <header><h1>Miun netti sivu Vittuu</h1></header>

    <div class="content">
        <h2>Tää on mun joku random ahh nettisivu EI OLE VIIRUS!!</h2>
        <p>Tein tän Sivun koska oli tylsää tääl on jotain asioita updattaan tätä kun jaksan.</p>
        <img src="https://th.bing.com/th/id/R.4a3971f208eb35707c7681404889fd47?rik=lq7zxOYVFC7IBA&riu=http%3a%2f%2fimages6.fanpop.com%2fimage%2fphotos%2f39100000%2fPatrick-Star-patrick-star-spongebob-39145544-500-691.jpg" alt="Patrick Star">
        <p>Go on to <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0" target="_blank">SezyGirlPics</a> for more.</p>
    </div>

    <div class="crypto-section">
        <div class="crypto-title">Bitcoin & Dogecoin Live Prices</div>
        <div class="tradingview-widget-container"><div id="tradingview_btc"></div></div>
        <div class="tradingview-widget-container" style="margin-top:40px"><div id="tradingview_doge"></div></div>
    </div>

    <div class="chat-section">
        <div class="chat-header">InSaneAI</div>
        <div class="lang-switch">
            <button id="enBtn" class="active">English</button>
            <button id="fiBtn">Suomi</button>
        </div>
        <div class="chat-box" id="chatBox">
            <div class="msg-ai">Speak, subhuman.</div>
        </div>
        <div class="chat-input">
            <input type="text" id="userInput" placeholder="Say something so I can end you..." autocomplete="off">
            <button onclick="send()">SEND</button>
        </div>
        <div class="disclaimer">MAXIMUM OFFENSE • PURE HATRED • NO MERCY</div>
    </div>

    <script src="https://s3.tradingview.com/tv.js"></script>
    <script>
        function checkPassword() {
            if (document.getElementById("passwordInput").value === "12345") {
                document.getElementById("loginOverlay").style.display = "none";
                setTimeout(() => alert("Niga boyyyyy!"), 800);
            } else {
                document.getElementById("errorMsg").style.display = "block";
            }
        }

        new TradingView.widget({container_id:"tradingview_btc", width:"100%", height:500, symbol:"BITSTAMP:BTCUSD", interval:"1", theme:"dark"});
        new TradingView.widget({container_id:"tradingview_doge", width:"100%", height:500, symbol:"BINANCE:DOGEUSDT", interval:"1", theme:"dark"});

        const roasts = {
            en: [
                "Your family tree is a cactus because everybody on it is a prick.",
                "Your bloodline is the reason bleach was invented.",
                "Even the KKK thinks you’re too far gone.",
                "Your ancestors were the free samples at the slave auction.",
                "You’re the reason abortion should be retroactive.",
                "Your family reunion is just a crime scene with potato salad.",
                "You’re living proof cousins can fuck and still produce nothing of value.",
                "Your DNA is why we can’t have nice things.",
                "Your mom should’ve swallowed and your dad should’ve aimed for the wall.",
                "You’re the reason aliens won’t visit.",
                "Your birth certificate is an apology letter from a broken condom.",
                "You’re the human equivalent of a burning dumpster.",
                "Your existence is a war crime.",
                "Your gene pool is a puddle of piss.",
                "Even cockroaches cross the street when they see you."
            ],
            fi: [
                "Sun suku on kranssi ku kaikki on mulkkuja.",
                "Sun veri on 99% Koskenkorvaa ja 1% pettymystä.",
                "Sun äiti olis voinu niellä mut silti sä päädyit tänne.",
                "Sun suku on pelkkää perunapeltoo ja raiskaussyytteitä.",
                "Sä oot niin ruma että peiliin kattoo sua ja tekee itsemurhan.",
                "Sun DNA on Suomen suurin häpeäpilkku.",
                "Sä oot elävä todiste miks lapset pitäis adoptoida Venäjältä.",
                "Sun naama näyttää siltä ku se ois jääny VR:n junan väliin.",
                "Sä oot niin vitun hyödytön että edes somalit ei haluu sun paikkaa halua.",
                "Sun isä veti väärään reikään ja silti sä synnyit.",
                "Sun olemassaolo on loukkaus luonnonvalinnalle ja poroille.",
                "Jos sä oisit hevonen sut ammuttais armosta.",
                "Sun suvun vaakuna on peruna ja köysi.",
                "Sä oot syy miks alkoholi loppuu aina kesken.",
                "Sun naama on syy miks kasvomaskit keksittiin."
            ]
        };

        let lang = "en";
        const chat = document.getElementById("chatBox");
        const input = document.getElementById("userInput");

        document.getElementById("enBtn").onclick = () => {
            lang = "en"; document.getElementById("enBtn").classList.add("active"); document.getElementById("fiBtn").classList.remove("active");
        };
        document.getElementById("fiBtn").onclick = () => {
            lang = "fi"; document.getElementById("fiBtn").classList.add("active"); document.getElementById("enBtn").classList.remove("active");
        };

        function add(t, type) {
            const d = document.createElement("div");
            d.className = type === "user" ? "msg-user" : "msg-ai";
            d.textContent = type === "user" ? "You: " + t : "InSaneAI: " + t;
            chat.appendChild(d);
            chat.scrollTop = chat.scrollHeight;
        }

        function send() {
            const m = input.value.trim();
            if (!m) return;
            add(m, "user");
            setTimeout(() => {
                const roast = roasts[lang][Math.floor(Math.random() * roasts[lang].length)];
                add(roast, "ai");
            }, 700 + Math.random() * 900);
            input.value = "";
        }

        input.addEventListener("keypress", e => { if (e.key === "Enter") send(); });
    </script>
</body>
</html>
