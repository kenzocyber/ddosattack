# ddosattack
<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>⚠️ SITE UNDER ATTACK | KENZO</title>
<style>
  :root{
    --bg:#050608;
    --red:#ff375f;
    --neon:#00ffe0;
    --muted:#9aa2ad;
    --glass:rgba(255,255,255,0.03);
    --mono:ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", monospace;
  }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:var(--mono);background:linear-gradient(180deg,#030405,#071019);color:#e6eef8}
  /* full-screen centered */
  .wrap{height:100vh;display:flex;align-items:center;justify-content:center;padding:20px}
  .card{
    width:100%;max-width:940px;border-radius:14px;padding:24px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);
    border:1px solid rgba(255,255,255,0.04);backdrop-filter:blur(6px);box-shadow:0 20px 60px rgba(2,6,12,0.7)
  }
  .row{display:flex;gap:18px;flex-wrap:wrap;align-items:flex-start}
  .left{flex:1;min-width:260px}
  .right{width:300px;min-width:260px}
  h1{font-size:1.5rem;margin:0;letter-spacing:1px}
  .subtitle{color:var(--muted);margin-top:8px;font-size:0.92rem}
  /* Glitch headline */
  .glitch{
    position:relative;display:inline-block;font-weight:800;font-size:1.25rem;margin-top:12px;
    color:transparent;
    -webkit-text-stroke:1px rgba(255,255,255,0.02);
    background:linear-gradient(90deg,var(--red),#ff8a6b 40%,var(--neon));
    -webkit-background-clip:text;background-clip:text;
  }
  .glitch::before,.glitch::after{
    content:attr(data-text);
    position:absolute;left:0;top:0;
    width:100%;overflow:hidden;
  }
  .glitch::before{
    left:2px;text-shadow:-2px 0 var(--red);clip-path: inset(0 0 50% 0);
    animation:glitchTop 2.2s infinite linear;
  }
  .glitch::after{
    left:-2px;text-shadow:-2px 0 var(--neon);clip-path: inset(50% 0 0 0);
    animation:glitchBottom 1.8s infinite linear;
  }
  @keyframes glitchTop{0%{transform:translate(0,0)}20%{transform:translate(-6px,-3px)}40%{transform:translate(2px,-1px)}60%{transform:translate(-2px,0)}80%{transform:translate(0,0)}100%{transform:translate(0,0)}}
  @keyframes glitchBottom{0%{transform:translate(0,0)}15%{transform:translate(6px,3px)}35%{transform:translate(-2px,1px)}55%{transform:translate(2px,0)}75%{transform:translate(0,0)}100%{transform:translate(0,0)}}
  /* terminal-like panel */
  .term{
    background:#03050a;border-radius:10px;padding:12px;border:1px solid rgba(255,255,255,0.03);font-size:0.92rem;
    color:#9fd3ff;height:220px;overflow:auto;white-space:pre-wrap;
  }
  .term .line.err{color:var(--red)}
  .term .line.warn{color:#ffd38a}
  .term .line.ok{color:#9fd3ff}
  /* attack meter */
  .meter{background:rgba(255,255,255,0.03);border-radius:10px;padding:12px;border:1px solid rgba(255,255,255,0.03)}
  .bar-wrap{height:10px;background:rgba(255,255,255,0.02);border-radius:999px;overflow:hidden;margin-top:8px}
  .bar{height:100%;width:0%;background:linear-gradient(90deg,var(--red),#ff9fa8)}
  .stat{display:flex;justify-content:space-between;align-items:center;font-size:0.88rem;color:var(--muted)}
  .badge{display:inline-block;padding:6px 8px;border-radius:999px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);font-weight:700}
  /* simulated traffic chart (sparkline) */
  .spark{height:48px;display:flex;gap:4px;align-items:end;margin-top:8px}
  .spark > i{flex:1;background:linear-gradient(180deg,#ff6b7a,#ff1f3a);border-radius:4px;opacity:0.95}
  .controls{display:flex;gap:8px;margin-top:12px}
  .btn{padding:8px 10px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);cursor:pointer;color:var(--neon);font-weight:700}
  .btn.warn{color:var(--red)}
  .small{font-size:0.82rem;color:var(--muted);margin-top:8px}
  footer.note{margin-top:14px;font-size:0.78rem;color:var(--muted);text-align:center}
  /* mobile tweaks */
  @media(max-width:860px){
    .row{flex-direction:column}
    .right{width:100%}
    .term{height:160px}
  }
</style>
</head>
<body>
  <div class="wrap">
    <div class="card" role="main" aria-labelledby="attack-title">
      <div class="row">
        <div class="left">
          <h1 id="attack-title">⚠️ SITE UNDER ATTACK</h1>
          <div class="subtitle">This site has been targeted by a high-volume DDoS attack.</div>

          <div class="glitch" data-text="BLACK HAT CYBER | KENZO">BLACK HAT CYBER | KENZO</div>

          <div style="margin-top:14px" class="term" id="terminal" aria-live="polite">
            <div class="line err">[ALERT] Incoming traffic spike detected — SYN flood pattern.</div>
            <div class="line warn">[WARN] Connection queues filling... mitigation recommended.</div>
            <div class="line ok">[INFO] Monitoring active. Timestamp: <span id="ts">--:--:--</span></div>
            <div class="line" id="flow">[FLOW] Current connections: 0 | Peak: 0</div>
            <div class="line" id="attack-src">[SOURCE] Multiple vectors detected (masked IPs)</div>
            <div class="line" style="margin-top:8px;color:#c8c8c8">
              NOTE: This is a simulated defacement/alert interface for demonstration & awareness only.
            </div>
          </div>

          <div class="small">Purpose: demonstration — use this UI for awareness, incident drills, or themed page. Not a real compromise.</div>

        </div>

        <div class="right">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="badge">INTRUSION DETECTED</div>
              <div class="small" style="margin-top:6px">Mitigation Status</div>
            </div>
            <div style="text-align:right">
              <div style="font-weight:800;font-size:1.3rem;color:var(--red)" id="status-text">ACTIVE</div>
              <div class="small">Severity: <strong style="color:var(--red)">CRITICAL</strong></div>
            </div>
          </div>

          <div style="margin-top:12px" class="meter">
            <div class="stat"><span>Attack Intensity</span><span id="pct">0%</span></div>
            <div class="bar-wrap" aria-hidden="true"><div class="bar" id="bar"></div></div>

            <div class="stat" style="margin-top:10px"><span>Connections</span><span id="conns">0</span></div>
            <div class="spark" id="spark">
              <!-- bars injected by JS -->
            </div>

            <div class="controls">
              <button class="btn" id="btn-sim">Start Simulation</button>
              <button class="btn warn" id="btn-stop">Stop</button>
              <button class="btn" id="btn-reset">Reset</button>
            </div>

            <div class="small">Indicator shows simulated traffic load. No real network actions performed.</div>
          </div>

          <div style="margin-top:12px" class="small">
            <div><strong>Notice:</strong> If this were real, contact your hosting provider & enable rate limiting / WAF / CDN-based mitigation.</div>
          </div>
        </div>
      </div>

      <footer class="note">Simulation generated by <strong>Kenzo | Payakumbuh Cyber Hub</strong> — For education & awareness.</footer>
    </div>
  </div>

<script>
  // Simulated attack UI (visual only). No networking or malicious actions.
  const bar = document.getElementById('bar');
  const pct = document.getElementById('pct');
  const conns = document.getElementById('conns');
  const ts = document.getElementById('ts');
  const flow = document.getElementById('flow');
  const attackSrc = document.getElementById('attack-src');
  const terminal = document.getElementById('terminal');
  const spark = document.getElementById('spark');
  const statusText = document.getElementById('status-text');

  let running = false;
  let interval = null;
  let peak = 0;

  // create spark columns
  function initSpark(){
    spark.innerHTML = '';
    for(let i=0;i<12;i++){
      const el = document.createElement('i');
      el.style.height = Math.max(4, Math.floor(Math.random()*60)) + 'px';
      spark.appendChild(el);
    }
  }
  initSpark();

  function updateTime(){ 
    const d = new Date();
    ts.textContent = d.toLocaleTimeString();
  }
  updateTime(); setInterval(updateTime,1000);

  function randomInt(min,max){ return Math.floor(Math.random()*(max-min+1))+min; }

  function stepSim(){
    // simulate connections and intensity
    const con = randomInt(2000, 50000);
    const intensity = Math.min(100, Math.round((con/50000)*100 + randomInt(-8,8)));
    const pctVal = Math.max(0,Math.min(100,intensity));
    if(con > peak) peak = con;

    // update UI
    bar.style.width = pctVal + '%';
    pct.textContent = pctVal + '%';
    conns.textContent = con.toLocaleString();
    flow.textContent = `[FLOW] Current connections: ${con.toLocaleString()} | Peak: ${peak.toLocaleString()}`;

    // update sparkbars
    const items = spark.querySelectorAll('i');
    items.forEach(i=>{
      const h = Math.max(4, Math.floor((Math.random()*pctVal/100)*80));
      i.style.height = (h+4) + 'px';
      i.style.opacity = 0.7 + Math.random()*0.3;
    });

    // terminal log append
    const lines = [
      `[ALERT] High request rate from multiple sources. SYN/UDP amplification patterns observed.`,
      `[WARN] Rate limiting triggered on edge nodes; observed bypass attempts.`,
      `[INFO] Auto-mitigation toggled: CDN rules applied.`,
      `[TRACE] Sources masked by proxy chains. Geo: multiple regions.`,
      `[HINT] Consider blackhole routing or scrubbing service (simulated).`
    ];
    const ln = document.createElement('div');
    ln.className = 'line';
    ln.textContent = lines[randomInt(0,lines.length-1)];
    // occasionally mark error
    if(pctVal > 80 && Math.random() < 0.35){ ln.classList.add('err'); }
    terminal.appendChild(ln);
    terminal.scrollTop = terminal.scrollHeight;
    // update attack source placeholder (masked)
    attackSrc.textContent = `[SOURCE] Vectors: ${randomInt(3,12)} | Masked IPs: ${randomInt(120,999)} | Botnets: ${randomInt(1,12)}`;
  }

  document.getElementById('btn-sim').addEventListener('click', ()=>{
    if(running) return;
    running = true;
    statusText.textContent = 'ACTIVE';
    statusText.style.color = 'var(--red)';
    interval = setInterval(stepSim, 1200);
  });
  document.getElementById('btn-stop').addEventListener('click', ()=>{
    if(!running) return;
    running = false;
    clearInterval(interval);
    statusText.textContent = 'MITIGATING';
    statusText.style.color = '#ffd38a';
    // final log
    const ln = document.createElement('div'); ln.className='line warn'; ln.textContent='[WARN] Automated mitigation engaged. Traffic rerouted to scrubbing service (simulated).';
    terminal.appendChild(ln); terminal.scrollTop = terminal.scrollHeight;
  });
  document.getElementById('btn-reset').addEventListener('click', ()=>{
    running = false; clearInterval(interval); peak = 0;
    bar.style.width = '0%'; pct.textContent = '0%'; conns.textContent='0';
    flow.textContent = '[FLOW] Current connections: 0 | Peak: 0';
    statusText.textContent = 'INACTIVE'; statusText.style.color = 'var(--neon)';
    terminal.innerHTML = '<div class="line ok">[INFO] Simulation reset. Ready.</div>';
    initSpark();
  });

  // init terminal start line
  terminal.innerHTML = '<div class="line ok">[INFO] Synthetic DDoS simulation ready. Press "Start Simulation".</div>';
  statusText.style.color = 'var(--neon)'; statusText.textContent = 'INACTIVE';
</script>
</body>
</html>
