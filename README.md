# Spotify-clone
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/7.0.1/css/all.min.css" integrity="sha512-2SwdPD6INVrV/lHTZbO2nodKhrnDdJK9/kg2XD1r9uGqPo1cUbujc+IYdlYdEErWNu69gVcYgdxlmVmzTWnetw==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <title>Spotify - Web player: music for everyone</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Montserrat', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #000;
            color: #fff;
            overflow: hidden;
        }

        .main {
            display: flex;
            flex-direction: row;
            height: 100vh;
            padding: 0.2rem;
        }

        .sidebar {
            width: 340px;
            background-color: black;
        }

        .nav {
            background-color: #121212;
            border-radius: 1rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100px;
            padding: 0.5rem 0.75rem;
            margin: 0.5rem;
        }

        .nav-option {
            line-height: 2rem;
            display: flex;
            align-items: center;
            font-size: 1rem;
            padding: 0.5rem;
        }

        .nav-option:hover {
            opacity: 1;
        }

        .nav-option i {
            font-size: 1.2rem;
        }

        .nav-option a {
            font-size: 1rem;
        }

        .main-content {
            background-color: #121212;
            width: 100%;
            flex: 1;
            overflow: auto;
            border-radius: 1rem;
            margin: 0.5rem;
            padding-bottom: 5rem;
        }

        .music-player {
            background-color: black;
            height: 72px;
            width: 100%;
            position: fixed;
            bottom: 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 1rem;
        }

        a {
            text-decoration: none;
            color: #fff;
            margin-left: 1rem;
        }

        .icons {
            font-size: 1.25rem;
            display: flex;
        }

        .icons i {
            margin-right: 1rem;
            opacity: 0.6;
            cursor: pointer;
        }

        .icons i:hover {
            opacity: 1;
        }

        .library {
            background-color: #121212;
            border-radius: 1rem;
            height: 30rem;
            justify-content: center;
            padding: 0.5rem 0.75rem;
            margin: 0.5rem;
        }

        .options {
            border-radius: 1rem;
            height: 50px;
            width: 100%;
            padding: 0.5rem 0.75rem;
            margin: 0.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .box {
            background-color: #232323;
            border-radius: 1rem;
            height: 6rem;
            padding: 1rem;
            margin: 0.5rem;
        }

        .box-p1 {
            font-size: 1rem;
            font-weight: 500;
            padding-bottom: 0.5rem;
            margin-top: 0.5rem;
        }

        .box-p2 {
            font-size: 0.8rem;
            opacity: 0.6;
            margin: 0.5rem;
        }

        .badge {
            background-color: white;
            color: black;
            font-weight: 500;
            border-radius: 1rem;
            padding: 0.25rem 0.5rem;
            border: none;
            opacity: 0.8;
            height: 2rem;
            cursor: pointer;
        }

        .badge:hover {
            opacity: 1;
            transition: all 0.2s ease-in-out;
        }

        .box2 {
            background-color: #232323;
            border-radius: 1rem;
            height: 7rem;
            margin: 0.5rem 0 0.5rem 0;
            padding: 0.5rem;
            margin-top: 1rem;
        }

        .sticky-nav {
            position: sticky;
            top: 0;
            background-color: #121212;
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 3rem;
            border-radius: 1rem 1rem 0 0;
            z-index: 10;
        }

        .nav-icons {
            height: 1rem;
            width: 1rem;
            display: flex;
            align-items: center;
            margin-left: 1rem;
            margin-top: 0.5rem;
        }

        .nav-icons i {
            margin-right: 0.75rem;
            opacity: 0.6;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .nav-icons i:hover {
            opacity: 1;
        }

        .nav-buttons {
            display: flex;
            align-items: center;
            margin-right: 1rem;
        }

        .dark-badge {
            background-color: black;
            color: white;
        }

        .nav-buttons i {
            margin-right: 1rem;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Cards Section */
        .cards-container {
            padding: 1rem;
        }

        .cards-container h2 {
            margin-bottom: 1rem;
        }

        .cards {
            display: flex;
            gap: 1rem;
            overflow-x: auto;
            padding-bottom: 1rem;
        }

        .cards::-webkit-scrollbar {
            height: 8px;
        }

        .cards::-webkit-scrollbar-track {
            background: #121212;
        }

        .cards::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 10px;
        }

        .card {
            min-width: 160px;
            background-color: #181818;
            border-radius: 0.5rem;
            padding: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .card:hover {
            background-color: #282828;
        }

        .card-img {
            width: 100%;
            height: 160px;
            background-color: #333;
            border-radius: 0.5rem;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            position: relative;
        }

        .card-title {
            font-size: 1rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .card-info {
            font-size: 0.85rem;
            opacity: 0.7;
        }

        .play-button {
            position: absolute;
            bottom: 10px;
            right: 10px;
            background-color: #1db954;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }

        .card:hover .play-button {
            opacity: 1;
        }

        .play-button i {
            color: black;
            font-size: 1.2rem;
        }

        /* Music Player Styles */
        .player-left {
            display: flex;
            align-items: center;
            width: 30%;
        }

        .player-song-info {
            display: flex;
            align-items: center;
        }

        .player-song-img {
            width: 56px;
            height: 56px;
            background-color: #333;
            border-radius: 0.25rem;
            margin-right: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .player-song-details h4 {
            margin: 0;
            font-size: 0.9rem;
            font-weight: 500;
        }

        .player-song-details p {
            margin: 0;
            font-size: 0.75rem;
            opacity: 0.7;
        }

        .player-left-icons {
            margin-left: 1rem;
            display: flex;
            gap: 1rem;
        }

        .player-left-icons i {
            opacity: 0.7;
            cursor: pointer;
        }

        .player-left-icons i:hover {
            opacity: 1;
        }

        .player-center {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 40%;
        }

        .player-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 0.5rem;
        }

        .player-controls i {
            opacity: 0.7;
            cursor: pointer;
            font-size: 1rem;
        }

        .player-controls i:hover {
            opacity: 1;
        }

        .player-controls .fa-circle-play {
            font-size: 2rem;
            opacity: 1;
        }

        .player-timeline {
            display: flex;
            align-items: center;
            width: 100%;
            gap: 0.5rem;
        }

        .player-timeline span {
            font-size: 0.75rem;
            opacity: 0.7;
        }

        .progress-bar {
            flex: 1;
            height: 4px;
            background-color: #4d4d4d;
            border-radius: 2px;
            cursor: pointer;
            position: relative;
        }

        .progress-bar:hover .progress {
            background-color: #1db954;
        }

        .progress {
            height: 100%;
            background-color: #fff;
            border-radius: 2px;
            width: 30%;
            position: relative;
        }

        .player-right {
            display: flex;
            align-items: center;
            width: 30%;
            justify-content: flex-end;
            gap: 1rem;
        }

        .player-right i {
            opacity: 0.7;
            cursor: pointer;
        }

        .player-right i:hover {
            opacity: 1;
        }

        .volume-bar {
            width: 100px;
            height: 4px;
            background-color: #4d4d4d;
            border-radius: 2px;
            cursor: pointer;
        }

        .volume-level {
            height: 100%;
            background-color: #fff;
            border-radius: 2px;
            width: 70%;
        }

        @media (max-width: 1000px) {
            .hide {
                display: none;
            }
            .sidebar {
                width: 100px;
            }
            .player-left, .player-right {
                width: 25%;
            }
            .player-center {
                width: 50%;
            }
        }
    </style>
</head>
<body>
    <div class="main">
        <div class="sidebar">
            <div class="nav">
                <div class="nav-option" style="opacity: 1;">
                    <i class="fa-solid fa-house"></i>
                    <a href="#">Home</a>
                </div>
                <div class="nav-option">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <a href="#">Search</a>
                </div>
            </div>

            <div class="library">
                <div class="options">
                    <div class="lib-options nav-option">
                        <i class="fa-solid fa-book" style="font-size: 1.25rem;"></i>
                        <a href="#">Your Library</a>
                    </div>
                    <div class="icons">
                        <i class="fa-solid fa-plus"></i>
                        <i class="fa-solid fa-arrow-right"></i>
                    </div>
                </div>

                <div class="lib-box">
                    <div class="box">
                        <div class="box-p1">Create Your first Playlist</div>
                        <div class="box-p2">It's easy, we'll help you</div>
                        <button class="badge">Create Playlist</button>
                    </div>
                    <div class="box2">
                        <div class="box-p1">Let's find some podcasts to follow</div>
                        <div class="box-p2">We'll keep you updated on new episodes</div>
                        <button class="badge">Browse Podcasts</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="main-content">
            <div class="sticky-nav">
                <div class="nav-icons">
                    <i class="fa-solid fa-chevron-left"></i>
                    <i class="fa-solid fa-chevron-right hide"></i>
                </div>
                <div class="nav-buttons">
                    <button class="badge hide">Explore Premium</button>
                    <button class="badge dark-badge">
                        <i class="fa-regular fa-circle-down" style="margin-right: 0.3rem;"></i>Install App
                    </button>
                    <i class="fa-regular fa-user"></i>
                </div>
            </div>

            <div class="cards-container">
                <h2>Focus</h2>
                <div class="cards">
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-music"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Peaceful Piano</div>
                        <div class="card-info">Relax and indulge with beautiful piano pieces</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-guitar"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Deep Focus</div>
                        <div class="card-info">Keep calm and focus with ambient music</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-headphones"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Instrumental Study</div>
                        <div class="card-info">Focus with soft study music in the background</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-star"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Jazz Vibes</div>
                        <div class="card-info">The original chill instrumental beats playlist</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-cloud"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Calm Vibes</div>
                        <div class="card-info">Relax with these calm and peaceful tunes</div>
                    </div>
                </div>
            </div>

            <div class="cards-container">
                <h2>Spotify Playlists</h2>
                <div class="cards">
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-fire"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Today's Top Hits</div>
                        <div class="card-info">Ed Sheeran is on top of the Hottest 50!</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-bolt"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">RapCaviar</div>
                        <div class="card-info">New music from Lil Baby, Juice WRLD and more</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-heart"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">All Out 2010s</div>
                        <div class="card-info">The biggest songs of the 2010s</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-drum"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Rock Classics</div>
                        <div class="card-info">Rock legends and epic songs</div>
                    </div>
                    <div class="card">
                        <div class="card-img">
                            <i class="fa-solid fa-coffee"></i>
                            <div class="play-button">
                                <i class="fa-solid fa-play"></i>
                            </div>
                        </div>
                        <div class="card-title">Chill Hits</div>
                        <div class="card-info">Kick back to the best new and recent chill hits</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="music-player">
        <div class="player-left">
            <div class="player-song-info">
                <div class="player-song-img">
                    <i class="fa-solid fa-music"></i>
                </div>
                <div class="player-song-details">
                    <h4>Song Name</h4>
                    <p>Artist Name</p>
                </div>
            </div>
            <div class="player-left-icons">
                <i class="fa-regular fa-heart"></i>
                <i class="fa-solid fa-plus"></i>
            </div>
        </div>

        <div class="player-center">
            <div class="player-controls">
                <i class="fa-solid fa-shuffle"></i>
                <i class="fa-solid fa-backward-step"></i>
                <i class="fa-solid fa-circle-play"></i>
                <i class="fa-solid fa-forward-step"></i>
                <i class="fa-solid fa-repeat"></i>
            </div>
            <div class="player-timeline">
                <span>1:23</span>
                <div class="progress-bar">
                    <div class="progress"></div>
                </div>
                <span>3:45</span>
            </div>
        </div>

        <div class="player-right">
            <i class="fa-solid fa-list"></i>
            <i class="fa-solid fa-volume-high"></i>
            <div class="volume-bar">
                <div class="volume-level"></div>
            </div>
            <i class="fa-solid fa-expand"></i>
        </div>
    </div>
</body>
</html>
