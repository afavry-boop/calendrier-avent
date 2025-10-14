<!DOCTYPE html>
<html lang="fr">
  <meta charset="UTF-8" />


<!-- Police Lora avec italiques -->
<link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;0,700;1,400;1,600&display=swap" rel="stylesheet">

<style>
  :root {
    --bg: #EDE6DC;
    --card: #EDE6DC;
    --muted: #7f8aa3;
    --accent: #e0b567;
    --accent-2: #24b47e;
    --danger: #e35d6a;
    --red: #BE1917;
    --shadow: 0 4px 10px rgba(0, 0, 0, .06);
    --radius: 18px;
  }

  html, body {
    margin: 0;
    background: var(--bg);
    color: #2b1f1f;
    font-family: 'Lora', serif;
    font-weight: 400;
  }

  * {
    font-family: 'Lora', serif !important;
    box-sizing: border-box;
  }

  .wrap {
    max-width: 1100px;
    margin: 100px auto;
    padding: 0 20px;
  }

  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 16px;
  }

  .title {
    font-size: 46px;
    font-weight: 600;
    letter-spacing: 0px;
      color: #BE1917;
  }

.subtitle {
  font-family: 'Lora', serif;
  font-size: 20px;
  color: #8a2c2c;
  font-style: italic;
  margin-top: 12px;
}

  .toolbar {
    display: flex;
    align-items: center;
    gap: 16px;
    justify-content: flex-end;  
    max-width: 1100px;           /* distance au-dessus si tu veux qu'il remonte */
    margin: 40px auto 0;    /* centré horizontalement */
    padding-right: 20px; 
    padding-bottom: 40px; 
  }

  .pill {
    background: rgba(255,255,255,.06);
    border: 1px solid rgba(255,255,255,.1);
    padding: 8px 12px;
    border-radius: 999px;
    font-size: 12px;
    color: var(--muted);
  }

  .btn {
    appearance: none;
    border: none;
    cursor: pointer;
    padding: 10px 14px;
    border-radius: 12px;
    background: #17362A;
    color: #f7f9fc;
    border: 1px solid rgba(255,255,255,.12);
    box-shadow: var(--shadow);
    font-weight: 600;
  }

  .btn:hover {
    transform: translateY(-1px);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(6, minmax(120px, 1fr));
    gap: 25px;
    margin-top: 40px; /* espace entre le titre et la grille */

  }

  @media (max-width:900px) { .grid { grid-template-columns: repeat(4, minmax(100px, 1fr)); } }
  @media (max-width:600px) { .grid { grid-template-columns: repeat(3, minmax(90px, 1fr)); } }

  .door {
    position: relative;
    background: var(--card);
    border: 1px solid #DED7CF;
    border-radius: 30px(--radius);
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 28px;
    letter-spacing: .5px;
    box-shadow: var(--shadow);
    overflow: hidden;
    transition: all 0.2s ease-in-out;
    color: var(--red);
  }

 .door:hover:not(.opened) {
  box-shadow: 0 6px 14px rgba(0,0,0,.12);
  transform: translateY(-2px);
}


  .door .num {
    position: absolute;
    top: 8px;
    left: 10px;
    color: var(--red);
    font-size: 32px;
    font-weight: 600;
  }

  .door.locked {
    background: var(--card);
    cursor: not-allowed;
    filter: none;
    opacity: 1; /* plus de gris */
  }

  .door.opened {
    background: #D0B1B1;
  }

  .badge {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 12px;
    font-style: italic; /* italique chic */
    padding: 3px 6px;
    border-radius: 0px;
    border: 1px solid #E99D9C;
    color: #BE1917;
    letter-spacing: 0.3px;
    background: rgba(255, 255, 255, 0.4);
  }

  .modal-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(5,8,13,.55);
    backdrop-filter: blur(6px);
    display: none;
    align-items: flex-start;
    justify-content: center;
    padding-top: 20vh;
    z-index: 50;
  }

  .modal {
    width: min(680px, calc(100vw - 32px));
    background: #151c2f;
    border: 1px solid rgba(255,255,255,.12);
    border-radius: 22px;
    box-shadow: var(--shadow);
    overflow: hidden;
    transition: transform 0.3s ease;
    color: var(--snow);
  }

  .modal.shake {
    animation: shake 0.3s ease;
  }

  @keyframes shake {
    0% { transform: translateX(0); }
    20% { transform: translateX(-8px); }
    40% { transform: translateX(8px); }
    60% { transform: translateX(-5px); }
    80% { transform: translateX(5px); }
    100% { transform: translateX(0); }
  }

  .modal-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 18px;
    border-bottom: 1px solid rgba(255,255,255,.08);
    font-weight: 600;
  }

  .modal-title {
    font-size: 18px;
    font-weight: 700;
  }

  .modal-close {
    background: transparent;
    border: none;
    color: var(--muted);
    font-size: 22px;
    cursor: pointer;
  }

  .modal-body {
    padding: 18px;
  }

  .anecdote {
    background: rgba(255,255,255,.04);
    border: 1px solid rgba(255,255,255,.08);
    padding: 14px 16px;
    border-radius: 14px;
    line-height: 1.5;
  }

  .form {
    display: grid;
    gap: 12px;
    margin-top: 14px;
  }

  .row {
    display: grid;
    gap: 10px;
    grid-template-columns: 1fr 140px;
  }

  @media(max-width:560px){ .row { grid-template-columns: 1fr; } }

  select {
    width: 100%;
    background: #0e1424;
    color: var(--snow);
    border: 1px solid rgba(255,255,255,.12);
    border-radius: 12px;
    padding: 10px 12px;
    font-size: 14px;
  }

  .result { margin-top: 10px; font-weight: 700; }
  .ok { color: var(--accent-2); }
  .ko { color: var(--danger); }

  .footer {
    margin-top: 18px;
    display: flex;
    justify-content: flex-end;
  }

  .confetti {
    position: fixed;
    pointer-events: none;
    inset: 0;
    overflow: hidden;
    z-index: 60;
  }
</style>


<body>
  <div class="wrap">
    <div class="header">
      <div>
        <div class="title"> Le Calendrier de l’Avent <br>
Cambon Partners</div>
        <div class="subtitle">À qui appartient le FunFact du jour ?</div>
      </div>

    </div>

    <div class="grid" id="grid"></div>
  </div>



<div class="toolbar">
  <span class="pill" id="today-pill"></span>
  <button class="btn" id="toggle-dev">Mode test</button>
  <button class="btn" id="reset">Réinitialiser</button>
</div>


  <!-- Modal -->
  <div class="modal-backdrop" id="backdrop" aria-hidden="true">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="modal-title" id="modalBox">
      <div class="modal-head">
        <div class="modal-title" id="modal-title">Jour 1</div>
        <button class="modal-close" id="close">×</button>
      </div>
      <div class="modal-body">
        <div class="anecdote" id="anecdote"></div>

        <div class="form">
          <label class="hint">À qui appartient ce FunFact ?</label>
          <div class="row">
            <select id="answerSelect"></select>
            <button class="btn" id="submit">Valider</button>
          </div>

          <div class="result" id="result"></div>
        </div>

        <div class="footer">
          <!-- Plus de points affichés -->
        </div>
      </div>
    </div>
  </div>

  <canvas class="confetti" id="confetti"></canvas>

  <script>
    const TEAM = [
      "David", "Michael", "Morgann", "Laurent", "Guillaume T.", "Jonathan", "Romain D", "Guillaume E.", "Nicolas SP.", "Nicolas P.",
      "Alexandre A.", "Thomas B.", "Min", "Aubert", "Julien", "Maxime", "Gabriel", "Florian", "Robin", "Raphaël", "Camille", "Simon", "Younes",
      "Victor", "Jordan", "Grégoire", "Baptiste", "Pierre", "Yvette", "Télio", "Alain", "Maxime P.", "Alexandre C.", "Luca", "Chadi", "Nicolas O.",
      "Marius", "Paul", "Lily", "Nicolas R.", "Thomas K.", "Yahia", "Elena", "Mathieu", "Alexandre H.", "Juliette", "Louis", "Anna", "Romain P.",
      "Briac", "Mostapha", "Jeremy", "Carine", "Amélie", "Pauline", "Adèle", "Thomas A.", "Nathalie", "Annabelle", "Gaiané", "Alexandra", "Anselme"
    ];

    const DAYS = [
      {
        day: 1,
        anecdote: "Quand j’étais petite, je me suis faite renverser par un dromadaire au cirque 😅",
        answer: "Annabelle",
        aliases: ["Annabelle", "Nathalie", "Camille"]
      },
      ...Array.from({length:23}, (_,i)=>({
        day: i+2,
        anecdote: `Anecdote du jour ${i+2} — à personnaliser plus tard.`,
        answer: TEAM[i+1] || TEAM[0],
        aliases: TEAM[i+1] ? [TEAM[i+1], TEAM[i+1].toLowerCase()] : []
      }))
    ];

    const STORAGE_KEY = "advent-quiz-v1";
    const state = { dev:false, score:0, opened:{} };

    function load(){
      try{
        const raw = localStorage.getItem(STORAGE_KEY);
        if(raw) Object.assign(state, JSON.parse(raw));
      }catch(_){}
    }
    function save(){
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
    }

    const today = new Date();
    const month = today.getMonth()+1;
    const date = today.getDate();
    function isUnlocked(day){ return state.dev || (month===12 && day<=date); }

    function $(id){return document.getElementById(id)}
    function el(tag, attrs={}, children=[]){
      const node=document.createElement(tag);
      Object.entries(attrs).forEach(([k,v])=>{ if(k==="class") node.className=v; else if(k==="text") node.textContent=v; else node.setAttribute(k,v); });
      [].concat(children).forEach(c=>node.appendChild(typeof c==="string"?document.createTextNode(c):c));
      return node;
    }

    function norm(s){return (s||"").toString().normalize("NFD").replace(/[\u0300-\u036f]/g,"").trim().toLowerCase();}
    function check(day, guess){
      const d=DAYS.find(x=>x.day===day);
      const target=norm(d.answer);
      const aliases=(d.aliases||[]).map(norm);
      const g=norm(guess);
      return g===target||aliases.includes(g);
    }

    const grid=$("grid");
    function renderGrid(){
      grid.innerHTML="";
      DAYS.forEach(d=>{
        const opened=!!state.opened[d.day];
        const door=el("button",{class:`door ${!isUnlocked(d.day)?'locked':''} ${opened?'opened':''}`,"data-day":d.day});
        door.appendChild(el("span",{class:"badge",text:opened?"ouvert":(isUnlocked(d.day)?"dispo":"verrouillé")}));
        const dayLabel = String(d.day).padStart(2, '0');
door.appendChild(el("div", {class:"num", text: dayLabel}));

        door.addEventListener("click",()=>{if(!isUnlocked(d.day))return;openModal(d.day);});
        grid.appendChild(door);
      });
    }

    const backdrop=$("backdrop"), modalBox=$("modalBox"), modalTitle=$("modal-title"), anecdote=$("anecdote"),
          answerSelect=$("answerSelect"), submitBtn=$("submit"), result=$("result");

    let currentDay=1;
    function buildOptions(){
      answerSelect.innerHTML="";
      answerSelect.appendChild(el("option",{value:"",text:"— Sélectionne un nom —"}));
      TEAM.forEach(name=>answerSelect.appendChild(el("option",{value:name,text:name})));
    }

    function openModal(day){
      currentDay=day;
      const d=DAYS.find(x=>x.day===day);
      modalTitle.textContent=`Jour ${day}`;
      anecdote.textContent=d.anecdote;
      buildOptions();
      const saved=state.opened[day]||{};
      answerSelect.value=saved.answer||"";
      result.textContent="";
      result.className="result";
      backdrop.style.display="flex";
    }

    function closeModal(){ backdrop.style.display="none"; }
    $("close").addEventListener("click",closeModal);
    backdrop.addEventListener("click",e=>{if(e.target===backdrop)closeModal();});

    submitBtn.addEventListener("click",()=>{
      const guess=answerSelect.value;
      if(!guess){result.textContent="Choisis un nom avant de valider";result.className="result ko";return;}
      const good=check(currentDay,guess);
      state.opened[currentDay]={answer:guess,correct:good};
      if(good){
        const d=DAYS.find(x=>x.day===currentDay);
        result.textContent=`Bien joué 🎉 C’était ${d.answer} ✨`;
        result.className="result ok";
        celebrate();
      } else {
        result.textContent="Loupé...! Essaie quelqu’un d’autre 😄";
        result.className="result ko";
        modalBox.classList.add("shake");
        setTimeout(()=>modalBox.classList.remove("shake"),400);
      }
      state.score=Object.values(state.opened).filter(x=>x.correct).length;
      save();renderGrid();
    });

    $("reset").addEventListener("click",()=>{if(confirm("Réinitialiser tes réponses et le score ?")){state.opened={};state.score=0;save();renderGrid();}});
    $("toggle-dev").addEventListener("click",()=>{state.dev=!state.dev;save();renderGrid();$("toggle-dev").textContent=state.dev?"Mode test (ON)":"Mode test";});

    const confettiCanvas=$("confetti");const ctx=confettiCanvas.getContext('2d');let particles=[];
    function resize(){confettiCanvas.width=window.innerWidth;confettiCanvas.height=window.innerHeight;}
    window.addEventListener('resize',resize);resize();
    function celebrate(){
      for(let i=0;i<150;i++){particles.push({x:Math.random()*confettiCanvas.width,y:-10,s:Math.random()*6+2,v:Math.random()*3+2,r:Math.random()*360,a:1});}
      requestAnimationFrame(tick);
      setTimeout(()=>{particles=[];ctx.clearRect(0,0,confettiCanvas.width,confettiCanvas.height);},1500);
    }
    function tick(){
      ctx.clearRect(0,0,confettiCanvas.width,confettiCanvas.height);
      particles.forEach(p=>{
        p.y+=p.v;p.r+=6;p.a-=0.01;
        ctx.save();ctx.translate(p.x,p.y);ctx.rotate(p.r*Math.PI/180);
        ctx.globalAlpha=Math.max(p.a,0);
        const c=Math.floor(p.r)%3;
        ctx.fillStyle=c===0?'#e0b567':(c===1?'#24b47e':'#e35d6a');
        ctx.fillRect(-p.s/2,-p.s/2,p.s,p.s);
        ctx.restore();
      });
      if(particles.some(p=>p.a>0))requestAnimationFrame(tick);
    }

    (function init(){
      load();
      const pad=n=>String(n).padStart(2,'0');
      const now=new Date();
      const fmt=`${pad(now.getDate())}/${pad(now.getMonth()+1)}/${now.getFullYear()}`;
      $("today-pill").textContent=`Aujourd’hui : ${fmt}`;
      renderGrid();
    })();
  </script>
</body>
</html>
