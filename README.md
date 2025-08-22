
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juegos de Cocina</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            min-height: 100vh;
            padding: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            width: 100%;
            max-width: 500px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            color: white;
            padding: 25px 20px;
            text-align: center;
            position: relative;
        }

        .header h1 {
            font-size: 1.8rem;
            margin-bottom: 8px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .header p {
            font-size: 1rem;
            opacity: 0.9;
        }

        /* MENÚ PRINCIPAL */
        .menu-screen {
            padding: 30px 20px;
            text-align: center;
        }

        .menu-title {
            font-size: 1.6rem;
            color: #333;
            margin-bottom: 30px;
            font-weight: bold;
            position: relative;
            display: inline-block;
        }

        .menu-title::after {
            content: "";
            position: absolute;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            border-radius: 2px;
        }

        .game-selector {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin: 0 auto;
        }

        .game-option {
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            color: white;
            border: none;
            border-radius: 15px;
            padding: 20px 15px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .game-option::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, rgba(255,255,255,0.2) 0%, rgba(255,255,255,0) 100%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .game-option:hover, .game-option:active {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        .game-option:hover::before, .game-option:active::before {
            opacity: 1;
        }

        .game-option .emoji {
            font-size: 1.5rem;
            margin-right: 10px;
            display: block;
            margin-bottom: 5px;
        }

        .game-description {
            font-size: 0.8rem;
            margin-top: 8px;
            opacity: 0.9;
            font-weight: normal;
        }

        /* PANTALLAS DE JUEGOS */
        .game-screen {
            display: none;
            padding: 20px;
        }

        .game-header {
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            color: white;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            text-align: center;
            position: relative;
        }

        .game-title {
            font-size: 1.4rem;
            font-weight: bold;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
            padding: 0 40px;
        }

        .back-btn {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(255,255,255,0.2);
            color: white;
            border: 2px solid white;
            border-radius: 8px;
            padding: 6px 12px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        .back-btn:hover, .back-btn:active {
            background: white;
            color: #ff7e5f;
        }

        .question-container {
            text-align: center;
            margin-bottom: 30px;
        }

        .score {
            background: linear-gradient(135deg, #ffd89b 0%, #19547b 100%);
            color: white;
            padding: 12px;
            border-radius: 10px;
            text-align: center;
            font-size: 1rem;
            font-weight: bold;
            margin-bottom: 15px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
        }

        .tool-display {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            border: 3px solid #ff7e5f;
            border-radius: 15px;
            padding: 25px 15px;
            margin-bottom: 20px;
            font-size: 1.8rem;
            font-weight: bold;
            color: #333;
            text-shadow: 1px 1px 2px rgba(255,255,255,0.8);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        .options-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        .option-btn {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border: 2px solid #ff8a80;
            border-radius: 12px;
            padding: 15px;
            font-size: 1.1rem;
            font-weight: bold;
            color: #333;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            text-shadow: 1px 1px 2px rgba(255,255,255,0.8);
        }

        .option-btn:hover, .option-btn:active {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.15);
            background: linear-gradient(135deg, #fff9c4 0%, #f093fb 100%);
        }

        .option-btn.correct {
            background: linear-gradient(135deg, #a8e6cf 0%, #88d8a3 100%);
            border-color: #4caf50;
            color: #2e7d32;
            animation: correctPulse 0.6s ease-in-out;
        }

        .option-btn.incorrect {
            background: linear-gradient(135deg, #ffcdd2 0%, #f8bbd9 100%);
            border-color: #f44336;
            color: #c62828;
            animation: incorrectShake 0.6s ease-in-out;
        }

        @keyframes correctPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        @keyframes incorrectShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-3px); }
            75% { transform: translateX(3px); }
        }

        .feedback {
            margin-top: 15px;
            padding: 12px;
            border-radius: 10px;
            font-weight: bold;
            font-size: 1rem;
            text-align: center;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }

        .feedback.correct {
            background: linear-gradient(135deg, #c8e6c9 0%, #a5d6a7 100%);
            color: #2e7d32;
            border: 2px solid #4caf50;
        }

        .feedback.incorrect {
            background: linear-gradient(135deg, #ffcdd2 0%, #f8bbd9 100%);
            color: #c62828;
            border: 2px solid #f44336;
        }

        .controls {
            text-align: center;
            margin-top: 20px;
        }

        .next-btn {
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 12px 30px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.15);
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
            display: inline-block;
            margin-right: 10px;
        }

        .next-btn:hover, .next-btn:active {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        .next-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        .reset-btn {
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%);
            color: white;
            border: none;
            border-radius: 15px;
            padding: 10px 20px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        .reset-btn:hover, .reset-btn:active {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.15);
        }

        /* Animación de celebración */
        .celebrate {
            font-size: 2.5rem;
            animation: celebrate 1s infinite alternate;
            display: block;
            margin: 10px 0;
        }

        @keyframes celebrate {
            0% { transform: scale(1); }
            100% { transform: scale(1.2); }
        }

        /* Media queries para tablets y pantallas más grandes */
        @media (min-width: 768px) {
            .container {
                max-width: 700px;
            }
            
            .header {
                padding: 30px;
            }
            
            .header h1 {
                font-size: 2.2rem;
            }
            
            .menu-screen {
                padding: 40px 30px;
            }
            
            .menu-title {
                font-size: 2rem;
            }
            
            .game-option {
                padding: 25px 20px;
                font-size: 1.4rem;
            }
            
            .game-screen {
                padding: 30px;
            }
            
            .options-grid {
                grid-template-columns: 1fr 1fr;
                gap: 20px;
            }
            
            .tool-display {
                font-size: 2.2rem;
                padding: 30px 20px;
            }
        }

        /* Media queries para pantallas grandes */
        @media (min-width: 1024px) {
            body {
                padding: 30px;
            }
            
            .container {
                max-width: 900px;
            }
            
            .options-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🍳 Juegos de Cocina 🍳</h1>
            <p>Aprende sobre herramientas culinarias jugando</p>
        </div>

        <!-- MENÚ PRINCIPAL -->
        <div class="menu-screen" id="menuScreen">
            <h2 class="menu-title">Elige tu juego favorito</h2>
            <div class="game-selector">
                <button class="game-option" onclick="startGame(1)">
                    <span class="emoji">🔧</span>
                    ¿Cuál es su función?
                    <div class="game-description">
                        Identifica para qué sirve cada herramienta de cocina
                    </div>
                </button>
                
                <button class="game-option" onclick="startGame(2)">
                    <span class="emoji">🌐</span>
                    Inglés ⇄ Español
                    <div class="game-description">
                        Traduce nombres de herramientas entre idiomas
                    </div>
                </button>
            </div>
        </div>

        <!-- JUEGO 1: FUNCIONALIDAD -->
        <div class="game-screen" id="game1Screen">
            <div class="game-header">
                <button class="back-btn" onclick="showMenu()">← Volver</button>
                <div class="game-title">🔧 ¿Cuál es su función?</div>
            </div>
            <div class="score" id="score1">
                Puntuación: <span id="scoreValue1">0</span> / <span id="totalQuestions1">0</span>
            </div>
            <div class="question-container">
                <div class="tool-display" id="toolDisplay1"></div>
                <div class="options-grid" id="optionsGrid1"></div>
                <div class="feedback" id="feedback1" style="display: none;"></div>
                <div class="controls">
                    <button class="next-btn" id="nextBtn1" onclick="nextQuestion1()" disabled>
                        Siguiente
                    </button>
                    <button class="reset-btn" onclick="resetGame1()">
                        Reiniciar
                    </button>
                </div>
            </div>
        </div>

        <!-- JUEGO 2: TRADUCCIÓN -->
        <div class="game-screen" id="game2Screen">
            <div class="game-header">
                <button class="back-btn" onclick="showMenu()">← Volver</button>
                <div class="game-title">🌐 Inglés ⇄ Español</div>
            </div>
            <div class="score" id="score2">
                Puntuación: <span id="scoreValue2">0</span> / <span id="totalQuestions2">0</span>
            </div>
            <div class="question-container">
                <div class="tool-display" id="toolDisplay2"></div>
                <div class="options-grid" id="optionsGrid2"></div>
                <div class="feedback" id="feedback2" style="display: none;"></div>
                <div class="controls">
                    <button class="next-btn" id="nextBtn2" onclick="nextQuestion2()" disabled>
                        Siguiente
                    </button>
                    <button class="reset-btn" onclick="resetGame2()">
                        Reiniciar
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Datos para Juego 1: Funcionalidad
        const game1Data = [
            {
                tool: "AMASADORA",
                correct: "Amasar",
                options: ["Cortar", "Medir", "Amasar", "Calentar"]
            },
            {
                tool: "BALANZA DIGITAL",
                correct: "Pesar",
                options: ["Cortar", "Pesar", "Mezclar", "Calentar"]
            },
            {
                tool: "BATIDORA",
                correct: "Mezclar",
                options: ["Pesar", "Cortar", "Mezclar", "Medir"]
            },
            {
                tool: "TERMOSELLADORA",
                correct: "Sellar",
                options: ["Cortar", "Sellar", "Pesar", "Mezclar"]
            },
            {
                tool: "HORNO PIZZERO",
                correct: "Hornear",
                options: ["Mezclar", "Pesar", "Hornear", "Cortar"]
            }
        ];

        // Datos para Juego 2: Traducción
        const game2Data = [
            {
                word: "COFIA",
                correct: "CAP",
                options: ["CAP", "KITCHEN APRON", "KITCHEN GLOVES", "HEADSCARF"]
            },
            {
                word: "CAP",
                correct: "COFIA",
                options: ["COFIA", "DELANTAL DE COCINA", "GUANTES DE COCINA", "BARBIJO"]
            },
            {
                word: "DELANTAL DE COCINA",
                correct: "KITCHEN APRON",
                options: ["KITCHEN APRON", "KITCHEN GLOVES", "LATEX GLOVES", "HEADSCARF"]
            },
            {
                word: "KITCHEN APRON",
                correct: "DELANTAL DE COCINA",
                options: ["DELANTAL DE COCINA", "GUANTES DE COCINA", "GUANTES DE LATEX", "BARBIJO"]
            },
            {
                word: "GUANTES DE COCINA",
                correct: "KITCHEN GLOVES",
                options: ["KITCHEN GLOVES", "LATEX GLOVES", "CAP", "HEADSCARF"]
            },
            {
                word: "KITCHEN GLOVES",
                correct: "GUANTES DE COCINA",
                options: ["GUANTES DE COCINA", "GUANTES DE LATEX", "COFIA", "BARBIJO"]
            },
            {
                word: "GUANTES DE LATEX",
                correct: "LATEX GLOVES",
                options: ["LATEX GLOVES", "KITCHEN GLOVES", "CAP", "HEADSCARF"]
            },
            {
                word: "LATEX GLOVES",
                correct: "GUANTES DE LATEX",
                options: ["GUANTES DE LATEX", "GUANTES DE COCINA", "COFIA", "BARBIJO"]
            },
            {
                word: "BARBIJO",
                correct: "HEADSCARF",
                options: ["HEADSCARF", "CAP", "KITCHEN APRON", "KITCHEN GLOVES"]
            },
            {
                word: "HEADSCARF",
                correct: "BARBIJO",
                options: ["BARBIJO", "COFIA", "DELANTAL DE COCINA", "GUANTES DE COCINA"]
            },
            {
                word: "BALANZA DIGITAL",
                correct: "DIGITAL SCALE",
                options: ["DIGITAL SCALE", "BLENDER", "MIX", "HEAT SEALER"]
            },
            {
                word: "DIGITAL SCALE",
                correct: "BALANZA DIGITAL",
                options: ["BALANZA DIGITAL", "AMASADORA", "BATIDORA", "TERMOSELLADORA"]
            },
            {
                word: "AMASADORA",
                correct: "KNEADER",
                options: ["KNEADER", "BLENDER", "MIX", "HEAT SEALER"]
            },
            {
                word: "KNEADER",
                correct: "AMASADORA",
                options: ["AMASADORA", "BATIDORA", "TERMOSELLADORA", "HORNO PIZZERO"]
            },
            {
                word: "BATIDORA",
                correct: "BLENDER",
                options: ["BLENDER", "MIX", "KNEADER", "HEAT SEALER"]
            },
            {
                word: "BLENDER",
                correct: "BATIDORA",
                options: ["BATIDORA", "AMASADORA", "TERMOSELLADORA", "HORNO PIZZERO"]
            },
            {
                word: "BATIDORA",
                correct: "MIX",
                options: ["MIX", "BLENDER", "KNEADER", "HEAT SEALER"]
            },
            {
                word: "MIX",
                correct: "BATIDORA",
                options: ["BATIDORA", "AMASADORA", "TERMOSELLADORA", "HORNO PIZZERO"]
            },
            {
                word: "TERMOSELLADORA",
                correct: "HEAT SEALER",
                options: ["HEAT SEALER", "BLENDER", "MIX", "PIZZA OVEN"]
            },
            {
                word: "HEAT SEALER",
                correct: "TERMOSELLADORA",
                options: ["TERMOSELLADORA", "AMASADORA", "BATIDORA", "HORNO PIZZERO"]
            },
            {
                word: "HORNO PIZZERO",
                correct: "PIZZA OVEN",
                options: ["PIZZA OVEN", "BLENDER", "MIX", "HEAT SEALER"]
            },
            {
                word: "PIZZA OVEN",
                correct: "HORNO PIZZERO",
                options: ["HORNO PIZZERO", "AMASADORA", "BATIDORA", "TERMOSELLADORA"]
            }
        ];

      // Variables de estado
        let currentScreen = 'menu';
        let game1Index = 0;
        let game1Score = 0;
        let game1Questions = [...game1Data];

        let game2Index = 0;
        let game2Score = 0;
        let game2Questions = [...game2Data];

        // Navegación entre pantallas
        function showMenu() {
            document.getElementById('menuScreen').style.display = 'block';
            document.getElementById('game1Screen').style.display = 'none';
            document.getElementById('game2Screen').style.display = 'none';
            currentScreen = 'menu';
        }

        function startGame(gameNumber) {
            document.getElementById('menuScreen').style.display = 'none';
            
            if (gameNumber === 1) {
                document.getElementById('game1Screen').style.display = 'block';
                document.getElementById('game2Screen').style.display = 'none';
                currentScreen = 'game1';
                initGame1();
            } else {
                document.getElementById('game1Screen').style.display = 'none';
                document.getElementById('game2Screen').style.display = 'block';
                currentScreen = 'game2';
                initGame2();
            }
        }
        
        // Función para mezclar array
        function shuffleArray(array) {
            const newArray = [...array];
            for (let i = newArray.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [newArray[i], newArray[j]] = [newArray[j], newArray[i]];
            }
            return newArray;
        }

        // Inicializar juegos
        function initGame1() {
            game1Questions = shuffleArray(game1Data);
            game1Index = 0;
            game1Score = 0;
            updateScore1();
            showQuestion1();
            document.getElementById('nextBtn1').style.display = 'inline-block';
        }

        function initGame2() {
            game2Questions = shuffleArray(game2Data);
            game2Index = 0;
            game2Score = 0;
            updateScore2();
            showQuestion2();
            document.getElementById('nextBtn2').style.display = 'inline-block';
        }

        // Mostrar pregunta Juego 1
        function showQuestion1() {
            if (game1Index >= game1Questions.length) {
                document.getElementById('toolDisplay1').innerHTML = '<span class="celebrate">🎉</span> ¡Juego Completado! <span class="celebrate">🎉</span><br><small>¡Excelente trabajo!</small><br>Puntuación final: ' + game1Score + ' / ' + game1Questions.length;
                document.getElementById('optionsGrid1').innerHTML = '';
                document.getElementById('feedback1').style.display = 'none';
                document.getElementById('nextBtn1').style.display = 'none';
                return;
            }
            
        const question = game1Questions[game1Index];
            document.getElementById('toolDisplay1').textContent = question.tool;
            
            const shuffledOptions = shuffleArray(question.options);
            const optionsHtml = shuffledOptions.map(option => 
                `<button class="option-btn" onclick="selectOption1('${option}')">${option}</button>`
            ).join('');
            
            document.getElementById('optionsGrid1').innerHTML = optionsHtml;
            document.getElementById('feedback1').style.display = 'none';
            document.getElementById('nextBtn1').disabled = true;
        }

        // Mostrar pregunta Juego 2
        function showQuestion2() {
            if (game2Index >= game2Questions.length) {
                document.getElementById('toolDisplay2').innerHTML = '<span class="celebrate">🎉</span> ¡Juego Completado! <span class="celebrate">🎉</span><br><small>¡Excelente trabajo!</small><br>Puntuación final: ' + game2Score + ' / ' + game2Questions.length;
                document.getElementById('optionsGrid2').innerHTML = '';
                document.getElementById('feedback2').style.display = 'none';
                document.getElementById('nextBtn2').style.display = 'none';
                return;
            }

            const question = game2Questions[game2Index];
            document.getElementById('toolDisplay2').textContent = question.word;
            
            const shuffledOptions = shuffleArray(question.options);
            const optionsHtml = shuffledOptions.map(option => 
                `<button class="option-btn" onclick="selectOption2('${option}')">${option}</button>`
            ).join('');
            
            document.getElementById('optionsGrid2').innerHTML = optionsHtml;
            document.getElementById('feedback2').style.display = 'none';
            document.getElementById('nextBtn2').disabled = true;
        }
                // Seleccionar opción Juego 1
        function selectOption1(selected) {
            const question = game1Questions[game1Index];
            const buttons = document.querySelectorAll('#optionsGrid1 .option-btn');
            const feedback = document.getElementById('feedback1');
            
            buttons.forEach(btn => {
                btn.disabled = true;
                if (btn.textContent === question.correct) {
                    btn.classList.add('correct');
                } else if (btn.textContent === selected && selected !== question.correct) {
                    btn.classList.add('incorrect');
                }
            });

            if (selected === question.correct) {
                game1Score++;
                feedback.textContent = '¡Correcto! 🎉';
                feedback.className = 'feedback correct';
            } else {
                feedback.textContent = `Incorrecto. La respuesta correcta es: ${question.correct}`;
                feedback.className = 'feedback incorrect';
            }
            
            feedback.style.display = 'block';
            document.getElementById('nextBtn1').disabled = false;
            updateScore1();
        }

        // Seleccionar opción Juego 2
        function selectOption2(selected)
        {
            const question = game2Questions[game2Index];
            const buttons = document.querySelectorAll('#optionsGrid2 .option-btn');
            const feedback = document.getElementById('feedback2');
            
            buttons.forEach(btn => {
                btn.disabled = true;
                if (btn.textContent === question.correct) {
                    btn.classList.add('correct');
                } else if (btn.textContent === selected && selected !== question.correct) {
                    btn.classList.add('incorrect');
                }
            });

            if (selected === question.correct) {
                game2Score++;
                feedback.textContent = '¡Correcto! 🎉';
                feedback.className = 'feedback correct';
            } else {
                feedback.textContent = `Incorrecto. La respuesta correcta es: ${question.correct}`;
                feedback.className = 'feedback incorrect';
            }
            
            feedback.style.display = 'block';
            document.getElementById('nextBtn2').disabled = false;
            updateScore2();
        }

        // Siguiente pregunta
        function nextQuestion1() {
            game1Index++;
            showQuestion1();
        }

        function nextQuestion2() {
            game2Index++;
            showQuestion2();
        }

        // Actualizar puntuaciones
        
function updateScore1() {
            document.getElementById('scoreValue1').textContent = game1Score;
            document.getElementById('totalQuestions1').textContent = Math.min(game1Index + 1, game1Questions.length);
        }

        function updateScore2() {
            document.getElementById('scoreValue2').textContent = game2Score;
            document.getElementById('totalQuestions2').textContent = Math.min(game2Index + 1, game2Questions.length);
        }

        // Reiniciar juegos
        function resetGame1() {
            initGame1();
        }

        function resetGame2() {
            initGame2();
        }

        // Inicializar al cargar la página
        window.onload = function() {
            showMenu();
        };
    </script>
</body>
</html>
```
