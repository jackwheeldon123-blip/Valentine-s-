<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine 💘</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Comic Sans MS', cursive, sans-serif;
    }

    .card {
      background: #fff0f5;
      padding: 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      position: relative;
      z-index: 2;
    }

    h1 {
      color: #d6336c;
      margin-bottom: 30px;
    }

    .buttons {
      position: relative;
      height: 80px;
    }

    button {
      font-size: 18px;
      padding: 12px 30px;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    #yes {
      background-color: #ff4d6d;
      color: white;
    }

    #yes:hover {
      background-color: #e63950;
    }

    #no {
      background-color: #adb5bd;
      color: white;
      position: absolute;
      left: 140px;
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      bottom: -20px;
      font-size: 20px;
      color: #ff4d6d;
      animation: floatUp 6s linear infinite;
      opacity: 0.8;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 0;
      }
      10% {
        opacity: 1;
      }
      100% {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="card" id="card">
    <h1>Will you be my Valentine? 💌</h1>
    <div class="buttons">
      <button id="yes" onclick="sayYes()">Yes 💕</button>
      <button id="no">No 🙅‍♀️</button>
    </div>
  </div>

  <script>
    // No button dodges
    const noButton = document.getElementById("no");
    noButton.addEventListener("mouseover", () => {
      const x = Math.random() * 200 - 100;
      const y = Math.random() * 80 - 40;
      noButton.style.transform = `translate(${x}px, ${y}px)`;
    });

    // Floating hearts generator
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerHTML = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = Math.random() * 3 + 4 + "s";
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 7000);
    }

    setInterval(createHeart, 400);

    // Yes button → love note
    function sayYes() {
      document.body.innerHTML = `
        <div style="
          height:100vh;
          display:flex;
          justify-content:center;
          align-items:center;
          background:linear-gradient(135deg, #ff9a9e, #fad0c4);
          font-family:'Comic Sans MS', cursive;
          color:#d6336c;
          text-align:center;
          padding:40px;
        ">
          <div>
            <h1>💖 You said YES! 💖</h1>
            <p style="font-size:22px; max-width:600px;">
              From the moment you came into my life, everything felt warmer,
              brighter, and a little more magical. Thank you for being you,
              for making me smile, and for choosing me today.  
              <br><br>
              Happy Valentine’s Day, my favorite person 💘
            </p>
          </div>
        </div>
      `;
    }
  </script>

</body>
</html>
