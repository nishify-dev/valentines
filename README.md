# valentines
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Ana, Be My Valentine?</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      height: 100vh;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .card {
      background: white;
      padding: 2.5rem;
      border-radius: 25px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      max-width: 360px;
      z-index: 2;
    }

    h1 {
      color: #ff4d6d;
      margin-bottom: 10px;
    }

    p {
      font-size: 1.1rem;
      margin-bottom: 20px;
    }

    button {
      font-size: 1rem;
      padding: 12px 22px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      margin: 10px;
      transition: all 0.2s ease;
    }

    #yesBtn {
      background: #ff4d6d;
      color: white;
      font-size: 1.1rem;
    }

    #noBtn {
      background: #ddd;
      color: #333;
      position: absolute;
    }

    .hearts {
      position: fixed;
      top: -10px;
      font-size: 22px;
      animation: fall 5s linear infinite;
      z-index: 1;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="card">
    <h1>Ana ❤️</h1>
    <p>Will you be my Valentine?</p>
    <button id="yesBtn" onclick="sayYes()">Yes 💕</button>
    <button id="noBtn" onmouseover="goCrazy()">No 🙄</button>
  </div>

  <script>
    let noCount = 0;

    function goCrazy() {
      const btn = document.getElementById("noBtn");
      noCount++;

      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 50);

      btn.style.left = x + "px";
      btn.style.top = y + "px";
      btn.style.transform = `scale(${Math.max(0.4, 1 - noCount * 0.1)}) rotate(${Math.random() * 360}deg)`;

      const texts = [
        "No 🙄",
        "Wait—",
        "Stop 😭",
        "Wrong choice",
        "Try again",
        "Be serious",
        "That’s illegal",
        "You don’t mean that",
        "Click Yes 😏"
      ];

      btn.innerText = texts[Math.min(noCount, texts.length - 1)];

      const yesBtn = document.getElementById("yesBtn");
      yesBtn.style.transform = `scale(${1 + noCount * 0.05})`;
    }

    function sayYes() {
      document.body.innerHTML = `
        <div class="card">
          <h1>YAY ANA!!! 💖💖💖</h1>
          <p>You officially made me the happiest person ever 🥹<br><br>
          I can’t wait to be your Valentine 😘</p>
        </div>
      `;
      createHearts();
    }

    function createHearts() {
      setInterval(() => {
        const heart = document.createElement("div");
        heart.classList.add("hearts");
        heart.innerText = "❤️";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (Math.random() * 3 + 2) + "s";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 5000);
      }, 250);
    }
  </script>

</body>
</html>
