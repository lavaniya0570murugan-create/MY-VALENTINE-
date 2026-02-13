<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Favorite Person</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@300;500&display=swap');

        body {
            margin: 0;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, #fce4ec 0%, #f8bbd0 100%);
            font-family: 'Quicksand', sans-serif;
            overflow: hidden;
            position: relative;
        }

        /* Floating Hearts Animation */
        .heart {
            position: absolute;
            color: rgba(255, 77, 109, 0.3);
            animation: float 6s infinite linear;
            z-index: 0;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        .card {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            padding: 3rem;
            border-radius: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            text-align: center;
            z-index: 1;
            max-width: 350px;
            border: 2px solid #fff;
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            color: #d63384;
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        p { color: #666; line-height: 1.6; }

        .btn-container {
            margin-top: 2rem;
            position: relative;
            height: 120px;
        }

        button {
            padding: 12px 30px;
            border-radius: 50px;
            border: none;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Quicksand', sans-serif;
        }

        #yesBtn {
            background: #ff4d6d;
            color: white;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
            font-size: 1.1rem;
        }

        #yesBtn:hover { transform: scale(1.1); background: #ff758f; }

        #noBtn {
            background: white;
            color: #ff4d6d;
            border: 2px solid #ff4d6d;
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
        }

        .hidden { display: none; }

        .celebration h1 { font-size: 3rem; animation: heartbeat 1s infinite; }

        @keyframes heartbeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>

    <div id="heart-bg"></div>

    <div class="card" id="mainCard">
        <h1>Hi Handsome... ✨</h1>
        <p>I wanted to ask you something really important today because you make my heart skip a beat.</p>
        
        <div class="btn-container">
            <button id="yesBtn">Will you be my Valentine?</button>
            <button id="noBtn">No way</button>
        </div>
    </div>

    <div class="card hidden" id="successCard">
        <div class="celebration">
            <h1>YES! ❤️</h1>
            <p>You just made me the luckiest person alive. I can't wait to spend tomorrow with you!</p>
            <p style="font-size: 0.8rem; margin-top: 20px;">I love you! 🥰</p>
        </div>
    </div>

    <script>
        // Create floating hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = Math.random() * 20 + 10 + 'px';
            heart.style.animationDuration = Math.random() * 3 + 3 + 's';
            document.getElementById('heart-bg').appendChild(heart);
            setTimeout(() => heart.remove(), 6000);
        }
        setInterval(createHeart, 300);

        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const mainCard = document.getElementById('mainCard');
        const successCard = document.getElementById('successCard');

        // The "Runaway" Logic for Mobile & Desktop
        const moveNo = () => {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 50);
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            noBtn.style.position = 'fixed';
        };

        noBtn.addEventListener('mouseover', moveNo);
        noBtn.addEventListener('touchstart', (e) => { e.preventDefault(); moveNo(); });

        yesBtn.addEventListener('click', () => {
            mainCard.classList.add('hidden');
            successCard.classList.remove('hidden');
            // Flashy effect
            document.body.style.background = "linear-gradient(135deg, #ff758f 0%, #ff4d6d 100%)";
        });
    </script>
</body>
</html>
