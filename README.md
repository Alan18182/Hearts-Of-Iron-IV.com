<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Cuartel de Mando</title>
    <style>
        /* --- ESTÉTICA VISUAL (FIJA) --- */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }

        body {
            background: url('fondo.png') no-repeat center center fixed;
            background-size: cover;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .capa-oscura {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.82);
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
            to { transform: translate(-100px,-100px); }
        }

        .wrapper {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 95%;
            max-width: 900px;
        }

        h1 {
            font-size: clamp(30px, 8vw, 60px);
            text-shadow: 0 0 25px #00aaff;
            margin-bottom: 20px;
        }

        .btn-entrar {
            padding: 20px 60px;
            background: #00aaff;
            border: none;
            color: white;
            font-size: 22px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 5px;
            box-shadow: 0 0 20px rgba(0, 170, 255, 0.6);
            transition: 0.3s;
            position: relative;
            z-index: 100;
        }

        .btn-entrar:hover { transform: scale(1.05); box-shadow: 0 0 40px #00aaff; }

        /* --- NAVEGACIÓN --- */
        #inicio { display: block; }
        #contenido { display: none; flex-direction: column; align-items: center; }

        .grid-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 30px;
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

        #detalle {
            margin-top: 25px;
            padding: 30px;
            background: rgba(0, 0, 0, 0.95);
            border: 1px solid #00aaff;
            display: none;
            text-align: left;
            line-height: 1.7;
            max-height: 550px;
            overflow-y: auto;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 15px; border-bottom: 1px solid #333; padding-bottom: 5px; }
        #detalle strong { color: #00ccff; }
        #detalle ul { margin: 15px 0 15px 25px; }
        #detalle li { margin-bottom: 8px; }

        .btn-volver {
            background: none;
            border: 1px solid white;
            color: white;
            padding: 10px 20px;
            cursor: pointer;
            margin-bottom: 20px;
            align-self: flex-start;
        }
    </style>
</head>
<body>

    <div class="capa-oscura"></div>
    <div class="humo"></div>

    <div class="wrapper">
        <div id="inicio">
            <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
            <p style="margin-bottom: 40px; opacity: 0.8;">MANUAL ESTRATÉGICO DE OPERACIONES</p>
            <button class="btn-entrar" onclick="accesoSeguro()">ENTRAR</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="regresar()">⬅ VOLVER</button>
            <div class="grid-menu">
                <div class="tarjeta" onclick="cargarSeccion('marina')">⚓ MARINA</div>
                <div class="tarjeta" onclick="cargarSeccion('tierra')">🪖 TERRESTRE</div>
                <div class="tarjeta" onclick="cargarSeccion('aire')">✈️ AÉREO</div>
                <div class="tarjeta" onclick="cargarSeccion('logistica')">📦 LOGÍSTICA</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        function accesoSeguro() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
            document.body.style.overflow = "auto";
        }

        function regresar() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
            document.body.style.overflow = "hidden";
        }

        function cargarSeccion(s) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const info = {
                marina: `
                    <h3>⚓ ESTRATEGIA NAVAL DEFINITIVA</h3>
                    <p><strong>Composición de Flota:</strong> La clave es el posicionamiento y el ratio de pantallas (Destructores y Cruceros Ligeros). Se recomienda un ratio de 4:1 para proteger a los Buques Capitales.</p>
                    <ul>
                        <li><strong>Misiones:</strong> Patrulla para detectar, Fuerza de Choque para destruir.</li>
                        <li><strong>Submarinos:</strong> Úsalos en grupos pequeños para guerra de convoyes en océanos profundos.</li>
                    </ul>`,
                tierra: `
                    <h3>🪖 EJÉRCITO Y COMBATE TERRESTRE</h3>
                    <p><strong>Mecánicas Cruciales:</strong> El éxito depende del Ataque Ligero (contra infantería), Ataque Pesado (contra tanques) y la Organización (capacidad de mantenerse en lucha).</p>
                    <ul>
                        <li><strong>Ancho de Combate:</strong> Atacar desde múltiples flancos añade +35 de ancho por cada lado extra, permitiendo que entren más reservas al combate.</li>
                        <li><strong>Terrenos:</strong> Las Llanuras son ideales para tanques. Montañas y Ciudades dan bonos defensivos masivos. Evita Selvas o Pantanos.</li>
                        <li><strong>Doctrinas Terrestres:</strong> 
                            <ul>
                                <li><em>Fuego Superior:</em> Máximo daño de artillería, ideal contra la IA.</li>
                                <li><em>Guerra Móvil:</em> Enfoque en velocidad y tanques para embolsamientos rápidos.</li>
                                <li><em>Asalto en Masa:</em> Reduce el ancho de la infantería para saturar el frente.</li>
                            </ul>
                        </li>
                    </ul>`,
                aire: `<h3>✈️ SUPERIORIDAD AÉREA</h3><p>Sin superioridad aérea, tus tropas sufren una penalización de defensa y movimiento. El apoyo aéreo cercano (CAS) es el mayor multiplicador de daño en tierra.</p>`,
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Red de Suministro:</strong> El suministro fluye desde la Capital hacia los Hubs (centros de suministros) por vías férreas o hacia puertos por convoys.</p>
                    <ul>
                        <li><strong>Motorización de Hubs:</strong> Clickea en un Hub para cambiar de caballos a camiones (Nivel 1 o 2). Esto expande el rango de entrega de suministros.</li>
                        <li><strong>Ferrocarriles:</strong> Mejora el nivel de las vías para eliminar cuellos de botella. La capacidad total depende del eslabón más débil de la ruta.</li>
                        <li><strong>Tipos de Trenes:</strong> 
                            <ul>
                                <li><em>Trenes de Austeridad:</em> Baratos y rápidos de producir.</li>
                                <li><em>Trenes Blindados:</em> Fundamentales para resistir bombardeos logísticos enemigos.</li>
                            </ul>
                        </li>
                        <li><strong>Puentes Aéreos:</strong> Aviones de transporte para suministrar unidades aisladas o cercadas.</li>
                        <li><strong>Desempeño Logístico:</strong> Debe estar siempre arriba del 70% para evitar atrición y pérdida de organización.</li>
                    </ul>`
            };

            d.innerHTML = info[s];
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
