<A fines de entretenimiento y conocimientos.>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV</title>
    <style>
        /* RESET */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }

        body {
            background: url('fondo.png') no-repeat center center fixed;
            background-size: cover;
            color: white;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* CAPA OSCURA */
        .capa-oscura {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            z-index: 1;
        }

        /* EFECTO HUMO */
        .humo {
            position: fixed;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.05) 10%, transparent 60%);
            animation: humo-mov 20s linear infinite;
            z-index: 2;
            pointer-events: none;
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-200px,-200px); }
        }

        /* INTERFAZ */
        .interface {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 90%;
            max-width: 800px;
        }

        h1 {
            font-size: clamp(30px, 8vw, 55px);
            margin-bottom: 10px;
            text-shadow: 0 0 25px rgba(0,150,255,0.9);
            color: white;
        }

        .slogan {
            font-size: 1.2rem;
            margin-bottom: 40px;
            opacity: 0.9;
        }

        /* BOTONES */
        .btn-entrar {
            padding: 15px 50px;
            border: none;
            border-radius: 8px;
            background: #00aaff;
            color: white;
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 15px rgba(0,170,255,0.5);
        }

        .btn-entrar:hover {
            background: #0077aa;
            transform: scale(1.05);
            box-shadow: 0 0 30px #00aaff;
        }

        /* CONTENIDO SECCIONES */
        #contenido {
            display: none;
            flex-direction: column;
            align-items: center;
            animation: aparecer 0.5s ease;
        }

        .grid-secciones {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 20px;
        }

        .seccion {
            padding: 15px;
            background: rgba(0,0,0,0.8);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            transition: 0.3s;
            text-align: left;
        }

        .seccion:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(5px);
        }

        #detalle {
            margin-top: 20px;
            padding: 20px;
            background: rgba(0,0,0,0.9);
            border: 1px solid #00aaff;
            text-align: left;
        }

        @keyframes aparecer {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .volver {
            background: transparent;
            border: 1px solid white;
            color: white;
            padding: 5px 15px;
            margin-bottom: 20px;
            cursor: pointer;
            align-self: flex-start;
        }
    </style>
</head>
<body>

    <div class="capa-oscura"></div>
    <div class="humo"></div>

    <div class="interface">
        
        <div id="inicio">
            <h1>⚔️ Hearts Of Iron IV ⚔️</h1>
            <p class="slogan">Dominá la guerra, controlá el mundo.</p>
            <button class="btn-entrar" onclick="entrar()">Entrar</button>
        </div>

        <div id="contenido">
            <button class="volver" onclick="volver()">⬅ Volver</button>
            <div class="grid-secciones">
                <div class="seccion" onclick="abrir('marina')">⚓ Marina</div>
                <div class="seccion" onclick="abrir('tierra')">🪖 Terrestre</div>
                <div class="seccion" onclick="abrir('aire')">✈ Aéreo</div>
                <div class="seccion" onclick="abrir('logistica')">📦 Logística</div>
            </div>
            <div id="detalle" style="display:none;"></div>
        </div>

    </div>

    <script>
        function entrar() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
        }
        function volver() {
            document.getElementById("contenido").style.display = "none";
            document.getElementById("inicio").style.display = "block";
        }
        function abrir(tipo) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            const info = {
                marina: "<h3>⚓ Marina</h3><p>Usa submarinos para atacar convoyes enemigos.</p>",
                tierra: "<h3>🪖 Terrestre</h3><p>Mantén tu ancho de combate en 20 o 40.</p>",
                aire: "<h3>✈ Aéreo</h3><p>La superioridad aérea es clave para avanzar.</p>",
                logistica: "<h3>📦 Logística</h3><p>Sin suministros, tus tropas no podrán pelear.</p>"
            };
            d.innerHTML = info[tipo];
        }
    </script>
</body>
</html>
