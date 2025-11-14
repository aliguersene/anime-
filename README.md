<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>AG ANIME — النسخة المطوّرة WebView</title>
<style>
body{margin:0;font-family:'Cairo',Tajawal,sans-serif;background:#000;color:#fff;}
header{display:flex;justify-content:space-between;align-items:center;padding:10px;background:#111;}
nav{display:flex;overflow-x:auto;}
nav a{padding:6px 10px;color:#bdbdbd;text-decoration:none;white-space:nowrap;transition:0.2s;}
nav a.active{color:#111;background:linear-gradient(90deg,#ff3b3b,#ffb86b);border-radius:6px;}
nav a:hover{opacity:0.8;}
.content{padding:10px;}
.panel{background:#111;padding:10px;margin-bottom:10px;border-radius:8px;}
.grid{display:block;}
.card{background:#1a1a1a;padding:10px;margin-bottom:8px;border-radius:8px;cursor:pointer;display:flex;align-items:center;transition:0.2s;}
.card:hover{transform:scale(1.03);background:#222;}
.thumb{width:60px;height:60px;margin-left:8px;}
.thumb img{width:100%;height:100%;object-fit:cover;border-radius:6px;}
.meta h3{margin:0;font-size:14px;}
.meta p{margin:4px 0 0 0;color:#bdbdbd;font-size:12px;}
input#searchInput{width:100%;padding:6px;margin:8px 0;border-radius:6px;border:none;background:#222;color:#fff;}
.modal{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.85);display:none;align-items:center;justify-content:center;z-index:999;}
.modal-content{background:#1a1a1a;padding:10px;border-radius:8px;width:90%;max-width:400px;}
.modal-content img{width:100%;border-radius:8px;margin:8px 0;}
.modal-content a{color:#ffb86b;text-decoration:none;display:block;margin-top:4px;}
#botIcon{position:fixed;bottom:10px;right:10px;width:50px;height:50px;background:linear-gradient(135deg,#ff3b3b,#ffb86b);border-radius:50%;display:flex;justify-content:center;align-items:center;font-size:24px;color:#111;cursor:pointer;z-index:999;}
#botPopup{position:fixed;bottom:70px;right:10px;width:calc(100% - 20px);max-height:60vh;background:#111;border-radius:12px;display:none;flex-direction:column;overflow:hidden;z-index:999;}
#botHeader{background:linear-gradient(90deg,#ff3b3b,#ffb86b);padding:8px;color:#111;display:flex;justify-content:space-between;}
#botHeader button{background:none;border:none;font-size:18px;cursor:pointer;}
#botMessages2{flex:1;padding:8px;overflow-y:auto;display:flex;flex-direction:column;gap:6px;}
#botMessages2 .msg.user{align-self:flex-end;background:rgba(255,255,255,0.1);padding:6px;border-radius:6px;}
#botMessages2 .msg.bot{align-self:flex-start;background:rgba(255,59,59,0.2);padding:6px;border-radius:6px;}
#botInputRow{display:flex;gap:4px;padding:6px;border-top:1px solid rgba(255,255,255,0.1);}
#botInput2{flex:1;padding:6px;border-radius:6px;border:1px solid rgba(255,255,255,0.2);background:transparent;color:#fff;}
#botSend2{padding:6px 8px;border-radius:6px;border:none;background:linear-gradient(90deg,#ff3b3b,#ffb86b);color:#111;cursor:pointer;}
</style>
</head>
<body>

<header>
  <div>AG ANIME</div>
  <nav>
    <a href="#home" class="active" data-target="home">الرئيسية</a>
    <a href="#characters" data-target="characters">الشخصيات</a>
    <a href="#crew" data-target="crew">طاقم</a>
    <a href="#powers" data-target="powers">القوى</a>
    <a href="#episodes" data-target="episodes">الحلقات</a>
    <a href="#maps" data-target="maps">الخرائط</a>
  </nav>
</header>

<div class="content page" id="home">
  <div class="panel"><h2>الرئيسية</h2>
    <p>مرحبًا بك في النسخة الكاملة WebView. جميع القوائم والبطاقات قابلة للعرض هنا.</p>
  </div>
</div>

<!-- شريط بحث عام -->
<input type="text" id="searchInput" placeholder="ابحث عن شخصية، حلقة، أو قوة...">

<div class="content page" id="characters" style="display:none;">
  <div class="panel"><h2>الشخصيات</h2><div id="charactersGrid" class="grid"></div></div>
</div>

<div class="content page" id="crew" style="display:none;">
  <div class="panel"><h2>طاقم الطاقم</h2><div id="crewGrid" class="grid"></div></div>
</div>

<div class="content page" id="powers" style="display:none;">
  <div class="panel"><h2>القوى والفواكه الشيطانية</h2><div id="powersGrid" class="grid"></div></div>
</div>

<div class="content page" id="episodes" style="display:none;">
  <div class="panel"><h2>الحلقات</h2><div id="episodesGrid" class="grid"></div></div>
</div>

<div class="content page" id="maps" style="display:none;">
  <div class="panel"><h2>الخرائط</h2><div id="mapsGrid" class="grid"></div></div>
</div>

<div class="modal" id="modal">
  <div class="modal-content">
    <h3 id="modalTitle"></h3>
    <img id="modalImg" src="">
    <p id="modalDesc"></p>
    <a id="modalLink" href="#" target="_blank">زيارة الصفحة</a>
    <button onclick="closeModal()">إغلاق</button>
  </div>
</div>

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
// ======================
// قاعدة بيانات افتراضية كاملة
// ======================
const DB = {
  characters: Array.from({length:50},(_,i)=>({id:`char${i}`,name:`شخصية ${i+1}`,role:`دور ${i+1}`,img:'https://via.placeholder.com/80',desc:`وصف الشخصية ${i+1}`,link:'#'})),
  crew: Array.from({length:10},(_,i)=>({id:`crew${i}`,name:`عضو ${i+1}`,role:`دوره ${i+1}`,img:'https://via.placeholder.com/80',desc:`وصف عضو الطاقم ${i+1}`,link:'#'})),
  powers: Array.from({length:20},(_,i)=>({id:`power${i}`,name:`القوة ${i+1}`,desc:`وصف القوة ${i+1}`,img:'https://via.placeholder.com/80',link:'#'})),
  episodes: Array.from({length:30},(_,i)=>({id:`ep${i}`,name:`الحلقة ${i+1}`,desc:`وصف الحلقة ${i+1}`,img:'https://via.placeholder.com/80',link:'#'})),
  maps: Array.from({length:10},(_,i)=>({id:`map${i}`,name:`الخريطة ${i+1}`,desc:`وصف الخريطة ${i+1}`,img:'https://via.placeholder.com/80',link:'#'}))
};

// ======================
// التنقل بين الصفحات
// ======================
const navLinks = document.querySelectorAll('nav a');
const pages = document.querySelectorAll('.page');
navLinks.forEach(link=>{
  link.addEventListener('click',()=>{
    navLinks.forEach(a=>a.classList.remove('active'));
    link.classList.add('active');
    const target=link.dataset.target;
    pages.forEach(p=>p.style.display=(p.id===target)?'block':'none');
  });
});

// ======================
// عرض البطاقات
// ======================
function makeCard(c){
  const d=document.createElement('div');
  d.className='card';
  d.innerHTML=`<div class='thumb'><img src='${c.img}'></div><div class='meta'><h3>${c.name}</h3><p>${c.role||c.desc}</p></div>`;
  d.addEventListener('click',()=>openModal(c));
  return d;
}
function renderGrid(gridId,data){
  const g=document.getElementById(gridId);
  g.innerHTML='';
  data.forEach(d=>g.appendChild(makeCard(d)));
}
window.addEventListener('load',()=>{
  renderGrid('charactersGrid',DB.characters);
  renderGrid('crewGrid',DB.crew);
  renderGrid('powersGrid',DB.powers);
  renderGrid('episodesGrid',DB.episodes);
  renderGrid('mapsGrid',DB.maps);
});

// ======================
// Modal
// ======================
const modal=document.getElementById('modal');
function openModal(data){
  document.getElementById('modalTitle').textContent=data.name;
  document.getElementById('modalImg').src=data.img;
  document.getElementById('modalDesc').textContent=data.role||data.desc||'';
  document.getElementById('modalLink').href=data.link||'#';
  modal.style.display='flex';
}
function closeModal(){modal.style.display='none';}

// ======================
// شريط البحث
// ======================
document.getElementById('searchInput').addEventListener('input', e=>{
  const q = e.target.value.toLowerCase();
  ['characters','crew','powers','episodes','maps'].forEach(section=>{
    document.getElementById(section+'Grid').childNodes.forEach(card=>{
      card.style.display = card.innerText.toLowerCase().includes(q) ? 'flex' : 'none';
    });
  });
});

// ======================
// Bot
// ======================
const botIcon=document.getElementById('botIcon');
const botPopup=document.getElementById('botPopup');
const botMessages2=document.getElementById('botMessages2');
const botInput2=document.getElementById('botInput2');
const botSend2=document.getElementById('botSend2');

botIcon.addEventListener('click',()=>botPopup.style.display=(botPopup.style.display==='flex')?'none':'flex'));

const BOT_KB = [...DB.characters,...DB.powers,...DB.episodes].map(i=>({keywords:[i.name],answer:i.desc}))
.concat([
  {keywords:['لوفي'], answer:'لوفي هو قائد الطاقم وحلمه أن يصبح ملك القراصنة.'},
  {keywords:['زورو'], answer:'زورو هو السيفي القوي في الطاقم.'}
]);

function addBotMsg(type,text){
  const d=document.createElement('div');
  d.className='msg '+(type==='user'?'user':'bot');
  d.textContent=text;
  botMessages2.appendChild(d);
  botMessages2.scrollTop=botMessages2.scrollHeight;
}
function sendBotMessage(){
  const txt = botInput2.value.trim();
  if(!txt) return;
  addBotMsg('user',txt);
  botInput2.value='';
  setTimeout(()=>{
    let ans='عذرًا، لم أجد إجابة.';
    BOT_KB.forEach(b=>b.keywords.forEach(k=>{if(txt.includes(k))ans=b.answer;}));
    addBotMsg('bot',ans);
  },200);
}
botSend2.addEventListener('click',sendBotMessage);
botInput2.addEventListener('keydown',e=>{if(e.key==='Enter')sendBotMessage();});
</script>
</body>
</html>
