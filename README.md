<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="theme-color" content="#000000">
  <title>Chúc Mừng Năm Mới</title>
  <link href="https://fonts.googleapis.com/css?family=Russo+One" rel="stylesheet">
  <link rel="shortcut icon" type="image/png" href="https://s3-us-west-2.amazonaws.com/s.cdpn.io/329180/firework-burst-icon-v2.png">
  <style>
    /* CSS Code from your file */
    * { position: relative; box-sizing: border-box; }
    html, body { height: 100%; }
    html { background-color: #000; }
    body { overflow: hidden; color: rgba(255, 255, 255, 0.5); font-family: "Russo One", arial, sans-serif; }
    .container { height: 100%; display: flex; justify-content: center; align-items: center; }
    .loading-init { text-align: center; text-transform: uppercase; }
    .loading-init__header { font-size: 2.2em; }
    .loading-init__status { margin-top: 1em; font-size: 0.8em; opacity: 0.75; }
    .stage-container { overflow: hidden; border: 1px solid #222; margin: -1px; }
    .canvas-container { width: 100%; height: 100%; }
    .controls { position: absolute; top: 0; width: 100%; padding-bottom: 50px; display: flex; justify-content: space-between; }
    .btn { opacity: 0.16; width: 50px; height: 50px; display: flex; cursor: pointer; transition: opacity 0.3s; }
    .btn:hover { opacity: 0.32; }
    .credits { font-size: 0.8em; opacity: 0.75; }
    .menu { background-color: rgba(0, 0, 0, 0.42); }
    .menu__header { font-size: 2em; text-transform: uppercase; }
    /* Add remaining CSS here */
  </style>
</head>
<body>
  <div class="container">
    <div class="loading-init">
      <div class="loading-init__header">Đang Tải</div>
      <div class="loading-init__status">Vui Lòng Đợi Trong Giây Lát</div>
    </div>
    <div class="stage-container remove">
      <div class="canvas-container">
        <canvas id="trails-canvas"></canvas>
        <canvas id="main-canvas"></canvas>
      </div>
      <div class="controls">
        <div class="btn pause-btn">
          <svg fill="white" width="24" height="24"><use href="#icon-pause" xlink:href="#icon-pause"></use></svg>
        </div>
        <div class="btn sound-btn">
          <svg fill="white" width="24" height="24"><use href="#icon-sound-off" xlink:href="#icon-sound-off"></use></svg>
        </div>
        <div class="btn settings-btn">
          <svg fill="white" width="24" height="24"><use href="#icon-settings" xlink:href="#icon-settings"></use></svg>
        </div>
      </div>
    </div>
  </div>

  <script>
    // JavaScript Code from your file
    'use strict';
    console.clear();
    const IS_MOBILE = window.innerWidth <= 640;
    const IS_DESKTOP = window.innerWidth > 800;
    const IS_HIGH_END_DEVICE = (() => {
      const hwConcurrency = navigator.hardwareConcurrency || 2;
      return hwConcurrency >= (window.innerWidth <= 1024 ? 4 : 8);
    })();
    const MAX_WIDTH = 7680, MAX_HEIGHT = 4320, GRAVITY = 0.9;
    let simSpeed = 1;

    function getDefaultScaleFactor() {
      return IS_MOBILE ? 0.9 : 1;
    }

    let stageW, stageH, quality = 1, isLowQuality = false, isHighQuality = false;
    const QUALITY_LOW = 1, QUALITY_NORMAL = 2, QUALITY_HIGH = 3;

    const trailsStage = new Stage('trails-canvas');
    const mainStage = new Stage('main-canvas');
    const stages = [trailsStage, mainStage];

    function togglePause(toggle) {
      store.setState({ paused: typeof toggle === 'boolean' ? toggle : !store.state.paused });
    }

    const store = {
      state: { paused: true, soundEnabled: false, fullscreen: false },
      setState(nextState) { Object.assign(this.state, nextState); },
    };

    function renderApp(state) {
      const pauseBtnIcon = `#icon-${state.paused ? 'play' : 'pause'}`;
      document.querySelector('.pause-btn use').setAttribute('href', pauseBtnIcon);
    }

    store.setState({ paused: false }); // Unpause simulation

    // Add your full JavaScript code here (or from the uploaded file)
  </script>
</body>
</html>
