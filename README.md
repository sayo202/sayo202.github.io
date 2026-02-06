
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
    background: radial-gradient(circle, #ff7eb3, #ff758c);
    font-family: 'Comic Sans MS', cursive;
  }

  .hearts {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
  }

  .heart {
    position: absolute;
    font-size: 32px;
    animation: float 6s linear infinite;
  }

  @keyframes float {
    from {
      transform: translateY(100vh) scale(1);
      opacity: 1;
    }
    to {
      transform: translateY(-10vh) scale(1.6);
      opacity: 0;
    }
  }

  .card {
    z-index: 1;
    background: rgba(255,255,255,0.25);
    backdrop-filter: blur(12px);
    padding: 40px 60px;
    border-radius: 30px;
    text-align: center;
    box-shadow: 0 30px 60px rgba(0,0,0,0.3);
  }

  h1 {
    font-size: 50px;
    color: white;
    text-shadow: 0 0 20px #ff2e63;
    margin-bottom: 40px;
  }

  .buttons {
    position: relative;
    width: 420px;
    height: 220px;
    margin: auto;
  }

  button {
    position: absolute;
    font-size: 26px;
    padding: 16px 34px;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    transition: transform 0.15s ease;
  }

  #yes {
    background: #ff2e63;
    color: white;
  }

  #no {
    right: 20px;
    bottom: 20px;
    background: white;
    color: #ff2e63;
  }

  .shake {
    animation: shake 0.25s;
  }

  @keyframes shake {
    0% { transform: translate(0,0); }
    25% { transform: translate(-4px,4px); }
    50% { transform: translate(4px,-4px); }
    75% { transform: translate(-4px,-4px); }
    100% { transform: translate(0,0); }
  }
</style>
</head>

<body>

<div class="hearts"></div>

<div class="card">
  <h1> George do you have a val? 💖</h1>

  <div class="buttons">
    <button id="yes">Yes 💘</button>
    <button id="no">No 💔</button>
  </div>
</div>

<script>
  const hearts = document.querySelector('.hearts');
  const yesBtn = document.getElementById('yes');
  const container = document.querySelector('.buttons');

  let chaos = 1;

  // Floating hearts
  setInterval(() => {
    const h = document.createElement('div');
    h.className = 'heart';
    h.innerText = '💖';
    h.style.left = Math.random() * 100 + 'vw';
    h.style.animationDuration = 4 + Math.random() * 4 + 's';
    hearts.appendChild(h);
    setTimeout(() => h.remove(), 8000);
  }, 250);

  function moveYes() {
    const c = container.getBoundingClientRect();
    const b = yesBtn.getBoundingClientRect();

    const maxX = c.width - b.width;
    const maxY = c.height - b.height;

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    yesBtn.style.left = x + 'px';
    yesBtn.style.top = y + 'px';

    chaos += 0.3;
    yesBtn.classList.add('shake');
    setTimeout(() => yesBtn.classList.remove('shake'), 250);
  }

  // Dodge on attempted click
  yesBtn.addEventListener('mousedown', moveYes);
  yesBtn.addEventListener('touchstart', moveYes);

  // Start random
  moveYes();

  // NO button destiny
  document.getElementById('no').addEventListener('click', () => {
    document.body.innerHTML = `
      <div style="
        display:flex;
        align-items:center;
        justify-content:center;
        height:100vh;
        background:#ff2e63;
        color:white;
        font-size:60px;
        text-align:center;
        font-family:'Comic Sans MS', cursive;
      ">
        TOO BAD 😌💖<br>
        of course you dont  💘
      </div>
    `;
  });
</script>

</body>
</html>
