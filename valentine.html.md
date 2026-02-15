<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
<title>For Shymoon 💖</title>  
  
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&family=Dancing+Script:wght@600;700&display=swap" rel="stylesheet">  
  
<style>  
*{margin:0;padding:0;box-sizing:border-box;}  
  
body{  
font-family:'Poppins',sans-serif;  
height:100vh;  
overflow:hidden;  
background:linear-gradient(135deg,#ffd6e8,#ff6f91,#ff1493);  
background-size:400% 400%;  
animation:bgMove 10s ease infinite;  
display:flex;  
justify-content:center;  
align-items:center;  
text-align:center;  
color:white;  
position:relative;  
}  
  
@keyframes bgMove{  
0%{background-position:0% 50%;}  
50%{background-position:100% 50%;}  
100%{background-position:0% 50%;}  
}  
  
.container{z-index:2;padding:20px;}  
  
.bear{  
font-size:70px;  
animation:bounce 2s infinite;  
}  
  
@keyframes bounce{  
0%,100%{transform:translateY(0);}  
50%{transform:translateY(-20px);}  
}  
  
h1{  
font-family:'Dancing Script',cursive;  
font-size:3rem;  
margin:15px 0;  
min-height:60px;  
}  
  
.subtitle{font-style:italic;margin-bottom:15px;}  
.closing{margin-top:10px;}  
  
.buttons{  
display:flex;  
justify-content:center;  
gap:40px;  
margin-top:25px;  
}  
  
#yesBtn{  
padding:15px 45px;  
font-size:1.2rem;  
border:none;  
border-radius:50px;  
background:linear-gradient(to right,#ff0000,#ff4d4d);  
color:white;  
cursor:pointer;  
transition:0.3s;  
box-shadow:0 0 20px rgba(255,0,0,0.6);  
}  
  
#yesBtn:hover{  
box-shadow:0 0 35px rgba(255,0,0,1);  
transform:scale(1.08);  
}  
  
#noBtn{  
padding:10px 25px;  
font-size:1rem;  
border-radius:50px;  
border:2px solid red;  
background:white;  
color:red;  
cursor:pointer;  
position:relative;  
}  
  
/* Floating Hearts */  
.heart{  
position:absolute;  
bottom:-50px;  
animation:floatUp linear infinite;  
}  
  
@keyframes floatUp{  
0%{transform:translateY(0);opacity:0;}  
10%{opacity:1;}  
90%{opacity:1;}  
100%{transform:translateY(-110vh);opacity:0;}  
}  
  
/* Celebration */  
.celebration{  
position:fixed;  
inset:0;  
display:flex;  
flex-direction:column;  
justify-content:center;  
align-items:center;  
background:linear-gradient(135deg,#ff6f91,#ff1493,#ff0000);  
z-index:20;  
display:none;  
}  
  
.yay{  
font-size:4rem;  
animation:pulse 1s infinite;  
}  
  
@keyframes pulse{  
0%,100%{transform:scale(1);}  
50%{transform:scale(1.2);}  
}  
  
.spin{  
font-size:60px;  
animation:spin 2s linear infinite;  
margin:15px 0;  
}  
  
@keyframes spin{  
from{transform:rotate(0deg);}  
to{transform:rotate(360deg);}  
}  
  
.confetti{  
position:fixed;  
width:10px;  
height:10px;  
animation:fall 4s linear forwards;  
}  
  
@keyframes fall{  
to{transform:translateY(100vh) rotate(720deg);opacity:0;}  
}  
</style>  
</head>  
<body>  
  
<div class="container" id="mainContent">  
<div class="bear">🐻</div>  
<h1 id="typingText"></h1>  
<div class="subtitle">From the moment you walked into my life, everything felt brighter 💕</div>  
<div class="closing">Every love story is beautiful, but ours is my favourite</div>  
  
<div class="buttons">  
<button id="yesBtn">Yes 💖</button>  
<button id="noBtn">No</button>  
</div>  
</div>  
  
<div class="celebration" id="celebration">  
<div class="yay">Yayyyy!!</div>  
<div class="spin">💍💞</div>  
<p>This is just the beginning of our beautiful story, Shymoon ❤️</p>  
</div>  
  
<!-- 🔥 THIS IS YOUR AUDIO LINE -->  
<audio id="bgMusic" src="lover.mp3" loop></audio>  
  
<script>  
  
/* Typing */  
const text="Will You Be My Valentine, Shymoon? 💖";  
const typing=document.getElementById("typingText");  
let i=0;  
function type(){  
if(i<text.length){  
typing.innerHTML+=text.charAt(i);  
i++;  
setTimeout(type,60);  
}}  
type();  
  
/* Floating Hearts */  
setInterval(()=>{  
const heart=document.createElement("div");  
heart.className="heart";  
heart.textContent="💖";  
heart.style.left=Math.random()*100+"vw";  
heart.style.fontSize=(20+Math.random()*30)+"px";  
heart.style.animationDuration=(4+Math.random()*4)+"s";  
document.body.appendChild(heart);  
setTimeout(()=>heart.remove(),8000);  
},500);  
  
/* No Button Escape */  
const noBtn=document.getElementById("noBtn");  
const yesBtn=document.getElementById("yesBtn");  
  
const messages=[  
"Nope, not an option!",  
"Try again!",  
"You sure about that?",  
"Not happening!",  
"Think again!"  
];  
let msgIndex=0;  
  
function moveButton(){  
const yesRect=yesBtn.getBoundingClientRect();  
let x,y;  
do{  
x=Math.random()*(window.innerWidth-noBtn.offsetWidth);  
y=Math.random()*(window.innerHeight-noBtn.offsetHeight);  
}  
while(  
x<yesRect.right &&  
x+noBtn.offsetWidth>yesRect.left &&  
y<yesRect.bottom &&  
y+noBtn.offsetHeight>yesRect.top  
);  
  
noBtn.style.position="fixed";  
noBtn.style.left=x+"px";  
noBtn.style.top=y+"px";  
noBtn.textContent=messages[msgIndex];  
msgIndex=(msgIndex+1)%messages.length;  
}  
  
noBtn.addEventListener("click",moveButton);  
noBtn.addEventListener("touchstart",moveButton);  
  
/* YES CLICK */  
yesBtn.addEventListener("click",()=>{  
document.getElementById("mainContent").style.display="none";  
document.getElementById("celebration").style.display="flex";  
document.getElementById("bgMusic").play(); // 🔥 PLAYS YOUR AUDIO  
createConfetti();  
});  
  
/* Confetti */  
function createConfetti(){  
for(let i=0;i<120;i++){  
const c=document.createElement("div");  
c.className="confetti";  
c.style.left=Math.random()*100+"vw";  
c.style.backgroundColor=`hsl(${Math.random()*360},100%,50%)`;  
document.body.appendChild(c);  
}  
}  
</script>  
  
</body>  
</html>  
