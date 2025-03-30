<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eid Mubarak Surprise</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f0f8ff;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
        }

        @keyframes gradientBG {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }

        .container {
            text-align: center;
            z-index: 10;
        }

        .surprise-button {
            padding: 15px 30px;
            font-size: 20px;
            background: linear-gradient(45deg, #ff8a00, #e52e71);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .surprise-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
        }

        .surprise-button:active {
            transform: translateY(1px);
        }

        .surprise-button::after {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.1);
            transform: rotate(45deg);
            transition: all 0.3s ease;
        }

        .surprise-button:hover::after {
            left: 100%;
            top: 100%;
        }

        .eid-message {
            font-size: 0;
            color: white;
            margin-top: 30px;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.8);
            transition: all 0.5s ease;
            opacity: 0;
            transform: scale(0.5);
        }

        .show {
            font-size: 60px;
            opacity: 1;
            transform: scale(1);
            animation: glow 2s infinite alternate;
        }

        @keyframes glow {
            from {
                text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #e60073, 0 0 40px #e60073;
            }
            to {
                text-shadow: 0 0 20px #fff, 0 0 30px #ff4da6, 0 0 40px #ff4da6, 0 0 50px #ff4da6;
            }
        }

        .stars {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: 1;
        }

        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle 1s infinite alternate;
            opacity: 0;
        }

        @keyframes twinkle {
            to {
                opacity: 1;
                transform: scale(1.5);
            }
        }

        .moon {
            position: absolute;
            top: 50px;
            right: 100px;
            width: 80px;
            height: 80px;
            background: #f5f3ce;
            border-radius: 50%;
            box-shadow: 0 0 30px #f5f3ce;
            opacity: 0;
            transition: opacity 1s ease;
        }

        .show-moon {
            opacity: 1;
        }

        .lanterns {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
        }

        .lantern {
            position: absolute;
            width: 40px;
            height: 60px;
            background: linear-gradient(to bottom, #e52e71, #ff8a00);
            border-radius: 5px;
            opacity: 0;
            transition: all 1s ease;
            animation: swing 3s infinite ease-in-out;
        }

        .lantern::before {
            content: "";
            position: absolute;
            width: 10px;
            height: 10px;
            background: #ff8a00;
            border-radius: 50%;
            top: -5px;
            left: 15px;
        }

        .lantern::after {
            content: "";
            position: absolute;
            width: 30px;
            height: 5px;
            background: #ff8a00;
            bottom: -5px;
            left: 5px;
            border-radius: 5px;
        }

        @keyframes swing {
            0%, 100% {
                transform: rotate(-5deg);
            }
            50% {
                transform: rotate(5deg);
            }
        }

        .show-lanterns .lantern {
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <div class="container">
        <button class="surprise-button" id="surpriseButton">Press Button for Surprise</button>
        <div class="eid-message" id="eidMessage">Eid Mubarak!</div>
    </div>

    <div class="stars" id="stars"></div>
    <div class="moon" id="moon"></div>
    <div class="lanterns" id="lanterns"></div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const surpriseButton = document.getElementById('surpriseButton');
            const eidMessage = document.getElementById('eidMessage');
            const starsContainer = document.getElementById('stars');
            const moon = document.getElementById('moon');
            const lanternsContainer = document.getElementById('lanterns');

            // Create stars
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                star.style.width = `${Math.random() * 3 + 1}px`;
                star.style.height = star.style.width;
                star.style.left = `${Math.random() * 100}%`;
                star.style.top = `${Math.random() * 100}%`;
                star.style.animationDelay = `${Math.random() * 2}s`;
                starsContainer.appendChild(star);
            }

            // Create lanterns
            for (let i = 0; i < 10; i++) {
                const lantern = document.createElement('div');
                lantern.classList.add('lantern');
                lantern.style.left = `${10 + (i * 8)}%`;
                lantern.style.top = `${10 + (Math.random() * 20)}%`;
                lantern.style.animationDelay = `${i * 0.3}s`;
                lanternsContainer.appendChild(lantern);
            }

            surpriseButton.addEventListener('click', function() {
                // Hide button
                this.style.transform = 'scale(0)';
                this.style.opacity = '0';
                
                // Show Eid message
                setTimeout(() => {
                    eidMessage.classList.add('show');
                    moon.classList.add('show-moon');
                    lanternsContainer.classList.add('show-lanterns');
                }, 500);
                
                // Create burst effect
                createBurst();
            });

            function createBurst() {
                const colors = ['#ff0000', '#ffff00', '#00ff00', '#00ffff', '#0000ff', '#ff00ff'];
                
                for (let i = 0; i < 50; i++) {
                    const particle = document.createElement('div');
                    particle.style.position = 'absolute';
                    particle.style.width = '10px';
                    particle.style.height = '10px';
                    particle.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    particle.style.borderRadius = '50%';
                    particle.style.left = '50%';
                    particle.style.top = '50%';
                    particle.style.transform = 'translate(-50%, -50%)';
                    
                    const angle = Math.random() * Math.PI * 2;
                    const distance = Math.random() * 200 + 100;
                    const duration = Math.random() * 1 + 0.5;
                    
                    document.body.appendChild(particle);
                    
                    setTimeout(() => {
                        particle.style.transition = `all ${duration}s ease-out`;
                        particle.style.left = `${50 + Math.cos(angle) * distance}%`;
                        particle.style.top = `${50 + Math.sin(angle) * distance}%`;
                        particle.style.opacity = '0';
                        
                        setTimeout(() => {
                            particle.remove();
                        }, duration * 1000);
                    }, 10);
                }
            }
        });
    </script>
</body>
</html>
