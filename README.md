<!DOCTYPE html>
<html lang="km">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Angkor Player</title>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800;900&display=swap"
        rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: #2b5c8f;
            color: #ffffff;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Hero Container */
        .hero-container {
            position: relative;
            width: 100vw;
            height: 100vh;
            background: linear-gradient(135deg, #2b5b8c 0%, #1e456e 100%);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 5%;
            overflow: hidden;
        }

        /* Background Big Text Overlay */
        .bg-text {
            position: absolute;
            font-size: 26vw;
            font-weight: 900;
            color: rgba(255, 255, 255, 0.05);
            letter-spacing: 5px;
            user-select: none;
            z-index: 1;
            white-space: nowrap;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        /* Header / Navbar */
        .header {
            position: absolute;
            top: 40px;
            left: 5%;
            right: 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 10;
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .grid-icon {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 4px;
            cursor: pointer;
        }

        .grid-icon span {
            width: 5px;
            height: 5px;
            background-color: #ffffff;
            border-radius: 50%;
        }

        .brand-name {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 20px;
            font-weight: 700;
            letter-spacing: 1.5px;
        }

        .brand-name i {
            font-size: 22px;
        }

        .share-btn {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background-color: #ffffff;
            color: #2b5c8f;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
            transition: transform 0.2s;
        }

        .share-btn:hover {
            transform: scale(1.08);
        }

        /* Main Content Left */
        .content-left {
            max-width: 500px;
            z-index: 5;
            margin-top: -40px;
        }

        .title {
            font-size: 110px;
            font-weight: 900;
            line-height: 0.9;
            letter-spacing: 2px;
            margin-bottom: 25px;
        }

        .description {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.75);
            line-height: 1.6;
            margin-bottom: 35px;
            font-weight: 300;
        }

        /* Platform Buttons */
        .platform-btns {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .platform-btns i {
            font-size: 28px;
            cursor: pointer;
            opacity: 0.9;
            transition: opacity 0.2s;
        }

        .platform-btns i:hover {
            opacity: 1;
        }

        .download-btn {
            background-color: #ffffff;
            color: #2b5c8f;
            padding: 10px 28px;
            border-radius: 30px;
            font-weight: 700;
            font-size: 12px;
            letter-spacing: 1px;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .download-btn:hover {
            background-color: #f0f0f0;
            transform: translateY(-2px);
        }

        /* Main Character Image */
        .hero-image {
            position: absolute;
            right: 15%;
            bottom: 0;
            height: 90%;
            z-index: 4;
            pointer-events: none;
        }

        .hero-image img {
            height: 100%;
            object-fit: contain;
            filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.3));
        }

        /* Bottom Wave Vector */
        .bottom-wave {
            position: absolute;
            bottom: 25px;
            left: 5%;
            width: 250px;
            opacity: 0.5;
            z-index: 5;
        }

        /* Player Bar (Glassmorphic Container) */
        .player-bar {
            position: absolute;
            bottom: 40px;
            left: 32%;
            right: 5%;
            height: 90px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            display: flex;
            align-items: center;
            padding: 0 30px;
            z-index: 10;
        }

        .album-cover {
            width: 70px;
            height: 70px;
            border-radius: 4px;
            overflow: hidden;
            margin-right: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .album-cover img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .song-info {
            flex-grow: 1;
        }

        .playing-now {
            font-size: 10px;
            letter-spacing: 1.5px;
            color: rgba(255, 255, 255, 0.7);
            font-weight: 600;
            margin-bottom: 2px;
        }

        .artist {
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .song-title {
            font-size: 22px;
            font-weight: 800;
            letter-spacing: 0.5px;
        }

        /* Player Controls */
        .controls {
            display: flex;
            align-items: center;
            gap: 25px;
        }

        .control-label {
            font-size: 11px;
            font-weight: 600;
            letter-spacing: 1.5px;
            color: rgba(255, 255, 255, 0.8);
            cursor: pointer;
        }

        .btn-ctrl {
            background: none;
            border: none;
            color: #ffffff;
            font-size: 18px;
            cursor: pointer;
            transition: transform 0.1s;
        }

        .btn-ctrl:hover {
            transform: scale(1.1);
        }

        .play-btn {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            border: 2px solid #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            padding-left: 2px;
        }

        /* Right Navigation Dots */
        .right-nav {
            position: absolute;
            right: 3%;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            gap: 15px;
            z-index: 10;
        }

        .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.8);
            cursor: pointer;
        }

        .dot.active {
            background-color: #ffffff;
            box-shadow: 0 0 8px rgba(255, 255, 255, 0.8);
        }

        /* --- កែប្រែត្រង់នេះក្នុង Tag <style> --- */

        .hero-image img {
            height: 100%;
            object-fit: contain;
            filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.3));

            /* ១. កំណត់ឱ្យរូបភាពដើមមានសខ្មៅ ១០០% */
            filter: grayscale(100%);

            /* ២. កំណត់ឱ្យការប្តូរពណ៌មានភាពទន់ភ្លន់ */
            transition: filter 0.8s ease;
        }

        /* ៣. បង្កើត class ថ្មីដើម្បីដាក់ឱ្យរូបភាពមានពណ៌វិញ ពេលកំពុង Play */
        .hero-image img.is-playing {
            filter: grayscale(0%);
        }
    </style>
</head>

<body>

    <!-- 
      កន្លែងដាក់ឯកសារវីដេអូ ឬចម្រៀងរបស់អ្នក 
      សូមប្តូរ video.mp4 ទៅជាឈ្មោះឯកសារដែលអ្នកបានទាញយកមក
    -->
    <audio id="myAudio" src="animal.mp4"></audio>

    <div class="hero-container">
        <!-- Big Text Background -->
        <div class="bg-text">MUSIC DISPLAY</div>

        <!-- Header -->
        <div class="header">
            <div class="logo-section">
                <div class="grid-icon">
                    <span></span><span></span><span></span>
                    <span></span><span></span><span></span>
                </div>
                <div class="brand-name">
                    <i class="fa-solid fa-bars-staggered"></i>
                    <span>ANGKOR PLAYER</span>
                </div>
            </div>
            <div class="share-btn">
                <i class="fa-solid fa-share-nodes"></i>
            </div>
        </div>

        <!-- Left Content -->
        <div class="content-left">
            <h1 class="title">PLAY.</h1>
            <p class="description">
                WavePlayer is a simple, but elegant music player that puts
                very little between you and your music. It operates on a tab
                structure and you can customize the tabs to use only the ones
                that you actually want.
            </p>
            <div class="platform-btns">
                <i class="fa-brands fa-android"></i>
                <i class="fa-brands fa-apple"></i>
                <button class="download-btn">DOWNLOAD</button>
            </div>
        </div>

        <!-- Hero Girl Image -->
        <div class="hero-image">
            <img src="091.jpg" alt="Music Listener">
        </div>

        <!-- Bottom Left Wave Decoration -->
        <svg class="bottom-wave" viewBox="0 0 200 40" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M0,20 Q10,5 20,20 T40,20 T60,20 T80,5 T100,20 T120,35 T140,20 T160,20 T180,5 T200,20"
                stroke="rgba(255,255,255,0.4)" fill="none" />
        </svg>

        <!-- Glassmorphism Player Bar -->
        <div class="player-bar">
            <div class="album-cover">
                <img src="https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=300&q=80"
                    alt="Album Cover">
            </div>
            <div class="song-info">
                <div class="playing-now">PLAYING NOW</div>
                <div class="artist">SILEUK MUSIC</div>
                <div class="song-title">7 rings</div>
            </div>
            <div class="controls">
                <span class="control-label">PREVIOUS</span>
                <button class="btn-ctrl"><i class="fa-solid fa-backward-step"></i></button>

                <!-- ប៊ូតុង Play/Pause ដែលបានភ្ជាប់ JavaScript -->
                <button class="btn-ctrl play-btn" id="playPauseBtn">
                    <i class="fa-solid fa-play" id="playIcon"></i>
                </button>

                <button class="btn-ctrl"><i class="fa-solid fa-forward-step"></i></button>
                <span class="control-label">NEXT</span>
            </div>
        </div>

        <!-- Right Side Navigation Dots -->
        <div class="right-nav">
            <div class="dot active"></div>
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
        </div>
    </div>

    <!-- JavaScript សម្រាប់បញ្ជាការ Play / Pause -->
    <script>
        /* --- កែប្រែ JavaScript ក្នុង Tag <script> ឱ្យដូចខាងក្រោម --- */

        const audio = document.getElementById('myAudio');
        const playPauseBtn = document.getElementById('playPauseBtn');
        const playIcon = document.getElementById('playIcon');
        // ចាប់យក Element រូបភាព
        const heroImage = document.querySelector('.hero-image img');

        playPauseBtn.addEventListener('click', function () {
            if (audio.paused) {
                audio.play();
                // ប្តូរ Icon ទៅជា Pause
                playIcon.classList.remove('fa-play');
                playIcon.classList.add('fa-pause');
                playPauseBtn.style.paddingLeft = '0px';

                // --- ថែម Class ដើម្បីឱ្យរូបភាពប្តូរមកមានពណ៌ ---
                heroImage.classList.add('is-playing');

            } else {
                audio.pause();
                // ប្តូរ Icon ទៅជា Play
                playIcon.classList.remove('fa-pause');
                playIcon.classList.add('fa-play');
                playPauseBtn.style.paddingLeft = '2px';

                // --- ដក Class ចេញវិញ ដើម្បីឱ្យរូបភាពទៅជាសខ្មៅ ---
                heroImage.classList.remove('is-playing');
            }
        });

        // កុំភ្លេចកំណត់ករណីចាក់ចប់៖ ឱ្យរូបភាពទៅជាសខ្មៅវិញ
        audio.addEventListener('ended', function () {
            playIcon.classList.remove('fa-pause');
            playIcon.classList.add('fa-play');
            playPauseBtn.style.paddingLeft = '2px';
            // ដកពណ៌ចេញ
            heroImage.classList.remove('is-playing');
        });
    </script>
</body>

</html>
