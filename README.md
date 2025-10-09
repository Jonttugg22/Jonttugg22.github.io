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

        /* Chat UI (added) */
        .chat-section {
            margin-top: 30px;
            background: #0b1020;
            color: #fff;
            border-radius: 10px;
            padding: 16px;
        }

        .chat-header {
            display:flex;
            justify-content: space-between;
            align-items: center;
            gap: 12px;
            margin-bottom: 12px;
        }

        .chat-title {
            font-size: 20px;
            color: #ffd36a;
        }

        .username-box {
            display:flex;
            gap:8px;
            align-items:center;
        }

        .username-box input {
            padding:6px 8px;
            border-radius:6px;
            border:1px solid #333;
            background:#0f1724;
            color:#fff;
        }

        .username-box button {
            background:#1f6feb;
            color:white;
            border:none;
            padding:6px 10px;
            border-radius:6px;
            cursor:pointer;
        }

        .messages {
            height: 320px;
            overflow-y: auto;
            padding: 12px;
            background: linear-gradient(180deg,#080a0f 0%, #09111a 100%);
            border-radius: 8px;
            margin-bottom: 12px;
            border: 1px solid rgba(255,255,255,0.03);
        }

        .msg {
            margin-bottom:10px;
            display:flex;
            gap:8px;
            align-items:flex-start;
        }

        .msg .avatar {
            width:36px;
            height:36px;
            border-radius:50%;
            background:#2b3140;
            display:flex;
            align-items:center;
            justify-content:center;
            font-weight:bold;
            color:#fff;
            flex-shrink:0;
        }

        .msg .bubble {
            background: #0f1724;
            padding:8px 10px;
            border-radius:8px;
            max-width:75%;
            box-shadow: 0 1px 0 rgba(0,0,0,0.3);
        }

        .msg .meta {
            font-size:12px;
            color:#9aa7c7;
            margin-bottom:6px;
        }

        .chat-input {
            display:flex;
            gap:8px;
            align-items:center;
        }

        .chat-input input[type="text"] {
            flex:1;
            padding:10px 12px;
            border-radius:8px;
            border:1px solid #233044;
            background:#071024;
            color:#fff;
        }

        .chat-input button {
            padding:10px 14px;
            border-radius:8px;
            border:none;
            background:#10b981;
            color:#fff;
            cursor:pointer;
        }

        .small-muted {
            font-size:12px;color:#9aa7c7;margin-left:8px;
        }

        /* responsive */
        @media (max-width:600px) {
            .tradingview-widget-container { height: 300px; }
            .messages { height: 220px; }
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
            <button onclick="checkPassword()">Login</button>
            <div id="errorMsg">Incorrect password. Try again.</div>
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
        <div class="crypto-title">📈 Bitcoin & Dogecoin Live Prices</div>
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

    <!-- Chat Section (added) -->
    <div class="chat-section" id="chatSection">
        <div class="chat-header">
            <div class="chat-title">Chat Messenger</div>
            <div class="username-box">
                <input id="usernameInput" type="text" placeholder="Enter username">
                <button id="setUsernameBtn">Set</button>
                <div class="small-muted" id="usernameDisplay"></div>
            </div>
        </div>

        <div class="messages" id="messages"></div>

        <div class="chat-input">
            <input type="text" id="messageInput" placeholder="Type a message...">
            <button id="sendBtn">Send</button>
        </div>
        <div style="margin-top:8px;font-size:12px;color:#9aa7c7;">Messages are stored locally on your browser (localStorage).</div>
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

        /***** Chat logic (client-side, localStorage only) *****/
        const messagesEl = document.getElementById('messages');
        const messageInput = document.getElementById('messageInput');
        const sendBtn = document.getElementById('sendBtn');
        const usernameInput = document.getElementById('usernameInput');
        const setUsernameBtn = document.getElementById('setUsernameBtn');
        const usernameDisplay = document.getElementById('usernameDisplay');

        // storage keys
        const LS_USER = 'miun_chat_username';
        const LS_MSGS = 'miun_chat_messages'; // stores array of {u,t,m,id}

        // load username and messages
        function loadUsername() {
            const u = localStorage.getItem(LS_USER) || '';
            if (u) {
                usernameDisplay.textContent = 'Signed as: ' + u;
                usernameInput.value = '';
            } else {
                usernameDisplay.textContent = '';
            }
        }

        function loadMessages() {
            const raw = localStorage.getItem(LS_MSGS);
            let arr = [];
            try { arr = raw ? JSON.parse(raw) : []; } catch(e){ arr = []; }
            renderMessages(arr);
        }

        function saveMessage(obj) {
            const raw = localStorage.getItem(LS_MSGS);
            let arr = [];
            try { arr = raw ? JSON.parse(raw) : []; } catch(e){ arr = []; }
            arr.push(obj);
            // keep last 200 messages max
            if (arr.length > 200) arr = arr.slice(arr.length - 200);
            localStorage.setItem(LS_MSGS, JSON.stringify(arr));
        }

        function renderMessages(arr) {
            messagesEl.innerHTML = '';
            arr.forEach(msg => {
                const node = createMessageNode(msg);
                messagesEl.appendChild(node);
            });
            // scroll to bottom
            messagesEl.scrollTop = messagesEl.scrollHeight;
        }

        function createMessageNode(msg) {
            const wrap = document.createElement('div');
            wrap.className = 'msg';
            const avatar = document.createElement('div');
            avatar.className = 'avatar';
            avatar.textContent = (msg.u && msg.u[0]) ? msg.u[0].toUpperCase() : '?';

            const content = document.createElement('div');
            const meta = document.createElement('div');
            meta.className = 'meta';
            const ts = new Date(msg.t).toLocaleTimeString();
            meta.textContent = `${msg.u} • ${ts}`;

            const bubble = document.createElement('div');
            bubble.className = 'bubble';
            bubble.textContent = msg.m;

            content.appendChild(meta);
            content.appendChild(bubble);

            wrap.appendChild(avatar);
            wrap.appendChild(content);
            return wrap;
        }

        // set username
        setUsernameBtn.addEventListener('click', () => {
            const val = usernameInput.value.trim();
            if (!val) {
                alert('Please enter a username.');
                return;
            }
            localStorage.setItem(LS_USER, val);
            usernameDisplay.textContent = 'Signed as: ' + val;
            usernameInput.value = '';
        });

        // send message
        sendBtn.addEventListener('click', sendMessage);
        messageInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') sendMessage();
        });

        function sendMessage() {
            const text = messageInput.value.trim();
            if (!text) return;
            const user = localStorage.getItem(LS_USER) || 'Anonymous';
            const msgObj = { u: user, t: Date.now(), m: text, id: Math.random().toString(36).slice(2,9) };
            saveMessage(msgObj);
            // re-render
            loadMessages();
            messageInput.value = '';
        }

        // init
        loadUsername();
        loadMessages();

        // Optional: expose a function to clear messages (for dev)
        window.__miun_clearChat = function(){
            if (confirm('Clear all local messages?')) {
                localStorage.removeItem(LS_MSGS);
                loadMessages();
            }
        };

        // If multiple tabs open, keep messages in sync via storage event
        window.addEventListener('storage', (e) => {
            if (e.key === LS_MSGS) {
                loadMessages();
            } else if (e.key === LS_USER) {
                loadUsername();
            }
        });
    </script>

</body>
</html>
