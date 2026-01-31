# Tap-mania--Game
<!DOCTYPE html>
<html>
<head>
  <title>Tap Mania Game</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      background: linear-gradient(135deg, #111, #222);
      color: white;
      font-family: Arial;
      overflow: hidden;
      text-align: center;
    }
    #top {
      padding: 10px;
      font-size: 18px;
      display: flex;
      justify-content: space-around;
    }
    #box {
      width: 70px;
      height: 70px;
      background: red;
      position: absolute;
      border-radius: 15px;
    }
    #gameOver {
      display: none;
      position: fixed;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 26px;
    }
    button {
      padding: 10px 20px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      margin-top: 15px;
    }
  </style>
</head>
<body>

<div id="top">
  <div>⏱ Time: <span id="time">30</span></div>
  <div>🔥 Score: <span id="score">0</span></div>
</div>

<div id="box"></div>

<div id="gameOver">
  <div>😵 Game Over!</div>
  <div>Your Score: <span id="finalScore"></span></div>
  <button onclick="location.reload()">Play Again</button>
</div>

<script>
  let box = document.getElementById("box");
  let score = 0;
  let time = 30;
  let speed = 800;

  function moveBox() {
    let x = Math.random() * (window.innerWidth - 80);
    let y = Math.random() * (window.innerHeight - 120) + 60;
    box.style.left = x + "px";
    box.style.top = y + "px";
  }

  box.onclick = () => {
    score++;
    document.getElementById("score").innerText = score;
    speed = speed - 30; // speed increase
    if (speed < 200) speed = 200;
    moveBox();
  };

  let timer = setInterval(() => {
    time--;
    document.getElementById("time").innerText = time;
    if (time <= 0) {
      clearInterval(timer);
      box.style.display = "none";
      document.getElementById("finalScore").innerText = score;
      document.getElementById("gameOver").style.display = "block";
    }
  }, 1000);

  moveBox();
  setInterval(moveBox, speed);
</script>

</body>
</html>
