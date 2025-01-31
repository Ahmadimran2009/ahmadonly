---
layout: page 
title: countdown
search_exclude: true
permalink: /search/

---
# this is a countdown for my 16th birthday🥳

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Timer</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
        }
        #countdown {
            font-size: 2em;
            font-weight: bold;
            text-align: center;
        }
        .countdown-section {
            display: inline-block;
            padding: 0 10px;
        }
    </style>
</head>
<body>
    <div id="countdown">
        <div class="countdown-section" id="days">00</div> Days 
        <div class="countdown-section" id="hours">00</div> Hours 
        <div class="countdown-section" id="minutes">00</div> Minutes 
        <div class="countdown-section" id="seconds">00</div> Seconds
    </div>

    <script>
        function updateCountdown() {
            const targetDate = new Date('2025-05-28T00:00:00');
            const now = new Date();
            const timeDiff = targetDate - now;

            if (timeDiff <= 0) {
                document.getElementById('countdown').innerHTML = 'The date has arrived!';
                return;
            }

            const days = Math.floor(timeDiff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeDiff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeDiff % (1000 * 60)) / 1000);

            document.getElementById('days').textContent = days.toString().padStart(2, '0');
            document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
        }

        setInterval(updateCountdown, 1000);
        updateCountdown();  // Initial call to display the countdown immediately
    </script>
</body>
</html>


