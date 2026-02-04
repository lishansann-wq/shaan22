# shaan22
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lisha 💖 Shaan</title>

  <style>
    body {
      margin: 0;
      font-family: 'Comic Sans MS', 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ffb6c1, #ffe4e1);
      text-align: center;
      color: #b3003b;
      overflow-x: hidden;
    }

    h1 {
      margin-top: 40px;
      font-size: 3rem;
    }

    .card {
      background: white;
      width: 80%;
      max-width: 520px;
      margin: 40px auto;
      padding: 30px;
      border-radius: 25px;
      box-shadow: 0 10px 30px rgba(255, 0, 102, 0.3);
      position: relative;
      min-height: 300px;
    }

    h2 {
      margin-bottom: 40px;
    }

    button {
      padding: 12px 25px;
      font-size: 1.1rem;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      margin: 10px;
    }

    .yes {
      background: #ff4d88;
      color: white;
    }

    .yes:hover {
      background: #ff1a66;
    }

    .no {
      background: #ffc2d1;
      color: #b3003b;
      position: relative;
    }

    .moving-no {
      position: absolute;
    }

    .hidden {
      display: none;
    }

    img {
      width: 260px;
      margin-top: 20px;
      border-radius: 20px;
    }

    .hearts span {
      position: fixed;
      bottom: -20px;
      font-size: 24px;
      animation: floatUp 6s infinite;
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-100vh); opacity: 0; }
    }
  </style>
</head>

<body>

<h1>Hey Shaan 💕</h1>

<!-- Background Music -->
<audio id="bgMusic" loop>
  <source src="https://www.orangefreesounds.com/wp-content/uploads/2021/06/Slow-calm-relaxing-music.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

<!-- Questions 1–4 -->
<div class="card" id="card">
  <h2 id="question"></h2>
  <button class="yes" onclick="nextQuestion()">Yes 💖</button>
  <button class="no">No 😌</button>
</div>

<!-- Valentine Question -->
<div class="card hidden" id="final">
  <h2>Okay… now the real question 💘</h2>
  <h1>Will you be my Valentine? 💝</h1>
  <button class="yes" onclick="showGif()">YES 💕</button>
  <button class="no moving-no" id="finalNo">No 😤</button>
</div>

<!-- Success Screen -->
<div class="card hidden" id="gifCard">
  <h1>I LOVE YOU 🥹❤️</h1>
  
  <p>— Love, Lisha 💌</p>
  <img src="https://media.giphy.com/media/l0MYyDa8S9ghzNebm/giphy.gif">
</div>

<div class="hearts"></div>

<script>
  const questions = [
    "If I steal Buddy, will you still love me? 😌",
    "Do you agree that me annoying you is actually my love language? 😏",
    "Do you promise to stand by me even on our worst days? ❤️",
    "Will you always choose me? 💞"
  ];

  let index = 0;
  let musicStarted = false;
  let noInterval;

  const questionEl = document.getElementById("question");
  const music = document.getElementById("bgMusic");

  questionEl.innerText = questions[index];

  function nextQuestion() {
    if (!musicStarted) {
      music.play();
      musicStarted = true;
    }

    index++;
    if (index < questions.length) {
      questionEl.innerText = questions[index];
    } else {
      document.getElementById("card").classList.add("hidden");
      document.getElementById("final").classList.remove("hidden");
      startMovingNo();
    }
  }

  function startMovingNo() {
    const noBtn = document.getElementById("finalNo");
    const card = document.getElementById("final");

    noInterval = setInterval(() => {
      const w = card.offsetWidth - 120;
      const h = card.offsetHeight - 120;

      // Safe zone: bottom half only
      const x = Math.random() * w;
      const y = Math.random() * (h / 2) + h / 2;

      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
    }, 1000);
  }

  function showGif() {
    clearInterval(noInterval);
    document.getElementById("final").classList.add("hidden");
    document.getElementById("gifCard").classList.remove("hidden");
  }

  // Floating hearts
  const heartsContainer = document.querySelector(".hearts");
  setInterval(() => {
    const heart = document.createElement("span");
    heart.innerHTML = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
    heartsContainer.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 300);
</script>

</body>
</html>
