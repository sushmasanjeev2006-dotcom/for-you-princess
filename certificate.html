// app.js - Mystic Pink Portal (style C)
// Keep code compact and performant. No external libs required.

// ---- config & data ----
const PLAYER_NAME = "Shub";
const COIN_TIME = 15; // seconds
const MISSIONS = [
  { text: "Promise to spot at gym — how do you respond?", choices: [{t:"Always (deal)", c:3},{t:"Sometimes", c:1}]},
  { text: "Which anime vibe today?", choices: [{t:"Shonen energy", c:2},{t:"Chill slice-of-life", c:1}]},
  { text: "Snack truce — will you share?", choices: [{t:"Of course", c:2},{t:"Maybe later", c:0}]},
  { text: "Bracelet honor — will you protect it?", choices: [{t:"Always", c:3},{t:"I'll keep safe", c:2}]}
];

// ---- DOM refs ----
const bgCanvas = document.getElementById('bgCanvas');
const entry = document.getElementById('entry');
const enterBtn = document.getElementById('enterBtn');
const qrBtn = document.getElementById('qrBtn');
const qrModal = document.getElementById('qrModal');
const qrImg = document.getElementById('qrImg');
const closeQr = document.getElementById('closeQr');

const app = document.getElementById('app');
const stageEl = id => document.getElementById(id);
const coinsEl = document.getElementById('coins');
const stageLabel = document.getElementById('stage');

const startBtn = document.getElementById('startBtn');
const playCoins = document.getElementById('playCoins');
const coinCanvas = document.getElementById('coinCanvas');
const timeEl = document.getElementById('time');

const missionBox = document.getElementById('missionBox');
const nextMission = document.getElementById('nextMission');
const skipMissions = document.getElementById('skipMissions');

const boardEl = document.getElementById('board');
const tttReset = document.getElementById('tttReset');
const tttMsg = document.getElementById('tttMsg');
const finishToCert = document.getElementById('finishToCert');

const certCanvas = document.getElementById('certCanvas');
const makeCert = document.getElementById('makeCert');
const openCert = document.getElementById('openCert');

const openWarning = document.getElementById('openWarning');
const restart = document.getElementById('restart');

let state = {
  stage:0, coins:0, coinActive:false, timeLeft:COIN_TIME,
  missionIndex:0, missionLog:[], tttBoard:Array(9).fill(null)
};

// ---- background particles (light & cheap) ----
const bgCtx = bgCanvas.getContext('2d');
function resizeBg(){ bgCanvas.width = innerWidth; bgCanvas.height = innerHeight; }
window.addEventListener('resize', resizeBg);
const particles = [];
function initParticles(){
  resizeBg();
  for(let i=0;i<60;i++){
    particles.push({
      x: Math.random()*bgCanvas.width,
      y: Math.random()*bgCanvas.height,
      r: 0.8 + Math.random()*2.2,
      vy: -0.1 - Math.random()*0.5,
      alpha: 0.2 + Math.random()*0.6,
      glow: 8 + Math.random()*20
    });
  }
  (function loop(){
    bgCtx.clearRect(0,0,bgCanvas.width,bgCanvas.height);
    particles.forEach(p=>{
      const g = bgCtx.createRadialGradient(p.x,p.y,0,p.x,p.y,p.glow);
      g.addColorStop(0, `rgba(255,255,255,${p.alpha})`);
      g.addColorStop(1, 'rgba(255,150,200,0)');
      bgCtx.fillStyle = g;
      bgCtx.fillRect(p.x-p.glow,p.y-p.glow,p.glow*2,p.glow*2);
      p.y += p.vy;
      if(p.y < -50){ p.y = bgCanvas.height + 20; p.x = Math.random()*bgCanvas.width; }
    });
    requestAnimationFrame(loop);
  })();
}

// ---- simple HUD / navigation ----
function setStage(n){
  // hide all stage blocks
  ['stage0','stage1','stage2','stage3','stage4','stage5'].forEach(id=>stageEl(id).classList.add('hidden'));
  stageEl('stage'+n).classList.remove('hidden');
  state.stage = n;
  stageLabel.textContent = n;
  coinsEl.textContent = state.coins;
}

enterBtn.addEventListener('click', ()=> {
  entry.classList.add('hidden');
  app.classList.remove('hidden');
  initParticles();
  setStage(0);
});
qrBtn.addEventListener('click', ()=> {
  qrImg.src = `https://api.qrserver.com/v1/create-qr-code/?size=400x400&ecc=H&data=${encodeURIComponent(location.href)}`;
  qrModal.classList.remove('hidden');
});
closeQr && closeQr.addEventListener('click', ()=> qrModal.classList.add('hidden'));

// ---- Stage 0 -->
startBtn.addEventListener('click', ()=> setStage(1));

// ---- Stage 1: coin mini-game ----
const cctx = coinCanvas.getContext('2d');
let coinParticles = [];
let coinTimer = null;

function spawnCoinParticles(n=18){
  coinParticles = [];
  coinCanvas.width = coinCanvas.clientWidth * devicePixelRatio;
  coinCanvas.height = coinCanvas.clientHeight * devicePixelRatio;
  for(let i=0;i<n;i++){
    coinParticles.push({
      x: Math.random()*coinCanvas.width,
      y: -Math.random()*coinCanvas.height,
      vy: 1 + Math.random()*2,
      r: (10 + Math.random()*12)*devicePixelRatio,
      tapped:false
    });
  }
}

function drawCoins(){
  cctx.clearRect(0,0,coinCanvas.width,coinCanvas.height);
  coinParticles.forEach(p=>{
    const grad = cctx.createLinearGradient(p.x-p.r,p.y-p.r,p.x+p.r,p.y+p.r);
    grad.addColorStop(0,'#ffd681'); grad.addColorStop(1,'#ffb3e6');
    cctx.fillStyle = grad;
    cctx.beginPath();
    cctx.arc(p.x,p.y,p.r,0,Math.PI*2);
    cctx.fill();
    cctx.lineWidth = 2;
    cctx.strokeStyle = '#ffd18a';
    cctx.stroke();
    p.y += p.vy;
    if(p.y > coinCanvas.height + 30){ p.y = -20; p.x = Math.random()*coinCanvas.width; p.tapped=false; }
  });
}

function startCoinRound(){
  if(state.coinActive) return;
  state.coinActive = true;
  state.timeLeft = COIN_TIME;
  timeEl.textContent = state.timeLeft;
  spawnCoinParticles(20);
  coinTimer = setInterval(()=>{
    state.timeLeft--;
    timeEl.textContent = state.timeLeft;
    if(state.timeLeft<=0){ stopCoinRound(); }
  },1000);
  (function loop(){ if(!state.coinActive) return; drawCoins(); requestAnimationFrame(loop); })();
}

function stopCoinRound(){
  clearInterval(coinTimer);
  state.coinActive = false;
  // next stage
  setStage(2);
}

coinCanvas.addEventListener('click', (ev)=>{
  if(!state.coinActive) return;
  const rect = coinCanvas.getBoundingClientRect();
  const x = (ev.clientX - rect.left) * (coinCanvas.width / rect.width);
  const y = (ev.clientY - rect.top) * (coinCanvas.height / rect.height);
  for(let p of coinParticles){
    const dx = x - p.x, dy = y - p.y;
    if(!p.tapped && dx*dx + dy*dy <= p.r*p.r){
      p.tapped = true;
      state.coins++;
      coinsEl.textContent = state.coins;
      // small pop effect
      const orig = p.r;
      let s=0;
      const pop = setInterval(()=>{ s++; p.r = orig + Math.sin((s/6)*Math.PI)*8; if(s>6){ clearInterval(pop); p.r = orig; } },16);
      break;
    }
  }
});

playCoins.addEventListener('click', startCoinRound);

// ---- Stage 2: missions ----
function renderMission(){
  missionBox.innerHTML = '';
  const m = MISSIONS[state.missionIndex] || null;
  if(!m){
    setStage(3);
    return;
  }
  const div = document.createElement('div'); div.className='missionBox';
  div.innerHTML = `<div style="font-weight:700">${m.text}</div>`;
  const ch = document.createElement('div'); ch.className='missionChoices';
  m.choices.forEach(opt=>{
    const b = document.createElement('button'); b.className='choiceBtn'; b.textContent = `${opt.t} (+${opt.c})`;
    b.onclick = ()=>{
      state.coins += opt.c; coinsEl.textContent = state.coins;
      state.missionLog.push({mission:state.missionIndex,choice:opt.t,coins:opt.c});
      state.missionIndex++;
      renderMission();
    };
    ch.appendChild(b);
  });
  div.appendChild(ch);
  missionBox.appendChild(div);
}
nextMission.addEventListener('click', ()=> renderMission());
skipMissions.addEventListener('click', ()=> setStage(3));

// ---- Stage 3: TicTacToe (Minimax AI) ----
function makeBoard(){
  boardEl.innerHTML = '';
  state.tttBoard = Array(9).fill(null);
  for(let i=0;i<9;i++){
    const cell = document.createElement('div'); cell.className='cell'; cell.dataset.idx = i;
    cell.addEventListener('click', ()=> humanMove(i));
    boardEl.appendChild(cell);
  }
  tttMsg.textContent = 'Your move (X).';
}

function humanMove(i){
  if(state.tttBoard[i] || checkWinner(state.tttBoard)) return;
  state.tttBoard[i] = 'X';
  updateBoard();
  if(checkWinner(state.tttBoard) || isBoardFull(state.tttBoard)) return;
  tttMsg.textContent = 'Portal is thinking...';
  setTimeout(()=>{ aiMove(); }, 240);
}

function aiMove(){
  const idx = minimaxRoot(state.tttBoard, 'O');
  if(idx != null){ state.tttBoard[idx] = 'O'; }
  updateBoard();
  const winner = checkWinner(state.tttBoard);
  if(winner) tttMsg.textContent = winner==='X' ? 'You win!' : 'Portal wins.';
  else if(isBoardFull(state.tttBoard)) tttMsg.textContent = "It's a draw.";
  else tttMsg.textContent = 'Your move.';
}

function updateBoard(){
  for(let i=0;i<9;i++){
    const cell = boardEl.children[i];
    cell.textContent = state.tttBoard[i] || '';
    if(state.tttBoard[i]) cell.classList.add('disabled'); else cell.classList.remove('disabled');
  }
}

function isBoardFull(b){ return b.every(c=>c); }
function checkWinner(b){
  const win = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
  for(const w of win){
    const [a,b1,c] = w;
    if(b[a] && b[a]===b[b1] && b[a]===b[c]) return b[a];
  }
  return null;
}

// Minimax implementation (unbeatable for 3x3)
// returns index for best move for player ('O') at root
function minimaxRoot(newBoard, player){
  const avail = newBoard.map((v,i)=> v ? null : i).filter(v=>v!==null);
  let bestScore = -Infinity;
  let move = null;
  for(const i of avail){
    const boardCopy = newBoard.slice(); boardCopy[i] = player;
    const score = minimax(boardCopy, 0, false);
    if(score > bestScore){ bestScore = score; move = i; }
  }
  return move;
}
function minimax(board, depth, isMaximizing){
  const winner = checkWinner(board);
  if(winner === 'O') return 10 - depth;
  if(winner === 'X') return depth - 10;
  if(isBoardFull(board)) return 0;
  if(isMaximizing){
    let best = -Infinity;
    for(let i=0;i<9;i++){
      if(!board[i]){
        board[i]='O';
        best = Math.max(best, minimax(board, depth+1, false));
        board[i]=null;
      }
    }
    return best;
  } else {
    let best = Infinity;
    for(let i=0;i<9;i++){
      if(!board[i]){
        board[i]='X';
        best = Math.min(best, minimax(board, depth+1, true));
        board[i]=null;
      }
    }
    return best;
  }
}

tttReset.addEventListener('click', makeBoard);
finishToCert.addEventListener('click', ()=> setStage(4));

// ---- Stage 4: certificate generation & save ----
function drawCertificate(){
  const c = certCanvas;
  const ctx = c.getContext('2d');
  // background parchment tone
  ctx.fillStyle = '#fff6f8'; ctx.fillRect(0,0,c.width,c.height);
  // soft border
  ctx.strokeStyle = '#d9a27a'; ctx.lineWidth = 12;
  roundRect(ctx, 30,30, c.width-60, c.height-60, 22, false, true);
  // title
  ctx.fillStyle = '#5a1537'; ctx.font = '32px serif'; ctx.textAlign='center';
  ctx.fillText('Certificate of Unescapable Friendship', c.width/2, 120);
  // name block
  ctx.font = '40px serif'; ctx.fillStyle = '#3b0d26';
  ctx.fillText(PLAYER_NAME, c.width/2, 220);
  // message
  ctx.font = '20px sans-serif'; ctx.fillStyle = '#4b1233';
  const msg = `This certifies that ${PLAYER_NAME} is forcefully enrolled in this Princess Friendship. Escape is not an option.`;
  wrapText(ctx, msg, c.width/2, 280, c.width-220, 26);
  // seal
  ctx.beginPath(); ctx.fillStyle = '#ffb3e6'; ctx.arc(c.width/2, c.height-180, 56, 0, Math.PI*2); ctx.fill();
  ctx.fillStyle = '#5a1537'; ctx.font = '16px serif'; ctx.fillText('PRINCESS SEAL', c.width/2, c.height-176);
}

makeCert.addEventListener('click', ()=>{
  drawCertificate();
  // create high-res version and save to localStorage
  const scale = 2;
  const tmp = document.createElement('canvas'); tmp.width = certCanvas.width*scale; tmp.height = certCanvas.height*scale;
  const tctx = tmp.getContext('2d'); tctx.scale(scale, scale);
  // re-draw (simplified)
  tctx.fillStyle = '#fff6f8'; tctx.fillRect(0,0,certCanvas.width,certCanvas.height);
  tctx.strokeStyle = '#d9a27a'; tctx.lineWidth = 12;
  roundRect(tctx,30,30,certCanvas.width-60,certCanvas.height-60,22,false,true);
  tctx.fillStyle = '#5a1537'; tctx.font = '32px serif'; tctx.textAlign='center';
  tctx.fillText('Certificate of Unescapable Friendship', certCanvas.width/2, 120);
  tctx.font = '40px serif'; tctx.fillStyle = '#3b0d26'; tctx.fillText(PLAYER_NAME, certCanvas.width/2, 220);
  tctx.font = '20px sans-serif'; tctx.fillStyle = '#4b1233';
  const msg = `This certifies that ${PLAYER_NAME} is forcefully enrolled in this Princess Friendship. Escape is not an option.`;
  // center wrap
  (function wrap(){
    tctx.textAlign='center';
    const words = msg.split(' '); let line=''; let y=280; for(let n=0;n<words.length;n++){
      const test = line + words[n] + ' ';
      if(tctx.measureText(test).width > certCanvas.width-220 && n>0){ tctx.fillText(line, certCanvas.width/2, y); line=words[n]+' '; y+=26; } else line=test;
    }
    tctx.fillText(line, certCanvas.width/2, y);
  })();
  tctx.beginPath(); tctx.fillStyle = '#ffb3e6'; tctx.arc(certCanvas.width/2, certCanvas.height-180, 56,0,Math.PI*2); tctx.fill();
  tctx.fillStyle = '#5a1537'; tctx.font='16px serif'; tctx.fillText('PRINCESS SEAL', certCanvas.width/2, certCanvas.height-176);
  // save
  const dataUrl = tmp.toDataURL('image/png');
  try{ localStorage.setItem('mystic_cert', dataUrl); } catch(e){ console.warn('localStorage error', e); }
  openCert.classList.remove('hidden');
  alert('Certificate generated. You can open it on the new Certificate page.');
});

// open certificate page button should link to certificate.html
openCert.addEventListener('click', ()=> window.open('certificate.html','_blank'));

// ---- Stage 5 final
restart.addEventListener('click', ()=> location.reload());

// ---- helpers ----
function roundRect(ctx,x,y,w,h,r,fill,stroke){
  ctx.beginPath(); ctx.moveTo(x+r,y); ctx.arcTo(x+w,y,x+w,y+h,r); ctx.arcTo(x+w,y+h,x,y+h,r); ctx.arcTo(x,y+h,x,y,r); ctx.arcTo(x,y,x+w,y,r); ctx.closePath();
  if(fill) ctx.fill(); if(stroke) ctx.stroke();
}
function wrapText(ctx, text, x, y, maxWidth, lineHeight){
  ctx.textAlign='center';
  const words = text.split(' '); let line=''; let row=0;
  for(let n=0;n<words.length;n++){
    const test = line + words[n] + ' ';
    if(ctx.measureText(test).width > maxWidth && n>0){ ctx.fillText(line, x, y + row*lineHeight); line=words[n]+' '; row++; } else line=test;
  }
  ctx.fillText(line, x, y + row*lineHeight);
}

// ---- init UI ----
function init(){
  document.querySelector('.subtitle strong').textContent = PLAYER_NAME;
  document.getElementById('playerNameDisplay').textContent = PLAYER_NAME;
  setStage(0);
  // pre-setup
  makeBoardUI();
}
init();

// ---- TicTacToe UI builder ----
function makeBoardUI(){
  boardEl.innerHTML = '';
  for(let i=0;i<9;i++){
    const div = document.createElement('div'); div.className='cell'; div.dataset.i = i;
    div.addEventListener('click', ()=> humanMove(i));
    boardEl.appendChild(div);
  }
  state.tttBoard = Array(9).fill(null);
  tttMsg.textContent = 'Your move.';
}
function humanMove(i){
  if(state.tttBoard[i] || checkWinner(state.tttBoard)) return;
  state.tttBoard[i] = 'X'; updateBoard();
  if(checkWinner(state.tttBoard) || isBoardFull(state.tttBoard)) return;
  setTimeout(()=>{ const ai = minimaxRoot(state.tttBoard,'O'); if(ai!=null){ state.tttBoard[ai]='O'; updateBoard(); } }, 240);
}
function updateBoard(){
  for(let i=0;i<9;i++){
    const cell = boardEl.children[i]; cell.textContent = state.tttBoard[i]||''; cell.classList.toggle('disabled', !!state.tttBoard[i]);
  }
  const w = checkWinner(state.tttBoard);
  if(w) tttMsg.textContent = (w==='X' ? 'You win!' : 'Portal wins.');
  else if(isBoardFull(state.tttBoard)) tttMsg.textContent = "Draw.";
  else tttMsg.textContent = 'Your move.';
}
tttReset.addEventListener('click', makeBoardUI);

// ---- minimax (same as earlier but localized) ----
function isBoardFull(b){ return b.every(Boolean); }
function checkWinner(b){
  const lines = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
  for(const [a,b1,c] of lines){ if(b[a] && b[a]===b[b1] && b[a]===b[c]) return b[a]; }
  return null;
}
function minimaxRoot(board, player){
  const avail = board.map((v,i)=> v ? null : i).filter(x=>x!==null);
  let best = -Infinity, move = null;
  for(const i of avail){
    board[i] = player;
    const score = minimax(board,0,false);
    board[i] = null;
    if(score > best){ best = score; move = i; }
  }
  return move;
}
function minimax(board, depth, isMax){
  const winner = checkWinner(board);
  if(winner === 'O') return 10 - depth;
  if(winner === 'X') return depth - 10;
  if(isBoardFull(board)) return 0;
  if(isMax){
    let best = -Infinity;
    for(let i=0;i<9;i++){ if(!board[i]){ board[i]='O'; best = Math.max(best, minimax(board, depth+1, false)); board[i]=null; } }
    return best;
  } else {
    let best = Infinity;
    for(let i=0;i<9;i++){ if(!board[i]){ board[i]='X'; best = Math.min(best, minimax(board, depth+1, true)); board[i]=null; } }
    return best;
  }
}
