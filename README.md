<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Number System Converter</title>
<link rel="stylesheet" href="style.css" />
</head>
<body>
<div class="container">
<h1>Number System Converter</h1>
<p>Automate conversions between Binary, Decimal, Octal & Hexadecimal</p>
<div class="converter-box">
<label for="inputNumber">Enter Number:</label>
<input type="text" id="inputNumber" placeholder="e.g. 1010 or FF" />
<label for="fromBase">From Base:</label>
<select id="fromBase">
<option value="2">Binary (2)</option>
<option value="8">Octal (8)</option>
<option value="10" selected>Decimal (10)</option>
<option value="16">Hexadecimal (16)</option>
</select>
<label for="toBase">To Base:</label>
<select id="toBase">
<option value="2">Binary (2)</option>
<option value="8">Octal (8)</option>
<option value="10">Decimal (10)</option>
<option value="16">Hexadecimal (16)</option>
</select>
<button id="convertBtn">Convert</button>
<div class="result">
<h3>Converted Result:</h3>
<p id="output"></p>
</div>
</div>
</div>
<script src="script.js"></script>
</body>
</html>
body {
background: linear-gradient(to bottom right, #4a90e2, #8e44ad);
font-family: "Poppins", sans-serif;
display: flex;
justify-content: center;
align-items: center;
height: 100vh;
margin: 0;
}
.container {
background-color: white;
padding: 30px;
border-radius: 20px;
box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.2);
width: 350px;
text-align: center;
}
h1 {
color: #333;
}
p {
color: #555;
font-size: 14px;
}
.converter-box {
display: flex;
flex-direction: column;
gap: 10px;
margin-top: 20px;
}
input,
select,
button {
padding: 10px;
border-radius: 8px;
border: 1px solid #ccc;
font-size: 15px;
}
button {
background-color: #4a90e2;
color: white;
cursor: pointer;
border: none;
transition: background 0.3s ease;
}
button:hover {
background-color: #357ABD;
}
.result {
margin-top: 15px;
background: #f0f4ff;
border-radius: 10px;
padding: 10px;
}
#output {
font-weight: bold;
font-size: 20px;
color: #2c3e50;
}
document.getElementById("convertBtn").addEventListener("click", function () {
const input = document.getElementById("inputNumber").value.trim();
const fromBase = parseInt(document.getElementById("fromBase").value);
const toBase = parseInt(document.getElementById("toBase").value);
const output = document.getElementById("output");
try {
if (!input) {
output.textContent = "Please enter a number!";
return;
}
// Convert from input base to decimal
const decimal = parseInt(input, fromBase);
if (isNaN(decimal)) {
output.textContent = "Invalid number for selected base!";
return;
}
// Convert from decimal to target base
let result = decimal.toString(toBase).toUpperCase();
output.textContent = result;
} catch (error) {
output.textContent = "Error: Invalid conversion!";
}
});
