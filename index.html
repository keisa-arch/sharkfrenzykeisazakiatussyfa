<?php
session_start();
?>
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shark Frenzy - Mega Bomb Update</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Courier New', Courier, monospace; }
        body { background: #010610; display: flex; justify-content: center; align-items: center; min-height: 100vh; color: #fff; overflow: hidden; }
        
        #game-container { 
            position: relative; width: 800px; height: 500px; 
            border: 4px solid #00e5ff; border-radius: 12px; overflow: hidden; 
            box-shadow: 0 0 50px rgba(0, 229, 255, 0.4); background: #00122a;
        }
        canvas { display: block; width: 100%; height: 100%; }
        
        .overlay { 
            position: absolute; top: 0; left: 0; width: 100%; height: 100%; 
            display: flex; flex-direction: column; justify-content: center; align-items: center; 
            background: rgba(1, 10, 26, 0.88); backdrop-filter: blur(5px); z-index: 10; 
        }
        .hidden { display: none !important; }
        
        h1 { font-size: 38px; text-shadow: 4px 4px 0px #005c97, 0 0 20px #00e5ff; margin-bottom: 15px; }
        h2 { font-size: 22px; color: #ffd54f; margin-bottom: 15px; }
        
        .btn { 
            padding: 12px 30px; font-size: 16px; font-weight: bold; color: #010a1a; 
            background: #ffb300; border: 3px solid #fff; cursor: pointer; 
            box-shadow: 4px 4px 0px #000; margin: 6px; width: 220px; transition: 0.1s; text-align: center;
        }
        .btn:hover { background: #ffd54f; transform: translate(-2px, -2px); box-shadow: 6px 6px 0px #000; }
        
        .player-selector { display: flex; gap: 15px; margin-bottom: 20px; }
        .player-card { 
            border: 3px solid #546e7a; background: rgba(255,255,255,0.05); padding: 10px; 
            border-radius: 8px; text-align: center; cursor: pointer; width: 140px;
            display: flex; flex-direction: column; align-items: center;
        }
        .player-card.active { border-color: #00e5ff; background: rgba(0, 229, 255, 0.15); box-shadow: 0 0 15px #00e5ff; }
        .player-card img { width: 80px; height: 45px; object-fit: contain; margin-bottom: 8px; }

        .hud { 
            position: absolute; top: 15px; left: 20px; right: 20px; 
            display: flex; justify-content: space-between; align-items: center; 
            pointer-events: none; z-index: 5; text-shadow: 2px 2px 0px #000;
        }
        .hud-item { font-size: 16px; font-weight: bold; color: #ffd54f; }
        .energy-bar-bg { width: 140px; height: 16px; background: #000; border: 2px solid #fff; overflow: hidden; }
        .energy-bar-fill { width: 100%; height: 100%; background: linear-gradient(90deg, #ff1744, #00e676); transition: width 0.1s linear; }
    </style>
</head>
<body>

<div id="game-container">
    <canvas id="gameCanvas" width="800" height="500"></canvas>

    <div id="hud" class="hud hidden">
        <div class="hud-item" style="color: #00e5ff;">LEVEL: <span id="levelText">1</span></div>
        <div class="hud-item">SKOR: <span id="scoreText">0</span>/<span id="targetScoreText">150</span></div>
        <div class="hud-item" style="color: #ff5252;">WAKTU: <span id="timeText">90</span>s</div>
        <div style="display: flex; align-items: center; gap: 8px;">
            <span style="font-size:12px; font-weight:bold;">ENERGY</span>
            <div class="energy-bar-bg"><div id="energyFill" class="energy-bar-fill"></div></div>
        </div>
    </div>

    <div id="mainMenu" class="overlay">
        <h1>SHARK FRENZY</h1>
        <button class="btn" onclick="startGame()">PLAY</button>
        <button class="btn" onclick="showScreen('playerMenu')">PILIH PLAYER</button>
    </div>

    <div id="playerMenu" class="overlay hidden">
        <h2>PILIH KARAKTER</h2>
        <div class="player-selector">
            <div class="player-card active" id="card-default" onclick="selectShark('default', 5)">
                <img src="hiu.png" alt="Hiu Default">
                <p style="font-weight:bold; color:#00e5ff;">DEFAULT</p>
            </div>
            <div class="player-card" id="card-red" onclick="selectShark('red', 6.5)">
                <img src="hiu_merah.png" alt="Hiu Merah">
                <p style="font-weight:bold; color:#ff1744;">RED SHARK</p>
            </div>
            <div class="player-card" id="card-gold" onclick="selectShark('gold', 4)">
                <img src="hiu_gold.png" alt="Hiu Gold">
                <p style="font-weight:bold; color:#ffd54f;">GOLD SHARK</p>
            </div>
        </div>
        <button class="btn" onclick="showScreen('mainMenu')">KEMBALI</button>
    </div>

    <div id="levelClearMenu" class="overlay hidden">
        <h1 style="color:#00e676;">LEVEL SELESAI!</h1>
        <p style="font-size: 18px; margin-bottom: 20px;">Menuju Level <span id="nextLevelText">2</span>...</p>
        <button class="btn" onclick="nextLevel()">LANJUT LEVEL</button>
    </div>

    <div id="gameOverMenu" class="overlay hidden">
        <h1 style="color:#ff1744;" id="gameOverTitle">GAME OVER</h1>
        <p style="font-size: 18px; margin-bottom: 15px;" id="gameOverReason">Energi Kamu Habis!</p>
        <p style="font-size: 18px; margin-bottom: 20px;">SKOR AKHIR: <span id="finalScore">0</span></p>
        <button class="btn" onclick="startGame()">MAIN LAGI</button>
        <button class="btn" style="background:#00bcd4;" onclick="showScreen('mainMenu')">MENU UTAMA</button>
    </div>
</div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

let audioCtx = null;
function initAudio() {
    try {
        if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    } catch (e) {}
}

function playEatSound() {
    if (!audioCtx) return;
    try {
        if (audioCtx.state === 'suspended') audioCtx.resume();
        const now = audioCtx.currentTime;
        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.type = 'triangle';
        osc.frequency.setValueAtTime(320, now);
        osc.frequency.exponentialRampToValueAtTime(60, now + 0.12);
        gain.gain.setValueAtTime(0.8, now);
        gain.gain.exponentialRampToValueAtTime(0.01, now + 0.12);
        osc.connect(gain); gain.connect(audioCtx.destination);
        osc.start(now); osc.stop(now + 0.12);
    } catch (e) {}
}

function removeWhiteBackground(img, threshold = 220) {
    const offCanvas = document.createElement('canvas');
    offCanvas.width = img.width;
    offCanvas.height = img.height;
    const offCtx = offCanvas.getContext('2d');
    
    offCtx.drawImage(img, 0, 0);
    const imgData = offCtx.getImageData(0, 0, offCanvas.width, offCanvas.height);
    const data = imgData.data;

    for (let i = 0; i < data.length; i += 4) {
        if (data[i] >= threshold && data[i+1] >= threshold && data[i+2] >= threshold) {
            data[i + 3] = 0;
        }
    }

    offCtx.putImageData(imgData, 0, 0);
    return offCanvas;
}

const bgImage = new Image();
let bgLoaded = false;
bgImage.onload = () => { bgLoaded = true; draw(); };
bgImage.src = 'background(2).jpeg';

const sharkImages = {};
const sharkSources = { 'default': 'hiu.png', 'red': 'hiu_merah.png', 'gold': 'hiu_gold.png' };
for (let key in sharkSources) {
    sharkImages[key] = new Image();
    sharkImages[key].src = sharkSources[key];
}

let bombCanvas = null;
const bombImage = new Image();
bombImage.onload = () => { 
    bombCanvas = removeWhiteBackground(bombImage, 215); 
};
bombImage.src = 'bomb.png';

const fishSources = [
    'fish1.png', 'fish2.png', 'fish3.png', 
    'fish4.png', 'fish5.png', 'fish6.png', 'fish7.png'
];
const fishCanvases = [];

fishSources.forEach((src) => {
    const img = new Image();
    img.onload = () => {
        const cleanedCanvas = removeWhiteBackground(img, 230);
        fishCanvases.push(cleanedCanvas);
    };
    img.src = src;
});

// PENGATURAN DENGAN JUMLAH BOM JAUH LEBIH BANYAK
const levelConfig = [
    { level: 1, targetScore: 150, timeLimit: 90,  fishCount: 15, mineCount: 10, fishSpeedMin: 2.0, fishSpeedMax: 4.5, drainRate: 0.02 },
    { level: 2, targetScore: 350, timeLimit: 100, fishCount: 18, mineCount: 16, fishSpeedMin: 2.5, fishSpeedMax: 5.0, drainRate: 0.025 }
];

let currentLevelIdx = 0;
let gameState = 'MENU';
let score = 0; 
let energy = 100;
let timeRemaining = 0;
let timerInterval = null;
let keys = {};
let currentSharkConfig = { key: 'default', speed: 5 };

let bubbles = Array.from({length: 20}, () => ({
    x: Math.random() * canvas.width, y: Math.random() * canvas.height,
    r: Math.random() * 3 + 1, speed: Math.random() * 1 + 0.5
}));

window.addEventListener('keydown', e => keys[e.key] = true);
window.addEventListener('keyup', e => keys[e.key] = false);

function showScreen(screenId) {
    clearInterval(timerInterval);
    document.querySelectorAll('.overlay').forEach(el => el.classList.add('hidden'));
    document.getElementById(screenId).classList.remove('hidden');
    document.getElementById('hud').classList.add('hidden');
    gameState = 'MENU'; draw();
}

function selectShark(key, speed) {
    currentSharkConfig.key = key;
    currentSharkConfig.speed = speed;
    document.querySelectorAll('.player-card').forEach(c => c.classList.remove('active'));
    document.getElementById('card-' + key).classList.add('active');
}

class ImageShark {
    constructor() {
        this.width = 130; this.height = 70;
        this.x = 80; this.y = 220;
        this.speed = currentSharkConfig.speed;
        this.imageKey = currentSharkConfig.key;
        this.frame = 0; this.targetAngle = 0;
    }

    update() {
        this.targetAngle = 0;
        let isMoving = false;
        if (keys['ArrowUp'] || keys['w']) { if (this.y > 20) this.y -= this.speed; this.targetAngle = -10; isMoving = true; }
        if (keys['ArrowDown'] || keys['s']) { if (this.y < canvas.height - 75) this.y += this.speed; this.targetAngle = 10; isMoving = true; }
        if (keys['ArrowLeft'] || keys['a']) { if (this.x > 20) this.x -= this.speed; isMoving = true; }
        if (keys['ArrowRight'] || keys['d']) { if (this.x < canvas.width - 130) this.x += this.speed; isMoving = true; }
        this.frame += isMoving ? 0.12 : 0.04;
    }

    triggerEat() { playEatSound(); }

    draw() {
        ctx.save();
        ctx.translate(this.x + this.width / 2, this.y + this.height / 2);
        let tailWiggle = Math.sin(this.frame) * 2;
        ctx.rotate((this.targetAngle + tailWiggle) * Math.PI / 180);

        let activeImg = sharkImages[this.imageKey];
        if (activeImg && activeImg.complete && activeImg.naturalWidth !== 0) {
            let imgAspect = activeImg.width / activeImg.height;
            let drawW = this.width * 1.5; 
            let drawH = drawW / imgAspect;
            ctx.drawImage(activeImg, -drawW / 2, -drawH / 2, drawW, drawH);
        } else {
            ctx.fillStyle = '#ff1744';
            ctx.fillRect(-this.width/2, -this.height/2, this.width, this.height);
        }
        ctx.restore();
    }
}

class ExactCartoonFish {
    constructor(speedMin = 2.0, speedMax = 4.5) { 
        this.speedMin = speedMin;
        this.speedMax = speedMax;
        this.reset(true); 
    }
    reset(initial = false) {
        this.x = initial ? Math.random() * (canvas.width - 200) + 200 : canvas.width + Math.random() * 100;
        this.y = Math.random() * (canvas.height - 120) + 40;
        this.speed = this.speedMin + Math.random() * (this.speedMax - this.speedMin);
        this.fishIndex = Math.floor(Math.random() * fishSources.length);
    }
    update() {
        this.x -= this.speed;
        if (this.x < -60) this.reset();
    }
    draw() {
        ctx.save();
        ctx.translate(this.x, this.y);

        const currentCanvas = fishCanvases[this.fishIndex];
        if (currentCanvas) {
            let drawW = 50;
            let drawH = 40;
            ctx.drawImage(currentCanvas, -drawW / 2, -drawH / 2, drawW, drawH);
        } else {
            ctx.fillStyle = '#ff9800';
            ctx.beginPath();
            ctx.ellipse(0, 0, 15, 10, 0, 0, Math.PI * 2);
            ctx.fill();
        }
        ctx.restore();
    }
}

class Mine {
    constructor() { this.reset(true); }
    reset(initial = false) { 
        // Mengatur urutan jarak spawn bom agar terus bermunculan tiada henti
        this.x = initial ? canvas.width + Math.random() * 1200 : canvas.width + Math.random() * 500; 
        this.y = Math.random() * (canvas.height - 120) + 40; 
        this.speed = 1.5 + Math.random() * 2.3; 
        this.size = 48;
    }
    update() { 
        this.x -= this.speed; 
        if (this.x < -60) this.reset(); 
    }
    draw() {
        if (bombCanvas) {
            ctx.drawImage(bombCanvas, this.x - this.size / 2, this.y - this.size / 2, this.size, this.size);
        } else {
            ctx.fillStyle = '#000'; 
            ctx.beginPath(); 
            ctx.arc(this.x, this.y, 18, 0, Math.PI * 2); 
            ctx.fill();
        }
    }
}

let player = new ImageShark();
let fishes = [];
let mines = [];

function checkCollision(r1, r2) {
    return r1.x < r2.x + r2.w && r1.x + r1.w > r2.x && r1.y < r2.y + r2.h && r1.y + r1.h > r2.y;
}

function drawBackground() {
    if (bgLoaded) { ctx.drawImage(bgImage, 0, 0, canvas.width, canvas.height); } 
    else {
        let grad = ctx.createLinearGradient(0, 0, 0, canvas.height);
        grad.addColorStop(0, '#005c97'); grad.addColorStop(1, '#00122a');
        ctx.fillStyle = grad; ctx.fillRect(0, 0, canvas.width, canvas.height);
    }
    ctx.fillStyle = 'rgba(255, 255, 255, 0.3)';
    bubbles.forEach(b => {
        b.y -= b.speed;
        if (b.y < 0) { b.y = canvas.height; b.x = Math.random() * canvas.width; }
        ctx.beginPath(); ctx.arc(b.x, b.y, b.r, 0, Math.PI * 2); ctx.fill();
    });
}

function startLevel() {
    let cfg = levelConfig[currentLevelIdx] || levelConfig[0];
    timeRemaining = cfg.timeLimit;
    energy = 100; player.x = 80; player.y = 220;

    fishes = Array.from({length: cfg.fishCount}, () => new ExactCartoonFish(cfg.fishSpeedMin, cfg.fishSpeedMax));
    mines = Array.from({length: cfg.mineCount}, () => new Mine());

    document.getElementById('levelText').innerText = cfg.level;
    document.getElementById('targetScoreText').innerText = cfg.targetScore;
    document.getElementById('timeText').innerText = timeRemaining;

    clearInterval(timerInterval);
    timerInterval = setInterval(() => {
        if (gameState === 'PLAYING') {
            timeRemaining--;
            document.getElementById('timeText').innerText = timeRemaining;
            if (timeRemaining <= 0) gameOver("Waktu Habis!");
        }
    }, 1000);

    gameState = 'PLAYING';
    document.querySelectorAll('.overlay').forEach(el => el.classList.add('hidden'));
    document.getElementById('hud').classList.remove('hidden');
    gameLoop();
}

function startGame() {
    initAudio(); 
    score = 0; energy = 100; currentLevelIdx = 0;
    player = new ImageShark();
    startLevel();
}

function gameOver(reason = "Energi Kamu Habis!") {
    gameState = 'GAMEOVER';
    clearInterval(timerInterval);
    document.getElementById('hud').classList.add('hidden');
    document.getElementById('gameOverMenu').classList.remove('hidden');
    document.getElementById('gameOverReason').innerText = reason;
    document.getElementById('finalScore').innerText = score;
}

function gameLoop() {
    if (gameState !== 'PLAYING') return;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();

    let cfg = levelConfig[currentLevelIdx] || levelConfig[0];
    energy -= cfg.drainRate;
    document.getElementById('energyFill').style.width = Math.max(0, energy) + '%';
    document.getElementById('scoreText').innerText = score;

    if (energy <= 0) { gameOver("Energi Kamu Habis!"); return; }

    player.update(); player.draw();

    fishes.forEach(f => {
        f.update(); f.draw();
        if (checkCollision({x: player.x, y: player.y, w: player.width, h: player.height}, {x: f.x - 20, y: f.y - 15, w: 40, h: 30})) {
            score += 10; 
            energy = Math.min(100, energy + 8); 
            player.triggerEat();
            f.reset();
        }
    });

    mines.forEach(m => {
        m.update(); m.draw();
        if (checkCollision({x: player.x, y: player.y, w: player.width, h: player.height}, {x: m.x - 20, y: m.y - 20, w: 40, h: 40})) {
            energy -= 20; m.reset();
        }
    });

    requestAnimationFrame(gameLoop);
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();
}
draw();
</script>
</body>
</html>
