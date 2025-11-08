<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AG ANIME — موسوعة ون بيس الشاملة</title>
  <meta name="description" content="AG ANIME — موقع متخصص في أنمي ONE PIECE، معلومات عن الحلقات، الشخصيات، القوى، الخرائط، ومساعد AG-BOT الذكي الخاص بون بيس." />
  <style>
    :root{
      --bg:#000000; --panel:#070707; --card:#0b0b0b; --accent:#ff3b3b; --accent-2:#ffb86b;
      --muted:#bdbdbd; --glass:rgba(255,255,255,0.03); --radius:14px; --shadow:0 18px 60px rgba(0,0,0,0.8);
      --text:#ffffff;
    }
    [data-theme='light']{
      --bg:#f6f6f7; --panel:#ffffff; --card:#ffffff; --accent:#d84315;
      --accent-2:#ff7043; --muted:#444; --glass:rgba(0,0,0,0.03); --text:#111;
    }

    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%;font-family:'Cairo',Tajawal,system-ui,Arial,sans-serif;
      background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;overflow-x:hidden}

    .wrap{max-width:1300px;margin:auto;padding:18px;display:grid;grid-template-rows:auto 1fr auto;gap:18px}
    header{display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:12px;
      padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);
      backdrop-filter:blur(6px);position:sticky;top:12px;z-index:90}
    .brand{display:flex;align-items:center;gap:12px;flex:1;min-width:220px}
    .logo{width:56px;height:56px;border-radius:12px;overflow:hidden;border:2px solid rgba(255,255,255,0.03)}
    .logo img{width:100%;height:100%;object-fit:cover}
    h1{font-size:18px;margin:0}
    .tag{color:var(--muted);font-size:13px}

    nav{display:flex;flex-wrap:wrap;gap:6px;align-items:center;justify-content:center}
    nav a{color:var(--muted);text-decoration:none;padding:6px 10px;border-radius:10px;font-size:14px;white-space:nowrap}
    nav a.active{background:linear-gradient(90deg, rgba(255,59,59,0.12), rgba(255,184,107,0.06));
      color:var(--text);border:1px solid rgba(255,59,59,0.08)}

    .controls{display:flex;flex-wrap:wrap;gap:8px;align-items:center;justify-content:center;width:100%}
    .search{display:flex;align-items:center;gap:8px;background:var(--glass);padding:8px 12px;border-radius:12px;
      border:1px solid rgba(255,255,255,0.03);flex:1;max-width:320px}
    .search input{background:transparent;border:0;outline:none;color:var(--text);width:100%;font-size:14px}

    .content{display:grid;grid-template-columns:2fr 420px;gap:18px}
    .panel{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);padding:18px;border-radius:var(--radius);
      border:1px solid rgba(255,255,255,0.03);box-shadow:var(--shadow)}
    h2{color:var(--accent);margin-bottom:12px;font-size:20px}

    .grid{display:grid;grid-template-columns:repeat(auto-fit, minmax(200px, 1fr));gap:14px}
    .card{display:flex;gap:12px;align-items:center;padding:12px;border-radius:12px;
      background:linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.02);transition:transform .28s ease,box-shadow .28s}
    .thumb{flex:0 0 100px;height:100px;border-radius:10px;overflow:hidden}
    .thumb img{width:100%;height:100%;object-fit:cover}
    .meta h3{margin:0;font-size:16px}
    .meta p{margin:4px 0;color:var(--muted);font-size:13px}
    .btn{padding:8px 10px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);
      background:transparent;color:var(--muted);cursor:pointer}
    .btn.primary{background:linear-gradient(90deg,var(--accent),var(--accent-2));border:0;color:#111}

    footer{text-align:center;color:var(--muted);padding:12px 0;font-size:13px}

    /* البوت المنبثق */
    #botIcon {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 64px;
      height: 64px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), var(--accent-2));
      display: flex;
      justify-content: center;
      align-items: center;
      color: #111;
      font-size: 30px;
      cursor: pointer;
      box-shadow: 0 4px 18px rgba(0,0,0,0.4);
      z-index: 9999;
    }

    #botPopup {
      position: fixed;
      bottom: 100px;
      right: 20px;
      width: 320px;
      max-height: 480px;
      background: #0f0f10;
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 14px;
      box-shadow: 0 20px 50px rgba(0,0,0,0.8);
      display: none;
      flex-direction: column;
      z-index: 9999;
      overflow: hidden;
    }

    #botHeader {
      background: linear-gradient(90deg, var(--accent), var(--accent-2));
      padding: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: #111;
      font-weight: bold;
    }

    #botHeader button {
      background: transparent;
      border: none;
      font-size: 20px;
      cursor: pointer;
    }

    #botMessages2 {
      flex: 1;
      padding: 10px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    #botMessages2 .msg.user {
      align-self: flex-end;
      background: rgba(255,255,255,0.1);
      color: var(--text);
      padding: 8px;
      border-radius: 8px;
    }

    #botMessages2 .msg.bot {
      align-self: flex-start;
      background: rgba(255,59,59,0.15);
      color: var(--text);
      padding: 8px;
      border-radius: 8px;
    }

    #botInputRow {
      display: flex;
      gap: 6px;
      padding: 10px;
      border-top: 1px solid rgba(255,255,255,0.05);
    }

    #botInput2 {
      flex: 1;
      padding: 8px;
      border-radius: 8px;
      border: 1px solid rgba(255,255,255,0.1);
      background: transparent;
      color: var(--text);
    }

    #botSend2 {
      padding: 8px 10px;
      background: linear-gradient(90deg, var(--accent), var(--accent-2));
      border: none;
      border-radius: 8px;
      cursor: pointer;
      color: #111;
    }

    /* responsive */
    @media (max-width:980px){
      .content{grid-template-columns:1fr}
      header{flex-direction:column;align-items:flex-start}
      .logo{width:50px;height:50px}
    }
    @media (max-width:600px){
      h1{font-size:16px}
      nav a{font-size:13px;padding:5px 8px}
      .btn{font-size:13px}
      #botPopup{right:10px;width:90%;bottom:90px}
      #botIcon{bottom:10px;right:10px;width:56px;height:56px}
    }
  </style>
</head>

<body data-theme="dark">

  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo"><img src="https://i.imgur.com/z8E5eBa.png" alt="Logo"></div>
        <div>
          <h1>AG ANIME</h1>
          <div class="tag">موسوعة ون بيس الشاملة</div>
        </div>
      </div>
      <nav>
        <a href="#">الرئيسية</a>
        <a href="#">الشخصيات</a>
        <a href="#">الخرائط</a>
      </nav>
    </header>

    <main class="content">
      <section class="panel">
        <h2>أهلاً بك في موسوعة ون بيس</h2>
        <p>هنا يمكنك استكشاف كل ما يتعلق بعالم ون بيس، الشخصيات، القوى، والمواقع.</p>
      </section>
    </main>

    <footer>© 2025 AG ANIME</footer>
  </div>

  <!-- أيقونة البوت -->
  <div id="botIcon">💬</div>

  <!-- نافذة البوت -->
  <div id="botPopup">
    <div id="botHeader">
      AG-BOT
      <button id="botClose">&times;</button>
    </div>
    <div id="botMessages2"></div>
    <div id="botInputRow">
      <input id="botInput2" placeholder="اكتب سؤالك...">
      <button id="botSend2">إرسال</button>
    </div>
  </div>

  <script>
    const botIcon = document.getElementById('botIcon');
    const botPopup = document.getElementById('botPopup');
    const botClose = document.getElementById('botClose');
    const botSend2 = document.getElementById('botSend2');
    const botInput2 = document.getElementById('botInput2');
    const botMessages2 = document.getElementById('botMessages2');

    // قاعدة بيانات بسيطة
    const BOT_KB = [
      {q:['لوفي','luffy'], a:'لوفي هو قائد طاقم قبعة القش. حلمه أن يصبح ملك القراصنة!'},
      {q:['زورو'], a:'زورو هو السياف الأول في الطاقم، يستخدم ثلاث سيوف في القتال.'},
      {q:['سانجي'], a:'سانجي هو الطباخ الشهير في طاقم لوفي، يستخدم قدميه فقط في القتال.'},
      {q:['نامي'], a:'نامي هي الملاحة الذكية في الطاقم، تحب المال والخرائط!'},
      {q:['اينيل','إنيل'], a:'إنيل هو إله البرق في جزيرة سكايبيا.'},
    ];

    function botQuery(text){
      const t = text.trim().toLowerCase();
      for(const item of BOT_KB){
        for(const k of item.q) if(t.includes(k)) return item.a;
      }
      return 'عذرًا، لم أجد إجابة لهذا السؤال.';
    }

    // عرض / إخفاء البوت
    botIcon.onclick = () => botPopup.style.display = 'flex';
    botClose.onclick = () => botPopup.style.display = 'none';

    // إرسال الرسائل
    botSend2.onclick = sendMessage;
    botInput2.addEventListener('keydown', e => { if(e.key === 'Enter') sendMessage(); });

    function sendMessage(){
      const text = botInput2.value.trim();
      if(!text) return;
      addMsg('user', text);
      botInput2.value = '';
      setTimeout(()=>{
        const reply = botQuery(text);
        addMsg('bot', reply);
        saveMemory();
      },400);
      saveMemory();
    }

    function addMsg(type, text){
      const div = document.createElement('div');
      div.className = 'msg ' + type;
      div.textContent = text;
      botMessages2.appendChild(div);
      botMessages2.scrollTop = botMessages2.scrollHeight;
    }

    // تخزين الذاكرة في localStorage
    function saveMemory(){
      localStorage.setItem('botChat', botMessages2.innerHTML);
    }

    function loadMemory(){
      const data = localStorage.getItem('botChat');
      if(data) botMessages2.innerHTML = data;
    }

    loadMemory();
  </script>
</body>
</html>
