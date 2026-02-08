<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Invitation 50 ans</title>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      color: #fff;
      text-align: center;
      overflow: hidden;
    }
    @keyframes gradientBG {
      0% {background-position:0% 50%;}
      50% {background-position:100% 50%;}
      100% {background-position:0% 50%;}
    }
    h1 {
      font-size: 3em;
      margin-top: 50px;
      text-shadow: 2px 2px 5px #000;
      animation: bounce 2s infinite;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
    }
    p {
      font-size: 1.5em;
      margin: 10px 0;
    }
    #countdown {
      font-size: 2em;
      margin: 30px 0;
      font-weight: bold;
    }
    button {
      background-color: #ff4081;
      border: none;
      padding: 15px 30px;
      font-size: 1.5em;
      border-radius: 12px;
      cursor: pointer;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.3);
      transition: transform 0.2s;
    }
    button:hover {
      transform: scale(1.1);
    }
    /* Confetti animation */
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background-color: #fff;
      top: -10px;
      animation: fall linear infinite;
    }
    @keyframes fall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>
  <h1>🎉 Invitation pour mes 50 ans ! 🎉</h1>
  <p>📅 4 avril 2026 à 18h</p>
  <p>📍 750 route de Keryouen, 29910 Trégunc</p>

  <div id="countdown"></div>

  <button onclick="window.open('https://docs.google.com/forms/d/e/1FAIpQLSekLiMgKf6C3dD4V-ypeuR8uVNd2qS8nXGwY4YZLMhKCKxtAA/viewform?usp=header','_blank')">Répondre au questionnaire</button>

  <script>
    // Compte à rebours
    const eventDate = new Date('April 4, 2026 18:00:00').getTime();
    const countdown = document.getElementById('countdown');

    function updateCountdown() {
      const now = new Date().getTime();
      const distance = eventDate - now;

      if(distance < 0) {
        countdown.innerHTML = "🎉 C'est aujourd'hui ! 🎉";
        return;
      }

      const days = Math.floor(distance / (1000*60*60*24));
      const hours = Math.floor((distance % (1000*60*60*24)) / (1000*60*60));
      const minutes = Math.floor((distance % (1000*60*60)) / (1000*60));
      const seconds = Math.floor((distance % (1000*60)) / 1000);

      countdown.innerHTML = `${days}j ${hours}h ${minutes}m ${seconds}s`;
    }

    setInterval(updateCountdown, 1000);
    updateCountdown();

    // Confetti générateur
    function createConfetti() {
      const confetti = document.createElement('div');
      confetti.classList.add('confetti');
      confetti.style.left = Math.random() * window.innerWidth + 'px';
      confetti.style.backgroundColor = `hsl(${Math.random()*360}, 100%, 50%)`;
      confetti.style.animationDuration = (2 + Math.random()*3) + 's';
      document.body.appendChild(confetti);
      setTimeout(() => confetti.remove(), 5000);
    }

    setInterval(createConfetti, 200);
  </script>
</body>
</html>
