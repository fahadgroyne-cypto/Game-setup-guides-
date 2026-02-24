# Game-setup-guides-
Learn how to set up ur gaming emulator 

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fahad Groyne Gaming Portal</title>

<style>
body{
margin:0;
font-family:Arial;
background:#0f2027;
color:white;
}

.page{display:none;padding:20px;}
.active{display:block;}

nav{
background:black;
padding:10px;
display:flex;
gap:10px;
flex-wrap:wrap;
}

button{
padding:8px 15px;
border:none;
border-radius:6px;
cursor:pointer;
background:#FFD700;
font-weight:bold;
}

input,select,textarea{
width:100%;
padding:8px;
margin:5px 0;
border-radius:6px;
border:none;
}

.card{
background:#1c1c1c;
padding:15px;
margin:10px 0;
border-radius:10px;
}

h1,h2,h3{color:#FFD700;}
ul{columns:2;}
</style>
</head>

<body>

<!-- THANK YOU PAGE -->
<div id="intro" class="page active">
<h1>Thank You For Downloading</h1>
<p>This app was developed by <b>Fahad Groyne</b>.</p>
<button onclick="goLogin()">Continue</button>
</div>

<!-- LOGIN -->
<div id="login" class="page">
<h2>Login / Register</h2>
<input type="text" id="user" placeholder="Username">
<input type="password" id="pass" placeholder="Password">
<button onclick="login()">Enter Portal</button>
<p>Follow WhatsApp Channel:</p>
<a href="https://whatsapp.com/channel/0029Vb7jjtZLo4hnTZRnqW1n" target="_blank">
WhatsApp Channel
</a>
</div>

<!-- MAIN APP -->
<div id="app" class="page">

<nav>
<button onclick="show('dashboard')">Dashboard</button>
<button onclick="show('games')">Games</button>
<button onclick="show('compatibility')">Compatibility</button>
<button onclick="show('rating')">Ratings</button>
<button onclick="show('cloud')">Cloud Save</button>
<button onclick="show('settings')">Settings</button>
<button onclick="show('support')">Support</button>
<button onclick="show('developer')">Hire Dev</button>
</nav>

<!-- DASHBOARD -->
<div id="dashboard">
<h2>Admin Dashboard</h2>
<div class="card">
<p>Welcome: <span id="currentUser"></span></p>
<p>Developer: Fahad Groyne</p>
<p>Version: 2.0 Enterprise</p>
</div>
</div>

<!-- GAMES DATABASE -->
<div id="games">
<h2>Top 100 Games Per Emulator</h2>

<h3>PS2</h3>
<ul id="ps2"></ul>

<h3>PS3</h3>
<ul id="ps3"></ul>

<h3>PSP</h3>
<ul id="psp"></ul>

<p><b>Note:</b> Only use legally owned games.</p>
</div>

<!-- COMPATIBILITY -->
<div id="compatibility">
<h2>Compatibility Checker</h2>
<select id="emu">
<option>PPSSPP</option>
<option>PCSX2</option>
<option>RPCS3</option>
</select>
<input type="text" id="gameCheck" placeholder="Game Name">
<button onclick="checkGame()">Check</button>
<p id="result"></p>
</div>

<!-- RATING SYSTEM -->
<div id="rating">
<h2>Game Rating System</h2>
<input type="text" id="rateGame" placeholder="Game Name">
<select id="rateValue">
<option>1</option><option>2</option><option>3</option>
<option>4</option><option>5</option>
</select>
<button onclick="rate()">Submit Rating</button>
<ul id="ratingList"></ul>
</div>

<!-- CLOUD SAVE -->
<div id="cloud">
<h2>Cloud Save (Local Simulation)</h2>
<input type="text" id="saveGame" placeholder="Game Name">
<textarea id="saveProgress" placeholder="Progress details"></textarea>
<button onclick="saveProgress()">Save</button>
<ul id="saveList"></ul>
</div>

<!-- SETTINGS -->
<div id="settings">
<h2>Settings</h2>
<select onchange="theme(this.value)">
<option value="dark">Dark</option>
<option value="light">Light</option>
</select>

<h3>Music Player</h3>
<input type="file" id="musicFile" accept="audio/*">
<button onclick="playMusic()">Play</button>
<button onclick="pauseMusic()">Pause</button>
<audio id="audio"></audio>
</div>

<!-- SUPPORT -->
<div id="support">
<h2>Support & Social</h2>
<a href="https://www.instagram.com/channel/Aba9KPoJDIJ-im6Z/" target="_blank">Instagram Channel</a><br><br>
<a href="https://www.instagram.com/d.e.m.o.x_11" target="_blank">@d.e.m.o.x_11</a><br>
<a href="https://www.instagram.com/games_site_online" target="_blank">@games_site_online</a><br><br>
<a href="https://www.tiktok.com/@d.e.m.o.x_11" target="_blank">TikTok</a><br><br>
<a href="https://github.com/fahadgroyne-cypto" target="_blank">GitHub</a>
</div>

<!-- DEVELOPER PAGE -->
<div id="developer">
<h2>Request App Development</h2>
<textarea placeholder="Describe your app idea"></textarea>
<button onclick="alert('Request Sent Successfully!')">Submit</button>
</div>

</div>

<script>

function goLogin(){
hideAll();
document.getElementById("login").classList.add("active");
}

function login(){
let user=document.getElementById("user").value;
localStorage.setItem("user",user);
hideAll();
document.getElementById("app").classList.add("active");
document.getElementById("currentUser").innerText=user;
show("dashboard");
}

function hideAll(){
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
}

function show(id){
document.querySelectorAll("#app > div").forEach(d=>d.style.display="none");
document.getElementById(id).style.display="block";
}

function theme(mode){
if(mode=="light"){
document.body.style.background="white";
document.body.style.color="black";
}else{
document.body.style.background="#0f2027";
document.body.style.color="white";
}
}

function checkGame(){
document.getElementById("result").innerText=
"Compatibility depends on emulator version and PC specs.";
}

function rate(){
let game=document.getElementById("rateGame").value;
let value=document.getElementById("rateValue").value;
let list=document.getElementById("ratingList");
let li=document.createElement("li");
li.innerText=game+" - "+value+"/5";
list.appendChild(li);
}

function saveProgress(){
let game=document.getElementById("saveGame").value;
let prog=document.getElementById("saveProgress").value;
let list=document.getElementById("saveList");
let li=document.createElement("li");
li.innerText=game+" : "+prog;
list.appendChild(li);
}

document.getElementById("musicFile").addEventListener("change",function(){
let file=this.files[0];
if(file){
let url=URL.createObjectURL(file);
document.getElementById("audio").src=url;
}
});

function playMusic(){
document.getElementById("audio").play();
}

function pauseMusic(){
document.getElementById("audio").pause();
}

/* AUTO GENERATE TOP 100 */
let sample=[
"God of War","GTA Series","Final Fantasy","Metal Gear",
"Gran Turismo","Tekken","Resident Evil",
"Kingdom Hearts","Shadow of the Colossus","Call of Duty"
];

function fill(id){
let ul=document.getElementById(id);
for(let i=0;i<100;i++){
let li=document.createElement("li");
li.innerText=sample[i % sample.length]+" "+(i+1);
ul.appendChild(li);
}
}

fill("ps2");
fill("ps3");
fill("psp");

</script>

</body>
</html>
