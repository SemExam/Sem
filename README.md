PACMAN

let pos = 0;
const pageWidth = window.innerWidth;
const pacArray = [
  ["./images/PacMan1.png", "./images/PacMan2.png"],
  ["./images/PacMan3.png", "./images/PacMan4.png"],
];
let direction = 0;
let focus = 0;

function Move() {
  let img = document.getElementById('pacman');
  let imgWidth = img.width;
  focus = (focus + 1) % 2;
  direction = checkPageBounds(direction, imgWidth, pos, pageWidth);
  img.src = pacArray[direction][focus];
  pos += (direction ? -20 : 20);
  img.style.left = pos + 'px';
}

function checkPageBounds(direction, imgWidth, pos, pageWidth) {
  if (direction === 0 && pos + imgWidth > pageWidth) direction = 1;
  if (direction === 1 && pos < 0) direction = 0;
  return direction;
}

setInterval(Move, 200);


MOVING BALL



const ball1 = { element: document.getElementById('ball1'), dx: 2, dy: 2 };
const ball2 = { element: document.getElementById('ball2'), dx: 3, dy: 3 };
const ball3 = { element: document.getElementById('ball3'), dx: 4, dy: 4 };

function moveTo(ball, x, y) {
  ball.element.style.left = x + 'px';
  ball.element.style.top = y + 'px';
}

function changeDirectionIfNecessary(ball, x, y) {
  const screenWidth = window.innerWidth;
  const screenHeight = window.innerHeight;
  if (x <= 0 || x >= screenWidth - 50) ball.dx *= -1;
  if (y <= 0 || y >= screenHeight - 50) ball.dy *= -1;
}

function update(ball, x, y) {
  moveTo(ball, x, y);
  changeDirectionIfNecessary(ball, x, y);
  x += ball.dx;
  y += ball.dy;
  setTimeout(() => update(ball, x, y), 16);
}

update(ball1, 70, 0);
update(ball2, 20, 200);
update(ball3, 300, 330);

const setBg = () => {
  const randomColor = Math.floor(Math.random() * 16777215).toString(16);
  document.body.style.backgroundColor = "#" + randomColor;
  color.innerHTML = "#" + randomColor;
};

setBg();
// genNew.addEventListener("click", setBg);
