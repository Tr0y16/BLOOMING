
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Magical Blooming Flowers</title>
<style>
body{
    margin:0;
    font-family: Arial, sans-serif;
    text-align:center;
    background: linear-gradient(#ffe6f2,#fff);
    overflow-x:hidden;
}

/* HEADER */
header{
    background:#ff4d88;
    color:white;
    padding:20px;
    font-size:28px;
}

/* MAIN SECTION */
section{
    padding:80px 20px;
}

/* FLOWER CONTAINER */
.flower{
    width:120px;
    height:120px;
    margin:50px auto;
    position:relative;
    transform-style: preserve-3d;
}

.petal{
    width:60px;
    height:60px;
    background:pink;
    border-radius:50%;
    position:absolute;
    top:0;
    left:0;
    transform-origin:30px 30px;
    transition: transform 0.3s;
}

.petal:hover{
    transform: scale(1.3) rotate(20deg);
}

.center{
    width:40px;
    height:40px;
    background:yellow;
    border-radius:50%;
    position:absolute;
    top:10px;
    left:10px;
}

/* MESSAGE */
.message{
    font-size:22px;
    margin-top:30px;
    color:#333;
}

button{
    padding:12px 25px;
    font-size:18px;
    border:none;
    background:#ff4d88;
    color:white;
    border-radius:8px;
    cursor:pointer;
}

button:hover{
    background:#e6005c;
}

/* FOOTER */
footer{
    margin-top:50px;
    background:#ff4d88;
    color:white;
    padding:15px;
}

/* FLOATING ELEMENTS */
.floating{
    position:absolute;
    font-size:24px;
    animation:float linear infinite;
    pointer-events:none;
}

@keyframes float{
    0%{ transform: translateY(0) rotate(0deg); opacity:1; }
    100%{ transform: translateY(-400px) rotate(360deg); opacity:0; }
}
</style>
</head>
<body>

<header>
🌹 Magical Blooming Flowers
</header>

<section>
<h1>Click the button to bloom flowers</h1>
<button onclick="bloomFlowers()">Bloom!</button>
<div id="flowerArea"></div>
<div class="message" id="msg"></div>
</section>

<footer>
Made with love 💖
</footer>

<script>
// Function to create a single flower
function createFlower(){
    let flower = document.createElement("div");
    flower.className = "flower";
    for(let i=0;i<6;i++){
        let petal = document.createElement("div");
        petal.className = "petal";
        petal.style.transform = `rotate(${i*60}deg) translateY(-60px)`;
        flower.appendChild(petal);
    }
    let center = document.createElement("div");
    center.className = "center";
    flower.appendChild(center);
    return flower;
}

// Function to create floating petals/hearts
function floatingElement(symbol){
    let el = document.createElement("div");
    el.className="floating";
    el.innerHTML=symbol;
    el.style.left=Math.random()*window.innerWidth+"px";
    el.style.top=window.innerHeight+"px";
    el.style.fontSize=(20+Math.random()*20)+"px";
    el.style.animationDuration=(4+Math.random()*4)+"s";
    document.body.appendChild(el);
    setTimeout(()=>el.remove(),8000);
}

// Bloom multiple flowers in sequence
function bloomFlowers(){
    let area = document.getElementById("flowerArea");
    area.innerHTML="";
    document.getElementById("msg").innerHTML="";
    let messages = [
        "Love is like a flower that grows slowly and beautifully. It starts small but becomes stronger with care and attention.",
        "Just like flowers, you make the world beautifulJust like flowers need water and sunlight, love needs trust, kindness, and patience to grow well.",
        "Just like flowers need water and sunlight, love needs trust, kindness, and patience to grow well."
    ];
    messages.forEach((msg,i)=>{
        setTimeout(()=>{
            let f = createFlower();
            area.appendChild(f);
            document.getElementById("msg").innerHTML = msg;
            for(let j=0;j<5;j++){
                floatingElement("🌸");
                floatingElement("💖");
            }
        }, i*1500);
    });
}
</script>

</body>
</html>
