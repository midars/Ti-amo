<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Mi Amor: Un Jardín Mágico</title>
    <style>
        /* --- 1. VARIABLES DE COLOR Y FUENTES --- */
        :root {
            --primary-light: #FFC0CB; /* Rosa claro */
            --primary-dark: #FF69B4;  /* Rosa fuerte (rosa chicle) */
            --secondary-light: #ADD8E6; /* Azul cielo claro */
            --secondary-dark: #87CEEB;  /* Azul cielo */
            --accent-color: #DA70D6;    /* Orquídea (Morado suave) */
            --text-main: #4B0082;       /* Índigo */
            --text-highlight: #FFF0F5;  /* Flor de lavanda pálida */
            --sparkle-color: #FFFFE0;   /* Amarillo muy pálido (limón chiflado) */
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden; /* Muy importante para el efecto de partículas */
            font-family: 'Dancing Script', cursive; /* Fuente elegante y cursiva */
            background: linear-gradient(135deg, var(--primary-light) 0%, var(--secondary-light) 100%);
            background-size: 400% 400%; /* Para la animación del degradado */
            animation: gradientAnimation 15s ease infinite; /* Animación del fondo */
            color: var(--text-main);
            text-align: center;
        }

        /* --- Animación del degradado de fondo --- */
        @keyframes gradientAnimation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* --- 2. ESTILOS DEL CONTENEDOR DE MENSAJE PRINCIPAL --- */
        .main-message-container {
            position: relative;
            z-index: 100;
            padding: 40px 30px;
            background: rgba(255, 255, 255, 0.85); /* Fondo blanco semitransparente */
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(5px); /* Efecto de desenfoque detrás del contenedor */
            border: 2px solid var(--accent-color);
            max-width: 80%;
            transition: all 0.5s ease-in-out;
            cursor: pointer; /* Indica que es interactivo */
        }

        .main-message-container:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        h1 {
            font-size: 3.5em; /* Tamaño grande para el título */
            margin: 0 0 15px 0;
            color: var(--primary-dark);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            line-height: 1.2;
        }

        .reveal-message {
            font-size: 1.8em;
            color: var(--text-main);
            opacity: 0; /* Inicialmente oculto */
            max-height: 0; /* Para la animación de revelado */
            overflow: hidden;
            transition: opacity 1s ease-in-out, max-height 1s ease-in-out;
            margin-top: 20px;
        }

        .reveal-message.visible {
            opacity: 1;
            max-height: 200px; /* Suficiente para mostrar el texto */
        }

        /* --- 3. ESTILOS DE LAS PARTÍCULAS MÁGICAS --- */
        .sparkle {
            position: absolute;
            background-color: var(--sparkle-color);
            border-radius: 50%;
            pointer-events: none; /* Crucial para que no bloquee el clic */
            opacity: 0; /* Inicialmente invisible */
            animation: sparkleFade 3s ease-out forwards;
            filter: blur(1px); /* Efecto de brillo suave */
            box-shadow: 0 0 8px var(--sparkle-color);
        }

        @keyframes sparkleFade {
            0% { opacity: 0; transform: scale(0); }
            20% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(0.5) translateY(50px); }
        }

        /* --- 4. FUENTES DE GOOGLE (OPCIONAL, PERO RECOMENDADO) --- */
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&display=swap');
    </style>
</head>
<body>

<div class="main-message-container" id="message-box">
    <h1>¡Para Mi Amor Más Bonita! 💖</h1>
    <p class="reveal-message" id="hidden-message">
        "En cada estrella veo tu brillo, en cada flor siento tu esencia. Eres la melodía que alegra mi alma y la razón de mi sonrisa. Gracias por ser tú, mi vida entera."
    </p>
    <p class="reveal-message visible" style="font-size: 1.2em; color: var(--accent-color); opacity: 1; max-height: 100px;">
        ¡Haz clic aquí para un mensaje especial!
    </p>
</div>

<script>
    const messageBox = document.getElementById('message-box');
    const hiddenMessage = document.getElementById('hidden-message');
    const body = document.body;
    let messageRevealed = false;

    // --- Revelar mensaje al hacer clic ---
    messageBox.addEventListener('click', () => {
        if (!messageRevealed) {
            hiddenMessage.classList.add('visible');
            messageBox.style.paddingBottom = '30px'; // Ajustar padding para el mensaje
            messageRevealed = true;
            // Opcional: Cambiar el texto de "Haz clic" una vez revelado
            const clickPrompt = messageBox.querySelector('p:last-child');
            if (clickPrompt) clickPrompt.textContent = "¡Te amo más de lo que las palabras pueden expresar!";
        }
    });

    // --- Generación de partículas mágicas al mover el ratón ---
    body.addEventListener('mousemove', (e) => {
        for (let i = 0; i < 2; i++) { // Genera 2 partículas por movimiento para un efecto más denso
            const sparkle = document.createElement('div');
            sparkle.classList.add('sparkle');
            const size = Math.random() * 8 + 4; // Tamaño entre 4 y 12px
            sparkle.style.width = `${size}px`;
            sparkle.style.height = `${size}px`;
            sparkle.style.left = `${e.clientX + (Math.random() * 20 - 10)}px`; // Posición aleatoria cerca del cursor
            sparkle.style.top = `${e.clientY + (Math.random() * 20 - 10)}px`;
            sparkle.style.animationDuration = `${Math.random() * 2 + 2}s`; // Duración de 2 a 4 segundos
            sparkle.style.animationDelay = `${Math.random() * 0.1}s`; // Pequeño retraso para variación

            body.appendChild(sparkle);

            // Remover la chispa después de su animación
            sparkle.addEventListener('animationend', () => {
                sparkle.remove();
            });
        }
    });

    // Asegurarse de que la fuente se cargue antes de mostrar el contenido (mejora la experiencia)
    document.addEventListener('DOMContentLoaded', () => {
        const fontLink = document.createElement('link');
        fontLink.href = 'https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&display=swap';
        fontLink.rel = 'stylesheet';
        document.head.appendChild(fontLink);
    });
</script>
</body>
</html>
