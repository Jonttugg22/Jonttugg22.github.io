<!DOCTYPE html>
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
            color: rgb(66, 66, 66);
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
            max-width: 800px;
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
            width: 250px;
            height: auto;
            display: block;
            margin: 20px auto;
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

        /* Password overlay styling */
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
    </style>
</head>
<body>

    <!-- Login Overlay -->
    <div id="loginOverlay">
        <div id="loginBox">
            <h2>🔒 Enter Password</h2>
            <input type="password" id="passwordInput" placeholder="Password">
            <br>
            <button onclick="checkPassword()">Login</button>
            <div id="errorMsg">Incorrect password. Try again.</div>
        </div>
    </div>

    <header>
        <h1>Welcome to My Website</h1>
    </header>

    <div class="content">
        <h2>About This Page</h2>
        <p>This is a simple HTML website created using Visual Studio Code. It includes a header, some text, an image, and a link.</p>

        <img src="https://th.bing.com/th/id/R.4a3971f208eb35707c7681404889fd47?rik=lq7zxOYVFC7IBA&riu=http%3a%2f%2fimages6.fanpop.com%2fimage%2fphotos%2f39100000%2fPatrick-Star-patrick-star-spongebob-39145544-500-691.jpg&ehk=OnW2FLCZEKRKil2RjMS5RxWPyFjvmDr1RUxTRMrkZUw%3d&risl=&pid=ImgRaw&r=0" alt="Patrick Star">

        <p>Go on to <a href="https://www.youtube.com/watch?v=xvFZjo5PgG0" target="_blank">SezyGirlPics</a> for more 👦🏿🍗🏀.</p>
    </div>

    <script>
        // Password protection logic
        const correctPassword = "12345"; // change this to whatever you want

        function checkPassword() {
            const input = document.getElementById("passwordInput").value;
            const errorMsg = document.getElementById("errorMsg");

            if (input === correctPassword) {
                document.getElementById("loginOverlay").style.display = "none";
                setTimeout(() => {
                    alert("👋 Welcome to my vibrant page!");
                }, 1000);
            } else {
                errorMsg.style.display = "block";
            }
        }

        // Prevent seeing page source before login
        document.addEventListener("contextmenu", event => event.preventDefault());
    </script>

</body>
</html>
