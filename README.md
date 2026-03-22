<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Love Heart</title>
<style>
body {
  margin: 0;
  background: black;
  overflow: hidden;
}

canvas {
  display: block;
}
</style>
</head>
<body>

<canvas id="c"></canvas>

<script>
const canvas = document.getElementById("c");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let t = 0;

function heart(t) {
  let x = 10 * Math.pow(Math.sin(t), 3);
  let y = 10 * Math.cos(t) - 5 * Math.cos(2*t) - 2 * Math.cos(3*t) - Math.cos(4*t);
  return {x, y};
}

function draw() {
  ctx.fillStyle = "rgba(0,0,0,0.9)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "red";
  ctx.font = "10px Arial";

  for (let i = 0; i < Math.PI * 2; i += 0.05) {
    let p = heart(i + t);

    let x = canvas.width / 2 + p.x * 15;
    let y = canvas.height / 2 - p.y * 15;

    ctx.fillText(" I LOVE YOU DIMA ", x, y);
  }

  t += 0.09;
  requestAnimationFrame(draw);
}

draw();
</script>

</body>
</html>
