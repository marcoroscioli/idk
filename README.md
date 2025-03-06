<!DOCTYPE html>
<html>
<head>
  <title>My Game Website</title>
</head>
<body>

  <h1>Welcome to my Game! How to play: You use your cursor / mouse to move the red cube side to side. Each blue square = 1 point. each circle = - 1 life. CAUTION YOU ONLY HAVE 3 LIVES. </h1>

  <div id="game-container">
    <<!DOCTYPE html>
<html>
<head>
  
  </script>
</body>
</html>>
  </div>

  <script src="<!DOCTYPE html>
<html>
<head>
<title>Catch the Falling Objects!</title>
<style>
#bucket {
  width: 100px;
  height: 50px;
  background-color: red;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}
.object {
  width: 30px;
  height: 30px;
  background-color: blue;
  position: absolute;
}
.death-object {
  width: 20px;
  height: 20px;
  background-color: black;
  position: absolute;
  border-radius: 50%; /* Makes it a circle */
}
</style>
</head>
<body>

<div id="bucket"></div>
<p>Score: <span id="score">0</span></p>
<p>Lives: <span id="lives">3</span></p>

<script>
const bucket = document.getElementById('bucket');
const scoreDisplay = document.getElementById('score');
const livesDisplay = document.getElementById('lives');
let score = 0;
let lives = 3;
let bucketX = window.innerWidth / 2 - bucket.offsetWidth / 2; //Initial position

function isCollision(a, b) {
  const aRect = a.getBoundingClientRect();
  const bRect = b.getBoundingClientRect();
  return !(aRect.right < bRect.left || aRect.left > bRect.right || aRect.bottom < bRect.top || aRect.top > bRect.bottom);
}

function createObject() {
  const object = document.createElement('div');
  object.classList.add('object');
  const x = Math.random() * (window.innerWidth - 30);
  object.style.left = x + 'px';
  object.style.top = '-30px';
  document.body.appendChild(object);

  let y = 0;
  const intervalId = setInterval(() => {
    y += 2;
    object.style.top = y + 'px';
    if (y > window.innerHeight) {
      clearInterval(intervalId);
      document.body.removeChild(object);
    }
    if (isCollision(object, bucket)) {
      clearInterval(intervalId);
      document.body.removeChild(object);
      score++;
      scoreDisplay.textContent = score;
    }
  }, 20);
}

function createDeathObject() {
  const object = document.createElement('div');
  object.classList.add('death-object');
  const x = Math.random() * (window.innerWidth - 20);
  object.style.left = x + 'px';
  object.style.top = '-20px';
  document.body.appendChild(object);

  let y = 0;
  const intervalId = setInterval(() => {
    y += 2;
    object.style.top = y + 'px';
    if (y > window.innerHeight) {
      clearInterval(intervalId);
      document.body.removeChild(object);
    }
    if (isCollision(object, bucket)) {
      clearInterval(intervalId);
      document.body.removeChild(object);
      lives--;
      livesDisplay.textContent = lives;
      if (lives === 0) {
        alert('Game Over!');
      }
    }
  }, 20);
}

function moveBucket(e) {
  bucketX += e.movementX; //Change in mouse position
  bucketX = Math.max(0, Math.min(bucketX, window.innerWidth - bucket.offsetWidth)); //Keep bucket on screen
  bucket.style.left = bucketX + 'px';
}

document.addEventListener('mousemove', moveBucket);


setInterval(createObject, 1000);
setInterval(createDeathObject, 1500);
</script>

</body>
</html>"></script> </body>
</html>
