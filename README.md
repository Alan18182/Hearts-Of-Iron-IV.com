<!DOCTYPE html>
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
            overflow: hidden; /* Evita scrolls raros en el inicio */
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* CAPA OSCURA DE PROFUNDIDAD */
        .capa-oscura {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            z-index: 1;
        }

        /* EFECTO DE HUMO ANIMADO */
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

        /* CONTENEDOR DE INTERFAZ */
        .interface {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 100%;
            max-width: 900px;
        }

        /* TITULO CON BRILLO AZUL */
        h1 {
            font-size: 55px;
            margin-bottom: 10px;
            text-shadow: 0 0 25px rgba(0,150,255,0.9);
            letter-spacing: 3px;
        }

        p.slogan {
            font-size: 20px;
            margin-bottom: 40px;
            opacity: 0.8;
        }

        /* BOTON PRINCIPAL */
        .btn-entrar {
            padding: 15px 50px;
            border: none;
            border-radius: 10px;
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
            transform: scale(1.1);
            box-shadow: 0 0 30px #00aaff;
        }

        /* SECCIONES Y GRILLA */
        #contenido {
            display: none;
            flex-direction: column;
            align-items: center;
            animation: aparecer 0.8s ease;
        }

        .seccion-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 20px;
        }

        .seccion {
            padding: 20px;
            background: rgba(0,0,0,0.8);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            transition: 0.3s;
            text-align: left;
            font-size: 18px;
        }

        .seccion:hover {
            transform: translateX(10px);
            background: rgba(0,170,255,0.2);
            box-shadow: 0 0 15px #00aaff;
        }

        /* DETALLE */
        #detalle {
            margin-top: 25px;
            padding: 25px;
            background: rgba(0,0,0,0.9);
            border-radius: 10px;
            border: 1px solid #00aaff;
            text-align: left;
            animation: aparecer 0.5s ease;
        }

        @keyframes aparecer {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .btn-volver {
            background: transparent;
            border: 1px solid white;
            color: white;
            padding: 8px 15px;
            cursor: pointer;
            margin-bottom: 20px;
            transition: 0.3s;
        }

        .btn-volver:hover { background: white; color: black; }

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
            <button class="btn-volver" onclick="volver()">⬅ Volver</button>
            
            <div class="seccion-container">
                <div class="seccion" onclick="abrirSeccion('marina')">⚓ Marina</div>
                <div class="seccion" onclick="abrirSeccion('tierra')">🪖 Terrestre</div>
                <div class="seccion" onclick="abrirSeccion('aire')">✈ Aéreo</div>
                <div class="seccion" onclick="abrirSeccion('logistica')">📦 Logística</div>
            </div>

            <div id="detalle" style="display:none;"></div>
        </div>

    </div>

    <script>
        function entrar() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
            document.body.style.overflow = "auto"; // Permite scroll si el detalle es largo
        }

        function volver() {
            document.getElementById("contenido").style.display = "none";
            document.getElementById("inicio").style.display = "block";
            document.getElementById("detalle").style.display = "none";
            document.body.style.overflow = "hidden";
        }

        function abrirSeccion(seccion) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const textos = {
                marina: "<h3>⚓ Marina</h3><p>Controlá las rutas de suministro y protegé tus costas. Usa submarinos para asfixiar al enemigo.</p>",
                tierra: "<h3>🪖 Terrestre</h3><p>Diseñá divisiones equilibradas y usá el terreno a tu favor. ¡Cuidado con el invierno ruso!</p>",
                aire: "<h3>✈ Aéreo</h3><p>La superioridad aérea gana guerras. Apoyá a tus tropas con apoyo aéreo cercano.</p>",
                logistica: "<h3>📦 Logística</h3><p>Sin trenes ni suministros, tus tanques no se moverán. Vigilá siempre tus líneas de abastecimiento.</p>"
            };

            d.innerHTML = textos[seccion];
        }
    </script>
</body>
</html>
