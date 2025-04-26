<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>同舟共济，心海护航 - 支持中国海员心理健康研究</title>
    <!-- 基础样式与动画 CSS -->
    <style>
        /* 基础样式 */
        body {
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; /* 更现代的字体 */
            line-height: 1.7;
            margin: 0;
            padding: 0;
            color: #333;
            background-color: #f8f9fa; /* 淡灰色背景 */
        }
        .container {
            max-width: 960px;
            margin: 0 auto;
            padding: 20px;
            overflow: hidden; /* 防止动画元素溢出 */
        }
        h1, h2, h3 {
            color: #003366; /* 深海军蓝 */
            font-weight: 600; /* 稍粗字体 */
        }
        h1 {
            font-size: 2.8em;
            text-align: center;
            margin-bottom: 15px;
        }
        h2 {
            font-size: 2em;
            border-bottom: 3px solid #FF9900; /* 亮橙色下划线 */
            padding-bottom: 8px;
            margin-top: 50px;
            margin-bottom: 25px; /* 增加标题下方间距 */
        }
        h3 {
            font-size: 1.4em;
            color: #0055A4; /* 稍亮的蓝色 */
            margin-top: 30px;
        }
        p {
            margin-bottom: 1.2em; /* 段落间距 */
            color: #555; /* 深灰色文字 */
        }
        /* 通用图片样式 (保留，以防未来需要) */
        /* img {
            max-width: 100%;
            height: auto;
            display: block;
            margin: 30px auto;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        } */

        /* 各区域样式 */
        .hero {
            background-image: url('https://images.pexels.com/photos/1631677/pexels-photo-1631677.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'); /* 海洋/天空背景图 */
            background-size: cover;
            background-position: center;
            height: 400px; /* 设定一个高度以显示背景 */
            display: flex; /* 使用 Flexbox 居中内容 */
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white; /* 文字改为白色 */
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* 添加文字阴影以提高可读性 */
            padding: 60px 20px; /* 保留内边距 */
            text-align: center;
            margin-bottom: 40px;
        }
        .hero h1 { /* 确保标题也是白色 */
             color: white;
        }
        .hero .subtitle {
            font-size: 1.3em;
            color: #eee; /* 副标题也用浅色 */
            margin-bottom: 30px;
        }
        .goal-card {
            border: 1px solid #ddd;
            padding: 20px;
            margin-bottom: 20px;
            background-color: #fff; /* 白色卡片背景 */
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease; /* 为悬停效果添加过渡 */
        }
        .goal-card:hover {
             transform: translateY(-5px); /* 悬停时轻微上移 */
             box-shadow: 0 6px 12px rgba(0,0,0,0.1); /* 悬停时阴影加深 */
        }
        #invitation ul {
            list-style: none;
            padding-left: 0;
        }
        #invitation li {
            margin-bottom: 15px;
            padding-left: 30px;
            position: relative;
            font-size: 1.1em;
        }
        #invitation li::before {
            content: '★'; /* 使用五角星 */
            color: #FF9900; /* 橙色 */
            position: absolute;
            left: 0;
            font-size: 1.2em;
            top: 2px;
        }
        #contact p {
            margin: 8px 0;
            font-size: 1.1em;
        }
        footer {
            background-color: #343a40; /* 深灰色页脚 */
            color: #fff;
            text-align: center;
            padding: 30px 20px;
            margin-top: 60px;
        }
        footer p {
            margin: 5px 0;
            color: #f8f9fa; /* 页脚亮色文字 */
        }
        footer .acknowledgements {
            font-size: 0.9em;
            color: #adb5bd; /* 页脚稍暗文字 */
        }
        strong {
            color: #D9534F; /* 红色强调 */
            font-weight: bold;
        }

        /* === 动画定义 === */
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeInLeft { from { opacity: 0; transform: translateX(-50px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes fadeInRight { from { opacity: 0; transform: translateX(50px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes scaleUp { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }


        /* === 动画应用 === */
        .animate {
            opacity: 0; /* 初始状态隐藏，等待动画 */
            animation-fill-mode: forwards; /* 动画结束后保持最后状态 */
            animation-duration: 0.8s; /* 默认动画时长 */
            animation-timing-function: ease-out; /* 缓动函数 */
        }

        /* 应用动画到具体元素 */
        .hero h1.animate { animation-name: fadeInUp; animation-delay: 0.1s; }
        .hero p.subtitle.animate { animation-name: fadeInUp; animation-delay: 0.3s; }

        #acknowledgement .container > h2.animate,
        #urgency .container > h2.animate,
        #research .container > h2.animate,
        #invitation .container > h2.animate, /* 邀请部分的标题动画保留 */
        #vision .container > h2.animate,
        #contact .container > h2.animate { animation-name: fadeInLeft; animation-delay: 0.2s; }

        #acknowledgement .container > p.animate,
        #urgency .container > p.animate,
        #research .container > p.animate,
        #invitation .container > p.animate, /* 邀请部分的段落动画保留 */
        #vision .container > p.animate,
        #contact .container > p.animate { animation-name: fadeInRight; animation-delay: 0.4s; }

        #research .goal-card.animate { animation-name: scaleUp; /* 延迟效果在下面单独加 */ }
        /* === 修改: 移除对邀请列表项的动画规则 === */
        /* #invitation ul.animate > li { animation-name: fadeInUp; } */

        /* 为列表项和卡片添加交错延迟效果 */
        #research .goal-card.animate:nth-child(odd) { animation-delay: 0.5s; } /* 奇数卡片 */
        #research .goal-card.animate:nth-child(even) { animation-delay: 0.7s; } /* 偶数卡片 */

        /* === 修改: 移除对邀请列表项的动画延迟规则 === */
        /* #invitation ul.animate > li:nth-child(1) { animation-delay: 0.5s; } */
        /* #invitation ul.animate > li:nth-child(2) { animation-delay: 0.7s; } */

    </style>
</head>
<body>

    <!-- 1. 首屏/英雄区域 -->
    <header class="hero" id="hero">
        <div class="container">
            <h1 class="animate fadeInUp">致敬海洋守护者：同舟共济，心海护航</h1>
            <p class="subtitle animate fadeInUp">诚邀您支持首个《中国海员SCL-90心理健康常模》建立研究</p>
        </div>
    </header>

    <main>
        <!-- 2. 第一部分：致敬与理解 -->
        <section id="acknowledgement">
            <div class="container">
                <h2 class="animate fadeInLeft">致每一位乘风破浪的您：责任与荣光</h2>
                <p class="animate fadeInRight">当这封信经由电波传递至茫茫大海，我满怀敬意地想到您和您的船员们正在世界某处的海域上坚守岗位，为国家航运事业默默奉献。作为大连海事大学的研究人员，我深知海员职业的艰辛与伟大。</p>
                <p class="animate fadeInRight">你们是连接世界的蓝色动脉，是国家航运的基石。我们深知，这份荣光背后，是常人难以想象的付出与挑战：远离亲友的孤寂、变幻莫测的风险、日夜颠倒的辛劳……</p>
            </div>
        </section>

        <!-- 3. 第二部分：为何研究至关重要 -->
        <section id="urgency">
            <div class="container">
                <h2 class="animate fadeInLeft">一座亟待填补的灯塔：中国海员心理健康的“航海图”</h2>
                <p class="animate fadeInRight">中国有近 <strong>40万</strong> 持证海员活跃在全球航线上，他们远离家乡，忍受着常人难以想象的孤独与压力。然而遗憾的是，作为如此重要的职业群体，中国海员至今没有专属的心理健康评估标准。</p>
                <p class="animate fadeInRight">这意味着，我们对海员群体的心理状况了解不足，无法提供有针对性的支持与服务。这不仅关乎每位海员的个人福祉，也直接影响航行安全，进而关系到我国航运事业的长远发展。</p>
                <p class="animate fadeInRight">船长，您比任何人都更了解海上生活的艰辛。长期远离亲人，有限的通讯条件，单调的船上生活，不可预测的海况和天气变化，以及沉重的工作责任，这一切都考验着每位海员的心理承受能力。正如船舶需要定期检修以确保航行安全，海员的心理健康同样需要专业的关注与呵护。</p>
            </div>
        </section>

        <!-- 4. 第三部分：我们的行动与目标 -->
        <section id="research">
            <div class="container">
                <h2 class="animate fadeInLeft">《中国海员SCL-90常模建立研究》：为了更好的守护</h2>
                <p class="animate fadeInRight">我们正在开展的《中国海员SCL-90常模建立研究》，旨在为中国海员建立专属的心理健康评估标准，填补这一领域的空白。这不仅是一次科学调查，更是对海员群体的深切关怀。</p>
                <div class="goal-card animate scaleUp">
                    <h3>目标一：建立常模</h3>
                    <p>建立中国首个海员专属SCL-90心理健康常模，填补空白，为科学关怀奠定基石。</p>
                </div>
                <div class="goal-card animate scaleUp">
                    <h3>目标二：了解现状</h3>
                    <p>了解当前海员在航期间真实的整体心理健康水平，为行业支持策略提供依据。</p>
                </div>
                 <p class="animate fadeInRight">我们使用的是结合海员工作情境改良的量表，力求反映真实状况。</p>
            </div>
        </section>

        <!-- 5. 第四部分：船长的关键角色与诚挚邀请 -->
        <section id="invitation">
            <div class="container">
                <h2 class="animate fadeInLeft">船长，您是这艘“研究之船”的关键舵手！</h2>
                <p class="animate fadeInRight">问卷调查的成功与否，很大程度上取决于您的支持与协助！您是航船的灵魂，更是船员弟兄们的‘大家长’。这项研究的成败，离不开您的鼎力支持！</p>
                <p class="animate fadeInRight"><strong>我们诚挚邀请您：</strong></p>
                 <!-- === 修改: 移除了 ul 和 li 的 animate 类 === -->
                <ul>
                    <li><strong>传递意义：</strong> 在工作会议或合适场合，向全体船员介绍这项研究对他们自身及整个群体的重要性。请告诉他们，他们的每一个回答，都将为中国海员群体的未来福祉贡献一份力量。</li>
                    <li><strong>鼓励参与：</strong> 动员大家本着自愿原则，抽出宝贵的 <strong>8-10分钟</strong> 时间完成线上问卷。请让他们放心，所有数据将 <strong>严格保密</strong>，仅用于整体统计分析，绝不涉及个人评价。</li>
                </ul>
                <p class="animate fadeInRight">我们深知海员工作繁忙，填写调查问卷需要耐心。但正如您领航穿越风暴一样，您的鼓励将极大地提升船员参与的积极性。这不仅是为研究贡献数据，更是为所有中国海员的心理健康事业播下希望的种子。</p>
            </div>
        </section>

        <!-- 6. 第五部分：未来的愿景与感谢 -->
        <section id="vision">
            <div class="container">
                <h2 class="animate fadeInLeft">您今天的支持，将照亮中国海员心理健康研究的明天</h2>
                <p class="animate fadeInRight">当研究完成后，我们将建立中国第一个海员心理健康评估标准，为海员群体的心理健康服务提供科学依据。这一切离不开您和您船员们的宝贵参与。</p>
                <p class="animate fadeInRight">在这片蓝色的海洋上，您不仅承载着货物，更承载着国家的希望和家人的期盼。现在，请您也为这项关乎海员未来的研究，贡献您宝贵的力量。</p>
                <p class="animate fadeInRight">衷心感谢您的阅读与支持！期待您的船员们积极参与问卷调查。祝您和全体船员一帆风顺，平安幸福！</p>
            </div>
        </section>

        <!-- 7. 联系信息区域 -->
        <section id="contact">
            <div class="container">
                <h2 class="animate fadeInLeft">联系我们</h2>
                <p class="animate fadeInRight"><strong>杨传勇 教授：</strong> 13700095559 | davidyang@dlmu.edu.cn</p>
                <p class="animate fadeInRight"><strong>崔天雪 老师：</strong> 15792452217 | tianxuecui@dlmu.edu.cn</p>
                <p class="animate fadeInRight"><strong>研究团队：</strong> 大连海事大学</p>
            </div>
        </section>
    </main>

    <!-- 8. 页脚 -->
    <footer>
        <div class="container">
            <p>&copy; 2024 大连海事大学 《中国海员SCL-90常模建立研究》项目组. 保留所有权利.</p>
            <p class="acknowledgements">
                资助单位：华洋海事中心有限公司 | 支持单位：航海类专业就业工作协作组
            </p>
        </div>
    </footer>

    <!-- JavaScript 文件链接 (可选，用于更复杂的交互或动画) -->
    <!-- <script src="script.js"></script> -->

</body>
</html>
