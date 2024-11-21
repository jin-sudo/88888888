<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>随机抽签</title>
<style>
    body {
        position:fixed;
        top: 0;
        left: 0;
		width:200%;
		height:200%;
        min-width: 1000px;
        background: url(./2.jpg);
        background-repeat: no-repeat;
        background-size: cover;
        -webkit-background-size: cover;
        -o-background-size: cover;
        background-position: center center;
    body {
        font-family: Arial, sans-serif;
        padding: 20px;
    }
    #inputArea {
        margin-bottom: 10px;
    }
    #drawButton {
        padding: 10px 20px;
        font-size: 16px;
        cursor: pointer;
    }
    #result {
        margin-top: 20px;
        font-size: 20px;
        color: green;
    }
</style>
</head>
<body>

<div id="inputArea">
    <label for="numbers">输入数字，用逗号分隔:</label>
    <input type="text" id="numbers" placeholder="例如：1,2,3,4,5">
</div>

<button id="drawButton" onclick="drawLottery()">抽签</button>

<div id="result"></div>
<div id="drawnNumbers">
    <h3>历史抽中的数字：</h3>
    <ul id="drawnNumbersList">
    </ul>
</div>

<script>
function drawLottery() {
    var input = document.getElementById('numbers').value;
    var numbers = input.split(',').map(function(item) {
        return item.trim();
    });

    // 过滤掉空字符串，并转换为整数
    numbers = numbers.filter(function(item) {
        return item !== '' && !isNaN(item);
    }).map(function(item) {
        return parseInt(item, 10);
    });

    if (numbers.length === 0) {
        document.getElementById('result').innerText = '请输入有效的数字！';
        return;
    }

    var randomIndex = Math.floor(Math.random() * numbers.length);
    var result = numbers[randomIndex];

    // 显示结果
    document.getElementById('result').innerText = '抽中的数字是：' + result;

    // 添加到历史列表
    var drawnNumbersList = document.getElementById('drawnNumbersList');
    var listItem = document.createElement('li');
    listItem.innerText = result;
    drawnNumbersList.appendChild(listItem);
}
</script>

</body>
</html>
