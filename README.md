<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced Calculator</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    background:#121212;
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
}

.calculator{
    width:95%;
    max-width:380px;
    background:#1f1f1f;
    padding:20px;
    border-radius:25px;
    box-shadow:0 0 20px rgba(0,0,0,0.5);
}

.display{
    width:100%;
    height:80px;
    border:none;
    outline:none;
    background:#2b2b2b;
    color:white;
    font-size:2rem;
    text-align:right;
    padding:15px;
    border-radius:15px;
    margin-bottom:15px;
}

.buttons{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:10px;
}

button{
    height:65px;
    border:none;
    border-radius:15px;
    font-size:1.3rem;
    cursor:pointer;
    transition:0.2s;
}

button:hover{
    transform:scale(1.05);
}

.num{
    background:#333;
    color:white;
}

.operator{
    background:#ff9500;
    color:white;
}

.special{
    background:#555;
    color:white;
}

.equal{
    background:#28a745;
    color:white;
}

@media(max-width:480px){
    button{
        height:60px;
        font-size:1.2rem;
    }

    .display{
        font-size:1.8rem;
    }
}
</style>
</head>

<body>

<div class="calculator">
    <input type="text" class="display" id="display" readonly>

    <div class="buttons">
        <button class="special" onclick="clearDisplay()">C</button>
        <button class="special" onclick="backspace()">⌫</button>
        <button class="special" onclick="appendValue('%')">%</button>
        <button class="operator" onclick="appendValue('/')">÷</button>

        <button class="num" onclick="appendValue('7')">7</button>
        <button class="num" onclick="appendValue('8')">8</button>
        <button class="num" onclick="appendValue('9')">9</button>
        <button class="operator" onclick="appendValue('*')">×</button>

        <button class="num" onclick="appendValue('4')">4</button>
        <button class="num" onclick="appendValue('5')">5</button>
        <button class="num" onclick="appendValue('6')">6</button>
        <button class="operator" onclick="appendValue('-')">−</button>

        <button class="num" onclick="appendValue('1')">1</button>
        <button class="num" onclick="appendValue('2')">2</button>
        <button class="num" onclick="appendValue('3')">3</button>
        <button class="operator" onclick="appendValue('+')">+</button>

        <button class="special" onclick="appendValue('(')">(</button>
        <button class="num" onclick="appendValue('0')">0</button>
        <button class="special" onclick="appendValue(')')">)</button>
        <button class="equal" onclick="calculate()">=</button>

        <button class="num" style="grid-column: span 4;"
            onclick="appendValue('.')">.</button>
    </div>
</div>

<script>
const display = document.getElementById("display");

function appendValue(value){
    display.value += value;
}

function clearDisplay(){
    display.value = "";
}

function backspace(){
    display.value = display.value.slice(0,-1);
}

function calculate(){
    try{
        let expression = display.value.replace(/%/g,"/100");
        display.value = eval(expression);
    }
    catch{
        display.value = "Error";
    }
}

document.addEventListener("keydown",(e)=>{
    const key = e.key;

    if("0123456789+-*/.%()".includes(key)){
        appendValue(key);
    }
    else if(key==="Enter"){
        calculate();
    }
    else if(key==="Backspace"){
        backspace();
    }
    else if(key==="Escape"){
        clearDisplay();
    }
});
</script>

</body>
</html>
