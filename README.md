<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Untuk Cacan 💖</title>

<style>
body{
    margin:0;
    font-family:'Segoe UI',sans-serif;
    overflow:hidden;
    background:radial-gradient(circle at top,#2a002a,#000);
    color:white;
}

/* background glow */
.bg{
    position:absolute;
    width:300px;
    height:300px;
    background:#ff66cc;
    filter:blur(120px);
    opacity:0.3;
    animation:move 12s infinite alternate;
}

@keyframes move{
    0%{top:10%; left:10%;}
    100%{top:60%; left:60%;}
}

/* center */
.center{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
}

/* password */
#lock{text-align:center}
input{
    padding:12px;
    border:none;
    border-radius:12px;
    text-align:center;
    font-size:16px;
}

/* amplop */
#envelope{
    font-size:70px;
    display:none;
    cursor:pointer;
    transition:0.5s;
}

/* text */
#text{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    width:85%;
    max-width:400px;
    text-align:center;
    font-size:17px;
    opacity:0;
}

/* animasi */
.show{animation:fadeIn 1s forwards}
.hide{animation:fadeOut 1s forwards}

@keyframes fadeIn{
    from{opacity:0; transform:translate(-50%,-40%)}
    to{opacity:1; transform:translate(-50%,-50%)}
}

@keyframes fadeOut{
    to{opacity:0; transform:translate(-50%,-60%)}
}

/* love */
.heart{
    position:absolute;
    color:#ff4da6;
    font-size:18px;
    animation:fall linear infinite;
}

@keyframes fall{
    100%{transform:translateY(110vh)}
}

/* ending */
#final{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%) scale(0);
    font-size:28px;
    color:#ff66cc;
    transition:1s;
}
</style>
</head>

<body>

<div class="bg"></div>
<div class="bg"></div>

<!-- password -->
<div id="lock" class="center">
    <h3>Masukkan kode rahasia 💖</h3>
    <input type="password" id="pass">
</div>

<!-- amplop -->
<div id="envelope" class="center">✉️</div>

<!-- text -->
<div id="text"></div>

<div id="final">I LOVE YOU CACAN 💖</div>

<!-- AUDIO (GANTI LINK INI DENGAN "Married Life") -->
<audio id="audio" loop>
<source src="MASUKKAN_LINK_MARRIED_LIFE_DISINI.mp3">
</audio>

<script>

let pass=document.getElementById("pass");
let lock=document.getElementById("lock");
let envelope=document.getElementById("envelope");
let audio=document.getElementById("audio");

// langsung ke amplop setelah password
pass.addEventListener("keyup",()=>{
    if(pass.value==="190426"){
        lock.style.display="none";
        envelope.style.display="block";
        audio.play().catch(()=>{});
    }
});

// klik amplop
envelope.onclick=()=>{
    envelope.style.transform="translate(-50%,-50%) scale(0)";
    setTimeout(()=>{
        envelope.style.display="none";
        mulai();
    },400);
};

// teks
let teks=[
"di saat cacan bobo aku lagi buat ini...",
"aku kangen banget sama cacan 💖",
"aku sayang banget sama cacan",
"pagi, can ☀️",
"semoga hari kamu penuh kebahagiaan",
"doain aku sehat selalu ya dan pastinya aku akan selalu ada untuk kamu",
"cacan jangan kecewain aku ya sayang aku percaya cacan adalah perempuan baik",
"ntah kenapa aku kangen khawatir dan semua perasaan aku campur aduk ke kamu",
"pasti kamu ngerti rasanya ketika seseorang sedang jatuh cinta 💞"
];

let i=0;
let text=document.getElementById("text");

function mulai(){
    tampil();
    hujanLove();
}

function tampil(){
    if(i<teks.length){
        text.innerHTML=teks[i];
        text.className="show";

        setTimeout(()=>{
            text.className="hide";
            i++;
            setTimeout(tampil,1000);
        },2500);
    }else{
        ending();
    }
}

// love klik
let count=0;

function hujanLove(){
    setInterval(()=>{
        let h=document.createElement("div");
        h.className="heart";
        h.innerHTML="❤";
        h.style.left=Math.random()*100+"vw";
        h.style.animationDuration=(4+Math.random()*2)+"s";

        h.onclick=()=>{
            count++;
            h.innerHTML="💖";
            if(count>=8){
                ending();
            }
        };

        document.body.appendChild(h);
        setTimeout(()=>h.remove(),6000);
    },400);
}

function ending(){
    document.getElementById("final").style.transform="translate(-50%,-50%) scale(1.2)";
}

</script>

</body>
</html>
