<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Hearts Of Iron IV - Guía para Principiantes</title>

<style>
/* RESET */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* FONDO */
body {
  /* He añadido 'fixed' para que el fondo no se mueva al hacer scroll */
  background: url('fondo.png') no-repeat center center fixed;
  background-size: cover;
  color: white;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #111; /* Color de respaldo */
}

/* CAPA OSCURA */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.8);
  z-index: 1;
}

/* CONTENEDOR PRINCIPAL (Para centrar todo) */
.main-container {
  position: relative;
  z-index: 10;
  width: 90%;
  max-width: 800px;
  text-align: center;
  padding: 20px;
}

/* PANTALLAS */
#inicio, #contenido {
  display: flex;
  flex-direction: column;
  align-items: center;
  animation: aparecer 0.5s ease;
}

/* TITULO */
h1 {
  font-size: clamp(25px, 5vw, 50px); /* Tamaño responsivo */
  margin-bottom: 10px;
  text-shadow: 0 0 20px rgba(0,150,255,0.8);
  color: #00aaff;
}

/* BOTON */
button {
  padding: 12px 30px;
  border: 2px solid #00aaff;
  border-radius: 5px;
  background: rgba(0, 170, 255, 0.2);
  color: white;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
  margin-bottom: 20px;
}

button:hover {
  background: #00aaff;
  box-shadow: 0 0 20px #00aaff;
}

/* CONTENEDOR DE SECCIONES (Grid para que no se estiren) */
.grid-secciones {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 15px;
  width: 100%;
  margin-top: 20px;
}

.seccion {
  padding: 15px;
  background: rgba(20,20,20,0.8);
  border-left: 5px solid #00aaff;
  cursor: pointer;
  transition: 0.3s;
  text-align: left;
}

.seccion:hover {
  background: #00aaff;
  color: black;
  transform: scale(1.05);
}

/* DETALLE */
#detalle {
  margin-top: 30px;
  padding: 20px;
  background: rgba(0,0,0,0.9);
  border: 1px solid #00aaff;
  border-radius: 5px;
  width: 100%;
  min-height: 100px;
}

@keyframes aparecer {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

</style>
</head>

<body>

<div class="overlay"></div>

<div class="main-container">
  <!-- INICIO -->
  <div id="inicio">
    <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
    <p style="margin-bottom: 30px;">Manual de campo para nuevos comandantes.</p>
    <button onclick="entrar()">INICIAR OPERACIÓN</button>
  </div>

  <!-- CONTENIDO -->
  <div id="contenido" style="display:none;">
    <button onclick="volver()">⬅ VOLVER AL MENÚ</button>

    <div class="grid-secciones">
      <div class="seccion" onclick="abrirSeccion('marina')">⚓ Marina</div>
      <div class="seccion" onclick="abrirSeccion('tierra')">🪖 Terrestre</div>
      <div class="seccion" onclick="abrirSeccion('aire')">✈ Aéreo</div>
      <div class="seccion" onclick="abrirSeccion('investigaciones')">🔬 Investigaciones</div>
      <div class="seccion" onclick="abrirSeccion('focos')">📜 Focos Nacionales</div>
      <div class="seccion" onclick="abrirSeccion('logistica')">📦 Logística</div>
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
  document.getElementById("inicio").style.display = "flex";
  document.getElementById("detalle").style.display = "none";
}

function abrirSeccion(seccion) {
  let detalleDiv = document.getElementById("detalle");
  detalleDiv.style.display = "block";
  
  let contenidos = {
    marina: "<h3>⚓ Marina</h3><p>Gestiona el control de los mares. No olvides asignar convoyes para el comercio y escoltas para evitar submarinos enemigos.</p>",
    tierra: "<h3>🪖 Terrestre</h3><p>La clave es el 'Combat Width' (Ancho de combate). Mantén tus divisiones de infantería con suficiente artillería.</p>",
    aire: "<h3>✈ Aéreo</h3><p>Sin superioridad aérea, tus tropas sufrirán penalizadores graves. Prioriza los cazas pesados y apoyo cercano.</p>",
    investigaciones: "<h3>🔬 Investigaciones</h3><p>Enfócate en industria y computación al principio del juego para acelerar todo lo demás.</p>",
    focos: "<h3>📜 Focos Nacionales</h3><p>El camino político que elijas determinará tus alianzas. Lee bien los requisitos antes de empezar uno.</p>",
    logistica: "<h3>📦 Logística</h3><p>¡El corazón del juego! Construye trenes y centros de suministros para que tus tropas no mueran de hambre en el frente.</p>"
  };

  detalleDiv.innerHTML = contenidos[seccion];
}
</script>

</body>
</html>
