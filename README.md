<!doctype html>
<html lang="pl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <title>Wiara Przenosi Góry — Aktualizacja</title>

  <!-- Czcionki -->
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Roboto:wght@400;700&display=swap" rel="stylesheet">

  <style>
    :root{
      /* Kolory i style według opisu */
      --navy: #1e3a8a;
      --quote-grad-start: #3b5998;
      --quote-grad-end: #5a8dee;
      --point-blue: #2b7bd6;

      --card-bg: #f7fbff;
      --round-radius: 12px;
      --shadow-1: 0 10px 30px rgba(6,21,52,0.12);
      --shadow-2: 0 6px 18px rgba(59,89,152,0.08);
      --accent-text: #071a3a;
      --glass: rgba(255,255,255,0.95);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      min-height:100vh;
      font-family: "Roboto", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      color: var(--accent-text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;

      /* Zmienione tło na żądany gradient: góra #a0c7e3, dół #cbe6f8 */
      background: linear-gradient(180deg, #a0c7e3 0%, #cbe6f8 100%);
      display:flex;
      align-items:center;
      justify-content:center;
      padding:20px;
    }

    .container{
      width:100%;
      max-width:820px;
      border-radius: 16px;
      padding:22px;
      box-shadow: var(--shadow-1), var(--shadow-2);
      position:relative;
      overflow:hidden;
      background: linear-gradient(180deg, rgba(255,255,255,0.98), rgba(245,250,255,0.95));
      border: 1px solid rgba(30,58,138,0.06);
    }

    header{
      display:flex;
      gap:14px;
      align-items:center;
      margin-bottom:8px;
    }

    .logo-badge{
      width:64px;height:64px;
      border-radius:14px;
      background: linear-gradient(135deg,var(--quote-grad-start),var(--quote-grad-end));
      display:flex;
      align-items:center;
      justify-content:center;
      color:white;
      font-weight:700;
      box-shadow: 0 8px 28px rgba(59,89,152,0.14);
      font-family: "Roboto";
      flex-shrink:0;
    }

    h1{
      margin:0;
      font-family: "Pacifico", cursive;
      font-size:36px;
      color:var(--navy);
      letter-spacing:0.6px;
      line-height:1;
    }

    .card{
      margin-top:12px;
      background: linear-gradient(180deg, rgba(255,255,255,0.96), var(--card-bg));
      border-radius: var(--round-radius);
      padding:18px;
      box-shadow: var(--shadow-2);
    }

    .update-note{
      display:flex;
      gap:14px;
      align-items:center;
      flex-direction:row;
    }

    .note-text{
      flex:1;
      font-size:15px;
      color:#16314f;
    }

    .btn{
      appearance:none;
      border:0;
      padding:12px 18px;
      border-radius:14px;
      font-weight:700;
      cursor:pointer;
      font-family: "Roboto";
      background: linear-gradient(90deg, var(--quote-grad-start), var(--quote-grad-end));
      color:white;
      box-shadow: 0 10px 26px rgba(59,89,152,0.14);
      transition: transform .15s ease, box-shadow .15s ease, opacity .12s ease;
      text-decoration:none;
      display:inline-flex;
      align-items:center;
      justify-content:center;
    }
    .btn:active{ transform: translateY(1px) }
    .btn[disabled]{ opacity:0.6; cursor:not-allowed; transform:none }

    .muted{
      color:#4b6a98; font-size:14px;
    }

    /* Progress area */
    .progress-wrap{
      margin-top:18px;
      display:grid;
      grid-template-columns: 1fr 110px;
      gap:16px;
      align-items:center;
    }

    .progress-column{
      display:flex;
      flex-direction:column;
      gap:10px;
    }

    .progress-bar{
      width:100%;
      height:18px;
      background: linear-gradient(90deg, rgba(30,58,138,0.08), rgba(30,58,138,0.03));
      border-radius:999px;
      overflow:hidden;
      position:relative;
    }

    .progress-filled{
      height:100%;
      width:0%;
      background: linear-gradient(90deg, var(--quote-grad-start), var(--quote-grad-end));
      border-radius:999px;
      transition: width 0.25s linear;
      box-shadow: 0 6px 16px rgba(59,89,152,0.12) inset;
    }

    .progress-meta{
      display:flex;
      justify-content:space-between;
      font-size:13px;
      color:#274060;
      align-items:center;
    }

    .percent-bubble{
      width:96px;height:96px;border-radius:16px;
      display:flex;flex-direction:column;align-items:center;justify-content:center;
      background: linear-gradient(180deg, #ffffff, #f6fbff);
      box-shadow: 0 16px 40px rgba(6,21,52,0.12);
      font-weight:700;
      border: 1px solid rgba(30,58,138,0.06);
      flex-shrink:0;
    }
    .percent-bubble .big{ font-size:22px; color:var(--navy) }
    .percent-bubble .small{ font-size:12px; color: #4f6ca6 }

    .complete{
      margin-top:18px;
      padding:14px;
      border-radius:12px;
      background: linear-gradient(180deg, rgba(59,89,152,0.03), rgba(90,141,238,0.01));
      border: 1px dashed rgba(30,58,138,0.06);
    }
    .completion-list{ margin:8px 0 12px 0; padding-left:18px; color:#16324a; }
    .completion-list li{ margin-bottom:6px; font-weight:500 }

    .hint{ font-size:13px; color:#2b5ea3 }

    .hidden{ display:none !important }

    /* pulse animation for button */
    .pulse {
      animation: pulse .95s infinite;
    }
    @keyframes pulse {
      0% { transform: translateY(0) scale(1) }
      50% { transform: translateY(-2px) scale(1.01) }
      100% { transform: translateY(0) scale(1) }
    }

    /* RESPONSYWNOŚĆ - szczególnie dla telefonów w pionie */
    @media (max-width:760px){
      .container{ padding:18px; border-radius:14px; }
      .logo-badge{ width:56px;height:56px;border-radius:12px; }
      h1{ font-size:30px; }
      .progress-wrap{ grid-template-columns: 1fr 84px; gap:12px; align-items:center; }
      .percent-bubble{ width:84px;height:84px; }
      .progress-bar{ height:14px; }
      .btn{ padding:12px 16px; border-radius:12px; font-size:15px; }
      .note-text{ font-size:15px }
    }

    @media (max-width:420px){
      .container{ padding:16px; border-radius:12px; }
      header{ gap:12px; align-items:flex-start; }
      .update-note{ flex-direction:column; align-items:stretch; gap:12px; }
      .progress-wrap{ grid-template-columns: 1fr; }
      .percent-bubble{ width:72px;height:72px; margin:0 auto; }
      .progress-meta{ flex-direction:column; align-items:flex-start; gap:6px; }
      .card{ padding:14px; }
      .btn{ width:100%; justify-content:center; }
    }
  </style>
</head>
<body>
  <div class="container" role="application" aria-labelledby="app-title">
    <header>
      <div class="logo-badge" aria-hidden="true">WPG</div>
      <div>
        <h1 id="app-title">Wiara Przenosi Góry</h1>
      </div>
    </header>

    <main>
      <div class="card" id="card-root">
        <!-- initial update prompt -->
        <div id="initial" class="update-note">
          <div style="flex:1">
            <div class="note-text" id="note-text">
              <strong>Aplikacja wymaga aktualizacji</strong><br>
              Zaaktualizuj ją aby móc z niej korzystać.
            </div>
            <div class="muted" style="margin-top:10px">Wymagane: <strong id="required-mb">385mb</strong></div>
          </div>

          <div style="display:flex;flex-direction:column;gap:10px;align-items:flex-end">
            <button id="update-btn" class="btn pulse" aria-label="Zaaktualizuj">Zaaktualizuj</button>
            <div class="hint" id="start-hint">Kliknij by rozpocząć</div>
          </div>
        </div>

        <!-- progress area (hidden initially) -->
        <div id="progress-area" class="hidden" style="margin-top:12px">
          <div class="progress-wrap">
            <div class="progress-column">
              <div class="progress-bar" aria-hidden="true">
                <div id="progress-filled" class="progress-filled" style="width:0%"></div>
              </div>

              <div class="progress-meta" aria-live="polite">
                <div>
                  <div style="font-size:13px;color:#133050">Pobrano: <strong id="downloaded">0 MB</strong> / <span id="total-mb">385 MB</span></div>
                  <div style="font-size:13px;color:#133050">Pozostały czas: <strong id="time-left">03:00</strong></div>
                </div>
                <div style="text-align:right">
                  <div class="muted">Szybkość: <span id="speed">—</span></div>
                </div>
              </div>
            </div>

            <div style="display:flex;align-items:center;justify-content:flex-end">
              <div class="percent-bubble" aria-hidden="true">
                <div class="big" id="percent">0%</div>
                <div class="small">zakt.</div>
              </div>
            </div>
          </div>
        </div>

        <!-- completion card (hidden initially) -->
        <div id="completion" class="complete hidden" aria-live="polite">
          <div style="font-weight:700; color:var(--navy)">Uruchom Zaaktualizowaną Wersję Bloga z:</div>
          <ul class="completion-list">
            <li>Nowym Wpisem</li>
            <li>Poprawą Błędów</li>
            <li>Drobnymi poprawkami kosmetycznymi</li>
          </ul>

          <div style="display:flex;gap:12px;align-items:center;flex-wrap:wrap">
            <a id="launch-link" class="btn" href="https://blogwpg.my.canva.site/" target="_blank" rel="noopener">Uruchom</a>
            <div class="muted">Kliknij by otworzyć bloga</div>
          </div>
        </div>

      </div>
    </main>
  </div>

  <script>
    /* Polski UI — symulacja działania (bez adnotacji "symulacja") */
    (function(){
      const TOTAL_MB = 385;
      const TOTAL_SECONDS = 180; // 3 minuty
      const REDIRECT_URL = 'https://blogwpg.my.canva.site/';
      const STORAGE_KEY = 'wpg_updated_v1';

      const updateBtn = document.getElementById('update-btn');
      const initialEl = document.getElementById('initial');
      const progressArea = document.getElementById('progress-area');
      const progressFilled = document.getElementById('progress-filled');
      const downloadedEl = document.getElementById('downloaded');
      const percentEl = document.getElementById('percent');
      const timeLeftEl = document.getElementById('time-left');
      const speedEl = document.getElementById('speed');
      const completionEl = document.getElementById('completion');
      const noteText = document.getElementById('note-text');

      // jeśli już zaktualizowane — automatycznie otwórz link (zgodnie z wymaganiem)
      if (localStorage.getItem(STORAGE_KEY) === '1') {
        window.location.href = REDIRECT_URL;
      }

      // generuje losowe kroki tak, żeby suma_dur = TOTAL_SECONDS i suma_mb = TOTAL_MB
      function generateSteps(count){
        const durWeights = new Array(count).fill(0).map(()=> Math.random() + 0.15 );
        const mbWeights  = new Array(count).fill(0).map(()=> Math.random() + 0.15 );

        const durSum = durWeights.reduce((a,b)=>a+b,0);
        const mbSum = mbWeights.reduce((a,b)=>a+b,0);

        const durations = durWeights.map(w => w / durSum * TOTAL_SECONDS); // seconds
        const mbs = mbWeights.map(w => w / mbSum * TOTAL_MB); // MB

        const cumDur = [];
        const cumMB = [];
        let d=0, m=0;
        for (let i=0;i<count;i++){
          d += durations[i];
          m += mbs[i];
          cumDur.push(d);
          cumMB.push(m);
        }
        const lastIdx = count-1;
        cumDur[lastIdx] = TOTAL_SECONDS;
        cumMB[lastIdx] = TOTAL_MB;

        return {durations, cumDur, cumMB};
      }

      function formatTimeSeconds(s){
        if (s < 0) s = 0;
        s = Math.round(s);
        const mm = Math.floor(s/60);
        const ss = s % 60;
        return String(mm).padStart(2,'0') + ':' + String(ss).padStart(2,'0');
      }

      updateBtn.addEventListener('click', startUpdate);

      function startUpdate(){
        updateBtn.disabled = true;
        initialEl.style.display = 'none';
        progressArea.classList.remove('hidden');
        noteText.innerHTML = '<strong>Trwa aktualizacja…</strong><br>Proszę nie zamykać okna.';

        const STEPS = 90 + Math.floor(Math.random()*40); // 90-129 kroków
        const {durations, cumDur, cumMB} = generateSteps(STEPS);

        const startTime = performance.now();
        let rafId = null;

        function frame(){
          const now = performance.now();
          const elapsedSec = (now - startTime)/1000;
          const clampedElapsed = Math.min(elapsedSec, TOTAL_SECONDS);

          let idx = cumDur.findIndex(x => x >= clampedElapsed);
          if (idx === -1) idx = cumDur.length - 1;
          const prevCum = idx === 0 ? 0 : cumMB[idx-1];
          const prevTime = idx === 0 ? 0 : cumDur[idx-1];
          const nextCum = cumMB[idx];
          const nextTime = cumDur[idx];

          const ratio = nextTime === prevTime ? 1 : (clampedElapsed - prevTime)/(nextTime - prevTime);
          const currentMB = prevCum + (nextCum - prevCum) * ratio;

          const percent = Math.min(100, currentMB / TOTAL_MB * 100);

          progressFilled.style.width = percent + '%';
          downloadedEl.textContent = currentMB >= TOTAL_MB ? `${TOTAL_MB} MB` : `${currentMB.toFixed(1)} MB`;
          percentEl.textContent = Math.floor(percent) + '%';

          const remaining = Math.max(0, TOTAL_SECONDS - clampedElapsed);
          timeLeftEl.textContent = formatTimeSeconds(remaining);

          const speed = elapsedSec > 0 ? (currentMB / elapsedSec) : 0;
          speedEl.textContent = elapsedSec < 0.5 ? '—' : speed.toFixed(1) + ' MB/s';

          if (clampedElapsed < TOTAL_SECONDS) {
            rafId = requestAnimationFrame(frame);
          } else {
            cancelAnimationFrame(rafId);
            finishUpdate();
          }
        }

        rafId = requestAnimationFrame(frame);
      }

      function finishUpdate(){
        localStorage.setItem(STORAGE_KEY, '1');

        progressFilled.style.width = '100%';
        downloadedEl.textContent = TOTAL_MB + ' MB';
        percentEl.textContent = '100%';
        timeLeftEl.textContent = '00:00';
        speedEl.textContent = '—';

        completionEl.classList.remove('hidden');
      }

      document.getElementById('required-mb').textContent = TOTAL_MB + 'mb';
      document.getElementById('total-mb').textContent = TOTAL_MB + ' MB';

      // accessibility: enter key triggers
      updateBtn.addEventListener('keydown', (e)=>{
        if (e.key === 'Enter' || e.key === ' ') {
          e.preventDefault();
          updateBtn.click();
        }
      });

    })();
  </script>
</body>
</html>
