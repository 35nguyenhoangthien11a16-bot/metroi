# metroi
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>❤️ đôi lời gửi cậu </title>
  <style>
    :root{
      --bg: #ffdee9; --card:#fff0f6; --accent:#ff4da6; --accent-2:#ff7ec3; --text:#3d003d; --muted:#6a4c6a;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0; font-family: 'Comic Sans MS', cursive, sans-serif; background: linear-gradient(135deg, #ffdee9, #b5fffc); color:var(--text);}
    .wrap{min-height:100%; display:grid; place-items:center; padding:24px}

    .card{width:min(600px, 92vw); background:var(--card); border:2px solid var(--accent); border-radius:24px; box-shadow: 0 10px 30px rgba(0,0,0,.2); padding:24px; position:relative; overflow:hidden}

    .title{display:flex; gap:10px; align-items:center; font-weight:800; letter-spacing:.3px; font-size:22px; margin:0 0 12px; color:var(--accent)}
    .title .dot{width:12px; height:12px; border-radius:50%; background:linear-gradient(135deg, var(--accent), var(--accent-2)); box-shadow:0 0 14px var(--accent)}

    .preview{border-radius:18px; padding:20px; background:linear-gradient(180deg, rgba(255,255,255,.6), rgba(255,255,255,.3)); border:2px dashed var(--accent-2); position:relative; min-height:220px; text-align:center}

    .btn{appearance:none; border:none; cursor:pointer; padding:12px 18px; border-radius:14px; font-weight:700; color:white; background:linear-gradient(135deg, var(--accent), var(--accent-2)); box-shadow: 0 8px 20px rgba(255,77,166,.35); transition: transform .08s ease, filter .2s ease}
    .btn:active{transform: translateY(1px)}

    .muted{color:var(--muted); font-size:13px}

    /* Modal */
    dialog{ width:min(420px, 92vw); border:none; border-radius:22px; padding:0; background:#fff0f6; color:var(--text); box-shadow: 0 20px 80px rgba(0,0,0,.3); }
    dialog::backdrop{background: rgba(0,0,0,.3);}
    .modal-head{padding:16px 18px; display:flex; align-items:center; justify-content:space-between; border-bottom:2px solid var(--accent-2)}
    .modal-title{display:flex; gap:10px; font-weight:800; letter-spacing:.2px; color:var(--accent)}
    .modal-body{padding:22px 22px 10px; text-align:center}
    .love{font-size:28px; font-weight:900; line-height:1.25; color:var(--accent)}
    .sub{margin-top:8px; color:#6a4c6a}
    .modal-actions{display:flex; gap:10px; padding:0 22px 22px; justify-content:center}
    .btn-ghost{background:transparent; border:2px solid var(--accent-2); color:var(--accent)}

    /* Floating hearts */
    .heart{position:absolute; font-size:20px; animation:rise 3.6s linear forwards; opacity:.9}
    @keyframes rise{ 0%{ transform: translateY(0) scale(.9); opacity:.95 } 90%{opacity:1} 100%{ transform: translateY(-140px) scale(1.2); opacity:0 } }
  </style>
</head>
<body>
  <audio id="bgm" loop>
    <source src="music.mp3" type="audio/mpeg">
  </audio>

  <div class="wrap">
    <div class="card">
      <h1 class="title"><span class="dot"></span> THÔNG BÁO  !!!</h1>
      <div class="preview" id="preview">
        <p class="muted">nhắc nhở nhỏ nhẹ 💖</p>
        <button class="btn" id="open">💖 Nhấp dzô đê </button>
        <p class="muted" style="margin-top:10px">blablabla 🎶</p>
      </div>
    </div>
  </div>

  <!-- Modal -->
  <dialog id="dlg">
    <div class="modal-head">
      <div class="modal-title">❤️ Thông báo tình yêu</div>
      <button class="btn btn-ghost" id="closeTop">✕</button>
    </div>
    <div class="modal-body">
      <div class="love">Anh yêu bé 💕</div>
      <div class="sub">Cảm ơn bé đã luôn dễ thương mỗi ngày 🥰</div>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost" id="close">Đóng</button>
      <button class="btn" id="ok">Hehe 🥰</button>
    </div>
  </dialog>

  <script>
    // --- Modal logic ---
    const dlg = document.getElementById('dlg');
    const openBtn = document.getElementById('open');
    const closeBtn = document.getElementById('close');
    const closeTop = document.getElementById('closeTop');
    const okBtn = document.getElementById('ok');
    const preview = document.getElementById('preview');
    const audio = document.getElementById('bgm');

    function openModal(){
      dlg.showModal();
      burstHearts();
      audio.play().catch(err=>console.log("Autoplay bị chặn, phải click mới phát được:" ,err));
    }
    function closeModal(){ dlg.close(); }

    openBtn.addEventListener('click', openModal);
    closeBtn.addEventListener('click', closeModal);
    closeTop.addEventListener('click', closeModal);
    okBtn.addEventListener('click', ()=>{ closeModal(); setTimeout(()=>burstHearts(24), 80); });

    // Auto show modal on page load
    window.addEventListener('load', ()=>{ setTimeout(openModal, 500); });

    // --- Floating hearts effect ---
    function burstHearts(n=16){
      const bounds = preview.getBoundingClientRect();
      for(let i=0;i<n;i++){
        const span = document.createElement('span');
        span.className = 'heart';
        span.textContent = Math.random() > .5 ? '💖' : '💗';
        const x = 24 + Math.random()*(bounds.width-48);
        const y = bounds.height - 28 + Math.random()*12;
        span.style.left = x + 'px';
        span.style.bottom = (bounds.height - y) + 'px';
        span.style.animationDuration = (2.4 + Math.random()*1.8) + 's';
        preview.appendChild(span);
        setTimeout(()=> span.remove(), 4200);
      }
    }
  </script>
</body>
</html>
