head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Professional Calculator</title>
    <style>
        body { display: flex; justify-content: center; align-items: center; height: 100vh; background-color: #f4f4f9; font-family: sans-serif; }
        .calculator { background: #333; padding: 20px; border-radius: 15px; box-shadow: 0px 10px 20px rgba(0,0,0,0.3); }
        #display { width: 100%; height: 50px; font-size: 24px; text-align: right; margin-bottom: 10px; padding: 5px; box-sizing: border-box; border: none; border-radius: 5px; }
        .buttons { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; }
        button { padding: 20px; font-size: 18px; border: none; border-radius: 5px; cursor: pointer; background: #555; color: white; }
        button:hover { background: #777; }
        .operator { background: #f39c12; }
        .operator:hover { background: #e67e22; }
        .equal { grid-column: span 2; background: #27ae60; }
        .equal:hover { background: #2ecc71; }
    </style>
</head>
<body>

<div class="calculator">
    <input type="text" id="display" disabled>
    <div class="buttons">
        <button onclick="clearDisplay()">C</button>
        <button onclick="appendToDisplay('/')" class="operator">/</button>
        <button onclick="appendToDisplay('*')" class="operator">*</button>
        <button onclick="deleteLast()">DEL</button>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
        <button onclick="appendToDisplay('-')" class="operator">-</button>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendTo
