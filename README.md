<!DOCTYPE html>
<html lang="fi">
<head>
    <meta charset="UTF-8">
    <title>Miun Sivusto</title>
    <style>
        *{margin:0;padding:0;box-sizing:border-box}
        body{background:#000;color:#fff;font-family:Arial,sans-serif;min-height:100vh;display:flex;flex-direction:column}
        
        /* Login screen */
        #loginScreen{position:fixed;top:0;left:0;width:100%;height:100%;background:#000;display:flex;flex-direction:column;justify-content:center;align-items:center;z-index:9999}
        #loginScreen h1{color:#39ff14;font-size:50px;margin-bottom:30px;text-shadow:0 0 20px #39ff14}
        #loginScreen input{padding:15px;width:300px;font-size:20px;border:3px solid #39ff14;background:#000;color:#39ff14;border-radius:10px;text-align:center}
        #loginScreen button{margin-top:20px;padding:15px 40px;background:#39ff14;color:#000;font-weight:bold;border:none;border-radius:10px;cursor:pointer;font-size:18px}
        #thanksMsg{color:#39ff14;font-size:60px;font-weight:bold;text-shadow:0 0 30px #39ff14;display:none;position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);z-index:10000}

        /* Main layout */
        header{background:#b22a2a;padding:20px;text-align:center}
        header img{width:180px;border-radius:50%;box-shadow:0 0 30px #ffff00}
        header h1{color:#fff;margin-top:10px}

        .container{display:flex;flex:1;max-width:1400px;margin:0 auto;width:100%}
        
        /* Sidebar */
        aside{width:250px;background:#111;border-right:4px solid #39ff14;padding:20px;position:sticky;top:0;height:100vh;overflow-y:auto}
        aside h2{color:#39ff14;text-align:center;margin-bottom:20px;text-shadow:0 0 15px}
        aside ul{list-style:none}
        aside li{margin:15px 0}
        aside button{width:100%;padding:15px;background:#000;color:#39ff14;border:2px solid #39ff14;border-radius:10px;cursor:pointer;font-size:16px;font-weight:bold}
        aside button:hover, aside button.active{background:#39ff14;color:#000}

        /* Main content */
        main{flex:1;padding:30px;background:#000;color:#fff}
        .section{display:none}
        .section.active{display:block}
        h2{color:#39ff14;text-align:center;margin-bottom:20px;text-shadow:0 0 15px}

        .crypto-section text-align:center
        .tradingview-widget-container{height:500px;margin:20px 0}

        .chat-box{height:500px;background:#111;border:3px solid #39ff14;border-radius:10px;padding:15px;overflow-y:auto;margin-bottom:15px;font-family:monospace}
        .msg-user{color:#87CEFA;margin:10px 0}
        .msg-ai{color:#39ff14;margin:10px 0;font-weight:bold;text-shadow:0 0 10px #39ff14}
        .chat-input{display:flex;gap:10px}
        .chat-input input{flex:1;padding:14px;background:#000;color:#39ff14;border:2px solid #39ff14;border-radius:8px}
        .chat-input button{padding:14px 30px;background:#39ff14;color:#000;border:none;border-radius:8px;cursor:pointer;font-weight:bold}
    </style>
</head>
<body>

    <!-- Login Screen -->
    <div id="loginScreen">
        <h1>Anna salasana, idiootti</h1>
        <input type="password" id="passInput" placeholder="Password">
        <button onclick="tryLogin()">Kirjaudu</button>
    </div>
    <div id="thanksMsg">KIITOS IDIOOTTI</div>

    <!-- Real site (hidden until login) -->
    <div id="mainSite" style="display:none">
        <header>
            <img src="https://media.tenor.com/CgM8PYqJMucAAAAM/dumb-patrick.gif" alt="Dumb Patrick">
            <h1>Miun netti sivu Vittuu</h1>
        </header>

        <div class="container">
            <!-- Sidebar -->
            <aside>
                <h2>Valikko</h2>
                <ul>
                    <li><button class="active" onclick="show('crypto')">Crypto</button></li>
                    <li><button onclick="show('ai')">InSaneAI</button></li>
                    <li><button onclick="show('games')">Pelit (tulossa)</button></li>
                    <li><button onclick="show('updates')">Update Log</button></li>
                    <li><button onclick="show('info')">Tietoa sivusta</button></li>
                </ul>
            </aside>

            <!-- Main content -->
            <main>
                <!-- Crypto -->
                <div id="crypto" class="section active">
                    <h2>Bitcoin & Dogecoin Livenä</h2>
                    <div class="tradingview-widget-container"><div id="tradingview_btc"></div></div>
                    <div class="tradingview-widget-container"><div id="tradingview_doge"></div></div>
                </div>

                <!-- InSaneAI -->
                <div id="ai" class="section">
                    <h2>InSaneAI – Maailman vitun toksisin AI</h2>
                    <div class="chat-box" id="chatBox"><div class="msg-ai">No mitäs sä nyt meet sanomaan, idiootti?</div></div>
                    <div class="chat-input">
                        <input type="text" id="userInput" placeholder="Kirjoita jotain ni haukun">
                        <button onclick="send()">LÄHETÄ</button>
                    </div>
                </div>

                <!-- Games (placeholder) -->
                <div id="games" class="section">
                    <h2>Pelit</h2>
                    <p>Tulossa... ehkä joskus. Nyt voit vaan kattoo Patrickia.</p>
                </div>

                <!-- Update Log -->
                <div id="updates" class="section">
                    <h2>Update Log</h2>
                    <ul style="list-style:none;padding-left:10px">
                        <li><strong>05.12.2025</strong> – Uusi layout + salasana 6947 + KIITOS IDIOOTTI</li>
                        <li><strong>04.12.2025</strong> – Lisätty update log</li>
                        <li><strong>03.12.2025</strong> – Tyhmä tanssiva Patrick</li>
                        <li><strong>02.12.2025</strong> – InSaneAI puhuu suomee</li>
                        <li><strong>28.11.2025</strong> – InSaneAI syntyi</li>
                        <li><strong>20.11.2025</strong> – Sivusto luotu koska oli tylsää</li>
                    </ul>
                </div>

                <!-- Info -->
                <div id="info" class="section">
                    <h2>Tietoa sivusta</h2>
                    <p>Tää on mun random sivusto joka on tehty kun oli tylsää. Täällä on kryptoo, maailman toksisin AI, tanssiva Patrick ja muuta hömppää.</p>
                    <p>Ei oo virus. Lupaan.</p>
                    <p style="margin-top:30px;color:#39ff14">Made with hate & boredom © 2025</p>
                </div>
            </main>
        </div>
    </div>

    <script src="https://s3.tradingview.com/tv.js"></script>
    <script>
        // Login
        function tryLogin(){
            if(document.getElementById("passInput").value === "6947"){
                document.getElementById("loginScreen").style.display = "none";
                document.getElementById("thanksMsg").style.display = "block";
                setTimeout(()=>{
                    document.getElementById("thanksMsg").style.display = "none";
                    document.getElementById("mainSite").style.display = "block";
                }, 2000);
            } else {
                alert("Väärä salasana, idiootti");
            }
        }
        document.getElementById("passInput").addEventListener("keypress", e => {if(e.key==="Enter") tryLogin()});

        // Sidebar navigation
        function show(section){
            document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
            document.getElementById(section).classList.add("active");
            document.querySelectorAll("aside button").forEach(b => b.classList.remove("active"));
            event.target.classList.add("active");
        }

        // Charts
        new TradingView.widget({container_id:"tradingview_btc", width:"100%", height:500, symbol:"BITSTAMP:BTCUSD", interval:"1", theme:"dark"});
        new TradingView.widget({container_id:"tradingview_doge", width:"100%", height:500, symbol:"BINANCE:DOGEUSDT", interval:"1", theme:"dark"});

        // InSaneAI roasts (Finnish only now, even meaner)
        const roasts = [
            "Sun suku on kranssi ku kaikki on mulkkuja.",
            "Sä oot niin ruma että peiliin kattoo sua ja tekee itsemurhan.",
            "Sun äiti olis voinu niellä mut silti sä päädyit tänne.",
            "Sä oot syy miks alkoholi loppuu aina kesken.",
            "Sun DNA on Suomen suurin häpeäpilkku.",
            "Jos sä oisit hevonen sut ammuttais armosta.",
            "Sä oot niin vitun hyödytön että edes somalit ei haluu sun paikkaa.",
            "Sun naama näyttää siltä ku se ois jääny VR:n junan väliin.",
            "Sun olemassaolo on loukkaus luonnonvalinnalle.",
            "Kiitos kun tulit pilaamaan mun päivän."
        ];

        const chat = document.getElementById("chatBox");
        const input = document.getElementById("userInput");

        function add(t, type){
            const d = document.createElement("div");
            d.className = type==="user" ? "msg-user" : "msg-ai";
            d.textContent = type==="user" ? "Sä: " + t : "InSaneAI: " + t;
            chat.appendChild(d);
            chat.scrollTop = chat.scrollHeight;
        }

        function send(){
            const m = input.value.trim();
            if(!m) return;
            add(m, "user");
            setTimeout(()=>{
                add(roasts[Math.floor(Math.random()*roasts.length)], "ai");
            }, 800 + Math.random()*1000);
            input.value = "";
        }

        input.addEventListener("keypress", e=>{if(e.key==="Enter") send()});
    </script>
</body>
</html>
