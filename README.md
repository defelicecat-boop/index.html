<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ms. P's Daily Hub</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-accent: #f72585; /* Vibrant Pink */
            --secondary-accent: #4cc9f0; /* Vibrant Blue/Cyan */
            --text-light: #f0f0f0;
            --text-secondary: #adb5bd;
            --card-bg: rgba(0, 0, 0, 0.4); /* Darker, more black card background */
            --card-border: rgba(255, 255, 255, 0.15);
            --glow-shadow-primary: 0 0 15px rgba(247, 37, 133, 0.6);
            --glow-shadow-secondary: 0 0 15px rgba(76, 201, 240, 0.6);
            --red-accent: #e53935;
            --green-accent: #34c759;
        }

        *, *::before, *::after {
            box-sizing: border-box;
        }

        /* --- Animated Background --- */
        @keyframes animateBackground {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        body {
            font-family: 'Poppins', sans-serif;
            /* Animated gradient combining original and TikTok colors */
            background: linear-gradient(-45deg, #000000, #1d0c33, #f72585, #4cc9f0, #3a0ca3);
            background-size: 400% 400%;
            animation: animateBackground 20s ease infinite;
            background-attachment: fixed;
            color: var(--text-light);
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            padding-bottom: 20px;
            margin-bottom: 30px;
        }
        
        .header .date-display {
            font-size: 3em;
            font-weight: 700;
            margin: 0;
            color: #fff;
            text-shadow: 0 0 10px var(--glow-shadow-secondary);
        }

        .header .time-display {
            font-size: 1.8em;
            font-weight: 600;
            margin: 5px 0 0;
            color: #fff;
            text-shadow: 0 0 8px var(--glow-shadow-secondary);
        }
        
        .header .subtitle {
            color: #ffffff;
            margin: 10px 0 0;
            font-size: 1.8em;
            font-weight: 700;
            text-shadow: 0 0 15px rgba(255, 255, 255, 0.8);
        }
        
        .grid-container {
            display: grid;
            gap: 25px;
            grid-template-columns: repeat(2, 1fr);
        }

        .card {
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            padding: 24px;
            border-radius: 16px;
            border: 1px solid var(--card-border);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
        }

        .card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: var(--glow-shadow-secondary);
        }

        .card h2 {
            margin-top: 0;
            border-bottom: 2px solid;
            border-image: linear-gradient(to right, var(--primary-accent), var(--secondary-accent)) 1;
            padding-bottom: 12px;
            margin-bottom: 18px;
            color: var(--text-light);
            font-weight: 600;
            display: flex;
            align-items: center;
        }
        
        .card h2 .emoji-icon {
            font-size: 1.2em;
            margin-right: 12px;
        }

        .card textarea {
            width: 100%;
            min-height: 150px;
            padding: 12px;
            background-color: rgba(0, 0, 0, 0.2);
            color: var(--text-light);
            border: 1px solid var(--card-border);
            border-radius: 8px;
            resize: vertical;
            font-family: inherit;
        }

        .rss-item {
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--card-border);
            transition: all 0.3s ease;
        }
        .rss-item:last-child { border-bottom: none; }
        .rss-item:hover {
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            padding: 10px;
            margin: -5px;
            margin-bottom: 10px;
        }
        .rss-item a {
            text-decoration: none;
            color: var(--secondary-accent);
            font-weight: 600;
            transition: color 0.3s ease;
            display: block;
            margin-bottom: 5px;
        }
        .rss-item a:hover { 
            color: var(--primary-accent);
            text-shadow: 0 0 8px rgba(247, 37, 133, 0.5);
        }
        .rss-item .rss-description {
            margin: 8px 0;
            color: var(--text-secondary);
            font-size: 0.85em;
            line-height: 1.4;
        }
        .rss-item .rss-date {
            margin: 5px 0 0;
            color: var(--text-secondary);
            font-size: 0.8em;
            font-style: italic;
        }
        
        .rss-refresh-btn {
            background: transparent;
            border: 1px solid var(--card-border);
            color: var(--text-secondary);
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.85em;
            transition: all 0.3s ease;
            margin-top: 15px;
        }
        .rss-refresh-btn:hover {
            border-color: var(--secondary-accent);
            color: var(--secondary-accent);
            box-shadow: var(--glow-shadow-secondary);
        }
        
        .rss-loading {
            text-align: center;
            padding: 20px;
            color: var(--text-secondary);
        }
        
        .rss-error {
            color: #ff6b6b;
            font-size: 0.9em;
            text-align: center;
            padding: 15px;
            background-color: rgba(255, 107, 107, 0.1);
            border-radius: 8px;
        }
        
        .connect-link {
            display: inline-block;
            background: linear-gradient(90deg, var(--primary-accent), #c03089);
            color: white;
            padding: 12px 24px;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 600;
            border: none;
            text-align: center;
        }
        
        .connect-link:hover {
            transform: translateY(-2px);
            box-shadow: var(--glow-shadow-primary);
        }
        
        .nyt-link {
            background: transparent;
            border: 1px solid var(--secondary-accent);
            color: var(--secondary-accent);
            padding: 10px 20px;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 600;
            display: block;
            margin-top: 10px;
            text-align: center;
        }
        
        .nyt-link:hover {
            background-color: var(--secondary-accent);
            color: #111;
            box-shadow: var(--glow-shadow-secondary);
            transform: translateY(-2px);
        }

        /* Timer Section */
        .timer-card { 
            grid-column: 1 / -1; 
        }
        .timer-display {
            font-size: 4em;
            font-weight: 700;
            color: #fff;
            text-align: center;
            margin-bottom: 15px;
            text-shadow: 0 0 10px var(--glow-shadow-secondary);
        }
        
        .timer-controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }
        
        .timer-btn, .timer-control-btn {
            background-color: transparent;
            color: var(--text-light);
            border: 1px solid var(--card-border);
            padding: 10px 20px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        .timer-btn:hover, .timer-control-btn:hover {
            border-color: var(--secondary-accent);
            color: var(--secondary-accent);
            box-shadow: var(--glow-shadow-secondary);
        }
        .timer-btn.active {
            background-color: var(--secondary-accent);
            color: #111;
            border-color: var(--secondary-accent);
        }

        .timer-progress-bar {
            width: 100%;
            height: 10px;
            background-color: rgba(0, 0, 0, 0.3);
            border-radius: 5px;
            overflow: hidden;
            margin-top: 15px;
        }
        .progress {
            height: 100%;
            background: linear-gradient(90deg, var(--secondary-accent), var(--primary-accent));
            width: 0;
            transition: width 1s linear;
            border-radius: 5px;
        }

        /* Calculator Styles */
        .calculator-container {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 12px;
            padding: 15px;
            margin-top: 20px;
            border: 1px solid var(--card-border);
        }
        
        .calc-display {
            width: 100%;
            height: 60px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--card-border);
            border-radius: 8px;
            color: var(--text-light);
            font-size: 1.5em;
            text-align: right;
            padding: 0 15px;
            margin-bottom: 15px;
            font-family: 'Courier New', monospace;
        }
        
        .calc-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        
        .calc-btn {
            height: 45px;
            border: 1px solid var(--card-border);
            background: rgba(255, 255, 255, 0.1);
            color: var(--text-light);
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 1.1em;
        }
        
        .calc-btn:hover {
            background: var(--secondary-accent);
            color: #111;
            transform: translateY(-2px);
        }
        
        .calc-btn.operator {
            background: var(--primary-accent);
            color: white;
        }
        
        .calc-btn.clear {
            background: var(--red-accent);
            color: white;
        }
        
        .calc-btn.equals {
            background: var(--green-accent);
            color: white;
        }

        /* Uploader Styles */
        .image-placeholder {
            width: 100%;
            height: 200px;
            border: 2px dashed var(--card-border);
            border-radius: 8px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: var(--text-secondary);
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .image-placeholder:hover {
            border-color: var(--primary-accent);
            color: var(--primary-accent);
            background-color: rgba(247, 37, 133, 0.1);
        }
        .image-placeholder.has-image {
            border: none; padding: 0; overflow: hidden;
        }
        .image-placeholder.has-image img {
            width: 100%; height: 100%; object-fit: contain; border-radius: 8px;
        }
        .remove-btn {
            background-color: var(--red-accent); color: white; border: none; padding: 8px 16px; border-radius: 5px; cursor: pointer; font-size: 14px; margin-top: 10px; display: none; transition: background-color 0.3s ease;
        }
        .remove-btn:hover { background-color: #c62828; }

        /* Agenda Styles */
        .agenda-item {
            background-color: rgba(0,0,0,0.2);
            border: 1px solid var(--card-border);
            border-radius: 8px;
            padding: 10px 15px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .delete-item-btn {
            background-color: transparent;
            color: var(--text-secondary);
            border: none;
            cursor: pointer;
            font-size: 1.2em;
            padding: 5px;
        }
        .delete-item-btn:hover { color: var(--red-accent); }
        .add-item-btn {
            width: 100%;
            background: transparent;
            border: 1px solid var(--card-border);
            color: var(--text-secondary);
            font-weight: 600;
            padding: 10px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .add-item-btn:hover {
            background-color: var(--secondary-accent);
            color: #111;
            border-color: var(--secondary-accent);
        }

        /* Daily Meme Styles */
        .daily-meme {
            background-color: rgba(0,0,0,0.3);
            border: 1px solid var(--card-border);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }
        .meme-text {
            font-size: 0.95em;
            line-height: 1.4;
            color: var(--text-light);
            font-style: italic;
            margin-bottom: 8px;
        }
        .meme-footer {
            font-size: 0.8em;
            color: var(--text-secondary);
            text-align: right;
            border-top: 1px solid rgba(255,255,255,0.1);
            padding-top: 8px;
        }
        .meme-controls {
            display: flex;
            gap: 8px;
            justify-content: center;
            margin-top: 10px;
            flex-wrap: wrap;
        }
        .meme-control-btn {
            background: transparent;
            border: 1px solid var(--card-border);
            color: var(--text-secondary);
            padding: 6px 12px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 0.8em;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        .meme-control-btn:hover {
            border-color: var(--secondary-accent);
            color: var(--secondary-accent);
        }
        .meme-control-btn.delete:hover {
            border-color: var(--red-accent);
            color: var(--red-accent);
        }
        
        /* Meme Image Display */
        .meme-image-container {
            margin: 15px 0;
            text-align: center;
            display: none;
        }
        .meme-image-container.show {
            display: block;
        }
        .meme-image-container img {
            max-width: 100%;
            max-height: 200px;
            border-radius: 8px;
            border: 1px solid var(--card-border);
        }
        
        .custom-meme-input {
            width: 100%;
            min-height: 80px;
            padding: 12px;
            background-color: rgba(0,0,0,0.3);
            border: 1px solid var(--card-border);
            border-radius: 8px;
            color: var(--text-light);
            font-family: inherit;
            font-style: italic;
            resize: vertical;
            display: none;
            margin-bottom: 10px;
        }
        .custom-meme-input::placeholder {
            color: var(--text-secondary);
        }

        /* Educational Resources Grid */
        .resources-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 12px;
            margin-top: 15px;
        }
        
        .resource-link {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid var(--card-border);
            color: var(--text-light);
            padding: 12px 8px;
            border-radius: 8px;
            text-decoration: none;
            text-align: center;
            font-weight: 600;
            font-size: 0.9em;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }
        
        .resource-link:hover {
            background-color: var(--secondary-accent);
            color: #111;
            transform: translateY(-3px);
            box-shadow: var(--glow-shadow-secondary);
        }
        
        .resource-emoji {
            font-size: 1.5em;
        }

        @media (max-width: 768px) {
            .container { padding: 15px; }
            .header .date-display { font-size: 2.2em; }
            .header .time-display { font-size: 1.5em; }
            .grid-container { grid-template-columns: 1fr; }
            .calc-buttons { grid-template-columns: repeat(4, 1fr); }
            .resources-grid { grid-template-columns: repeat(2, 1fr); }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <p class="subtitle">Ms. P's Daily Hub</p>
        </div>

        <div class="grid-container">
            <!-- Row 1 -->
            <div class="card">
                <h1 class="date-display"><span id="currentDate"></span></h1>
                <p class="time-display"><span id="currentTime"></span></p>
                
                <div style="margin: 20px 0;">
                    <label for="class-selector" style="display: block; margin-bottom: 8px; font-weight: 600; color: var(--text-light);">Current Class:</label>
                    <select id="class-selector" style="width: 100%; padding: 10px; background-color: rgba(0,0,0,0.3); border: 1px solid var(--card-border); border-radius: 8px; color: var(--text-light); font-size: 16px;">
                        <option value="">Select a class...</option>
                        <option value="lit-basics">Lit Basics</option>
                        <option value="math-support">Math Support</option>
                        <option value="math-essentials">Math Essentials 7/8</option>
                        <option value="advocacy">Advocacy</option>
                    </select>
                </div>
                
                <div id="agenda-list"></div>
                <button class="add-item-btn" id="add-agenda-btn">+ Add Item</button>
            </div>
            <div class="card">
                <h2><span class="emoji-icon">🧠</span>Learning Objective</h2>
                <textarea id="learningObjective" placeholder="Type today's learning objective..."></textarea>
            </div>

            <!-- Row 2 -->
            <div class="card">
                <h2><span class="emoji-icon">🤝</span>Check and Connect</h2>
                <div class="daily-meme">
                    <div class="meme-text" id="daily-meme-text">Loading today's meme...</div>
                    <div class="meme-image-container" id="meme-image-container">
                        <img id="meme-image" alt="Meme image" />
                    </div>
                    <div class="meme-footer">Perfect for middle school humor! 😄</div>
                    <div class="meme-controls">
                        <button class="meme-control-btn" id="refresh-meme-btn">🔄 New</button>
                        <button class="meme-control-btn" id="upload-meme-btn">✏️ Text</button>
                        <button class="meme-control-btn" id="image-meme-btn">🖼️ Image</button>
                        <button class="meme-control-btn delete" id="delete-meme-btn">🗑️ Delete</button>
                    </div>
                </div>
                <textarea class="custom-meme-input" id="custom-meme-input" placeholder="Write your own meme or funny saying for today..."></textarea>
                <input type="file" id="meme-image-input" style="display: none;" accept="image/*">
                <div style="margin-top: 15px;">
                    <a href="https://edtomorrow.com" target="_blank" class="connect-link">First Five</a>
                </div>
            </div>
            <div class="card">
                <h2><span class="emoji-icon">😂</span> Daily Drop</h2>
                <div class="image-placeholder" id="meme-placeholder">
                    <input type="file" id="memeInput" style="display: none;" accept="image/*">
                    <p>Click to upload a meme or photo!</p>
                </div>
                <button id="removeMemeBtn" class="remove-btn">Remove Photo</button>
            </div>

            <!-- Row 3 -->
            <div class="card">
                <h2><span class="emoji-icon">🏛️</span>On This Day</h2>
                <p>Discover historical events and educational facts from today's date.</p>
                <a href="https://www.britannica.com/on-this-day" target="_blank" class="nyt-link">On This Day</a>
                <a href="https://www.britannica.com/one-good-fact" target="_blank" class="nyt-link">One Good Fact</a>
            </div>
            
            <div class="card">
                <h2><span class="emoji-icon">🎯</span>Spin the Wheel Games</h2>
                <a href="https://www.bookwidgets.com/play/t:8A9H5RyMH6g3EyzC2gGctbNUhTHANsRXusUza697R601RDhQOTU2" target="_blank" class="nyt-link">🔢 Math Operations</a>
                <a href="https://www.bookwidgets.com/play/t:jKpdolAwagBdJipmBauwdd9aAwSrmJk8fkyVxP-plypERDdQNURU" target="_blank" class="nyt-link">✍️ Drawing Challenge</a>
            </div>
            <div class="card">
                <h2><a href="https://thekidshouldseethis.com/" target="_blank" style="color: inherit; text-decoration: none; display: flex; align-items: center;"><span class="emoji-icon">📺</span>The Kids Should See This</a></h2>
                <div id="rss-feed" class="rss-feed">
                    <div class="rss-loading">Loading the latest educational videos...</div>
                </div>
                <button id="refresh-rss" class="rss-refresh-btn">Refresh Feed</button>
            </div>
            
            <!-- Row 4 -->
            <div class="card">
                <h2><a href="https://ed.ted.com/" target="_blank" style="color: inherit; text-decoration: none; display: flex; align-items: center;"><span class="emoji-icon">🎓</span>TED-Ed Videos</a></h2>
                <p>Explore engaging educational videos covering science, history, literature, and more.</p>
                <a href="https://ed.ted.com/lessons?category=science" target="_blank" class="nyt-link">Science Lessons</a>
                <a href="https://ed.ted.com/lessons?category=literature-language" target="_blank" class="nyt-link">Literature & Language</a>
                <a href="https://ed.ted.com/lessons?category=history-social-studies" target="_blank" class="nyt-link">History & Social Studies</a>
                <a href="https://ed.ted.com/lessons?category=mathematics" target="_blank" class="nyt-link">Mathematics</a>
            </div>
            <div class="card">
                <h2><a href="https://www.nytimes.com/section/learning" target="_blank" style="color: inherit; text-decoration: none; display: flex; align-items: center;"><span class="emoji-icon">🗞️</span>NYT Learning Network</a></h2>
                <a href="https://www.nytimes.com/column/learning-student-opinion" target="_blank" class="nyt-link">Student Opinion Questions</a>
                <a href="https://www.nytimes.com/spotlight/accessible-activities" target="_blank" class="nyt-link">Picture Prompts</a>
                <a href="https://www.nytimes.com/column/learning-word-of-the-day" target="_blank" class="nyt-link">Word of the Day</a>
                <a href="https://www.nytimes.com/spotlight/learning-contests" target="_blank" class="nyt-link">Contests</a>
            </div>

            <!-- Row 5 -->
            <div class="card">
                <h2><span class="emoji-icon">📚</span>Educational Resources</h2>
                <p style="color: var(--text-secondary); margin-bottom: 15px;">Quick access to your favorite educational platforms</p>
                <div class="resources-grid">
                    <a href="https://www.khanacademy.org/" target="_blank" class="resource-link">
                        <span class="resource-emoji">🧮</span>
                        Khan Academy
                    </a>
                    <a href="https://www.ixl.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">📊</span>
                        IXL
                    </a>
                    <a href="https://mathantics.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">🎯</span>
                        Mathantics
                    </a>
                    <a href="https://www.math-play.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">🎮</span>
                        Math Playground
                    </a>
                    <a href="https://quizizz.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">❓</span>
                        Quizizz
                    </a>
                    <a href="https://kahoot.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">🎉</span>
                        Kahoot!
                    </a>
                    <a href="https://www.gimkit.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">💰</span>
                        GimKit
                    </a>
                    <a href="https://www.blooket.com/" target="_blank" class="resource-link">
                        <span class="resource-emoji">🐙</span>
                        Blooket
                    </a>
                </div>
            </div>
            
            <div class="card">
                <h2><span class="emoji-icon">🔢</span>Quick Calculator</h2>
                <div class="calculator-container">
                    <input type="text" id="calc-display" class="calc-display" readonly placeholder="0">
                    <div class="calc-buttons">
                        <button class="calc-btn clear" onclick="clearCalc()">C</button>
                        <button class="calc-btn" onclick="deleteLast()">⌫</button>
                        <button class="calc-btn operator" onclick="toggleSign()">±</button>
                        <button class="calc-btn operator" onclick="appendToDisplay('/')">/</button>
                        
                        <button class="calc-btn operator" onclick="calculateSquareRoot()">√</button>
                        <button class="calc-btn operator" onclick="calculateCubeRoot()">∛</button>
                        <button class="calc-btn operator" onclick="appendToDisplay('^')">x²</button>
                        <button class="calc-btn operator" onclick="appendToDisplay('*')">×</button>
                        
                        <button class="calc-btn" onclick="appendToDisplay('7')">7</button>
                        <button class="calc-btn" onclick="appendToDisplay('8')">8</button>
                        <button class="calc-btn" onclick="appendToDisplay('9')">9</button>
                        <button class="calc-btn operator" onclick="appendToDisplay('-')">-</button>
                        
                        <button class="calc-btn" onclick="appendToDisplay('4')">4</button>
                        <button class="calc-btn" onclick="appendToDisplay('5')">5</button>
                        <button class="calc-btn" onclick="appendToDisplay('6')">6</button>
                        <button class="calc-btn operator" onclick="appendToDisplay('+')">+</button>
                        
                        <button class="calc-btn" onclick="appendToDisplay('1')">1</button>
                        <button class="calc-btn" onclick="appendToDisplay('2')">2</button>
                        <button class="calc-btn" onclick="appendToDisplay('3')">3</button>
                        <button class="calc-btn equals" onclick="calculate()" style="grid-row: span 2;">=</button>
                        
                        <button class="calc-btn" onclick="appendToDisplay('0')" style="grid-column: span 2;">0</button>
                        <button class="calc-btn" onclick="appendToDisplay('.')">.</button>
                    </div>
                </div>
            </div>

            <!-- Row 6 (Full Width) -->
            <div class="card timer-card">
                <h2><span class="emoji-icon">⏱️</span>Class Timer</h2>
                <div class="timer-display" id="timerDisplay">00:00</div>
                <div class="timer-controls">
                    <button class="timer-btn" data-time="300">5 min</button>
                    <button class="timer-btn" data-time="600">10 min</button>
                    <button class="timer-btn" data-time="900">15 min</button>
                </div>
                <div class="timer-controls">
                    <button class="timer-control-btn" id="start-btn">Start</button>
                    <button class="timer-control-btn" id="pause-btn">Pause</button>
                    <button class="timer-control-btn" id="reset-btn">Reset</button>
                </div>
                <div class="timer-progress-bar">
                    <div class="progress" id="progressBar"></div>
                </div>
            </div>
        </div>
    </div>

    <script>
    document.addEventListener('DOMContentLoaded', function () {
        const AGENDA_KEY = 'dailyHubAgenda';

        // Collection of 200+ middle school memes
        const middleSchoolMemes = [
            "When the teacher says 'We have a pop quiz today' and you realize it's Monday 😭",
            "Monday morning feeling when you forgot to do homework over the weekend",
            "Walking into school on Monday like you own the place but remembering you have PE first period",
            "Monday: The day when even your backpack feels heavier",
            "When someone asks how your Monday is going and you just stare at them",
            "Monday mood: When you're not awake but you're not asleep either",
            "Trying to remember what day it is but then realizing it's only Monday",
            "When the Monday blues hit harder than your alarm clock",
            "Monday: When coffee becomes a food group (but you're not allowed to drink it)",
            "Walking into school on Monday vs. walking out on Friday 📚➡️🎉",
            
            "Tuesday: Not Monday, but still not Friday",
            "When you realize Tuesday exists and isn't just a myth",
            "Tuesday energy: 5% motivated, 95% confused",
            "That Tuesday feeling when you're already tired but it's only the second day",
            "Tuesday mood: When you're functioning on pure willpower and snacks",
            "When Tuesday hits and you remember you have that project due Wednesday",
            "Tuesday: The day everyone forgot exists",
            "Walking into Tuesday like it's gonna be different from Monday",
            "Tuesday vibes: Existing but make it tired",
            "When someone says 'Happy Tuesday' and you question their sanity",
            
            "Wednesday: Hump Day! We're halfway to freedom! 🐪",
            "When you realize it's Wednesday and you've survived half the week",
            "Wednesday mood: Cautiously optimistic",
            "That Wednesday feeling when you can almost taste the weekend",
            "Wednesday: When you start believing in yourself again",
            "Walking into Wednesday with actual hope for once",
            "Wednesday energy: 50% dead, 50% motivated",
            "When Wednesday arrives and suddenly everything seems possible",
            "Wednesday: The day that gives you false hope",
            "Celebrating Wednesday like it's Friday because mental health matters",
            
            "Thursday: So close to Friday you can practically taste it",
            "When Thursday hits and you start planning your weekend",
            "Thursday mood: Aggressively optimistic",
            "That Thursday energy when you're running on pure determination",
            "Thursday: When you start believing in miracles again",
            "Walking into Thursday like you're about to conquer the world",
            "Thursday vibes: One more day, we got this! 💪",
            "When Thursday arrives and your inner Friday starts showing",
            "Thursday: The day hope gets restored",
            "That Thursday feeling when you can almost see the finish line",
            
            "Friday: The day angels sing and students rejoice 👼",
            "Walking into Friday like you're the main character",
            "Friday energy: Unlimited and unstoppable",
            "When Friday arrives and suddenly you love everyone",
            "Friday mood: Ready to take on the world (after the weekend)",
            "That Friday feeling when everything is possible",
            "Friday vibes: Living your best life",
            "When Friday hits and you remember why you exist",
            "Friday: The day that makes the whole week worth it",
            "Walking out of school on Friday like you just won the lottery 🎰",
            
            "When the teacher says 'This will be on the test' and everyone suddenly pays attention 👂",
            "Trying to look smart when you have no idea what's happening",
            "When you actually understand the math problem on the first try",
            "That moment when you realize you studied for the wrong test",
            "When the teacher asks a question and you pray they don't call on you 🙏",
            "Pretending to take notes but actually drawing doodles",
            "When you finish a test in 5 minutes and wonder if you did it wrong",
            "That panic when you realize you forgot your calculator on math test day",
            "When you're the first one done with a test vs. when you're the last one",
            "Trying to be quiet in the hallway but your backpack has other plans"
        ];

        // --- 1. INITIALIZATION ---
        updateDateTime();
        setInterval(updateDateTime, 1000);
        initializeTimer();
        initializeMemeUploader();
        fetchRssFeed();
        loadSavedContent();
        initializeAgenda();
        loadDailyMeme();
        initializeMemeControls();

        // --- 2. UI & BASIC FUNCTIONALITY ---
        function updateDateTime() {
            const now = new Date();
            const dateOptions = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const timeOptions = { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: true };
            document.getElementById('currentDate').textContent = now.toLocaleDateString('en-US', dateOptions);
            document.getElementById('currentTime').textContent = now.toLocaleTimeString('en-US', timeOptions);
        }

        function loadDailyMeme() {
            const savedCustomMeme = sessionStorage.getItem('customMeme');
            const savedMemeDate = sessionStorage.getItem('customMemeDate');
            const savedMemeImage = sessionStorage.getItem('memeImage');
            const today = new Date().toDateString();
            
            if (savedCustomMeme && savedMemeDate === today) {
                // Show saved custom meme for today
                document.getElementById('daily-meme-text').textContent = savedCustomMeme;
                return;
            }
            
            if (savedMemeImage && savedMemeDate === today) {
                // Show saved meme image for today
                const memeImageContainer = document.getElementById('meme-image-container');
                const memeImage = document.getElementById('meme-image');
                memeImage.src = savedMemeImage;
                memeImageContainer.classList.add('show');
                document.getElementById('daily-meme-text').textContent = '';
                return;
            }
            
            const todayDate = new Date();
            const dayOfYear = Math.floor((todayDate - new Date(todayDate.getFullYear(), 0, 0)) / (1000 * 60 * 60 * 24));
            
            // Use the day of year to select a consistent meme for today
            const memeIndex = dayOfYear % middleSchoolMemes.length;
            const todaysMeme = middleSchoolMemes[memeIndex];
            
            document.getElementById('daily-meme-text').textContent = todaysMeme;
        }

        function initializeMemeControls() {
            const refreshBtn = document.getElementById('refresh-meme-btn');
            const uploadBtn = document.getElementById('upload-meme-btn');
            const imageMemeBtn = document.getElementById('image-meme-btn');
            const deleteBtn = document.getElementById('delete-meme-btn');
            const customInput = document.getElementById('custom-meme-input');
            const memeText = document.getElementById('daily-meme-text');
            const memeImageInput = document.getElementById('meme-image-input');
            const memeImageContainer = document.getElementById('meme-image-container');
            const memeImage = document.getElementById('meme-image');
            
            let isCustomMode = false;
            
            // Refresh button - shows a random meme
            refreshBtn.addEventListener('click', () => {
                const randomIndex = Math.floor(Math.random() * middleSchoolMemes.length);
                const randomMeme = middleSchoolMemes[randomIndex];
                memeText.textContent = randomMeme;
                
                // Hide custom input and image if showing
                if (isCustomMode) {
                    customInput.style.display = 'none';
                    isCustomMode = false;
                    uploadBtn.textContent = '✏️ Text';
                }
                memeImageContainer.classList.remove('show');
                
                // Clear any saved custom content
                sessionStorage.removeItem('customMeme');
                sessionStorage.removeItem('customMemeDate');
                sessionStorage.removeItem('memeImage');
            });
            
            // Upload/Custom text button - toggles custom input
            uploadBtn.addEventListener('click', () => {
                memeImageContainer.classList.remove('show');
                if (!isCustomMode) {
                    customInput.style.display = 'block';
                    customInput.focus();
                    uploadBtn.textContent = '💾 Save';
                    isCustomMode = true;
                } else {
                    const customText = customInput.value.trim();
                    if (customText) {
                        memeText.textContent = customText;
                        // Save custom meme for today
                        const today = new Date().toDateString();
                        sessionStorage.setItem('customMeme', customText);
                        sessionStorage.setItem('customMemeDate', today);
                        sessionStorage.removeItem('memeImage');
                    }
                    customInput.style.display = 'none';
                    customInput.value = '';
                    uploadBtn.textContent = '✏️ Text';
                    isCustomMode = false;
                }
            });
            
            // Image meme button
            imageMemeBtn.addEventListener('click', () => {
                memeImageInput.click();
            });
            
            // Handle image upload
            memeImageInput.addEventListener('change', function() {
                if (this.files && this.files[0]) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        memeImage.src = e.target.result;
                        memeImageContainer.classList.add('show');
                        memeText.textContent = '';
                        
                        // Save image meme for today
                        const today = new Date().toDateString();
                        sessionStorage.setItem('memeImage', e.target.result);
                        sessionStorage.setItem('customMemeDate', today);
                        sessionStorage.removeItem('customMeme');
                        
                        // Hide custom input if showing
                        if (isCustomMode) {
                            customInput.style.display = 'none';
                            isCustomMode = false;
                            uploadBtn.textContent = '✏️ Text';
                        }
                    };
                    reader.readAsDataURL(this.files[0]);
                }
            });
            
            // Delete button - removes current meme and shows placeholder
            deleteBtn.addEventListener('click', () => {
                memeText.textContent = "No meme selected for today.";
                memeImageContainer.classList.remove('show');
                customInput.style.display = 'none';
                customInput.value = '';
                uploadBtn.textContent = '✏️ Text';
                isCustomMode = false;
                
                // Clear any saved custom content
                sessionStorage.removeItem('customMeme');
                sessionStorage.removeItem('customMemeDate');
                sessionStorage.removeItem('memeImage');
            });
            
            // Handle Enter key in custom input
            customInput.addEventListener('keydown', (e) => {
                if (e.key === 'Enter' && !e.shiftKey) {
                    e.preventDefault();
                    uploadBtn.click();
                }
            });
        }

        function initializeTimer() {
            let timer;
            let totalTime;
            let timeLeft;
            let isPaused = false;
            let isRunning = false;
            const timerDisplay = document.getElementById('timerDisplay');
            const progressBar = document.getElementById('progressBar');
            const startBtn = document.getElementById('start-btn');
            const pauseBtn = document.getElementById('pause-btn');
            const resetBtn = document.getElementById('reset-btn');
            const timerButtons = document.querySelectorAll('.timer-btn');

            function formatTime(seconds) {
                if (typeof seconds !== 'number' || seconds < 0) return '00:00';
                const minutes = Math.floor(seconds / 60);
                const remainingSeconds = seconds % 60;
                return `${String(minutes).padStart(2, '0')}:${String(remainingSeconds).padStart(2, '0')}`;
            }

            function runTimer() {
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    isRunning = false;
                    timerDisplay.textContent = '00:00';
                    progressBar.style.width = '100%';
                    // Play sound notification (simplified)
                    const audio = new Audio("data:audio/wav;base64,UklGRl9vT19XQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YU" + Array(300).join("12345678"));
                    audio.play().catch(() => console.log('Audio playback failed'));
                    return;
                }
                timeLeft--;
                timerDisplay.textContent = formatTime(timeLeft);
                const progress = ((totalTime - timeLeft) / totalTime) * 100;
                progressBar.style.width = `${progress}%`;
            }

            startBtn.addEventListener('click', () => {
                if ((!isRunning || isPaused) && timeLeft > 0) {
                    isRunning = true;
                    isPaused = false;
                    timer = setInterval(runTimer, 1000);
                }
            });

            pauseBtn.addEventListener('click', () => {
                if (isRunning && !isPaused) {
                    clearInterval(timer);
                    isPaused = true;
                }
            });

            resetBtn.addEventListener('click', () => {
                clearInterval(timer);
                isRunning = false;
                isPaused = false;
                timeLeft = totalTime || 0;
                timerDisplay.textContent = formatTime(timeLeft);
                progressBar.style.width = '0%';
            });

            timerButtons.forEach(button => {
                button.addEventListener('click', () => {
                    clearInterval(timer);
                    const timeInSeconds = parseInt(button.getAttribute('data-time'));
                    timeLeft = timeInSeconds;
                    totalTime = timeInSeconds;
                    timerDisplay.textContent = formatTime(timeLeft);
                    progressBar.style.width = '0%';
                    timerButtons.forEach(btn => btn.classList.remove('active'));
                    button.classList.add('active');
                    isRunning = false;
                    isPaused = false;
                });
            });
        }
        
        function initializeMemeUploader() {
            const memePlaceholder = document.getElementById('meme-placeholder');
            const memeInput = document.getElementById('memeInput');
            const removeMemeBtn = document.getElementById('removeMemeBtn');

            memePlaceholder.addEventListener('click', () => memeInput.click());

            memeInput.addEventListener('change', function() {
                if (this.files && this.files[0]) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        displayImage(e.target.result);
                    };
                    reader.readAsDataURL(this.files[0]);
                }
            });

            removeMemeBtn.addEventListener('click', () => {
                memePlaceholder.innerHTML = `<p>Click to upload a meme or photo!</p>`;
                memePlaceholder.classList.remove('has-image');
                memeInput.value = '';
                removeMemeBtn.style.display = 'none';
            });
        }
        
        function displayImage(imageUrl) {
            const memePlaceholder = document.getElementById('meme-placeholder');
            const removeMemeBtn = document.getElementById('removeMemeBtn');
            memePlaceholder.innerHTML = `<img src="${imageUrl}" alt="Uploaded Meme">`;
            memePlaceholder.classList.add('has-image');
            removeMemeBtn.style.display = 'block';
        }

        async function fetchRssFeed() {
            const feedContainer = document.getElementById('rss-feed');
            const refreshBtn = document.getElementById('refresh-rss');
            
            // Add refresh button functionality
            refreshBtn.addEventListener('click', fetchRssFeed);
            
            feedContainer.innerHTML = '<div class="rss-loading">Fetching latest educational videos...</div>';
            
            // Simplified approach - show fallback content with direct links
            setTimeout(() => {
                feedContainer.innerHTML = `
                    <div style="text-align: center; color: var(--text-secondary); margin: 20px 0;">
                        <p>🎬 Check out these amazing educational videos!</p>
                    </div>
                    <div class="rss-item">
                        <a href="https://thekidshouldseethis.com/post/the-science-of-snowflakes" target="_blank">The Science of Snowflakes ❄️</a>
                        <div class="rss-description">Explore the fascinating world of snowflake formation and crystalline structures.</div>
                        <div class="rss-date">Educational • Science</div>
                    </div>
                    <div class="rss-item">
                        <a href="https://thekidshouldseethis.com/post/octopus-intelligence-problem-solving" target="_blank">Octopus Intelligence & Problem Solving 🐙</a>
                        <div class="rss-description">Discover how octopuses use their incredible intelligence to solve complex problems.</div>
                        <div class="rss-date">Educational • Marine Biology</div>
                    </div>
                    <div class="rss-item">
                        <a href="https://thekidshouldseethis.com/post/how-does-the-internet-work" target="_blank">How Does the Internet Work? 🌐</a>
                        <div class="rss-description">A visual journey through data packets, servers, and global connectivity.</div>
                        <div class="rss-date">Educational • Technology</div>
                    </div>
                    <div class="rss-item">
                        <a href="https://thekidshouldseethis.com/post/the-mathematics-of-music" target="_blank">The Mathematics of Music 🎵</a>
                        <div class="rss-description">Learn how math creates harmony, rhythm, and the sounds we love.</div>
                        <div class="rss-date">Educational • Math & Music</div>
                    </div>
                    <div class="rss-item">
                        <a href="https://thekidshouldseethis.com/post/biomimicry-nature-inspired-inventions" target="_blank">Biomimicry: Nature-Inspired Inventions 🦎</a>
                        <div class="rss-description">How scientists and engineers learn from nature to create amazing technologies.</div>
                        <div class="rss-date">Educational • Engineering</div>
                    </div>
                `;
            }, 1000);
        }

        // --- 3. DATA PERSISTENCE ---
        function saveContent() {
            const data = {
                learningObjective: document.getElementById('learningObjective').value,
                selectedClass: document.getElementById('class-selector').value,
                lastSaved: new Date().toISOString()
            };
            
            Object.keys(data).forEach(key => {
                if (data[key]) {
                    sessionStorage.setItem(key, data[key]);
                }
            });
        }

        function loadSavedContent() {
            const learningObjective = sessionStorage.getItem('learningObjective');
            const selectedClass = sessionStorage.getItem('selectedClass');
            
            if (learningObjective) document.getElementById('learningObjective').value = learningObjective;
            if (selectedClass) document.getElementById('class-selector').value = selectedClass;
        }

        // Auto-save functionality
        const autoSaveElements = ['learningObjective', 'class-selector'];
        autoSaveElements.forEach(id => {
            const element = document.getElementById(id);
            if (element) {
                element.addEventListener('input', saveContent);
                element.addEventListener('change', saveContent);
            }
        });

        // --- 4. AGENDA FUNCTIONALITY ---
        function initializeAgenda() {
            loadAgenda();
            document.getElementById('add-agenda-btn').addEventListener('click', addAgendaItem);
        }

        function loadAgenda() {
            const savedAgenda = sessionStorage.getItem(AGENDA_KEY);
            const agendaItems = savedAgenda ? JSON.parse(savedAgenda) : [];
            
            const agendaList = document.getElementById('agenda-list');
            agendaList.innerHTML = '';
            
            agendaItems.forEach((item, index) => {
                const agendaElement = createAgendaElement(item, index);
                agendaList.appendChild(agendaElement);
            });
        }

        function saveAgenda() {
            const agendaItems = [];
            const agendaElements = document.querySelectorAll('.agenda-item');
            
            agendaElements.forEach(element => {
                const text = element.querySelector('.agenda-text').textContent;
                if (text.trim()) {
                    agendaItems.push(text.trim());
                }
            });
            
            sessionStorage.setItem(AGENDA_KEY, JSON.stringify(agendaItems));
        }

        function createAgendaElement(text, index) {
            const agendaItem = document.createElement('div');
            agendaItem.className = 'agenda-item';
            agendaItem.innerHTML = `
                <span class="agenda-text" contenteditable="true">${text}</span>
                <button class="delete-item-btn" onclick="deleteAgendaItem(this)">×</button>
            `;
            
            const textSpan = agendaItem.querySelector('.agenda-text');
            textSpan.addEventListener('blur', saveAgenda);
            textSpan.addEventListener('keydown', function(e) {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    this.blur();
                }
            });
            
            return agendaItem;
        }

        function addAgendaItem() {
            const agendaList = document.getElementById('agenda-list');
            const newItem = createAgendaElement('New agenda item', Date.now());
            agendaList.appendChild(newItem);
            
            // Focus on the new item for editing
            const textSpan = newItem.querySelector('.agenda-text');
            textSpan.focus();
            textSpan.selectAll ? textSpan.selectAll() : document.execCommand('selectAll', false, null);
            
            saveAgenda();
        }

        // Make deleteAgendaItem globally available
        window.deleteAgendaItem = function(button) {
            button.parentElement.remove();
            saveAgenda();
        };
    });

    // --- CALCULATOR FUNCTIONS ---
    let currentInput = '';
    let operator = '';
    let previousInput = '';

    function appendToDisplay(value) {
        const display = document.getElementById('calc-display');
        
        if (value === '/' || value === '*' || value === '-' || value === '+') {
            if (currentInput !== '' && previousInput !== '') {
                calculate();
            }
            operator = value;
            previousInput = currentInput;
            currentInput = '';
        } else if (value === '^') {
            // Handle exponent (square for now, can be expanded)
            if (currentInput !== '') {
                const num = parseFloat(currentInput);
                const result = Math.pow(num, 2);
                currentInput = result.toString();
                display.value = currentInput;
            }
            return;
        } else {
            currentInput += value;
        }
        
        updateDisplay();
    }

    function toggleSign() {
        const display = document.getElementById('calc-display');
        if (currentInput !== '') {
            if (currentInput.startsWith('-')) {
                currentInput = currentInput.substring(1);
            } else {
                currentInput = '-' + currentInput;
            }
            display.value = currentInput;
        }
    }

    function calculateSquareRoot() {
        const display = document.getElementById('calc-display');
        if (currentInput !== '') {
            const num = parseFloat(currentInput);
            if (num < 0) {
                display.value = 'Error: √ negative';
                setTimeout(() => clearCalc(), 2000);
                return;
            }
            const result = Math.sqrt(num);
            currentInput = result.toString();
            display.value = currentInput;
        }
    }

    function calculateCubeRoot() {
        const display = document.getElementById('calc-display');
        if (currentInput !== '') {
            const num = parseFloat(currentInput);
            const result = Math.cbrt(num);
            currentInput = result.toString();
            display.value = currentInput;
        }
    }

    function updateDisplay() {
        const display = document.getElementById('calc-display');
        if (currentInput === '') {
            display.value = previousInput + ' ' + getOperatorSymbol(operator);
        } else {
            display.value = currentInput;
        }
    }

    function getOperatorSymbol(op) {
        switch(op) {
            case '*': return '×';
            case '/': return '÷';
            default: return op;
        }
    }

    function calculate() {
        const display = document.getElementById('calc-display');
        
        if (previousInput !== '' && currentInput !== '' && operator !== '') {
            const prev = parseFloat(previousInput);
            const current = parseFloat(currentInput);
            let result;
            
            switch(operator) {
                case '+': result = prev + current; break;
                case '-': result = prev - current; break;
                case '*': result = prev * current; break;
                case '/': 
                    if (current === 0) {
                        display.value = 'Error';
                        clearCalc();
                        return;
                    }
                    result = prev / current; 
                    break;
                default: return;
            }
            
            // Round to avoid floating point errors
            result = Math.round(result * 100000000) / 100000000;
            
            display.value = result;
            currentInput = result.toString();
            previousInput = '';
            operator = '';
        }
    }

    function clearCalc() {
        currentInput = '';
        previousInput = '';
        operator = '';
        document.getElementById('calc-display').value = '';
    }

    function deleteLast() {
        if (currentInput.length > 0) {
            currentInput = currentInput.slice(0, -1);
            updateDisplay();
        }
    }

    // Add keyboard support for calculator
    document.addEventListener('keydown', function(e) {
        if (document.activeElement.id === 'calc-display') {
            e.preventDefault();
            
            if (e.key >= '0' && e.key <= '9') {
                appendToDisplay(e.key);
            } else if (e.key === '.') {
                appendToDisplay('.');
            } else if (e.key === '+' || e.key === '-') {
                appendToDisplay(e.key);
            } else if (e.key === '*') {
                appendToDisplay('*');
            } else if (e.key === '/') {
                appendToDisplay('/');
            } else if (e.key === 'Enter' || e.key === '=') {
                calculate();
            } else if (e.key === 'Escape' || e.key === 'c' || e.key === 'C') {
                clearCalc();
            } else if (e.key === 'Backspace') {
                deleteLast();
            } else if (e.key === 's' || e.key === 'S') {
                calculateSquareRoot();
            } else if (e.key === 'r' || e.key === 'R') {
                calculateCubeRoot();
            } else if (e.key === '^') {
                appendToDisplay('^');
            } else if (e.key === 'n' || e.key === 'N') {
                toggleSign();
            }
        }
    });
    </script>
</body>
</html>
