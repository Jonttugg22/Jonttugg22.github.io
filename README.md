<!DOCTYPE html>
<html lang="fi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Miun Sivusto</title>
    <style>
        *{margin:0;padding:0;box-sizing:border-box}
        body{background:#000;color:#fff;font-family:Arial,sans-serif;overflow-x:hidden}

        /* Login */
        #loginScreen{position:fixed;top:0;left:0;width:100%;height:100%;background:#000;display:flex;flex-direction:column;justify-content:center;align-items:center;z-index:9999}
        #loginScreen h1{color:#39ff14;font-size:45px;margin-bottom:40px;text-shadow:0 0 20px #39ff14}
        #loginScreen input{padding:18px;width:80%;max-width:340px;font-size:22px;border:3px solid #39ff14;background:#000;color:#39ff14;border-radius:12px;text-align:center}
        #loginScreen button{margin-top:25px;padding:18px 50px;background:#39ff14;color:#000;font-weight:bold;border:none;border-radius:12px;cursor:pointer;font-size:20px}

        /* Mode + thanks */
        #modeScreen, #thanksMsg{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:#000;flex-direction:column;justify-content:center;align-items:center;z-index:9999}
        #modeScreen h1, #thanksMsg{font-size:60px;color:#39ff14;text-shadow:0 0 30px #39ff14;text-align:center}
        #modeScreen button{margin:20px;padding:20px 50px;background:#39ff14;color:#000;font-size:22px;border:none;border-radius:12px;cursor:pointer}

        /* Header */
        header{background:#b22a2a;padding:15px;text-align:center;position:relative}
        header img{width:140px;border-radius:50%;box-shadow:0 0 30px #ffff00}
        header h1{font-size:28px;margin-top:10px}

        #menuBtn, #modeBtn{position:absolute;top:50%;transform:translateY(-50%);background:none;border:none;color:#39ff14;font-size:34px;cursor:pointer;z-index:100}
        #menuBtn{left:15px}
        #modeBtn{right:15px}

        /* Sidebar */
        aside{width:300px;background:#111;border-right:4px solid #39ff14;padding:25px;position:fixed;top:0;left:-320px;height:100%;overflow-y:auto;transition:left .3s;z-index:99;box-shadow:0 0 30px #39ff14}
        aside.active{left:0}
        aside h2{color:#39ff14;text-align:center;margin-bottom:30px;text-shadow:0 0 15px;font-size:26px}
        aside button{width:100%;padding:18px;margin:10px 0;background:#000;color:#39ff14;border:2px solid #39ff14 solid;border-radius:12px;font-size:18px;font-weight:bold;cursor:pointer}
        aside button:hover, aside button.active{background:#39ff14;color:#000}

        main{padding:20px;padding-top:110px}
        .section{display:none}
        .section.active{display:block}
        h2{color:#39ff14;text-align:center;margin:30px 0 20px;text-shadow:0 0 15px;font-size:28px}

        .tradingview-widget-container{height:420px;margin:20px 0;border-radius:12px;overflow:hidden;border:2px solid #333}
        .chat-box{height:500px;background:#111;border:3px solid #39ff14;border-radius:12px;padding:15px;overflow-y:auto;margin-bottom:15px;font-family:monospace;font-size:16px}
        .msg-user{color:#87CEFA;margin:12px 0}
        .msg-ai{color:#39ff14;margin:12px 0;font-weight:bold;text-shadow:0 0 10px #39ff14}
        .chat-input{display:flex;gap:10px;margin-top:10px}
        .chat-input input{flex:1;padding:16px;background:#000;color:#39ff14;border:2px solid #39ff14;border-radius:10px;font-size:17px}
        .chat-input button{padding:16px 30px;background:#39ff14;color:#000;border:none;border-radius:10px;font-weight:bold;font-size:17px}

        @media (max-width:900px){
            aside{width:100%;left:-100%}
            .tradingview-widget-container{height:360px}
            .chat-box{height:440px}
        }
    </style>
</head>
<body>

    <!-- Login -->
    <div id="loginScreen">
        <h1>Anna salasana</h1>
        <input type="password" id="passInput" placeholder="Password">
        <button onclick="checkPass()">Kirjaudu</button>
    </div>

    <!-- Mode selection -->
    <div id="modeScreen">
        <h1>Mobiili vai tietokone?</h1>
        <button onclick="setMode('mobile')">MOBIILI</button>
        <button onclick="setMode('computer')">TIETOKONE</button>
    </div>

    <!-- Thanks message -->
    <div id="thanksMsg">KIITOS IDIOOTTI</div>

    <!-- Main site -->
    <div id="mainSite" style="display:none">
        <header>
            <button id="menuBtn">Menu</button>
            <img src="https://media.tenor.com/CgM8PYqJMucAAAAM/dumb-patrick.gif" alt="Patrick">
            <button id="modeBtn" title="Vaihda näkymä">Mobile/PC</button>
            <h1>Miun netti sivu Vittuu</h1>
        </header>

        <aside id="sidebar">
            <h2>Valikko</h2>
            <button class="active" onclick="show('crypto')">Crypto</button>
            <button onclick="show('ai')">InSaneAI</button>
            <button onclick="show('games')">Pelit</button>
            <button onclick="show('updates')">Update Log</button>
            <button onclick="show('info')">Tietoa</button>
        </aside>

        <main>
            <div id="crypto" class="section active">
                <h2>Bitcoin & Dogecoin</h2>
                <div class="tradingview-widget-container"><div id="tradingview_btc"></div></div>
                <div class="tradingview-widget-container"><div id="tradingview_doge"></div></div>
            </div>

            <div id="ai" class="section">
                <h2>InSaneAI</h2>
                <div class="chat-box" id="chatBox">
                    <div class="msg-ai">Mitä sä nyt meet sanomaan, idiootti?</div>
                </div>
                <div class="chat-input">
                    <input type="text" id="userInput" placeholder="Kirjoita jotain...">
                    <button onclick="send()">LÄHETÄ</button>
                </div>
            </div>

            <div id="games" class="section"><h2>Pelit</h2><p>Tulossa joskus... tai ei.</p></div>
            <div id="updates" class="section"><h2>Update Log</h2><ul style="padding-left:20px"><li><strong>05.12.2025</strong> – Toimiva versio, ei virheitä</li><li><strong>05.12.2025</strong> – Mobiili/PC-nappi + klikkaus ulos sulkee</li></ul></div>
            <div id="info" class="section"><h2>Tietoa</h2><p>Random sivusto. Ei virus. Lupaan.</p></div>
        </main>
    </div>

    <script src="https://s3.tradingview.com/tv.js"></script>
    <script>
        const correctPass = "6947"; // ei näytetä missään

        function checkPass(){
            if(document.getElementById("passInput").value === correctPass){
                document.getElementById("loginScreen").style.display = "none";
                document.getElementById("modeScreen").style.display = "flex";
            } else {
                alert("VÄÄRÄ SALASANA");
            }
        }
        document.getElementById("passInput").addEventListener("keypress", e=>{if(e.key==="Enter") checkPass()});

        function setMode(mode){
            localStorage.setItem("viewMode", mode);
            document.getElementById("modeScreen").style.display = "none";
            document.getElementById("thanksMsg").style.display = "flex";
            setTimeout(()=>{
                document.getElementById("thanksMsg").style.display = "none";
                document.getElementById("mainSite").style.display = "block";
                applyMode();
            }, 1800);
        }

        function applyMode(){
            const mode = localStorage.getItem("viewMode") || "mobile";
            document.getElementById("modeBtn").textContent = mode === "mobile" ? "Mobile" : "PC";
            if(mode === "computer" && window.innerWidth > 900){
                document.getElementById("sidebar").classList.add("active");
            }
        }

        document.getElementById("menuBtn").onclick = () => document.getElementById("sidebar").classList.toggle("active");

        document.getElementById("modeBtn").onclick = () => {
            const newMode = localStorage.getItem("viewMode") === "mobile" ? "computer" : "mobile";
            localStorage.setItem("viewMode", newMode);
            location.reload();
        };

        // Klikkaus ulkopuolella sulkee palkin mobiilissa
        document.addEventListener("click", e => {
            const sidebar = document.getElementById("sidebar");
            if(window.innerWidth <= 900 && sidebar.classList.contains("active")){
                if(!sidebar.contains(e.target) && e.target.id !== "menuBtn" && e.target.id !== "modeBtn"){
                    sidebar.classList.remove("active");
                }
            }
        });

        function show(section){
            document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
            document.getElementById(section).classList.add("active");
            document.querySelectorAll("aside button").forEach(b=>b.classList.remove("active"));
            event.target.classList.add("active");
            if(window.innerWidth <= 900) document.getElementById("sidebar").classList.remove("active");
        }

        // Charts
        new TradingView.widget({container_id:"tradingview_btc", width:"100%", height:"100%", symbol:"BITSTAMP:BTCUSD", theme:"dark"});
        new TradingView.widget({container_id:"tradingview_doge", width:"100%", height:"100%", symbol:"BINANCE:DOGEUSDT", theme:"dark"});

        // InSaneAI
        const roasts = ["Sun suku on kranssi ku kaikki on mulkkuja.","Sä oot niin ruma että peili tekee itsemurhan.","Sun äiti olis voinu niellä mut sä päädyit silti tänne.","Kiitos kun tulit pilaamaan mun päivän.","Sä oot syy miks alkoholi loppuu aina kesken."];
        const chat = document.getElementById("chatBox");
        const input = document.getElementById("userInput");
        function add(t,type){
            const d=document.createElement("div");
            d.className=type==="user"?"msg-user":"msg-ai";
            d.textContent=type==="user"?"Sä: "+t:"InSaneAI: "+t;
            chat.appendChild(d);chat.scrollTop=chat.scrollHeight;
        }
        function send(){
            const m=input.value.trim();if(!m)return;
            add(m,"user");
            setTimeout(()=>{add(roasts[Math.floor(Math.random()*roasts.length)],"ai");},900);
            input.value="";
        }
        input.addEventListener("keypress",e=>{if(e.key==="Enter")send()});

        window.onload = applyMode;
    </script>
</body>
</html>
