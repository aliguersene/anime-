<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>AG ANIME — نسخة الهاتف</title>
<style>
:root{
  --bg:#000; --panel:#111; --card:#1a1a1a; --accent:#ff3b3b; --accent-2:#ffb86b; --muted:#bdbdbd; --radius:12px; --shadow:0 10px 40px rgba(0,0,0,0.6);
  --text:#fff;
}
body{margin:0;font-family:'Cairo',Tajawal,sans-serif;background:var(--bg);color:var(--text);}
.wrap{width:100%;margin:0 auto;padding:8px;display:flex;flex-direction:column;gap:12px;}
header{display:flex;justify-content:space-between;align-items:center;padding:10px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);backdrop-filter:blur(6px);}
.logo{width:50px;height:50px;border-radius:10px;overflow:hidden;}
.logo img{width:100%;height:100%;object-fit:cover;}
nav{display:flex;gap:6px;overflow-x:auto;}
nav a{flex-shrink:0;color:var(--muted);text-decoration:none;padding:6px 10px;border-radius:8px;font-size:13px;}
nav a.active{background:linear-gradient(90deg,var(--accent),var(--accent-2));color:#111;}
.content{display:flex;flex-direction:column;gap:12px;}
.panel{background:var(--panel);padding:12px;border-radius:var(--radius);}
.grid{display:grid;grid-template-columns:1fr;gap:12px;}
.card{display:flex;gap:8px;align-items:center;padding:10px;border-radius:var(--radius);background:var(--card);border:1px solid rgba(255,255,255,0.05);}
.thumb{flex:0 0 80px;height:80px;border-radius:8px;overflow:hidden;background:#222;display:flex;align-items:center;justify-content:center;}
.thumb img{width:100%;height:100%;object-fit:cover;}
.meta h3{margin:0;font-size:14px;}
.meta p{margin:4px 0 0 0;color:var(--muted);font-size:12px;}
.btn{padding:6px 8px;border-radius:8px;border:none;background:linear-gradient(90deg,var(--accent),var(--accent-2));color:#111;font-size:13px;cursor:pointer;}

/* Modal responsive */
.modal{position:fixed;inset:0;display:grid;place-items:center;background:rgba(0,0,0,0.8);visibility:hidden;opacity:0;transition:opacity .2s,visibility .2s;z-index:999;}
.modal.open{visibility:visible;opacity:1;}
.modal-card{width:95%;background:#1a1a1a;padding:12px;border-radius:12px;}
.modal-row{display:flex;flex-direction:column;gap:8px;}
.modal-row img{width:100%;height:auto;border-radius:8px;}

/* Bot */
#botIcon{position:fixed;bottom:10px;right:10px;width:56px;height:56px;border-radius:50%;background:linear-gradient(135deg,var(--accent),var(--accent-2));display:flex;justify-content:center;align-items:center;font-size:26px;color:#111;cursor:pointer;z-index:9999;}
#botPopup{position:fixed;bottom:70px;right:10px;width:calc(100% - 20px);max-height:60vh;background:#111;border-radius:12px;display:none;flex-direction:column;overflow:hidden;z-index:9999;}
#botHeader{background:linear-gradient(90deg,var(--accent),var(--accent-2));padding:8px;display:flex;justify-content:space-between;color:#111;font-weight:bold;}
#botHeader button{background:transparent;border:none;font-size:18px;cursor:pointer;}
#botMessages2{flex:1;padding:8px;overflow-y:auto;display:flex;flex-direction:column;gap:6px;}
#botMessages2 .msg.user{align-self:flex-end;background:rgba(255,255,255,0.1);padding:6px;border-radius:6px;}
#botMessages2 .msg.bot{align-self:flex-start;background:rgba(255,59,59,0.2);padding:6px;border-radius:6px;}
#botInputRow{display:flex;gap:4px;padding:6px;border-top:1px solid rgba(255,255,255,0.1);}
#botInput2{flex:1;padding:6px;border-radius:6px;border:1px solid rgba(255,255,255,0.2);background:transparent;color:#fff;}
#botSend2{padding:6px 8px;border-radius:6px;border:none;background:linear-gradient(90deg,var(--accent),var(--accent-2));color:#111;cursor:pointer;}
</style>
</head>
<body>
<div class="wrap">

<header>
  <div class="logo"><img src="https://i.ibb.co/6X9Gk2B/ag-anime-emblem.png" alt="AG ANIME"></div>
  <nav>
    <a href="#home" class="active" data-target="home">الرئيسية</a>
    <a href="#characters" data-target="characters">الشخصيات</a>
    <a href="#crew" data-target="crew">طاقم</a>
    <a href="#powers" data-target="powers">القوى</a>
    <a href="#episodes" data-target="episodes">الحلقات</a>
    <a href="#maps" data-target="maps">الخرائط</a>
  </nav>
</header>

<main id="home" class="content page" style="display:block">
  <section class="panel">
    <h2>نظرة عامة — ون بيس</h2>
    <p class="muted">مرحبًا بك في قسم One Piece. ملفات مفصلة عن الشخصيات، الطاقم، الفواكه الشيطانية، الهاكي، وقوائم الحلقات.</p>
    <div id="charactersGrid" class="grid"></div>
  </section>
</main>

<!-- Modal -->
<div id="modal" class="modal" onclick="closeModal(event)">
  <div class="modal-card" onclick="event.stopPropagation()">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
      <h3 id="modalTitle"></h3>
      <button onclick="closeModal()">إغلاق</button>
    </div>
    <div class="modal-row">
      <img id="modalImg" src="" alt="media">
      <p id="modalDesc" class="muted"></p>
    </div>
  </div>
</div>

<!-- Bot -->
<div id="botIcon">🤖</div>
<div id="botPopup">
  <div id="botHeader">بوت الموقع <button onclick="botPopup.style.display='none'">×</button></div>
  <div id="botMessages2"></div>
  <div id="botInputRow">
    <input type="text" id="botInput2" placeholder="اكتب رسالتك...">
    <button id="botSend2">إرسال</button>
  </div>
</div>

<script>
/* قاعدة البيانات */
const DB={characters:[{id:'luffy',name:'لوفي',role:'قائد',img:'https://i.ibb.co/5KXftx8/luffy.jpg'}]};

/* عناصر DOM */
const charactersGrid = document.getElementById('charactersGrid');

/* عرض البطاقات */
function makeCharCard(c){
  const d=document.createElement('div');
  d.className='card';
  d.innerHTML=`<div class='thumb'><img src='${c.img}'></div><div class='meta'><h3>${c.name}</h3><p class='muted'>${c.role}</p></div>`;
  d.addEventListener('click',()=>openModal('character',c.id));
  return d;
}

function renderHome(){
  charactersGrid.innerHTML='';
  DB.characters.forEach(c=>charactersGrid.appendChild(makeCharCard(c)));
}
renderHome();

/* Modal */
const modal=document.getElementById('modal');
function openModal(type,id){
  const data = DB.characters.find(x=>x.id===id);
  if(!data) return;
  document.getElementById('modalTitle').textContent = data.name;
  document.getElementById('modalImg').src = data.img;
  document.getElementById('modalDesc').textContent = data.role;
  modal.classList.add('open');
}
function closeModal(e){if(e&&e.stopPropagation)e.stopPropagation(); modal.classList.remove('open');}

/* Bot بسيط */
const BOT_KB=[{q:['لوفي'],a:'لوفي قائد الطاقم وحلمه أن يصبح ملك القراصنة!'}];
const botIcon=document.getElementById('botIcon');
const botPopup=document.getElementById('botPopup');
const botMessages2=document.getElementById('botMessages2');
const botInput2=document.getElementById('botInput2');
const botSend2=document.getElementById('botSend2');

botIcon.addEventListener('click',()=>{botPopup.style.display=(botPopup.style.display==='flex')?'none':'flex';botPopup.style.flexDirection='column';});
botSend2.addEventListener('click',sendBotMessage);
botInput2.addEventListener('keydown',e=>{if(e.key==='Enter')sendBotMessage();});

function addBotMsg(type,text){const d=document.createElement('div');d.className='msg '+(type==='user'?'user':'bot');d.textContent=text;botMessages2.appendChild(d);botMessages2.scrollTop=botMessages2.scrollHeight;}
function sendBotMessage(){const txt=botInput2.value.trim();if(!txt)return;addBotMsg('user',txt);botInput2.value='';setTimeout(()=>{let ans='عذرًا، لم أجد إجابة.';BOT_KB.forEach(b=>{b.q.forEach(k=>{if(txt.includes(k))ans=b.a;});});addBotMsg('bot',ans);},300);}
</script>
</body>
</html>
