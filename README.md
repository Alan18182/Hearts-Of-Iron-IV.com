<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Cuartel de Mando</title>
    <style>
        /* --- ESTÉTICA VISUAL (FIJA E INTACTA) --- */
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
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
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
            font-size: 0.9rem;
        }

        .tarjeta:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
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
            animation: fadeIn 0.4s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        #detalle h3 { color: #00aaff; margin-bottom: 15px; border-bottom: 1px solid #333; padding-bottom: 5px; }
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
                <div class="tarjeta" onclick="cargarSeccion('investigaciones')">🔬 INVESTIGACIONES</div>
                <div class="tarjeta" onclick="cargarSeccion('inteligencia')">🕵️ INTELIGENCIA</div>
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
                    <p><strong>Composición y Proporción:</strong> La supervivencia de tu flota depende de las pantallas (Destructores y Cruceros Ligeros). Debes mantener un ratio mínimo de 4 pantallas por cada Buque Capital para bloquear torpedos enemigos.</p>
                    <ul>
                        <li><strong>Fuerza de Choque (Strike Force):</strong> Tu flota principal en puerto para ahorrar combustible.</li>
                        <li><strong>Patrulla:</strong> Cruceros Ligeros rápidos con radares para detección.</li>
                        <li><strong>Guerra de Convoyes:</strong> Submarinos en grupos de 8 a 12 en Océano Profundo.</li>
                    </ul>`,
                tierra: `
                    <h3>🪖 EJÉRCITO Y COMBATE TERRESTRE</h3>
                    <p><strong>Mecánicas de Batalla:</strong> Las divisiones luchan según su Ataque Ligero, Pesado y Defensa. Se pierde cuando la Organización o Fuerza llega a cero.</p>
                    <ul>
                        <li><strong>Ancho de Combate:</strong> Atacar desde múltiples direcciones suma +35 de ancho adicional por cada flanco extra.</li>
                        <li><strong>Terrenos:</strong> Llanura es el mejor para avanzar; Selva y Pantano penalizan severamente el movimiento y ataque.</li>
                        <li><strong>Doctrinas:</strong> Guerra Móvil (Blindados), Fuego Superior (Artillería), Gran Plan (Planificación) o Asalto en Masa (Infantería).</li>
                    </ul>`,
                aire: `
                    <h3>✈️ PODER AÉREO Y SUPERIORIDAD</h3>
                    <p><strong>La Regla de Oro:</strong> Quien controla el cielo, controla el frente. La Superioridad Aérea otorga un bono directo de ataque a tus tropas y reduce la defensa y movimiento del enemigo.</p>
                    <ul>
                        <li><strong>Misión de Superioridad:</strong> Asigna Cazadores (Fighters) para derribar aviones enemigos. Prioriza el diseño con alta Agilidad y Ataque Aéreo.</li>
                        <li><strong>Apoyo Aéreo Cercano (CAS):</strong> Los aviones de ataque a tierra infligen daño directo a la organización y fuerza enemiga durante los combates. Son el mayor multiplicador de bajas en el juego.</li>
                        <li><strong>Bombardeo Logístico:</strong> Una misión clave para destruir trenes y camiones enemigos, dejando sus divisiones sin suministros en medio de la batalla.</li>
                        <li><strong>Eficiencia de Misión:</strong> Depende de la cobertura del radar y del alcance del avión. Operar desde bases aéreas saturadas reduce drásticamente el rendimiento.</li>
                        <li><strong>Intercepción:</strong> Úsala para defender tus fábricas de los bombardeos estratégicos enemigos sin desperdiciar combustible patrullando constantemente.</li>
                    </ul>`,
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Sistema de Red:</strong> El suministro fluye desde la Capital hacia los Hubs por vías férreas.</p>
                    <ul>
                        <li><strong>Motorización de Hubs:</strong> Configura centros para usar camiones para expandir el alcance del suministro hacia el frente.</li>
                        <li><strong>Ferrocarriles:</strong> Mejora el nivel de las vías para evitar cuellos de botella en el flujo.</li>
                        <li><strong>Trenes:</strong> Produce Trenes Blindados para resistir ataques aéreos enemigos.</li>
                    </ul>`,
                investigaciones: `
                    <h3>🔬 PRIORIDADES DE INVESTIGACIÓN</h3>
                    <p><strong>Gestión del Tiempo:</strong> Prioriza tecnologías de Industria y Electrónica para acelerar el ritmo de toda la partida.</p>
                    <ul>
                        <li><strong>Máquinas Herramientas:</strong> Aumentan tu capacidad de producción en fábricas civiles y militares.</li>
                        <li><strong>Computación:</strong> Reduce el tiempo total de cada investigación futura.</li>
                        <li><strong>Bonos:</strong> Aprovecha los enfoques nacionales para obtener bonos de investigación del 100%.</li>
                    </ul>`,
                inteligencia: `
                    <h3>🕵️ SERVICIOS DE INTELIGENCIA</h3>
                    <p><strong>La Agencia:</strong> Permite conocer la ubicación de las tropas enemigas y sus diseños tecnológicos.</p>
                    <ul>
                        <li><strong>Redes:</strong> Mantén espías activos para reducir el bono de planificación enemigo.</li>
                        <li><strong>Criptografía:</strong> Desencriptar claves otorga una ventaja táctica masiva temporal.</li>
                        <li><strong>Colaboración:</strong> Prepara gobiernos de colaboración para anexionar territorios con menos resistencia.</li>
                    </ul>`
            };

            d.innerHTML = info[s];
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
