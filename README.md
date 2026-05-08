<!-- Todo hecho a base para conocimientos sobre el juego. -->
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Hearts Of Iron IV</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: black;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* INICIO */
#inicio {
  text-align: center;
}

button {
  padding: 10px 20px;
  cursor: pointer;
}

/* MENU */
#menu {
  display: none;
  position: absolute;
  width: 100%;
  height: 100%;
  background: #111;
  text-align: center;
  padding-top: 50px;
}

/* BOTON VOLVER */
.volver-btn {
  position: absolute;
  top: 10px;
  left: 10px;
}

/* SECCIONES */
.seccion {
  margin: 10px;
  padding: 10px;
  border: 1px solid white;
  display: inline-block;
}
</style>
</head>

<body>

<div id="inicio">
  <h1>Hearts Of Iron IV</h1>
  <p>Todo lo relacionado con el juego Hearts Of Iron IV de Paradox</p>
  <button onclick="entrar()">Entrar</button>
</div>

<div id="menu">
  <button onclick="volver()" class="volver-btn">Volver atrás</button>

  <h2>Secciones</h2>

  <div class="seccion">Marina</div>
  <div class="seccion">Terrestre</div>
  <div class="seccion">Aéreo</div>
  <div class="seccion">Investigaciones</div>
  <div class="seccion">Focos Nacionales</div>
  <div class="seccion">Guía Logística</div>
</div>

<script>
function entrar() {
  document.getElementById("inicio").style.display = "none";
  document.getElementById("menu").style.display = "block";
}

function volver() {
  document.getElementById("menu").style.display = "none";
  document.getElementById("inicio").style.display = "block";
}
</script>

</body>
</html>
