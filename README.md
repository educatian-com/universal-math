

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Universal Math — Образовательная платформа</title>
    <style>
        :root {
            --accent: #6c5ce7;
            --accent-light: #a29bfe;
            --bg: #f4f7fa;
            --card-bg: #ffffff;
            --text-main: #2d3436;
            --text-secondary: #636e72;
            --success: #00b894;
            --error: #d63031;
        }

        body {
            font-family: 'Segoe UI', Roboto, -apple-system, sans-serif;
            margin: 0;
            background-color: var(--bg);
            color: var(--text-main);
            line-height: 1.6;
        }

        header {
            background: linear-gradient(135deg, #4834d4 0%, var(--accent) 100%);
            color: white;
            padding: 60px 20px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(72, 52, 212, 0.2);
        }

        header h1 { 
            margin: 0; 
            font-size: 3em; 
            letter-spacing: -1px;
            text-transform: uppercase;
        }
        
        header p { opacity: 0.9; font-size: 1.2em; margin-top: 10px; font-weight: 300; }

        nav {
            background: var(--card-bg);
            padding: 15px 0;
            display: flex;
            justify-content: center;
            gap: 30px;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        nav a {
            text-decoration: none;
            color: var(--text-secondary);
            font-weight: 600;
            transition: 0.3s;
            font-size: 0.95em;
        }

        nav a:hover { color: var(--accent); }

        .container {
            max-width: 1000px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .exercise-container {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            border-top: 6px solid #4834d4;
            text-align: center;
        }

        .exercise-header {
            color: var(--accent);
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.85em;
            font-weight: 700;
            margin-bottom: 10px;
            display: block;
        }

        .question-text {
            font-size: 2em;
            margin: 20px 0;
            font-weight: 700;
            color: #2d3436;
        }

        input[type="number"] {
            width: 120px;
            padding: 15px;
            font-size: 1.5em;
            border: 2px solid #dfe6e9;
            border-radius: 15px;
            text-align: center;
            outline: none;
            transition: 0.3s;
        }

        input[type="number"]:focus {
            border-color: var(--accent);
            box-shadow: 0 0 15px rgba(108, 92, 231, 0.2);
        }

        .controls { margin-top: 30px; }

        .btn {
            background: #4834d4;
            color: white;
            border: none;
            padding: 16px 35px;
            border-radius: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            font-size: 1.1em;
        }

        .btn:hover {
            background: #3c2bb3;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(72, 52, 212, 0.4);
        }

        .btn-next {
            background: var(--text-secondary);
            margin-top: 15px;
            display: none;
        }

        #result-message {
            margin-top: 25px;
            font-weight: 600;
            font-size: 1.2em;
        }

        .is-correct { color: var(--success); }
        .is-wrong { color: var(--error); }

        footer {
            text-align: center;
            padding: 60px;
            color: #b2bec3;
            border-top: 1px solid #eee;
            margin-top: 50px;
        }
    </style>
</head>
<body>

<header>
    <h1>Universal Math</h1>
    <p>Ваше универсальное пространство для изучения математики</p>
</header>

<nav>
    <a href="#">Теория</a>
    <a href="#">Формулы</a>
    <a href="#">Калькуляторы</a>
    <a href="#">Практика</a>
</nav>

<div class="container">
    <div class="exercise-container">
        <span class="exercise-header">Раздел: Практика / Арифметика</span>
        <h2>Проверьте свои силы</h2>
        <p style="color: var(--text-secondary);">Решите пример ниже, чтобы потренироваться:</p>
        
        <div class="question-text" id="quest">6 × 7 = ?</div>
        
        <input type="number" id="ans" placeholder="?">
        
        <div class="controls">
            <button class="btn" onclick="check()">Проверить ответ</button>
            <br>
            <button class="btn btn-next" id="next" onclick="newQuest()">Следующий пример</button>
        </div>

        <div id="result-message"></div>
    </div>
</div>

<footer>
    <p>&copy; 2026 Universal Math. Все права защищены.</p>
</footer>

<script>
    let rightAns = 42;

    function newQuest() {
        const n1 = Math.floor(Math.random() * 10) + 3;
        const n2 = Math.floor(Math.random() * 10) + 3;
        rightAns = n1 * n2;
        
        document.getElementById('quest').innerText = `${n1} × ${n2} = ?`;
        document.getElementById('ans').value = '';
        document.getElementById('result-message').innerText = '';
        document.getElementById('next').style.display = 'none';
    }

    function check() {
        const userAns = document.getElementById('ans').value;
        const msg = document.getElementById('result-message');
        
        if (userAns == rightAns) {
            msg.innerText = "✅ Верно! Отличная работа.";
            msg.className = "is-correct";
            document.getElementById('next').style.display = 'inline-block';
        } else {
            msg.innerText = "❌ Ошибка в расчетах. Попробуйте еще раз!";
            msg.className = "is-wrong";
        }
    }
</script>

</body>
</html>

