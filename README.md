<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Guía</title>
    <style>
        /* RESET TOTAL */
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
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
        }

        /* CAPA OSCURA UNIFICADA */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1;
        }

        .main-container {
            position: relative;
            z-index: 10;
            width: 90%;
            max-width: 800px;
            text-align: center;
        }

        /* TITULOS */
        .game-title {
            font-size: clamp(30px, 5vw, 55px);
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #00aaff;
            text-shadow: 0 0 20px rgba(0, 170, 255, 0.6);
            margin-bottom: 5px;
        }

        .divider {
            width: 60%;
            height: 2px;
            background: linear-gradient(90deg, transparent, #00aaff, transparent);
            margin: 15px auto;
        }

        .subtitle {
            font-size: 1.2rem;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        /* BOTON ESTILO HOI4 */
        .btn-action {
            padding: 15px 40px;
            background: rgba(0, 170, 255, 0.1);
            border: 2px solid #00aaff;
            color: white;
            font-size: 18px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            transition: 0.3s;
            border-radius: 4px;
        }

        .btn-action:hover {
            background: #00aaff;
            box-shadow: 0 0 25px #00aaff;
            transform: scale(1.05);
        }

        /* GRILLA DE SECCIONES */
        .grid-secciones {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .card {
            background: rgba(0, 0, 0, 0.7);
            border-left: 4px solid #00aaff;
            padding: 20px;
            text-align: left;
            cursor: pointer;
            transition: 0.3s;
        }

        .card:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
        }

        #detalle {
            margin-top: 20px;
            padding: 20px;
            background: rgba(0, 0, 0, 0.9);
            border: 1px solid #00aaff;
            text-align: left;
            line-height: 1.6;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="overlay"></div>

    <div class="main-container">
        <div id="inicio">
            <h1 class="game-title">⚔️ HEARTS OF IRON IV ⚔️</h1>
            <div class="divider"></div>
            <p class="subtitle">Manual de campo para nuevos comandantes.</p>
            <button class="btn-action" onclick="entrar()">INICIAR OPERACIÓN</button>
        </div>

        <div id="contenido" style="display:none;">
            <button class="btn-action" style="font-size: 14px; padding: 10px 20px;" onclick="volver()">⬅ VOLVER</button>
            
            <div class="grid-secciones">
                <div class="card" onclick="mostrar('marina')">⚓ MARINA</div>
                <div class="card" onclick="mostrar('tierra')">🪖 TERRESTRE</div>
                <div class="card" onclick="mostrar('aire')">✈️ AÉREO</div>
                <div class="card" onclick="mostrar('logistica')">📦 LOGÍSTICA</div>
            </div>

            <div id="detalle" style="display:none;"></div>
        </div>
    </div>

    <script>
        function entrar() {
            document.getElementById('inicio').style.display = 'none';
            document.getElementById('contenido').style.display = 'block';
        }

        function volver() {
            document.getElementById('contenido').style.display = 'none';
            document.getElementById('inicio').style.display = 'block';
            document.getElementById('detalle').style.display = 'none';
        }

        function mostrar(seccion) {
            const det = document.getElementById('detalle');
            det.style.display = 'block';
            
            const info = {
                marina: "<h3>⚓ ESTRATEGIA NAVAL</h3><p>Para países pequeños, enfócate en submarinos (U-Boats) para hundir suministros. Para imperios, construye portaaviones.</p>",
                tierra: "<h3>🪖 GUERRA TERRESTRE</h3><p>La clave es el ancho de combate (20 o 40). Usa compañías de ingenieros para defender mejor los ríos.</p>",
                aire: "<h3>✈️ SUPERIORIDAD AÉREA</h3><p>Sin cazas, tus tropas sufren un -50% de movimiento. ¡Gana el cielo primero!</p>",
                logistica: "<h3>📦 SUMINISTROS</h3><p>Construye trenes y camiones. Si tus tropas no tienen comida ni balas, perderás aunque tengas los mejores tanques.</p>"
            };
            
            det.innerHTML = info[seccion];
        }
    </script>
</body>
</html>
