<!DOCTYPE html>
<html lang="ms">
<head>
    <meta charset="UTF-8">
    <title>Permainan Pengenalan Microsoft PowerPoint</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #f6d365 0%, #fda085 100%);
            text-align: center;
        }
        .game-container {
            background-color: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            max-width: 500px;
            width: 100%;
        }
        #question {
            font-size: 20px;
            margin-bottom: 20px;
            color: #333;
        }
        .btn {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin: 10px;
            cursor: pointer;
            border-radius: 8px;
            transition: background-color 0.3s ease;
        }
        .btn:hover {
            background-color: #45a049;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <h1>🎮 Kuiz PowerPoint Interaktif</h1>
        <div id="question">Soalan akan dipaparkan di sini</div>
        <div id="choices"></div>
        <div id="result"></div>
    </div>

    <script>
        const questions = [
            {
                question: "Apakah kegunaan utama Microsoft PowerPoint?",
                choices: [
                    "Menulis surat",
                    "Membuat pembentangan slaid",
                    "Mengira nombor",
                    "Melayari internet"
                ],
                correctAnswer: 1
            },
            {
                question: "Ikon apakah yang biasanya digunakan untuk membuka Microsoft PowerPoint?",
                choices: [
                    "🖥️ Komputer",
                    "📊 Graf",
                    "🖼️ Slaid berwarna merah dan putih",
                    "📝 Pen"
                ],
                correctAnswer: 2
            },
            {
                question: "Apakah nama slaid pertama dalam pembentangan PowerPoint?",
                choices: [
                    "Mukasurat Utama",
                    "Slaid Tajuk",
                    "Slaid Pertama",
                    "Halaman Hadapan"
                ],
                correctAnswer: 1
            },
            {
                question: "Apakah fungsi butang 'New Slide' dalam PowerPoint?",
                choices: [
                    "Memadamkan slaid",
                    "Menambah slaid baru",
                    "Menyalin slaid",
                    "Menukar warna slaid"
                ],
                correctAnswer: 1
            },
            {
                question: "Apakah nama tab yang biasa digunakan untuk meletakkan animasi?",
                choices: [
                    "Home",
                    "Insert",
                    "Design",
                    "Animations"
                ],
                correctAnswer: 3
            },
            {
                question: "Bagaimanakah anda boleh menukar tema keseluruhan pembentangan?",
                choices: [
                    "Pada tab Format",
                    "Pada tab Design",
                    "Pada tab Slide Show",
                    "Pada tab Review"
                ],
                correctAnswer: 1
            },
            {
                question: "Apakah kegunaan 'Slide Master'?",
                choices: [
                    "Membuat slaid rahsia",
                    "Mengawal reka bentuk keseluruhan pembentangan",
                    "Menyimpan slaid",
                    "Mengimport slaid"
                ],
                correctAnswer: 1
            },
            {
                question: "Bagaimanakah anda boleh menambah nota pada slaid?",
                choices: [
                    "Pada tab Insert",
                    "Pada tab Home",
                    "Pada tab Review",
                    "Pada tab Notes"
                ],
                correctAnswer: 0
            },
            {
                question: "Apakah format fail PowerPoint biasa?",
                choices: [
                    ".doc",
                    ".ppt",
                    ".xlsx",
                    ".pdf"
                ],
                correctAnswer: 1
            },
            {
                question: "Apakah kegunaan 'Transitions' dalam PowerPoint?",
                choices: [
                    "Menukar warna slaid",
                    "Mengubah susunan slaid",
                    "Menambah kesan peralihan antara slaid",
                    "Memadam slaid"
                ],
                correctAnswer: 2
            }
        ];

        let currentQuestion = 0;
        let score = 0;

        function loadQuestion() {
            const questionObj = questions[currentQuestion];
            document.getElementById('question').textContent = questionObj.question;
            
            const choicesDiv = document.getElementById('choices');
            choicesDiv.innerHTML = '';
            
            questionObj.choices.forEach((choice, index) => {
                const button = document.createElement('button');
                button.textContent = choice;
                button.classList.add('btn');
                button.onclick = () => checkAnswer(index);
                choicesDiv.appendChild(button);
            });
        }

        function checkAnswer(selectedIndex) {
            const resultDiv = document.getElementById('result');
            
            if (selectedIndex === questions[currentQuestion].correctAnswer) {
                resultDiv.textContent = "✅ Jawapan Betul!";
                score++;
            } else {
                resultDiv.textContent = "❌ Jawapan Salah!";
            }

            currentQuestion++;

            if (currentQuestion < questions.length) {
                setTimeout(loadQuestion, 1500);
            } else {
                setTimeout(showFinalScore, 1500);
            }
        }

        function showFinalScore() {
            const gameContainer = document.querySelector('.game-container');
            gameContainer.innerHTML = `
                <h1>🏆 Tamat Kuiz!</h1>
                <p>Anda mendapat ${score} markah daripada ${questions.length} soalan.</p>
                <button class="btn" onclick="location.reload()">Main Semula</button>
            `;
        }

        // Memulakan permainan
        loadQuestion();
    </script>
</body>
</html>
