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
  aspect-ratio:1/1; /* مربع دائم */
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
#botHeader button {background: transparent;border: none;font-size: 20px;cursor: pointer;}
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

<!-- صفحات (كل صفحة عنصر .page) -->
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

<!-- صفحة الشخصيات (تفتح عند الضغط على الشخصيات) -->
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
/* ---------------------------
   قاعدة البيانات الداخلية (قابلة للتوسيع)
   --------------------------- */
const DB = {
  animes:[{id:'onepiece',title:'One Piece',year:1999,eps:1000,desc:'رحلة مونكي دي لوفي وطاقمه للعثور على الكنز الأسطوري One Piece.',cover:'https://i.ibb.co/5KXftx8/luffy.jpg'}],
  characters:[
    {id:'luffy',name:'مونكي دي. لوفي',role:'قائد طاقم قبعة القش',img:'luffy.jpg',desc:'قائد مغامر وله قوة فاكهة غومو غومو.',powers:'فاكهة الشيطان: غومو غومو — هاكي'},
    {id:'zoro',name:'رورونوا زورو',role:'سياف الطاقم',img:'zoro.jpg',desc:'سيفي يسعى لأن يصبح أعظم سيفي.',powers:'تقنيات السيف • هاكي'},
    {id:'nami',name:'نامي',role:'الملاح',img:'nami.jpg',desc:'ملاح بارع وخبيرة الطقس.',powers:'مهارات ملاحة واستخدام الكليما تاكت'},
    {id:'sanji',name:'سانجي',role:'الطباخ',img:'sanji.jpg',desc:'طباخ الطاقم ومقاتل بأسلوب الركل.',powers:'قوة بدنية وتقنيات قتالية'}
  ],
  crew:['luffy','zoro','nami','sanji'],
  powers:[
    {id:'devilfruits',title:'الفواكه الشيطانية',desc:'أنواع فواكه الشيطان: باراميشيا، زو، لوجيا.'},
    {id:'haki',title:'الهاكي',desc:'قوة روحية تعطي تحكماً في القوة.'}
  ],
  episodes:[
    {id:'ep1',anime:'onepiece',num:1,title:'بداية الرحلة',summary:'لوفي يغادر قريته ويشرع في رحلته.'},
    {id:'ep37',anime:'onepiece',num:37,title:'اللقاء مع زورو',summary:'انضمام زورو إلى الطاقم.'}
  ],
  maps:[{id:'grandline',title:'الجراند لاين',desc:'الممر البحري الرئيسي في عالم ون بيس.'},{id:'wano',title:'مملكة وانو',desc:'أراضي تقليدية ذات ثقافة يابانية قوية.'}],
};

/* ---------------------------
   عناصر DOM مركزية
   --------------------------- */
const charactersGrid = document.getElementById('charactersGrid');
const charactersList = document.getElementById('charactersList');
const crewList = document.getElementById('crewList');
const epList = document.getElementById('epList');
const episodesFull = document.getElementById('episodesFull');
const gallery = document.getElementById('gallery');
const miniArticles = document.getElementById('miniArticles');
const mapsList = document.getElementById('mapsList');

/* ---------------------------
   التخزين: المفضلات والنجوم
   --------------------------- */
function favKey(){ return 'ag_onepiece_favs_v1'; }
function getFavs(){ return JSON.parse(localStorage.getItem(favKey())||'[]'); }
function toggleFavId(id){
  const favs = getFavs();
  if(favs.includes(id)){ localStorage.setItem(favKey(), JSON.stringify(favs.filter(x=>x!==id))); return false; }
  favs.push(id); localStorage.setItem(favKey(), JSON.stringify(favs)); return true;
}
function starsKey(){ return 'ag_onepiece_stars_v1'; }
function getStarMap(){ return JSON.parse(localStorage.getItem(starsKey())||'{}'); }
function setStar(id,val){ const m=getStarMap(); m[id]=val; localStorage.setItem(starsKey(), JSON.stringify(m)); }

/* ---------------------------
   إنشاء بطاقة شخصية (مستخدمة في عدة صفحات)
   - النقر على البطاقة يفتح المودال
   - النجوم قابلة للنقر وتُخزن
   - القلب (المفضلة) أبيض افتراضياً ويصبح أحمر عند الضغط
   --------------------------- */
function makeCharCard(c){
  const d = document.createElement('div');
  d.className = 'card visible';
  d.innerHTML = `
    <div class='thumb'><img loading='lazy' src='${c.img}' alt='${c.name}'></div>
    <div class='meta'>
      <h3>${escapeHtml(c.name)}</h3>
      <p class='muted'>${escapeHtml(c.role)}</p>
      <div class="stars" data-id="${c.id}">
        <span data-i="1">★</span><span data-i="2">★</span><span data-i="3">★</span><span data-i="4">★</span><span data-i="5">★</span>
      </div>
      <div style="margin-top:8px">
        <span class="heart" data-id="${c.id}" title="أضف إلى المفضلات">♡</span>
      </div>
    </div>
  `;

  // فتح المودال عند الضغط على البطاقة (باستثناء النجوم أو القلب)
  d.addEventListener('click', (ev)=>{
    const target = ev.target;
    if(target.closest('.stars') || target.classList.contains('heart')) return;
    openModal('character', c.id);
  });

  // إعداد النجوم (عرض وحفظ)
  const stars = d.querySelector('.stars');
  const starSpans = Array.from(stars.querySelectorAll('span'));
  function refreshStars(){
    const cur = getStarMap()[c.id] || 0;
    starSpans.forEach(s=>{
      const i = Number(s.dataset.i);
      if(i <= cur) s.classList.add('active'); else s.classList.remove('active');
    });
  }
  starSpans.forEach(s=>{
    s.addEventListener('click', (e)=>{
      e.stopPropagation();
      const i = Number(s.dataset.i);
      setStar(c.id, i);
      refreshStars();
    });
  });
  refreshStars();

  // إعداد القلب (مفضلة)
  const heart = d.querySelector('.heart');
  function refreshHeart(){
    if(getFavs().includes(c.id)) heart.classList.add('liked'); else heart.classList.remove('liked');
  }
  heart.addEventListener('click', (e)=>{
    e.stopPropagation();
    const liked = toggleFavId(c.id);
    if(liked) heart.classList.add('liked'); else heart.classList.remove('liked');
  });
  refreshHeart();

  return d;
}

/* ---------------------------
   رندر الصفحة الرئيسية والصفحات الأخرى
   --------------------------- */
function createArticle(title, excerpt){
  const a = document.createElement('article');
  a.className = 'panel';
  a.style.padding = '12px';
  a.innerHTML = `<h3>${escapeHtml(title)}</h3><p class="muted" style="margin-top:8px">${escapeHtml(excerpt)}</p>`;
  return a;
}

function renderHome(){
  charactersGrid.innerHTML = '';
  DB.characters.forEach(ch => charactersGrid.appendChild(makeCharCard(ch)));

  epList.innerHTML = '';
  DB.episodes.forEach(e=>{
    const el = document.createElement('div');
    el.className = 'episode';
    el.innerHTML = `<div><strong>#${e.num} — ${escapeHtml(e.title)}</strong><div class="muted">${escapeHtml(e.summary||'')}</div></div><div class="muted">${escapeHtml(e.anime)}</div>`;
    epList.appendChild(el);
  });

  gallery.innerHTML = '';
  DB.characters.forEach(c=>{
    const img = document.createElement('img');
    img.src = c.img;
    img.alt = c.name;
    gallery.appendChild(img);
  });

  miniArticles.innerHTML = '';
  miniArticles.appendChild(createArticle('ما هي الفواكه الشيطانية؟','شرح مبسط لأنواع الفواكه وقيودها.'));
  miniArticles.appendChild(createArticle('مفهوم الهاكي','أنواعه وكيف يعمل في القتال.'));

  observeCards();
}

function renderCharactersPage(){
  charactersList.innerHTML = '';
  DB.characters.forEach(c => charactersList.appendChild(makeCharCard(c)));
  observeCards();
}

function renderCrewPage(){
  crewList.innerHTML = '';
  DB.crew.forEach(id=>{
    const c = DB.characters.find(x=>x.id===id);
    if(c) crewList.appendChild(makeCharCard(c));
  });
  observeCards();
}

function renderPowersPage(){
  const box = document.getElementById('powersList');
  if(!box) return;
  box.innerHTML = '';
  DB.powers.forEach(p=>{
    const art = createArticle(p.title, p.desc);
    box.appendChild(art);
  });
}

function renderEpisodesPage(){
  if(!episodesFull) return;
  episodesFull.innerHTML = '';
  DB.episodes.forEach(e=>{
    const d = document.createElement('div');
    d.className = 'panel';
    d.style.marginBottom = '10px';
    d.innerHTML = `<strong>#${e.num} — ${escapeHtml(e.title)}</strong><p class="muted">${escapeHtml(e.summary||'')}</p><button class="btn" onclick="openModal('episode','${e.id}')">عرض</button>`;
    episodesFull.appendChild(d);
  });
}

function renderMapsPage(){
  mapsList.innerHTML = '';
  DB.maps.forEach(m=>{
    const d = document.createElement('div');
    d.className = 'card';
    d.style.padding = '12px';
    d.innerHTML = `<div class='meta'><h3>${escapeHtml(m.title)}</h3><p class='muted'>${escapeHtml(m.desc)}</p></div><div class='actions'><button class='btn' onclick="openModal('map','${m.id}')">عرض</button></div>`;
    mapsList.appendChild(d);
  });
  observeCards();
}

/* ---------------------------
   Modal (تفاصيل)
   --------------------------- */
const modal = document.getElementById('modal');
function openModal(type, id){
  playClick();
  let data = null;
  if(type === 'character') data = DB.characters.find(x=>x.id===id);
  if(type === 'episode') data = DB.episodes.find(x=>x.id===id);
  if(type === 'map') data = DB.maps.find(x=>x.id===id);
  if(!data){ alert('لا توجد بيانات'); return; }
  document.getElementById('modalTitle').textContent = data.title || data.name;
  document.getElementById('modalImg').src = data.img || data.cover || '';
  document.getElementById('modalDesc').textContent = data.desc || data.summary || '';
  document.getElementById('modalInfo').textContent = (data.powers?('قدرات: '+data.powers):'') + (data.year?(' • عام: '+data.year):'');
  modal.classList.add('open');
}
function closeModal(e){ if(e && e.stopPropagation) e.stopPropagation(); modal.classList.remove('open'); }

/* ---------------------------
   click sound placeholder (music removed as requested)
   --------------------------- */
const clickSfx = null;
function playClick(){ try{ if(clickSfx) clickSfx.play(); }catch(e){} }

/* ---------------------------
   IntersectionObserver للبطاقات (تأثير الظهور)
   --------------------------- */
function observeCards(){
  const cards = document.querySelectorAll('.card');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(en=>{
      if(en.isIntersecting){ en.target.classList.add('visible'); io.unobserve(en.target); }
    });
  },{threshold:0.12});
  cards.forEach(c => io.observe(c));
}

/* ---------------------------
   مساعدة: حماية من XSS في النصوص
   --------------------------- */
function escapeHtml(s){
  if(!s) return '';
  return String(s).replace(/[&<>"']/g, ch => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[ch]));
}

/* ---------------------------
   بحث محلي داخل DB
   --------------------------- */
document.getElementById('searchInput').addEventListener('input', e=>{
  const q = e.target.value.trim().toLowerCase();
  if(!q){ showPage('home'); renderHome(); return; }
  const ch = DB.characters.filter(x=> x.name.toLowerCase().includes(q) || x.role.toLowerCase().includes(q));
  const ep = DB.episodes.filter(x=> (''+x.num).includes(q) || x.title.toLowerCase().includes(q));
  const pw = DB.powers.filter(x=> x.title.toLowerCase().includes(q) || x.desc.toLowerCase().includes(q));
  charactersGrid.innerHTML = '';
  ch.forEach(c => charactersGrid.appendChild(makeCharCard(c)));
  epList.innerHTML = '';
  ep.forEach(e=>{ const el=document.createElement('div'); el.className='episode'; el.innerHTML=`<div><strong>#${e.num} — ${escapeHtml(e.title)}</strong><div class="muted">${escapeHtml(e.summary||'')}</div></div><div class="muted">${escapeHtml(e.anime)}</div>`; epList.appendChild(el); });
  miniArticles.innerHTML = '';
  pw.forEach(p=> miniArticles.appendChild(createArticle(p.title,p.desc)));
  observeCards();
});

/* ---------------------------
   Navigation SPA بسيطة (عرض صفحة في نفس الملف)
   --------------------------- */
document.querySelectorAll('nav a').forEach(a=> a.addEventListener('click', navClick));
function navClick(e){
  e.preventDefault();
  document.querySelectorAll('nav a').forEach(x=>x.classList.remove('active'));
  this.classList.add('active');
  const t = this.dataset.target;
  showPage(t);
  if(t === 'home'){ renderHome(); }
  if(t === 'characters'){ renderCharactersPage(); }
  if(t === 'crew'){ renderCrewPage(); }
  if(t === 'powers'){ renderPowersPage(); }
  if(t === 'episodes'){ renderEpisodesPage(); }
  if(t === 'maps'){ renderMapsPage(); }
}
function showPage(key){
  const pages = document.querySelectorAll('.page');
  pages.forEach(p=> p.style.display = 'none');
  if(key === 'home') document.getElementById('home').style.display = 'grid';
  else document.getElementById('home').style.display = 'none';
  const mapping = {
    'characters':'charactersPage',
    'crew':'crewPage',
    'powers':'powersPage',
    'episodes':'episodesPage',
    'maps':'mapsPage'
  };
  Object.values(mapping).forEach(id => {
    const el = document.getElementById(id);
    if(el) el.style.display = 'none';
  });
  if(mapping[key]){
    const el = document.getElementById(mapping[key]);
    if(el) el.style.display = 'block';
  }
}

/* ---------------------------
   Theme toggle (داكن/فاتح)
   --------------------------- */
document.getElementById('themeToggle').addEventListener('click', ()=>{
  const el = document.body;
  const t = el.getAttribute('data-theme') || 'dark';
  const next = t === 'dark' ? 'light' : 'dark';
  el.setAttribute('data-theme', next);
  localStorage.setItem('ag_theme', next);
});
(function(){ const t=localStorage.getItem('ag_theme')||'dark'; document.body.setAttribute('data-theme',t); })();

/* ---------------------------
   Init: render home & fill lists
   --------------------------- */
renderHome();
renderCharactersPage();
renderCrewPage();
renderPowersPage();
renderEpisodesPage();
renderMapsPage();

/* ---------------------------
   close modal on esc
   --------------------------- */
document.addEventListener('keydown', e=>{ if(e.key === 'Escape') closeModal(); });

/* ---------------------------
   Bot (قواعد بسيطة، مع حفظ المحادثة في localStorage)
   --------------------------- */
const BOT_KB = [
  {q:['لوفي','luffy'], a:'لوفي هو قائد طاقم قبعة القش. حلمه أن يصبح ملك القراصنة!'},
  {q:['زورو'], a:'زورو هو السياف الأول في الطاقم، يستخدم ثلاث سيوف.'},
  {q:['سانجي'], a:'سانجي هو طباخ الطاقم، يستخدم قدميه في القتال.'},
  {q:['نامي'], a:'نامي هي ملاح الطاقم وخبيرة الطقس.'}
];

function botQuery(text){
  const t = text.trim().toLowerCase();
  for(const item of BOT_KB){
    for(const k of item.q) if(t.includes(k)) return item.a;
  }
  return 'عذرًا، لم أجد إجابة لهذا السؤال.';
}

const botIcon = document.getElementById('botIcon');
const botPopup = document.getElementById('botPopup');
const botMessages2 = document.getElementById('botMessages2');
const botInput2 = document.getElementById('botInput2');
const botSend2 = document.getElementById('botSend2');

botIcon.addEventListener('click', ()=> {
  botPopup.style.display = (botPopup.style.display === 'flex') ? 'none' : 'flex';
  botPopup.style.flexDirection = 'column';
});

botSend2.addEventListener('click', sendBotMessage);
botInput2.addEventListener('keydown', e=>{ if(e.key === 'Enter') sendBotMessage(); });

function addBotMsg(type, text){
  const d = document.createElement('div');
  d.className = 'msg ' + (type === 'user' ? 'user' : 'bot');
  d.textContent = text;
  botMessages2.appendChild(d);
  botMessages2.scrollTop = botMessages2.scrollHeight;
}
function sendBotMessage(){
  const txt = botInput2.value.trim();
  if(!txt) return;
  addBotMsg('user', txt);
  botInput2.value = '';
  saveBotMemory();
  setTimeout(()=>{
    const ans = botQuery(txt);
    addBotMsg('bot', ans);
    saveBotMemory();
  }, 300);
}
function saveBotMemory(){
  localStorage.setItem('botChat', botMessages2.innerHTML);
}
function loadBotMemory(){
  const d = localStorage.getItem('botChat');
  if(d) botMessages2.innerHTML = d;
}
loadBotMemory();

/* ---------------------------
   safety: expose helpers globally when needed by inline handlers
   --------------------------- */
window.openModal = openModal;
window.closeModal = closeModal;

</script>
</body>
</html>
