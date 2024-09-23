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
    <title>Simple Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #f0f0f0;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        .calculator {
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
            background: white;
            width: 320px;
            padding: 20px;
            box-sizing: border-box;
        }
        .display {
            font-size: 2em;
            margin-bottom: 10px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            background: #f9f9f9;
            text-align: right;
            overflow: hidden;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        button {
            font-size: 1.5em;
            padding: 20px;
            border: none;
            border-radius: 5px;
            background: #e0e0e0;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background: #d0d0d0;
        }
        .operator {
            background: #f9a825;
            color: white;
        }
        .operator:hover {
            background: #f57f17;
        }
        .equals {
            grid-column: span 4;
            background: #4caf50;
            color: white;
        }
        .equals:hover {
            background: #388e3c;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button class="equals" onclick="calculate()">=</button>
            <button class="operator" onclick="appendToDisplay('.')">.</button>
            <button class="equals" onclick="calculate()">0</button>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            const display = document.getElementById('display');
            if (display.innerText === '0') {
                display.innerText = value;
            } else {
                display.innerText += value;
            }
        }

        function clearDisplay() {
            document.getElementById('display').innerText = '0';
        }

        function calculate() {
            const display = document.getElementById('display');
            try {
                display.innerText = eval(display.innerText);
            } catch {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>
