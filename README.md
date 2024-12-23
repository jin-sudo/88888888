<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>智游三晋——用人工智能探索山西的千年瑰宝</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
</head>
<body>
    <header>
        <div class="logo">山西文旅</div>
        <nav>
            <ul>
                <li><a href="#home">首页</a></li>
                <li><a href="#culture">文化介绍</a></li>
                <li><a href="#ai-services">人工智能服务</a></li>
                <li><a href="#contact">联系我们</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <!-- 首页部分 -->
        <section id="home" class="home">
            <div class="video-background">
                <video autoplay loop id="video-background" controls muted>
                    <source src="video.mp4" type="video/mp4">
                    您的浏览器不支持视频标签。
                </video>
            </div>
        
            <div class="home-content">
                <h1>智游三晋——用人工智能探索山西的千年瑰宝</h1>
                <p class="intro-text">感受山西传统文化与人工智能的完美结合，通过AI与黑神化悟空探索山西文化之美，在虚拟与现实交织的世界中，深度体验山西的千年瑰宝。</p>
                <button onclick="scrollToSection('culture')">探索文化介绍</button>
            </div>
        </section>
        
        <!-- 文化介绍部分 -->
        <section id="culture" class="page">
            <h2>文化介绍</h2>
            <div class="content">
                <p>山西是中国历史文化的重要发源地之一，黑神化悟空的形象完美融合了山西的传统文化与现代科技。从晋商文化到煤炭历史，从云冈石窟到精致的山西小吃，黑神化悟空将这些文化元素与虚拟现实、增强现实和人工智能等技术相结合，带您进入全新的体验世界。</p>
                <div class="image">
                    <img src="晋商文化.jpg" alt="山西晋商文化" loading="lazy">
                    <img src="晋祠.jpg" alt="晋祠景区" loading="lazy">
                    <img src="见知佛入.jpg" alt="佛教文化" loading="lazy">
                    <img src="云冈石窟.jpg" alt="云冈石窟遗址" loading="lazy">
                    <img src="壁画.jpg" alt="山西壁画艺术" loading="lazy">
                    <img src="历史文物.jpg" alt="历史文物展览" loading="lazy">
                    <img src="醋文化.jpg" alt="山西醋文化" loading="lazy">
                </div>
                
            </div>
        </section>
        
        <!-- 人工智能服务部分 -->
        <section id="ai-services" class="page">
            <h2>人工智能服务</h2>
            <div class="content">
                <p>山西文旅通过引入最新的人工智能技术，改变了游客体验方式。虚拟现实与增强现实技术，让游客穿越千年，亲身感受历史的脉搏；AI导览员提供个性化的服务，带您探索每一处山西的美景与文化。</p>

                <ul class="ai-services-list">
                    <li><strong>语音助手与AI导游：：</strong>语音助手与AI导游为您提供精准的路线和解说，带您走遍山西的每一个角落</li>
                    <li><strong>VR全景游览：</strong>通过虚拟现实技术，您将进入一个栩栩如生的山西，感受历史与未来的交织。</li>
                    <li><strong>AR增强景区讲解：</strong>增强现实让您在山西的每个角落都能体验到生动的历史故事。</li>
                </ul>
            </div>
        </div>
    </section>

    <section id="ai-chat" class="page">
        <h2>与AI导览员对话</h2>
        <div class="content">
            <div class="ai-chatbox">
                <div class="chat-container">
                    <div id="chat-box" class="chat-box">
                        <div class="bot-message">
                            <p>你好！有什么问题我可以帮助你解答吗？(如：山西有哪些景点，山西的历史文化，山西有哪些小吃)</p>
                        </div>
                    </div>
                    <input type="text" id="user-input" class="user-input" placeholder="输入问题..." aria-label="输入问题">
                    <button onclick="submitMessage()">发送</button>
                </div>
            </div>
        </div>
    </section>      

        <!-- 联系我们部分 -->
        <section id="contact" class="page">
            <h2>联系我们</h2>
            <div class="content">
                <p>欢迎联系山西文旅，我们将为您提供更多信息和支持，带您体验山西文旅的魅力。</p>
                <form id="contact-form">
                    <label for="name">姓名：</label><br>
                    <input type="text" id="name" name="name" required><br><br>
                    <label for="email">电子邮箱：</label><br>
                    <input type="email" id="email" name="email" required><br><br>
                    <label for="email">留言内容：</label><br>
                    <textarea placeholder="请输入您的留言内容" rows="4" cols="50" required></textarea><br><br>
                    <button type="submit">提交</button>
                </form>
                <div id="form-feedback" class="feedback"></div>
            </div>
        </section>
    </main>

     <footer>
        <p>&copy; 2024 山西文旅 | 由AI驱动的创新体验</p>
    </footer>

    <script>
        // 页面滚动至目标部分
        function scrollToSection(sectionId) {
            const section = document.getElementById(sectionId);
            section.scrollIntoView({ behavior: 'smooth' });
        }

        // 提交聊天信息
        function submitMessage() {
            const userInput = document.getElementById("user-input").value;
            const chatBox = document.getElementById("chat-box");

            if (userInput.trim() !== "") {
                // 显示用户输入
                const userMessage = document.createElement("div");
                userMessage.classList.add("user-message");
                userMessage.innerHTML = `<p>${userInput}</p>`;
                chatBox.appendChild(userMessage);
                
                // 清空输入框
                document.getElementById("user-input").value = "";

                // 处理AI响应（这里简单模拟）
                const botMessage = document.createElement("div");
                botMessage.classList.add("bot-message");
                botMessage.innerHTML = `<p>您问的是：${userInput}。我会为您提供相关的信息！</p>`;
                chatBox.appendChild(botMessage);

                // 自动滚动到底部
                chatBox.scrollTop = chatBox.scrollHeight;
            }
        }

        // 表单提交事件处理
        document.getElementById('contact-form').addEventListener('submit', function(event) {
            event.preventDefault(); // 阻止默认的表单提交行为

            // 获取表单数据
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.querySelector('textarea').value;

            // 显示反馈信息
            const feedbackDiv = document.getElementById('form-feedback');
            feedbackDiv.innerHTML = `<p>感谢您的留言，${name}！我们已收到您的信息，稍后会通过邮箱 <strong>${email}</strong> 与您联系。</p>`;

            // 清空表单
            document.getElementById('contact-form').reset();
        });
    </script>
</body>
</html>
