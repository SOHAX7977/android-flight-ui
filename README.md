<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>MySite™ Loader</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background-color: #000;
      color: white;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      text-align: center;
    }

    h1 {
      font-size: 2rem;
      font-weight: bold;
      margin-bottom: 10px;
      animation: glow 1.5s ease-in-out infinite alternate;
    }

    @keyframes glow {
      from {
        text-shadow: 0 0 10px #fff;
      }
      to {
        text-shadow: 0 0 20px #0ff, 0 0 30px #0ff;
      }
    }

    .subheading {
      font-style: italic;
      color: #ccc;
      margin-bottom: 20px;
    }

    .loading-text {
      font-size: 1.5rem;
      font-weight: 600;
      margin-bottom: 10px;
      animation: fadeIn 1s ease-in-out forwards;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
      }
      to {
        opacity: 1;
      }
    }

    .countdown {
      margin: 15px 0;
      font-size: 1rem;
      color: #999;
    }

    .progress-bar {
      width: 80%;
      height: 6px;
      background-color: #222;
      border-radius: 10px;
      overflow: hidden;
      margin-bottom: 15px;
    }

    .progress {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, #00f5ff, #00ff88);
      transition: width 1s linear;
    }

    .tip {
      margin-top: 10px;
      font-size: 0.9rem;
      color: #aaa;
    }

    .footer {
      margin-top: 30px;
      font-size: 0.8rem;
      color: #777;
    }
  </style>
</head>
<body>

  <h1>MySite™</h1>
  <div class="loading-text">YOUR<br>WEB EXPERIENCE<br>IS LOADING RIGHT <em>NOW</em></div>

  <div class="countdown">Loading in <span id="seconds">10</span> seconds</div>

  <div class="progress-bar">
    <div class="progress" id="progress"></div>
  </div>

  <div class="tip">Tip: For the best experience, use Chrome or Firefox.</div>
  <div class="footer">Please wait a few seconds</div>

  <script>
    let seconds = 10;
    const countdownEl = document.getElementById('seconds');
    const progressEl = document.getElementById('progress');

    const interval = setInterval(() => {
      seconds--;
      countdownEl.textContent = seconds;
      progressEl.style.width = `${(10 - seconds) * 10}%`;

      if (seconds === 0) {
        clearInterval(interval);
        countdownEl.textContent = '0';
        document.querySelector('.loading-text').textContent = 'Loaded!';
        progressEl.style.width = '100%';
        progressEl.style.background = 'linear-gradient(90deg, #00ff88, #00f5ff)';
      }
    }, 1000);
  </script>

</body>
</html>
