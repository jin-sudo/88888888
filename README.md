<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>随机抽签工具</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background-image: url('castle.jpg'); /* 图片与HTML文件在同一目录下 */
            background-size: cover; /* 使背景图覆盖整个页面 */
            background-position: center; /* 背景图居中 */
            background-attachment: fixed; /* 固定背景图片，不随页面滚动 */
            color: white; /* 设置文字颜色为白色，以便更好地与背景对比 */
            background-color: rgba(0, 0, 0, 0.5); /* 半透明黑色背景层，增强文字对比度 */
        }

        input {
            padding: 8px;
            font-size: 16px;
            margin: 5px;
            width: 100px;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
        }

        button:hover {
            background-color: #0056b3;
        }

        .results {
            margin-top: 20px;
        }

        #currentResult {
            font-size: 24px;
            font-weight: bold;
            color: #f1f1b8;
        }

        #history {
            margin-top: 10px;
            font-size: 18px;
            color: #d9b8f1;
        }
    </style>
</head>
<body>
    <h1>随机抽签工具</h1>
    <div>
        <label for="minNumber">最小值:</label>
        <input type="number" id="minNumber" placeholder="如：1">
        <label for="maxNumber">最大值:</label>
        <input type="number" id="maxNumber" placeholder="如：100">
    </div>
    <button onclick="drawNumber()">抽取数字</button>
    <div class="results">
        <h3>抽取结果:</h3>
        <p id="currentResult">尚未抽取</p>
        <h3>已抽取的数字:</h3>
        <p id="history">无</p>
    </div>
    <script>
        let drawnNumbers = [];

        function drawNumber() {
            const min = parseInt(document.getElementById('minNumber').value);
            const max = parseInt(document.getElementById('maxNumber').value);

            if (isNaN(min) || isNaN(max) || min >= max) {
                alert("请输入有效的数字范围（最小值需小于最大值）！");
                return;
            }

            if (min < 0) {
                alert("最小值不能小于0！");
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
