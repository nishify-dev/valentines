# valentines
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine?</title>
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
      max-width: 350px;
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
      padding: 12px 20px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      margin: 10px;
    }

    #yesBtn {
      background: #ff4d6d;
      color: white;
    }

    #noBtn {
      background: #ddd;
      color: #333;
      position: relative;
    }

    .hearts {
      position: fixed;
      top: -10px;
      font-size: 20px;
      animation: fall 5s linear infinite;
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
    <h1>Hey ❤️</h1>
    <p>Will you be my Valentine?</p>
    <button id="yesBtn" onclick="sayYes()">Yes 💕</button>
    <button id="noBtn" onmouseover="moveNo()">No 🙄</button>
  </div>

  <script>
    function sayYes() {
      document.body.innerHTML = `
        <div class="card">
          <h1>YAY!!! 💖💖💖</h1>
          <p>I can’t wait to spend Valentine’s Day with you 😘</p>
        </div>
      `;
      createHearts();
    }

    function moveNo() {
      const btn = document.getElementById("noBtn");
      const x = Math.random() * 200 - 100;
      const y = Math.random() * 200 - 100;
      btn.style.transform = `translate(${x}px, ${y}px)`;
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
      }, 300);
    }
  </script>

</body>
</html>
