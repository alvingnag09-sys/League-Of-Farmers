<!DOCTYPE html><html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover"><title>League Of Farmers</title>
<style>
:root{--bg:#222;--pn:#c6c6c6;--ink:#222;--bd:#555;--ac:#5cb338;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme=light]){--pn:#8b8b8b;--ink:#111}}
html,body{height:100%;margin:0;background:#87ceeb;overflow:hidden;font-family:"Courier New",monospace;touch-action:none;user-select:none;-webkit-user-select:none}
canvas{display:block;position:fixed;inset:0}
button{font:inherit;font-weight:bold;background:var(--pn);color:var(--ink);border:3px solid var(--bd);border-radius:0;padding:6px 9px;box-shadow:inset -3px -3px #0004,inset 3px 3px #fff6}
button:active{filter:brightness(.8)}
#top{position:fixed;top:calc(6px + env(safe-area-inset-top,0px));left:8px;right:8px;display:flex;gap:6px;justify-content:space-between;pointer-events:none}
#top span,#top button{pointer-events:auto;background:#000a;color:#fff;padding:5px 9px;border:2px solid #fff6;font-weight:bold;font-size:14px}
#banner{position:fixed;top:48px;left:50%;transform:translateX(-50%);background:#000b;color:#fff;padding:6px 14px;border:2px solid #fff;font-weight:bold;display:none;text-align:center;font-size:15px}
#bar{position:fixed;right:8px;bottom:8px;display:grid;grid-template-columns:1fr 1fr;gap:4px}#bar button{padding:4px 7px;font-size:18px}#sv{opacity:.3;transition:opacity .4s}
#hot{position:fixed;left:50%;bottom:8px;transform:translateX(-50%);display:flex;gap:3px;background:#000a;padding:3px;border:2px solid #000}
.slot{flex:0 0 auto;width:42px;height:46px;background:#8b8b8b;border:3px solid #373737;color:#fff;font-size:11px;text-align:center;position:relative;line-height:1}
.slot b{display:block;font-size:22px;margin-top:3px}.slot i{position:absolute;right:2px;bottom:1px;font-style:normal;text-shadow:1px 1px #000}
.slot.on{border-color:#fff;background:#aaa}
#stick{position:fixed;left:18px;bottom:18px;width:110px;height:110px;border-radius:50%;background:#fff3;border:3px solid #fff8}
#knob{position:absolute;left:35px;top:35px;width:40px;height:40px;border-radius:50%;background:#fffc}
#panel{position:fixed;left:50%;top:50%;transform:translate(-50%,-50%);width:min(560px,94vw);max-height:84vh;overflow:auto;background:var(--pn);color:var(--ink);border:4px solid #000;padding:10px;display:none;touch-action:pan-y}
#ph{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;font-size:18px}
.row{display:flex;justify-content:space-between;align-items:center;gap:8px;border-bottom:2px solid #0003;padding:5px 0;font-size:14px}
small{opacity:.75}
#start,#rot{position:fixed;inset:0;background:#000c;color:#fff;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;gap:12px;font-size:18px;z-index:9;padding:20px}
#rot{display:none;z-index:10}
#start h1{margin:0;color:#7bd34a;text-shadow:3px 3px #000}
#toast{position:fixed;left:50%;top:92px;transform:translateX(-50%);color:#fff;background:#000c;padding:5px 12px;border:2px solid #fff6;display:none;font-size:14px;text-align:center}
.ic{image-rendering:pixelated;vertical-align:middle}.slot img{width:30px;height:30px;image-rendering:pixelated;display:block;margin:2px auto 0}.slot{transition:transform .1s}.slot.on{transform:translateY(-5px)}
.tb{font-style:normal;font-size:10px;color:#fff;padding:1px 5px;text-shadow:1px 1px #000}.grid{display:grid;grid-template-columns:repeat(auto-fill,76px);gap:6px;margin:6px 0 10px}
.frame{background:#d9b26f;border:4px solid;outline:3px solid #6b4423;text-align:center;padding:3px;font-size:10px;color:#222}.frame img{width:56px;height:56px;image-rendering:pixelated}.lock img{filter:brightness(0);opacity:.5}
#hatch{position:fixed;inset:0;background:#000d;color:#fff;display:none;flex-direction:column;align-items:center;justify-content:center;gap:10px;z-index:8;font-size:18px}
.shake{animation:sh .25s infinite}@keyframes sh{0%,100%{transform:rotate(-12deg)}50%{transform:rotate(12deg)}}.pop{animation:po .5s}@keyframes po{0%{transform:scale(0)}70%{transform:scale(1.3)}100%{transform:scale(1)}}#panel{animation:fd .2s}@keyframes fd{from{opacity:0}}
#jump,#bm,#fish{position:fixed;border-radius:50%;padding:0;z-index:3;font-size:24px}
#jump{right:116px;bottom:16px;width:68px;height:68px}#bm{right:124px;bottom:96px;width:52px;height:52px}#bm.on{background:#7bd34a}
#fish{right:196px;bottom:70px;width:62px;height:62px;display:none}
.slot b{font-size:20px}
.slot s{position:absolute;left:2px;top:0;font-size:9px;text-decoration:none;opacity:.8}.dim{opacity:.55}
.bgrid{display:grid;grid-template-columns:repeat(auto-fill,50px);gap:4px;margin:6px 0 10px}.bgrid .slot{width:42px}
@media(max-width:760px){.slot{width:34px;height:40px}.slot img{width:24px;height:24px}.slot b{font-size:18px}}
#brh{position:fixed;top:calc(44px + env(safe-area-inset-top,0px));left:8px;display:none;gap:6px;align-items:center;z-index:2;pointer-events:none}
#brh span,#brh button{background:#000a;color:#fff;padding:4px 8px;border:2px solid #fff6;font-weight:bold;font-size:13px}#brh button{pointer-events:auto}#ba{display:inline-block;color:#7bd3ff;font-style:normal}
#brp2{position:fixed;left:50%;bottom:66px;transform:translateX(-50%);width:min(300px,46vw);display:none;flex-direction:column;gap:3px;z-index:2;pointer-events:none}
#bhp,#bsh{height:16px;background:#000a;border:2px solid #000;position:relative}#bsh{height:8px}#bhp i{display:block;height:100%;background:#e53935;width:100%}#bsh i{display:block;height:100%;background:#42a5f5;width:0}
#hpt{position:absolute;inset:0;text-align:center;color:#fff;font-size:12px;line-height:16px;text-shadow:1px 1px #000}
#brhot{position:fixed;left:50%;bottom:8px;transform:translateX(-50%);display:none;gap:3px;background:#000a;padding:3px;border:2px solid #000;z-index:2}
#atk,#heal,#rel{position:fixed;display:none;border-radius:50%;padding:0;z-index:3;font-size:26px}
#atk{right:20px;bottom:20px;width:80px;height:80px;background:#e57373}#heal{right:20px;bottom:112px;width:56px;height:56px}#rel{right:116px;bottom:96px;width:52px;height:52px}
#hurt{position:fixed;inset:0;pointer-events:none;box-shadow:inset 0 0 120px 40px #f00;opacity:0;z-index:4}
#brend{position:fixed;inset:0;background:#000c;color:#fff;display:none;flex-direction:column;align-items:center;justify-content:center;text-align:center;gap:14px;font-size:20px;z-index:8}
</style></head><body>
<div id="top"><span id="money"></span><span id="clock"></span><span id="sv">💾</span><button onclick="skin()">Skin</button><button onclick="muteT(this)">🔊</button></div>
<div id="banner"></div><div id="toast"></div>
<div id="hot"></div>
<div id="bar"><button title="Pets" onclick="P('pets')">🐾</button><button title="Sell" onclick="P('sell')">💰</button><button title="Index" onclick="P('index')">📖</button><button title="Teleport" onclick="P('tp')">🧭</button><button title="My garden" onclick="tp('garden')">🏡</button><button title="Bag" onclick="P('bag')">🎒</button><button title="Craft" onclick="P('craft')">🔨</button><button title="Fishing" onclick="P('fish')">🎣</button></div>
<button id="jump">⤒</button><button id="fish" onclick="fishBtn()">🎣</button>
<div id="stick"><div id="knob"></div></div>
<div id="panel"><div id="ph"><b id="pt"></b><button onclick="closeP()">✕</button></div><div id="pb"></div></div>
<div id="start"><h1>LEAGUE OF FARMERS</h1><div>Blocky Edition · Battle Royale</div><small>🌀 NEW: walk into the purple portal near the shops for a 20-player Battle Royale · ⚔️ Weapon Shop sells Sword, Crossbow &amp; Pistol<br>Gold ×5 · Rainbow ×10 variants · Winter event!<br>Drag: rotate camera · Pinch/scroll: zoom<br>Stick or WASD: move · Tap a plot: plant · tap a crop to see value · tap again to harvest<br>6 bases: visit farmers & trade seeds, pets, coins<br>Tap shop NPCs to buy · 🧭 teleport · 🏡 home · Auto-saves<br>⤒ / Space: jump · 🎒 bag &amp; hotbar (keys 1-6) · 🔨 craft &amp; expand your Build Yard · 🎣 fish at the pond</small><button style="font-size:20px;padding:10px 24px">▶ PLAY</button></div>
<div id="hatch"></div><div id="rot">📱 Please rotate your device to landscape</div>
<div id="brh"><span id="bri"></span><span id="brz"></span><span><i id="ba">▲</i><b id="bd"></b></span><button onclick="leaveBR(1)">🚪</button></div>
<div id="brp2"><div id="bsh"><i></i></div><div id="bhp"><i></i><b id="hpt"></b></div></div><div id="brhot"></div>
<button id="atk">⚔</button><button id="heal">💊</button><button id="rel">🔄</button><div id="hurt"></div><div id="brend"></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
var BR={on:0,drop:0};const $=id=>document.getElementById(id),R=(a,b)=>a+Math.random()*(b-a),cl=(v,a,b)=>Math.max(a,Math.min(b,v));
const TIER=['Common','Uncommon','Rare','Legendary','Mythic'],TC=['#9e9e9e','#3fbf3f','#3a8fe8','#ffb300','#ff4de1'],TM=[1,1.25,1.6,2.2,3],CT={carrot:0,strawberry:0,tomato:1,corn:1,blueberry:1,pumpkin:2,bamboo:2,melon:3,apple:3,dfruit:4,cactus:4,moonflower:4};
const CROPS={carrot:{n:'Carrot',e:'🥕',cost:10,t:20,kg:[.2,1.2],p:14,col:0xff8c1a,d:[.25,.6,.25]},strawberry:{n:'Strawberry',e:'🍓',cost:25,t:25,kg:[.1,.7],p:45,col:0xe0203a,d:[.3,.3,.3]},tomato:{n:'Tomato',e:'🍅',cost:45,t:35,kg:[.4,2.5],p:32,col:0xe53935,d:[.5,.5,.5]},corn:{n:'Corn',e:'🌽',cost:80,t:45,kg:[.5,3],p:40,col:0xf2d13a,d:[.3,.9,.3]},blueberry:{n:'Blueberry',e:'🫐',cost:130,t:40,kg:[.2,1.2],p:100,col:0x3b5bdb,d:[.3,.3,.3]},pumpkin:{n:'Pumpkin',e:'🎃',cost:160,t:60,kg:[2,12],p:55,col:0xe8731a,d:[.8,.6,.8]},bamboo:{n:'Bamboo',e:'🎋',cost:420,t:70,kg:[3,15],p:38,col:0x6dbf3a,d:[.3,1.6,.3]},melon:{n:'Melon',e:'🍈',cost:520,t:90,kg:[4,25],p:120,col:0x7ccf3a,d:[.8,.8,.8]},apple:{n:'Apple',e:'🍎',cost:1400,t:100,kg:[3,14],p:200,col:0xd62828,d:[.6,.6,.6]},dfruit:{n:'Dragonfruit',e:'🐲',cost:2500,t:120,kg:[3,20],p:260,col:0xe91e8c,d:[.7,.7,.7]},cactus:{n:'Cactus',e:'🌵',cost:6000,t:150,kg:[5,30],p:340,col:0x2e9e57,d:[.5,1.4,.5]},moonflower:{n:'Moonflower',e:'🌙',cost:15000,t:200,kg:[2,12],p:900,col:0xb8c4ff,d:[.6,.8,.6]}};
const MUT={wet:{n:'Wet',m:2,c:0x4aa3ff},chilled:{n:'Chilled',m:3,c:0x9fe3ff},moon:{n:'Moonlit',m:3,c:0xb8c4ff},blood:{n:'Bloodlit',m:4,c:0xc01818},shocked:{n:'Shocked',m:5,c:0xfff23a},twisted:{n:'Twisted',m:8,c:0xb04aff},frozen:{n:'Frozen',m:10,c:0xd8f6ff}};
const BASE={normal:{n:'Normal',m:1},gold:{n:'Gold',m:5},rainbow:{n:'Rainbow',m:10}};
const PETS={dog:{n:'Dog',e:'🐶',col:0xb5855a,a:'sell'},pig:{n:'Pig',e:'🐷',col:0xf2a6b0,a:'sell'},chicken:{n:'Chicken',e:'🐔',col:0xffffff,c2:0xff4040,a:'grow'},rabbit:{n:'Rabbit',e:'🐰',col:0xf0e6dc,c2:0xffffff,a:'grow'},cat:{n:'Cat',e:'🐱',col:0x888888,a:'kg'},bee:{n:'Bee',e:'🐝',col:0xf5d020,c2:0x222222,a:'mut'},fox:{n:'Fox',e:'🦊',col:0xe8752a,a:'grow'},turtle:{n:'Turtle',e:'🐢',col:0x4c9a4c,c2:0x8bc34a,a:'sell'},wolf:{n:'Wolf',e:'🐺',col:0x8d949c,c2:0x6c737a,a:'sell'},penguin:{n:'Penguin',e:'🐧',col:0x222831,c2:0xffffff,a:'mut'},panda:{n:'Panda',e:'🐼',col:0xffffff,c2:0x111111,a:'kg'},polar:{n:'Polar Bear',e:'🐻',col:0xffffff,c2:0xe3edf5,a:'kg'},dragon:{n:'Dragon',e:'🐉',col:0x3aa655,c2:0xc03030,a:'all'},unicorn:{n:'Unicorn',e:'🦄',col:0xffffff,c2:0xffb8ec,a:'all'},cow:{n:'Cow',e:'🐮',col:0xffffff,c2:0x222222,a:'sz'},duck:{n:'Duck',e:'🦆',col:0xf5e050,c2:0xf59a1a,a:'hsz'},sheep:{n:'Sheep',e:'🐑',col:0xf2f2f2,c2:0x555555,a:'sz'},frog:{n:'Frog',e:'🐸',col:0x4caf50,c2:0x2e7d32,a:'hsz'},elephant:{n:'Elephant',e:'🐘',col:0x9aa0a6,c2:0x8a9096,a:'sz'},dino:{n:'Dino',e:'🦕',col:0x3fa07a,c2:0x2f7d5e,a:'hsz'},mammoth:{n:'Mammoth',e:'🦣',col:0x6b4a2b,c2:0x8a5a3a,a:'sz'}};
const PT={dog:0,pig:0,chicken:0,rabbit:0,cat:1,turtle:1,bee:2,fox:2,wolf:2,penguin:2,panda:3,polar:3,dragon:4,unicorn:4,cow:0,duck:0,sheep:1,frog:1,elephant:3,dino:3,mammoth:4};const PER={sell:.04,grow:.03,mut:.02,kg:.02,hsz:.04},AN={sell:'sell price',grow:'growth speed',mut:'mutation chance',kg:'fruit weight',sz:'crop size & weight',hsz:'hatched pet size',all:'everything (half)'};
const EGGS={common:{n:'Common Egg',e:'🥚',cost:100,pool:[['dog',30],['chicken',22],['pig',12],['rabbit',12],['cow',12],['duck',12]],kg:[.5,2]},rare:{n:'Rare Egg',e:'🪺',cost:600,pool:[['cat',25],['bee',22],['fox',15],['turtle',10],['sheep',14],['frog',14]],kg:[1,4]},frost:{n:'Frost Egg',e:'🥚',cost:1800,pool:[['penguin',50],['wolf',30],['polar',20]],kg:[1,5]},legend:{n:'Legendary Egg',e:'🥚',cost:3000,pool:[['panda',50],['dragon',20],['elephant',15],['dino',15]],kg:[2,8]},mythic:{n:'Mythic Egg',e:'🥚',cost:9000,pool:[['unicorn',55],['dragon',30],['mammoth',15]],kg:[3,10]}};
const EVN={rain:'🌧️ Rain Shower: Wet mutations!',thunder:'⛈️ Thunderstorm: Shocked mutations!',lunar:'🌕 Lunar Event: Moonlit mutations!',blood:'🩸 Blood Moon: Bloodlit mutations!',winter:'❄️ Winter: Chilled & Frozen mutations!'};
let S={m:60,seeds:{carrot:2},fruit:[],pets:[],eq:[],can:0,spr:0,chm:0,sel:'carrot',alex:0};
try{const s=JSON.parse(localStorage.getItem('gag_blocky'));if(s&&s.seeds)S=s}catch(e){}
S.inv=S.inv||{planks:12,dirt:12,stone:8,log:3,sand:4};S.blk=S.blk||[];S.bag=S.bag||[];S.fc=S.fc||{};S.rod=S.rod||0;S.bsel=S.bsel||'planks';S.ye=S.ye||0;S.hs=S.hs||0;S.hb=S.hb||(()=>{const f=S.sel||'carrot',o=['carrot','strawberry','tomato','corn'].filter(k=>k!==f).slice(0,2);return['c:'+f,...o.map(k=>'c:'+k),'b:planks','b:stone','x:break']})();S.disc=S.disc||{};S.pets.forEach(p=>S.disc['p_'+p.id]=1);const SAVED={plots:S.plots,ts:S.ts,px:S.px,pz:S.pz,gt:S.gt};delete S.plots;
const SLOTS=[[-30,0],[0,0],[30,0],[-30,30],[0,30],[30,30]];
const oldO=S.bs&&S.bs.length===6?SLOTS[S.bs.indexOf(-1)]:null;
S.bs=[-1,0,1,2,3,4];for(let i=5;i>0;i--){const j=Math.random()*(i+1)|0;[S.bs[i],S.bs[j]]=[S.bs[j],S.bs[i]]}
if(!S.yv){S.yv=1;const nb=[];(S.blk||[]).forEach(b=>{const lx=oldO?b[0]-oldO[0]+8:-1,lz=oldO?b[2]-oldO[1]+10:-1;if(lx>=0&&lx<10&&lz>=0&&lz<10&&b[1]<12)nb.push([lx,b[1],lz,b[3]]);else S.inv[b[3]]=(S.inv[b[3]]||0)+1});S.blk=nb}
const OX=SLOTS[S.bs.indexOf(-1)][0],OZ=SLOTS[S.bs.indexOf(-1)][1],MOVED=!oldO||oldO[0]!==OX||oldO[1]!==OZ;
const mobile=matchMedia('(pointer:coarse)').matches;
// ---------- three setup
const scene=new THREE.Scene(),cam=new THREE.PerspectiveCamera(60,innerWidth/innerHeight,.1,400);
const rd=new THREE.WebGLRenderer({antialias:false});rd.setPixelRatio(Math.min(devicePixelRatio,2));rd.setSize(innerWidth,innerHeight);document.body.prepend(rd.domElement);
const amb=new THREE.AmbientLight(0xffffff,.7),sunL=new THREE.DirectionalLight(0xffffff,.8);scene.add(amb,sunL);
const NT=(()=>{const c=document.createElement('canvas');c.width=c.height=8;const x=c.getContext('2d');for(let i=0;i<8;i++)for(let j=0;j<8;j++){const v=185+Math.random()*70|0;x.fillStyle=`rgb(${v},${v},${v})`;x.fillRect(i,j,1,1)}const t=new THREE.CanvasTexture(c);t.magFilter=t.minFilter=THREE.NearestFilter;return t})();
function box(w,h,d,c,x,y,z,p){const m=new THREE.Mesh(new THREE.BoxGeometry(w,h,d),new THREE.MeshLambertMaterial({color:c,map:NT}));m.position.set(x,y,z);p&&p.add(m);return m}
// ground
const cv=document.createElement('canvas');cv.width=cv.height=16;const cx=cv.getContext('2d');
for(let i=0;i<16;i++)for(let j=0;j<16;j++){cx.fillStyle=`hsl(100,${45+Math.random()*10}%,${32+Math.random()*10}%)`;cx.fillRect(i,j,1,1)}
const tx=new THREE.CanvasTexture(cv);tx.magFilter=THREE.NearestFilter;tx.wrapS=tx.wrapT=THREE.RepeatWrapping;tx.repeat.set(120,120);
const gr=new THREE.Mesh(new THREE.PlaneGeometry(240,240),new THREE.MeshLambertMaterial({map:tx}));gr.rotation.x=-Math.PI/2;scene.add(gr);
for(let i=0;i<22;i++){const a=i/22*6.28,r=R(78,105),x=Math.cos(a)*r,z=Math.sin(a)*r;if(x>36&&z>24&&x<85&&z<75)continue;const t=new THREE.Group();box(.8,3,.8,0x6b4a2b,0,1.5,0,t);box(3,2,3,0x2f8f2f,0,3.7,0,t);box(2,1,2,0x3aa83a,0,5,0,t);t.position.set(x,0,z);scene.add(t)}
for(let i=0;i<60;i++){const f=box(.2,.3,.2,[0xff5577,0xffee44,0xffffff][i%3],R(-60,60),.15,R(-45,70));scene.add(f)}
// sun, moon, clouds
const sun=box(10,10,2,0xffee66,0,0,0),moon=box(6,6,2,0xe8ecff,0,0,0);sun.material.fog=false;scene.add(sun,moon);
const clouds=[];for(let i=0;i<9;i++){const g=new THREE.Group(),m=new THREE.MeshLambertMaterial({color:0xffffff});for(let k=0;k<5;k++){const b=new THREE.Mesh(new THREE.BoxGeometry(R(6,10),2.5,R(5,8)),m);b.position.set(k*4-8,R(-.5,.5),R(-2,2));g.add(b)}g.position.set(R(-80,80),R(38,50),R(-80,80));g.userData.m=m;scene.add(g);clouds.push(g)}
// rain
const rg=new THREE.BufferGeometry(),rp=new Float32Array(900);for(let i=0;i<300;i++){rp[i*3]=R(-25,25);rp[i*3+1]=R(0,25);rp[i*3+2]=R(-25,25)}rg.setAttribute('position',new THREE.BufferAttribute(rp,3));
const rain=new THREE.Points(rg,new THREE.PointsMaterial({color:0x9ec8ff,size:.35}));rain.visible=false;rain.frustumCulled=false;scene.add(rain);
const sg=new THREE.BufferGeometry(),sa=new Float32Array(1200);for(let i=0;i<400;i++){sa[i*3]=R(-25,25);sa[i*3+1]=R(0,25);sa[i*3+2]=R(-25,25)}sg.setAttribute('position',new THREE.BufferAttribute(sa,3));
const snow=new THREE.Points(sg,new THREE.PointsMaterial({color:0xffffff,size:.3}));snow.visible=false;snow.frustumCulled=false;scene.add(snow);let snowF=0;
const snowP=new THREE.Mesh(new THREE.PlaneGeometry(120,120),new THREE.MeshLambertMaterial({color:0xffffff,transparent:true,opacity:0}));snowP.rotation.x=-Math.PI/2;snowP.position.y=.03;snowP.visible=false;scene.add(snowP);
const bolt=box(.5,40,.5,0xffffaa,0,20,0);bolt.material.fog=false;bolt.visible=false;scene.add(bolt);
// ---------- physics / collision
const COL=[],BM=new Map(),PR=.3,PH=1.8,STEP=1.05;
const solid=(cx,cz,w,d,y0,y1)=>COL.push({a:cx-w/2,b:cx+w/2,c:cz-d/2,d:cz+d/2,y0,y1});
const pad=(bx,bz)=>{solid(bx,SZ+bz,SW,SD,0,.2);[-1,1].forEach(s=>{solid(bx,SZ+bz+s*(SD/2+.15),SW+.6,.3,0,.3);solid(bx+s*(SW/2+.15),SZ+bz,.3,SD,0,.3)})};
function hit(x,y,z){if(BR.on)return brHit(x,y,z);for(const c of COL)if(x+PR>c.a&&x-PR<c.b&&z+PR>c.c&&z-PR<c.d&&y+PH>c.y0&&y<c.y1-.001)return 1;
for(let i=Math.floor(x-PR);i<=Math.floor(x+PR);i++)for(let k=Math.floor(z-PR);k<=Math.floor(z+PR);k++){if(!(x+PR>i&&x-PR<i+1&&z+PR>k&&z-PR<k+1))continue;for(let j=Math.floor(y);j<=Math.floor(y+PH);j++)if(BM.has(i+','+j+','+k)&&y+PH>j&&y<j+1-.001)return 1}return 0}
function tops(x,z,lo,hi){if(BR.on)return brTops(x,z,lo,hi);const r=[];for(const c of COL)if(x+PR>c.a&&x-PR<c.b&&z+PR>c.c&&z-PR<c.d&&c.y1>lo&&c.y1<=hi)r.push(c.y1);
for(let i=Math.floor(x-PR);i<=Math.floor(x+PR);i++)for(let k=Math.floor(z-PR);k<=Math.floor(z+PR);k++){if(!(x+PR>i&&x-PR<i+1&&z+PR>k&&z-PR<k+1))continue;for(let j=Math.max(0,Math.floor(lo));j<=Math.floor(hi);j++)if(BM.has(i+','+j+','+k)&&j+1>lo&&j+1<=hi)r.push(j+1)}return r.sort((a,b)=>a-b)}
const supportY=(x,z,y)=>Math.max(0,...tops(x,z,-1,y+.02));
function tryMove(dx,dz){const nx=pl.x+dx,nz=pl.z+dz;if(!hit(nx,pl.y,nz)){pl.x=nx;pl.z=nz;return}
if(pl.g)for(const t of tops(nx,nz,pl.y+.001,pl.y+STEP))if(!hit(nx,t,nz)){pl.x=nx;pl.z=nz;pl.y=t;return}}
function slide(dx,dz){const n=Math.max(1,Math.ceil(Math.hypot(dx,dz)/.2));for(let i=0;i<n;i++){tryMove(dx/n,0);tryMove(0,dz/n)}if(!BR.on){pl.x=cl(pl.x,-58,80);pl.z=cl(pl.z,-30,70)}}
let jh=0;function phys(dt){if((jh||keys.Space)&&pl.g){pl.vy=9.3;pl.g=0;sfx('jump')}
const oy=pl.y;pl.vy=Math.max(pl.vy-32*dt,BR.drop?-8:-40);let ny=oy+pl.vy*dt;
if(pl.vy<=0){const s=supportY(pl.x,pl.z,oy);if(ny<=s){ny=s;pl.vy=0;pl.g=1}else pl.g=0}else{pl.g=0;if(hit(pl.x,ny,pl.z)){ny=oy;pl.vy=0}}
pl.y=ny;if(pl.g)pl.sy+=(pl.y-pl.sy)*Math.min(1,dt*18);else pl.sy=pl.y}
// plots
const plots=[],SX=2.2,SW=SX*6,SD=SX*4,SZ=-4;
const dc=document.createElement('canvas');dc.width=dc.height=16;{const x=dc.getContext('2d');for(let i=0;i<16;i++)for(let j=0;j<16;j++){const v=Math.random();x.fillStyle=`rgb(${95+v*30|0},${62+v*20|0},${35+v*14|0})`;x.fillRect(i,j,1,1)}}
const dtx=new THREE.CanvasTexture(dc);dtx.magFilter=dtx.minFilter=THREE.NearestFilter;dtx.wrapS=dtx.wrapT=THREE.RepeatWrapping;dtx.repeat.set(SW/1.1,SD/1.1);
const soil=new THREE.Mesh(new THREE.BoxGeometry(SW,.2,SD),new THREE.MeshLambertMaterial({map:dtx}));soil.position.set(OX,.1,SZ+OZ);soil.userData.soil=1;scene.add(soil);
[-1,1].forEach(s=>{box(SW+.6,.3,.3,0x6b4a2b,OX,.15,SZ+OZ+s*(SD/2+.15),scene);box(.3,.3,SD,0x6b4a2b,OX+s*(SW/2+.15),.15,SZ+OZ,scene)});pad(OX,OZ);
for(let j=0;j<4;j++)for(let i=0;i<6;i++)plots.push({x:(i-2.5)*SX+OX,z:(j-1.5)*SX+SZ+OZ,p:null});
// player
let me,walk=0;const pl={x:OX,y:0,z:8+OZ,ry:0,g:1,vy:0,sy:0};
function mkPlayer(){const al=S.alex,sk=0xc99872,hair=al?0xd9822b:0x3b2a1a,sh=al?0x62a83a:0x00a9a9,pn=al?0x6b4a2b:0x3a3a9c,g=new THREE.Group();
const hd=new THREE.Group();hd.position.y=1.3;g.add(hd);box(.5,.5,.5,sk,0,.25,0,hd);box(.52,.14,.52,hair,0,.5,0,hd);box(.52,.4,.08,hair,0,.3,-.24,hd);box(.08,.2,.5,hair,-.24,.38,0,hd);box(.08,.2,.5,hair,.24,.38,0,hd);box(.14,.08,.02,0xffffff,-.12,.27,.26,hd);box(.14,.08,.02,0xffffff,.12,.27,.26,hd);box(.07,.08,.03,0x3b2fa0,-.09,.27,.265,hd);box(.07,.08,.03,0x3b2fa0,.09,.27,.265,hd);box(.16,.06,.02,0x7a4a30,0,.12,.26,hd);
box(.5,.7,.25,sh,0,.95,0,g);const L=[];
[[-.125,.6,pn],[.125,.6,pn]].forEach(a=>{const l=new THREE.Group();l.position.set(a[0],a[1],0);box(.25,.6,.25,a[2],0,-.3,0,l);g.add(l);L.push(l)});
[[-.375],[.375]].forEach(a=>{const l=new THREE.Group();l.position.set(a[0],1.3,0);box(.25,.6,.25,sk,0,-.3,0,l);box(.26,.3,.26,sh,0,-.1,0,l);g.add(l);L.push(l)});
g.userData.L=L;return g}
function skin(){S.alex^=1;scene.remove(me);me=mkPlayer();scene.add(me);hk='';hm=null;updHold()}
me=mkPlayer();scene.add(me);
// pets
const GB={x0:OX-7.6,x1:OX+7.6,z0:OZ-10,z1:OZ+2};let petMs=[];
function mkPet(id,kg){const P=PETS[id],g=new THREE.Group(),c2=P.c2||P.col;g.userData={legs:[],wings:[]};box(.5,.4,.8,P.col,0,.5,0,g);const hd=new THREE.Group();hd.position.set(0,.75,.5);g.add(hd);g.userData.hd=hd;box(.4,.4,.4,c2,0,0,0,hd);box(.08,.08,.02,0x111111,-.1,.05,.21,hd);box(.08,.08,.02,0x111111,.1,.05,.21,hd);box(.1,.12,.1,c2,-.15,.25,0,hd);box(.1,.12,.1,c2,.15,.25,0,hd);const tl=new THREE.Group();tl.position.set(0,.6,-.4);g.add(tl);g.userData.tl=tl;box(.1,.1,.35,c2,0,0,-.17,tl);
[[-.15,-.28],[.15,-.28],[-.15,.28],[.15,.28]].forEach(a=>{const lg=new THREE.Group();lg.position.set(a[0],.3,a[1]);box(.14,.3,.14,c2,0,-.15,0,lg);g.add(lg);g.userData.legs.push(lg)});
const W=(c,w,d)=>[-1,1].forEach(s=>{const wg=new THREE.Group();wg.position.set(s*.25,.8,-.05);box(w,.05,d,c,s*w/2,0,0,wg);wg.userData.s=s;g.add(wg);g.userData.wings.push(wg)});if(id==='dragon')W(0x2a7a40,.8,.5);if(id==='bee')W(0xcceeff,.5,.3);if(id==='unicorn'){W(0xffc9f2,.7,.45);box(.08,.3,.08,0xffe066,0,.35,.05,hd)}if(id==='rabbit'){box(.08,.45,.08,0xffffff,-.1,.5,0,hd);box(.08,.45,.08,0xffffff,.1,.5,0,hd)}if(id==='penguin')box(.12,.08,.12,0xff9d1f,0,-.05,.25,hd);if(id==='polar')box(.1,.08,.04,0x111111,0,-.02,.21,hd);if(id==='turtle')box(.6,.25,.7,0x2f6f2f,0,.8,0,g);if(id==='cow'){box(.08,.12,.08,0xeeeeee,-.2,.28,0,hd);box(.08,.12,.08,0xeeeeee,.2,.28,0,hd);box(.3,.1,.3,0x222222,.1,.72,0,g)}if(id==='sheep')box(.62,.5,.9,0xf2f2f2,0,.58,0,g);if(id==='duck')box(.2,.08,.15,0xf5801a,0,-.05,.25,hd);if(id==='elephant'||id==='mammoth'){box(.14,.4,.14,c2,0,-.2,.28,hd);box(.05,.3,.3,c2,-.24,.05,0,hd);box(.05,.3,.3,c2,.24,.05,0,hd);if(id==='mammoth'){box(.06,.06,.3,0xf5f0dc,-.15,-.15,.3,hd);box(.06,.06,.3,0xf5f0dc,.15,-.15,.3,hd)}}if(id==='dino')box(.1,.15,.5,0x2a6a50,0,.78,0,g);if(id==='frog'){box(.1,.1,.1,0xffffff,-.12,.2,.1,hd);box(.1,.1,.1,0xffffff,.12,.2,.1,hd)}
g.scale.setScalar(.4+.2*kg);g.userData.s0=.4+.2*kg;return g}
function rebuildPets(){petMs.forEach(m=>scene.remove(m));petMs=S.eq.map(i=>S.pets[i]).filter(Boolean).map((p,k)=>{const m=mkPet(p.id,p.kg);m.userData.k=k;m.position.set(R(GB.x0,GB.x1),0,R(GB.z0,GB.z1));m.userData.tx=m.position.x;m.userData.tz=m.position.z;m.userData.w=R(.5,3);scene.add(m);return m})}
rebuildPets();
// ---------- garden fence, market, NPCs, teleport, save
const FX=8.2,FZ0=-10.6,FZ1=2.6,WD=0x8b5a2b;
function fenceAt(ox,oz){const A=(x,z,w,d)=>{solid(x+ox,z+oz,Math.max(w,.45),Math.max(d,.45),0,1.6);box(w,.12,d,WD,x+ox,.45,z+oz,scene);box(w,.12,d,WD,x+ox,.8,z+oz,scene)},Q=(x,z)=>box(.25,1,.25,0x6b4423,x+ox,.5,z+oz,scene);
A(0,FZ0,FX*2,.12);A(-FX,(FZ0+FZ1)/2,.12,FZ1-FZ0);A(FX,(FZ0+FZ1)/2,.12,FZ1-FZ0);A((-FX-1.5)/2,FZ1,FX-1.5,.12);A((FX+1.5)/2,FZ1,FX-1.5,.12);
for(let x=-FX;x<=FX+.1;x+=FX/4){Q(x,FZ0);if(Math.abs(x)>1.6)Q(x,FZ1)}
for(let z=FZ0+2.6;z<FZ1;z+=2.6)[-FX,FX].forEach(x=>Q(x,z));
[-1.5,1.5].forEach(x=>{solid(x+ox,FZ1+oz,.4,.4,0,1.6);box(.3,1.5,.3,0x6b4423,x+ox,.75,FZ1+oz,scene)})}
fenceAt(OX,OZ);
function mkText(t,bg,w,h,sx,sy){const c=document.createElement('canvas');c.width=w;c.height=h;const x=c.getContext('2d');x.fillStyle=bg;x.fillRect(0,0,w,h);x.strokeStyle='#000';x.lineWidth=6;x.strokeRect(0,0,w,h);x.fillStyle='#fff';x.font='bold '+(h*.5|0)+'px "Courier New",monospace';x.textAlign='center';x.textBaseline='middle';x.fillText(t,w/2,h/2+2);const s=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(c)}));s.scale.set(sx,sy,1);s.raycast=()=>{};return s}
box(44,.06,9,0xa89f8a,0,.03,-18.5,scene);
const npcs=[];
function mkNPC(sk,hair,sh,pn,hat){const g=new THREE.Group(),hd=new THREE.Group();hd.position.y=1.3;g.add(hd);box(.5,.5,.5,sk,0,.25,0,hd);box(.52,.14,.52,hair,0,.5,0,hd);box(.52,.4,.08,hair,0,.3,-.24,hd);box(.1,.08,.02,0x111111,-.12,.27,.26,hd);box(.1,.08,.02,0x111111,.12,.27,.26,hd);box(.16,.05,.02,0x7a4a30,0,.12,.26,hd);hat(hd);box(.5,.7,.25,sh,0,.95,0,g);g.userData.L=[-.125,.125].map(x=>{const l=new THREE.Group();l.position.set(x,.6,0);box(.25,.6,.25,pn,0,-.3,0,l);g.add(l);return l});
g.userData.A=[-.375,.375].map(x=>{const a=new THREE.Group();a.position.set(x,1.3,0);box(.25,.6,.25,sk,0,-.3,0,a);box(.26,.3,.26,sh,0,-.1,0,a);g.add(a);return a});g.userData.hd=hd;return g}
function stall(x,key,sign,col,name,npc){solid(x,-18,3.9,1.3,0,1.6);solid(x,-19.7,3.6,.4,0,3);const g=new THREE.Group();g.position.set(x,0,-18);
box(3.6,1,1,WD,0,.5,0,g);box(3.9,.12,1.3,0xd9b26f,0,1.06,0,g);box(3.6,3,.2,0xc9a46a,0,1.5,-1.7,g);[-1.8,1.8].forEach(s=>box(.2,3.1,.2,0x6b4423,s,1.55,.7,g));box(4.1,.2,3,col,0,3.15,-.5,g);box(4.1,.3,.1,0xffffff,0,2.9,1,g);
npc.position.set(0,0,-1);g.add(npc);const a=mkText(sign,'#'+col.toString(16).padStart(6,'0'),384,96,5,1.25);a.position.set(0,4.3,-.5);g.add(a);const b=mkText(name,'#000a',256,64,2.4,.6);b.position.set(0,2.45,-1);g.add(b);
g.traverse(o=>o.userData.shop=key);npc.userData.wx=x;npc.userData.wz=-19;npcs.push(npc);scene.add(g)}
stall(-12,'seeds','🌱 SEED SHOP',0x3fa63f,'🌱 Sprout',mkNPC(0xc99872,0x5a3a1a,0x62a83a,0x6b4a2b,h=>{box(.8,.06,.8,0xe8c15a,0,.56,0,h);box(.5,.16,.5,0xe8c15a,0,.65,0,h)}));
stall(0,'eggs','🥚 EGG SHOP',0xc45be0,'🥚 Eggbert',mkNPC(0xf0c8a0,0x222222,0x3a8fe8,0x333366,h=>box(.5,.3,.5,0xffffff,0,.68,0,h)));
stall(12,'gear','⚙️ GEAR SHOP',0x3a8fe8,'⚙️ Gizmo',mkNPC(0x8d5a3a,0x111111,0xe8751a,0x444444,h=>{box(.56,.2,.56,0xffcc00,0,.6,0,h);box(.6,.04,.7,0xffcc00,0,.52,.05,h)}));
const SPOTS={garden:[OX,OZ+5,'🏡 My Garden'],seeds:[-12,-14,'🌱 Seed Shop'],eggs:[0,-14,'🥚 Egg Shop'],gear:[12,-14,'⚙️ Gear Shop']};
function tp(k){const s=SPOTS[k];puff(pl.x,pl.z,0xb8c4ff);pl.x=s[0];pl.z=s[1];pl.y=supportY(s[0],s[1],2);pl.vy=0;pl.sy=pl.y;yaw=0;puff(pl.x,pl.z,0xb8c4ff);sfx('hatch');closeP();toast('✨ '+s[2]+(k==='garden'?'':' · tap the NPC to shop'));save()}
const PV=[70,300,700,1500,3500],pv=p=>Math.round(PV[PT[p.id]]*(.5+.08*p.kg));let sc=-1;
function sellPet(i){const p=S.pets[i];if(!p)return;if(sc!==i){sc=i;rp_();return}sc=-1;S.m+=pv(p);S.pets.splice(i,1);S.hb=S.hb.map(x=>x&&x[0]==='p'?'':x);S.eq=S.eq.filter(x=>x!==i).map(x=>x>i?x-1:x);sfx('sell');rebuildPets();save();rp_()}
// ---------- NPC bases & trading
const NP=[
{n:'Daisy',e:'🌼',tier:0,m:180,sk:0xf0c8a0,hr:0xd9822b,sh:0xff7aa8,pn:0x555599,hat:h=>box(.6,.1,.6,0xffe066,0,.56,0,h)},
{n:'Rex',e:'🤠',tier:1,m:1200,sk:0xc99872,hr:0x222222,sh:0xc0392b,pn:0x3a3a3a,hat:h=>{box(.8,.06,.8,0x8b5a2b,0,.56,0,h);box(.5,.16,.5,0x8b5a2b,0,.65,0,h)}},
{n:'Maple',e:'🍁',tier:2,m:6000,sk:0x8d5a3a,hr:0x5a3a1a,sh:0xe8751a,pn:0x2a5a8a,hat:h=>box(.54,.2,.54,0x2f8f2f,0,.6,0,h)},
{n:'Orion',e:'🧙',tier:3,m:40000,sk:0xf0c8a0,hr:0xdddddd,sh:0x6a3aa8,pn:0x222244,hat:h=>{box(.6,.08,.6,0x3a2a6a,0,.56,0,h);box(.36,.4,.36,0x3a2a6a,0,.78,0,h)}},
{n:'Luna',e:'🌙',tier:4,m:200000,sk:0xe8c8b0,hr:0x1a1a3a,sh:0x1e2a5a,pn:0x111111,hat:h=>{box(.56,.12,.56,0xffd24a,0,.6,0,h);box(.12,.2,.12,0xffd24a,0,.74,0,h)}}];
const ET=[['common'],['common','rare'],['rare','frost'],['frost','legend'],['legend','mythic']];
const allowed=t=>Object.keys(CROPS).filter(k=>CT[k]<=t),pick=a=>a[Math.random()*a.length|0];
function rollEgg(eid){const E=EGGS[eid];let r=Math.random()*100,pid=E.pool[0][0];for(const p of E.pool){if(r<p[1]){pid=p[0];break}r-=p[1]}return{id:pid,kg:+(R(...E.kg)*(Math.random()<.1?1.6:1)).toFixed(2)}}
function newCrop(k,pr){const r=Math.random();return{type:k,kg:R(...CROPS[k].kg),prog:pr===undefined?Math.random():pr,b:r<.01?'rainbow':r<.05?'gold':'normal',mut:Math.random()<.2?[pick(['wet','chilled','moon'])]:[]}}
function genNPC(i){const P=NP[i],al=allowed(P.tier),n={m:P.m,up:0,seeds:{},pets:[],pl:[]};for(let j=0;j<24;j++)n.pl.push(Math.random()<.75?newCrop(pick(al)):null);
for(let j=0;j<4;j++){const k=pick(al);n.seeds[k]=(n.seeds[k]||0)+1+(Math.random()*3|0)}
for(let j=0;j<2+P.tier;j++)n.pets.push(rollEgg(pick(ET[P.tier])));return n}
S.npc=S.npc||[];let fresh=0;for(let i=0;i<5;i++)if(!S.npc[i]){S.npc[i]=genNPC(i);fresh=1}
const cropVal=c=>Math.round(CROPS[c.type].p*c.kg*BASE[c.b].m*c.mut.reduce((a,k)=>a+MUT[k].m-1,1));
function nGrow(i,dt){const t=NP[i].tier;S.npc[i].pl.forEach(c=>{if(c)c.prog+=dt*(1+t*.1+(S.npc[i].up||0)*.12)/CROPS[c.type].t})}
function nEco(i,dt,live){const n=S.npc[i],P=NP[i],al=allowed(P.tier);let ch=0;
if(!live)n.pl.forEach((c,j)=>{if(c){if(c.prog>=1.2){n.m+=cropVal(c);n.pl[j]=null}}
else{let k=Object.keys(n.seeds).filter(k=>n.seeds[k]>0).sort((a,b)=>CROPS[b].cost-CROPS[a].cost)[0];
if(k)n.seeds[k]--;else{k=pick(al);if(n.m>=CROPS[k].cost)n.m-=CROPS[k].cost;else k=null}
if(k)n.pl[j]=newCrop(k,0)}});
{const uc=Math.round(150*(P.tier+1)*Math.pow(1.7,n.up||0));if((n.up||0)<12&&n.m>=uc*2){n.m-=uc;n.up=(n.up||0)+1;ch=1;if(live)puff(NB[i].g.position.x,NB[i].g.position.z,0x4aa3ff)}}
if(Math.random()<dt*.02){const k=pick(al);n.seeds[k]=(n.seeds[k]||0)+1}
if(n.pets.length<6&&Math.random()<dt*.003){const e=pick(ET[P.tier]);if(n.m>=EGGS[e].cost*2){n.m-=EGGS[e].cost;n.pets.push(rollEgg(e));ch=1}}return ch}
const NB=[],NV=[],NPM=[];let nt=0;
function rebuildNPets(i){(NPM[i]||[]).forEach(m=>scene.remove(m));const b=NB[i];NPM[i]=S.npc[i].pets.slice(0,6).map((p,k)=>{const m=mkPet(p.id,p.kg),U=m.userData;U.k=k;m.position.set(b.bx+R(-7.4,7.4),0,b.bz+R(-9.5,1.8));U.tx=m.position.x;U.tz=m.position.z;U.w=R(.5,3);scene.add(m);return m})}
function syncN(i){const n=S.npc[i],b=NB[i];n.pl.forEach((c,j)=>{let v=NV[i][j];if(v&&v.d!==c){scene.remove(v.m);v=NV[i][j]=null}
if(c&&!v){const m=mkPlant(c.type,c.kg);m.position.set(b.bx+(j%6-2.5)*SX,.2,b.bz+SZ+((j/6|0)-1.5)*SX);scene.add(m);tint({m,mut:c.mut,b:c.b});NV[i][j]={d:c,m}}})}
for(let i=0;i<5;i++){const P=NP[i],[bx,bz]=SLOTS[S.bs.indexOf(i)];fenceAt(bx,bz);
const sl=new THREE.Mesh(new THREE.BoxGeometry(SW,.2,SD),new THREE.MeshLambertMaterial({map:dtx}));sl.position.set(bx,.1,SZ+bz);scene.add(sl);pad(bx,bz);
[-1,1].forEach(s=>{box(SW+.6,.3,.3,0x6b4a2b,bx,.15,SZ+bz+s*(SD/2+.15),scene);box(.3,.3,SD,0x6b4a2b,bx+s*(SW/2+.15),.15,SZ+bz,scene)});
const g=mkNPC(P.sk,P.hr,P.sh,P.pn,P.hat);g.position.set(bx,0,bz+1);const tag=mkText(P.e+' '+P.n,'#000a',256,64,2.6,.65);tag.position.set(0,2.6,0);g.add(tag);
Object.assign(g.userData,{tx:bx,tz:bz+1,w:1,i,job:-1});g.traverse(o=>o.userData.shop='npc'+i);scene.add(g);NB[i]={g,bx,bz};NV[i]=[];
SPOTS['npc'+i]=[bx,bz+5,P.e+' '+P.n+"'s Base"]}
if(!fresh&&SAVED.ts){const el=cl((Date.now()-SAVED.ts)/1000,0,7200);for(let i=0;i<5;i++)for(let t=0;t<Math.min(360,el/20);t++){nGrow(i,20);nEco(i,20)}}
for(let i=0;i<5;i++){rebuildNPets(i);syncN(i)}
function npcAgent(i,dt){const n=S.npc[i],B=NB[i],g=B.g,U=g.userData,al=allowed(NP[i].tier);let mvg=0,face=null;
if(U.w>0){U.w-=dt;if(U.act){face=Math.PI;if(U.w<=0){const j=U.job,c=n.pl[j];
if(U.act==='h'&&c&&c.prog>=1){n.m+=cropVal(c);n.pl[j]=null;puff(g.position.x,g.position.z-.6,0xffd700)}
else if(U.act==='p'&&!c){let k=Object.keys(n.seeds).filter(k=>n.seeds[k]>0).sort((a,b)=>CROPS[b].cost-CROPS[a].cost)[0];if(k)n.seeds[k]--;else{k=pick(al);if(n.m>=CROPS[k].cost)n.m-=CROPS[k].cost;else k=null}if(k){n.pl[j]=newCrop(k,0);puff(g.position.x,g.position.z-.6,0x6b4423)}}
U.act=0;U.job=-1;syncN(i)}}}
else{if(U.job<0&&U.job!==-2){let best=-1,bd=1e9;const cheap=Math.min(...al.map(k=>CROPS[k].cost)),can=Object.values(n.seeds).some(v=>v>0)||n.m>=cheap;
for(let j=0;j<24;j++){const c=n.pl[j];if(c?c.prog>=1:can){const d=Math.hypot(B.bx+(j%6-2.5)*SX-g.position.x,B.bz+SZ+((j/6|0)-1.5)*SX+1-g.position.z)+(c?0:Math.random()*2);if(d<bd){bd=d;best=j}}}
if(best>=0){U.job=best;U.tx=B.bx+(best%6-2.5)*SX;U.tz=B.bz+SZ+((best/6|0)-1.5)*SX+1}else{U.job=-2;U.tx=B.bx+R(-7,7);U.tz=B.bz+R(-9,1.8)}}
const dx=U.tx-g.position.x,dz=U.tz-g.position.z,d=Math.hypot(dx,dz);
if(d<.25){if(U.job>=0){U.act=n.pl[U.job]?'h':'p';U.w=.7}else{U.job=-1;U.w=R(1,2.5)}}
else{const sp=Math.min(d,2.4*dt);g.position.x+=dx/d*sp;g.position.z+=dz/d*sp;mvg=1;face=Math.atan2(dx,dz)}}
if(face!==null)g.rotation.y+=(((face-g.rotation.y+Math.PI*3)%(Math.PI*2))-Math.PI)*Math.min(1,dt*8);
const sw=Math.sin(now*10)*.7*mvg;U.L[0].rotation.x=sw;U.L[1].rotation.x=-sw;U.A[0].rotation.x=U.act?-1+Math.sin(now*14)*.4:-sw;U.A[1].rotation.x=U.act?-1-Math.sin(now*14)*.4:sw;U.hd.rotation.x=U.act?.35:0}
function npcUpdate(dt){nt+=dt;const eco=nt>=3;if(eco)nt=0;
for(let i=0;i<5;i++){nGrow(i,dt);if(eco){if(nEco(i,3,1))rebuildNPets(i);syncN(i)}
NV[i].forEach(v=>{if(!v)return;const c=v.d;v.m.scale.setScalar(v.m.userData.base*(.15+.85*Math.min(1,c.prog)));if(c.b==='rainbow'){const q=v.m.userData.mat;q.color.setHSL((now*.4+i*.2)%1,.85,.55);q.emissive.copy(q.color).multiplyScalar(.3)}});
npcAgent(i,dt);const g=NB[i].g,U=g.userData;
const px=pl.x-g.position.x,pz=pl.z-g.position.z,pd=Math.hypot(px,pz);U.A[1].rotation.z=pd<7?2.7+Math.sin(now*9)*.35:U.A[1].rotation.z*(1-Math.min(1,dt*6));
(NPM[i]||[]).forEach((m,k)=>{const V=m.userData,B=NB[i];let mg=0;if(V.w>0)V.w-=dt;else{const dx=V.tx-m.position.x,dz=V.tz-m.position.z,d=Math.hypot(dx,dz);if(d<.25){V.w=R(1.5,5);V.tx=B.bx+R(-7.4,7.4);V.tz=B.bz+R(-9.5,1.8)}else{const s=Math.min(d,1.6*dt);m.position.x+=dx/d*s;m.position.z+=dz/d*s;mg=.7;m.rotation.y+=(((Math.atan2(dx,dz)-m.rotation.y+Math.PI*3)%(Math.PI*2))-Math.PI)*Math.min(1,dt*8)}}petAnim(m,k,mg,dt)})}}
let tr={g:null,t:null};
function tItem(key,me,i){const [ty,k]=key.split(':'),n=S.npc[i];if(ty==='s'){const c=(me?S.seeds:n.seeds)[k]||0;return c>0?{v:CROPS[k].cost,ic:I('c_'+k,()=>mkPlant(k,CROPS[k].kg[1]*.9),32),nm:CROPS[k].n+' seed ×'+c+' '+tb(CT[k]),d:CROPS[k].p+'🪙/kg'}:null}
const p=(me?S.pets:n.pets)[+k];return p?{v:pv(p),ic:I('p_'+p.id,()=>mkPet(p.id,1),32),nm:PETS[p.id].n+' '+tb(PT[p.id])+' '+p.kg.toFixed(2)+'kg',d:'+ '+AN[PETS[p.id].a]}:null}
function mvItem(key,me,i){const n=S.npc[i],[ty,k]=key.split(':');
if(ty==='s'){const A=me?S.seeds:n.seeds,B=me?n.seeds:S.seeds;A[k]--;B[k]=(B[k]||0)+1}
else{const x=+k;if(me){const p=S.pets[x];S.pets.splice(x,1);S.hb=S.hb.map(x=>x&&x[0]==='p'?'':x);S.eq=S.eq.filter(y=>y!==x).map(y=>y>x?y-1:y);n.pets.push(p)}else{const p=n.pets.splice(x,1)[0];S.pets.push(p);S.disc['p_'+p.id]=1}rebuildPets();rebuildNPets(i)}}
function npcTrade(i){const P=NP[i],n=S.npc[i],keys=me=>{const a=[];Object.keys(me?S.seeds:n.seeds).forEach(k=>a.push('s:'+k));(me?S.pets:n.pets).forEach((p,x)=>a.push('p:'+x));return a};
const row=(key,me)=>{const it=tItem(key,me,i);if(!it)return'';const sel=(me?tr.g:tr.t)===key;return`<div class="row"><span>${it.ic} ${it.nm}<br><small>${it.d} · worth ${fm(it.v)}🪙</small></span><span style="display:flex;flex-direction:column;gap:4px"><button onclick="tAct('${key}',${me?1:0},0)">${fm(me?'Sell '+fm(Math.round(it.v*.6)):'Buy '+fm(Math.round(it.v*1.25)))}🪙</button><button${sel?' style="background:#7bd34a"':''} onclick="tAct('${key}',${me?1:0},1)">${sel?'✔ ':''}Swap</button></span></div>`};
const tot=S.fruit.reduce((a,f)=>a+val(f),0),offer=Math.round(tot*1.1);
let h=`<small>Farmer lvl ${P.tier+1} · ⚙️ upgrades ${n.up||0}/12 · 🪙 ${fm(n.m)} · ${n.pl.filter(c=>c).length}/24 plots · ${n.pets.length} pets</small><br><b>${P.n} has</b>`+(keys(0).map(k=>row(k,0)).join('')||'<br><small>Nothing right now.</small>')+'<br><b>You have</b>'+(keys(1).map(k=>row(k,1)).join('')||'<br><small>No seeds or pets.</small>');
if(S.fruit.length)h+=`<div class="row"><span>🧺 All ${S.fruit.length} crops<br><small>${P.n} pays +10%</small></span><button onclick="tCrops()">${fm(offer)}🪙</button></div>`;
if(tr.g&&tr.t){const a=tItem(tr.g,1,i),b=tItem(tr.t,0,i);if(a&&b){const need=Math.round(b.v*1.1-a.v);h+=`<div class="row"><span><b>Swap</b> your item for theirs<br><small>${need>0?'You add '+fm(need)+'🪙':need<0?P.n+' adds '+fm(Math.round(-need*.8))+'🪙':'Even trade'}</small></span><button onclick="tSwap()">Trade</button></div>`}}
else h+='<small>Pick one of yours + one of theirs with Swap. Prices differ a bit from shops.</small>';
return[P.e+' '+P.n+"'s Base",h]}
function tAct(key,me,sw){const i=+cur.slice(3),n=S.npc[i],it=tItem(key,me,i);if(!it)return rp_();
if(sw){const f=me?'g':'t';tr[f]=tr[f]===key?null:key;return rp_()}
if(me){const pay=Math.round(it.v*.6);if(n.m<pay)return toast(NP[i].n+" can't afford that"),sfx('err');S.m+=pay;n.m-=pay}
else{const pr=Math.round(it.v*1.25);if(S.m<pr)return toast('Not enough coins'),sfx('err');S.m-=pr;n.m+=pr}
mvItem(key,!!me,i);tr={g:null,t:null};sfx('buy');save();rp_()}
function tSwap(){const i=+cur.slice(3),n=S.npc[i],a=tItem(tr.g,1,i),b=tItem(tr.t,0,i);if(!a||!b)return;const need=Math.round(b.v*1.1-a.v),pay=Math.round(-need*.8);
if(need>0&&S.m<need)return toast('Not enough coins'),sfx('err');if(need<0&&n.m<pay)return toast(NP[i].n+' is short on coins'),sfx('err');
const g=tr.g,t=tr.t;mvItem(g,true,i);mvItem(t,false,i);if(need>0){S.m-=need;n.m+=need}else{S.m+=pay;n.m-=pay}tr={g:null,t:null};sfx('hatch');toast('🤝 Trade done!');save();rp_()}
function tCrops(){const i=+cur.slice(3),n=S.npc[i],o=Math.round(S.fruit.reduce((a,f)=>a+val(f),0)*1.1);if(n.m<o)return toast(NP[i].n+" can't afford that"),sfx('err');S.m+=o;n.m-=o;S.fruit=[];sfx('sell');save();rp_()}

// ---------- blocks, crafting, pond & fishing
const BK={log:{n:'Log',c:0x6b4a2b,e:'🪵',p:6},stone:{n:'Stone',c:0x8d8d8d,e:'🪨',p:5},dirt:{n:'Dirt',c:0x8b5a2b,e:'🟫',p:2},sand:{n:'Sand',c:0xe6d9a0,e:'🏖️',p:4},planks:{n:'Planks',c:0xc9a064,e:'🟨'},brick:{n:'Brick',c:0xb0533a,e:'🧱'},glass:{n:'Glass',c:0xbfe9ff,e:'🔲'},lantern:{n:'Lantern',c:0xffd24a,e:'🏮'},gold:{n:'Gold Block',c:0xffd700,e:'🟡'},diamond:{n:'Diamond Block',c:0x4de6e0,e:'💠'},nugget:{n:'Gold Nugget',e:'🟠',ni:1},gem:{n:'Diamond',e:'💎',ni:1}};
const RC=[{o:'planks',q:4,i:{log:1}},{o:'brick',q:4,i:{stone:4}},{o:'glass',q:2,i:{sand:2}},{o:'lantern',q:1,i:{glass:1,nugget:1}},{o:'gold',q:1,i:{nugget:4}},{o:'diamond',q:1,i:{gem:3}}];
const YX0=44,YZ0=34,yardN=()=>10+4*S.ye;
const BTX={},BMT={},BG=new THREE.Group(),BGEO=new THREE.BoxGeometry(1,1,1);scene.add(BG);let bm=false;
function btex(k){if(BTX[k])return BTX[k];const c=document.createElement('canvas');c.width=c.height=16;const x=c.getContext('2d'),B=new THREE.Color(BK[k].c);
for(let i=0;i<16;i++)for(let j=0;j<16;j++){let v=.78+Math.random()*.22,f=0;if(k==='planks'&&j%4===3)v=.6;if(k==='brick'&&(j%4===3||(i+(j>>2)*4)%8===7))f=1;if(k==='log'&&(i<2||i>13))v*=.7;if(k==='glass'&&(i<1||j<1||i>14||j>14))v=1;if(k==='stone'&&Math.random()<.12)v=.6;
x.fillStyle=f?'#c9c2b8':'#'+B.clone().multiplyScalar(v).getHexString();x.fillRect(i,j,1,1)}
const t=new THREE.CanvasTexture(c);t.magFilter=t.minFilter=THREE.NearestFilter;return BTX[k]=t}
const bmat=k=>BMT[k]||(BMT[k]=new THREE.MeshLambertMaterial({map:btex(k),transparent:k==='glass',opacity:k==='glass'?.5:1,emissive:k==='lantern'?0xffa500:k==='diamond'?0x118888:k==='gold'?0x664400:0}));
const mkBlk=k=>{const g=new THREE.Group();g.add(new THREE.Mesh(BGEO,bmat(k)));return g};
function addBlk(x,y,z,k){const m=new THREE.Mesh(BGEO,bmat(k));m.position.set(x+.5,y+.5,z+.5);m.userData={bk:1,gx:x,gy:y,gz:z,k};BG.add(m);BM.set(x+','+y+','+z,m)}
syncSel();
S.blk.forEach(b=>BK[b[3]]&&!BK[b[3]].ni&&b[0]<yardN()&&b[2]<yardN()&&addBlk(YX0+b[0],b[1],YZ0+b[2],b[3]));
function canBuild(x,y,z){const n=yardN(),lx=x-YX0,lz=z-YZ0;if(BM.has(x+','+y+','+z))return'Already a block here';if(lx<0||lx>=n||lz<0||lz>=n||y<0||y>11)return'🧱 Build inside your Build Yard fence (expand it in 🔨)';
if(lx<=1&&Math.abs(lz+.5-n/2)<2)return'Keep the gate clear';if(Math.hypot(x+.5-pl.x,z+.5-pl.z)>18)return'Too far away';
if(pl.x+PR>x&&pl.x-PR<x+1&&pl.z+PR>z&&pl.z-PR<z+1&&pl.y+PH>y&&pl.y<y+1)return"You're standing there";return''}
const YF=new THREE.Group();scene.add(YF);let YC=[];SPOTS.yard=[YX0-3,YZ0+5,'🏗️ Build Yard'];
function buildYard(){while(YF.children.length)YF.remove(YF.children[0]);YC.forEach(o=>{const i=COL.indexOf(o);if(i>=0)COL.splice(i,1)});YC=[];
const n=yardN(),a=YX0-.3,b=YX0+n+.3,c=YZ0-.3,d=YZ0+n+.3,zc=YZ0+n/2;box(n,.04,n,0x7cc04f,YX0+n/2,.02,YZ0+n/2,YF);
const rail=(cx,cz,w,dd)=>{if(w<=0||dd<=0)return;box(w,.12,dd,WD,cx,.45,cz,YF);box(w,.12,dd,WD,cx,.8,cz,YF);const W=Math.max(w,.45)/2,D=Math.max(dd,.45)/2,o={a:cx-W,b:cx+W,c:cz-D,d:cz+D,y0:0,y1:1.6};COL.push(o);YC.push(o)};
rail((a+b)/2,c,b-a,.12);rail((a+b)/2,d,b-a,.12);rail(b,(c+d)/2,.12,d-c);rail(a,(c+zc-1.5)/2,.12,zc-1.5-c);rail(a,(zc+1.5+d)/2,.12,d-zc-1.5);
const post=(x,z,h)=>box(.25,h,.25,0x6b4423,x,h/2,z,YF),m=Math.round((n+.6)/2.5);
for(let i=0;i<=m;i++){const x=a+i*(b-a)/m,z=c+i*(d-c)/m;post(x,c,1);post(x,d,1);post(b,z,1);if(Math.abs(z-zc)>1.8)post(a,z,1)}
post(a,zc-1.5,1.6);post(a,zc+1.5,1.6);const sp=mkText('🏗️ BUILD YARD','#8a5a2b',384,96,5,1.2);sp.position.set(a,3.2,zc);YF.add(sp);SPOTS.yard[1]=zc;
if(typeof pl!=='undefined'&&hit(pl.x,pl.y,pl.z)){pl.x=YX0-3;pl.z=zc}}
buildYard();
const YCOST=[1500,15000,150000,2000000];
const yardH=()=>{const n=yardN();return `<div class="row"><span>🏗️ <b>Build Yard ${n}×${n}</b><br><small>${S.ye>=4?'Max size reached':'Next: '+(n+4)+'×'+(n+4)+' · 🧭 Teleport → Build Yard'}</small></span>${S.ye>=4?'<b>MAX</b>':`<button onclick="expandYard()">Expand ${fm(fm(YCOST[S.ye]))}🪙</button>`}</div>`};
function expandYard(){if(S.ye>=4)return;const c=YCOST[S.ye];if(S.m<c)return toast('Not enough coins'),sfx('err');S.m-=c;S.ye++;buildYard();sfx('hatch');toast('🏗️ Yard expanded to '+yardN()+'×'+yardN()+'!');save();rp_()}
{const yb=mkText('🏡 YOUR BASE','#2f7f2f',384,96,5,1.2);yb.position.set(OX,3.4,OZ+FZ1+.4);scene.add(yb)}
function putBlock(x,y,z){const t=S.bsel;if(!BK[t]||BK[t].ni)return;if(!(S.inv[t]>0))return toast('No '+BK[t].n+' · open 🔨 to craft or buy'),sfx('err');const w=canBuild(x,y,z);if(w)return toast(w),sfx('err');
S.inv[t]--;addBlk(x,y,z,t);S.blk.push([x-YX0,y,z-YZ0,t]);sfx('place');puff(x+.5,z+.5,BK[t].c);hot();save()}
function delBlock(x,y,z){const m=BM.get(x+','+y+','+z);if(!m)return;if(Math.hypot(x+.5-pl.x,z+.5-pl.z)>14)return toast('Too far away');const k=m.userData.k;BG.remove(m);BM.delete(x+','+y+','+z);S.blk=S.blk.filter(b=>!(b[0]===x-YX0&&b[1]===y&&b[2]===z-YZ0));S.inv[k]=(S.inv[k]||0)+1;sfx('brk');puff(x+.5,z+.5,BK[k].c);hot();save()}
function buildTap(){const h=rc.intersectObjects([...BG.children,gr],false)[0];if(!h)return;
if(S.bsel==='break'){const u=h.object.userData;if(!u.bk)return toast('Tap a block you placed to break it');return delBlock(u.gx,u.gy,u.gz)}
const n=h.face.normal.clone().transformDirection(h.object.matrixWorld),q=h.point.clone().addScaledVector(n,.01);putBlock(Math.floor(q.x),Math.floor(q.y),Math.floor(q.z))}
const jb=$('jump');jb.addEventListener('pointerdown',e=>{e.preventDefault();jh=1});['pointerup','pointercancel','pointerleave'].forEach(n=>jb.addEventListener(n,()=>jh=0));
const ic_=k=>BK[k].ni?`<span style="font-size:24px">${BK[k].e}</span>`:I('k_'+k,()=>mkBlk(k),28);
function craftP(){const inv='<b>Inventory</b><div class="grid">'+Object.keys(BK).map(k=>`<div class="frame">${ic_(k)}<br>${BK[k].n}<br>×${S.inv[k]||0}</div>`).join('')+'</div>';
const sup=Object.keys(BK).filter(k=>BK[k].p).map(k=>`<div class="row"><span>${ic_(k)} ${BK[k].n}</span><span><button onclick="bb('${k}',1)">+1 · ${fm(BK[k].p)}🪙</button> <button onclick="bb('${k}',10)">+10 · ${fm(BK[k].p*10)}🪙</button></span></div>`).join('');
const rec=RC.map((r,i)=>{const ok=Object.entries(r.i).every(([k,n])=>(S.inv[k]||0)>=n);return `<div class="row"><span>${ic_(r.o)} <b>${BK[r.o].n} ×${r.q}</b><br><small>${Object.entries(r.i).map(([k,n])=>BK[k].e+n+' '+BK[k].n).join(' + ')}</small></span><button${ok?'':' disabled style="opacity:.5"'} onclick="craft(${i})">Craft</button></div>`}).join('');
return['🔨 Crafting',yardH()+inv+'<b>Supplies</b>'+sup+'<br><b>Recipes</b>'+rec+'<small>Nuggets 🟠 and diamonds 💎 come from fishing. Put blocks in your 🎒 hotbar, then tap inside your Build Yard to place; pick ⛏ to break (blocks return to you).</small>']}
function craft(i){const r=RC[i];if(!Object.entries(r.i).every(([k,n])=>(S.inv[k]||0)>=n))return sfx('err');Object.entries(r.i).forEach(([k,n])=>S.inv[k]-=n);S.inv[r.o]=(S.inv[r.o]||0)+r.q;sfx('buy');toast('🔨 Crafted '+r.q+' '+BK[r.o].n);save();rp_()}
function bb(k,n){const c=BK[k].p*n;if(S.m<c)return toast('Not enough coins'),sfx('err');S.m-=c;S.inv[k]=(S.inv[k]||0)+n;sfx('buy');save();rp_()}
// pond
const PX=0,PZ=52,PW=20,PD=14;box(PW+3,.06,PD+3,0xe6d9a0,PX,.03,PZ,scene);
const water=new THREE.Mesh(new THREE.BoxGeometry(PW,.08,PD),new THREE.MeshLambertMaterial({color:0x3a8fe8,transparent:true,opacity:.88}));water.position.set(PX,.07,PZ);scene.add(water);
for(let i=0;i<6;i++)box(.9,.04,.9,0x2f9f4f,PX+R(-8,8),.12,PZ+R(-5,5),scene);solid(PX,PZ,PW,PD,0,1.7);
{const sg2=mkText('🎣 FISHING POND','#1f5fa8',384,96,5,1.25);sg2.position.set(PX,2.8,PZ-PD/2-1.6);scene.add(sg2);[-2.4,2.4].forEach(x=>box(.2,2.4,.2,0x6b4423,PX+x,1.2,PZ-PD/2-1.6,scene))}
SPOTS.pond=[PX,PZ-PD/2-3.5,'🎣 Fishing Pond'];
const FI={boot:{n:'Old Boot',e:'🥾',w:8,v:1},sardine:{n:'Sardine',e:'🐟',w:28,v:10},trout:{n:'Trout',e:'🐠',w:22,v:18},puffer:{n:'Pufferfish',e:'🐡',w:13,v:30},squid:{n:'Squid',e:'🦑',w:9,v:45},sand:{n:'Sand Bucket',e:'🏖️',w:5},wood:{n:'Driftwood',e:'🪵',w:4},nugget:{n:'Gold Nugget',e:'🟠',w:4,r:1},seed:{n:'Mystery Seed',e:'🌱',w:3,r:1},chest:{n:'Treasure Chest',e:'🎁',w:2,r:1},gem:{n:'Diamond',e:'💎',w:1.5,r:1},shark:{n:'Golden Shark',e:'🦈',w:.5,r:1,v:1500}};
const FS={st:0,t:0,x:0,z:0},bob=new THREE.Group();box(.3,.3,.3,0xff3030,0,.1,0,bob);box(.3,.12,.3,0xffffff,0,.31,0,bob);bob.visible=false;scene.add(bob);
const nearPond=()=>Math.hypot(Math.max(PX-PW/2-pl.x,0,pl.x-PX-PW/2),Math.max(PZ-PD/2-pl.z,0,pl.z-PZ-PD/2))<5.5;
function ftab(){const a=Object.keys(FI).map(k=>[k,FI[k].r?FI[k].w*(1+S.rod*.6):k==='boot'?FI[k].w*(1-S.rod*.2):FI[k].w]),t=a.reduce((x,y)=>x+y[1],0);return a.map(([k,w])=>[k,w/t*100])}
function fishEnd(){FS.st=0;bob.visible=false}
function fishBtn(){if(!nearPond())return toast('🎣 Walk to the pond (🧭 Teleport)'),sfx('err');
if(FS.st===0){const nx=cl(pl.x,PX-PW/2,PX+PW/2),nz=cl(pl.z,PZ-PD/2,PZ+PD/2),d=Math.hypot(nx-pl.x,nz-pl.z)||1,dx=(nx-pl.x)/d,dz=(nz-pl.z)/d,L=d+R(2.5,5);
FS.x=cl(pl.x+dx*L,PX-PW/2+1,PX+PW/2-1);FS.z=cl(pl.z+dz*L,PZ-PD/2+1,PZ+PD/2-1);pl.ry=Math.atan2(dx,dz);FS.st=1;FS.t=R(2,5)/(1+S.rod*.25);bob.position.set(FS.x,.1,FS.z);bob.visible=true;sfx('splash');puff(FS.x,FS.z,0x9ed0ff);toast('🎣 Waiting for a bite...')}
else if(FS.st===1){fishEnd();toast('Too early! Wait for the float to dip')}else reel()}
function reel(){const T=ftab();let r=Math.random()*100,id=T[0][0];for(const [k,p] of T){if(r<p){id=k;break}r-=p}fishEnd();const F=FI[id];S.fc[id]=(S.fc[id]||0)+1;let m=F.e+' '+F.n;
if(id==='sand'){S.inv.sand=(S.inv.sand||0)+4;m+=' +4 sand'}else if(id==='wood'){S.inv.log=(S.inv.log||0)+3;m+=' +3 logs'}else if(id==='nugget')S.inv.nugget=(S.inv.nugget||0)+1;else if(id==='gem')S.inv.gem=(S.inv.gem||0)+1;
else if(id==='seed'){const k=pick(Object.keys(CROPS).filter(k=>CT[k]>=2));S.seeds[k]=(S.seeds[k]||0)+1;m+=' → '+CROPS[k].n+' seed'}
else if(id==='chest'){const c=R(200,600)|0,k=pick(['stone','sand','log','dirt']);S.m+=c;S.inv[k]=(S.inv[k]||0)+5;m+=' +'+fm(c)+'🪙 +5 '+BK[k].n}
else{const v=Math.round(F.v*R(.8,1.5));S.bag.push({id,v});m+=' · '+v+'🪙'}
sfx(F.r?'hatch':'buy');puff(FS.x,FS.z,F.r?0xffd700:0x9ed0ff);toast((F.r?'✨ RARE! ':'🎣 Caught: ')+m);hot();save()}
function fishTick(dt,mvg){water.material.color.setHSL(.58,.7,.52+Math.sin(now*1.5)*.03);
if(FS.st){if(mvg||!nearPond()){fishEnd();toast('Fishing cancelled')}else{FS.t-=dt;bob.position.y=.1+(FS.st===2?-.12+Math.sin(now*30)*.05:Math.sin(now*3)*.03);
if(FS.t<=0){if(FS.st===1){FS.st=2;FS.t=1.4;sfx('bite');toast('❗ Bite! Tap 🎣 now!');puff(FS.x,FS.z,0xffffff)}else{fishEnd();toast('It got away…')}}}}
const f=$('fish'),show=!!(FS.st||nearPond()),tx=['🎣','⏳','❗'][FS.st];if(f.style.display!==(show?'block':'none'))f.style.display=show?'block':'none';if(f.textContent!==tx)f.textContent=tx}
const bagH=()=>S.bag.length?`<div class="row"><span>🧺 ${S.bag.length} fish</span><button onclick="sellFish()">Sell ${fm(S.bag.reduce((a,f)=>a+f.v,0))}🪙</button></div>`:'';
function sellFish(){sfx('sell');S.m+=S.bag.reduce((a,f)=>a+f.v,0);S.bag=[];save();rp_()}
function fishP(){return['🎣 Fishing','<small>Stand by the pond, tap 🎣, then tap again when the float dips. Rod level '+S.rod+'/3 improves rare odds.</small><br><b>Catch chances</b>'+ftab().sort((a,b)=>b[1]-a[1]).map(([k,p])=>{const F=FI[k];return `<div class="row"><span>${F.e} ${F.n}${F.r?' <em class="tb" style="background:#ffb300">RARE</em>':''}<br><small>caught ${S.fc[k]||0}${F.v?' · ~'+fm(F.v)+'🪙':''}</small></span><b>${p.toFixed(1)}%</b></div>`}).join('')+bagH()]}

const FMS=['','K','M','B','T','QD','QT','SX','SP','OC','NO','DC'];
function fm(n){if(typeof n!=='number'||!isFinite(n))return n;const ng=n<0?'-':'';n=Math.abs(Math.floor(n));if(n<1000)return ng+n;let e=0;while(e<FMS.length-1&&n/Math.pow(1000,e+1)>=1)e++;let v=Math.floor(n/Math.pow(1000,e)*100)/100;return ng+(+v.toFixed(2))+FMS[e]}

function save(){try{localStorage.setItem('gag_blocky',JSON.stringify(Object.assign({},S,{plots:plots.map(o=>o.p&&{type:o.p.type,kg:o.p.kg,prog:o.p.prog,mut:o.p.mut,b:o.p.b}),ts:Date.now(),px:pl.x,pz:pl.z,gt})));const v=$('sv');v.style.opacity=1;clearTimeout(v.t);v.t=setTimeout(()=>v.style.opacity=.3,700)}catch(e){}}
function loadGame(){const A=SAVED;if(!A.plots)return;const el=A.ts?cl((Date.now()-A.ts)/1000,0,7200):0,spd=1+S.spr*.2+bonus('grow');A.plots.forEach((d,i)=>{if(!d||!CROPS[d.type]||!plots[i])return;plant(i,d.type,d);const p=plots[i].p;p.prog=Math.min(1,p.prog+el*spd/CROPS[p.type].t);if(p.prog>=1)p.rd=1;lab(p)});if(A.px!=null&&!MOVED){pl.x=cl(+A.px||0,-58,80);pl.z=cl(+A.pz||8,-30,70);pl.y=supportY(pl.x,pl.z,2);if(hit(pl.x,pl.y,pl.z)){pl.x=OX;pl.z=OZ+8;pl.y=0}pl.sy=pl.y}if(A.gt!=null)gt=+A.gt||gt;if(MOVED)toast('🔀 Bases were shuffled! Find 🏡 YOUR BASE — your progress came with you');else if(el>60)toast('Welcome back! Your crops kept growing 🌱')}
setInterval(save,5000);addEventListener('pagehide',save);document.addEventListener('visibilitychange',()=>{document.hidden&&save()});
const MAXEQ=8,pb1=(p,t)=>t==='grow'?.1*(.7+.1*p.kg)*TM[PT[p.id]]:p.kg*PER[t==='sz'?'kg':t]*TM[PT[p.id]]*(PETS[p.id].a==='sz'?2:1);
function bonus(t){let b=0;const c={};S.eq.forEach(i=>{const p=S.pets[i];p&&(c[p.id]=(c[p.id]||0)+1)});S.eq.forEach(i=>{const p=S.pets[i];if(!p)return;const a=PETS[p.id].a,d=1+.1*(c[p.id]-1);if(a===t||(t==='kg'&&a==='sz'))b+=pb1(p,t)*d;else if(a==='all'&&t!=='hsz')b+=pb1(p,t)*.5*d});return b}
const szN=k=>k<1.5?'Tiny':k<3?'Small':k<5?'Normal':k<8?'Big':'HUGE',pScore=p=>pb1(p,'grow')*(PETS[p.id].a==='grow'?1.4:PETS[p.id].a==='all'?1.1:.6)+(PETS[p.id].a==='grow'||PETS[p.id].a==='all'?0:pb1(p,PETS[p.id].a)*.5);
function eqBest(){S.eq=S.pets.map((p,i)=>[i,pScore(p)]).sort((a,b)=>b[1]-a[1]).slice(0,MAXEQ).map(x=>x[0]);rebuildPets();sfx('buy');toast('⭐ Best '+S.eq.length+' pets equipped');save();rp_()}
function eqNone(){S.eq=[];rebuildPets();sfx('click');save();rp_()}
const petTop=()=>`<div style="display:flex;gap:4px;margin-bottom:6px"><button onclick="eqBest()">⭐ Equip best ${MAXEQ}</button><button onclick="eqNone()">Unequip all</button></div><small>🌱 Growth +${Math.round(bonus('grow')*100)}% · 💰 Sell +${Math.round(bonus('sell')*100)}% · ✨ Mut +${Math.round(bonus('mut')*100)}% · 🌾 Crop size +${Math.round(bonus('kg')*100)}% · 🥚 Hatch size +${Math.round(bonus('hsz')*100)}%<br>Growth pets all add together · each extra copy of the same pet adds +10% to its bonus.</small>`;
// ---------- sound, icons (item models), fx
let AC=null,mute=false;
function snd(f,d,ty='square',v=.15,sl=0,t0=0){if(!AC||mute)return;const t=AC.currentTime+t0,o=AC.createOscillator(),g=AC.createGain();o.type=ty;o.frequency.setValueAtTime(f,t);if(sl)o.frequency.exponentialRampToValueAtTime(Math.max(30,f*sl),t+d);g.gain.setValueAtTime(v,t);g.gain.exponentialRampToValueAtTime(.001,t+d);o.connect(g);g.connect(AC.destination);o.start(t);o.stop(t+d)}
function noise(d,v=.3,fq=800){if(!AC||mute)return;const n=AC.sampleRate*d|0,b=AC.createBuffer(1,n,AC.sampleRate),a=b.getChannelData(0);for(let i=0;i<n;i++)a[i]=(Math.random()*2-1)*(1-i/n);const s=AC.createBufferSource(),f=AC.createBiquadFilter(),g=AC.createGain();f.frequency.value=fq;g.gain.value=v;s.buffer=b;s.connect(f);f.connect(g);g.connect(AC.destination);s.start()}
const SF={click:()=>snd(600,.05),plant:()=>{snd(200,.12,'square',.2,2);noise(.1,.15,400)},harvest:()=>{snd(500,.1);snd(750,.12,'square',.15,0,.08)},water:()=>noise(.25,.2,2500),buy:()=>{snd(700,.08);snd(1000,.12,'square',.15,0,.07)},sell:()=>[900,1200,1500].forEach((f,i)=>snd(f,.1,'square',.12,0,i*.07)),err:()=>snd(120,.2,'sawtooth',.2),hatch:()=>[400,500,600,800,1000].forEach((f,i)=>snd(f,.12,'triangle',.2,0,i*.09)),thunder:()=>noise(1.2,.7,300),event:()=>{snd(260,.4,'sawtooth',.15);snd(390,.6,'sawtooth',.12,0,.3)},step:()=>noise(.04,.08,1200),place:()=>{snd(180,.07,'square',.15,.6);noise(.05,.1,600)},brk:()=>noise(.15,.25,500),splash:()=>noise(.3,.25,1800),bite:()=>{snd(900,.08);snd(900,.08,'square',.15,0,.12)},jump:()=>snd(300,.1,'square',.08,1.6)};
const sfx=k=>{try{SF[k]()}catch(e){}};function muteT(b){mute=!mute;b.textContent=mute?'🔇':'🔊'}
const ir=new THREE.WebGLRenderer({alpha:true,preserveDrawingBuffer:true});ir.setSize(64,64);ir.setClearColor(0,0);
const is=new THREE.Scene(),ic=new THREE.OrthographicCamera(-1,1,1,-1,.1,50),il=new THREE.DirectionalLight(0xffffff,.7);il.position.set(2,4,3);is.add(il,new THREE.AmbientLight(0xffffff,.8));
const IC={};function ico(k,mk){if(IC[k])return IC[k];const g=mk();g.scale.set(1,1,1);g.rotation.y=.7;is.add(g);const b=new THREE.Box3().setFromObject(g),c=b.getCenter(new THREE.Vector3()),s=b.getSize(new THREE.Vector3()),r=Math.max(s.x,s.y,s.z)*.7;ic.left=-r;ic.right=r;ic.top=r;ic.bottom=-r;ic.updateProjectionMatrix();ic.position.set(c.x+4,c.y+3,c.z+4);ic.lookAt(c);ir.render(is,ic);is.remove(g);return IC[k]=ir.domElement.toDataURL()}
const I=(k,mk,s=40)=>`<img class="ic" style="width:${s}px;height:${s}px" src="${ico(k,mk)}">`,tb=t=>`<em class="tb" style="background:${TC[t]}">${TIER[t]}</em>`;
function egg(c){const g=new THREE.Group();box(.6,.5,.6,c,0,.25,0,g);box(.4,.3,.4,c,0,.65,0,g);box(.15,.15,.02,0x886644,.15,.35,.31,g);return g}
const MODEL={e_common:()=>egg(0xf2e8d0),e_rare:()=>egg(0x6ec6ff),e_legend:()=>egg(0xffd24a),e_frost:()=>egg(0xbfe9ff),e_mythic:()=>egg(0xe27bff),can:()=>{const g=new THREE.Group();box(.7,.5,.5,0x3a8fe8,0,.25,0,g);box(.5,.1,.1,0x3a8fe8,.5,.45,0,g);box(.2,.4,.1,0x2a6fb8,-.4,.3,0,g);return g},spr:()=>{const g=new THREE.Group();box(.2,.6,.2,0x888888,0,.3,0,g);box(.5,.15,.5,0x44ccff,0,.65,0,g);return g},rod:()=>{const g=new THREE.Group();box(.1,1,.1,0x6b4a2b,0,.5,0,g);box(.5,.1,.1,0x6b4a2b,.25,.95,0,g);box(.08,.4,.08,0xffffff,.5,.75,0,g);box(.2,.2,.2,0xff3030,.5,.5,0,g);return g},chm:()=>{const g=new THREE.Group();[[-.2,0],[.2,0],[0,.2],[0,-.2]].forEach(a=>box(.3,.3,.1,0x2faa3f,a[0],a[1]+.3,0,g));box(.1,.3,.1,0x6b4a2b,0,0,0,g);return g}};
const pts=[];function puff(x,z,c){for(let i=0;i<10;i++){const m=box(.15,.15,.15,c,x,.5,z);m.userData={v:new THREE.Vector3(R(-2,2),R(3,6),R(-2,2)),l:.7};scene.add(m);pts.push(m)}}
function particles(dt){for(let i=pts.length-1;i>=0;i--){const m=pts[i],u=m.userData;u.l-=dt;u.v.y-=15*dt;m.position.addScaledVector(u.v,dt);m.scale.setScalar(Math.max(.01,u.l/.7));if(u.l<=0){scene.remove(m);pts.splice(i,1)}}}
function petAnim(m,k,sp,dt){const U=m.userData,T=performance.now()/1000,mg=cl(sp*1.5,0,1),f=0,fly=U.wings.length>0,ph=T*(6+mg*8)+k;
U.legs.forEach((l,i)=>l.rotation.x=Math.sin(ph+(i%2?0:Math.PI)+(i>1?Math.PI:0))*.7*mg);U.wings.forEach(w=>w.rotation.z=w.userData.s*Math.sin(T*(fly?25:10))*.7);
U.hd.rotation.x=Math.sin(T*2+k)*.08+Math.sin(ph)*.1*mg;U.tl.rotation.y=Math.sin(T*8+k)*(.4+.3*(1-mg));m.position.y=fly?1.2+Math.sin(T*3+k)*.2:Math.abs(Math.sin(ph))*.1*mg;m.scale.y=U.s0*(1+Math.sin(T*3+k)*.025*(1-mg))}
function hatch(eid,pid,kg){const h=$('hatch');h.style.display='flex';h.onclick=null;h.innerHTML=`<div class="shake">${I('e_'+eid,MODEL['e_'+eid],128)}</div><div>Hatching...</div>`;sfx('click');let n=0;const iv=setInterval(()=>{snd(300+n*60,.06,'square',.1);if(++n>8)clearInterval(iv)},120);
setTimeout(()=>{rebuildPets();sfx('hatch');h.innerHTML=`<div class="pop">${I('p_'+pid,()=>mkPet(pid,1),Math.round(cl(70+kg*14,80,230)))}</div><div>${tb(PT[pid])} ${PETS[pid].n} · <b>${kg}kg</b> · ${szN(kg)}</div>${bonus('hsz')>0?'<small>🥚 Pet bonus: +'+Math.round(bonus('hsz')*100)+'% size</small>':''}<small>Tap to continue</small>`;h.onclick=()=>{h.style.display='none';h.onclick=null}},1200)}
// plants
function mkPlant(type,kg){const C=CROPS[type],g=new THREE.Group(),mat=new THREE.MeshLambertMaterial({color:C.col,map:NT});
const f=new THREE.Mesh(new THREE.BoxGeometry(...C.d),mat);f.position.y=C.d[1]/2;g.add(f);box(.12,.25,.12,0x2f8f2f,0,C.d[1]+.1,0,g);box(.4,.1,.4,0x3aa83a,0,C.d[1]*.3,0,g);g.userData.mat=mat;g.userData.base=.5+.9*(kg/(C.kg[1]*1.1));return g}
function mkLab(){const c=document.createElement('canvas');c.width=256;c.height=384;const s=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(c),transparent:true,depthTest:false}));s.visible=false;s.scale.set(3.4,5.1,1);s.center.set(.5,0);s.renderOrder=5;s.raycast=()=>{};s.userData.c=c;return s}
function lab(p){const c=p.lab.userData.c,x=c.getContext('2d'),mu=p.mut.reduce((a,k)=>a+MUT[k].m-1,1),L=[];x.clearRect(0,0,256,384);p.lab.visible=!!p.show;if(!p.show)return;
L.push(p.prog>=1?['✔ READY','#8dff6a']:['Growing '+Math.min(99,p.prog*100|0)+'%','#ddd']);
L.push(['🪙 '+fm(Math.round(CROPS[p.type].p*p.kg*(1+bonus('kg'))*BASE[p.b].m*mu*(1+bonus('sell')))),'#ffe066']);if(p.prog>=1)L.push(['Tap to harvest','#fff']);

if(p.b==='gold')L.push(['★ GOLD ×5','#ffd700']);if(p.b==='rainbow')L.push(['🌈 RAINBOW ×10','rb']);
p.mut.forEach(k=>L.push([MUT[k].n+' ×'+MUT[k].m,new THREE.Color(MUT[k].c).lerp(new THREE.Color(1,1,1),.35).getStyle()]));
if(p.mut.length||p.b!=='normal')L.push(['= ×'+BASE[p.b].m*mu+' value','#fff']);
x.font='bold 26px "Courier New",monospace';x.textAlign='center';x.lineJoin='round';x.lineWidth=6;x.strokeStyle='#000';
L.forEach((l,i)=>{const y=374-(L.length-1-i)*36;let f=l[1];if(f==='rb'){f=x.createLinearGradient(20,0,236,0);['#ff5c5c','#ffd24a','#6dff6a','#4ac8ff','#c46bff'].forEach((q,n)=>f.addColorStop(n/4,q))}x.strokeText(l[0],128,y);x.fillStyle=f;x.fillText(l[0],128,y)});p.lab.material.map.needsUpdate=true}
function tint(p){const mt=p.m.userData.mat,k=p.mut[p.mut.length-1],c=k&&new THREE.Color(MUT[k].c);if(p.b==='gold'){mt.color.set(0xffd700);mt.emissive.copy(c||new THREE.Color(0x664400)).multiplyScalar(c?.35:1)}else if(p.b==='normal'&&c){mt.color.copy(c);mt.emissive.copy(c).multiplyScalar(.35)}}
function plant(i,type,pre){const C=CROPS[type],kg=pre?pre.kg:R(...C.kg)*(Math.random()<.06?1.8:1),m=mkPlant(type,kg),lk=1+S.chm*.4,r=Math.random(),b=pre?(pre.b||'normal'):r<.012*lk?'rainbow':r<.06*lk?'gold':'normal';m.position.set(plots[i].x,.2,plots[i].z);m.userData.pi=i;m.traverse(o=>o.userData.pi=i);scene.add(m);S.disc['c_'+type]=1;S.disc['b_'+b]=1;const p={type,kg,prog:pre?cl(+pre.prog||0,0,1):0,mut:pre?(pre.mut||[]).filter(k=>MUT[k]):[],m,b,lab:mkLab()};plots[i].p=p;p.lab.position.set(plots[i].x,1.7,plots[i].z);scene.add(p.lab);tint(p);lab(p);if(!pre&&b!=='normal')toast((b==='gold'?'★ Gold':'🌈 Rainbow')+' '+C.n+'! ×'+BASE[b].m)}
function mutOf(p,k){if(p.mut.includes(k)||p.mut.length>=5)return;p.mut.push(k);S.disc['m_'+k]=1;tint(p);lab(p)}
function tap(i){setTimeout(save,50);const pl_=plots[i],p=pl_.p;
if(!p){if('fp'.includes((S.hb[S.hs]||'-')[0]))return sfx('err'),toast('🙌 Hands full: pick a seed in your hotbar');if(!(S.seeds[S.sel]>0))return sfx('err'),toast('No seeds! Open 🌱 Seeds');S.seeds[S.sel]--;plant(i,S.sel);sfx('plant');puff(pl_.x,pl_.z,0x6b4423);hot()}
else{const shown=p.show;plots.forEach(o=>{if(o.p&&o!==pl_&&o.p.show){o.p.show=0;lab(o.p)}});p.show=1;p.sh=6;lab(p);
if(p.prog>=1){if(!shown)return sfx('click');const kg=p.kg*(1+bonus('kg')),mu=p.mut.reduce((a,k)=>a+MUT[k].m-1,1);S.fruit.push({t:p.type,kg,mu,b:p.b,mn:p.mut.map(k=>MUT[k].n)});scene.remove(p.m);scene.remove(p.lab);pl_.p=null;sfx('harvest');puff(pl_.x,pl_.z,CROPS[p.type].col);hot();toast('+'+CROPS[p.type].e+' '+(p.b!=='normal'?BASE[p.b].n+' ':'')+kg.toFixed(2)+'kg '+p.mut.map(k=>MUT[k].n).join(' '))}
else if(S.can&&(p.cd||0)<=0){p.prog+=.1;p.cd=1.5;sfx('water');puff(pl_.x,pl_.z,0x4aa3ff);lab(p)}else sfx('click')}}
const val=f=>Math.round(CROPS[f.t].p*f.kg*(f.b?BASE[f.b].m:1)*f.mu*(1+bonus('sell')));
// ---------- weather & time
let gt=.05,ev=null,nextEv=25,tick=0,boltT=3,flash=0,now=0;
function banner(t){const b=$('banner');b.textContent=t;b.style.display=t?'block':'none'}
const SKY={day:new THREE.Color(0x87ceeb),night:new THREE.Color(0x0b1030),blood:new THREE.Color(0x4a0606),storm:new THREE.Color(0x4a5560),rain:new THREE.Color(0x8da2b5),winter:new THREE.Color(0xc4d4e4)};
scene.fog=new THREE.Fog(0x87ceeb,40,120);scene.background=new THREE.Color(0x87ceeb);
function weather(dt){now+=dt;
if(ev&&now>ev.end){ev=null;banner('');nextEv=now+R(30,60)}
if(!ev&&now>nextEv){const k=['rain','thunder','lunar','blood','winter'][Math.random()*5|0];ev={k,end:now+R(40,60)};banner(EVN[k]);toast(EVN[k]);sfx('event')}
tick+=dt;if(tick>3){tick=0;plots.forEach(o=>{const p=o.p;if(!p)return;const ch=.3+bonus('mut')+S.chm*.08;
if(ev&&Math.random()<ch){if(ev.k==='rain'||ev.k==='thunder')mutOf(p,'wet');if(ev.k==='lunar')mutOf(p,'moon');if(ev.k==='blood')mutOf(p,'blood');if(ev.k==='winter'){mutOf(p,'chilled');if(Math.random()<.3)mutOf(p,'frozen')}}
if(Math.random()<.004+bonus('mut')*.05)mutOf(p,'twisted')})}
if(ev&&ev.k==='thunder'){boltT-=dt;if(boltT<0){boltT=R(3,6);flash=.25;const c=plots.filter(o=>o.p);if(c.length){const o=c[Math.random()*c.length|0];bolt.position.set(o.x,20,o.z);bolt.visible=true;mutOf(o.p,'shocked');sfx('thunder');setTimeout(()=>bolt.visible=false,200)}}}
flash=Math.max(0,flash-dt)}
function env(dt){gt=(gt+dt/200)%1;const k=ev&&ev.k,a=gt*6.283,sy=Math.sin(a);let d=cl(sy*2+.3,0,1);if(k==='lunar'||k==='blood')d=0;
const sky=SKY.night.clone().lerp(SKY.day,d);if(k==='blood')sky.copy(SKY.blood);if(k==='thunder')sky.lerp(SKY.storm,.8).multiplyScalar(.5+.5*d);if(k==='rain')sky.lerp(SKY.rain,.6*d+.2);if(k==='winter')sky.lerp(SKY.winter,.7*d+.15);if(flash>0)sky.set(0xdde6ff);
scene.background.copy(sky);scene.fog.color.copy(sky);amb.intensity=.25+.55*d+(flash>0?.8:0);sunL.intensity=.1+.8*d*(k==='thunder'?.4:1);
const px=pl.x,pz=pl.z;sun.position.set(px,sy*80,pz-Math.cos(a)*80-20);sun.lookAt(cam.position);sun.visible=sy>-.1&&d>0;
moon.position.set(px,-sy*80,pz+Math.cos(a)*80-20);if(k==='lunar'||k==='blood'){moon.position.set(px+20,60,pz-90)}moon.lookAt(cam.position);
moon.visible=d<.7;const big=k==='lunar'||k==='blood';moon.scale.setScalar(big?2.4:1);moon.material.color.set(k==='blood'?0xcc1111:0xe8ecff);moon.material.fog=false;
sunL.position.set(px+30,Math.max(20,sy*60),pz+20);
clouds.forEach(c=>{c.position.x+=dt*(k?3:1.2);if(c.position.x>90)c.position.x=-90;c.visible=d>.2||k==='thunder'||k==='rain'||k==='winter';c.userData.m.color.set(k==='thunder'?0x555a66:k==='rain'?0x9aa3ad:k==='winter'?0xdde4ea:0xffffff)});
rain.visible=k==='rain'||k==='thunder';if(rain.visible){const p=rg.attributes.position;for(let i=0;i<300;i++){let y=p.array[i*3+1]-dt*28;if(y<0)y=25;p.array[i*3+1]=y}rain.position.set(px,0,pz);p.needsUpdate=true}
snowF+=((k==='winter'?1:0)-snowF)*Math.min(1,dt*.4);snowP.visible=snowF>.02;snowP.material.opacity=snowF*.85;snow.visible=k==='winter';if(snow.visible){const p=sg.attributes.position;for(let i=0;i<400;i++){let y=p.array[i*3+1]-dt*3.5;if(y<0)y=25;p.array[i*3+1]=y;p.array[i*3]+=Math.sin(now*1.5+i)*dt*.6}snow.position.set(px,0,pz);p.needsUpdate=true}
const h=(gt*24+6)%24;$('clock').textContent=(d>.3?'☀️ ':'🌙 ')+String(h|0).padStart(2,'0')+':'+String((h%1)*60|0).padStart(2,'0')}
// ---------- input / camera
let yaw=0,pit=.7,dist=12;const keys={},mv={x:0,z:0},ptr=new Map();let pinch=0,down=null;
addEventListener('keydown',e=>{keys[e.code]=1;if(/^Digit[1-6]$/.test(e.code)){BR.on?brSel(+e.code[5]-1):selSlot(+e.code[5]-1)}if(BR.on&&e.code==='KeyR')brRel();if(BR.on&&e.code==='KeyH')brHeal();if(!BR.on&&e.code==='KeyE')$('panel').style.display==='block'?closeP():P('bag')});addEventListener('keyup',e=>keys[e.code]=0);
addEventListener('wheel',e=>{if(!e.target.closest('#panel'))dist=cl(dist*(1+e.deltaY*.001),4,26)},{passive:true});
const cvs=rd.domElement,rc=new THREE.Raycaster();
cvs.addEventListener('pointerdown',e=>{cvs.setPointerCapture(e.pointerId);ptr.set(e.pointerId,{x:e.clientX,y:e.clientY});down={x:e.clientX,y:e.clientY,t:performance.now(),mv:0};if(ptr.size===2){const [a,b]=[...ptr.values()];pinch=Math.hypot(a.x-b.x,a.y-b.y)}});
cvs.addEventListener('pointermove',e=>{const o=ptr.get(e.pointerId);if(!o)return;const dx=e.clientX-o.x,dy=e.clientY-o.y;o.x=e.clientX;o.y=e.clientY;if(down)down.mv+=Math.abs(dx)+Math.abs(dy);
if(ptr.size===2){const [a,b]=[...ptr.values()],d=Math.hypot(a.x-b.x,a.y-b.y);dist=cl(dist*pinch/d,4,26);pinch=d}else{yaw-=dx*.006;pit=cl(pit+dy*.005,.1,1.45)}});
cvs.addEventListener('pointerup',e=>{ptr.delete(e.pointerId);if(down&&down.mv<10&&performance.now()-down.t<450&&ptr.size===0){rc.setFromCamera({x:e.clientX/innerWidth*2-1,y:-e.clientY/innerHeight*2+1},cam);if(BR.on){brAtk();down=null;return}if(bm){buildTap();down=null;return}const h=rc.intersectObjects(scene.children,true).find(x=>{let o=x.object;while(o){if(o.userData.pi!==undefined||o.userData.soil||o.userData.shop)return true;o=o.parent}});if(h){let o=h.object;while(o&&o.userData.pi===undefined&&!o.userData.soil&&!o.userData.shop)o=o.parent;if(o.userData.shop){sfx('click');P(o.userData.shop)}else if(o.userData.soil){const q=h.point;tap(cl(Math.floor((q.z-SZ-OZ+SD/2)/SX),0,3)*6+cl(Math.floor((q.x-OX+SW/2)/SX),0,5))}else tap(o.userData.pi)}}if(!ptr.size)down=null});
cvs.addEventListener('pointercancel',e=>ptr.delete(e.pointerId));
const st=$('stick'),kn=$('knob');let sid=null;
function sm(e){const r=st.getBoundingClientRect(),dx=e.clientX-r.left-55,dy=e.clientY-r.top-55,l=Math.hypot(dx,dy)||1,k=Math.min(l,45)/l;kn.style.left=35+dx*k+'px';kn.style.top=35+dy*k+'px';mv.x=dx*k/45;mv.z=dy*k/45}
st.addEventListener('pointerdown',e=>{sid=e.pointerId;st.setPointerCapture(sid);sm(e)});st.addEventListener('pointermove',e=>{if(e.pointerId===sid)sm(e)});
const se=e=>{if(e.pointerId===sid){sid=null;mv.x=mv.z=0;kn.style.left=kn.style.top='35px'}};st.addEventListener('pointerup',se);st.addEventListener('pointercancel',se);
// ---------- UI
function toast(t){const e=$('toast');e.textContent=t;e.style.display='block';clearTimeout(e.t);e.t=setTimeout(()=>e.style.display='none',1800)}
function slotH(it,on,oc,num){const[k,v]=(it||'').split(':');let img='',n='';
if(k==='c'&&CROPS[v]){img=`<img src="${ico('s_'+v,()=>mkSeed(v))}">`;n=S.seeds[v]||0}else if(k==='f'&&CROPS[v]){img=`<img src="${ico('c_'+v,()=>mkPlant(v,CROPS[v].kg[1]*.9))}">`;n=S.fruit.filter(f=>f.t===v).length}else if(k==='p'&&S.pets[+v]){const q=S.pets[+v];img=`<img src="${ico('p_'+q.id,()=>mkPet(q.id,1))}">`;n=q.kg.toFixed(1)}else if(k==='b'&&BK[v]){img=`<img src="${ico('k_'+v,()=>mkBlk(v))}">`;n=S.inv[v]||0}else if(k==='x')img='<b>⛏</b>';
return `<div class="slot ${on?'on':''} ${n===0?'dim':''}" onclick="${oc}">${num?'<s>'+num+'</s>':''}${img}<i>${n}</i></div>`}
let hk='',hm=null,HC=0;
const mkSeed=k=>{const g=new THREE.Group(),c=CROPS[k].col;box(.5,.65,.1,0xe8d9b0,0,.35,0,g);box(.5,.1,.12,0xc9a46a,0,.7,0,g);box(.36,.3,.12,c,0,.35,0,g);box(.1,.1,.14,0x333333,-.1,.2,0,g);box(.1,.1,.14,0x333333,.1,.5,0,g);return g};
const mkPick=()=>{const g=new THREE.Group();box(.1,.8,.1,0x6b4a2b,0,.4,0,g);box(.6,.12,.12,0x9a9a9a,0,.82,0,g);box(.12,.2,.12,0x9a9a9a,-.3,.74,0,g);box(.12,.2,.12,0x9a9a9a,.3,.74,0,g);return g};
function fixHb(){let ch=0;S.hb=S.hb.map(it=>{const[k,v]=(it||'').split(':');if(k==='f'&&!S.fruit.some(f=>f.t===v)||k==='p'&&!S.pets[+v]){ch=1;return''}return it});if(ch)syncSel()}
function updHold(){const it=S.hb[S.hs]||'',[k,v]=it.split(':');let key=it,f=null,p=null;if(k==='f'){f=S.fruit.find(x=>x.t===v);key=f?it+f.kg+f.b:''}else if(k==='p'){p=S.pets[+v];key=p?it+p.id+p.kg:''}
if(key===hk&&(hm?hm.parent:!key))return;hk=key;if(hm&&hm.parent)hm.parent.remove(hm);hm=null;HC=0;let g=null;const L=me.userData.L;
if(k==='c'&&CROPS[v]){g=mkSeed(v);g.scale.setScalar(.7);HC=2}else if(k==='b'&&BK[v]){g=mkBlk(v);g.scale.setScalar(.4);g.position.y=.2;HC=2}else if(k==='x'){g=mkPick();HC=2}
if(HC===2){const h=new THREE.Group();h.position.set(0,-.55,.12);h.rotation.x=1;h.add(g);g.position.y+=-.1;L[3].add(h);hm=h;return}
if(f){g=mkPlant(v,f.kg);g.scale.setScalar(Math.min(g.userData.base*.9,1.2));if(f.b==='gold')g.userData.mat.color.set(0xffd700);if(f.b==='rainbow')g.userData.mat.color.set(0xff7ad9);g.position.set(0,.95,.68)}
else if(p){g=mkPet(p.id,p.kg);g.scale.setScalar(cl((.4+.2*p.kg)*.6,.3,1));g.position.set(0,.85,.7)}
if(g){HC=1;me.add(g);hm=g}}
function hot(){if(BR.on)return;fixHb();$('hot').innerHTML=S.hb.map((it,i)=>slotH(it,i===S.hs,`selSlot(${i})`,i+1)).join('');$('money').textContent='🪙 '+fm(S.m);updHold()}
function syncSel(){const[k,v]=(S.hb[S.hs]||'').split(':');bm=k==='b'||k==='x';if(k==='c')S.sel=v;if(k==='b')S.bsel=v;if(k==='x')S.bsel='break'}
function selSlot(i){S.hs=i;syncSel();sfx('click');hot();if(cur==='bag')rp_()}
function setSlot(it){const j=S.hb.indexOf(it);if(j>=0&&j!==S.hs)S.hb[j]=S.hb[S.hs];S.hb[S.hs]=it;syncSel();sfx('click');save();rp_()}
function autoSlot(it){let i=S.hb.indexOf(it);if(i<0){i=S.hb.findIndex(x=>!x||(x[0]==='c'&&!(S.seeds[x.slice(2)]>0)));if(i<0)return toast('🎒 New seeds are in your bag');S.hb[i]=it}selSlot(i)}
function bagP(){const e=[];Object.keys(S.seeds).forEach(k=>CROPS[k]&&S.seeds[k]>0&&e.push('c:'+k));Object.keys(BK).forEach(k=>!BK[k].ni&&(S.inv[k]||0)>0&&e.push('b:'+k));e.push('x:break');[...new Set(S.fruit.map(f=>f.t))].forEach(k=>e.push('f:'+k));S.pets.forEach((p,i)=>e.push('p:'+i));while(e.length<20)e.push('');
return['🎒 Bag','<small>Tap a hotbar slot, then tap an item to put it there. Keys 1-6 · E opens the bag. Seeds show as packets; 🧺 crops and 🐾 pets are carried with both hands.</small><br><b>Hotbar</b><div class="bgrid">'+S.hb.map((it,i)=>slotH(it,i===S.hs,`selSlot(${i})`,i+1)).join('')+'</div><b>Items</b><div class="bgrid">'+e.map(it=>it?slotH(it,false,`setSlot(\'${it}\')`):'<div class="slot"></div>').join('')+`</div><small>🟠 ${S.inv.nugget||0} nuggets · 💎 ${S.inv.gem||0} diamonds · 🧺 ${S.bag.length} fish · ⛏ = break blocks</small>`]}
let cur='';
function P(n){sfx('click');cur=n;tr={g:null,t:null};$('panel').style.display='block';rp_()}function closeP(){cur='';sc=-1;$('panel').style.display='none'}
function rp_(){if(!cur)return;let h='',t='';
if(cur==='seeds'){t='🌱 Seed Shop';h=Object.entries(CROPS).map(([k,c])=>`<div class="row"><span>${I('c_'+k,()=>mkPlant(k,c.kg[1]*.9))} ${c.n} ${tb(CT[k])}<br><small>${c.t}s · ${c.kg[0]}–${c.kg[1]}kg · ${fm(c.p)}🪙/kg</small></span><button onclick="buy('seed','${k}')">${fm(c.cost)}🪙</button></div>`).join('')+'<small>Sell = 🪙/kg × kg × variant × mutations. Normal ×1 · Gold ×5 · Rainbow ×10</small>'}
if(cur==='eggs'){t='🥚 Egg Shop';h=Object.entries(EGGS).map(([k,c])=>`<div class="row"><span>${I('e_'+k,MODEL['e_'+k])} ${c.n}<br><small>${c.pool.map(p=>PETS[p[0]].e+p[1]+'%').join(' ')} · ${c.kg[0]}–${c.kg[1]}kg</small></span><button onclick="buy('egg','${k}')">${fm(c.cost)}🪙</button></div>`).join('')+'<small>Heavier pets are bigger and stronger. Equip up to 8; growth pets stack!</small>'}
if(cur==='gear'){t='⚙️ Gear Shop';const G=[['can','💧 Watering Can','Tap growing plants: +10% growth',200,1],['spr','🚿 Sprinkler','+20% growth speed (max 3)',[400,800,1500][S.spr]||0,3],['chm','🍀 Lucky Charm','+8% mutation chance (max 3)',1000*(S.chm+1),3],['rod','🎣 Lucky Rod','Rarer catches & faster bites (max 3)',[300,900,2500][S.rod]||0,3]];
h=G.map(g=>`<div class="row"><span>${I(g[0],MODEL[g[0]])} ${g[1]} <small>(${S[g[0]]}/${g[4]})</small><br><small>${g[2]}</small></span>${S[g[0]]>=g[4]?'<b>MAX</b>':`<button onclick="buy('${g[0]}')">${fm(g[3])}🪙</button>`}</div>`).join('')}
if(cur==='pets'){t='🐾 Pets ('+S.eq.length+'/'+MAXEQ+' equipped)';h=S.pets.length?petTop()+S.pets.map((p,i)=>{const D=PETS[p.id],on=S.eq.includes(i);return `<div class="row"><span>${I('p_'+p.id,()=>mkPet(p.id,1),Math.round(cl(26+p.kg*5,30,64)))} ${D.n} ${tb(PT[p.id])} <b>${p.kg.toFixed(2)}kg</b> <small>${szN(p.kg)}</small><br><small>+${((D.a==='all'?pb1(p,'sell')*.5:pb1(p,D.a))*100).toFixed(0)}% ${AN[D.a]}</small></span><span style="display:flex;flex-direction:column;gap:4px"><button onclick="eq(${i})">${on?'Unequip':'Equip'}</button><button onclick="setSlot('p:${i}')">✋ Hold</button><button onclick="sellPet(${i})"${sc===i?' style="background:#e57373"':''}>${sc===i?'Sure? ':'Sell '}${fm(pv(p))}🪙</button></span></div>`}).join(''):'No pets yet. Hatch an egg!'}
if(cur==='tp'){t='🧭 Teleport';h=Object.entries(SPOTS).map(([k,s])=>`<div class="row"><span style="font-size:18px">${s[2]}</span><button onclick="tp('${k}')">Go</button></div>`).join('')+'<small>Tap the NPC at a shop to buy. Pets roam your garden. Game saves automatically.</small>'}
if(cur==='index'){t='📖 Index';const fr=(ok,im,n,c)=>`<div class="frame ${ok?'':'lock'}" style="border-color:${c}">${im}<br>${ok?n:'???'}</div>`;h='<b>Seeds</b><div class="grid">'+Object.keys(CROPS).map(k=>fr(S.disc['c_'+k],I('c_'+k,()=>mkPlant(k,CROPS[k].kg[1]*.9),56),CROPS[k].n,TC[CT[k]])).join('')+'</div><b>Pets</b><div class="grid">'+Object.keys(PETS).map(k=>fr(S.disc['p_'+k],I('p_'+k,()=>mkPet(k,1),56),PETS[k].n,TC[PT[k]])).join('')+'</div><b>Mutations</b><div class="grid">'+Object.keys(MUT).map(k=>`<div class="frame ${S.disc['m_'+k]?'':'lock'}" style="border-color:#${MUT[k].c.toString(16).padStart(6,'0')}">${S.disc['m_'+k]?MUT[k].n+' x'+MUT[k].m:'???'}</div>`).join('')+'</div><b>Variants</b><div class="grid">'+Object.entries(BASE).map(([k,b])=>{const ok=k==='normal'||S.disc['b_'+k];return `<div class="frame ${ok?'':'lock'}" style="border-color:${k==='gold'?'#ffd700':k==='rainbow'?'#ff7ad9':'#999'}">${ok?b.n+' x'+b.m:'???'}</div>`}).join('')+'</div>'}
if(cur==='sell'){t='💰 Sell Crops';const tot=S.fruit.reduce((a,f)=>a+val(f),0);h=(S.fruit.length?S.fruit.slice(-12).map(f=>`<div class="row"><span>${CROPS[f.t].e} ${f.kg.toFixed(2)}kg<br><small>${f.b&&f.b!=='normal'?BASE[f.b].n+' ×'+BASE[f.b].m+' · ':''}${(f.mn||[]).join(', ')||'no mutation'} · mut ×${f.mu}</small></span><b>${fm(val(f))}🪙</b></div>`).join('')+`<small>${S.fruit.length} items</small><br><br><button onclick="sell()">Sell all: ${fm(tot)}🪙</button>`:'Nothing to sell. Harvest ripe plants!')+bagH()}
if(cur==='weapons')[t,h]=wpP();if(cur==='portal')[t,h]=portalP();if(cur==='bag')[t,h]=bagP();if(cur==='craft')[t,h]=craftP();if(cur==='fish')[t,h]=fishP();
if(cur.slice(0,3)==='npc'){const r=npcTrade(+cur.slice(3));t=r[0];h=r[1]}
if(cur==='seeds'||cur==='eggs'||cur==='gear'||cur==='weapons')h+=navH();
$('pt').textContent=t;$('pb').innerHTML=h;hot()}
const navH=()=>'<div style="display:flex;flex-wrap:wrap;gap:4px;margin-top:8px"><b style="width:100%">🧭 Teleport</b>'+[['seeds','🌱 Seeds'],['eggs','🥚 Eggs'],['gear','⚙️ Gear'],['weapons','⚔️ Weapons'],['garden','🏡 Garden']].filter(x=>x[0]!==cur).map(x=>`<button onclick="go('${x[0]}')">${x[1]}</button>`).join('')+'</div>';
function go(k){tp(k);if(k!=='garden')setTimeout(()=>P(k),60)}
function buy(k,id){const pay=c=>S.m>=c?(S.m-=c,sfx('buy'),1):(toast('Not enough coins'),sfx('err'),0);
if(k==='seed'&&pay(CROPS[id].cost)){S.seeds[id]=(S.seeds[id]||0)+1;autoSlot('c:'+id)}
else if(k==='egg'&&pay(EGGS[id].cost)){const E=EGGS[id];let r=Math.random()*100,pid=E.pool[0][0];for(const p of E.pool){if(r<p[1]){pid=p[0];break}r-=p[1]}const kg=+(R(...E.kg)*(Math.random()<.01?2.2:Math.random()<.1?1.6:1)*(1+bonus('hsz'))).toFixed(2);S.pets.push({id:pid,kg});if(S.eq.length<MAXEQ)S.eq.push(S.pets.length-1);S.disc['p_'+pid]=1;hatch(id,pid,kg)}
else if(k==='can'&&pay(200))S.can=1;else if(k==='spr'&&pay([400,800,1500][S.spr]))S.spr++;else if(k==='chm'&&pay(1000*(S.chm+1)))S.chm++;else if(k==='rod'&&pay([300,900,2500][S.rod]))S.rod++;
rp_()}
function eq(i){sc=-1;const x=S.eq.indexOf(i);if(x>=0)S.eq.splice(x,1);else if(S.eq.length<MAXEQ)S.eq.push(i);else toast('Max '+MAXEQ+' pets equipped');rebuildPets();rp_()}
function sell(){sfx('sell');S.m+=S.fruit.reduce((a,f)=>a+val(f),0);S.fruit=[];rp_()}
// ---------- start / fullscreen / orientation
const chkRot=()=>{$('rot').style.display=mobile&&innerHeight>innerWidth?'flex':'none'};
$('start').onclick=async()=>{$('start').style.display='none';try{AC=new(window.AudioContext||window.webkitAudioContext)()}catch(e){}if(mobile){try{await document.documentElement.requestFullscreen()}catch(e){}try{await screen.orientation.lock('landscape')}catch(e){}}chkRot()};
if(!mobile)$('stick').style.display='none';
addEventListener('resize',()=>{rd.setSize(innerWidth,innerHeight);cam.aspect=innerWidth/innerHeight;cam.updateProjectionMatrix();chkRot()});
// ================= LEAGUE OF FARMERS: weapons, portal, battle royale =================
const WP={fists:{n:'Fists',e:'✊',d:8,cd:.45,rg:2.2,m:'melee'},sword:{n:'Sword',e:'🗡️',d:30,cd:.55,rg:3.2,m:'melee',cost:400},crossbow:{n:'Crossbow',e:'🏹',d:55,cd:1.3,rg:60,m:'rng',sp:46,cost:2500},pistol:{n:'Pistol',e:'🔫',d:15,cd:.2,rg:50,m:'rng',sp:80,cost:6000}},WL=['fists','sword','crossbow','pistol'];
S.wp=S.wp||{};S.ammo=S.ammo||0;S.brs=S.brs||{w:0,k:0,g:0};
function mkWeapon(k){const g=new THREE.Group();
if(k==='sword'){box(.1,.3,.1,0x6b4a2b,0,.15,0,g);box(.4,.08,.12,0x999999,0,.32,0,g);box(.12,.8,.06,0xdfe8ee,0,.76,0,g)}
else if(k==='crossbow'){box(.1,.7,.1,0x6b4a2b,0,.35,0,g);box(.8,.08,.08,0x4a3a2a,0,.62,0,g);box(.78,.02,.02,0xeeeeee,0,.52,0,g);box(.04,.45,.04,0x999999,0,.5,.07,g)}
else if(k==='pistol'){box(.12,.5,.14,0x555555,0,.35,0,g);box(.1,.25,.12,0x222222,0,.08,.04,g)}
return g}
function wpP(){const row=k=>{const w=WP[k];return`<div class="row"><span>${I('w_'+k,()=>mkWeapon(k),40)} <b>${w.n}</b><br><small>${w.m==='melee'?'Melee · reach '+w.rg:'Ranged · uses ammo · '+w.rg+'m'} · ${w.d} dmg · ${w.cd}s${k==='pistol'?' · 12-round mag':''}</small></span>${S.wp[k]?'<b>OWNED</b>':`<button onclick="buyW('${k}')">${fm(w.cost)}🪙</button>`}</div>`};
return['⚔️ Weapon Shop',['sword','crossbow','pistol'].map(row).join('')+`<div class="row"><span>📦 <b>Ammo pack ×40</b><br><small>Carrying ${S.ammo} · used by 🏹 and 🔫</small></span><button onclick="buyW('ammo')">150🪙</button></div><small>Weapons you own come with you into the ⚔ Battle Royale 🌀 portal. More can be found in 📦 crates.</small>`]}
function buyW(k){const c=k==='ammo'?150:WP[k].cost;if(S.m<c)return toast('Not enough coins'),sfx('err');S.m-=c;if(k==='ammo')S.ammo+=40;else S.wp[k]=1;sfx('buy');save();rp_()}
function portalP(){const b=S.brs;return['🌀 Battle Royale Portal',`<div style="text-align:center;font-size:16px"><b>Teleport to the Battle Royale?</b><br><br>20 players · you + 19 bots<br>🪂 Parachute in · 📦 loot crates · ❤ health &amp; 🛡 armor<br>🔵 The safe zone collapses every 1 minute<br>🏆 Last farmer standing wins coins!<br><br><small>Your weapons: ${['sword','crossbow','pistol'].filter(k=>S.wp[k]).map(k=>WP[k].e).join(' ')||'none yet · buy some at the ⚔️ Weapon Shop'}<br>🏆 ${b.w} wins · ☠ ${b.k} kills · 🎮 ${b.g} games</small><br><br><button style="font-size:18px;padding:8px 18px" onclick="enterBR()">⚔ Teleport!</button> <button onclick="closeP()">Stay</button></div>`]}
// ---- weapon shop stall + portal on the island
stall(24,'weapons','⚔️ WEAPON SHOP',0xb03030,'⚔️ Blade',mkNPC(0xc99872,0x222222,0x777777,0x333333,h=>box(.56,.2,.56,0x888888,0,.6,0,h)));
SPOTS.weapons=[24,-14,'⚔️ Weapon Shop'];SPOTS.br=[-26,-18.5,'🌀 Battle Portal'];
const PQ=[-26,-23];let pa=1,pt_=0;
{const g=new THREE.Group();g.position.set(PQ[0],0,PQ[1]);[-1.7,1.7].forEach(x=>{box(.8,5,.8,0x2a1448,x,2.5,0,g);box(.3,5,.9,0x9b4dff,x,2.5,0,g)});box(4.2,.8,.8,0x2a1448,0,5.4,0,g);
const pm=new THREE.Mesh(new THREE.PlaneGeometry(2.6,4.8),new THREE.MeshBasicMaterial({color:0x8a3aff,transparent:true,opacity:.75,side:THREE.DoubleSide}));pm.position.set(0,2.5,0);g.add(pm);
const sg_=mkText('🌀 BATTLE ROYALE','#5a1a8a',384,96,5,1.25);sg_.position.set(0,6.7,0);g.add(sg_);g.traverse(o=>o.userData.shop='portal');scene.add(g);PQ.m=pm;solid(PQ[0]-1.7,PQ[1],.8,.8,0,5);solid(PQ[0]+1.7,PQ[1],.8,.8,0,5)}
function portalTick(dt){if(BR.on)return;PQ.m.material.color.setHSL(.74+Math.sin(now*2)*.04,.9,.55);pt_-=dt;if(pt_<=0){pt_=.45;puff(PQ[0]+R(-1.2,1.2),PQ[1]+.3,0xc08bff)}
const near=Math.abs(pl.x-PQ[0])<2.3&&Math.abs(pl.z-PQ[1]-.5)<2.3;if(near&&pa&&cur!=='portal'){pa=0;P('portal')}if(!near&&Math.hypot(pl.x-PQ[0],pl.z-PQ[1])>6)pa=1}
// ---- infinite voxel terrain (chunks)
const RD=5,SEA=5,CH=new Map(),HC_=new Map(),CR=new Map();let SEED=1;const BX=5000;
const hs=(x,z,s)=>{let h=Math.imul(x|0,374761393)^Math.imul(z|0,668265263)^Math.imul(s|0,1442695041);h=Math.imul(h^h>>>13,1274126177);return((h^h>>>16)>>>0)/4294967296};
const vn=(x,z,s)=>{const i=Math.floor(x),j=Math.floor(z),u=x-i,v=z-j,a=u*u*(3-2*u),b=v*v*(3-2*v);return hs(i,j,s)*(1-a)*(1-b)+hs(i+1,j,s)*a*(1-b)+hs(i,j+1,s)*(1-a)*b+hs(i+1,j+1,s)*a*b};
const rawH=(x,z)=>1+Math.floor((.55*vn(x/40,z/40,SEED)+.3*vn(x/17,z/17,SEED+7)+.15*vn(x/7,z/7,SEED+13))*17);
const ck=(cx,cz)=>(cx+32768)*65536+(cz+32768);
function hc(cx,cz){const k=ck(cx,cz);let a=HC_.get(k);if(!a){if(HC_.size>600)HC_.clear();a=new Uint8Array(256);for(let j=0;j<16;j++)for(let i=0;i<16;i++)a[j*16+i]=rawH(cx*16+i,cz*16+j);HC_.set(k,a)}return a}
const RH=(i,k)=>hc(i>>4,k>>4)[(k&15)*16+(i&15)],T=(x,z)=>Math.max(SEA,RH(Math.floor(x),Math.floor(z))),trunk=(i,k)=>RH(i,k)>SEA&&RH(i,k)<14&&hs(i,k,SEED+99)<.012;
function brHit(x,y,z){for(let i=Math.floor(x-PR);i<=Math.floor(x+PR);i++)for(let k=Math.floor(z-PR);k<=Math.floor(z+PR);k++){const t=T(i,k);if(y<t-.001)return 1;if(trunk(i,k)&&y<t+3.999&&y+PH>t)return 1}return 0}
function brTops(x,z,lo,hi){const r=[];for(let i=Math.floor(x-PR);i<=Math.floor(x+PR);i++)for(let k=Math.floor(z-PR);k<=Math.floor(z+PR);k++){const t=T(i,k);if(t>lo&&t<=hi)r.push(t);if(trunk(i,k)&&t+4>lo&&t+4<=hi)r.push(t+4)}return r.sort((a,b)=>a-b)}
const BRM=new THREE.MeshLambertMaterial({vertexColors:true});
function mkChunk(cx,cz){const P_=[],N=[],C=[],X=[];let vi=0;
const q=(pts,h,cols)=>{const cs=typeof cols[0]==='number'?[cols,cols,cols,cols]:cols.slice();pts=pts.slice();const a=pts[0],b=pts[1],c=pts[2],ux=b[0]-a[0],uy=b[1]-a[1],uz=b[2]-a[2],vx=c[0]-a[0],vy=c[1]-a[1],vz=c[2]-a[2];let nx=uy*vz-uz*vy,ny=uz*vx-ux*vz,nz=ux*vy-uy*vx;const l=Math.hypot(nx,ny,nz)||1;nx/=l;ny/=l;nz/=l;
if(nx*h[0]+ny*h[1]+nz*h[2]<0){[pts[1],pts[3]]=[pts[3],pts[1]];[cs[1],cs[3]]=[cs[3],cs[1]];nx=-nx;ny=-ny;nz=-nz}
for(let i=0;i<4;i++){P_.push(...pts[i]);N.push(nx,ny,nz);C.push(...cs[i])}X.push(vi,vi+1,vi+2,vi,vi+2,vi+3);vi+=4};
const bx=(x0,y0,z0,x1,y1,z1,c)=>{q([[x1,y0,z0],[x1,y1,z0],[x1,y1,z1],[x1,y0,z1]],[1,0,0],c);q([[x0,y0,z0],[x0,y1,z0],[x0,y1,z1],[x0,y0,z1]],[-1,0,0],c);q([[x0,y1,z0],[x0,y1,z1],[x1,y1,z1],[x1,y1,z0]],[0,1,0],c);q([[x0,y0,z1],[x0,y1,z1],[x1,y1,z1],[x1,y0,z1]],[0,0,1],c);q([[x0,y0,z0],[x0,y1,z0],[x1,y1,z0],[x1,y0,z0]],[0,0,-1],c)};
for(let j=0;j<16;j++)for(let i=0;i<16;i++){const x=cx*16+i,z=cz*16+j,rh=RH(x,z),t=Math.max(SEA,rh),v=(hs(x,z,SEED+3)-.5)*.1;
const tc=rh<SEA?[.2+v,.42+v,.85]:t<=SEA+1?[.86+v,.8+v,.55]:t<11?[.3+v,.62+v,.22+v]:t<14?[.45+v,.52+v,.4+v]:[.93,.96,1];
q([[x,t,z],[x,t,z+1],[x+1,t,z+1],[x+1,t,z]],[0,1,0],tc);
const sd=rh<SEA?[.8,.75,.5]:[.42,.28,.16],sg=[.4,.4,.42];
for(const[dx,dz]of[[1,0],[-1,0],[0,1],[0,-1]]){const n=T(x+dx,z+dz);if(n>=t)continue;let p;if(dx){const X1=dx>0?x+1:x;p=[[X1,n,z],[X1,t,z],[X1,t,z+1],[X1,n,z+1]]}else{const Z1=dz>0?z+1:z;p=[[x,n,Z1],[x,t,Z1],[x+1,t,Z1],[x+1,n,Z1]]}q(p,[dx,0,dz],[sg,sd,sd,sg])}
if(trunk(x,z)){bx(x+.3,t,z+.3,x+.7,t+4,z+.7,[.42,.28,.15]);const lv=[.15+v,.5+v,.14];bx(x-1,t+3,z-1,x+2,t+5,z+2,lv);bx(x,t+5,z,x+1,t+6,z+1,lv)}}
const g=new THREE.BufferGeometry();g.setAttribute('position',new THREE.Float32BufferAttribute(P_,3));g.setAttribute('normal',new THREE.Float32BufferAttribute(N,3));g.setAttribute('color',new THREE.Float32BufferAttribute(C,3));g.setIndex(X);g.computeBoundingSphere();
const m=new THREE.Mesh(g,BRM);scene.add(m);return m}
const OFF=[];for(let a=-RD;a<=RD;a++)for(let b=-RD;b<=RD;b++)if(a*a+b*b<=RD*RD+1)OFF.push([a,b]);OFF.sort((p,q)=>p[0]*p[0]+p[1]*p[1]-q[0]*q[0]-q[1]*q[1]);
function chunks(max){const pcx=Math.floor(pl.x/16),pcz=Math.floor(pl.z/16);let n=0;for(const[a,b]of OFF){const k=ck(pcx+a,pcz+b);if(!CH.has(k)){CH.set(k,{m:mkChunk(pcx+a,pcz+b),cx:pcx+a,cz:pcz+b});if(++n>=max)break}}
if((BR.fr=(BR.fr||0)+1)%40===0)for(const[k,c]of CH)if(Math.abs(c.cx-pcx)>RD+1||Math.abs(c.cz-pcz)>RD+1){hideCr(c);scene.remove(c.m);c.m.geometry.dispose();CH.delete(k)}}
// ---- loot crates
const CBG=new THREE.BoxGeometry(.8,.6,.8),LBG=new THREE.BoxGeometry(.86,.16,.86),BBG=new THREE.BoxGeometry(.12,14,.12),CMT=new THREE.MeshLambertMaterial({color:0xe2a72e,emissive:0x553300}),CLT=new THREE.MeshLambertMaterial({color:0x9c6a1a}),CBM=new THREE.MeshBasicMaterial({color:0xffe066,transparent:true,opacity:.35});
function rollLoot(n=2){const t=['ammo','ammo','bandage','bandage','medkit','vest','vest','sword','crossbow','pistol'],o=[];for(let i=0;i<n;i++)o.push(t[Math.random()*t.length|0]);return o}
function crates(cx,cz){const k=ck(cx,cz);let a=CR.get(k);if(!a){a=[];if(hs(cx,cz,SEED+5)<.5){const x=cx*16+3+(hs(cx,cz,SEED+6)*10|0),z=cz*16+3+(hs(cx,cz,SEED+8)*10|0);if(RH(x,z)>=SEA&&!trunk(x,z))a.push({x:x+.5,z:z+.5,y:T(x,z),loot:rollLoot(),m:null})}CR.set(k,a)}return a}
function syncCr(){for(const c of CH.values())for(const r of crates(c.cx,c.cz))if(!r.m){const m=new THREE.Mesh(CBG,CMT);m.position.set(r.x,r.y+.5,r.z);const l=new THREE.Mesh(LBG,CLT);l.position.y=.38;const b=new THREE.Mesh(BBG,CBM);b.position.y=7;m.add(l,b);scene.add(m);r.m=m}}
function hideCr(c){for(const r of crates(c.cx,c.cz))if(r.m){scene.remove(r.m);r.m=null}}
function nearCr(x,z,r){let best=null,bd=r;const cx=Math.floor(x/16),cz=Math.floor(z/16);for(let a=-2;a<=2;a++)for(let b=-2;b<=2;b++)for(const c of crates(cx+a,cz+b)){const d=Math.hypot(c.x-x,c.z-z);if(d<bd){bd=d;best=c}}return best}
function loot(f,r){const msg=[];for(const it of r.loot){if(it==='ammo'){f.ammo+=24;msg.push('+24 ammo')}else if(it==='bandage'){if(f.isP)BR.bd++;else f.hp=Math.min(100,f.hp+25);msg.push('🩹')}else if(it==='medkit'){if(f.isP)BR.mk++;else f.hp=Math.min(100,f.hp+60);msg.push('💊')}else if(it==='vest'){f.sh=Math.min(100,f.sh+40);msg.push('🛡️+40')}else{f.has[it]=1;msg.push(WP[it].e+' '+WP[it].n);if(f.isP&&BR.wp==='fists')brSel(WL.indexOf(it))}}
if(!f.isP)drawBar(f.bar,f.hp,f.sh);puff(r.x,r.z,0xffd24a);if(r.m){scene.remove(r.m);r.m=null}const a=crates(Math.floor(r.x/16),Math.floor(r.z/16)),i=a.indexOf(r);if(i>=0)a.splice(i,1);if(f.isP){toast('📦 '+msg.join(' '));sfx('buy')}}
// ---- fighters, bots, combat
const PL={isP:1,n:'You',hp:100,sh:0,ammo:0,mag:12,has:{fists:1}},fighters=[],NM=['Barley','Turnip','Radish','Clover','Pumpkin','Wheat','Rye','Beet','Maize','Basil','Acorn','Thistle','Fern','Moss','Poppy','Olive','Sage','Hazel','Juniper'];
const pos=f=>f.isP?pl:f;
function mkBar(){const c=document.createElement('canvas');c.width=64;c.height=10;const s=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(c),transparent:true,depthTest:false}));s.scale.set(1.6,.25,1);s.renderOrder=6;s.userData.c=c;return s}
function drawBar(s,hp,sh){const x=s.userData.c.getContext('2d');x.clearRect(0,0,64,10);x.fillStyle='#000';x.fillRect(0,0,64,10);x.fillStyle='#e33';x.fillRect(1,1,62*Math.max(0,hp)/100,8);if(sh>0){x.fillStyle='#4af';x.fillRect(1,1,62*sh/100,3)}s.material.map.needsUpdate=true}
PL.bar=mkBar();PL.bar.position.set(0,2.2,0);
const chute=new THREE.Group();box(2.4,.15,2.4,0xff5555,0,3.4,0,chute);box(1.2,.15,1.2,0xffffff,0,3.55,0,chute);[-.5,.5].forEach(x=>box(.04,2.2,.04,0xeeeeee,x,2.3,0,chute));
function bm_(b){if(b.wm&&b.wm.parent)b.wm.parent.remove(b.wm);const h=new THREE.Group();h.position.set(0,-.5,.05);h.rotation.x=Math.PI;if(b.wp!=='fists')h.add(mkWeapon(b.wp));b.g.userData.A[1].add(h);b.wm=h}
function mkBot(i,x,z){const C=()=>Math.random()*0xffffff|0,g=mkNPC(0xc99872,C(),C(),0x333344,h=>box(.54,.14,.54,C(),0,.56,0,h));
const tg=mkText('🤖 '+NM[i],'#000a',256,64,2.2,.55);tg.position.set(0,2.75,0);g.add(tg);const bar=mkBar();bar.position.set(0,2.35,0);g.add(bar);scene.add(g);
const w0=['fists','fists','sword','pistol','crossbow'][Math.random()*5|0],b={n:NM[i],g,bar,tg,x,y:55+Math.random()*25,z,vx:R(-3,3),vz:R(-3,3),hp:100,sh:0,has:{fists:1,[w0]:1},wp:w0,ammo:30+(Math.random()*30|0),cd:1+Math.random(),air:1,acc:R(.4,.8),sd:Math.random()<.5?1:-1,vis:30,fy:0,wt:0,sw:0,ph:0,wcd:0};
drawBar(bar,100,0);fighters.push(b);bm_(b);return b}
function los(a,e){const p=pos(e);for(let i=1;i<6;i++){const t=i/6;if(T(a.x+(p.x-a.x)*t,a.z+(p.z-a.z)*t)>a.y+1.5+(p.y-a.y)*t)return 0}return 1}
function mvTo(b,tx,tz,sp,dt){let dx=tx-b.x,dz=tz-b.z;const d=Math.hypot(dx,dz);if(d<.3)return 0;dx/=d;dz/=d;
for(const a of[0,.8,-.8,1.6,-1.6]){const c=Math.cos(a),s=Math.sin(a),mx=dx*c-dz*s,mz=dx*s+dz*c,nx=b.x+mx*sp*dt,nz=b.z+mz*sp*dt;if(T(nx,nz)-b.y<=1.25&&!trunk(Math.floor(nx),Math.floor(nz))){b.x=nx;b.z=nz;b.fy=Math.atan2(mx,mz);return 1}}return 0}
function pickWp(b,d){let w='fists';if(d>3.5&&b.ammo>0&&b.has.pistol)w='pistol';else if(d>3.5&&b.ammo>0&&b.has.crossbow)w='crossbow';else if(b.has.sword)w='sword';if(w!==b.wp){b.wp=w;bm_(b)}}
function botAtk(b,e,d){const w=WP[b.wp];if(w.m==='melee'){if(d>w.rg+.5)return;b.cd=w.cd*1.3;b.sw=.28;dmg(e,w.d*.8,b)}else{if(b.ammo<=0||d>w.rg-5)return;b.ammo--;b.cd=w.cd*(1.2+Math.random()*.8);const p=pos(e);shoot(b,w,p.x-b.x,p.y+1.1-(b.y+1.3),p.z-b.z,(1-b.acc)*.22+.02,.8)}}
function botAI(b,dt){const U=b.g.userData;
if(b.air){b.y-=9*dt;b.x+=b.vx*dt;b.z+=b.vz*dt;const g=T(b.x,b.z);if(b.y<=g){b.y=g;b.air=0}b.g.position.set(b.x,b.y,b.z);return}
b.cd-=dt;b.wcd-=dt;let en=null,ed=1e9;
for(const f of fighters){if(f===b||f.dead||f.air||(f.isP&&BR.drop))continue;const p=pos(f),d=Math.hypot(p.x-b.x,p.z-b.z);if(d<ed&&d<b.vis&&(d<5||los(b,f))){ed=d;en=f}}
if(en&&b.wcd<=0){b.wcd=.5;pickWp(b,ed)}
const gx=Z.shr?Z.tx:Z.cx,gz=Z.shr?Z.tz:Z.cz,gr=Z.shr?Z.tr:Z.r;let mvd=0;
if(Math.hypot(b.x-gx,b.z-gz)>gr-6)mvd=mvTo(b,gx,gz,4.4,dt);
else if(en){const w=WP[b.wp],p=pos(en),pf=w.m==='melee'?1.5:9;if(ed>pf+1)mvd=mvTo(b,p.x,p.z,3.9,dt);else if(ed<pf-3)mvd=mvTo(b,b.x-(p.x-b.x),b.z-(p.z-b.z),3,dt);else mvd=mvTo(b,b.x+(p.z-b.z)*b.sd,b.z-(p.x-b.x)*b.sd,2.4,dt)}
else{const c=nearCr(b.x,b.z,45);if(c)mvd=mvTo(b,c.x,c.z,4,dt);else{b.wt-=dt;if(b.wt<=0||Math.hypot(b.tx-b.x,b.tz-b.z)<2){b.wt=R(4,9);const a=R(0,6.28),r=Math.min(R(10,35),gr*.8);b.tx=gx+Math.cos(a)*r;b.tz=gz+Math.sin(a)*r}mvd=mvTo(b,b.tx,b.tz,3.4,dt)}}
const c=nearCr(b.x,b.z,1.7);if(c)loot(b,c);
if(en){const p=pos(en);b.fy=Math.atan2(p.x-b.x,p.z-b.z);if(b.cd<=0)botAtk(b,en,ed)}
b.y+=(T(b.x,b.z)-b.y)*Math.min(1,dt*12);
b.ph+=mvd?dt*9:0;const sw=mvd?Math.sin(b.ph)*.7:0;U.L[0].rotation.x=sw;U.L[1].rotation.x=-sw;U.A[0].rotation.x=-sw;b.sw=Math.max(0,b.sw-dt);
U.A[1].rotation.x=b.sw>0?-.8-1.2*Math.sin(b.sw*11):(WP[b.wp].m==='rng'?-1.45:b.wp==='fists'?sw:-.7);
b.g.position.set(b.x,b.y,b.z);b.g.rotation.y+=(((b.fy-b.g.rotation.y+Math.PI*3)%(Math.PI*2))-Math.PI)*Math.min(1,dt*10);
const dp=Math.hypot(b.x-pl.x,b.z-pl.z);b.g.visible=dp<120;b.tg.visible=dp<28}
const PGB=new THREE.BoxGeometry(.07,.07,.6),PMB=new THREE.MeshBasicMaterial({color:0xffe066}),PMC=new THREE.MeshBasicMaterial({color:0x8b5a2b}),PJ=[];
function shoot(f,w,dx,dy,dz,sp,dm){const l=Math.hypot(dx,dy,dz)||1;dx=dx/l+R(-sp,sp);dy=dy/l+R(-sp,sp)*.5;dz=dz/l+R(-sp,sp);const l2=Math.hypot(dx,dy,dz);dx/=l2;dy/=l2;dz/=l2;
const p=pos(f),m=new THREE.Mesh(PGB,w===WP.crossbow?PMC:PMB);m.position.set(p.x+dx*.8,p.y+1.3+dy*.8,p.z+dz*.8);m.lookAt(m.position.x+dx,m.position.y+dy,m.position.z+dz);scene.add(m);
PJ.push({m,vx:dx*w.sp,vy:dy*w.sp,vz:dz*w.sp,d:w.d*dm,o:f,life:w.rg/w.sp+.3,g:w===WP.crossbow?5:0});if(f.isP||Math.hypot(p.x-pl.x,p.z-pl.z)<40)snd(w===WP.pistol?700:300,.09,'square',.1,.4)}
function pjTick(dt){for(let i=PJ.length-1;i>=0;i--){const q=PJ[i],n=Math.max(1,Math.ceil(Math.hypot(q.vx,q.vz)*dt/.5));let dead=0;
for(let s=0;s<n&&!dead;s++){const h=dt/n,p=q.m.position;q.vy-=q.g*h;p.x+=q.vx*h;p.y+=q.vy*h;p.z+=q.vz*h;const t=T(p.x,p.z);
if(p.y<t||(p.y<t+4&&trunk(Math.floor(p.x),Math.floor(p.z)))){dead=1;break}
for(const f of fighters){if(f===q.o||f.dead||f.air)continue;const e=pos(f);if(Math.abs(e.x-p.x)<.55&&Math.abs(e.z-p.z)<.55&&p.y>e.y&&p.y<e.y+1.9){dmg(f,q.d,q.o);dead=1;break}}}
q.life-=dt;if(dead||q.life<=0){scene.remove(q.m);PJ.splice(i,1)}}}
function dmg(t,a,from){if(t.dead||BR.over||t.air||(t.isP&&BR.drop))return;const s=Math.min(t.sh,a);t.sh-=s;a-=s;t.hp-=a;if(t.isP){BR.hurt=.6;sfx('err')}else drawBar(t.bar,t.hp,t.sh);if(t.hp<=0)die(t,from)}
function zdmg(t,a){if(t.dead||BR.over||t.air||(t.isP&&BR.drop))return;t.hp-=a;if(t.isP)BR.hurt=Math.max(BR.hurt||0,.35);else if(Math.abs((t.lh??100)-t.hp)>4){t.lh=t.hp;drawBar(t.bar,t.hp,t.sh)}if(t.hp<=0)die(t,null)}
function die(t,by){t.dead=1;const al=fighters.filter(f=>!f.dead).length;if(by&&by.isP&&!t.isP)BR.kills++;
if(t.isP){endBR(0,al+1);return}
scene.remove(t.g);puff(t.x,t.z,0xff4040);crates(Math.floor(t.x/16),Math.floor(t.z/16)).push({x:t.x,z:t.z,y:T(t.x,t.z),loot:rollLoot(2),m:null});
toast('☠ '+(by?by.isP?'You':by.n:'The zone')+' eliminated '+t.n+' · '+al+' left');if(al===1&&!PL.dead)endBR(1,1)}
// ---- safe zone
const RS=[160,110,72,45,26,12,4,1.5],DPS=[1,2,3.5,5,8,12,16,22],Z={};
const zmA=new THREE.Mesh(new THREE.CylinderGeometry(1,1,120,48,1,true),new THREE.MeshBasicMaterial({color:0x2a7bff,transparent:true,opacity:.28,side:THREE.DoubleSide,depthWrite:false,fog:false})),zmB=new THREE.Mesh(new THREE.CylinderGeometry(1,1,120,48,1,true),new THREE.MeshBasicMaterial({color:0xffffff,wireframe:true,transparent:true,opacity:.35,fog:false}));
function zNext(){const p=Math.min(Z.p+1,RS.length-1);Z.sx=Z.cx;Z.sz=Z.cz;Z.sr=Z.r;Z.tr=RS[p];const a=R(0,6.28),d=Math.random()*Math.max(0,Z.sr-Z.tr)*.85;Z.tx=Z.sx+Math.cos(a)*d;Z.tz=Z.sz+Math.sin(a)*d}
function zTick(dt){Z.t+=dt;if(Z.t>=60){Z.t-=60;Z.cx=Z.tx;Z.cz=Z.tz;Z.r=Z.tr;Z.p=Math.min(Z.p+1,RS.length-1);Z.shr=0;zNext();toast('🔵 Zone closed · phase '+(Z.p+1)+' · '+DPS[Z.p]+' dmg/s outside');sfx('event')}
Z.shr=Z.t>=40;if(Z.shr){const s=(Z.t-40)/20;Z.cx=Z.sx+(Z.tx-Z.sx)*s;Z.cz=Z.sz+(Z.tz-Z.sz)*s;Z.r=Z.sr+(Z.tr-Z.sr)*s}
zmA.position.set(Z.cx,40,Z.cz);zmA.scale.set(Z.r,1,Z.r);zmB.position.set(Z.tx,40,Z.tz);zmB.scale.set(Z.tr,1,Z.tr)}
// ---- player actions
function aim(rg,cs0){const fx=-Math.sin(yaw),fz=-Math.cos(yaw);let best=null,bs=cs0;for(const f of fighters){if(f.isP||f.dead||f.air)continue;const dx=f.x-pl.x,dz=f.z-pl.z,d=Math.hypot(dx,dz);if(d>rg||d<.1)continue;const cs=(dx*fx+dz*fz)/d;if(cs>bs){bs=cs;best=f}}
return best?[best.x-pl.x,best.y+1.1-(pl.y+1.3),best.z-pl.z,best]:[fx,0,fz,null]}
function brAtk(){const w=WP[BR.wp];if(BR.over||BR.drop||BR.cd>0||BR.rl>0)return;const a=aim(w.rg,w.m==='melee'?.6:.93);pl.ry=Math.atan2(a[0],a[2]);
if(w.m==='melee'){BR.cd=w.cd;BR.sw=.28;snd(200,.1,'sawtooth',.12,.5);for(const f of fighters){if(f.isP||f.dead||f.air)continue;const dx=f.x-pl.x,dz=f.z-pl.z,d=Math.hypot(dx,dz);if(d<w.rg+.5&&(d<1||(dx*Math.sin(pl.ry)+dz*Math.cos(pl.ry))/d>.4))dmg(f,w.d,PL)}}
else{if(BR.wp==='pistol'){if(PL.mag<=0){if(PL.ammo>0){BR.rl=1.4;toast('🔄 Reloading…')}else toast('No ammo!');return}PL.mag--}else{if(PL.ammo<=0)return toast('No ammo!');PL.ammo--}BR.cd=w.cd;shoot(PL,w,a[0],a[1],a[2],.01,1)}}
function brRel(){if(BR.wp==='pistol'&&PL.mag<12&&PL.ammo>0&&BR.rl<=0){BR.rl=1.4;toast('🔄 Reloading…')}}
function brHeal(){if(BR.over)return;if(PL.hp>=100)return toast('Already at full health');if(BR.mk>0&&PL.hp<=60){BR.mk--;PL.hp=Math.min(100,PL.hp+75)}else if(BR.bd>0){BR.bd--;PL.hp=Math.min(100,PL.hp+25)}else if(BR.mk>0){BR.mk--;PL.hp=Math.min(100,PL.hp+75)}else return toast('No heals! Find 📦 crates');sfx('buy');puff(pl.x,pl.z,0x6dff6a)}
function brSel(i){const k=WL[i];if(!k)return;if(!PL.has[k])return toast('🔒 '+WP[k].n+' not found yet · buy it at the ⚔️ Weapon Shop');BR.wp=k;BR.rl=0;sfx('click');brModel()}
function brModel(){const A=me.userData.L[3];if(BR.wm&&BR.wm.parent)BR.wm.parent.remove(BR.wm);const h=new THREE.Group();h.position.set(0,-.5,.05);h.rotation.x=Math.PI;if(BR.wp!=='fists')h.add(mkWeapon(BR.wp));A.add(h);BR.wm=h;BR.wk=BR.wp+'|'+A.id}
function mspd(){return BR.on?(BR.drop?9:(RH(Math.floor(pl.x),Math.floor(pl.z))<SEA?4.6:7.5)):7}
// ---- HUD
const fmt=s=>{s=Math.max(0,Math.ceil(s));return(s/60|0)+':'+String(s%60).padStart(2,'0')};
function brHud(){const al=fighters.filter(f=>!f.dead).length,gx=(Z.shr?Z.tx:Z.cx)-pl.x,gz=(Z.shr?Z.tz:Z.cz)-pl.z,fx=-Math.sin(yaw),fz=-Math.cos(yaw);
$('bri').textContent='👥 '+al+'/20  ☠ '+BR.kills;$('brz').textContent=(Z.shr?'⚠ Closing '+fmt(60-Z.t):'🔵 Closes in '+fmt(40-Z.t))+' · P'+(Z.p+1);
$('ba').style.transform='rotate('+Math.atan2(-gx*fz+gz*fx,gx*fx+gz*fz)+'rad)';$('bd').textContent=' '+Math.round(Math.hypot(gx,gz))+'m';
$('bhp').firstElementChild.style.width=Math.max(0,PL.hp)+'%';$('bsh').firstElementChild.style.width=PL.sh+'%';$('hpt').textContent='❤ '+Math.ceil(Math.max(0,PL.hp))+(PL.sh>0?'  🛡 '+Math.ceil(PL.sh):'')+'   🩹'+BR.bd+' 💊'+BR.mk;
$('brhot').innerHTML=WL.map((k,i)=>{const w=WP[k],inf=k==='pistol'?PL.mag+'/'+PL.ammo:k==='crossbow'?PL.ammo:'';return`<div class="slot ${BR.wp===k?'on':''} ${PL.has[k]?'':'dim'}" onpointerdown="brSel(${i})"><s>${i+1}</s><b>${w.e}</b><i>${inf}</i></div>`}).join('');
if(BR.wk!==BR.wp+'|'+me.userData.L[3].id)brModel();if(!PL.bar.parent)me.add(PL.bar);const k=PL.hp+'/'+PL.sh;if(PL.lh!==k){PL.lh=k;drawBar(PL.bar,PL.hp,PL.sh)}}
// ---- main BR tick
function brTick(dt){
if(BR.over){pjTick(dt);return}
chunks(2);BR.sc=(BR.sc||0)-dt;if(BR.sc<=0){BR.sc=.4;syncCr()}
for(const c of CH.values())for(const r of crates(c.cx,c.cz))if(r.m)r.m.rotation.y+=dt;
zTick(dt);BR.cd-=dt;BR.sw-=dt;
if(BR.rl>0){BR.rl-=dt;if(BR.rl<=0){const n=Math.min(12-PL.mag,PL.ammo);PL.mag+=n;PL.ammo-=n;toast('🔫 Reloaded')}}
if(BR.drop){if(pl.g){BR.drop=0;me.remove(chute);toast('🪂 Landed! Grab 📦 crates & stay in the 🔵 zone')}else if(!chute.parent)me.add(chute)}
if((BR.fire||keys.KeyF)&&!BR.drop)brAtk();
const c=nearCr(pl.x,pl.z,1.8);if(c&&!BR.drop)loot(PL,c);
for(const f of fighters){if(f.dead)continue;if(!f.isP)botAI(f,dt);const p=pos(f);if(Math.hypot(p.x-Z.cx,p.z-Z.cz)>Z.r)zdmg(f,DPS[Z.p]*dt)}
pjTick(dt);BR.hurt=Math.max(0,(BR.hurt||0)-dt*1.2);$('hurt').style.opacity=BR.hurt;
const L=me.userData.L;L[3].rotation.x=BR.sw>0?-.9-1.3*Math.sin(Math.max(0,BR.sw)*11):(WP[BR.wp].m==='rng'?-1.45:BR.wp==='fists'?L[3].rotation.x:-.6);
BR.hu=(BR.hu||0)-dt;if(BR.hu<=0){BR.hu=.15;brHud()}}
// ---- enter / exit
const UIB=['brh','brp2','brhot'];
function enterBR(){closeP();if(BR.on)return;fishEnd();CH.forEach(c=>{hideCr(c);scene.remove(c.m);c.m.geometry.dispose()});CH.clear();HC_.clear();CR.clear();
SEED=Math.random()*1e6|0;Object.assign(BR,{on:1,over:0,kills:0,hurt:0,cd:0,rl:0,sw:0,bd:1,mk:0,wp:'fists',fire:0,drop:1,sure:0});
Object.assign(PL,{hp:100,sh:0,dead:0,ammo:20+(S.ammo||0),mag:12,has:Object.assign({fists:1},S.wp)});PL.lh=null;
Object.assign(Z,{cx:BX,cz:BX,r:RS[0],p:0,t:0,shr:0});zNext();scene.add(zmA,zmB);
let a=R(0,6.28),r=R(10,RS[0]*.7);pl.x=BX+Math.cos(a)*r;pl.z=BX+Math.sin(a)*r;pl.y=70;pl.sy=70;pl.vy=0;pl.g=0;
fighters.length=0;fighters.push(PL);NM.sort(()=>Math.random()-.5);for(let i=0;i<19;i++){a=R(0,6.28);r=Math.sqrt(Math.random())*RS[0]*.9;mkBot(i,BX+Math.cos(a)*r,BX+Math.sin(a)*r)}
chunks(30);syncCr();puff(pl.x,pl.z,0xb8c4ff);
hk='';if(hm&&hm.parent)hm.parent.remove(hm);hm=null;HC=0;brModel();me.add(PL.bar,chute);
$('hot').style.display=$('bar').style.display=$('fish').style.display='none';UIB.forEach(i=>$(i).style.display='flex');['atk','heal','rel'].forEach(i=>$(i).style.display='block');
scene.fog.near=30;scene.fog.far=95;sfx('event');toast('🪂 Dropping in! Find 📦 crates · stay inside the 🔵 zone · last farmer wins');brHud()}
function endBR(win,place){BR.over=1;const k=BR.kills,coins=k*60+(21-place)*15+(win?1500:0);S.m+=coins;S.brs.g++;S.brs.k+=k;if(win)S.brs.w++;save();
$('brend').innerHTML=`<h1 style="margin:0;color:${win?'#ffd24a':'#ff6a6a'}">${win?'🏆 WINNER WINNER!':'☠ ELIMINATED'}</h1><div>Placement <b>#${place}</b> / 20 · ☠ ${k} kills<br>+${fm(coins)}🪙</div><button onclick="leaveBR()">🏝 Back to island</button><button onclick="leaveBR(0,1)">⚔ Play again</button>`;$('brend').style.display='flex';sfx(win?'hatch':'err')}
function leaveBR(ask,again){if(ask&&!BR.over&&!BR.sure){BR.sure=1;toast('Tap 🚪 again to quit the match');setTimeout(()=>BR.sure=0,2500);return}
BR.on=0;fighters.forEach(f=>{if(!f.isP&&f.g)scene.remove(f.g)});fighters.length=0;PJ.forEach(q=>scene.remove(q.m));PJ.length=0;CH.forEach(c=>{hideCr(c);scene.remove(c.m);c.m.geometry.dispose()});CH.clear();CR.clear();
scene.remove(zmA,zmB);me.remove(PL.bar,chute);if(BR.wm&&BR.wm.parent)BR.wm.parent.remove(BR.wm);BR.wm=null;BR.wk='';BR.fire=0;
UIB.forEach(i=>$(i).style.display='none');['atk','heal','rel'].forEach(i=>$(i).style.display='none');$('brend').style.display='none';$('hurt').style.opacity=0;$('hot').style.display=$('bar').style.display='';
scene.fog.near=40;scene.fog.far=120;tp('garden');hk='';hot();if(again)setTimeout(enterBR,60)}
{const a=$('atk');a.addEventListener('pointerdown',e=>{e.preventDefault();BR.fire=1});['pointerup','pointercancel','pointerleave'].forEach(n=>a.addEventListener(n,()=>BR.fire=0));$('heal').onclick=brHeal;$('rel').onclick=brRel}

// ---------- loop
loadGame();const clk=new THREE.Clock();hot();
(function loop(){requestAnimationFrame(loop);const dt=Math.min(clk.getDelta(),.1);
let ix=mv.x+(keys.KeyD||keys.ArrowRight?1:0)-(keys.KeyA||keys.ArrowLeft?1:0),iz=mv.z+(keys.KeyS||keys.ArrowDown?1:0)-(keys.KeyW||keys.ArrowUp?1:0);const l=Math.hypot(ix,iz);
if(l>.05){const n=Math.min(l,1)/l;ix*=n;iz*=n;const s=Math.sin(yaw),c=Math.cos(yaw),wx=ix*c+iz*s,wz=-ix*s+iz*c;slide(wx*mspd()*dt,wz*mspd()*dt);pl.ry=Math.atan2(wx,wz);const lw=walk;walk+=dt*10;if((walk/Math.PI|0)!==(lw/Math.PI|0))sfx('step')}
phys(dt);me.position.set(pl.x,pl.sy,pl.z);me.rotation.y+=(((pl.ry-me.rotation.y+Math.PI*3)%(Math.PI*2))-Math.PI)*Math.min(1,dt*12);
const sw=l>.05?Math.sin(walk)*.7:0,L=me.userData.L;L[0].rotation.x=sw;L[1].rotation.x=-sw;L[2].rotation.x=-sw;L[3].rotation.x=FS.st?-1.3-(FS.st===2?Math.sin(now*40)*.15:0):sw;if(!FS.st){if(HC===1)L[2].rotation.x=L[3].rotation.x=-1.45;else if(HC===2)L[3].rotation.x=-1+sw*.15}
weather(dt);env(dt);particles(dt);portalTick(dt);if(BR.on)brTick(dt);else{npcUpdate(dt);fishTick(dt,l>.05)}
const spd=1+bonus('grow')+S.spr*.2+(ev&&(ev.k==='rain'||ev.k==='thunder')?.25:0)-(ev&&ev.k==='winter'?.1:0);
const ksz=Math.min(1+bonus('kg')*.6,1.8);plots.forEach(o=>{const p=o.p;if(!p)return;p.cd=(p.cd||0)-dt;if(p.show){p.sh-=dt;p.lt=(p.lt||0)-dt;if(p.sh<=0){p.show=0;lab(p)}else if(p.lt<=0){p.lt=.4;lab(p)}}p.prog=Math.min(1,p.prog+dt*spd/CROPS[p.type].t);if(p.prog>=1&&!p.rd){p.rd=1;lab(p)}if(p.b==='rainbow'){const c=p.m.userData.mat;c.color.setHSL((now*.4+o.x*.08)%1,.85,.55);c.emissive.copy(c.color).multiplyScalar(.3)}const s=p.m.userData.base*ksz*(.15+.85*p.prog);p.age=(p.age||0)+dt;p.m.scale.setScalar(s*(p.age<.4?1+Math.sin(p.age/.4*Math.PI)*.4:1)*(p.prog>=1?1+Math.sin(now*4+o.x)*.04:1));if(p.prog>=1)p.m.rotation.y=Math.sin(now*2+o.z)*.15});
petMs.forEach((m,k)=>{const U=m.userData;let mg=0;if(U.w>0)U.w-=dt;else{const dx=U.tx-m.position.x,dz=U.tz-m.position.z,d=Math.hypot(dx,dz);if(d<.25){U.w=R(1.5,5);U.tx=R(GB.x0,GB.x1);U.tz=R(GB.z0,GB.z1)}else{const s=Math.min(d,1.8*dt);m.position.x+=dx/d*s;m.position.z+=dz/d*s;mg=.7;m.rotation.y+=(((Math.atan2(dx,dz)-m.rotation.y+Math.PI*3)%(Math.PI*2))-Math.PI)*Math.min(1,dt*8)}}m.position.x=cl(m.position.x,GB.x0,GB.x1);m.position.z=cl(m.position.z,GB.z0,GB.z1);petAnim(m,k,mg,dt)});
npcs.forEach(n=>{const U=n.userData,dx=pl.x-U.wx,dz=pl.z-U.wz,d=Math.hypot(dx,dz);U.hd.rotation.y+=((d<14?cl(Math.atan2(dx,dz),-.9,.9):0)-U.hd.rotation.y)*Math.min(1,dt*5);U.A[1].rotation.z=d<8?2.7+Math.sin(now*9)*.35:U.A[1].rotation.z*(1-Math.min(1,dt*6))});
cam.position.set(pl.x+Math.sin(yaw)*Math.cos(pit)*dist,Math.sin(pit)*dist+1.2+pl.sy,pl.z+Math.cos(yaw)*Math.cos(pit)*dist);cam.lookAt(pl.x,1.2+pl.sy,pl.z);
rd.render(scene,cam)})();
</script></body></html>
