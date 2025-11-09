<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>AG ANIME — موسوعة ون بيس الشاملة</title>
<meta name="description" content="AG ANIME — موقع متخصص في أنمي ONE PIECE، معلومات عن الحلقات، الشخصيات، القوى، الخرائط." />
<style>
:root{
  --bg:#000000; --panel:#070707; --card:#0b0b0b; --accent:#ff3b3b; --accent-2:#ffb86b; --muted:#bdbdbd; --glass:rgba(255,255,255,0.03); --radius:14px; --shadow:0 18px 60px rgba(0,0,0,0.8);
  --text:#ffffff;
}
[data-theme='light']{
  --bg:#f6f6f7; --panel:#ffffff; --card:#ffffff; --accent:#d84315; --accent-2:#ff7043; --muted:#444; --glass:rgba(0,0,0,0.03); --text:#111;
}

*{box-sizing:border-box}
html,body{height:100%;margin:0;font-family:'Cairo',Tajawal,system-ui,Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;overflow-x:hidden}

.wrap{max-width:1300px;margin:18px auto;padding:18px;display:grid;grid-template-rows:auto 1fr auto;gap:18px}

header{display:flex;justify-content:space-between;align-items:center;gap:12px;padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);backdrop-filter:blur(6px);position:sticky;top:12px;z-index:90}
.brand{display:flex;align-items:center;gap:12px}
.logo{width:64px;height:64px;border-radius:12px;overflow:hidden;border:2px solid rgba(255,255,255,0.03)}
.logo img{width:100%;height:100%;object-fit:cover}
h1{font-size:20px;margin:0}
.tag{color:var(--muted);font-size:13px}

nav{display:flex;gap:8px;align-items:center}
nav a{color:var(--muted);text-decoration:none;padding:8px 12px;border-radius:10px;font-size:14px;cursor:pointer}
nav a.active{background:linear-gradient(90deg, rgba(255,59,59,0.12), rgba(255,184,107,0.06));color:var(--text);border:1px solid rgba(255,59,59,0.08)}

.controls{display:flex;gap:10px;align-items:center}
.search{display:flex;align-items:center;gap:8px;background:var(--glass);padding:8px 12px;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}
.search input{background:transparent;border:0;outline:none;color:var(--text);width:220px}

.content{display:grid;grid-template-columns:2fr 420px;gap:18px}
.panel{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);padding:18px;border-radius:var(--radius);border:1px solid rgba(255,255,255,0.03);box-shadow:var(--shadow)}
h2{color:var(--accent);margin:0 0 12px 0}

.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:14px}
.card{display:flex;gap:12px;align-items:center;padding:12px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.02);transition:transform .28s ease,box-shadow .28s;opacity:0;transform:translateY(18px)}
.card.visible{opacity:1;transform:none}
.thumb{flex:0 0 120px;height:120px;border-radius:12px;overflow:hidden;border:1px solid rgba(255,255,255,0.03);display:flex;align-items:center;justify-content:center;background:#111;}
.thumb img{
  width:100%;
  height:100%;
  aspect-ratio:1/1;
  object-fit:cover;
  display:block;
  border-radius:0;
}

.meta{flex:1}
.meta h3{margin:0;font-size:16px}
.meta p{margin:6px 0 0 0;color:var(--muted);font-size:14px}

.actions{display:flex;flex-direction:column;gap:8px}
.btn{padding:8px 10px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--muted);cursor:pointer}
.btn.primary{background:linear-gradient(90deg,var(--accent),var(--accent-2));border:0;color:#111}

/* زر التقييم والقلب */
.card .stars{display:flex;gap:6px;margin-top:8px}
.card .stars span{cursor:pointer;font-size:18px;color:rgba(255,255,255,0.18);transition:color .18s}
.card .stars span.active{color:gold;text-shadow:0 0 8px rgba(255,215,0,0.15)}
.card .heart{cursor:pointer;font-size:22px;color:white;user-select:none;transition:color .3s ease;margin-top:8px;display:inline-block}
.card .heart.liked{color:red}

/* Sidebar */
.sidebar .section{margin-bottom:12px}
.episodes{max-height:360px;overflow:auto;padding-right:6px}
.episode{display:flex;justify-content:space-between;align-items:center;padding:10px;border-radius:10px;background:rgba(0,0,0,0.25);border:1px solid rgba(255,255,255,0.02);margin-bottom:8px}

.gallery{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.gallery img{width:100%;height:100px;object-fit:cover;border-radius:8px;border:1px solid rgba(255,255,255,0.03)}

.modal{position:fixed;inset:0;display:grid;place-items:center;background:rgba(0,0,0,0.7);visibility:hidden;opacity:0;transition:opacity .18s,visibility .18s}
.modal.open{visibility:visible;opacity:1}
.modal-card{width:min(1000px,96%);background:linear-gradient(180deg,#0b0b0c,#060606);padding:18px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);box-shadow:0 30px 80px rgba(0,0,0,0.85)}
.modal-row{display:flex;gap:18px}
.modal-row img{width:360px;height:360px;object-fit:cover;border-radius:10px}

/* Navigation pages (hidden by default) */
.page{display:none}

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
#botHeader button {background: linear-gradient(90deg,#000,#fff);border: none;font-size: 20px;cursor: pointer;border-radius:6px;}
#botMessages2 {flex: 1;padding: 10px;overflow-y: auto;display: flex;flex-direction: column;gap: 8px;}
#botMessages2 .msg.user {align-self: flex-end;background: rgba(255,255,255,0.1);color: var(--text);padding: 8px;border-radius: 8px;}
#botMessages2 .msg.bot {align-self: flex-start;background: rgba(255,59,59,0.15);color: var(--text);padding: 8px;border-radius: 8px;}
#botInputRow {display: flex;gap: 6px;padding: 10px;border-top: 1px solid rgba(255,255,255,0.05);}
#botInput2 {flex: 1;padding: 8px;border-radius: 8px;border: 1px solid rgba(255,255,255,0.1);background: transparent;color: var(--text);}
#botSend2 {padding: 8px 10px;background: linear-gradient(90deg, var(--accent), var(--accent-2));border: none;border-radius: 8px;cursor: pointer;color: #111;}

@media (max-width:980px){.content{grid-template-columns:1fr} header{flex-direction:column;align-items:flex-start} .logo{width:50px;height:50px}}
@media (max-width:600px){h1{font-size:16px} nav a{font-size:13px;padding:5px 8px} .btn{font-size:13px} #botPopup{right:10px;bottom:80px;width:calc(100% - 20px);max-height:60vh;} #botIcon{bottom:10px;right:10px;width:56px;height:56px;font-size:26px}}

.muted{color:var(--muted)}
</style>
</head>
<body data-theme="dark">
<div class="wrap">
<header>
  <div class="brand">
    <div class="logo"><img src="https://i.ibb.co/6X9Gk2B/ag-anime-emblem.png" alt="AG ANIME"></div>
    <div>
      <h1>AG ANIME — موسوعة ون بيس</h1>
      <div class="tag">كل ما تحتاجه عن One Piece: شخصيات، حلقات، قوى، خرائط ومزيد.</div>
    </div>
  </div>

  <div class="controls">
    <nav>
      <a href="#home" class="active" data-target="home">الرئيسية</a>
      <a href="#characters" data-target="characters">الشخصيات</a>
      <a href="#crew" data-target="crew">طاقم قبعة القش</a>
      <a href="#powers" data-target="powers">القوى والهاكي</a>
      <a href="#episodes" data-target="episodes">الحلقات والمانجا</a>
      <a href="#maps" data-target="maps">الخرائط</a>
    </nav>
    <div class="search" role="search">
      <svg width="16" height="16" viewBox="0 0 24 24" stroke="var(--accent)" stroke-width="1.6" fill="none"><circle cx="11" cy="11" r="6"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input id="searchInput" placeholder="ابحث: شخصية، حلقة، قوة ..." aria-label="بحث" />
    </div>
    <button class="theme-toggle" id="themeToggle">تبديل الثيم</button>
  </div>
</header>

<!-- المحتوى الرئيسي -->
<main id="home" class="content page" style="display:block">
  <section class="panel">
    <h2>نظرة عامة — ون بيس</h2>
    <p class="muted">مرحبًا بك في قسم One Piece. هنا تجد ملفات مفصلة عن الشخصيات، الطاقم، الفواكه الشيطانية، الهاكي، وقوائم الحلقات والمانجا.</p>

    <h2 style="margin-top:16px">شخصيات بارزة</h2>
    <div id="charactersGrid" class="grid"></div>

    <h2 style="margin-top:18px">مقالات مختارة</h2>
    <div id="miniArticles"></div>
  </section>

  <aside class="sidebar panel">
    <div class="section">
      <h3 style="color:var(--accent)">الحلقات الأخيرة</h3>
      <div class="episodes" id="epList"></div>
    </div>

    <div class="section">
      <h3 style="color:var(--accent)">معرض</h3>
      <div class="gallery" id="gallery"></div>
    </div>
  </aside>
</main>

<!-- صفحات إضافية -->
<section id="charactersPage" class="panel page" style="display:none;max-width:1300px;margin:18px auto">
  <h2 style="color:var(--accent)">قائمة الشخصيات</h2>
  <div id="charactersList" class="grid"></div>
</section>

<section id="crewPage" class="panel page" style="display:none;max-width:1300px;margin:18px auto">
  <h2 style="color:var(--accent)">طاقم قبعة القش</h2>
  <div id="crewList" class="grid"></div>
</section>

<section id="powersPage" class="panel page" style="display:none;max-width:1300px;margin:18px auto">
  <h2 style="color:var(--accent)">الفواكه الشيطانية وهاكي</h2>
  <div id="powersList"></div>
</section>

<section id="episodesPage" class="panel page" style="display:none;max-width:1300px;margin:18px auto">
  <h2 style="color:var(--accent)">الحلقات والمانجا</h2>
  <div id="episodesFull"></div>
</section>

<section id="mapsPage" class="panel page" style="display:none;max-width:1300px;margin:18px auto">
  <h2 style="color:var(--accent)">الخرائط والمناطق</h2>
  <div id="mapsList" class="grid"></div>
</section>

<footer style="text-align:center;color:var(--muted);padding:12px 0">© 2025 — AG ANIME — One Piece Edition</footer>
</div>

<!-- Modal تفاصيل -->
<div id="modal" class="modal" onclick="closeModal(event)">
  <div class="modal-card" role="dialog" aria-modal="true" onclick="event.stopPropagation()">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
      <h3 id="modalTitle"></h3>
      <button class="btn" onclick="closeModal()">إغلاق</button>
    </div>
    <div class="modal-row">
      <img id="modalImg" src="" alt="media">
      <div style="flex:1">
        <p id="modalDesc" class="muted"></p>
        <p style="margin-top:10px"><strong>معلومات أساسية:</strong> <span id="modalInfo"></span></p>
      </div>
    </div>
  </div>
</div>

<!-- بوت -->
<div id="botIcon">🤖</div>
<div id="botPopup">
  <div id="botHeader">بوت الموقع <button onclick="document.getElementById('botPopup').style.display='none'">×</button></div>
  <div id="botMessages2"></div>
  <div id="botInputRow">
    <input type="text" id="botInput2" placeholder="اكتب رسالتك...">
    <button id="botSend2">إرسال</button>
  </div>
</div>

<script>
// --------------------------------
// قاعدة البيانات
// --------------------------------
const DB = {
  animes:[{id:'onepiece',title:'One Piece',year:1999,eps:1000,desc:'رحلة مونكي دي لوفي وطاقمه للعثور على الكنز الأسطوري One Piece.',cover:'https://i.ibb.co/5KXftx8/luffy.jpg'}],
  characters:[
    {id:'luffy',name:'مونكي دي. لوفي',role:'قائد طاقم قبعة القش',img:'https://i.ibb.co/5KXftx8/luffy.jpg',desc:'قائد مغامر وله قوة فاكهة غومو غومو.',powers:'فاكهة الشيطان: غومو غومو — هاكي'},
    {id:'zoro',name:'رورونوا زورو',role:'سياف الطاقم',img:'https://i.ibb.co/2NsfwKg/zoro.jpg',desc:'سيفي يسعى لأن يصبح أعظم سيفي.',powers:'هاكي ملكي وهاكي تسللي'}
  ]
}

// --------------------------------
// وظائف البوت
// --------------------------------
const botIcon = document.getElementById('botIcon');
const botPopup = document.getElementById('botPopup');
const botInput = document.getElementById('botInput2');
const botSend = document.getElementById('botSend2');
const botMessages = document.getElementById('botMessages2');

botIcon.onclick = ()=>botPopup.style.display = 'flex';
botSend.onclick = ()=>{
  const val = botInput.value.trim();
  if(!val) return;
  botMessages.innerHTML += `<div class="msg user">${val}</div>`;
  botInput.value='';
  // رد تلقائي بسيط
  let reply = 'عذرًا، هذه النسخة تجريبية. سأجيب لاحقًا!';
  for(let c of DB.characters){
    if(val.includes(c.name.split(' ')[0])) reply=`معلومات عن ${c.name}: ${c.desc}`;
  }
  botMessages.innerHTML += `<div class="msg bot">${reply}</div>`;
  botMessages.scrollTop = botMessages.scrollHeight;
}

// --------------------------------
// المودال
// --------------------------------
function openModal(title,img,desc,info){
  document.getElementById('modalTitle').textContent = title;
  document.getElementById('modalImg').src = img;
  document.getElementById('modalDesc').textContent = desc;
  document.getElementById('modalInfo').textContent = info;
  document.getElementById('modal').classList.add('open');
}
function closeModal(e){if(!e||e.target.classList.contains('modal'))document.getElementById('modal').classList.remove('open')}

// --------------------------------
// عرض الشخصيات
// --------------------------------
const charactersGrid = document.getElementById('charactersGrid');
DB.characters.forEach(c=>{
  const card = document.createElement('div');
  card.className='card visible';
  card.innerHTML=`
    <div class="thumb"><img src="${c.img}" alt="${c.name}"></div>
    <div class="meta">
      <h3>${c.name}</h3>
      <p>${c.role}</p>
      <div class="stars">
        <span data-star="1">★</span>
        <span data-star="2">★</span>
        <span data-star="3">★</span>
        <span data-star="4">★</span>
        <span data-star="5">★</span>
      </div>
      <div class="heart">❤</div>
      <button class="btn primary">تفاصيل</button>
    </div>
  `;
  charactersGrid.appendChild(card);

  // النجوم
  card.querySelectorAll('.stars span').forEach(star=>{
    star.addEventListener('click', ()=> {
      card.querySelectorAll('.stars span').forEach(s=>s.classList.remove('active'));
      for(let i=1;i<=parseInt(star.dataset.star);i++) card.querySelector(`.stars span[data-star="${i}"]`).classList.add('active');
    })
  })

  // القلوب
  const heart = card.querySelector('.heart');
  heart.onclick = ()=>heart.classList.toggle('liked');

  // تفاصيل
  card.querySelector('button').onclick = ()=>openModal(c.name,c.img,c.desc,c.powers);
});

// --------------------------------
// تغيير الثيم
// --------------------------------
document.getElementById('themeToggle').onclick = ()=>{
  document.body.dataset.theme = document.body.dataset.theme==='dark'?'light':'dark';
}

// --------------------------------
// التنقل بين الصفحات
// --------------------------------
document.querySelectorAll('nav a').forEach(a=>{
  a.onclick = e=>{
    e.preventDefault();
    document.querySelectorAll('.page').forEach(p=>p.style.display='none');
    const target = document.getElementById(a.dataset.target+'Page') || document.getElementById(a.dataset.target);
    if(target) target.style.display='block';
    document.querySelectorAll('nav a').forEach(n=>n.classList.remove('active'));
    a.classList.add('active');
  }
})

// --------------------------------
// البحث
// --------------------------------
document.getElementById('searchInput').oninput = e=>{
  const val = e.target.value.toLowerCase();
  document.querySelectorAll('.card').forEach(card=>{
    const text = card.querySelector('h3').textContent.toLowerCase();
    card.style.display = text.includes(val)?'flex':'none';
  })
}
</script>
</body>
</html>
