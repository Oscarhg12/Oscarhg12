
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Juego: Verdadero o Falso</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background-color: #fce4ec; }
    .question { margin-bottom: 20px; background: #fff3f6; padding: 15px; border-radius: 8px; }
    .question h3 { margin-bottom: 10px; }
    button { margin-right: 10px; padding: 10px 20px; border: none; border-radius: 6px; cursor: pointer; }
    .true { background-color: #4caf50; color: white; }
    .false { background-color: #f44336; color: white; }
    .feedback { margin-top: 10px; font-weight: bold; }
    #reiniciar { background-color: #2196f3; color: white; margin-top: 20px; }
  </style>
</head>
<body>
  <h1>Juego: Verdadero o Falso</h1>
  <div id="quiz"></div>
  <button id="reiniciar" onclick="location.reload()">Reiniciar Juego</button>

  <script>
    const preguntas = [
      { texto: "El BHT es un conservante que se encuentra comúnmente en productos de maquillaje.", respuesta: true },
      { texto: "Los antioxidantes solo se encuentran en los alimentos, no en los cosméticos.", respuesta: false },
      { texto: "El maquillaje con antioxidantes puede ayudar a proteger la piel del daño ambiental.", respuesta: true },
      { texto: "El BHT es completamente natural y se obtiene de frutas.", respuesta: false },
      { texto: "Usar maquillaje con antioxidantes puede tener beneficios antienvejecimiento.", respuesta: true },
    ];

    const quizDiv = document.getElementById("quiz");

    preguntas.forEach((pregunta, i) => {
      const contenedor = document.createElement("div");
      contenedor.className = "question";

      const titulo = document.createElement("h3");
      titulo.textContent = `${i + 1}. ${pregunta.texto}`;

      const btnTrue = document.createElement("button");
      btnTrue.textContent = "Verdadero";
      btnTrue.className = "true";

      const btnFalse = document.createElement("button");
      btnFalse.textContent = "Falso";
      btnFalse.className = "false";

      const feedback = document.createElement("div");
      feedback.className = "feedback";

      btnTrue.onclick = () => {
        feedback.textContent = pregunta.respuesta ? "¡Correcto!" : "Incorrecto.";
        btnTrue.disabled = true;
        btnFalse.disabled = true;
      };

      btnFalse.onclick = () => {
        feedback.textContent = !pregunta.respuesta ? "¡Correcto!" : "Incorrecto.";
        btnTrue.disabled = true;
        btnFalse.disabled = true;
      };

      contenedor.appendChild(titulo);
      contenedor.appendChild(btnTrue);
      contenedor.appendChild(btnFalse);
      contenedor.appendChild(feedback);

      quizDiv.appendChild(contenedor);
    });
  </script>
</body>
</html>
