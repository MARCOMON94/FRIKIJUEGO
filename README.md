# FRIKIJUEGO
Juego privado
<!DOCTYPE html>
<html>
  <head>
    <title>Personajes del juego de mesa</title>
    <style>
      .personaje {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin: 10px;
  display: inline-block;
  text-align: center;
}

.personaje img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}

.personaje h2 {
  margin-top: 10px;
  margin-bottom: 5px;
}

.personaje .stats {
  margin-top: 10px;
  display: flex;
  justify-content: space-around;
}

.personaje .stats div {
  display: flex;
  align-items: center;
}

.personaje .stats div label {
  margin-right: 5px;
}

.personaje input[type="number"] {
  width: 40px;
  text-align: center;
}

    </style>
  </head>
  <body>
    <h1>Personajes</h1>

    <div class="personaje">
      <img src="imagen_personaje1.jpg" alt="Personaje 1">
      <h2>Personaje 1</h2>
      <div class="stats">
        <div>
          <label>Vida:</label>
          <input type="number" value="10" min="0" max="10">
        </div>
        <div>
          <label>Energía:</label>
          <input type="number" value="5" min="0" max="5">
        </div>
      </div>
    </div>

    <div class="personaje">
      <img src="imagen_personaje2.jpg" alt="Personaje 2">
      <h2>Personaje 2</h2>
      <div class="stats">
        <div>
          <label>Vida:</label>
          <input type="number" value="10" min="0" max="10">
        </div>
        <div>
          <label>Energía:</label>
          <input type="number" value="5" min="0" max="5">
        </div>
      </div>
    </div>

    <!-- Agrega más personajes aquí -->

    <script>
      // Obtiene todos los controles de entrada
const inputs = document.querySelectorAll('input[type="number"]');

// Agrega un controlador de eventos a cada control de entrada
inputs.forEach(input => {
  input.addEventListener('change', e => {
    // Obtiene el valor actual de la entrada y los valores máximo y mínimo permitidos
    const value = parseInt(e.target.value);
    const min = parseInt(e.target.min);
    const max = parseInt(e.target.max);

    // Verifica si el valor está dentro de los límites permitidos
    if (value < min) {
      e.target.value = min;
    } else if (value > max) {
      e.target.value = max;
    }

    // Obtiene los elementos relacionados con el control de entrada
    const stat = e.target.closest('.stats');
    const vida = stat.querySelector('input[name="vida"]');
    const energia = stat.querySelector('input[name="energia"]');
    const nombre = e.target.closest('.personaje').querySelector('h2');

    // Actualiza el estado del personaje
    const vidaValue = parseInt(vida.value);
    const energiaValue = parseInt(energia.value);

    if (vidaValue <= 0) {
      alert(`${nombre.textContent} ha perdido toda la vida`);
    }

    if (energiaValue <= 0) {
      alert(`${nombre.textContent} se ha quedado sin energía`);
    }
  });
});

    </script>
  </body>
</html>


