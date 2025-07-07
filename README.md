<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Untuk Nadia 💖</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Comic Sans MS', cursive;
      background: linear-gradient(#ffc0cb, #fff);
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
      padding: 1rem;
      text-align: center;
    }

    #lockScreen, #contentScreen {
      display: none;
      flex-direction: column;
      align-items: center;
    }

    #lockScreen.active, #contentScreen.active {
      display: flex;
    }

    .input {
      margin-top: 1rem;
      padding: 10px;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
    }

    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: red;
      transform: rotate(45deg);
      animation: fall 10s linear forwards;
      opacity: 0.8;
    }

    .heart::before, .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: red;
      border-radius: 50%;
    }

    .heart::before { top: -10px; left: 0; }
    .heart::after { left: -10px; top: 0; }

    @keyframes fall {
      0% { transform: translateY(0) rotate(45deg); opacity: 1; }
      100% { transform: translateY(100vh) rotate(45deg); opacity: 0; }
    }

    .card {
      background: white;
      padding: 1rem;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      max-width: 300px;
      margin-bottom: 1rem;
    }

    .button-spotify {
      background-color: #1DB954;
      color: white;
      padding: 0.7rem 1.2rem;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
      cursor: pointer;
      text-decoration: none;
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <audio id="music" preload="auto">
    <source id="audioSource" src="https://docs.google.com/uc?export=open&id=1lNnJ9K5fdHcUqMJZy3JzHLZfEYCRLvx7" type="audio/mpeg">
  </audio>

  <div id="lockScreen" class="active">
    <h2>Apakah kamu ingat saat kisah kita dimulai? 🔐</h2>
    <input id="dateInput" class="input" placeholder="DD/MM/YYYY" maxlength="10">
    <button class="input" onclick="checkDate()">Buka</button>
  </div>

  <div id="contentScreen">
    <div class="card">
      <p><strong>Cintaku 💕</strong></p>
      <p>Surat kecil ini hanyalah bisikan tentang betapa aku mencintaimu.<br>
      Terima kasih telah membuatku begitu bahagia.<br>
      Dari Meksiko ke Indonesia, hatiku selalu menemukanmu. Aku mencintaimu 💖</p>
    </div>

    <a class="button-spotify" href="https://open.spotify.com/playlist/76XQuQz8opoVWHyANv60Xo" target="_blank">Pergi ke Playlist 💿</a>
  </div>

  <script>
    const lockScreen = document.getElementById("lockScreen");
    const contentScreen = document.getElementById("contentScreen");
    const music = document.getElementById("music");
    const audioSource = document.getElementById("audioSource");
    const dateInput = document.getElementById("dateInput");

    function checkDate() {
      const value = dateInput.value;
      if (value === "17/05/2025" || value === "18/05/2025") {
        lockScreen.classList.remove("active");
        contentScreen.classList.add("active");
        audioSource.src = "https://docs.google.com/uc?export=open&id=1nra7VvwhkDFg_pvYQK7UZBOwO3-HEsmI";
        music.load();
        music.play();
      } else {
        alert("Tanggal salah, coba lagi ya ❤️");
      }
    }

    dateInput.addEventListener("input", function(e) {
      let value = this.value.replace(/[^0-9]/g, "");
      if (value.length > 2 && value.length <= 4)
        value = value.slice(0,2) + "/" + value.slice(2);
      else if (value.length > 4)
        value = value.slice(0,2) + "/" + value.slice(2,4) + "/" + value.slice(4,8);
      this.value = value;
    });

    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.top = Math.random() * -20 + "vh";
      heart.style.animationDuration = (Math.random() * 5 + 5) + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 10000);
    }

    setInterval(() => {
      if (document.querySelectorAll(".heart").length < 15) {
        createHeart();
      }
    }, 1000);
  </script>
</body>
</html>
