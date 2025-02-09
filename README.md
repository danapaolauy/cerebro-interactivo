<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Atlas Cerebral - Cerebelo Interactivo</title>
  <style>
    body {
      margin: 0;
      background-color: #333;
      color: #fff;
      font-family: Arial, sans-serif;
      overflow: hidden;
    }
    /* Contenedor para el SVG (ocupa toda la ventana) */
    #svgContainer {
      width: 100%;
      height: 100vh;
    }
    /* Caja informativa en la parte inferior */
    #info {
      position: fixed;
      bottom: 20px;
      left: 20px;
      right: 20px;
      background: rgba(255, 255, 255, 0.9);
      color: #000;
      padding: 15px;
      border-radius: 8px;
      font-size: 16px;
      line-height: 1.5;
      box-shadow: 0 2px 8px rgba(0,0,0,0.3);
    }
  </style>
</head>
<body>
  <!-- Contenedor del SVG -->
  <div id="svgContainer">
    <svg viewBox="0 0 800 600" id="brainAtlas">
      <!-- Grupo que contendrá la sección del cerebelo -->
      <g id="cerebellum">
        <!-- Región: Hemisferio Cerebelar Izquierdo (forma aproximada) -->
        <path id="cerebelumLeft" d="M200,400 
              C150,350 150,450 200,500 
              C250,550 300,550 350,500 
              C300,450 250,450 200,400 Z" 
              fill="#555" stroke="#fff" stroke-width="2"/>
        <!-- Región: Hemisferio Cerebelar Derecho (forma aproximada) -->
        <path id="cerebelumRight" d="M450,400 
              C400,350 400,450 450,500 
              C500,550 550,550 600,500 
              C550,450 500,450 450,400 Z" 
              fill="#777" stroke="#fff" stroke-width="2"/>
      </g>
      <!-- (Opcional) Puedes agregar más elementos SVG para representar otras regiones o detalles -->
    </svg>
  </div>
  
  <!-- Caja de información -->
  <div id="info">Haz clic en una región del cerebelo para ver información.</div>
  
  <script>
    // Obtenemos el contenedor de la información
    const infoBox = document.getElementById('info');

    // Definimos la información para cada región (puedes ampliar la información)
    const regionsInfo = {
      'cerebelumLeft': 'Hemisferio Cerebelar Izquierdo: Participa en el control motor, coordinación y aprendizaje motor.',
      'cerebelumRight': 'Hemisferio Cerebelar Derecho: Involucrado en la coordinación motora, equilibrio y procesamiento sensorial.'
    };

    // Función para cambiar el color de la región al pasar el mouse (efecto hover)
    function addHoverEffect(regionElement, originalFill) {
      regionElement.addEventListener('mouseover', () => {
        regionElement.style.fill = 'orange';
      });
      regionElement.addEventListener('mouseout', () => {
        regionElement.style.fill = originalFill;
      });
    }

    // Obtenemos los elementos de las dos regiones
    const leftRegion = document.getElementById('cerebelumLeft');
    const rightRegion = document.getElementById('cerebelumRight');

    // Agregamos el efecto hover a cada región
    addHoverEffect(leftRegion, '#555');
    addHoverEffect(rightRegion, '#777');

    // Agregamos eventos de clic para mostrar la información correspondiente
    leftRegion.addEventListener('click', () => {
      infoBox.textContent = regionsInfo['cerebelumLeft'];
    });

    rightRegion.addEventListener('click', () => {
      infoBox.textContent = regionsInfo['cerebelumRight'];
    });
  </script>
</body>
</html>
