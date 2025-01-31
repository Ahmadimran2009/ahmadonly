---
layout: page
title: Cookie Clicker
permalink: /cookieclicker/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0e68c;
        }
        #cookie {
            width: 200px;
            height: 200px;
            background-color: #ffcc00;
            border-radius: 50%;
            margin: 20px auto;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            color: #7a5a00;
        }
        #score {
            font-size: 32px;
            margin: 20px;
        }
        #upgrade {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Cookie Clicker</h1>
    <div id="cookie" onclick="clickCookie()">🍪</div>
    <div id="score">Cookies: 0</div>
    <button id="upgrade" onclick="buyUpgrade()">Upgrade (Cost: 10 cookies)</button>

    <script>
        let cookies = 0;
        let cookiesPerClick = 1;
        
        function clickCookie() {
            cookies += cookiesPerClick;
            document.getElementById("score").innerText = `Cookies: ${cookies}`;
            var cookieSound = new Audio("../assets/audio/crumple-92100.mp3");
            cookieSound.play();
        }

        function buyUpgrade() {
            const upgradeCost = 10 + (cookiesPerClick * 10); // Adjust cost for next upgrade
            if (cookies >= upgradeCost) {
                cookies -= upgradeCost;
                cookiesPerClick++;
                document.getElementById("score").innerText = `Cookies: ${cookies}`;
                document.getElementById("upgrade").innerText = `Upgrade (Cost: ${10 + (cookiesPerClick * 10)} cookies)`;
            } else {
                alert("Not enough cookies!");
            }
        }
    </script>
</body>
</html>
