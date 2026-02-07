<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Para Mónica 💖</title>

    <!-- =========================
         FUENTES ROMÁNTICAS
    ========================== -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Great+Vibes&display=swap" rel="stylesheet">

    <style>
        /* =========================
           ESTILOS GENERALES
        ========================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #fbd3e9, #cbb4d4);
            font-family: 'Playfair Display', serif;
            color: #5a2a4a;
            overflow-x: hidden;
            transition: background 1s ease;
        }

        section {
            min-height: 100vh;
            padding: 60px 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        /* =========================
           PANTALLA DE BIENVENIDA
        ========================== */
        .welcome {
            font-size: 2.2rem;
            margin-bottom: 20px;
            animation: fadeIn 2s ease;
        }

        .name {
            font-family: 'Great Vibes', cursive;
            font-size: 4rem;
            color: #c2185b;
        }

        /* =========================
           TÍTULO PRINCIPAL
        ========================== */
        h1 {
            font-size: 3rem;
            margin-bottom: 30px;
            animation: fadeInUp 2s ease;
        }

        /* =========================
           TEXTO ROMÁNTICO
        ========================== */
        .romantic-text {
            max-width: 800px;
            font-size: 1.3rem;
            line-height: 1.8;
            margin-bottom: 40px;
        }

        /* =========================
           BOTÓN INTERACTIVO
        ========================== */
        button {
            padding: 15px 35px;
            font-size: 1.2rem;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            background: linear-gradient(135deg, #ff5f9e, #ff85b3);
            color: white;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        button:hover {
            transform: scale(1.08);
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
        }

        /* =========================
           MENSAJE SORPRESA
        ========================== */
        .surprise {
            display: none;
            font-size: 2rem;
            margin-top: 30px;
            color: #b0004f;
            animation: fadeIn 2s ease;
        }

        /* =========================
           MENSAJE FINAL
        ========================== */
        .final-message {
            font-size: 2.5rem;
            font-family: 'Great Vibes', cursive;
            margin-top: 60px;
            color: #c2185b;
        }

        /* =========================
           CORAZONES ANIMADOS
        ========================== */
        .heart {
            position: fixed;
            bottom: -20px;
            font-size: 20px;
            color: rgba(255, 0, 100, 0.8);
            animation: floatUp 6s linear forwards;
            pointer-events: none;
        }

        /* =========================
           BOTÓN MÚSICA
        ========================== */
        .music-control {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255,255,255,0.8);
            border-radius: 50%;
            padding: 12px;
            cursor: pointer;
            font-size: 20px;
        }

        /* =========================
           ANIMACIONES
        ========================== */
        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.8);
                opacity: 1;
            }
            100% {
                transform: translateY(-110vh) scale(1.5);
                opacity: 0;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>

<body>

    <!-- =========================
         MÚSICA ROMÁNTICA
         (Reemplaza el archivo si deseas)
    ========================== -->
    <audio id="music" loop>
        <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_1b7a8cfe87.mp3" type="audio/mpeg">
    </audio>

    <div class="music-control" onclick="toggleMusic()">🎵</div>

    <!-- =========================
         SECCIÓN PRINCIPAL
    ========================== -->
    <section>
        <div class="welcome">
            Hola <span class="name">Mónica</span> 💖  
            <br>
            esto es solo para ti
        </div>

        <h1>Mi amor </h1>

        <p class="romantic-text" id="typedText"></p>

        <button onclick="loveAction()">Haz clic si me amas 💕</button>

        <div class="surprise" id="surprise">
            Sabía que dirías que sí 💘✨
        </div>

        <div class="final-message">
            Te amo hoy, mañana y siempre ❤️
        </div>
    </section>

    <script>
        /* =========================
           TEXTO CON EFECTO
           MÁQUINA DE ESCRIBIR
        ========================== */
        const text = `Mónica, desde que llegaste a mi vida todo tiene más color, más sentido y más magia.
Cada sonrisa tuya ilumina mis días y cada pensamiento contigo llena mi corazón.
No eres solo alguien que amo, eres mi lugar seguro, mi alegría diaria y mi sueño más bonito hecho realidad Felices 4 meses.`;

        let index = 0;
        const speed = 40;
        const typedText = document.getElementById("typedText");

        function typeEffect() {
            if (index < text.length) {
                typedText.innerHTML += text.charAt(index);
                index++;
                setTimeout(typeEffect, speed);
            }
        }

        typeEffect();

        /* =========================
           ACCIÓN DEL BOTÓN
        ========================== */
        function loveAction() {
            document.getElementById("surprise").style.display = "block";
            document.body.style.background = "linear-gradient(135deg, #ff9a9e, #fad0c4)";
            launchHearts();
        }

        /* =========================
           CORAZONES FLOTANDO
        ========================== */
        function launchHearts() {
            for (let i = 0; i < 30; i++) {
                setTimeout(createHeart, i * 200);
            }
        }

        function createHeart() {
            const heart = document.createElement("div");
            heart.classList.add("heart");
            heart.innerHTML = "❤️";
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.fontSize = (Math.random() * 20 + 20) + "px";
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 6000);
        }

        /* =========================
           CONTROL DE MÚSICA
        ========================== */
        const music = document.getElementById("music");
        let playing = false;

        function toggleMusic() {
            if (playing) {
                music.pause();
            } else {
                music.play();
            }
            playing = !playing;
        }
    </script>

</body>
</html>
