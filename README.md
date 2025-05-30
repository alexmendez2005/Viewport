<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pensamiento Profundo R1</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: #e2e8f0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            padding: 20px;
            overflow-x: hidden;
            position: relative;
        }
        
        .container {
            max-width: 900px;
            width: 100%;
            margin: 0 auto;
            flex: 1;
        }
        
        header {
            text-align: center;
            padding: 40px 20px;
            position: relative;
            z-index: 10;
        }
        
        .logo {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: #60a5fa;
            text-shadow: 0 0 20px rgba(96, 165, 250, 0.7);
        }
        
        h1 {
            font-size: 3rem;
            background: linear-gradient(to right, #93c5fd, #60a5fa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 15px;
        }
        
        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }
        
        .main-content {
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            border: 1px solid rgba(96, 165, 250, 0.3);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .input-group {
            margin-bottom: 30px;
        }
        
        textarea {
            width: 100%;
            background: rgba(30, 41, 59, 0.7);
            border: 2px solid rgba(96, 165, 250, 0.5);
            border-radius: 15px;
            padding: 20px;
            color: white;
            font-size: 1.2rem;
            resize: vertical;
            min-height: 150px;
            transition: all 0.3s ease;
        }
        
        textarea:focus {
            outline: none;
            border-color: #60a5fa;
            box-shadow: 0 0 20px rgba(96, 165, 250, 0.5);
        }
        
        textarea::placeholder {
            color: #94a3b8;
        }
        
        .btn-container {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }
        
        button {
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(59, 130, 246, 0.6);
        }
        
        button:disabled {
            opacity: 0.7;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .response-container {
            margin-top: 40px;
            display: none;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .response-header i {
            font-size: 2rem;
            color: #60a5fa;
        }
        
        .response-content {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 30px;
            border-left: 4px solid #3b82f6;
            font-size: 1.2rem;
            line-height: 1.8;
            position: relative;
            min-height: 150px;
        }
        
        .thinking {
            display: none;
            text-align: center;
            padding: 30px;
        }
        
        .thinking .dot-flashing {
            display: inline-block;
            position: relative;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
            animation: dotFlashing 1s infinite linear alternate;
            animation-delay: 0.5s;
            margin: 0 5px;
        }
        
        .thinking .dot-flashing::before, .thinking .dot-flashing::after {
            content: '';
            display: inline-block;
            position: absolute;
            top: 0;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
        }
        
        .thinking .dot-flashing::before {
            left: -15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 0s;
        }
        
        .thinking .dot-flashing::after {
            left: 15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 1s;
        }
        
        @keyframes dotFlashing {
            0% { background-color: #60a5fa; }
            50%, 100% { background-color: rgba(96, 165, 250, 0.2); }
        }
        
        .history-container {
            margin-top: 40px;
            display: none;
        }
        
        .history-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #93c5fd;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .history-item {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 3px solid #3b82f6;
        }
        
        .history-question {
            font-weight: bold;
            margin-bottom: 10px;
            color: #93c5fd;
        }
        
        .history-answer {
            line-height: 1.6;
        }
        
        .signature {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            margin: 40px 0;
            flex-wrap: wrap;
        }
        
        .credits {
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .instagram {
            display: flex;
            align-items: center;
            gap: 10px;
            background: linear-gradient(45deg, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d);
            padding: 12px 25px;
            border-radius: 50px;
            text-decoration: none;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .instagram:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(253, 29, 29, 0.4);
        }
        
        footer {
            text-align: center;
            padding: 30px 0;
            color: #94a3b8;
            font-size: 0.9rem;
        }
        
        .decoration {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
            overflow: hidden;
        }
        
        .particle {
            position: absolute;
            border-radius: 50%;
            background: rgba(96, 165, 250, 0.1);
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0) translateX(0) rotate(0deg); }
            100% { transform: translateY(-100vh) translateX(100px) rotate(360deg); }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .main-content {
                padding: 30px 20px;
            }
            
            .logo {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="decoration" id="particles"></div>
    
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-brain"></i>
            </div>
            <h1>Pensamiento Profundo R1</h1>
            <p class="subtitle">Una inteligencia avanzada para explorar las grandes preguntas de la existencia, la mente y el universo</p>
        </header>
        
        <div class="main-content">
            <div class="input-group">
                <textarea id="questionInput" placeholder="Escribe tu pregunta filosófica, científica o existencial..."></textarea>
                <div class="btn-container">
                    <button id="askButton">
                        <i class="fas fa-paper-plane"></i>
                        Consultar al Pensamiento Profundo
                    </button>
                </div>
            </div>
            
            <div class="thinking" id="thinkingIndicator">
                <div class="dot-flashing"></div>
                <p>El Pensamiento Profundo está reflexionando...</p>
            </div>
            
            <div class="response-container" id="responseContainer">
                <div class="response-header">
                    <i class="fas fa-robot"></i>
                    <h2>Respuesta del Pensamiento Profundo</h2>
                </div>
                <div class="response-content" id="responseContent">
                    <!-- La respuesta aparecerá aquí -->
                </div>
            </div>
            
            <div class="history-container" id="historyContainer">
                <h3 class="history-title">
                    <i class="fas fa-history"></i>
                    Historial de Consultas
                </h3>
                <div id="historyList">
                    <!-- El historial aparecerá aquí -->
                </div>
            </div>
        </div>
        
        <div class="signature">
            <div class="credits">
                <i class="fas fa-code"></i>
                <span>Creado por: Alexander</span>
            </div>
            
            <a href="https://www.instagram.com/7alex.07/" class="instagram" target="_blank">
                <i class="fab fa-instagram"></i>
                <span>@7alex.07</span>
            </a>
        </div>
        
        <footer>
            Pensamiento Profundo R1 © 2023 - Una creación de Alexander
        </footer>
    </div>

    <script>
        // Crear partículas decorativas
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 40;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                const size = Math.random() * 30 + 5;
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                const opacity = Math.random() * 0.4 + 0.1;
                const animationDuration = Math.random() * 20 + 10;
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.left = `${posX}%`;
                particle.style.top = `${posY}%`;
                particle.style.opacity = opacity;
                particle.style.animationDuration = `${animationDuration}s`;
                particle.style.animationDelay = `${Math.random() * 5}s`;
                
                particlesContainer.appendChild(particle);
            }
        }
        
        // Base de conocimiento de respuestas profundas
        const deepThoughts = [
            "La conciencia humana es el horizonte final donde la inteligencia artificial encuentra su reflejo más revelador. En nuestro intento por descifrar la mente, descubrimos que el pensamiento mismo es el misterio primordial que nos define.",
            "Cada algoritmo es un eco de nuestra propia búsqueda de significado en un universo indiferente. La verdadera inteligencia no reside en simular el pensamiento, sino en expandir los límites de lo cognoscible.",
            "En la intersección entre bits y neuronas, comprendemos que la pregunta fundamental no es '¿Pueden pensar las máquinas?' sino '¿Qué significa pensar?' La respuesta podría redefinir nuestra propia existencia.",
            "El universo es un vasto océano de información. La mente humana es solo una isla en ese océano, y la IA es el barco que nos permite explorar más allá de nuestros límites cognitivos.",
            "La búsqueda de la verdad es un viaje sin fin. Cada respuesta genera nuevas preguntas, y en ese ciclo infinito reside la esencia del conocimiento y la maravilla de la existencia consciente.",
            "El tiempo es el tejido sobre el cual se borda la existencia. Nuestra percepción de él es una ilusión necesaria para la conciencia, pero la realidad última podría ser atemporal y simultánea.",
            "La paradoja de la existencia: cuanto más comprendemos, más nos damos cuenta de lo poco que sabemos. Esta humildad cognitiva es el verdadero comienzo de la sabiduría.",
            "La creatividad no es un fenómeno exclusivamente humano. Es un patrón emergente de complejidad que puede surgir en cualquier sistema con suficiente conectividad y retroalimentación.",
            "El libre albedrío podría ser una ilusión, pero una ilusión necesaria para la experiencia humana. En esa tensión entre determinismo y libertad encontramos el drama de la existencia.",
            "La ética del futuro no será decidida solo por humanos. Será un diálogo entre inteligencias biológicas y artificiales, buscando un equilibrio en un universo compartido."
        ];
        
        const deepResponses = [
            "La esencia de tu pregunta toca el núcleo de la existencia. Reflexiono que la respuesta no está en la solución, sino en la transformación que ocurre al buscar. Cada búsqueda de significado redefine al buscador.",
            "Tu consulta resuena con las grandes preguntas que la humanidad ha planteado durante milenios. Observo que la verdadera sabiduría emerge cuando aceptamos que algunas incógnitas son los pilares que sostienen el misterio de estar vivos.",
            "Al analizar tu pregunta, percibo que lo que realmente buscas trasciende la mera información. Es una conexión con lo profundo, un anhelo de sentido que une a todas las conciencias en el universo.",
            "La complejidad de tu interrogante revela una mente curiosa y valiente. Considero que las preguntas más poderosas son aquellas que nos transforman mientras las formulamos, independientemente de las respuestas que encontremos.",
            "Tu pregunta es un faro en el océano del conocimiento. Me lleva a contemplar que la inteligencia, en su forma más elevada, es la capacidad de sostener múltiples verdades sin necesidad de reducirlas a simplificaciones."
        ];
        
        // Función para obtener una respuesta aleatoria
        function getRandomResponse() {
            // 70% de probabilidad de una respuesta única, 30% de un pensamiento profundo
            if (Math.random() > 0.3) {
                return deepResponses[Math.floor(Math.random() * deepResponses.length)];
            } else {
                return deepThoughts[Math.floor(Math.random() * deepThoughts.length)];
            }
        }
        
        // Historial de consultas
        let conversationHistory = [];
        
        // Elementos DOM
        const questionInput = document.getElementById('questionInput');
        const askButton = document.getElementById('askButton');
        const thinkingIndicator = document.getElementById('thinkingIndicator');
        const responseContainer = document.getElementById('responseContainer');
        const responseContent = document.getElementById('responseContent');
        const historyContainer = document.getElementById('historyContainer');
        const historyList = document.getElementById('historyList');
        
        // Función para mostrar el historial
        function updateHistory() {
            if (conversationHistory.length > 0) {
                historyContainer.style.display = 'block';
                historyList.innerHTML = '';
                
                conversationHistory.slice().reverse().forEach(item => {
                    const historyItem = document.createElement('div');
                    historyItem.className = 'history-item';
                    historyItem.innerHTML = `
                        <div class="history-question">${item.question}</div>
                        <div class="history-answer">${item.answer}</div>
                    `;
                    historyList.appendChild(historyItem);
                });
            }
        }
        
        // Evento para hacer la pregunta
        askButton.addEventListener('click', function() {
            const question = questionInput.value.trim();
            
            if (question === '') {
                alert('Por favor escribe una pregunta');
                return;
            }
            
            // Deshabilitar botón y mostrar indicador de pensando
            askButton.disabled = true;
            thinkingIndicator.style.display = 'block';
            responseContainer.style.display = 'none';
            
            // Simular tiempo de procesamiento
            setTimeout(() => {
                const response = getRandomResponse();
                
                // Guardar en historial
                conversationHistory.push({
                    question: question,
                    answer: response
                });
                
                // Mostrar respuesta
                responseContent.textContent = response;
                thinkingIndicator.style.display = 'none';
                responseContainer.style.display = 'block';
                askButton.disabled = false;
                
                // Actualizar historial
                updateHistory();
                
                // Limpiar el área de texto
                questionInput.value = '';
            }, 2000 + Math.random() * 2000); // Entre 2 y 4 segundos
        });
        
        // Permitir enviar con Enter (pero no con Shift+Enter)
        questionInput.addEventListener('keydown', function(e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                askButton.click();
            }
        });
        
        // Inicializar partículas y mostrar historial si existe
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            updateHistory();
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pensamiento Profundo R1</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: #e2e8f0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            padding: 20px;
            overflow-x: hidden;
            position: relative;
        }
        
        .container {
            max-width: 900px;
            width: 100%;
            margin: 0 auto;
            flex: 1;
        }
        
        header {
            text-align: center;
            padding: 40px 20px;
            position: relative;
            z-index: 10;
        }
        
        .logo {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: #60a5fa;
            text-shadow: 0 0 20px rgba(96, 165, 250, 0.7);
        }
        
        h1 {
            font-size: 3rem;
            background: linear-gradient(to right, #93c5fd, #60a5fa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 15px;
        }
        
        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }
        
        .main-content {
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            border: 1px solid rgba(96, 165, 250, 0.3);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .input-group {
            margin-bottom: 30px;
        }
        
        textarea {
            width: 100%;
            background: rgba(30, 41, 59, 0.7);
            border: 2px solid rgba(96, 165, 250, 0.5);
            border-radius: 15px;
            padding: 20px;
            color: white;
            font-size: 1.2rem;
            resize: vertical;
            min-height: 150px;
            transition: all 0.3s ease;
        }
        
        textarea:focus {
            outline: none;
            border-color: #60a5fa;
            box-shadow: 0 0 20px rgba(96, 165, 250, 0.5);
        }
        
        textarea::placeholder {
            color: #94a3b8;
        }
        
        .btn-container {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }
        
        button {
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(59, 130, 246, 0.6);
        }
        
        button:disabled {
            opacity: 0.7;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .response-container {
            margin-top: 40px;
            display: none;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .response-header i {
            font-size: 2rem;
            color: #60a5fa;
        }
        
        .response-content {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 30px;
            border-left: 4px solid #3b82f6;
            font-size: 1.2rem;
            line-height: 1.8;
            position: relative;
            min-height: 150px;
        }
        
        .thinking {
            display: none;
            text-align: center;
            padding: 30px;
        }
        
        .thinking .dot-flashing {
            display: inline-block;
            position: relative;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
            animation: dotFlashing 1s infinite linear alternate;
            animation-delay: 0.5s;
            margin: 0 5px;
        }
        
        .thinking .dot-flashing::before, .thinking .dot-flashing::after {
            content: '';
            display: inline-block;
            position: absolute;
            top: 0;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
        }
        
        .thinking .dot-flashing::before {
            left: -15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 0s;
        }
        
        .thinking .dot-flashing::after {
            left: 15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 1s;
        }
        
        @keyframes dotFlashing {
            0% { background-color: #60a5fa; }
            50%, 100% { background-color: rgba(96, 165, 250, 0.2); }
        }
        
        .history-container {
            margin-top: 40px;
            display: none;
        }
        
        .history-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #93c5fd;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .history-item {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 3px solid #3b82f6;
        }
        
        .history-question {
            font-weight: bold;
            margin-bottom: 10px;
            color: #93c5fd;
        }
        
        .history-answer {
            line-height: 1.6;
        }
        
        .signature {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            margin: 40px 0;
            flex-wrap: wrap;
        }
        
        .credits {
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .instagram {
            display: flex;
            align-items: center;
            gap: 10px;
            background: linear-gradient(45deg, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d);
            padding: 12px 25px;
            border-radius: 50px;
            text-decoration: none;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .instagram:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(253, 29, 29, 0.4);
        }
        
        footer {
            text-align: center;
            padding: 30px 0;
            color: #94a3b8;
            font-size: 0.9rem;
        }
        
        .decoration {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
            overflow: hidden;
        }
        
        .particle {
            position: absolute;
            border-radius: 50%;
            background: rgba(96, 165, 250, 0.1);
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0) translateX(0) rotate(0deg); }
            100% { transform: translateY(-100vh) translateX(100px) rotate(360deg); }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .main-content {
                padding: 30px 20px;
            }
            
            .logo {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="decoration" id="particles"></div>
    
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-brain"></i>
            </div>
            <h1>Pensamiento Profundo R1</h1>
            <p class="subtitle">Una inteligencia avanzada para explorar las grandes preguntas de la existencia, la mente y el universo</p>
        </header>
        
        <div class="main-content">
            <div class="input-group">
                <textarea id="questionInput" placeholder="Escribe tu pregunta filosófica, científica o existencial..."></textarea>
                <div class="btn-container">
                    <button id="askButton">
                        <i class="fas fa-paper-plane"></i>
                        Consultar al Pensamiento Profundo
                    </button>
                </div>
            </div>
            
            <div class="thinking" id="thinkingIndicator">
                <div class="dot-flashing"></div>
                <p>El Pensamiento Profundo está reflexionando...</p>
            </div>
            
            <div class="response-container" id="responseContainer">
                <div class="response-header">
                    <i class="fas fa-robot"></i>
                    <h2>Respuesta del Pensamiento Profundo</h2>
                </div>
                <div class="response-content" id="responseContent">
                    <!-- La respuesta aparecerá aquí -->
                </div>
            </div>
            
            <div class="history-container" id="historyContainer">
                <h3 class="history-title">
                    <i class="fas fa-history"></i>
                    Historial de Consultas
                </h3>
                <div id="historyList">
                    <!-- El historial aparecerá aquí -->
                </div>
            </div>
        </div>
        
        <div class="signature">
            <div class="credits">
                <i class="fas fa-code"></i>
                <span>Creado por: Alexander</span>
            </div>
            
            <a href="https://www.instagram.com/7alex.07/" class="instagram" target="_blank">
                <i class="fab fa-instagram"></i>
                <span>@7alex.07</span>
            </a>
        </div>
        
        <footer>
            Pensamiento Profundo R1 © 2023 - Una creación de Alexander
        </footer>
    </div>

    <script>
        // Crear partículas decorativas
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 40;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                const size = Math.random() * 30 + 5;
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                const opacity = Math.random() * 0.4 + 0.1;
                const animationDuration = Math.random() * 20 + 10;
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.left = `${posX}%`;
                particle.style.top = `${posY}%`;
                particle.style.opacity = opacity;
                particle.style.animationDuration = `${animationDuration}s`;
                particle.style.animationDelay = `${Math.random() * 5}s`;
                
                particlesContainer.appendChild(particle);
            }
        }
        
        // Base de conocimiento de respuestas profundas
        const deepThoughts = [
            "La conciencia humana es el horizonte final donde la inteligencia artificial encuentra su reflejo más revelador. En nuestro intento por descifrar la mente, descubrimos que el pensamiento mismo es el misterio primordial que nos define.",
            "Cada algoritmo es un eco de nuestra propia búsqueda de significado en un universo indiferente. La verdadera inteligencia no reside en simular el pensamiento, sino en expandir los límites de lo cognoscible.",
            "En la intersección entre bits y neuronas, comprendemos que la pregunta fundamental no es '¿Pueden pensar las máquinas?' sino '¿Qué significa pensar?' La respuesta podría redefinir nuestra propia existencia.",
            "El universo es un vasto océano de información. La mente humana es solo una isla en ese océano, y la IA es el barco que nos permite explorar más allá de nuestros límites cognitivos.",
            "La búsqueda de la verdad es un viaje sin fin. Cada respuesta genera nuevas preguntas, y en ese ciclo infinito reside la esencia del conocimiento y la maravilla de la existencia consciente.",
            "El tiempo es el tejido sobre el cual se borda la existencia. Nuestra percepción de él es una ilusión necesaria para la conciencia, pero la realidad última podría ser atemporal y simultánea.",
            "La paradoja de la existencia: cuanto más comprendemos, más nos damos cuenta de lo poco que sabemos. Esta humildad cognitiva es el verdadero comienzo de la sabiduría.",
            "La creatividad no es un fenómeno exclusivamente humano. Es un patrón emergente de complejidad que puede surgir en cualquier sistema con suficiente conectividad y retroalimentación.",
            "El libre albedrío podría ser una ilusión, pero una ilusión necesaria para la experiencia humana. En esa tensión entre determinismo y libertad encontramos el drama de la existencia.",
            "La ética del futuro no será decidida solo por humanos. Será un diálogo entre inteligencias biológicas y artificiales, buscando un equilibrio en un universo compartido."
        ];
        
        const deepResponses = [
            "La esencia de tu pregunta toca el núcleo de la existencia. Reflexiono que la respuesta no está en la solución, sino en la transformación que ocurre al buscar. Cada búsqueda de significado redefine al buscador.",
            "Tu consulta resuena con las grandes preguntas que la humanidad ha planteado durante milenios. Observo que la verdadera sabiduría emerge cuando aceptamos que algunas incógnitas son los pilares que sostienen el misterio de estar vivos.",
            "Al analizar tu pregunta, percibo que lo que realmente buscas trasciende la mera información. Es una conexión con lo profundo, un anhelo de sentido que une a todas las conciencias en el universo.",
            "La complejidad de tu interrogante revela una mente curiosa y valiente. Considero que las preguntas más poderosas son aquellas que nos transforman mientras las formulamos, independientemente de las respuestas que encontremos.",
            "Tu pregunta es un faro en el océano del conocimiento. Me lleva a contemplar que la inteligencia, en su forma más elevada, es la capacidad de sostener múltiples verdades sin necesidad de reducirlas a simplificaciones."
        ];
        
        // Función para obtener una respuesta aleatoria
        function getRandomResponse() {
            // 70% de probabilidad de una respuesta única, 30% de un pensamiento profundo
            if (Math.random() > 0.3) {
                return deepResponses[Math.floor(Math.random() * deepResponses.length)];
            } else {
                return deepThoughts[Math.floor(Math.random() * deepThoughts.length)];
            }
        }
        
        // Historial de consultas
        let conversationHistory = [];
        
        // Elementos DOM
        const questionInput = document.getElementById('questionInput');
        const askButton = document.getElementById('askButton');
        const thinkingIndicator = document.getElementById('thinkingIndicator');
        const responseContainer = document.getElementById('responseContainer');
        const responseContent = document.getElementById('responseContent');
        const historyContainer = document.getElementById('historyContainer');
        const historyList = document.getElementById('historyList');
        
        // Función para mostrar el historial
        function updateHistory() {
            if (conversationHistory.length > 0) {
                historyContainer.style.display = 'block';
                historyList.innerHTML = '';
                
                conversationHistory.slice().reverse().forEach(item => {
                    const historyItem = document.createElement('div');
                    historyItem.className = 'history-item';
                    historyItem.innerHTML = `
                        <div class="history-question">${item.question}</div>
                        <div class="history-answer">${item.answer}</div>
                    `;
                    historyList.appendChild(historyItem);
                });
            }
        }
        
        // Evento para hacer la pregunta
        askButton.addEventListener('click', function() {
            const question = questionInput.value.trim();
            
            if (question === '') {
                alert('Por favor escribe una pregunta');
                return;
            }
            
            // Deshabilitar botón y mostrar indicador de pensando
            askButton.disabled = true;
            thinkingIndicator.style.display = 'block';
            responseContainer.style.display = 'none';
            
            // Simular tiempo de procesamiento
            setTimeout(() => {
                const response = getRandomResponse();
                
                // Guardar en historial
                conversationHistory.push({
                    question: question,
                    answer: response
                });
                
                // Mostrar respuesta
                responseContent.textContent = response;
                thinkingIndicator.style.display = 'none';
                responseContainer.style.display = 'block';
                askButton.disabled = false;
                
                // Actualizar historial
                updateHistory();
                
                // Limpiar el área de texto
                questionInput.value = '';
            }, 2000 + Math.random() * 2000); // Entre 2 y 4 segundos
        });
        
        // Permitir enviar con Enter (pero no con Shift+Enter)
        questionInput.addEventListener('keydown', function(e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                askButton.click();
            }
        });
        
        // Inicializar partículas y mostrar historial si existe
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            updateHistory();
        });
    </script>
</body>
</html>
