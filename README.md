<!Todo hecho con el fin de conocimientos del juego.>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Hearts Of Iron IV</title>

  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      height: 100vh;
      background: url('fondo.png') no-repeat center center/cover;
      font-family: 'Orbitron', sans-serif;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      position: relative;
    }

    body::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(56,189,248,0.1) 1px, transparent 1px);
      background-size: 40px 40px;
      animation: moveBg 20s linear infinite;
    }

    body::after {
      content: "";
      position: absolute;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      top: 0;
      left: 0;
      z-index: 1;
    }

    @keyframes moveBg {
      from { transform: translate(0,0); }
      to { transform: translate(-200px, -200px); }
    }

    .container {
      text-align: center;
      position: relative;
      z-index: 2;
      backdrop-filter: blur(10px);
      background: rgba(0,0,0,0.4);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 0 40px rgba(56,189,248,0.3);
    }

    h1 {
      font-size: 3em;
      color: #38bdf8;
      text-shadow: 0 0 20px #38bdf8;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.2em;
      color: #cbd5f5;
      margin-bottom: 30px;
    }

    button {
      padding: 12px 25px;
      font-size: 1em;
      border: none;
      border-radius: 10px;
      background: #38bdf8;
      color: black;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 0 15px #38bdf8;
      margin: 5px;
    }

    button:hover {
      transform: scale(1.1);
      background: #0ea5e9;
      box-shadow: 0 0 25px #38bdf8;
    }

    footer {
      margin-top: 20px;
      font-size: 0.8em;
      color: #94a3b8;
    }
  </style>
</head>

<body>

  <!-- PANTALLA PRINCIPAL -->
  <div id="inicio" class="container">
    <h1>⚔️ Hearts Of Iron IV ⚔️</h1>
    
    <p>
      Todo lo relacionado con el juego Hearts Of Iron IV de Paradox
    </p>

    <button onclick="entrar()">Entrar</button>

    <footer>
      Fan page no oficial
    </footer>
  </div>

  <!-- MENÚ -->
  <div id="menu" class="container" style="display:none;">
    <h1>🌍 Panel de Estrategia</h1>

    <p>Selecciona una doctrina</p>

    <button onclick="alert('Sección Marina')">🚢 Marina</button>
    <button onclick="alert('Sección Terrestre')">🪖 Terrestre</button>
    <button onclick="alert('Sección Aéreo')">✈️ Aéreo</button>

    <br><br>

    <button onclick="alert('Sección Investigaciones')">🔬 Investigaciones</button>
    <button onclick="alert('Sección Focos Nacionales')">🏛️ Focos Nacionales</button>
    <button onclick="alert('Sección Guía Logística')">📦 Guía Logística</button>

    <br><br>

    <button onclick="volver()">⬅️ Volver</button>
  </div>

  <script>
    function entrar() {
      document.getElementById('inicio').style.display = 'none';
      document.getElementById('menu').style.display = 'block';
    }

    function volver() {
      document.getElementById('menu').style.display = 'none';
      document.getElementById('inicio').style.display = 'block';
    }
  </script>

</body>
</html>
