<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>随机抽签</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        input {
            padding: 5px;
            font-size: 16px;
            margin: 5px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
        .results {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>随机抽签工具</h1>
    <div>
        <label for="minNumber">最小值:</label>
        <input type="number" id="minNumber" placeholder="请输入最小值">
        <label for="maxNumber">最大值:</label>
        <input type="number" id="maxNumber" placeholder="请输入最大值">
    </div>
    <button onclick="drawNumber()">抽取数字</button>
    <div class="results">
        <h3>抽取结果:</h3>
        <p id="currentResult">尚未抽取</p>
        <h3>已抽取的数字:</h3>
        <p id="history">无</p>
    </div>
    <img src="C:/Users/lenovo/Videos/10.24/项目说明书/6.jpg","weight="50%" height="50%">
    <script>
        let drawnNumbers = [];

        function drawNumber() {
            const min = parseInt(document.getElementById('minNumber').value);
            const max = parseInt(document.getElementById('maxNumber').value);

            if (isNaN(min) || isNaN(max) || min > max) {
                alert("请输入有效的数字范围！");
                return;
            }

            // 生成候选数字数组
            const range = [];
            for (let i = min; i <= max; i++) {
                if (!drawnNumbers.includes(i)) {
                    range.push(i);
                }
            }

            if (range.length === 0) {
                alert("所有数字已抽取完毕！");
                return;
            }

            // 随机抽取
            const randomIndex = Math.floor(Math.random() * range.length);
            const drawnNumber = range[randomIndex];

            // 更新已抽取数字
            drawnNumbers.push(drawnNumber);

            // 显示结果
            document.getElementById('currentResult').textContent = drawnNumber;
            document.getElementById('history').textContent = drawnNumbers.join(', ');
        }
    </script>
</body>
</html>
