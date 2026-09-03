<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>rayna.space | 神島玲奈 宇宙哲学本陣</title>
    <style>
        /* 隠世のノイズを消し去る漆黒の世界観 */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: #000;
            color: #fff;
            font-family: 'Times New Roman', 'Noto Serif JP', serif;
            overflow: hidden;
            -webkit-user-select: none; /* 絶対防衛コピープロテクション */
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }

        /* 【新兵装】ド迫力・宇宙シネマ背景動画の器 */
        .video-background {
            position: absolute;
            top: 50%;
            left: 50%;
            width: 100vw;
            height: 56.25vw; /* 16:9の黄金シネマ比率 */
            min-height: 100vh;
            min-width: 177.77vh;
            transform: translate(-50%, -50%) scale(1.0);
            z-index: 1;
            transition: transform 6s cubic-bezier(0.1, 0.8, 0.2, 1);
            pointer-events: none;
        }

        /* 「Works」プッシュ時の一大ズームアップ挙動 */
        .video-background.zoom {
            transform: translate(-50%, -50%) scale(1.5);
        }

        /* 動画の上の漆黒フィルター（エレガントな深みを演出） */
        .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(0,0,0,0.2) 0%, rgba(0,0,0,0.8) 100%);
            z-index: 2;
            pointer-events: none;
        }

        /* シネマスコープ（映画館の上下黒帯） */
        .cinema-bolt {
            position: absolute;
            left: 0;
            width: 100%;
            height: 0;
            background: #000;
            z-index: 10;
            transition: height 2s cubic-bezier(0.25, 1, 0.3, 1);
        }
        .bolt-top { top: 0; }
        .bolt-bottom { bottom: 0; }

        .cinema-active .bolt-top,
        .cinema-active .bolt-bottom {
            height: 14vh; /* 荘厳なシネマ画角へ */
        }

        /* 操縦席（メインUI） */
        .interface {
            position: relative;
            z-index: 5;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: opacity 1.5s ease, filter 1.5s ease;
        }

        .works-trigger {
            background: transparent;
            border: 1px solid rgba(255,255,255,0.6);
            color: #fff;
            padding: 20px 60px;
            font-size: 1.4rem;
            letter-spacing: 0.5em;
            cursor: pointer;
            transition: all 0.8s cubic-bezier(0.1, 0.8, 0.2, 1);
            backdrop-filter: blur(4px);
        }

        .works-trigger:hover {
            background: #fff;
            color: #000;
            box-shadow: 0 0 40px rgba(255,255,255,0.8);
            letter-spacing: 0.7em;
        }

        /* 映画風シネマタイポグラフィ（神聖ゴールド） */
        .cinema-text-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 15;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            pointer-events: none;
        }

        .phrase {
            font-size: 2.6rem;
            color: #f1c40f; /* 聖なる金色の輝き */
            letter-spacing: 0.6em;
            margin: 30px 0;
            opacity: 0;
            filter: blur(25px);
            transform: scale(0.85);
            transition: opacity 3s cubic-bezier(0.1, 0.8, 0.2, 1), filter 3s cubic-bezier(0.1, 0.8, 0.2, 1), transform 3s cubic-bezier(0.1, 0.8, 0.2, 1);
            text-shadow: 0 0 25px rgba(241,196,15,0.6);
            font-weight: 300;
        }

        .phrase.reveal {
            opacity: 1;
            filter: blur(0px);
            transform: scale(1);
        }
    </style>
</head>
<body>

    <!-- 上下シネマスコープ -->
    <div class="cinema-bolt bolt-top"></div>
    <div class="cinema-bolt bolt-bottom"></div>

    <!-- 漆黒の深みベール -->
    <div class="video-overlay"></div>

    <!-- 【ステルス配置】Vimeoの超高精細宇宙映像を背景に強制同期（ノイズ完全カット仕様） -->
    <iframe class="video-background" id="space-video" 
        src="https://vimeo.com" 
        frameborder="0" allow="autoplay; fullscreen" allowfullscreen>
    </iframe>

    <!-- 初期インターフェース -->
    <div class="interface" id="ui">
        <h1 style="letter-spacing: 0.7em; font-weight: 300; margin-bottom: 70px; font-size: 3.2rem; text-shadow: 0 0 30px rgba(255,255,255,0.4);">RAYNA KAMISIMA</h1>
        <button class="works-trigger" onclick="launchCinema()">Works</button>
    </div>

    <!-- 視聴覚タイポグラフィの舞台 -->
    <div class="cinema-text-container">
        <p class="phrase" id="p1">今、神島玲奈が渾身の力で描く！</p>
        <p class="phrase" id="p2">宇宙と人間の真実が明かされる！</p>
    </div>

    <script>
        // 映画風大音響＆大ズーム演出発動
        function launchCinema() {
            // UIを静かに消去
            document.getElementById('ui').style.opacity = '0';
            document.getElementById('ui').style.filter = 'blur(15px)';
            setTimeout(() => {
                document.getElementById('ui').style.display = 'none';
            }, 1500);

            // シネマスコープ作動＆背景宇宙動画のウルトラズームアップ！
            document.body.classList.add('cinema-active');
            document.getElementById('space-video').classList.add('zoom');

            // 第1幕：2秒後に深みから神聖ゴールドが浮かび上がる
            setTimeout(() => {
                document.getElementById('p1').classList.add('reveal');
            }, 2000);

            // 第2幕：6秒後に圧倒的な調和をもって現る
            setTimeout(() => {
                document.getElementById('p2').classList.add('reveal');
            }, 6000);
        }

        /* ==========================================
           『宇宙神話・新創世記』絶対防衛トラップ
           ========================================== */
        document.addEventListener('contextmenu', e => e.preventDefault(), false);
        document.addEventListener('keydown', function(e) {
            if (e.ctrlKey && (e.keyCode === 67 || e.keyCode === 85 || e.keyCode === 83)) {
                e.preventDefault();
                return false;
            }
            if (e.keyCode === 123) {
                e.preventDefault();
                return false;
            }
        }, false);
    </script>
</body>
</html>

