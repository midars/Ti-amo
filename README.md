<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Una Pregunta Muy Importante! ❤️</title>
    <style>
        /* Estilos CSS */
        @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@400;700&display=swap');

        :root {
            --color-fondo: #fce4ec; /* Rosa muy claro */
            --color-principal: #e91e63; /* Rosa fuerte/rojo */
            --color-secundario: #880e4f; /* Rosa oscuro */
            --color-texto: #333333;
            --color-hover: #ff4081; /* Rosa claro para hover */
        }

        body {
            background-color: var(--color-fondo);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            font-family: 'Montserrat', sans-serif;
            text-align: center;
            overflow: hidden; /* Oculta las partículas fuera de la vista */
        }

        .container {
            background-color: #ffffff;
            padding: 40px 60px;
            border-radius: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
            z-index: 10; /* Asegura que el contenido esté sobre las partículas */
            animation: fadeIn 1.5s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        .title {
            font-family: 'Great Vibes', cursive;
            font-size: 4.5em; /* Más grande */
            color: var(--color-principal);
            margin-bottom: 5px;
            animation: bounceIn 1.5s ease-out;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .question {
            font-family: 'Montserrat', sans-serif;
            font-size: 2.2em;
            color: var(--color-secundario);
            margin-top: 5px;
            margin-bottom: 30px;
            font-weight: 700;
            animation: slideInUp 2s ease-out;
        }

        @keyframes bounceIn {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.1); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes slideInUp {
            0% { transform: translateY(50px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        .buttons-group {
            display: flex;
            justify-content: center;
            gap: 30px; /* Espacio entre los botones */
        }

        .button {
            padding: 15px 35px;
            font-size: 1.5em;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 700;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
        }

        /* Botón "¡SÍ!" */
        #yes-button {
            background-color: var(--color-principal);
            color: white;
        }

        #yes-button:hover {
            background-color: var(--color-hover);
            transform: scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        /* Botón "Tal vez..." */
        #maybe-button {
            background-color: #cccccc;
            color: var(--color-texto);
            position: absolute; /* Para que se mueva */
            transform: none; /* Resetear cualquier transformación inicial */
        }

        #maybe-button:hover {
            background-color: #bbbbbb;
        }

        /* ----- Efecto de Partículas (Corazones) ----- */
        .heart {
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: var(--color-principal);
            transform: rotate(-45deg);
            pointer-events: none; /* Para que no interfieran con clics */
            animation: floatUp 6s infinite ease-out;
            opacity: 0;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: var(--color-principal);
            border-radius: 50%;
        }

        .heart::before {
            top: -7.5px;
            left: 0;
        }

        .heart::after {
            left: 7.5px;
            top: 0;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100px) scale(1); opacity: 0; }
        }
    </style>
</head>
<body>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const body = document.body;
            const colors = ['#e91e63', '#ff4081', '#fce4ec'];

            function createHeart() {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                
                // Posición aleatoria en el eje X
                heart.style.left = Math.random() * 100 + 'vw';
                
                // Tamaño y duración aleatorios
                const size = Math.random() * 10 + 10;
                heart.style.width = size + 'px';
                heart.style.height = size + 'px';
                
                const duration = Math.random() * 5 + 5;
                heart.style.animationDuration = duration + 's';
                
                // Retraso para que aparezcan escalonadamente
                heart.style.animationDelay = Math.random() * 5 + 's';
                
                // Color aleatorio
                const color = colors[Math.floor(Math.random() * colors.length)];
                heart.style.backgroundColor = color;
                heart.style.setProperty('--color-principal', color);

                // Agregar los pseudo-elementos (la forma de corazón)
                const before = document.createElement('style');
                before.innerHTML = `.heart::before { background-color: ${color}; }`;
                document.head.appendChild(before);

                const after = document.createElement('style');
                after.innerHTML = `.heart::after { background-color: ${color}; }`;
                document.head.appendChild(after);
                
                body.appendChild(heart);

                // Eliminar el corazón después de su animación
                setTimeout(() => {
                    heart.remove();
                }, duration * 1000);
            }

            // Crear una cantidad de corazones (ej. 30)
            for (let i = 0; i < 30; i++) {
                createHeart();
            }
            
            // Seguir creando corazones para un ciclo infinito
            setInterval(createHeart, 300); // Crea un nuevo corazón cada 300ms
        });
    </script>
    <div class="container">
        <div class="title">
            ¡Te Amo Mucho!
        </div>
        <div class="question">
            ¿Quieres ser mi novia?
        </div>
        
        <div class="buttons-group">
            <button id="yes-button" class="button" onclick="alert('¡Sabía que dirías que SÍ! Te adoro. Ahora somos novios ❤️')">
                ¡SÍ!
            </button>
            <button id="maybe-button" class="button">
                Tal vez...
            </button>
        </div>
    </div>

    <script>
        const maybeButton = document.getElementById('maybe-button');
        const container = document.querySelector('.container');

        maybeButton.addEventListener('mouseover', () => {
            // Obtener el tamaño del contenedor y del botón
            const containerRect = container.getBoundingClientRect();
            const buttonRect = maybeButton.getBoundingClientRect();

            // Calcular límites para que el botón no se salga del contenedor
            // El desplazamiento debe ser dentro del contenedor (ancho - ancho_boton)
            const maxX = containerRect.width - buttonRect.width - 60; // -60 por el padding del container
            const maxY = containerRect.height - buttonRect.height - 100;

            // Generar nuevas posiciones aleatorias dentro del rango
            // Posición X: de 0 a maxX
            let newX = Math.random() * maxX;
            // Posición Y: de 0 a maxY (pero no muy cerca del título)
            let newY = Math.random() * maxY;

            // Ajustar el origen de la posición para que el botón se mueva solo un poco desde el centro
            const centerOffsetX = (containerRect.width / 2) - (buttonRect.width / 2);
            const centerOffsetY = (containerRect.height / 2) - (buttonRect.height / 2);

            // Queremos que el botón se mueva respecto a su posición *original* en la caja.
            // Para simplificar, lo movemos con 'transform: translate' a una nueva posición dentro del contenedor.
            
            // Si el botón está en la posición 'static' del flexbox, movemos el botón
            // una cantidad aleatoria (ej. ±150px) pero siempre cerca del botón de SÍ
            
            // Para mantener el botón "Tal vez" cerca del botón "¡SÍ!" y en la fila:
            // Vamos a hacer que se mueva en un rango pequeño.
            
            // Rango de movimiento (ej. 150px)
            const moveRange = 100;
            
            // Generar un pequeño movimiento aleatorio (entre -moveRange/2 y +moveRange/2)
            const randomX = Math.floor(Math.random() * moveRange) - (moveRange / 2);
            const randomY = Math.floor(Math.random() * moveRange) - (moveRange / 2);

            // Aplicar la transformación de movimiento
            maybeButton.style.position = 'relative'; // Necesario para que el translate funcione bien
            maybeButton.style.transform = `translate(${randomX}px, ${randomY}px)`;
            maybeButton.style.transition = 'transform 0.2s ease-out'; // Para que se mueva rápido
            
            // Pequeño truco para que si la persona intenta hacer clic, sea difícil:
            maybeButton.onclick = () => {
                alert('¡Ups! Tienes que intentarlo otra vez. ¡El botón de SÍ es el importante! 😉');
            };
        });

        // Asegúrate de que el botón regrese a su posición si no hay mouse encima
        maybeButton.addEventListener('mouseleave', () => {
            maybeButton.style.transform = 'translate(0, 0)';
            maybeButton.style.transition = 'transform 0.4s ease-out'; // Transición más lenta para volver
            maybeButton.onclick = null; // Quitar el truco de no clic
        });
    </script>
</body>
</html>
