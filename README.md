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
                    <p><strong>Composición y Proporción:</strong> La supervivencia de tu flota depende de las "pantallas" (Destructores y Cruceros Ligeros). Debes mantener un ratio mínimo de <strong>4 pantallas por cada Buque Capital</strong> para bloquear torpedos enemigos.</p>
                    <ul>
                        <li><strong>Fuerza de Choque (Strike Force):</strong> Tu flota principal. Déjala en puerto con esta misión para ahorrar combustible; solo saldrá cuando tus patrullas detecten una flota enemiga importante.</li>
                        <li><strong>Patrulla:</strong> Usa grupos de 1-2 Cruceros Ligeros muy rápidos equipados con radares y catapultas de aviones. Su objetivo es detectar, no combatir.</li>
                        <li><strong>Guerra de Convoyes:</strong> Los submarinos son letales en grupos de 8 a 12. Ataca en zonas de "Océano Profundo" para maximizar su ocultamiento.</li>
                        <li><strong>Control de Estrechos:</strong> El acceso a mares cerrados depende de puntos terrestres clave como Gibraltar, Suez o Copenhague.</li>
                        <li><strong>Diseño de Buques:</strong> Prioriza el Control de Daños y la Batería Principal en acorazados. En destructores, enfócate en cargas de profundidad si buscas cazar submarinos.</li>
                    </ul>`,
                tierra: `
                    <h3>🪖 EJÉRCITO Y COMBATE TERRESTRE</h3>
                    <p><strong>Mecánicas de Batalla:</strong> Las divisiones luchan según su Ataque Ligero, Pesado y Defensa. Se pierde cuando la Organización (barra verde) o Fuerza (barra naranja) llega a cero.</p>
                    <ul>
                        <li><strong>Ancho de Combate:</strong> Determinado por el terreno. Atacar desde múltiples direcciones suma +35 de ancho por cada lado adicional, permitiendo usar más reservas.</li>
                        <li><strong>Terrenos:</strong> Selva y Pantano son los peores; Llanura es el mejor para avanzar. Ciudades y Colinas ofrecen bonos defensivos.</li>
                        <li><strong>Generales:</strong> Nunca dejes ejércitos sin general. Ganan rasgos por experiencia (líder de infantería, montañero) y suben niveles de ataque, defensa, planificación y logística.</li>
                        <li><strong>Doctrinas Terrestres:</strong> 
                            <ul>
                                <li><em>Guerra Móvil:</em> Rapidez y blindados, decae en late game.</li>
                                <li><em>Fuego Superior:</em> Máximo ataque ligero, ideal contra la IA.</li>
                                <li><em>Gran Plan:</em> Bonos de planificación y defensa.</li>
                                <li><em>Asalto en Masa:</em> Reduce el ancho de la infantería, ideal para "avalanchas humanas".</li>
                            </ul>
                        </li>
                    </ul>`,
                aire: `<h3>✈️ SUPERIORIDAD AÉREA</h3><p>Sin superioridad aérea, tus tropas sufren una penalización de defensa y movimiento. El apoyo aéreo cercano (CAS) es el mayor multiplicador de daño en tierra.</p>`,
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Sistema de Red:</strong> El suministro fluye desde la Capital hacia los Hubs (centros de suministros) por vías férreas o hacia puertos por convoys.</p>
                    <ul>
                        <li><strong>Motorización de Hubs:</strong> Puedes configurar cada centro para usar caballos, camiones o motorización total. Esto extiende el "alcance" del suministro hacia las provincias cercanas.</li>
                        <li><strong>Ferrocarriles:</strong> Si hay cuellos de botella, mejora el nivel de las vías. El nivel de suministro que llega depende del nivel más bajo de vía en la ruta hacia la capital.</li>
                        <li><strong>Trenes:</strong> Produce Trenes Civiles (estándar), de Austeridad (baratos) o Blindados (resistentes a ataques aéreos).</li>
                        <li><strong>Puentes Aéreos:</strong> Aviones de transporte pueden suministrar tropas aisladas o cercadas si tienes superioridad aérea.</li>
                        <li><strong>Compañía de Logística:</strong> Indispensable en frentes grandes para reducir el consumo de suministros y combustible de la división.</li>
                    </ul>
                    <p><strong>Dato Crítico:</strong> El desempeño logístico debe estar siempre arriba del 70%. Los cuadros de cajas amarillas/rojas en el mapa indican dónde el suministro es insuficiente.</p>`,
                investigaciones: `
                    <h3>🔬 PRIORIDADES DE INVESTIGACIÓN</h3>
                    <p><strong>Gestión del Tiempo:</strong> Nunca dejes un slot de investigación vacío. Prioriza siempre las tecnologías que dan bonos de tiempo antes que las de equipo.</p>
                    <ul>
                        <li><strong>Industria y Electrónica:</strong> Son las más importantes al inicio. Investiga "Máquinas Herramientas" y "Computación" para acelerar todo el resto de la partida.</li>
                        <li><strong>Bonos de Tiempo:</strong> Evita investigar tecnologías con años de adelanto a menos que tengas un bono del 50% o 100% por enfoque nacional.</li>
                        <li><strong>Compañías de Apoyo:</strong> No olvides investigar la Compañía de Radio (Refuerzo) y la de Logística si planeas frentes extensos.</li>
                    </ul>`,
                inteligencia: `
                    <h3>🕵️ SERVICIOS DE INTELIGENCIA (La Agencia)</h3>
                    <p><strong>Espionaje:</strong> La creación de una agencia te permite conocer los planes del enemigo antes de que ocurran.</p>
                    <ul>
                        <li><strong>Redes de Espionaje:</strong> Mantén espías en naciones enemigas para obtener bonos de combate y reducir su bonificación de planificación.</li>
                        <li><strong>Criptografía:</strong> Desencriptar las claves enemigas otorga una ventaja táctica temporal masiva en el frente de batalla.</li>
                        <li><strong>Misiones:</strong> Usa espías para aumentar la ideología en otros países o para preparar una colaboración de gobierno que facilite la rendición del rival.</li>
                    </ul>`
            };

            d.innerHTML = info[s];
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
