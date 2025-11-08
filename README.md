<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AG ANIME — موسوعة ون بيس الشاملة</title>
  <meta name="description" content="AG ANIME — موقع متخصص في أنمي ONE PIECE، معلومات عن الحلقات، الشخصيات، القوى، الخرائط، ومساعد AG-BOT الذكي الخاص بون بيس." />
  <style>
    :root{
      --bg:#000000; --panel:#070707; --card:#0b0b0b; --accent:#ff3b3b; --accent-2:#ffb86b; --muted:#bdbdbd; --glass:rgba(255,255,255,0.03); --radius:14px; --shadow:0 18px 60px rgba(0,0,0,0.8);
      --text:#ffffff;
    }
    [data-theme='light']{ --bg:#f6f6f7; --panel:#ffffff; --card:#ffffff; --accent:#d84315; --accent-2:#ff7043; --muted:#444; --glass:rgba(0,0,0,0.03); --text:#111; }

    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%;font-family:'Cairo',Tajawal,system-ui,Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;overflow-x:hidden}

    /* Layout */
    .wrap{max-width:1300px;margin:18px auto;padding:18px;display:grid;grid-template-rows:auto 1fr auto;gap:18px}
    header{display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:12px;padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);backdrop-filter:blur(6px);position:sticky;top:12px;z-index:90}
    .brand{display:flex;align-items:center;gap:12px;flex:1;min-width:220px}
    .logo{width:64px;height:64px;border-radius:12px;overflow:hidden;border:2px solid rgba(255,255,255,0.03)}
    .logo img{width:100%;height:100%;object-fit:cover;display:block}
    h1{font-size:20px;margin:0}
    .tag{color:var(--muted);font-size:13px}

    nav{display:flex;flex-wrap:wrap;gap:8px;align-items:center;justify-content:center}
    nav a{color:var(--muted);text-decoration:none;padding:8px 12px;border-radius:10px;font-size:14px;white-space:nowrap}
    nav a.active{background:linear-gradient(90deg, rgba(255,59,59,0.12), rgba(255,184,107,0.06));color:var(--text);border:1px solid rgba(255,59,59,0.08)}

    .controls{display:flex;flex-wrap:wrap;gap:10px;align-items:center;justify-content:flex-end}
    .search{display:flex;align-items:center;gap:8px;background:var(--glass);padding:8px 12px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);flex:0 1 320px;min-width:140px}
    .search input{background:transparent;border:0;outline:none;color:var(--text);width:100%;font-size:14px}

    /* Main grid */
    .content{display:grid;grid-template-columns:2fr 420px;gap:18px}
    .panel{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);padding:18px;border-radius:var(--radius);border:1px solid rgba(255,255,255,0.03);box-shadow:var(--shadow)}
    h2{color:var(--accent);margin:0 0 12px 0}

    /* Cards */
    .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
    .card{display:flex;gap:12px;align-items:center;padding:12px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.02);transition:transform .28s ease,box-shadow .28s;opacity:0;transform:translateY(18px)}
    .card.visible{opacity:1;transform:none}
    .thumb{flex:0 0 120px;height:120px;border-radius:10px;overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
    .thumb img{width:100%;height:100%;object-fit:cover;display:block}
    .meta{flex:1}
    .meta h3{margin:0;font-size:16px}
    .meta p{margin:6px 0 0 0;color:var(--muted);font-size:14px}
    .actions{display:flex;flex-direction:column;gap:8px}
    .btn{padding:8px 10px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--muted);cursor:pointer}
    .btn.primary{background:linear-gradient(90deg,var(--accent),var(--accent-2));border:0;color:#111}

    /* Sidebar */
    .sidebar .section{margin-bottom:12px}
    .episodes{max-height:360px;overflow:auto;padding-right:6px}
    .episode{display:flex;justify-content:space-between;align-items:center;padding:10px;border-radius:10px;background:rgba(0,0,0,0.25);border:1px solid rgba(255,255,255,0.02);margin-bottom:8px;gap:8px}

    .gallery{display:grid;grid-template-columns:repeat(auto-fit,minmax(80px,1fr));gap:8px}
    .gallery img{width:100%;height:100px;object-fit:cover;border-radius:8px;border:1px solid rgba(255,255,255,0.03)}

    /* Modal */
    .modal{position:fixed;inset:0;display:grid;place-items:center;background:rgba(0,0,0,0.7);visibility:hidden;opacity:0;transition:opacity .18s,visibility .18s;padding:20px}
    .modal.open{visibility:visible;opacity:1}
    .modal-card{width:min(1000px,100%);max-height:92vh;overflow:auto;background:linear-gradient(180deg,#0b0b0c,#060606);padding:18px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);box-shadow:0 30px 80px rgba(0,0,0,0.85)}
    .modal-row{display:flex;gap:18px;align-items:flex-start}
    .modal-row img{width:360px;height:360px;object-fit:cover;border-radius:10px;flex-shrink:0}

    /* Stars & ratings */
    .stars{display:flex;gap:6px;align-items:center}
    .star{font-size:20px;cursor:pointer;color:rgba(255,255,255,0.2)}
    .star.active{color:gold;text-shadow:0 0 8px rgba(255,215,0,0.2)}

    /* AG-BOT */
    .bot{background:#0f0f10;border-radius:12px;padding:12px;border:1px solid rgba(255,255,255,0.03)}
    .bot-messages{height:220px;overflow:auto;padding:8px;display:flex;flex-direction:column;gap:8px}
    .msg.user{align-self:flex-end;background:linear-gradient(90deg,rgba(255,255,255,0.04),rgba(255,255,255,0.02));padding:8px;border-radius:10px;color:var(--text)}
    .msg.bot{align-self:flex-start;background:rgba(255,59,59,0.06);padding:8px;border-radius:10px;color:var(--text)}

    /* Theme toggle */
    .theme-toggle{padding:8px 10px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);cursor:pointer;background:transparent;color:var(--muted)}

    /* Responsive */
    @media (max-width:980px){
      .content{grid-template-columns:1fr}
      .grid{grid-template-columns:repeat(auto-fit,minmax(180px,1fr))}
      .gallery{grid-template-columns:repeat(auto-fit,minmax(80px,1fr))}
      .search{flex:1;max-width:none}
      header{align-items:flex-start}
      .modal-row{flex-direction:column}
      .modal-row img{width:100%;height:auto}
      .bot-messages{height:180px}
    }
    @media (max-width:600px){
      .logo{width:48px;height:48px}
      h1{font-size:16px}
      .thumb{flex:0 0 88px;height:88px}
      .gallery img{height:90px}
      .modal-card{padding:12px}
      .bot-messages{height:160px}
      #musicControl{left:10px;bottom:10px;padding:10px 12px}
    }

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

      <div class="controls" style="flex:0 1 560px;">
        <nav>
          <a href="#home" class="active" data-target="home">الرئيسية</a>
          <a href="#characters" data-target="characters">الشخصيات</a>
          <a href="#crew" data-target="crew">طاقم قبعة القش</a>
          <a href="#powers" data-target="powers">القوى والهاكي</a>
          <a href="#episodes" data-target="episodes">الحلقات والمانجا</a>
          <a href="#maps" data-target="maps">الخرائط</a>
        </nav>
        <div class="search" role="search" aria-label="بحث">
          <svg width="16" height="16" viewBox="0 0 24 24" stroke="var(--accent)" stroke-width="1.6" fill="none"><circle cx="11" cy="11" r="6"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
          <input id="searchInput" placeholder="ابحث: شخصية، حلقة، قوة ..." aria-label="بحث" />
        </div>
        <button class="theme-toggle" id="themeToggle" aria-pressed="false">وضع/ليلي/نهاري</button>
      </div>
    </header>

    <main id="home" class="content">
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

        <div class="section">
          <h3 style="color:var(--accent)">AG-BOT (مساعد ون بيس)</h3>
          <div class="bot">
            <div id="botMessages" class="bot-messages" aria-live="polite"></div>
            <div style="display:flex;gap:8px;margin-top:8px">
              <input id="botInput" placeholder="اسأل AG-BOT (مثال: من أقوى مستخدم هاكي؟)" style="flex:1;padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--text)" />
              <button class="btn primary" id="botSend">اسأل</button>
            </div>
          </div>
        </div>

      </aside>
    </main>

    <!-- صفحات داخلية -->
    <section id="charactersPage" class="panel" style="display:none">
      <h2 style="color:var(--accent)">قائمة الشخصيات</h2>
      <div id="charactersList" class="grid"></div>
    </section>

    <section id="crewPage" class="panel" style="display:none">
      <h2 style="color:var(--accent)">طاقم قبعة القش</h2>
      <div id="crewList" class="grid"></div>
    </section>

    <section id="powersPage" class="panel" style="display:none">
      <h2 style="color:var(--accent)">الفواكه الشيطانية وهاكي</h2>
      <div id="powersList"></div>
    </section>

    <section id="episodesPage" class="panel" style="display:none">
      <h2 style="color:var(--accent)">الحلقات والمانجا</h2>
      <div id="episodesFull"></div>
    </section>

    <section id="mapsPage" class="panel" style="display:none">
      <h2 style="color:var(--accent)">الخرائط والمناطق</h2>
      <div id="mapsList" class="grid"></div>
    </section>

    <footer style="text-align:center;color:var(--muted);padding:12px 0">© 2025 — AG ANIME — One Piece Edition</footer>
  </div>

  <!-- Modal تفاصيل -->
  <div id="modal" class="modal" onclick="closeModal(event)" aria-hidden="true">
    <div class="modal-card" role="dialog" aria-modal="true" onclick="event.stopPropagation()">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;gap:12px;flex-wrap:wrap">
        <h3 id="modalTitle"></h3>
        <div>
          <span id="modalType" class="muted" style="margin-left:12px"></span>
          <button class="btn" onclick="closeModal()">إغلاق</button>
        </div>
      </div>
      <div class="modal-row">
        <img id="modalImg" src="" alt="media">
        <div style="flex:1;min-width:200px">
          <p id="modalDesc" class="muted"></p>
          <p style="margin-top:10px"><strong>معلومات أساسية:</strong> <span id="modalInfo"></span></p>
          <div style="margin-top:12px;display:flex;align-items:center;gap:12px;flex-wrap:wrap">
            <div>
              <div class="muted">تقييمك:</div>
              <div id="userStars" class="stars"></div>
            </div>
            <div>
              <button id="favBtn" class="btn">♡ أضف للمفضلات</button>
            </div>
          </div>

          <div style="margin-top:16px">
            <h4 class="muted">التعليقات</h4>
            <div id="comments" style="max-height:160px;overflow:auto;margin-top:8px"></div>
            <div style="display:flex;gap:8px;margin-top:8px">
              <input id="commentInput" placeholder="أضف تعليقاً" style="flex:1;padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--text)" />
              <button class="btn primary" id="sendComment">إرسال</button>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>

  <!-- أصوات وموسيقى -->
  <audio id="clickSfx" src="https://cdn.pixabay.com/download/audio/2021/08/04/audio_6f0a8b5a8e.mp3?filename=click-2-23812.mp3"></audio>
  <audio id="bgMusic" loop src="https://cdn.pixabay.com/download/audio/2021/10/12/audio_3b2c0b80b9.mp3?filename=epic-cinematic-112916.mp3"></audio>
  <button id="musicControl" class="btn primary" style="position:fixed;left:18px;bottom:18px;padding:12px;border-radius:14px;z-index:1000">تشغيل الموسيقى</button>

  <script>
    // ====== قاعدة بيانات One Piece داخلية (قابلة للتوسيع) ======
    const DB = {
      animes:[{id:'onepiece',title:'One Piece',year:1999,eps:1000,desc:'رحلة مونكي دي لوفي وطاقمه للعثور على الكنز الأسطوري One Piece.',cover:'https://i.ibb.co/5KXftx8/luffy.jpg'}],
      characters:[
        {id:'luffy',name:'مونكي دي. لوفي',role:'قائد طاقم قبعة القش',img:'https://i.ibb.co/5KXftx8/luffy.jpg',desc:'قائد مغامر وله قوة فاكهة غوما غوما (مطاطي).',powers:'فاكهة الشيطان: غومو غومو — هاكي'},
        // استخدمت روابط مباشرة لصورة زورو وسانجي لتعمل على أي جهاز:
        {id:'zoro',name:'رورونوا زورو',role:'سياف الطاقم',img:'https://i.ibb.co/YN6j6K6/zoro.jpg',desc:'سيفي يسعى لأن يصبح أعظم سيفي.',powers:'تقنيات السيف • هاكي'},
        {id:'nami',name:'نامي',role:'الملاح',img:'https://i.ibb.co/mH5SWGf/nami.jpg',desc:'ملاح بارع وخبيرة الطقس.',powers:'مهارات ملاحة واستخدام الكليما تاكت'},
        {id:'sanji',name:'سانجي',role:'الطباخ',img:'https://i.ibb.co/8m2Tt9q/sanji.jpg',desc:'طباخ الطاقم ومقاتل بأسلوب الركل.',powers:'قوة بدنية وتقنيات قتالية'}
      ],
      crew:['luffy','zoro','nami','sanji'],
      powers:[
        {id:'devilfruits',title:'الفواكه الشيطانية',desc:'أنواع فواكه الشيطان: باراميشيا، زو، لوجيا. تمنح قدرات قوية لكنها تَجُرّ فقدان السباحة.'},
        {id:'haki',title:'الهاكي',desc:'قوة روحية تعطي تحكماً في القوة والهيمنة والحماية.'}
      ],
      episodes:[
        {id:'ep1',anime:'onepiece',num:1,title:'بداية الرحلة',summary:'لوفي يغادر قريته ويشرع في رحلته.'},
        {id:'ep37',anime:'onepiece',num:37,title:'اللقاء مع زورو',summary:'انضمام زورو إلى الطاقم.'}
      ],
      maps:[{id:'grandline',title:'الجراند لاين',desc:'الممر البحري الرئيسي في عالم ون بيس.'},{id:'wano',title:'مملكة وانو',desc:'أراضي تقليدية ذات ثقافة يابانية قوية.'}],
    };

    // ====== عناصر DOM ======
    const charactersGrid = document.getElementById('charactersGrid');
    const epList = document.getElementById('epList');
    const gallery = document.getElementById('gallery');
    const miniArticles = document.getElementById('miniArticles');

    // ====== مساعد AG-BOT — قاعدة Q&A مبسطة وقابلة للتوسيع ======
    const BOT_KB = [
      { q: ["لوفي", "من هو لوفي"], a: "مونكي دي لوفي هو بطل أنمي ون بيس..." },
      { q: ["زورو", "من هو زورو"], a: "رورونوا زورو هو أول عضو..." },
      { q: ["نامي", "من هي نامي"], a: "نامي هي ملاح طاقم قبعة القش..." },
      { q: ["سانجي", "من هو سانجي"], a: "سانجي هو طباخ الطاقم..." }
      // ... يمكنك توسيعها كما تريد
    ];

    function botQuery(text){
      const t = text.trim().toLowerCase();
      for(const item of BOT_KB){
        for(const k of item.q){ if(t.includes(k)) return item.a; }
      }
      if(t.includes('لوفي')||t.includes('luffy')) return 'مونكي دي. لوفي: قائد طموح، يمتلك فاكهة غومو غومو وقدرات هاكي متقدمة.';
      if(t.includes('زورو')) return 'رورونوا زورو: سياف الطاقم، قوي ومصمم ليكون الأعظم.';
      return 'عذراً، لا أعرف الإجابة الدقيقة لكن أضفني لمصادر جديدة — مثلاً اسأل: "ما هي أنواع الهاكي؟"';
    }

    // ====== Render functions ======
    function makeCharCard(c){
      const d = document.createElement('div'); d.className='card';
      d.innerHTML = `
        <div class='thumb'><img loading='lazy' src='${c.img}' alt='${c.name}' onerror="this.src='https://i.ibb.co/album/placeholder.jpg'"></div>
        <div class='meta'><h3>${c.name}</h3><p class='muted'>${c.role}</p></div>
        <div class='actions'><button class='btn' onclick="openModal('character','${c.id}')">عرض</button><button class='btn' onclick="toggleFav(event,'${c.id}')">♡</button></div>`;
      return d;
    }

    function renderHome(){
      charactersGrid.innerHTML=''; DB.characters.forEach(ch=> charactersGrid.appendChild(makeCharCard(ch)));
      epList.innerHTML=''; DB.episodes.forEach(e=>{ const el=document.createElement('div'); el.className='episode'; el.innerHTML=`<div style="max-width:70%"><strong>#${e.num} — ${e.title}</strong><div class='muted' style="font-size:13px">${e.summary}</div></div><div class='muted'>${e.anime}</div>`; epList.appendChild(el); });
      gallery.innerHTML=''; DB.characters.forEach(c=>{ const img=document.createElement('img'); img.src=c.img; img.alt=c.name; img.loading='lazy'; img.onerror = ()=>{ img.src='https://i.ibb.co/album/placeholder.jpg' }; gallery.appendChild(img); });
      miniArticles.innerHTML=''; miniArticles.appendChild(createArticle('ما هي الفواكه الشيطانية؟','شرح مبسط لأنواع الفواكه وقيودها.')); miniArticles.appendChild(createArticle('مفهوم الهاكي','أنواعه وكيف يعمل في القتال.'));
      observeCards();
    }

    function createArticle(title,excerpt){ const a=document.createElement('article'); a.className='panel'; a.style.padding='12px'; a.innerHTML=`<h3>${title}</h3><p class='muted' style='margin-top:8px'>${excerpt}</p>`; return a; }

    // ====== Modal ======
    const modal = document.getElementById('modal');
    function openModal(type,id){
      playClick();
      let data=null;
      if(type==='character') data = DB.characters.find(x=>x.id===id);
      if(type==='anime') data = DB.animes.find(x=>x.id===id);
      if(type==='map') data = DB.maps.find(x=>x.id===id);
      if(!data){ alert('لا توجد بيانات'); return; }
      document.getElementById('modalTitle').textContent = data.title || data.name;
      document.getElementById('modalImg').src = data.img || data.cover || 'https://i.ibb.co/album/placeholder.jpg';
      document.getElementById('modalDesc').textContent = data.desc || data.summary || '';
      document.getElementById('modalInfo').textContent = (data.powers?('قدرات: '+data.powers):'') + (data.year?(' • عام: '+data.year):'');
      document.getElementById('modalType').textContent = type.toUpperCase();
      buildStars(data.id || data.name);
      renderComments(data.id || data.name);
      const favBtn = document.getElementById('favBtn'); favBtn.textContent = isFav(data.id||data.name)? '♥ إزالة من المفضلات' : '♡ أضف للمفضلات';
      favBtn.onclick = ()=>{ toggleFav(null, data.id||data.name); favBtn.textContent = isFav(data.id||data.name)? '♥ إزالة من المفضلات' : '♡ أضف للمفضلات'; };
      modal.classList.add('open');
      modal.dataset.current = (data.id||data.name);
      modal.setAttribute('aria-hidden','false');
    }
    function closeModal(e){ if(e && e.stopPropagation) e.stopPropagation(); modal.classList.remove('open'); modal.setAttribute('aria-hidden','true'); }

    // ====== Favorites & Ratings & Comments ======
    function favKey(){ return 'ag_onepiece_favs_v1'; }
    function getFavs(){ return JSON.parse(localStorage.getItem(favKey())||'[]'); }
    function isFav(id){ return getFavs().includes(id); }
    function toggleFav(e,id){ if(e && e.stopPropagation) e.stopPropagation(); const favs=getFavs(); if(favs.includes(id)){ localStorage.setItem(favKey(), JSON.stringify(favs.filter(x=>x!==id))); alert('تم الإزالة من المفضلات'); } else { favs.push(id); localStorage.setItem(favKey(), JSON.stringify(favs)); alert('أضيف إلى المفضلات'); } }

    function starsKey(){ return 'ag_onepiece_stars_v1'; }
    function getStarMap(){ return JSON.parse(localStorage.getItem(starsKey())||'{}'); }
    function setStar(id,val){ const m=getStarMap(); m[id]=val; localStorage.setItem(starsKey(), JSON.stringify(m)); }
    function buildStars(id){ const container = document.getElementById('userStars'); container.innerHTML=''; const map=getStarMap(); const cur = map[id]||0; for(let i=1;i<=5;i++){ const sp=document.createElement('span'); sp.className='star'+(i<=cur?' active':''); sp.innerHTML='★'; sp.onclick = ()=>{ setStar(id,i); buildStars(id); }; container.appendChild(sp); } }

    function commentsKey(id){ return 'ag_comments_'+id; }
    function renderComments(id){ const box=document.getElementById('comments'); box.innerHTML=''; const arr=JSON.parse(localStorage.getItem(commentsKey(id))||'[]'); if(!arr.length) box.innerHTML='<div class="muted">لا تعليقات بعد</div>'; else arr.forEach(c=>{ const d=document.createElement('div'); d.style.padding='8px'; d.style.borderBottom='1px solid rgba(255,255,255,0.03)'; d.innerHTML=`<strong>${escapeHtml(c.name||'مستخدم')}</strong><div class='muted' style='font-size:13px'>${escapeHtml(c.text)}</div>`; box.appendChild(d); }); }
    document.getElementById('sendComment').addEventListener('click',()=>{ const id=modal.dataset.current; if(!id) return; const txt=document.getElementById('commentInput').value.trim(); if(!txt) return alert('أدخل تعليقاً'); const arr=JSON.parse(localStorage.getItem(commentsKey(id))||'[]'); arr.push({name:'زائر',text:txt,date:Date.now()}); localStorage.setItem(commentsKey(id), JSON.stringify(arr)); document.getElementById('commentInput').value=''; renderComments(id); });

    // ====== Search (within One Piece DB) ======
    document.getElementById('searchInput').addEventListener('input',e=>{ const q=e.target.value.trim().toLowerCase(); if(!q){ renderHome(); return; } const ch = DB.characters.filter(x=> x.name.toLowerCase().includes(q) || x.role.toLowerCase().includes(q)); const ep = DB.episodes.filter(x=> (''+x.num).includes(q) || x.title.toLowerCase().includes(q)); const pw = DB.powers.filter(x=> x.title.toLowerCase().includes(q) || x.desc.toLowerCase().includes(q)); charactersGrid.innerHTML=''; ch.forEach(c=> charactersGrid.appendChild(makeCharCard(c))); epList.innerHTML=''; ep.forEach(e=>{ const el=document.createElement('div'); el.className='episode'; el.innerHTML=`<div style="max-width:70%"><strong>#${e.num} — ${e.title}</strong><div class='muted' style="font-size:13px">${e.summary}</div></div><div class='muted'>${e.anime}</div>`; epList.appendChild(el); }); miniArticles.innerHTML=''; pw.forEach(p=> miniArticles.appendChild(createArticle(p.title,p.desc))); observeCards(); });

    // ====== Navigation single-file SPA behavior ======
    document.querySelectorAll('nav a').forEach(a=> a.addEventListener('click',navClick));
    function navClick(e){ e.preventDefault(); document.querySelectorAll('nav a').forEach(x=>x.classList.remove('active')); this.classList.add('active'); const t=this.dataset.target; document.getElementById('home').style.display = t==='home' ? 'grid' : 'none'; document.getElementById('charactersPage').style.display = t==='characters' ? 'block' : 'none'; document.getElementById('crewPage').style.display = t==='crew' ? 'block' : 'none'; document.getElementById('powersPage').style.display = t==='powers' ? 'block' : 'none'; document.getElementById('episodesPage').style.display = t==='episodes' ? 'block' : 'none'; document.getElementById('mapsPage').style.display = t==='maps' ? 'block' : 'none'; if(t==='characters') renderCharactersPage(); if(t==='crew') renderCrewPage(); if(t==='powers') renderPowersPage(); if(t==='episodes') renderEpisodesPage(); if(t==='maps') renderMapsPage(); }

    function renderCharactersPage(){ const list=document.getElementById('charactersList'); list.innerHTML=''; DB.characters.forEach(c=> list.appendChild(makeCharCard(c))); observeCards(); }
    function renderCrewPage(){ const list=document.getElementById('crewList'); list.innerHTML=''; DB.crew.forEach(id=>{ const c=DB.characters.find(x=>x.id===id); if(c) list.appendChild(makeCharCard(c)); }); observeCards(); }
    function renderPowersPage(){ const box=document.getElementById('powersList'); box.innerHTML=''; DB.powers.forEach(p=> box.appendChild(createArticle(p.title,p.desc))); }
    function renderEpisodesPage(){ const box=document.getElementById('episodesFull'); box.innerHTML=''; DB.episodes.forEach(e=>{ const d=document.createElement('div'); d.className='panel'; d.style.marginBottom='10px'; d.innerHTML=`<strong>#${e.num} — ${e.title}</strong><p class='muted'>${e.summary}</p><button class='btn' onclick="openModal('episode','${e.id}')">عرض</button>`; box.appendChild(d); }); }
    function renderMapsPage(){ const box=document.getElementById('mapsList'); box.innerHTML=''; DB.maps.forEach(m=>{ const d=document.createElement('div'); d.className='card'; d.style.padding='12px'; d.innerHTML=`<div class='meta'><h3>${m.title}</h3><p class='muted'>${m.desc}</p></div><div class='actions'><button class='btn' onclick="openModal('map','${m.id}')">عرض</button></div>`; box.appendChild(d); }); observeCards(); }

    // ====== AG-BOT handlers ======
    const botMsgs = document.getElementById('botMessages'); const botInput = document.getElementById('botInput'); document.getElementById('botSend').addEventListener('click',()=>{ const q=botInput.value.trim(); if(!q) return; addBotMsg('user',q); setTimeout(()=>{ const ans=botQuery(q); addBotMsg('bot',ans); },250); botInput.value=''; });
    function addBotMsg(kind,text){ const d=document.createElement('div'); d.className='msg '+(kind==='user'?'user':'bot'); d.textContent = text; botMsgs.appendChild(d); botMsgs.scrollTop = botMsgs.scrollHeight; }

    // ====== utilities: intersection observer, escapeHtml, sounds ======
    function observeCards(){ const cards=document.querySelectorAll('.card'); const io=new IntersectionObserver((entries)=>{ entries.forEach(en=>{ if(en.isIntersecting){ en.target.classList.add('visible'); io.unobserve(en.target); } }); },{threshold:0.12}); cards.forEach(c=> io.observe(c)); }
    function escapeHtml(s){ return (s||'').replace(/[&<>"']/g, ch=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[ch])); }
    const clickSfx = document.getElementById('clickSfx'); function playClick(){ try{ clickSfx.currentTime=0; clickSfx.play(); }catch(e){} }

    // ====== Music control & theme toggle ======
    const bgMusic = document.getElementById('bgMusic'); let musicPlaying=false; document.getElementById('musicControl').addEventListener('click',()=>{ if(!musicPlaying){ bgMusic.play().then(()=>{ musicPlaying=true; document.getElementById('musicControl').textContent='إيقاف الموسيقى'; }).catch(()=>{ alert('المتصفح منع التشغيل التلقائي، اضغط مرة أخرى'); }); } else { bgMusic.pause(); musicPlaying=false; document.getElementById('musicControl').textContent='تشغيل الموسيقى'; }});
    const themeToggle = document.getElementById('themeToggle'); themeToggle.addEventListener('click',()=>{ const el = document.body; const t = el.getAttribute('data-theme'); if(t==='dark'){ el.setAttribute('data-theme','light'); localStorage.setItem('ag_theme','light'); themeToggle.setAttribute('aria-pressed','true'); } else { el.setAttribute('data-theme','dark'); localStorage.setItem('ag_theme','dark'); themeToggle.setAttribute('aria-pressed','false'); } });
    (function(){ const t=localStorage.getItem('ag_theme')||'dark'; document.body.setAttribute('data-theme',t); })();

    // ====== Init ======
    renderHome();
    document.addEventListener('keydown',e=>{ if(e.key==='Escape') closeModal(); });

    // small accessibility: allow Enter in bot input
    botInput.addEventListener('keydown', (e)=>{ if(e.key === 'Enter'){ document.getElementById('botSend').click(); } });

  </script>
</body>
</html>
