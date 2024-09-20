---
layout: post
title: Snake Game
description: A Javascript Snake game that contains score and preferences.
categories: [Javascript]
menu: nav/javascript_project.html
permalink: /javascript/project/snake
toc: true
comments: false
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Game</title>
    <style>
        body {
            background-color: #f8d9ec;
            text-align: center;
        }
        canvas {
            border: 10px solid #FFFFFF;
            display: block;
            margin: 0 auto;
        }
        #menu, #gameover, #setting {
            display: none;
        }
    </style>
</head>
<body>

    <header>
        <h1>Snake Game</h1>
        <p>Score: <span id="score_value">0</span></p>
    </header>

    <div id="menu">
        <p>Press space to start</p>
    </div>
    
    <canvas id="snake" width="320" height="320" tabindex="1"></canvas>

    <div id="gameover">
        <p>Game Over! Press space to try again</p>
    </div>

    <script>
        const canvas = document.getElementById("snake");
        const ctx = canvas.getContext("2d");
        const BLOCK = 10;
        let snake = [{x: 10, y: 10}];
        let snake_dir = 1; // right
        let food = {};
        let score = 0;

        function startGame() {
            snake = [{x: 10, y: 10}];
            snake_dir = 1; // right
            score = 0;
            document.getElementById("score_value").innerText = score;
            placeFood();
            document.getElementById("menu").style.display = "none";
            document.getElementById("gameover").style.display = "none";
            setInterval(mainLoop, 100);
        }

        function placeFood() {
            food.x = Math.floor(Math.random() * (canvas.width / BLOCK)) * BLOCK;
            food.y = Math.floor(Math.random() * (canvas.height / BLOCK)) * BLOCK;
        }

        function mainLoop() {
            let head = {x: snake[0].x, y: snake[0].y};

            if (snake_dir === 0) head.y -= BLOCK; // up
            if (snake_dir === 1) head.x += BLOCK; // right
            if (snake_dir === 2) head.y += BLOCK; // down
            if (snake_dir === 3) head.x -= BLOCK; // left

            snake.unshift(head);

            if (head.x === food.x && head.y === food.y) {
                score++;
                document.getElementById("score_value").innerText = score;
                placeFood();
            } else {
                snake.pop();
            }

            if (checkCollision()) {
                gameOver();
                return;
            }

            draw();
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = 'green';
            snake.forEach(part => ctx.fillRect(part.x, part.y, BLOCK, BLOCK));
            ctx.fillStyle = 'red'; // strawberry color
            ctx.fillText("🍓", food.x, food.y + BLOCK); // drawing the strawberry emoji
        }

        function checkCollision() {
            const head = snake[0];
            if (head.x < 0 || head.x >= canvas.width || head.y < 0 || head.y >= canvas.height) return true;
            for (let i = 1; i < snake.length; i++) {
                if (head.x === snake[i].x && head.y === snake[i].y) return true;
            }
            return false;
        }

        function gameOver() {
            document.getElementById("gameover").style.display = "block";
            document.getElementById("menu").style.display = "none";
        }

        window.addEventListener("keydown", function(evt) {
            if (evt.code === "Space") {
                if (document.getElementById("menu").style.display === "block") {
                    startGame();
                } else {
                    gameOver();
                }
            }
            if (evt.code === "ArrowUp" && snake_dir !== 2) snake_dir = 0;
            if (evt.code === "ArrowRight" && snake_dir !== 3) snake_dir = 1;
            if (evt.code === "ArrowDown" && snake_dir !== 0) snake_dir = 2;
            if (evt.code === "ArrowLeft" && snake_dir !== 1) snake_dir = 3;
        });

        document.getElementById("menu").style.display = "block";
    </script>
</body>
</html>
