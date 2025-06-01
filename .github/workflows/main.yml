<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chúc mừng sinh nhật!</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: black;
    }
    canvas {
      position: absolute;
      top: 0;
      left: 0;
    }
    .message {
      position: absolute;
      top: 40%;
      width: 100%;
      text-align: center;
      font-size: 3em;
      font-weight: bold;
      font-family: 'Comic Sans MS', cursive;
      animation: colorChange 4s infinite;
      z-index: 10;
    }
    @keyframes colorChange {
      0% { color: red; }
      25% { color: orange; }
      50% { color: yellow; }
      75% { color: green; }
      100% { color: violet; }
    }
  </style>
</head>
<body>
  <canvas id="stars"></canvas>
  <div class="message">Chúc fen sinh nhật vui vẻ!</div>
  <audio autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/16/audio_400d0400e5.mp3?filename=happy-birthday-to-you-13267.mp3" type="audio/mpeg">
  </audio>
  <script>
    const canvas = document.getElementById('stars');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;const stars = [];
for (let i = 0; i < 200; i++) {
  stars.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    r: Math.random() * 2,
    alpha: Math.random(),
    dAlpha: Math.random() * 0.02
  });
}

const planets = [
  { radius: 10, dist: 100, angle: 0, speed: 0.01, color: 'orange' },
  { radius: 15, dist: 180, angle: Math.PI / 2, speed: 0.007, color: 'lightblue' },
  { radius: 8, dist: 250, angle: Math.PI, speed: 0.005, color: 'violet' }
];

const fireworks = [];

function drawFirework(x, y, color) {
  for (let i = 0; i < 20; i++) {
    fireworks.push({
      x: x,
      y: y,
      vx: Math.cos((Math.PI * 2) * i / 20) * (Math.random() * 3 + 2),
      vy: Math.sin((Math.PI * 2) * i / 20) * (Math.random() * 3 + 2),
      alpha: 1,
      color: color
    });
  }
}

function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Stars
  for (const s of stars) {
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255, 255, 255, ${s.alpha})`;
    ctx.fill();
    s.alpha += s.dAlpha;
    if (s.alpha <= 0 || s.alpha >= 1) s.dAlpha *= -1;
  }

  // Planets
  const cx = canvas.width / 2;
  const cy = canvas.height / 2;
  for (const p of planets) {
    const x = cx + Math.cos(p.angle) * p.dist;
    const y = cy + Math.sin(p.angle) * p.dist;
    ctx.beginPath();
    ctx.arc(x, y, p.radius, 0, Math.PI * 2);
    ctx.fillStyle = p.color;
    ctx.fill();
    p.angle += p.speed;
  }

  // Fireworks
  for (let i = fireworks.length - 1; i >= 0; i--) {
    const f = fireworks[i];
    ctx.beginPath();
    ctx.arc(f.x, f.y, 3, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(${f.color}, ${f.alpha})`;
    ctx.fill();
    f.x += f.vx;
    f.y += f.vy;
    f.alpha -= 0.02;
    if (f.alpha <= 0) fireworks.splice(i, 1);
  }

  requestAnimationFrame(animate);
}

animate();

setInterval(() => {
  const x = Math.random() * canvas.width;
  const y = Math.random() * canvas.height / 2;
  const color = `${Math.floor(Math.random()*255)},${Math.floor(Math.random()*255)},${Math.floor(Math.random()*255)}`;
  drawFirework(x, y, color);
}, 1000);

window.addEventListener('resize', () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});

  </script>
</body>
</html>
