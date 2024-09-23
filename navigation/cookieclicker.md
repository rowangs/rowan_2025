---
layout: page
title: Cookie Clicker
description: To solve stuff
permalink: /cookieclicker/
---
{% include nav/home.html %}
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 200vh;
            background-color: #F0F0F0;
        }
        
        #cookie {
            width: 250px; /* Increase the cookie size */
            cursor: pointer;
            margin-bottom: 20px;
        }
        #score {
            font-size: 32px; /* Increase score text size */
            color: white;
        }
        .game-container {
            background-color: #333; /* Add a background color */
            padding: 30px; /* Increase padding for a bigger box */
            border-radius: 10px; /* Rounded corners for a smoother look */
            width: 350px; /* Increase container width */
            text-align: center;
        }
    </style>
</head>


       <div id="upgrades">
           <button class="upgrade" onclick="buyUpgrade(10, 1)">+1 Cookie per Click (Cost: 10)</button>
           <button class="upgrade" onclick="buyUpgrade(100, 10)">+10 Cookies per Click (Cost: 100)</button>
           <button class="upgrade" onclick="buyUpgrade(500, 25)">+25 Cookies per Click (Cost: 500)</button>
           <button class="upgrade" onclick="buyUpgrade(1000, 50)">+50 Cookies per Click (Cost: 1000)</button>
           <button class="upgrade" onclick="buyUpgrade(5000, 100)">+100 Cookies per Click (Cost: 5000)</button>
           <button class="upgrade" onclick="buyAutoClicker(500)">Auto Clicker (Cost: 500)</button>
           <button class="upgrade" onclick="buyGoldenCookie(3000)">Golden Cookie (Cost: 3000)</button>
       </div>




       <div id="youWin">You Win! Cookies are raining down!</div>
       <button id="playAgain" onclick="resetGame()">Play Again</button>
   </div>

<body>
    <h1>Cookie Clicker</h1>
    <img src="{{ site.baseurl }}/images/cookie.png" alt="Cookie" id="cookie">
    <div id="score">Score: 0</div>
    <audio id="clickSound" src="{{ site.baseurl}}/assets/click-sound.wav"></audio>
    
    <script>
        let score = 0;
        const cookie = document.getElementById('cookie');
        const scoreDisplay = document.getElementById('score');
        const clickSound = document.getElementById('clickSound');
        cookie.addEventListener('click', function() {
            score++;
            scoreDisplay.textContent = 'Score: ' + score;
            clickSound.play();
        });
    </script>
</body>
</html>