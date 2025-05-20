<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Invitación con Stitch</title>
  <link rel="apple-touch-icon" href="https://static.wikia.nocookie.net/disney/images/4/48/Profile_-_Stitch.png">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="mobile-web-app-capable" content="yes">
  <!-- Fuente personalizada Pacifico -->
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Pacifico', cursive;
      background: linear-gradient(to bottom, #0acffe, #495aff);
      color: white;
      overflow: hidden;
    }

    .parallax {
      position: fixed;
      top: 0; left: 0;
      width: 200%;
      height: 200%;
      background-image: url('https://telasyretales.com/wp-content/uploads/2024/09/9-10.jpg');
      background-size: cover;
      animation: moveBg 30s linear infinite;
      opacity: 0.3;
      z-index: -1;
    }

    @keyframes moveBg {
      0% { transform: translate(0, 0); }
      100% { transform: translate(-50%, -50%); }
    }

    .container {
      text-align: center;
      padding: 40px 20px;
      display: none;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 20px;
      animation: slideIn 1.5s ease-out;
      color: #ffff5e;
      text-shadow: 3px 3px #000;
    }

    @keyframes slideIn {
      from { transform: translateY(-100px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .stitch {
      width: 220px;
      animation: float 4s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-25px); }
    }

    .info {
      margin-top: 30px;
      font-size: 1.2em;
      background: rgba(0,0,0,0.4);
      padding: 20px;
      border-radius: 15px;
      animation: fadeIn 2s ease-in;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .btn, .start-btn {
      margin-top: 20px;
      padding: 12px 25px;
      font-size: 1em;
      background: #ff4081;
      border: none;
      border-radius: 10px;
      color: white;
      cursor: pointer;
      animation: pulse 2s infinite;
    }

    .btn:hover, .start-btn:hover {
      background: #ff79a8;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }

    audio {
      display: none;
    }

    .welcome-screen {
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to bottom right, #0044ff, #00ccff);
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      z-index: 200;
      padding: 20px;
    }

    .welcome-screen h2 {
      font-size: 3em;
      margin-bottom: 20px;
      text-shadow: 2px 2px #000;
    }

    .welcome-screen img {
      width: 80%;
      max-width: 400px;
      margin-bottom: 50px;
      animation: float 4s ease-in-out infinite;
    }

    .audio-control {
      position: fixed;
      top: 15px;
      right: 15px;
      background: rgba(0,0,0,0.6);
      padding: 20px;
      border-radius: 50%;
      cursor: pointer;
      color: white;
      font-size: 18px;
    }
  </style>
</head>
<body>

  <div class="parallax"></div>

  <!-- PANTALLA DE BIENVENIDA -->
  <div class="welcome-screen" id="welcome">
    <img src="https://m.media-amazon.com/images/S/pv-target-images/a2af76dbe33a6e15255fd3ae50bde7feba4e94b1915e6983dfa3cf68e7bfe08d._SX1080_FMjpg_.jpg" alt="Stitch" />
    <h2>¡Ohana te da la bienvenida! 🌺</h2>
    <button class="start-btn" onclick="iniciarFiesta()">Entrar Invitación 🎉</button>
  </div>

  <!-- CONTENIDO PRINCIPAL -->
  <div class="container" id="mainContent">
    <h1>¡Quieres conmigo ir a ver Lilo & Stitch 🌺💙</h1>
    <img class="stitch" src="https://gallery.yopriceville.com/var/albums/Animated-Gif-Images/Lilo_and_Stitch_Dance_gif_Animation.gif?m=1629741116" alt="Stitch animado" />

    <div class="info">
      <p>📍 <strong>Lugar:</strong> Cine Hawaiana Espacial</p>
      <p>📅 <strong>Fecha:</strong> 25 de Mayo de 2025</p>
      <p>🕓 <strong>Hora:</strong> 5:00 PM</p>
      <p>🌸 Pasar tiempo conmigo, baile, comida ¡y sorpresas!</p>
      <p>💙 ¡Ohana significa familia, y tú eres parte de la mía!</p>
      <button class="btn" onclick="confirmarAsistencia()">Confirmar Asistencia</button>
    </div>
  </div>

  <!-- CONTROL DE AUDIO -->
  <div class="audio-control" onclick="toggleAudio()">🎵</div>

  <!-- AUDIO DE FONDO -->
  <audio id="bg-music" loop>
    <source src="https://archive.org/download/tvtunes_25269/Lilo%20and%20Stitch%20-%20He%20Mele%20No%20Lilo.mp3" type="audio/mpeg">
  </audio>

  <script>
    const music = document.getElementById('bg-music');
    const mainContent = document.getElementById('mainContent');
    const welcome = document.getElementById('welcome');

    function iniciarFiesta() {
      welcome.style.display = "none";
      mainContent.style.display = "block";
      music.play();
    }

    function confirmarAsistencia() {
      alert("¡Gracias por confirmar! 💌 Nos vemos en la cita.");
    }

    function toggleAudio() {
      if (music.paused) {
        music.play();
      } else {
        music.pause();
      }
    }
  </script>
</body>
</html>

