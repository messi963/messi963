const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

let playerX = 180;
const playerWidth = 40;
const playerHeight = 10;

function drawPlayer() {
    ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear canvas
    ctx.fillStyle = 'blue';
    ctx.fillRect(playerX, canvas.height - playerHeight - 10, playerWidth, playerHeight);
}

function updateGame() {
    drawPlayer();
    requestAnimationFrame(updateGame); // Loop the game
}

document.addEventListener('keydown', (event) => {
    if (event.key === 'ArrowLeft' && playerX > 0) {
        playerX -= 10; // Move left
    } else if (event.key === 'ArrowRight' && playerX < canvas.width - playerWidth) {
        playerX += 10; // Move right
    }
});

updateGame();
