<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>BIRTHDAY VIA</title>
<style>
  :root{
    --bg:#dbeeff; --card:#ffffff; --ink:#1e293b; --sub:#526277;
    --line:#e2e8f0; --accent:#3b82f6;
  }
  *{box-sizing:border-box; margin:0; padding:0;}

  /* ==== LANGIT PAGI ANIMATED ==== */
  @keyframes moveClouds {
    0% { background-position: 0% 0%; }
    50% { background-position: 100% 10%; }
    100% { background-position: 0% 0%; }
  }

  body {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: "Poppins", sans-serif;
    background: linear-gradient(180deg, #bfe6ff 0%, #e6f5ff 45%, #fdfcfb 100%);
    overflow: hidden;
    position: relative;
  }

  /* Awan halus lembut bergerak */
  .clouds {
    position: absolute;
    inset: 0;
    background: 
      radial-gradient(circle at 10% 20%, rgba(255,255,255,0.9) 0%, transparent 50%),
      radial-gradient(circle at 50% 40%, rgba(255,255,255,0.8) 0%, transparent 55%),
      radial-gradient(circle at 90% 30%, rgba(255,255,255,0.9) 0%, transparent 50%),
      radial-gradient(circle at 30% 70%, rgba(255,255,255,0.7) 0%, transparent 55%);
    background-size: 400% 400%;
    animation: moveClouds 60s linear infinite;
    opacity: 0.5;
  }

  /* Cahaya hangat di bawah kartu */
  .sun-glow {
    position: absolute;
    bottom: -200px;
    left: 50%;
    transform: translateX(-50%);
    width: 800px;
    height: 400px;
    background: radial-gradient(circle at center, rgba(255,230,180,0.5) 0%, rgba(255,255,255,0) 70%);
    filter: blur(60px);
    z-index: 0;
  }

  /* ===== CARD ===== */
  .card{
    position: relative;
    z-index: 1;
    width:min(640px,92vw);
    background: var(--card);
    border:1px solid var(--line);
    border-radius:20px;
    padding:32px 28px;
    text-align:center;
    box-shadow:
      0 8px 20px rgba(0,0,0,0.1),
      0 4px 40px rgba(255,255,255,0.6) inset;
  }

  h1{
    margin-bottom:8px;
    font-size:clamp(24px,3vw,32px);
    color:var(--ink);
  }
  .sub{ color:var(--sub); margin-bottom:16px; font-size:15px; }
  .hr{ height:1px; background:var(--line); margin:20px auto; width:80%; }
  p{ color:var(--ink); line-height:1.7; margin:10px 0; }
  .doa{ color:var(--sub); font-size:15px; }
  .arab{
    font-family: "Scheherazade New", "Amiri", serif;
    font-size: 18px;
    line-height: 1.9;
    direction: rtl;
  }

  .btn{
    display:inline-block;
    margin-top:16px;
    padding:10px 18px;
    border-radius:12px;
    border:1px solid #c8dcff;
    background:var(--accent);
    color:#fff;
    font-weight:600;
    text-decoration:none;
    transition:transform .1s ease, background .2s ease;
    box-shadow:0 5px 20px rgba(59,130,246,0.3);
  }
  .btn:hover{ background:#2563eb; }
  .btn:active{ transform:translateY(1px); }
  .hint{ margin-top:8px; font-size:12px; color:var(--sub); }
</style>
</head>
<body>

<!-- Background layer -->
<div class="clouds"></div>
<div class="sun-glow"></div>

<!-- Card utama -->
<main class="card" role="article" aria-label="BIRTHDAY VIA">
  <h1>Happy Birthday, VIA 🎉</h1>
  <p class="sub">Semoga harimu penuh keberkahan</p>
  <div class="hr"></div>

  <p>Semoga di usia baru ini, Allah memberikan kesehatan yang sempurna, rezeki yang berkah, dan hati yang selalu bersyukur.</p>

  <p class="doa"><strong>Doa:</strong> Barakallahu fi umrik. Semoga Allah memberkahi usiamu, melindungi langkahmu, dan menuntunmu dalam kebaikan setiap hari.</p>

  <p class="arab">اللَّهُمَّ بَارِكْ لَهُ فِي عُمْرِهِ، وَارْزُقْهُ سَعَادَةً دَائِمَةً وَتَوْفِيقًا فِي كُلِّ أَمْرٍ.</p>
  <p class="doa">Ya Allah, berkahilah umurnya, anugerahkan kebahagiaan yang langgeng, dan bimbinglah dalam setiap urusan hidupnya.</p>

  <a href="#" id="playBtn" class="btn" role="button" aria-pressed="false">▶️ COBA PLAY</a>
  <div class="hint">COBA PLAY 🎶</div>

  <audio id="song" preload="auto" playsinline>
    <source src="happy-birthday-357371.mp3" type="audio/mpeg">
  </audio>
</main>

<script>
  const btn = document.getElementById('playBtn');
  const audio = document.getElementById('song');
  let playing = false;

  btn.addEventListener('click', async (e) => {
    e.preventDefault();
    try {
      if (!playing) {
        await audio.play();
        btn.textContent = '⏸️ Jeda Lagu';
        playing = true;
      } else {
        audio.pause();
        btn.textContent = '▶️ COBA PLAY';
        playing = false;
      }
    } catch (err) {
      alert('Audio gagal diputar. Pastikan file MP3 ada & path benar.');
    }
  });

  audio.addEventListener('ended', () => {
    btn.textContent = '▶️ COBA PLAY';
    playing = false;
  });
</script>

</body>
</html>
