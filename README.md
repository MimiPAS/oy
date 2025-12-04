<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ทายนิสัยจากอาหารที่คุณชอบ | FoodMind</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 40px 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .header p {
            font-size: 1.1em;
            opacity: 0.95;
        }

        .nav-tabs {
            display: flex;
            background: #f8f9fa;
            border-bottom: 2px solid #e0e0e0;
        }

        .nav-tab {
            flex: 1;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            border: none;
            background: none;
            font-size: 1.1em;
            font-weight: 600;
            color: #666;
        }

        .nav-tab:hover {
            background: #e9ecef;
        }

        .nav-tab.active {
            background: white;
            color: #667eea;
            border-bottom: 3px solid #667eea;
        }

        .content {
            padding: 40px 30px;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .food-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .food-item {
            text-align: center;
            padding: 20px;
            border: 3px solid #e0e0e0;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s;
            background: white;
        }

        .food-item:hover {
            transform: translateY(-5px);
            border-color: #667eea;
            box-shadow: 0 10px 25px rgba(102,126,234,0.3);
        }

        .food-item.selected {
            border-color: #667eea;
            background: linear-gradient(135deg, #667eea15 0%, #764ba215 100%);
            transform: scale(1.05);
        }

        .food-icon {
            font-size: 3em;
            margin-bottom: 10px;
        }

        .food-name {
            font-weight: 600;
            color: #333;
        }

        .btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 1.05em;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
            display: inline-block;
            margin-top: 10px;
        }

        .btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102,126,234,0.4);
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .result-card {
            background: linear-gradient(135deg, #f093fb15 0%, #f5576c15 100%);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border-left: 5px solid #f5576c;
        }

        .result-card h3 {
            color: #f5576c;
            font-size: 1.6em;
            margin-bottom: 10px;
        }

        .result-card p {
            line-height: 1.8;
            color: #444;
            font-size: 1.02em;
            margin-bottom: 10px;
        }

        .traits {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 10px;
        }

        .trait-tag {
            background: #667eea;
            color: white;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.9em;
        }

        .nutrition-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin: 15px 0;
            box-shadow: 0 5px 15px rgba(0,0,0,0.06);
            border-left: 5px solid #667eea;
        }

        .nutrition-card h3 {
            color: #667eea;
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        .nutrition-card ul {
            list-style-position: inside;
            line-height: 1.8;
            color: #555;
        }

        .nutrition-card li {
            margin: 5px 0;
        }

        .category-section {
            margin: 25px 0;
        }

        .category-title {
            color: #333;
            font-size: 1.4em;
            margin-bottom: 10px;
            padding-bottom: 8px;
            border-bottom: 2px solid #e0e0e0;
        }

        .tips-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }

        .tip-card {
            background: linear-gradient(135deg, #667eea15 0%, #764ba215 100%);
            padding: 18px;
            border-radius: 12px;
            border-left: 4px solid #667eea;
        }

        .tip-card h4 {
            color: #667eea;
            margin-bottom: 8px;
        }

        .tip-card p {
            color: #555;
            line-height: 1.6;
        }

        .hidden {
            display: none;
        }

        /* Diary & avatar */
        .diary-grid {
            display: grid;
            grid-template-columns: minmax(0, 1.4fr) minmax(0, 1fr);
            gap: 20px;
            margin-top: 10px;
        }

        .diary-form label {
            font-size: 0.95em;
            color: #555;
            display: block;
            margin-bottom: 5px;
        }

        .diary-form input,
        .diary-form select {
            width: 100%;
            padding: 8px 10px;
            border-radius: 8px;
            border: 1px solid #d0d0d0;
            margin-bottom: 10px;
            font-size: 0.95em;
        }

        .diary-list {
            max-height: 220px;
            overflow-y: auto;
            padding-left: 15px;
            font-size: 0.95em;
            color: #444;
        }

        .diary-list li {
            margin-bottom: 4px;
        }

        .avatar-card {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 8px 20px rgba(0,0,0,0.12);
        }

        .avatar-emoji {
            font-size: 3rem;
            margin-bottom: 8px;
        }

        .avatar-title {
            font-weight: 700;
            margin-bottom: 5px;
            color: #4b3b3b;
        }

        .avatar-text {
            font-size: 0.96em;
            color: #4b3b3b;
            line-height: 1.5;
        }

        /* 🎮 GAME ZONE STYLES */
        #foodmind-game {
            margin-top: 10px;
            padding: 20px;
            border-radius: 18px;
            background: linear-gradient(135deg, #667eea10 0%, #764ba210 100%);
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
        }

        #foodmind-game h2 {
            text-align: center;
            color: #333;
            margin-bottom: 8px;
        }

        .game-intro {
            text-align: center;
            margin-bottom: 18px;
            color: #555;
            font-size: 0.98em;
        }

        .game-mode-selector {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-bottom: 18px;
        }

        .game-mode-btn {
            border: none;
            border-radius: 999px;
            padding: 8px 18px;
            cursor: pointer;
            font-size: 0.95em;
            background: #f1f3ff;
            color: #555;
            font-weight: 600;
            transition: all 0.2s;
        }

        .game-mode-btn:hover {
            background: #e0e4ff;
            transform: translateY(-1px);
            box-shadow: 0 2px 6px rgba(0,0,0,0.12);
        }

        .game-mode-btn.active {
            background: #667eea;
            color: #fff;
        }

        #game-status-bar {
            background: #fff;
            border-radius: 12px;
            padding: 10px 12px;
            border-left: 4px solid #667eea;
            margin-bottom: 12px;
            font-size: 0.9em;
            display: none;
        }

        #game-status-bar .game-status-row {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 6px;
        }

        .timer-wrapper {
            margin-top: 8px;
        }

        .timer-label {
            font-size: 0.9em;
            margin-bottom: 4px;
            color: #555;
        }

        .timer-bar {
            width: 100%;
            height: 10px;
            border-radius: 999px;
            background: #e0e0ff;
            overflow: hidden;
        }

        #game-timer-fill {
            height: 100%;
            width: 100%;
            background: #ffb74d;
            transition: width 0.25s linear;
        }

        #game-question-card {
            background: #fff;
            border-radius: 12px;
            padding: 16px 18px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.04);
            margin-bottom: 14px;
            display: none;
        }

        #game-question-text {
            font-size: 1.02em;
            margin-bottom: 12px;
            color: #333;
        }

        #game-choices {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .game-choice-btn {
            width: 100%;
            text-align: left;
            border-radius: 10px;
            border: 1px solid #dcdcff;
            padding: 8px 10px;
            cursor: pointer;
            background: #f9f9ff;
            font-size: 0.95em;
            transition: all 0.15s;
        }

        .game-choice-btn:hover {
            background: #eef0ff;
            transform: translateY(-1px);
            box-shadow: 0 2px 5px rgba(0,0,0,0.06);
        }

        .game-choice-btn.correct {
            border-color: #66bb6a;
            background: #e8f5e9;
        }

        .game-choice-btn.incorrect {
            border-color: #ef5350;
            background: #ffebee;
        }

        #game-feedback {
            display: none;
            background: #f9fbe7;
            border-radius: 12px;
            padding: 10px 12px;
            margin-bottom: 12px;
            font-size: 0.95em;
        }

        #game-feedback-brief {
            font-weight: 600;
            margin-bottom: 4px;
        }

        #game-feedback-explain {
            color: #555;
            line-height: 1.6;
        }

        #game-next-btn,
        #game-restart-btn {
            margin-top: 8px;
            padding: 8px 18px;
            border-radius: 999px;
            border: none;
            cursor: pointer;
            font-size: 0.95em;
            background: #aed581;
            color: #234;
            font-weight: 600;
            transition: all 0.2s;
        }

        #game-next-btn:hover,
        #game-restart-btn:hover {
            background: #9ccc65;
            transform: translateY(-1px);
            box-shadow: 0 2px 6px rgba(0,0,0,0.15);
        }

        #game-result-box {
            display: none;
            background: #e3f2fd;
            border-radius: 12px;
            padding: 14px 16px;
            margin-top: 4px;
        }

        #game-result-box h3 {
            margin-top: 0;
            margin-bottom: 6px;
            color: #1e88e5;
        }

        #game-result-message {
            font-size: 0.95em;
            color: #444;
            margin-bottom: 8px;
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 1.9em;
            }
            
            .food-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .nav-tab {
                font-size: 0.9em;
                padding: 15px 10px;
            }

            .diary-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🍽️ FoodMind</h1>
            <p>เลือกอาหารที่คุณชอบ แล้วค้นพบนิสัยของตัวเอง พร้อมเคล็ดลับโภชนาการแบบส่วนตัว</p>
        </div>

        <div class="nav-tabs">
            <button class="nav-tab active" onclick="switchTab('quiz')">🎯 ทายนิสัย & Diary</button>
            <button class="nav-tab" onclick="switchTab('nutrition')">🥗 Nutrition</button>
            <button class="nav-tab" onclick="switchTab('tips')">💡 เคล็ดลับ</button>
            <!-- 🎮 แท็บใหม่ Game Zone -->
            <button class="nav-tab" onclick="switchTab('game')">🎮 Game Zone</button>
        </div>

        <div class="content">
            <!-- Tab 1: Quiz + AI + Diary -->
            <div id="quiz" class="tab-content active">
                <h2 style="text-align: center; color: #333; margin-bottom: 20px;">เลือกอาหารที่คุณชอบที่สุด</h2>
                
                <div class="food-grid" id="foodGrid">
                    <div class="food-item" data-food="pizza">
                        <div class="food-icon">🍕</div>
                        <div class="food-name">พิซซ่า</div>
                    </div>
                    <div class="food-item" data-food="salad">
                        <div class="food-icon">🥗</div>
                        <div class="food-name">สลัด</div>
                    </div>
                    <div class="food-item" data-food="sushi">
                        <div class="food-icon">🍣</div>
                        <div class="food-name">ซูชิ</div>
                    </div>
                    <div class="food-item" data-food="burger">
                        <div class="food-icon">🍔</div>
                        <div class="food-name">เบอร์เกอร์</div>
                    </div>
                    <div class="food-item" data-food="ramen">
                        <div class="food-icon">🍜</div>
                        <div class="food-name">ราเมง</div>
                    </div>
                    <div class="food-item" data-food="fruit">
                        <div class="food-icon">🍎</div>
                        <div class="food-name">ผลไม้</div>
                    </div>
                    <div class="food-item" data-food="curry">
                        <div class="food-icon">🍛</div>
                        <div class="food-name">แกง</div>
                    </div>
                    <div class="food-item" data-food="dessert">
                        <div class="food-icon">🍰</div>
                        <div class="food-name">ของหวาน</div>
                    </div>
                </div>

                <div style="text-align: center;">
                    <button class="btn" onclick="analyzePersonality()" id="analyzeBtn" disabled>วิเคราะห์นิสัย & Health Insight</button>
                </div>

                <div id="result" class="hidden"></div>

                <!-- AI Health Insight -->
                <div id="healthInsight" class="hidden">
                    <div class="nutrition-card">
                        <h3>🧠 คำแนะนำสุขภาพส่วนตัว (Health Insight)</h3>
                        <p id="healthText" style="line-height:1.7; color:#444;"></p>
                    </div>
                </div>

                <!-- Diary + Avatar -->
                <div class="category-section">
                    <h3 class="category-title">📔 My Food Diary & Avatar</h3>
                    <p style="color:#555; font-size:0.95em; margin-bottom:10px;">
                        บันทึกเมนูที่คุณกิน แล้วดูว่าไลฟ์สไตล์การกินของคุณส่งผลต่ออวาตาร์อย่างไร
                    </p>

                    <div class="diary-grid">
                        <div>
                            <div class="nutrition-card diary-form">
                                <h3>✍️ บันทึกเมนูวันนี้</h3>
                                <label for="diaryDate">วันที่</label>
                                <input type="date" id="diaryDate">

                                <label for="diaryFoodSelect">เมนูที่กิน</label>
                                <select id="diaryFoodSelect">
                                    <option value="">-- เลือกเมนู --</option>
                                    <option value="pizza">พิซซ่า 🍕</option>
                                    <option value="salad">สลัด 🥗</option>
                                    <option value="sushi">ซูชิ 🍣</option>
                                    <option value="burger">เบอร์เกอร์ 🍔</option>
                                    <option value="ramen">ราเมง 🍜</option>
                                    <option value="fruit">ผลไม้ 🍎</option>
                                    <option value="curry">แกง 🍛</option>
                                    <option value="dessert">ของหวาน 🍰</option>
                                </select>

                                <button class="btn" style="margin-top:5px;" onclick="addDiaryEntry()">บันทึกเมนู</button>

                                <div style="margin-top:15px;">
                                    <strong>รายการที่บันทึก (ล่าสุด):</strong>
                                    <ul id="diaryList" class="diary-list"></ul>
                                </div>

                                <div id="diarySummary" style="margin-top:10px; font-size:0.95em; color:#444;"></div>
                            </div>
                        </div>

                        <div>
                            <div class="avatar-card" id="avatarCard">
                                <div class="avatar-emoji" id="avatarEmoji">🙂</div>
                                <div class="avatar-title" id="avatarTitle">Balanced Buddy</div>
                                <div class="avatar-text" id="avatarText">
                                    เริ่มบันทึกเมนู แล้วมาดูว่าอวาตาร์ของคุณจะเปลี่ยนไปอย่างไรบ้าง!
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>

            <!-- Tab 2: Nutrition -->
            <div id="nutrition" class="tab-content">
                <h2 style="text-align: center; color: #333; margin-bottom: 30px;">ความรู้เรื่อง Nutrition</h2>

                <div class="category-section">
                    <h3 class="category-title">📊 หลัก 5 หมู่อาหาร</h3>
                    <div class="nutrition-card">
                        <h3>🍚 หมู่ 1: คาร์โบไฮเดรต</h3>
                        <ul>
                            <li>ให้พลังงานแก่ร่างกาย</li>
                            <li>ตัวอย่าง: ข้าว ขนมปัง มัน เผือก</li>
                            <li>ควรกิน: 45-65% ของแคลอรีรวมต่อวัน</li>
                            <li>เลือกคาร์โบเชิงซ้อนเพื่อพลังงานยาวนาน</li>
                        </ul>
                    </div>

                    <div class="nutrition-card">
                        <h3>🥩 หมู่ 2: โปรตีน</h3>
                        <ul>
                            <li>สร้างและซ่อมแซมเนื้อเยื่อ</li>
                            <li>ตัวอย่าง: เนื้อสัตว์ ปลา ไข่ ถั่ว</li>
                            <li>ควรกิน: 10-35% ของแคลอรีรวมต่อวัน</li>
                            <li>เลือกโปรตีนไขมันต่ำเพื่อสุขภาพหัวใจ</li>
                        </ul>
                    </div>

                    <div class="nutrition-card">
                        <h3>🥛 หมู่ 3: แคลเซียม</h3>
                        <ul>
                            <li>บำรุงกระดูกและฟัน</li>
                            <li>ตัวอย่าง: นม โยเกิร์ต เต้าหู้ ผักใบเขียว</li>
                            <li>ควรกิน: 2-3 ส่วนต่อวัน</li>
                            <li>สำคัญสำหรับทุกวัยโดยเฉพาะเด็กและผู้สูงอายุ</li>
                        </ul>
                    </div>

                    <div class="nutrition-card">
                        <h3>🥕 หมู่ 4: วิตามินและแร่ธาตุ</h3>
                        <ul>
                            <li>เสริมสร้างภูมิคุ้มกัน</li>
                            <li>ตัวอย่าง: ผัก ผลไม้หลากสี</li>
                            <li>ควรกิน: 5-9 ส่วนต่อวัน</li>
                            <li>กินให้หลากหลายสีเพื่อได้สารอาหารครบ</li>
                        </ul>
                    </div>

                    <div class="nutrition-card">
                        <h3>🥑 หมู่ 5: ไขมัน</h3>
                        <ul>
                            <li>ช่วยดูดซึมวิตามินบางชนิด</li>
                            <li>ตัวอย่าง: น้ำมันพืช ถั่ว อะโวคาโด</li>
                            <li>ควรกิน: 20-35% ของแคลอรีรวมต่อวัน</li>
                            <li>เลือกไขมันดี (ไม่อิ่มตัว) หลีกเลี่ยงไขมันทรานส์</li>
                        </ul>
                    </div>
                </div>

                <div class="category-section">
                    <h3 class="category-title">💧 ความสำคัญของน้ำ</h3>
                    <div class="nutrition-card">
                        <ul>
                            <li>ควรดื่มน้ำ 8-10 แก้วต่อวัน (2-2.5 ลิตร)</li>
                            <li>ช่วยในการขับถ่ายและล้างสารพิษ</li>
                            <li>รักษาอุณหภูมิร่างกาย</li>
                            <li>ช่วยในการย่อยอาหารและดูดซึมสารอาหาร</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- Tab 3: Tips -->
            <div id="tips" class="tab-content">
                <h2 style="text-align: center; color: #333; margin-bottom: 30px;">เคล็ดลับสุขภาพดี</h2>

                <div class="category-section">
                    <h3 class="category-title">🌟 พื้นฐานการกินดี</h3>
                    <div class="tips-grid">
                        <div class="tip-card">
                            <h4>⏰ กินให้ตรงเวลา</h4>
                            <p>กินให้ครบ 3 มื้อหลัก เว้นระยะ 4-5 ชั่วโมง ช่วยให้ระบบย่อยอาหารทำงานได้ดี</p>
                        </div>
                        <div class="tip-card">
                            <h4>🌈 กินให้หลากหลาย</h4>
                            <p>เลือกกินผักผลไม้หลายสี แต่ละสีให้สารอาหารต่างกัน ยิ่งหลากหลายยิ่งดี</p>
                        </div>
                        <div class="tip-card">
                            <h4>🍽️ ปริมาณที่เหมาะสม</h4>
                            <p>กินพอดี ไม่มากเกินไป ใช้จานเล็กช่วยควบคุมปริมาณ เคี้ยวช้าๆ ให้ทันรู้สึกอิ่ม</p>
                        </div>
                        <div class="tip-card">
                            <h4>🥤 ลดน้ำตาลและเกลือ</h4>
                            <p>ลดเครื่องดื่มหวาน ของทอด อาหารรสจัด เพื่อสุขภาพหัวใจและไต</p>
                        </div>
                    </div>
                </div>

                <div class="category-section">
                    <h3 class="category-title">🏃 ไลฟ์สไตล์สุขภาพดี</h3>
                    <div class="tips-grid">
                        <div class="tip-card">
                            <h4>💪 ออกกำลังกายสม่ำเสมอ</h4>
                            <p>อย่างน้อยสัปดาห์ละ 3-5 วัน วันละ 30 นาที ช่วยเผาผลาญและเสริมสร้างกล้ามเนื้อ</p>
                        </div>
                        <div class="tip-card">
                            <h4>😴 นอนหลับพักผ่อนเพียงพอ</h4>
                            <p>นอน 7-8 ชั่วโมงต่อวัน ช่วยซ่อมแซมร่างกายและควบคุมฮอร์โมนความหิว</p>
                        </div>
                        <div class="tip-card">
                            <h4>🧘 จัดการความเครียด</h4>
                            <p>ฝึกสมาธิ ทำโยคะ หรือทำกิจกรรมที่ชอบ ความเครียดส่งผลต่อการกินและสุขภาพ</p>
                        </div>
                        <div class="tip-card">
                            <h4>📝 จดบันทึกการกิน</h4>
                            <p>บันทึกอาหารที่กินแต่ละวัน ช่วยให้รู้ว่ากินอะไรไปบ้าง และปรับปรุงได้</p>
                        </div>
                    </div>
                </div>

                <div class="category-section">
                    <h3 class="category-title">🍎 อาหารที่ควรกินบ่อยๆ</h3>
                    <div class="nutrition-card">
                        <ul>
                            <li><strong>ผักใบเขียวเข้ม:</strong> บรอกโคลี ผักโขม คะน้า อุดมไปด้วยวิตามินและเส้นใย</li>
                            <li><strong>ปลาทะเล:</strong> แซลมอน ทูน่า มีโอเมก้า-3 ดีต่อสมองและหัวใจ</li>
                            <li><strong>ถั่วและธัญพืช:</strong> ถั่วเหลือง ข้าวกล้อง ควินัว อุดมโปรตีนและเส้นใย</li>
                            <li><strong>ผลเบอร์รี่:</strong> บลูเบอร์รี่ สตรอเบอร์รี่ มีสารต้านอนุมูลอิสระสูง</li>
                            <li><strong>ถั่วและเมล็ดพืช:</strong> อัลมอนด์ เชีย ฟลักซ์ซีด ให้ไขมันดีและโปรตีน</li>
                        </ul>
                    </div>
                </div>

                <div class="category-section">
                    <h3 class="category-title">⚠️ อาหารที่ควรหลีกเลี่ยง</h3>
                    <div class="nutrition-card">
                        <ul>
                            <li><strong>อาหารแปรรูปสูง:</strong> มักมีเกลือ น้ำตาล ไขมันทรานส์สูง</li>
                            <li><strong>เครื่องดื่มน้ำตาลสูง:</strong> น้ำอัดลม น้ำหวาน ชาเย็น กาแฟหวาน</li>
                            <li><strong>อาหารทอดและไขมันสูง:</strong> ทำให้ได้แคลอรีมากเกินไป</li>
                            <li><strong>เนื้อแปรรูป:</strong> ไส้กรอก แฮม เบคอน มีสารกันบูดและเกลือสูง</li>
                            <li><strong>ขนมขบเคี้ยว:</strong> มักมีแคลอรีสูง คุณค่าทางโภชนาการต่ำ</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- Tab 4: GAME ZONE -->
            <div id="game" class="tab-content">
                <div id="foodmind-game">
                    <h2>🎮 FoodMind Game Zone</h2>
                    <p class="game-intro">
                        Gamified Learning + Active Recall  
                        เลือกโหมดเกม แล้วตอบคำถามให้ทันเวลาก่อนหมดเวลา!
                    </p>

                    <!-- โหมดเกม -->
                    <div class="game-mode-selector">
                        <button class="game-mode-btn" data-mode="healthy">🥦 Healthy Quiz</button>
                        <button class="game-mode-btn" data-mode="decision">🍽️ Food Decision</button>
                        <button class="game-mode-btn" data-mode="label">🏷️ Label Challenge</button>
                    </div>

                    <!-- สถานะเกม -->
                    <div id="game-status-bar">
                        <div class="game-status-row">
                            <div>โหมด: <span id="game-mode-name">-</span></div>
                            <div>คะแนน: <span id="game-score">0</span> ⭐</div>
                            <div>ข้อที่ <span id="game-q-index">0</span>/<span id="game-q-total">0</span></div>
                        </div>
                        <div class="timer-wrapper">
                            <div class="timer-label">⏱️ เวลา: <span id="game-time-left">20</span> วินาที</div>
                            <div class="timer-bar">
                                <div id="game-timer-fill"></div>
                            </div>
                        </div>
                    </div>

                    <!-- คำถาม -->
                    <div id="game-question-card">
                        <div id="game-question-text"></div>
                        <div id="game-choices"></div>
                    </div>

                    <!-- feedback -->
                    <div id="game-feedback">
                        <div id="game-feedback-brief"></div>
                        <div id="game-feedback-explain"></div>
                        <button id="game-next-btn">ข้อต่อไป ▶</button>
                    </div>

                    <!-- สรุปผล -->
                    <div id="game-result-box">
                        <h3>🎉 สรุปผลเกม</h3>
                        <p>คุณได้ <span id="game-final-score">0</span> คะแนน จากทั้งหมด <span id="game-final-total">0</span> คะแนน</p>
                        <p id="game-result-message"></p>
                        <button id="game-restart-btn">เล่นใหม่อีกครั้ง 🔄</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        let selectedFood = null;

        // ฐานข้อมูลนิสัย + health insight + หมวดหมู่สุขภาพ
        const personalities = {
            pizza: {
                title: "นักสังสรรค์ผู้เป็นมิตร 🎉",
                description: "คุณเป็นคนรักความสนุก ชอบอยู่กับเพื่อนฝูง มีบุคลิกเปิดเผยและเข้ากับใครได้ง่าย คุณมักเป็นศูนย์กลางของกลุ่มและชอบแบ่งปันความสุขกับคนรอบข้าง มีความคิดสร้างสรรค์และชอบลองของใหม่ๆ",
                traits: ["เข้ากับคนง่าย", "ชอบแบ่งปัน", "สนุกสนาน", "มีความคิดสร้างสรรค์"],
                health: "พิซซ่ามักจะมีแป้งและชีสค่อนข้างมาก ลองเพิ่มหน้าไฟเบอร์ เช่น ผัก เห็ด ข้าวโพด และจำกัดปริมาณชีส รวมถึงกินคู่กับสลัดผัก จะช่วยบาลานซ์มากขึ้นนะ",
                category: "indulgent"
            },
            salad: {
                title: "นักใช้ชีวิตสุขภาพดี 🌿",
                description: "คุณเป็นคนใส่ใจสุขภาพ มีวินัยในการดูแลตัวเอง รักการออกกำลังกาย และชอบความสมดุลในชีวิต คุณมักวางแผนอนาคตไว้ล่วงหน้า ชอบความเป็นระเบียบ และใส่ใจรายละเอียด",
                traits: ["ใส่ใจสุขภาพ", "มีวินัย", "วางแผนดี", "รักธรรมชาติ"],
                health: "สลัดเป็นตัวเลือกที่ดีต่อสุขภาพมากอยู่แล้ว ลองเน้นผักหลากสี โปรตีนดี เช่น ไก่ไม่ติดหนัง เต้าหู้ ถั่วต่าง ๆ และระวังน้ำสลัดที่หวานหรือมันเกินไป จะยิ่งทำให้มื้อสลัดนี้สมบูรณ์แบบ",
                category: "healthy"
            },
            sushi: {
                title: "ผู้รักความประณีต 🎨",
                description: "คุณเป็นคนที่ชื่นชมความงาม ใส่ใจรายละเอียด มีรสนิยมดี และชอบสิ่งที่มีคุณภาพ คุณเป็นคนสงบ นิ่งใจ และคิดรอบคอบก่อนตัดสินใจ มีความเคารพในวัฒนธรรมและประเพณี",
                traits: ["ละเอียดรอบคอบ", "รสนิยมดี", "สงบใจ", "เคารพประเพณี"],
                health: "ซูชิให้โปรตีนและคาร์โบไฮเดรตที่ดี แต่ควรระวังซอสเค็มและน้ำตาลในข้าวซูชิ เลือกเมนูที่มีปลา ไข่ ผัก และสลับกับซาชิมิหรือต้มยำ จะทำให้มื้อนี้เบาลงแต่ยังอร่อย",
                category: "mixed"
            },
            burger: {
                title: "นักผจญภัยผู้กล้าหาญ 🚀",
                description: "คุณเป็นคนตรงไปตรงมา ชอบความท้าทาย ไม่กลัวที่จะลองสิ่งใหม่ๆ มีพลังและความมั่นใจในตัวเอง ชอบความรวดเร็วและประสิทธิภาพ มักเป็นผู้นำในการตัดสินใจ",
                traits: ["กล้าหาญ", "ตรงไปตรงมา", "มีพลัง", "เป็นผู้นำ"],
                health: "เบอร์เกอร์ให้ทั้งโปรตีนและไขมัน ลองเลือกเนื้อไม่ติดมัน หรือเปลี่ยนเป็นเบอร์เกอร์ไก่ย่าง/ปลาย่าง เพิ่มผักในแซนด์วิช และหลีกเลี่ยงน้ำอัดลม+เฟรนช์ฟรายด้วย จะช่วยลดแคลอรีได้เยอะ",
                category: "indulgent"
            },
            ramen: {
                title: "นักเพลิดเพลินชีวิต 🎭",
                description: "คุณเป็นคนรักความสะดวกสบาย ชอบความอบอุ่น เห็นอกเห็นใจผู้อื่น และชอบดูแลคนรอบข้าง คุณมักหาความสุขในสิ่งเล็กๆ น้อยๆ มีความยืดหยุ่นและปรับตัวได้ดี",
                traits: ["อบอุ่น", "เห็นอกเห็นใจ", "ยืดหยุ่น", "มองโลกในแง่ดี"],
                health: "ราเมงมักมีน้ำซุปเค็มและเส้นคาร์โบไฮเดรตสูง ลองลดการซดน้ำซุป เลือกท็อปปิ้งเป็นผัก ไข่ และเนื้อไม่ติดมัน และเพิ่มผักเคียง จะช่วยให้มื้อนี้บาลานซ์มากขึ้น",
                category: "mixed"
            },
            fruit: {
                title: "ผู้บริสุทธิ์ใจดี 🌸",
                description: "คุณเป็นคนเรียบง่าย จริงใจ มองโลกในแง่ดี ชอบธรรมชาติและความสดใส มีพลังบวกที่ติดต่อได้ รักความสะอาดและชอบความเป็นระเบียบ มีจิตใจใฝ่ดี",
                traits: ["จริงใจ", "มองโลกในแง่ดี", "รักธรรมชาติ", "ใจดี"],
                health: "ผลไม้ให้วิตามิน ใยอาหาร และความสดชื่น ลองกินผลไม้สดแทนน้ำผลไม้กล่อง เพื่อลดน้ำตาล และผสมให้หลากหลายสี จะได้สารอาหารที่แตกต่างกันครบขึ้น",
                category: "healthy"
            },
            curry: {
                title: "นักผจญรสชาติ 🌶️",
                description: "คุณเป็นคนชอบความตื่นเต้น รักอิสระ ไม่ชอบความจำเจ ชอบสำรวจสิ่งใหม่ๆ มีความหลงใหลในวัฒนธรรมที่หลากหลาย กล้าแสดงออก และมีบุคลิกที่โดดเด่น",
                traits: ["ชอบความท้าทาย", "หลงใหลวัฒนธรรม", "กล้าแสดงออก", "โดดเด่น"],
                health: "แกงบางชนิดมีทั้งกะทิและน้ำมันค่อนข้างมาก ลองเลือกแกงที่น้ำใสมากขึ้น หรือเพิ่มผักและโปรตีนไม่ติดมัน และจำกัดปริมาณข้าว จะช่วยให้มื้อนี้ยังแซ่บแต่เบาลง",
                category: "indulgent"
            },
            dessert: {
                title: "นักฝันผู้โรแมนติก 💖",
                description: "คุณเป็นคนรักความสุข ชอบเฉลิมฉลอง มองหาแง่ดีของชีวิต มีจินตนาการสูงและชอบสิ่งที่สวยงาม คุณเป็นคนละเอียดอ่อน รักความสุขของคนรอบข้าง และชอบทำให้ผู้อื่นยิ้ม",
                traits: ["โรแมนติก", "มีจินตนาการ", "ละเอียดอ่อน", "ใจดี"],
                health: "ของหวานช่วยเติมความสุข แต่ควรระวังน้ำตาลและไขมันสูง ลองแบ่งกินคนละครึ่งกับเพื่อน เลือกไซส์เล็ก หรือกินคู่กับผลไม้และน้ำเปล่าแทนน้ำหวาน จะช่วยบาลานซ์ได้ดี",
                category: "indulgent"
            }
        };

        const foodItems = document.querySelectorAll('.food-item');
        const resultDiv = document.getElementById('result');
        const analyzeBtn = document.getElementById('analyzeBtn');
        const healthInsightDiv = document.getElementById('healthInsight');
        const healthText = document.getElementById('healthText');

        // diary elements
        const diaryDateInput = document.getElementById('diaryDate');
        const diaryFoodSelect = document.getElementById('diaryFoodSelect');
        const diaryListEl = document.getElementById('diaryList');
        const diarySummaryEl = document.getElementById('diarySummary');

        // avatar elements
        const avatarEmojiEl = document.getElementById('avatarEmoji');
        const avatarTitleEl = document.getElementById('avatarTitle');
        const avatarTextEl = document.getElementById('avatarText');

        // set default date today
        function setToday() {
            const today = new Date();
            const yyyy = today.getFullYear();
            const mm = String(today.getMonth() + 1).padStart(2, '0');
            const dd = String(today.getDate()).padStart(2, '0');
            diaryDateInput.value = `${yyyy}-${mm}-${dd}`;
        }
        setToday();

        // อ่าน diary จาก localStorage
        function loadDiary() {
            const raw = localStorage.getItem('foodMindDiary');
            if (!raw) return [];
            try {
                const data = JSON.parse(raw);
                return Array.isArray(data) ? data : [];
            } catch {
                return [];
            }
        }

        function saveDiary(entries) {
            localStorage.setItem('foodMindDiary', JSON.stringify(entries));
        }

        // อัปเดตหน้าจอ diary
        function renderDiary() {
            const entries = loadDiary();
            diaryListEl.innerHTML = '';

            // แสดงล่าสุด 10 รายการ
            const lastEntries = [...entries].slice(-10).reverse();
            for (const e of lastEntries) {
                const li = document.createElement('li');
                const name = getFoodThaiName(e.food);
                li.textContent = `${e.date} – ${name}`;
                diaryListEl.appendChild(li);
            }

            updateDiarySummary(entries);
            updateAvatar(entries);
        }

        function getFoodThaiName(key) {
            switch (key) {
                case 'pizza': return 'พิซซ่า';
                case 'salad': return 'สลัด';
                case 'sushi': return 'ซูชิ';
                case 'burger': return 'เบอร์เกอร์';
                case 'ramen': return 'ราเมง';
                case 'fruit': return 'ผลไม้';
                case 'curry': return 'แกง';
                case 'dessert': return 'ของหวาน';
                default: return key;
            }
        }

        function addDiaryEntry() {
            const date = diaryDateInput.value;
            const food = diaryFoodSelect.value;

            if (!date || !food) {
                alert('กรุณาเลือกวันที่และเมนูที่ต้องการบันทึก');
                return;
            }

            const entries = loadDiary();
            entries.push({ date, food });
            saveDiary(entries);
            renderDiary();
        }

        function updateDiarySummary(allEntries) {
            if (!allEntries.length) {
                diarySummaryEl.textContent = "ยังไม่มีการบันทึกวันนี้ ลองเพิ่มเมนูแรกของคุณดูนะ 🙂";
                return;
            }
            const today = diaryDateInput.value;
            const todayEntries = allEntries.filter(e => e.date === today);

            if (!todayEntries.length) {
                diarySummaryEl.textContent = "วันนี้ยังไม่ได้บันทึกเมนู ลองเพิ่มอย่างน้อย 1 เมนูเพื่อดูสรุปพฤติกรรมการกินของคุณ";
                return;
            }

            let healthy = 0, indulgent = 0, mixed = 0;
            todayEntries.forEach(e => {
                const cat = personalities[e.food]?.category || 'mixed';
                if (cat === 'healthy') healthy++;
                else if (cat === 'indulgent') indulgent++;
                else mixed++;
            });

            let text = `สรุปของวันที่ ${today}: `;
            text += `เมนูสุขภาพดี ${healthy} รายการ, เมนูสายอร่อยจัดเต็ม ${indulgent} รายการ, เมนูผสม ${mixed} รายการ. `;

            if (healthy > indulgent) {
                text += "วันนี้ภาพรวมดีมาก! ร่างกายกำลังขอบคุณคุณอยู่เลย 💚";
            } else if (indulgent > healthy) {
                text += "วันนี้เมนูจัดหนักนิดนึง พรุ่งนี้ลองเพิ่มผัก ผลไม้ หรือน้ำเปล่าให้มากขึ้นนะ 🌿";
            } else {
                text += "วันนี้ค่อนข้างบาลานซ์ ลองเติมเมนูสุขภาพเล็กน้อยในมื้อต่อไปจะยิ่งดีขึ้น ✨";
            }

            diarySummaryEl.textContent = text;
        }

        function updateAvatar(allEntries) {
            if (!allEntries.length) {
                avatarEmojiEl.textContent = "🙂";
                avatarTitleEl.textContent = "Balanced Buddy";
                avatarTextEl.textContent = "เริ่มบันทึกเมนู แล้วมาดูว่าอวาตาร์ของคุณจะค่อย ๆ เปลี่ยนไปตามพฤติกรรมการกินนะ!";
                return;
            }

            let healthy = 0, indulgent = 0;
            allEntries.forEach(e => {
                const cat = personalities[e.food]?.category || 'mixed';
                if (cat === 'healthy') healthy++;
                else if (cat === 'indulgent') indulgent++;
            });

            const score = healthy - indulgent;

            if (score >= 3) {
                avatarEmojiEl.textContent = "💪😄";
                avatarTitleEl.textContent = "Healthy Hero";
                avatarTextEl.textContent = "อวาตาร์ของคุณสดใสและแข็งแรงมาก! พฤติกรรมการกินตอนนี้ดีต่อสุขภาพสุด ๆ เลย รักษา momentum นี้ไว้นะ 🌈";
            } else if (score <= -3) {
                avatarEmojiEl.textContent = "😋🍰";
                avatarTitleEl.textContent = "Sweet Tooth Explorer";
                avatarTextEl.textContent = "อวาตาร์ของคุณสายของอร่อยเต็มที่! ลองเติมผัก ผลไม้ และดื่มน้ำเปล่าเพิ่มอีกนิด เพื่อให้ร่างกายบาลานซ์มากขึ้น 💧🥦";
            } else {
                avatarEmojiEl.textContent = "🙂";
                avatarTitleEl.textContent = "Balanced Buddy";
                avatarTextEl.textContent = "ตอนนี้อวาตาร์ของคุณค่อนข้างบาลานซ์ดี ลองตั้งเป้าเพิ่มเมนูสุขภาพ 1–2 มื้อต่อวัน เพื่ออัปเกรดเป็น Healthy Hero ได้ไม่ยาก ✨";
            }
        }

        // เลือกอาหาร
        foodItems.forEach(item => {
            item.addEventListener('click', () => {
                foodItems.forEach(i => i.classList.remove('selected'));
                item.classList.add('selected');
                selectedFood = item.dataset.food;
                analyzeBtn.disabled = false;
            });
        });

        // ฟังก์ชันวิเคราะห์นิสัย + health insight
        function analyzePersonality() {
            if (!selectedFood || !personalities[selectedFood]) return;

            const p = personalities[selectedFood];

            resultDiv.classList.remove('hidden');
            resultDiv.innerHTML = `
                <div class="result-card">
                    <h3>${p.title}</h3>
                    <p>${p.description}</p>
                    <div class="traits">
                        ${p.traits.map(t => `<span class="trait-tag">${t}</span>`).join('')}
                    </div>
                </div>
            `;

            healthInsightDiv.classList.remove('hidden');
            healthText.textContent = p.health;

            resultDiv.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }

        // ฟังก์ชันสลับแท็บ
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.nav-tab').forEach(btn => {
                btn.classList.remove('active');
            });

            const activeTab = document.getElementById(tabId);
            if (activeTab) activeTab.classList.add('active');

            document.querySelectorAll('.nav-tab').forEach(btn => {
                const onclick = btn.getAttribute('onclick') || "";
                if (onclick.includes(`'${tabId}'`)) {
                    btn.classList.add('active');
                }
            });
        }

        // initial render diary & avatar
        renderDiary();

        /* =========================
           🎮 GAME ZONE SCRIPT
           ========================= */

        const gameModeButtons = document.querySelectorAll('.game-mode-btn');
        const gameStatusBar = document.getElementById('game-status-bar');
        const gameModeNameEl = document.getElementById('game-mode-name');
        const gameScoreEl = document.getElementById('game-score');
        const gameQIndexEl = document.getElementById('game-q-index');
        const gameQTotalEl = document.getElementById('game-q-total');
        const gameTimeLeftEl = document.getElementById('game-time-left');
        const gameTimerFillEl = document.getElementById('game-timer-fill');

        const gameQuestionCard = document.getElementById('game-question-card');
        const gameQuestionTextEl = document.getElementById('game-question-text');
        const gameChoicesEl = document.getElementById('game-choices');

        const gameFeedbackBox = document.getElementById('game-feedback');
        const gameFeedbackBriefEl = document.getElementById('game-feedback-brief');
        const gameFeedbackExplainEl = document.getElementById('game-feedback-explain');
        const gameNextBtn = document.getElementById('game-next-btn');

        const gameResultBox = document.getElementById('game-result-box');
        const gameFinalScoreEl = document.getElementById('game-final-score');
        const gameFinalTotalEl = document.getElementById('game-final-total');
        const gameResultMessageEl = document.getElementById('game-result-message');
        const gameRestartBtn = document.getElementById('game-restart-btn');

        const timePerQuestion = 20; // วินาที

        const gameQuestionsHealthy = [
            {
                question: "ข้อใดคือ \"หมู่คาร์โบไฮเดรต\" (หมู่ที่ 1) ?",
                choices: [
                    "นม โยเกิร์ต ผักใบเขียว",
                    "ข้าว ขนมปัง มัน เผือก",
                    "เนื้อไก่ ปลา ไข่ ถั่ว",
                    "ผลไม้และผักหลากสี"
                ],
                correctIndex: 1,
                explanation: "หมู่ที่ 1 คือคาร์โบไฮเดรต เช่น ข้าว ขนมปัง มัน เผือก ให้พลังงานกับร่างกาย"
            },
            {
                question: "ถ้าอยากได้โปรตีนแบบไขมันต่ำ ควรเลือกเมนูใด?",
                choices: [
                    "ไก่ทอดกรอบ",
                    "ปลานึ่งมะนาว",
                    "หมูสามชั้นทอด",
                    "ไส้กรอกทอด"
                ],
                correctIndex: 1,
                explanation: "ปลานึ่งมะนาวเป็นโปรตีนไขมันต่ำ ไม่ผ่านการทอด ช่วยลดไขมันอิ่มตัว"
            },
            {
                question: "ข้อใดคือประโยชน์หลักของผักและผลไม้หลากสี?",
                choices: [
                    "ให้แต่แคลอรีสูง",
                    "มีเกลือสูง",
                    "ให้วิตามิน แร่ธาตุ และใยอาหาร",
                    "ให้แต่ไขมันดี"
                ],
                correctIndex: 2,
                explanation: "ผักผลไม้หลากสีอุดมด้วยวิตามิน แร่ธาตุ และใยอาหาร ช่วยระบบขับถ่ายและภูมิคุ้มกัน"
            }
        ];

        const gameQuestionsDecision = [
            {
                question: "ถ้าอยากได้มื้อกลางวันที่สมดุลกว่า เลือกเมนูไหน?",
                choices: [
                    "ข้าวไก่ทอด + น้ำอัดลม",
                    "ข้าวกล้องอกไก่ย่าง + สลัดผัก + น้ำเปล่า"
                ],
                correctIndex: 1,
                explanation: "เมนูที่มีข้าวกล้อง โปรตีนไขมันต่ำ ผัก และน้ำเปล่า จะสมดุลกว่ามาก"
            },
            {
                question: "ของว่างหลังเลิกเรียน ข้อใดเหมาะสมกว่า?",
                choices: [
                    "มันฝรั่งทอดกรอบ + น้ำอัดลม",
                    "กล้วยหอม 1 ผล + นมจืด 1 แก้ว"
                ],
                correctIndex: 1,
                explanation: "กล้วย + นมจืด ช่วยให้อิ่มได้นานกว่า และน้ำตาลไม่พุ่งเท่า snack + น้ำหวาน"
            },
            {
                question: "ถ้าอยากลดน้ำตาล เลือกเครื่องดื่มอะไร?",
                choices: [
                    "ชานมไข่มุกหวานปกติ",
                    "น้ำเปล่า หรือ น้ำใบเตยไม่หวาน"
                ],
                correctIndex: 1,
                explanation: "น้ำเปล่าหรือน้ำสมุนไพรไม่หวาน ไม่มีน้ำตาลเพิ่ม เหมาะกับการลดน้ำตาล"
            }
        ];

        const gameQuestionsLabel = [
            {
                question: "บนฉลากเขียนว่า \"น้ำตาล 30 กรัม\" ต่อขวด เทียบกับ \"น้ำตาล 8 กรัม\" ต่อกล่อง เมนูใดเหมาะสมกว่า?",
                choices: [
                    "เครื่องดื่มที่มีน้ำตาล 30 กรัม",
                    "เครื่องดื่มที่มีน้ำตาล 8 กรัม"
                ],
                correctIndex: 1,
                explanation: "เลือกตัวเลือกที่มีน้ำตาลน้อยกว่า เพื่อลดความเสี่ยงโรคไม่ติดต่อเรื้อรัง"
            },
            {
                question: "ฉลาก A: พลังงาน 250 kcal / ถุง, ฉลาก B: พลังงาน 90 kcal / ถุง ถ้าอยากควบคุมน้ำหนักควรเลือกอะไร?",
                choices: [
                    "ฉลาก A",
                    "ฉลาก B"
                ],
                correctIndex: 1,
                explanation: "ฉลาก B ให้พลังงานน้อยกว่ามาก เหมาะกับการควบคุมน้ำหนัก"
            },
            {
                question: "สัญลักษณ์ \"ทางเลือกสุขภาพ\" (Healthier Choice) บนฉลาก บอกอะไรเรา?",
                choices: [
                    "เป็นอาหารที่ไม่มีแคลอรีเลย",
                    "เป็นตัวเลือกที่มีน้ำตาล ไขมัน หรือโซเดียมลดลงเมื่อเทียบกับสินค้าในกลุ่มเดียวกัน",
                    "กินได้ไม่จำกัดปริมาณ",
                    "เป็นอาหารสำหรับคนป่วยเท่านั้น"
                ],
                correctIndex: 1,
                explanation: "สัญลักษณ์นี้ช่วยบอกว่าเป็นตัวเลือกที่ดีกว่าในหมวดเดียวกัน แต่ก็ต้องกินอย่างพอเหมาะอยู่ดี"
            }
        ];

        const gameModeConfig = {
            healthy: {
                name: "Healthy Quiz – ความรู้พื้นฐานโภชนาการ",
                questions: gameQuestionsHealthy
            },
            decision: {
                name: "Food Decision – เลือกเมนูที่เหมาะสมกว่า",
                questions: gameQuestionsDecision
            },
            label: {
                name: "Label Challenge – อ่านฉลากโภชนาการ",
                questions: gameQuestionsLabel
            }
        };

        let gameCurrentMode = null;
        let gameCurrentQuestions = [];
        let gameCurrentIndex = 0;
        let gameScore = 0;
        let gameTimer = null;
        let gameTimeLeft = timePerQuestion;
        let gameAnswered = false;

        function gameShuffle(arr) {
            const a = [...arr];
            for (let i = a.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [a[i], a[j]] = [a[j], a[i]];
            }
            return a;
        }

        function gameStartMode(modeKey) {
            const config = gameModeConfig[modeKey];
            if (!config) return;

            gameCurrentMode = modeKey;
            gameCurrentQuestions = gameShuffle(config.questions);
            gameCurrentIndex = 0;
            gameScore = 0;

            gameModeNameEl.textContent = config.name;
            gameScoreEl.textContent = gameScore;
            gameQTotalEl.textContent = gameCurrentQuestions.length;

            gameStatusBar.style.display = "block";
            gameResultBox.style.display = "none";
            gameFeedbackBox.style.display = "none";

            gameModeButtons.forEach(btn => {
                btn.classList.toggle("active", btn.dataset.mode === modeKey);
            });

            gameShowQuestion();
        }

        function gameShowQuestion() {
            if (gameCurrentIndex >= gameCurrentQuestions.length) {
                gameEnd();
                return;
            }

            const q = gameCurrentQuestions[gameCurrentIndex];
            gameAnswered = false;
            gameQIndexEl.textContent = gameCurrentIndex + 1;

            gameQuestionTextEl.textContent = q.question;
            gameChoicesEl.innerHTML = "";
            q.choices.forEach((choice, idx) => {
                const btn = document.createElement("button");
                btn.className = "game-choice-btn";
                btn.textContent = choice;
                btn.addEventListener("click", () => gameHandleAnswer(idx));
                gameChoicesEl.appendChild(btn);
            });

            gameQuestionCard.style.display = "block";
            gameFeedbackBox.style.display = "none";

            gameStartTimer();
        }

        function gameStartTimer() {
            clearInterval(gameTimer);
            gameTimeLeft = timePerQuestion;
            gameTimeLeftEl.textContent = gameTimeLeft;
            gameTimerFillEl.style.width = "100%";

            gameTimer = setInterval(() => {
                gameTimeLeft--;
                if (gameTimeLeft < 0) {
                    clearInterval(gameTimer);
                    if (!gameAnswered) {
                        gameHandleTimeout();
                    }
                    return;
                }
                gameTimeLeftEl.textContent = gameTimeLeft;
                const percent = (gameTimeLeft / timePerQuestion) * 100;
                gameTimerFillEl.style.width = percent + "%";
            }, 1000);
        }

        function gameHandleAnswer(selectedIndex) {
            if (gameAnswered) return;
            gameAnswered = true;
            clearInterval(gameTimer);

            const q = gameCurrentQuestions[gameCurrentIndex];
            const buttons = gameChoicesEl.querySelectorAll(".game-choice-btn");

            buttons.forEach((btn, idx) => {
                btn.disabled = true;
                if (idx === q.correctIndex) {
                    btn.classList.add("correct");
                }
                if (idx === selectedIndex && idx !== q.correctIndex) {
                    btn.classList.add("incorrect");
                }
            });

            gameFeedbackBox.style.display = "block";

            if (selectedIndex === q.correctIndex) {
                gameScore += 10;
                gameScoreEl.textContent = gameScore;
                gameFeedbackBriefEl.textContent = "✅ ตอบถูก เก่งมาก!";
            } else {
                gameFeedbackBriefEl.textContent = "❌ ยังไม่ใช่คำตอบที่ดีที่สุด ลองดูคำอธิบายด้านล่างนะ";
            }
            gameFeedbackExplainEl.textContent = q.explanation;
        }

        function gameHandleTimeout() {
            const q = gameCurrentQuestions[gameCurrentIndex];
            const buttons = gameChoicesEl.querySelectorAll(".game-choice-btn");

            buttons.forEach((btn, idx) => {
                btn.disabled = true;
                if (idx === q.correctIndex) {
                    btn.classList.add("correct");
                }
            });

            gameFeedbackBox.style.display = "block";
            gameFeedbackBriefEl.textContent = "⏱️ หมดเวลาแล้ว!";
            gameFeedbackExplainEl.textContent = q.explanation;
        }

        function gameEnd() {
            gameQuestionCard.style.display = "none";
            gameFeedbackBox.style.display = "none";
            gameResultBox.style.display = "block";

            const totalScore = gameCurrentQuestions.length * 10;
            gameFinalScoreEl.textContent = gameScore;
            gameFinalTotalEl.textContent = totalScore;

            const percent = (gameScore / totalScore) * 100;
            let msg = "";
            if (percent >= 80) {
                msg = "เยี่ยมมาก! คุณเป็น FoodMind Master แล้ว 🎓";
            } else if (percent >= 50) {
                msg = "ดีมาก! เหลืออีกนิดเดียวก็เทพโภชนาการแล้ว 💪";
            } else {
                msg = "ไม่เป็นไรเลย นี่คือจุดเริ่มต้นของการเรียนรู้ ลองเล่นอีกหลาย ๆ รอบนะ 🌱";
            }
            gameResultMessageEl.textContent = msg;
        }

        // next / restart
        gameNextBtn.addEventListener('click', () => {
            gameCurrentIndex++;
            gameShowQuestion();
        });

        gameRestartBtn.addEventListener('click', () => {
            if (!gameCurrentMode) return;
            gameStartMode(gameCurrentMode);
        });

        gameModeButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                const modeKey = btn.dataset.mode;
                gameStartMode(modeKey);
            });
        });
    </script>
</body>
</html>
