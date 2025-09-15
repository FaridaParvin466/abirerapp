# abirerapp
<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>সাজিদের তৈরি ফালতু WebSite</title>
<style>
  body {
    font-family: Arial, sans-serif;
    padding: 20px;
    background: #f0f0f0;
  }
  h1 {
    text-align: center;
    color: #000000; /* কালো রঙ */
    margin-bottom: 30px;
    font-size: 32px;
  }
  label {
    display: block;
    margin-top: 10px;
    font-weight: bold;
  }
  input[type="text"], input[type="number"] {
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
    box-sizing: border-box;
    font-size: 16px;
  }
  button {
    margin-top: 15px;
    padding: 10px 15px;
    font-size: 16px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
  }
  #output {
    margin-top: 20px;
    padding: 10px;
    background: #fff;
    border: 1px solid #ccc;
    white-space: pre-wrap; /* Enter চাপার মতো ফরম্যাট রাখবে */
    border-radius: 5px;
    min-height: 100px;
  }
</style>
</head>
<body>

<h1>সাজিদের তৈরি ফালতু WebSite</h1>

<label for="textInput">১ম বক্সে লেখা দিন:</label>
<input type="text" id="textInput" placeholder="এখানে লেখা লিখুন">

<label for="numberInput">২য় বক্সে সংখ্যা দিন:</label>
<input type="number" id="numberInput" placeholder="যতবার লেখা দেখাতে চান" min="1">

<button id="generateBtn">লেখা তৈরি করুন</button>
<button id="copyBtn">সব লেখা কপি করুন</button>

<div id="output"></div>

<script>
const textInput = document.getElementById('textInput');
const numberInput = document.getElementById('numberInput');
const generateBtn = document.getElementById('generateBtn');
const output = document.getElementById('output');
const copyBtn = document.getElementById('copyBtn');

generateBtn.addEventListener('click', () => {
  const text = textInput.value.trim();
  const count = parseInt(numberInput.value);
  
  if(!text) {
    alert('দয়া করে প্রথম বক্সে লেখা দিন।');
    return;
  }
  
  if(isNaN(count) || count < 1) {
    alert('দয়া করে দ্বিতীয় বক্সে একটি বৈধ সংখ্যা দিন।');
    return;
  }
  
  let result = '';
  for(let i = 0; i < count; i++) {
    result += text + '\n'; // প্রতিবার শেষে নতুন লাইন
  }
  
  output.textContent = result;
});

copyBtn.addEventListener('click', () => {
  const textToCopy = output.textContent;

  // হিডেন textarea বানিয়ে তাতে টেক্সট রাখব
  const hiddenTextArea = document.createElement("textarea");
  hiddenTextArea.value = textToCopy;
  document.body.appendChild(hiddenTextArea);
  hiddenTextArea.select();
  
  try {
    document.execCommand("copy");
    alert("লেখা কপি করা হয়েছে!");
  } catch (err) {
    alert("কপি করতে সমস্যা হয়েছে।");
  }

  document.body.removeChild(hiddenTextArea);
});
</script>

</body>
</html>
