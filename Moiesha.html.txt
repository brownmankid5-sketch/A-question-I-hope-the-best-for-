<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Girl ❤️</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            /* Background Image with a pink tint */
            background: linear-gradient(rgba(255, 192, 203, 0.6), rgba(255, 192, 203, 0.6)), url('us.jpg');
            background-size: cover;
            background-position: center;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            text-align: center;
        }

        .container {
            background-color: rgba(255, 255, 255, 0.85);
            padding: 2.5rem;
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            z-index: 10;
            border: 3px solid #ff4081;
        }

        h1 {
            color: #d81b60;
            margin-bottom: 1.5rem;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            height: 60px; /* Maintains space when No disappears */
            align-items: center;
        }

        button {
            padding: 12px 35px;
            font-size: 1.1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: 0.3s;
        }

        #yesBtn {
            background-color: #ff4081;
            color: white;
            box-shadow: 0 4px 15px rgba(255, 64, 129, 0.4);
        }

        #noBtn {
            background-color: #555;
            color: white;
        }

        /* Raining Hearts */
        .heart {
            position: fixed;
            top: -10%;
            color: #ff4081;
            font-size: 1.5rem;
            user-select: none;
            z-index: 1;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); }
        }

        /* Success Screen */
        #success-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(216, 27, 96, 0.95);
            color: white;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 100;
        }

        /* Music info tag */
        .music-tag {
            position: fixed;
            bottom: 20px;
            left: 20px;
            background: rgba(0,0,0,0.5);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            z-index: 5;
        }
    </style>
</head>
<body>

    <audio id="loveSong" loop>
        <source src="scrubs.mp3" type="audio/mpeg">
    </audio>

    <div class="music-tag">🎵 Lil Durk - Scrubs</div>

    <div class="container">
        <h1>Will you be my Valentine? 🌹</h1>
        <div class="buttons">
            <button id="yesBtn" onclick="celebrate()">YES</button>
            <button id="noBtn" onmouseover="hideNo()">NO</button>
        </div>
    </div>

    <div id="success-screen">
        <h1 style="font-size: 4rem;">I LOVE YOU! ❤️</h1>
        <p>You're stuck with me now.</p>
    </div>

    <script>
        const song = document.getElementById('loveSong');

        // Start hearts
        setInterval(createHeart, 300);

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }

        // Logic to hide NO and start music
        function hideNo() {
            document.getElementById('noBtn').style.display = 'none';
            // Play music when she tries to hit No (workaround for browser autoplay blocks)
            song.play(); 
        }

        function celebrate() {
            song.play(); // Ensure music plays on Yes click too
            document.getElementById('success-screen').style.display = 'flex';
        }
    </script>
</body>
</html>
