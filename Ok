<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🔥 Онлайн Платформер</title>
<style>
body {
  margin:0;
  font-family:'Segoe UI',Arial,sans-serif;
  overflow:hidden;
  background:linear-gradient(270deg,#ff4e50,#f9d423,#1a2a6c,#b21f1f,#fdbb2d);
  background-size:1000% 1000%;
  animation:gradientBG 25s ease infinite;
  color:#fff;
}
@keyframes gradientBG {
  0%{background-position:0% 50%;}
  50%{background-position:100% 50%;}
  100%{background-position:0% 50%;}
}
#startScreen {
  position:fixed;top:0;left:0;width:100%;height:100%;
  display:flex;flex-direction:column;justify-content:center;align-items:center;
  background:rgba(0,0,0,0.6);
  animation:fadeIn 1s forwards;
}
#startScreen h1 {
  font-size:4em;
  margin-bottom:40px;
  text-shadow:0 0 20px #fff;
  animation:textGlow 2s infinite alternate;
}
@keyframes textGlow{
  0%{text-shadow:0 0 10px #fff,0 0 20px #f0f,0 0 30px #0ff;}
  100%{text-shadow:0 0 20px #fff,0 0 40px #f0f,0 0 60px #0ff;}
}
#startScreen button {
  padding:20px 40px;
  margin:15px;
  font-size:1.5em;
  border:none;
  border-radius:15px;
  cursor:pointer;
  background:rgba(255,255,255,0.2);
  color:#fff;
  backdrop-filter:blur(5px);
  transition:0.3s;
  box-shadow:0 0 10px #fff;
}
#startScreen button:hover {
  background:rgba(255,255,255,0.4);
  transform:scale(1.1);
}
#loadingScreen {
  position:fixed;top:0;left:0;width:100%;height:100%;
  display:flex;flex-direction:column;justify-content:center;align-items:center;
  background:rgba(0,0,0,0.8);
  color:#0f0;
  font-size:2em;
  display:none;
}
#loadingBarWrapper {width:350px;height:25px;border:2px solid #0f0;border-radius:15px;overflow:hidden;margin-top:20px;}
#loadingBar {width:0%;height:100%;background:#0f0;transition:width 0.2s ease;}
#game {
  position:absolute;
  width:700px;height:450px;
  left:50%;top:50%;
  transform:translate(-50%,-50%);
  background:rgba(0,0,0,0.5);
  border:2px solid #fff;
  border-radius:15px;
  overflow:hidden;
  box-shadow:0 0 30px #0ff;
  display:none; /* скрываем до загрузки */
}
#player {
  position:absolute;width:50px;height:60px;background-color:#0ff;border-radius:10px;
  box-shadow:0 0 15px #0ff;
}
.platform {
  position:absolute;
  background-color:#fff;
  border-radius:8px;
  box-shadow:0 0 10px #fff;
}
#settingsBtn {
  position:fixed;top:20px;right:20px;
  font-size:26px;
  background:rgba(0,0,0,0.5);
  border:2px solid #fff;
  border-radius:10px;
  padding:10px 15px;
  cursor:pointer;
  transition:0.3s;
  box-shadow:0 0 10px #fff;
}
#settingsBtn:hover {transform:scale(1.1);}
#settingsModal {
  display:none;
  position:fixed;
  top:70px;right:20px;
  width:340px;
  background:rgba(20,20,20,0.95);
  padding:20px;
  border:2px solid #fff;
  border-radius:15px;
  box-shadow:0 0 20px #0ff;
  opacity:0;transform:scale(0.8);
  transition:0.3s;
}
#settingsModal.active {
  display:block;opacity:1;transform:scale(1);
}
#settingsModal label {
  display:flex;align-items:center;margin-bottom:12px;font-size:16px;
}
#settingsModal label span.icon {
  width:28px;text-align:center;margin-right:10px;font-size:18px;
}
#controls {
  position:fixed;bottom:25px;left:50%;
  transform:translateX(-50%);
  display:flex;gap:25px;
  z-index:300;
}
#controls button {
  font-size:28px;
  border-radius:20px;
  border:2px solid #fff;
  background-color:rgba(0,0,0,0.6);
  color:#fff;
  touch-action:none;
  transition:0.1s;
  box-shadow:0 0 15px #0ff;
}
#controls button:active {transform:scale(0.95);}
</style>
</head>
<body>

<div id="startScreen">
  <h1>🔥 Онлайн Платформер</h1>
  <button id="offlineBtn">Офлайн</button>
  <button id="onlineBtn">Онлайн</button>
</div>

<div id="loadingScreen">
  <div>Загрузка игры...</div>
  <div id="loadingBarWrapper"><div id="loadingBar"></div></div>
</div>

<div id="game"><div id="player"></div></div>

<button id="settingsBtn">🛠️</button>
<div id="settingsModal">
  <label><span class="icon">🎵</span>Громкость: <input type="range" id="volumeControl" min="0" max="1" step="0.01" value="0.5"></label>
  <label><span class="icon">⚡</span>FPS: 
    <select id="fpsLimitSelect">
      <option value="30">30</option>
      <option value="60" selected>60</option>
      <option value="90">90</option>
      <option value="120">120</option>
      <option value="144">144</option>
      <option value="165">165</option>
      <option value="180">180</option>
    </select>
  </label>
  <label><span class="icon">📊</span>Показывать FPS: <input type="checkbox" id="fpsToggle" checked></label>
  <label><span class="icon">🌐</span>Язык:
    <select id="languageSelect">
      <option value="ru">Русский</option>
      <option value="en">English</option>
    </select>
  </label>
  <label><span class="icon">🌞</span>Яркость: <input type="range" id="brightness" min="0.5" max="2" step="0.05" value="1"></label>
  <label><span class="icon">🌈</span>Насыщенность: <input type="range" id="saturation" min="0" max="3" step="0.05" value="1"></label>
  <label><span class="icon">🔹</span>Контраст: <input type="range" id="contrast" min="0.5" max="2" step="0.05" value="1"></label>
  <label><span class="icon">🖼️</span>Качество графики:
    <select id="graphicsQuality">
      <option value="low">Низкий</option>
      <option value="medium">Средний</option>
      <option value="high" selected>Высокий</option>
      <option value="ultra">Ультра</option>
    </select>
  </label>
  <label><span class="icon">🎮</span>Размер кнопок: <input type="range" id="buttonSize" min="20" max="60" step="2" value="28"></label>
  <label><span class="icon">🚀</span>Скорость игрока: <input type="range" id="playerSpeed" min="2" max="10" step="0.5" value="4"></label>
</div>

<div id="controls">
  <button id="leftBtn">←</button>
  <button id="jumpBtn">↑</button>
  <button id="rightBtn">→</button>
</div>

<audio id="bgMusic" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>
<button id="playMusic">Включить музыку</button>

<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-database-compat.js"></script>
<script>
// --- Firebase config ---
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT.firebaseio.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "SENDER_ID",
  appId: "APP_ID"
};
firebase.initializeApp(firebaseConfig);
const db = firebase.database();
let playerId = 'player_'+Date.now();
let otherPlayersDivs = {};
let isOnline = false;

// --- Start screen ---
const startScreen = document.getElementById('startScreen');
const offlineBtn = document.getElementById('offlineBtn');
const onlineBtn = document.getElementById('onlineBtn');
const loadingScreen = document.getElementById('loadingScreen');
const loadingBar = document.getElementById('loadingBar');
const game = document.getElementById('game');

offlineBtn.onclick = ()=>{isOnline=false; startGame();};
onlineBtn.onclick = ()=>{isOnline=true; startGame();};

function startGame(){
  startScreen.style.display='none';
  loadingScreen.style.display='flex';
  simulateLoading();
}

// --- Настройки ---
const settingsBtn = document.getElementById('settingsBtn');
const settingsModal = document.getElementById('settingsModal');
settingsBtn.addEventListener('click', ()=>{
  settingsModal.classList.toggle('active'); // открывает/закрывает
});

// --- Player and game ---
const player = document.getElementById('player');
const platforms = [
  {x:0,y:400,width:700,height:20},
  {x:150,y:320,width:120,height:15},
  {x:350,y:250,width:100,height:15},
  {x:200,y:180,width:150,height:15},
];
platforms.forEach(p=>{
  const plat=document.createElement('div');
  plat.className='platform';
  plat.style.left=p.x+'px';
  plat.style.top=p.y+'px';
  plat.style.width=p.width+'px';
  plat.style.height=p.height+'px';
  game.appendChild(plat);
});

let playerState={x:50,y:340,width:50,height:60,vx:0,vy:0,speed:4,jumpPower:12,grounded:false};
let keys = {};
document.addEventListener('keydown',e=>keys[e.key.toLowerCase()]=true);
document.addEventListener('keyup',e=>keys[e.key.toLowerCase()]=false);

const leftBtn = document.getElementById('leftBtn');
const rightBtn = document.getElementById('rightBtn');
const jumpBtn = document.getElementById('jumpBtn');
[leftBtn,rightBtn,jumpBtn].forEach(btn=>{
  btn.addEventListener('touchstart',()=>keys[btn.id.replace('Btn','').toLowerCase()]=true);
  btn.addEventListener('touchend',()=>keys[btn.id.replace('Btn','').toLowerCase()]=false);
});

// --- Настройки динамически ---
const volumeControl=document.getElementById('volumeControl');
const fpsLimitSelect=document.getElementById('fpsLimitSelect');
const fpsToggle=document.getElementById('fpsToggle');
const brightnessSlider=document.getElementById('brightness');
const saturationSlider=document.getElementById('saturation');
const contrastSlider=document.getElementById('contrast');
const graphicsQuality=document.getElementById('graphicsQuality');
const buttonSize=document.getElementById('buttonSize');
const playerSpeed=document.getElementById('playerSpeed');
const languageSelect=document.getElementById('languageSelect');

const controls=document.getElementById('controls');
volumeControl.addEventListener('input',()=>bgMusic.volume=volumeControl.value);
fpsLimitSelect.addEventListener('change',()=>fpsLimit=parseInt(fpsLimitSelect.value));
buttonSize.addEventListener('input',()=>[...controls.children].forEach(b=>b.style.fontSize=buttonSize.value+'px'));
playerSpeed.addEventListener('input',()=>playerState.speed=parseFloat(playerSpeed.value));
[brightnessSlider,saturationSlider,contrastSlider].forEach(slider=>{
  slider.addEventListener('input',()=>{
    game.style.filter=`brightness(${brightnessSlider.value}) saturate(${saturationSlider.value}) contrast(${contrastSlider.value})`;
  });
});

// --- Player movement ---
function updatePlayer(){
  playerState.vx=0;
  if(keys['left']||keys['a']) playerState.vx=-playerState.speed;
  if(keys['right']||keys['d']) playerState.vx=playerState.speed;
  if((keys['jump']||keys['w']||keys[' ']) && playerState.grounded){playerState.vy=-playerState.jumpPower; playerState.grounded=false;}
  playerState.vy+=0.5;
  playerState.x+=playerState.vx;
  playerState.y+=playerState.vy;
  playerState.grounded=false;
  platforms.forEach(p=>{
    if(playerState.x<p.x+p.width && playerState.x+playerState.width>p.x &&
       playerState.y+playerState.height>p.y && playerState.y+playerState.height<p.y+p.height+playerState.vy){
         playerState.y=p.y-playerState.height;
         playerState.vy=0;
         playerState.grounded=true;
       }
  });
  if(playerState.x<0) playerState.x=0;
  if(playerState.x+playerState.width>game.clientWidth) playerState.x=game.clientWidth-playerState.width;
  if(playerState.y+playerState.height>game.clientHeight){playerState.y=game.clientHeight-playerState.height; playerState.vy=0; playerState.grounded=true;}
  
  if(isOnline){
    db.ref('players/'+playerId).set({x:playerState.x,y:playerState.y});
  }
}

function renderPlayer(){player.style.left=playerState.x+'px'; player.style.top=playerState.y+'px';}

// --- Game loop ---
let fpsLimit = 60;
let lastFrameTime = performance.now();
function gameLoop(now){
  const delta=now-lastFrameTime;
  const interval=1000/fpsLimit;
  if(delta>=interval){
    updatePlayer();
    renderPlayer();
    lastFrameTime=now-(delta%interval);
  }
  requestAnimationFrame(gameLoop);
}

// --- Loading ---
function simulateLoading(){
  let loadProgress=0;
  const interval=setInterval(()=>{
    loadProgress+=Math.random()*5+2;
    if(loadProgress>=100) loadProgress=100;
    loadingBar.style.width=loadProgress+'%';
    if(loadProgress>=100){
      clearInterval(interval);
      loadingScreen.style.transition='opacity 0.5s';
      loadingScreen.style.opacity='0';
      setTimeout(()=>{
        loadingScreen.style.display='none';
        game.style.display='block';
        requestAnimationFrame(gameLoop);
      },500);
    }
  },100);
}

// --- Music ---
const bgMusic = document.getElementById('bgMusic');
const playMusicBtn = document.getElementById('playMusic');
playMusicBtn.onclick = ()=>bgMusic.play();
</script>
</body>
</html>
