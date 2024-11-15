<html><head><base href="https://websim-engine.ai/"/>
<title>RADIO EN VIVO</title>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
    body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        background-color: #f0f0f0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
        background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    }
    .player-container {
        background-color: #ffffff;
        border-radius: 15px;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        padding: 30px;
        text-align: center;
        max-width: 400px;
        width: 100%;
    }
    h1 {
        color: #333;
        margin-bottom: 20px;
        font-size: 24px;
    }
    .controls {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 20px;
        margin-bottom: 20px;
    }
    button {
        background-color: #4CAF50;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
        border-radius: 50px;
        transition: all 0.3s ease;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    button:hover {
        background-color: #45a049;
        transform: translateY(-2px);
        box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
    }
    button:active {
        transform: translateY(0);
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
    button:disabled {
        background-color: #cccccc;
        cursor: not-allowed;
    }
    .volume-control {
        display: flex;
        align-items: center;
        gap: 10px;
    }
    input[type="range"] {
        -webkit-appearance: none;
        width: 100%;
        height: 10px;
        border-radius: 5px;
        background: #d3d3d3;
        outline: none;
        opacity: 0.7;
        transition: opacity .2s;
    }
    input[type="range"]:hover {
        opacity: 1;
    }
    input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background: #4CAF50;
        cursor: pointer;
        transition: all 0.3s ease;
    }
    input[type="range"]::-moz-range-thumb {
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background: #4CAF50;
        cursor: pointer;
        transition: all 0.3s ease;
    }
    input[type="range"]::-webkit-slider-thumb:hover,
    input[type="range"]::-moz-range-thumb:hover {
        width: 22px;
        height: 22px;
    }
    .album-art {
        width: 200px;
        height: 200px;
        border-radius: 50%;
        margin: 20px auto;
        animation: spin 10s linear infinite;
        animation-play-state: paused;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }
    .album-art:hover {
        transform: scale(1.05);
        box-shadow: 0 0 30px rgba(0, 0, 0, 0.2);
    }
    @keyframes spin {
        100% { transform: rotate(360deg); }
    }
    .now-playing {
        font-weight: bold;
        margin-bottom: 10px;
        color: #4CAF50;
    }
    .song-info {
        font-size: 18px;
        margin-bottom: 15px;
        color: #333;
    }
    .live-indicator {
        background-color: #ff0000;
        color: white;
        padding: 5px 10px;
        border-radius: 20px;
        display: inline-block;
        margin-top: 10px;
        font-size: 14px;
        font-weight: bold;
        text-transform: uppercase;
        animation: pulse 2s infinite;
    }
    @keyframes pulse {
        0% { opacity: 1; }
        50% { opacity: 0.5; }
        100% { opacity: 1; }
    }
</style>
</head>
<body>
    <div class="player-container">
        <h1> JOSELOVEMUSIC</h1>
        <audio id="radioPlayer">
            <source src=" https://stream.zeno.fm/y77pn1nrsyntv" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
        <div class="controls">
            <button id="playPauseBtn">Play</button>
            <div class="volume-control">
                <span>Volume:</span>
                <input type="range" id="volumeSlider" min="0" max="1" step="0.1" value="1">
            </div>
        </div>
        <div class="now-playing">Está Sonando:</div>
        <div id="songInfo" class="song-info"></div>
        <img id=" https://i.ibb.co/2Z93PTf/LOGOS.jpg " class="album-art" src="https://i.ibb.co/2Z93PTf/LOGOS.jpg " alt=" ALBUN INVIVO">
        <div id="liveIndicator" class="live-indicator">EN VIVO</div>
    </div>

    <script>
        const radioPlayer = document.getElementById('radioPlayer');
        const playPauseBtn = document.getElementById('playPauseBtn');
        const volumeSlider = document.getElementById('volumeSlider');
        const songInfo = document.getElementById('songInfo');
        const albumArt = document.getElementById('albumArt');

        playPauseBtn.addEventListener('click', togglePlayPause);
        volumeSlider.addEventListener('input', adjustVolume);

        function togglePlayPause() {
            if (radioPlayer.paused) {
                radioPlayer.play();
                playPauseBtn.textContent = 'Pause';
                albumArt.style.animationPlayState = 'running';
            } else {
                radioPlayer.pause();
                playPauseBtn.textContent = 'Play';
                albumArt.style.animationPlayState = 'paused';
            }
        }

        function adjustVolume() {
            radioPlayer.volume = volumeSlider.value;
        }

        radioPlayer.addEventListener('play', () => {
            playPauseBtn.textContent = 'Pause';
            albumArt.style.animationPlayState = 'running';
        });

        radioPlayer.addEventListener('pause', () => {
            playPauseBtn.textContent = 'Play';
            albumArt.style.animationPlayState = 'paused';
        });

        radioPlayer.addEventListener('waiting', () => {
            playPauseBtn.disabled = true;
        });

        radioPlayer.addEventListener('canplay', () => {
            playPauseBtn.disabled = false;
        });

        radioPlayer.addEventListener('error', (e) => {
            console.error('Error loading audio:', e);
            alert('Error loading audio stream. Please try again later.');
        });

        function updateNowPlaying() {
            fetch(' PLAYER')
                .then(response => response.json())
                .then(data => {
                    const nowPlaying = data.now_playing.song;
                    songInfo.textContent = `${nowPlaying.artist} - ${nowPlaying.title}`;
                    albumArt.src = nowPlaying.art;
                    albumArt.alt = `Album art for ${nowPlaying.title} by ${nowPlaying.artist}`;
                })
                .catch(error => {
                    console.error('Error fetching now playing info:', error);
                });
        }

        // Update now playing info every 30 seconds
        updateNowPlaying();
        setInterval(updateNowPlaying, 30000);
    </script>
</body>
</html>
