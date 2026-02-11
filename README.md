# vv
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Be My Valentine</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff758c, #ff7eb3, #ffd1dc);
  font-family: "Poppins", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  text-align: center;
}

.container {
  padding: 20px;
  z-index: 2;
}

h1 {
  color: white;
  font-size: 1.8rem;
}

button {
  padding: 12px 22px;
  margin: 10px;
  font-size: 16px;
  border: none;
  border-radius: 25px;
  cursor: pointer;
}

#yesBtn {
  background: #ff4d6d;
  color: white;
}

#noBtn {
  background: #444;
  color: white;
  position: absolute;
}

.message {
  color: white;
  font-size: 1.4rem;
  margin-top: 15px;
  display: none;
}

/* Flower rain */
.flower {
  position: absolute;
  font-size: 24px;
  animation: fall linear forwards;
}

@keyframes fall {
  to {
    transform: translateY(100vh);
    opacity: 0;
  }
}

/* Firework */
.firework {
  position: absolute;
  font-size: 18px;
  animation: explode 1s ease-out forwards;
}

@keyframes explode {
  to {
    transform: translate(var(--x), var(--y));
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="container">
  <h1>XYZ, will you be my Valentine? 💕</h1>
  <button id="yesBtn">Yes ❤️</button>
  <button id="noBtn">No 😜</button>

  <div class="message" id="msg">
    You are the most pretty girl in the world who said yes to spend Valentine with ABC boy 💖🌸
  </div>
</div>

<!-- Background Music -->
<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
const noBtn = document.getElementById("noBtn");
const yesBtn = document.getElementById("yesBtn");
const msg = document.getElementById("msg");
const music = document.getElementById("bgMusic");

// Move NO button
function moveNoButton() {
  const x = Math.random() * (window.innerWidth - 80);
  const y = Math.random() * (window.innerHeight - 40);
  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";
}

noBtn.addEventListener("mouseover", moveNoButton);
noBtn.addEventListener("touchstart", moveNoButton);

// YES click
yesBtn.addEventListener("click", () => {
  msg.style.display = "block";
  flowerRain();
  fireworks();
  music.play();
});

// Flower rain
function flowerRain() {
  setInterval(() => {
    const flower = document.createElement("div");
    flower.className = "flower";
    flower.innerHTML = "🌸";
    flower.style.left = Math.random() * window.innerWidth + "px";
    flower.style.animationDuration = (3 + Math.random() * 3) + "s";
    document.body.appendChild(flower);

    setTimeout(() => flower.remove(), 6000);
  }, 200);
}

// Fireworks
function fireworks() {
  for (let i = 0; i < 40; i++) {
    const fw = document.createElement("div");
    fw.className = "firework";
    fw.innerHTML = "✨";
    fw.style.left = "50%";
    fw.style.top = "50%";
    fw.style.setProperty("--x", (Math.random() - 0.5) * 300 + "px");
    fw.style.setProperty("--y", (Math.random() - 0.5) * 300 + "px");
    document.body.appendChild(fw);

    setTimeout(() => fw.remove(), 1000);
  }
}
</script>

</body>
</html>
