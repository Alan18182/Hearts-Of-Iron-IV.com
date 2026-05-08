<A fines de entretenimiento y conocimientos.>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Bunker </title>
    <style>
        /* --- ESTILOS VISUALES --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: url('fondo.png') no-repeat center center fixed;
            background-size: cover;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
        }

        .capa-oscura {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.78);
            z-index: 1;
        }

        .humo {
            position: fixed;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.03) 10%, transparent 60%);
            animation: humo-mov 25s linear infinite;
            z-index: 2;
            pointer-events: none;
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-150px,-150px); }
        }

        .wrapper {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 90%;
            max-width: 850px;
            padding: 20px;
        }

        h1 {
            font-size: clamp(35px, 8vw, 60px);
            text-shadow: 0 0 25px #00aaff;
            letter-spacing: 2px;
            margin-bottom: 10px;
        }

        .slogan {
            font-size: 1.2rem;
            margin-bottom: 40px;
            opacity: 0.8;
            color: #ddd;
        }

        .btn-entrar {
            padding: 18px 55px;
            background: #00aaff;
            border: none;
            color: white;
            font-size: 20px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.3s;
            box-shadow: 0 0 20px rgba(0, 170, 255, 0.5);
        }

        .btn-entrar:hover {
            transform: scale(1.05);
            background: #0088cc;
            box-shadow: 0 0 35px #00aaff;
        }

        #contenido {
            display: none;
            flex-direction: column;
            align-items: center;
            animation: fadeIn 0.6s ease;
        }

        .grid-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 20px;
        }

        .tarjeta {
            padding: 20px;
            background: rgba(15, 15, 15, 0.9);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            transition: 0.3s;
            text-align: left;
            font-weight: bold;
        }

        .tarjeta:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
        }

        #detalle {
            margin-top: 25px;
            padding: 25px;
            background: rgba(0, 0, 0, 0.9);
            border: 1px solid #00aaff;
            border-radius: 5px;
            text-align: left;
            display: none;
            line-height: 1.7;
            animation: fadeIn 0.4s ease;
            max-height: 500px;
            overflow-y: auto;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 15px; font-size: 1.6rem; }
        #detalle ul { margin-left: 20px; margin-top: 10px; }
        #detalle li { margin-bottom: 10px; color: #eee; }

        .btn-volver {
            background: transparent;
            border: 1px solid #ffffff;
            color: white;
            padding: 8px 18px;
            cursor: pointer;
            margin-bottom: 25px;
            align-self: flex-start;
            transition: 0.3s;
        }

        .btn-volver:hover { background: white; color: black; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="capa-oscura"></div>
    <div class="humo"></div>

    <div class="wrapper">
        <div id="inicio">
            <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
            <p class="slogan">Guía de Mando y Estrategia</p>
            <button class="btn-entrar" onclick="entrar()">Entrar</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="volver()">⬅ Volver</button>
            <div class="grid-menu">
                <div class="tarjeta" onclick="abrir('marina')">⚓ Marina</div>
                <div class="tarjeta" onclick="abrir('tierra')">🪖 Terrestre</div>
                <div class="tarjeta" onclick="abrir('aire')">✈️ Aéreo</div>
                <div class="tarjeta" onclick="abrir('logistica')">📦 Logística</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        function entrar() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
        }

        function volver() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
        }

        function abrir(seccion) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const info = {
                marina: `
                    <h3>⚓ ESTRATEGIA NAVAL DEFINITIVA</h3>
                    <p><strong>Estructura de Combate:</strong> Divide tu flota en 4 zonas clave. Las pantallas (Destructores y Cruceros Ligeros) deben proteger a tus Buques Capitales en un ratio de 4:1 para interceptar torpedos.</p>
                    <ul>
                        <li><strong>Fuerza de Choque:</strong> Flota principal para el combate directo. Mantenla en puerto para ahorrar combustible.</li>
                        <li><strong>Patrulla:</strong> Barcos rápidos (Cruceros Ligeros) para localizar al enemigo sin entrar en batalla.</li>
                        <li><strong>Submarinos:</strong> Enfócalos en el ataque de convoyes en océanos profundos.</li>
                    </ul>
                `,
                tierra: `
                    <h3>🪖 MANUAL DEL EJÉRCITO TERRESTRE</h3>
                    <p><strong>Estadísticas de Combate:</strong>Las batallas se deciden por Ataque Ligero, Ataque Pesado y Organización. Las divisiones pierden cuando su Organización (barra verde) o Fuerza (barra naranja) se agotan.</p>
                    <ul>
                        <li><strong>Ancho de Combate:</strong> Ataca desde múltiples flancos para ampliar el ancho de combate y permitir que más divisiones luchen a la vez.</li>
                        <li><strong>Doctrinas Terrestres:</strong> 
                            <ul>
                                <li><em>Fuego Superior:</em> Máximo ataque ligero con artillería.</li>
                                <li><em>Guerra Móvil:</em> Enfoque en velocidad y tanques.</li>
                                <li><em>Asalto en Masa:</em> Ideal para países con mucho manpower (ej: URSS o China).</li>
                            </ul>
                        </li>
                    </ul>
                `,
                aire: "<h3>✈️ Superioridad Aérea</h3><p>La superioridad aérea protege a tus tropas de penalizadores y permite el Apoyo Aéreo Cercano (CAS), que es el mayor destructor de divisiones enemigas en combate.</p>",
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Red de Suministros:</strong>Todo nace en la Capital y se distribuye a través de Centros de Suministros (puntos amarillos) y Bases Navales (anclas) mediante Ferrocarriles o Convoys.</p>
                    <ul>
                        <li><strong>Motorización:</strong> Clica en un Centro de Suministros para cambiar de transporte con caballos a camiones. Esto aumenta drásticamente el alcance del suministro en el frente.</li>
                        <li><strong>Vías Férreas:</strong> Sube el nivel de los ferrocarriles para evitar "cuellos de botella" y permitir que más equipo llegue desde la capital a zonas lejanas.</li>
                        <li><strong>Tipos de Trenes:</strong> 
                            <ul>
                                <li><em>Civil:</em> El estándar básico.</li>
                                <li><em>De Austeridad:</em> Barato y rápido de producir.</li>
                                <li><em>Blindado:</em> Resistente a los bombardeos logísticos del enemigo.</li>
                            </ul>
                        </li>
                        <li><strong>Puentes Aéreos:</strong> Usa aviones de transporte para enviar
