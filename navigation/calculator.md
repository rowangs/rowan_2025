---
layout: page
title: Calculator
description: Calculator
permalink: /calculator/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Aesthetic Calculator</title>
    <style>
        body {
            background-color: #f3f4f6;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator {
            width: 300px;
            background-color: #a7bed3;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }
        .display {
            width: 100%;
            height: 50px;
            background-color: #282c34;
            color: #ffcaaf;
            text-align: right;
            font-size: 2em;
            padding: 10px;
            border-radius: 8px;
            margin-bottom: 15px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        .button {
            background-color: #c6e2e9;
            color: #282c34;
            border: none;
            font-size: 1.4em;
            border-radius: 8px;
            padding: 15px;
            cursor: pointer;
            transition: background-color 0.2s ease;
        }
        .button:hover {
            background-color: #ffcaaf;
        }
        .equal {
            background-color: #dab894;
            color: white;
        }
        .equal:hover {
            background-color: #f1ffc4;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="button" onclick="clearDisplay()">C</button>
            <button class="button" onclick="deleteLast()">DEL</button>
            <button class="button" onclick="appendToDisplay('%')">%</button>
            <button class="button" onclick="appendToDisplay('/')">/</button>
            <button class="button" onclick="appendToDisplay('7')">7</button>
            <button class="button" onclick="appendToDisplay('8')">8</button>
            <button class="button" onclick="appendToDisplay('9')">9</button>
            <button class="button" onclick="appendToDisplay('*')">*</button>
            <button class="button" onclick="appendToDisplay('4')">4</button>
            <button class="button" onclick="appendToDisplay('5')">5</button>
            <button class="button" onclick="appendToDisplay('6')">6</button>
            <button class="button" onclick="appendToDisplay('-')">-</button>
            <button class="button" onclick="appendToDisplay('1')">1</button>
            <button class="button" onclick="appendToDisplay('2')">2</button>
            <button class="button" onclick="appendToDisplay('3')">3</button>
            <button class="button" onclick="appendToDisplay('+')">+</button>
            <button class="button" onclick="appendToDisplay('0')">0</button>
            <button class="button" onclick="appendToDisplay('.')">.</button>
            <button class="button equal" onclick="calculate()">=</button>
        </div>
    </div>

<script>
        const display = document.getElementById('display');
        
        function appendToDisplay(value) {
            if (display.innerText === '0') {
                display.innerText = value;
            } else {
                display.innerText += value;
            }
        }

        function clearDisplay() {
            display.innerText = '0';
        }

        function deleteLast() {
            display.innerText = display.innerText.slice(0, -1) || '0';
        }

        function calculate() {
            try {
                display.innerText = eval(display.innerText);
            } catch {
                display.innerText = 'Error';
            }
        }
    </script>
    
</body>
</html>
