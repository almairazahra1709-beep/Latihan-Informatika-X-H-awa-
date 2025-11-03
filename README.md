<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🏍️ Motor Race Pro - Sederhana</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="game-container">
        <div id="road">
            <div id="motorcycle"></div>
            <div id="obstacle"></div>
        </div>
    </div>
    
    <div id="controls">
        <p>Gunakan tombol **Atas** (Gas) dan **Bawah** (Rem) untuk mengontrol motor.</p>
        <p>Jaga skor tetap tinggi!</p>
        <p>Skor: <span id="score">0</span></p>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #333;
    color: white;
    margin: 0;
    padding-top: 20px;
}

#game-container {
    width: 600px;
    height: 300px;
    border: 5px solid #fff;
    overflow: hidden; /* Penting agar motor dan rintangan tidak keluar dari batas */
    background-color: #555;
    position: relative;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
}

#road {
    width: 100%;
    height: 100%;
    position: relative;
}

/* Motor */
#motorcycle {
    width: 40px;
    height: 30px;
    background-color: #FF5722; /* Merah Oranye */
    position: absolute;
    bottom: 10px;
    left: 50px; /* Posisi awal motor */
    border-radius: 5px;
    transition: transform 0.05s ease-out; /* Untuk animasi gas/rem lebih halus */
}

/* Rintangan */
#obstacle {
    width: 20px;
    height: 40px;
    background-color: #4CAF50; /* Hijau */
    position: absolute;
    bottom: 10px;
    right: -20px; /* Mulai di luar layar */
    border-radius: 5px;
    transition: background-color 0.2s;
}

#controls {
    margin-top: 20px;
    text-align: center;
}

#score {
    font-size: 1.5em;
    font-weight: bold;
    color: #FFEB3B; /* Kuning */
}
// Pengaturan Game
const GAME_SPEED = 1000 / 60; // Refresh rate 60 FPS
const ROAD_WIDTH = 600;

// Kecepatan
let currentSpeed = 0; // Kecepatan horizontal motor
let acceleration = 0.5;
let maxSpeed = 8;

// DOM Elements
const motor = document.getElementById('motorcycle');
const obstacle = document.getElementById('obstacle');
const scoreDisplay = document.getElementById('score');

// Variabel Game
let score = 0;
let obstacleX = ROAD_WIDTH;
let isGameOver = false;

// --- KONTROL MOTOR ---
document.addEventListener('keydown', (e) => {
    if (isGameOver) return;

    if (e.key === 'ArrowUp') {
        // Gas: Meningkatkan kecepatan
        currentSpeed = Math.min(currentSpeed + acceleration, maxSpeed);
        motor.style.transform = 'scaleY(1.1)'; // Efek sedikit 'menekuk'
    } else if (e.key === 'ArrowDown') {
        // Rem: Mengurangi kecepatan
        currentSpeed = Math.max(currentSpeed - acceleration * 1.5, 0); // Rem lebih kuat
        motor.style.transform = 'scaleY(0.9)'; // Efek sedikit 'memendek'
    }
});

document.addEventListener('keyup', (e) => {
    // Reset efek visual saat tombol dilepas
    if (e.key === 'ArrowUp' || e.key === 'ArrowDown') {
        motor.style.transform = 'scaleY(1)';
    }
});

// --- LOGIKA PERGERAKAN ---
function updateGame() {
    if (isGameOver) return;

    // 1. Gerakkan Rintangan (berdasarkan kecepatan motor)
    // Motor yang lebih cepat membuat rintangan bergerak lebih cepat ke kiri
    obstacleX -= currentSpeed;
    
    // 2. Tampilkan Rintangan
    obstacle.style.right = `${ROAD_WIDTH - obstacleX}px`;

    // 3. Atur Ulang Rintangan
    if (obstacleX < -20) {
        // Rintangan melewati motor
        obstacleX = ROAD_WIDTH + Math.random() * 200; // Jarak acak
        score++;
        scoreDisplay.textContent = score;
    }

    // 4. Deteksi Tabrakan
    const motorLeft = motor.offsetLeft;
    const motorRight = motorLeft + motor.offsetWidth;
    const motorBottom = motor.offsetTop + motor.offsetHeight;
    
    const obstacleLeft = obstacle.offsetLeft;
    const obstacleRight = obstacleLeft + obstacle.offsetWidth;

    // Cek tabrakan berdasarkan posisi horizontal (kita anggap posisi Y-nya sama)
    if (motorRight > obstacleLeft && motorLeft < obstacleRight) {
        // Hanya cek jika rintangan berada di dekat motor
        if (obstacleX > 0 && obstacleX < ROAD_WIDTH) { 
            gameOver();
            return;
        }
    }
    
    // 5. Loop Game
    requestAnimationFrame(updateGame);
}

// --- FUNGSI GAME OVER ---
function gameOver() {
    isGameOver = true;
    obstacle.style.backgroundColor = '#F44336'; // Rintangan menjadi merah
    motor.style.backgroundColor = '#E91E63'; // Motor menjadi ungu
    alert(`Game Over! Skor Akhir Anda: ${score}`);
}

// --- INICIALISASI ---
function init() {
    // Mulai loop game
    requestAnimationFrame(updateGame);
}

// Jalankan inisialisasi setelah DOM dimuat
window.onload = init;
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🏍️ Motor Race Pro - Sederhana</title> 
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <a href="https://contoh-url-anda.com" style="text-decoration: none; color: inherit;">
        <div id="controls"> 
            <p>Gunakan tombol **Atas** (Gas) dan **Bawah** (Rem) untuk mengontrol motor.</p> 
            <p>Jaga skor tetap tinggi!</p> 
            <p>Skor: <span id="score">0</span></p> 
        </div> 
    </a>
    
    <script src="script.js"></script>
</body>
</html>
// script.js

// ... (Kode pengaturan dan variabel game di atas tetap sama) ...

// DOM Elements baru
const gasButton = document.getElementById('gasButton');
const brakeButton = document.getElementById('brakeButton');

// --- FUNGSI KONTROL MOTOR ---
function applyGas() {
    if (isGameOver) return;
    currentSpeed = Math.min(currentSpeed + acceleration, maxSpeed);
    motor.style.transform = 'scaleY(1.1)'; // Efek sedikit 'menekuk'
}

function applyBrake() {
    if (isGameOver) return;
    currentSpeed = Math.max(currentSpeed - acceleration * 1.5, 0); // Rem lebih kuat
    motor.style.transform = 'scaleY(0.9)'; // Efek sedikit 'memendek'
}

function resetMotorVisual() {
    motor.style.transform = 'scaleY(1)';
}

// --- KONTROL KEYBOARD (seperti kode Anda) ---
document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowUp') {
        applyGas();
    } else if (e.key === 'ArrowDown') {
        applyBrake();
    }
});

document.addEventListener('keyup', (e) => {
    if (e.key === 'ArrowUp' || e.key === 'ArrowDown') {
        resetMotorVisual();
    }
});

// --- KONTROL KLIK TOMBOL HTML (Perubahan utama) ---
// Ketika tombol GAS diklik
gasButton.addEventListener('mousedown', applyGas); 
gasButton.addEventListener('mouseup', resetMotorVisual); 
gasButton.addEventListener('mouseleave', resetMotorVisual); // Penting untuk mobile/klik tahan

// Ketika tombol REM diklik
brakeButton.addEventListener('mousedown', applyBrake);
brakeButton.addEventListener('mouseup', resetMotorVisual);
brakeButton.addEventListener('mouseleave', resetMotorVisual);

// ... (Sisa fungsi updateGame() dan gameOver() tetap sama) ...

