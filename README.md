# Angelinavalentines

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Angelina ❤️</title>

<style>
body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    font-family: Arial, sans-serif;
    text-align: center;
}

/* Falling hearts */
.heart {
    position: fixed;
    top: -10px;
    font-size: 20px;
    animation: fall linear infinite;
}

@keyframes fall {
    to { transform: translateY(110vh); }
}

/* Main text */
h1 {
    color: white;
    font-size: 3rem;
}

/* Buttons */
button {
    padding: 12px 25px;
    font-size: 18px;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    margin: 10px;
}

#yesBtn {
    background: #ff4d6d;
    color: white;
}

#noBtn {
    background: white;
    color: #ff4d6d;
    position: absolute;
}

/* Success screen */
#message {
    display: none;
    font-size: 3rem;
    color: white;
}

/* Real animated bear */
#bobu {
    display: none;
    margin-top: 20px;
}

#bobu img {
    width: 220px;
}
</style>
</head>

<body>

<!-- MUSIC -->
<audio id="music" loop>
    <source src="https://cdn.pixabay.com/audio/2022/02/23/audio_c8c8a73467.mp3" type="audio/mpeg">
</audio>

<div id="main">
    <h1>Angelina… will you be my Valentine? ❤️</h1>
    <button id="yesBtn">YES</button>
    <button id="noBtn">NO</button>
</div>

<div id="message">
    YAY THANK YOU ANGELINA ❤️🥰

    <div id="bobu">
        <!-- REAL ANIMATED BEAR -->
        <img src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif">
        <div style="font-size:1.5rem;">Bobu is jumping for joy!!! 🧸</div>
    </div>
</div>

<script>
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const message = document.getElementById("message");
const music = document.getElementById("music");
const bobu = document.getElementById("bobu");

let yesSize = 18;

/* Play music after first click */
document.body.addEventListener("click", () => {
    music.play().catch(()=>{});
}, { once: true });

/* Move NO button */
function moveNoButton() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    yesSize += 8;
    yesBtn.style.fontSize = yesSize + "px";
    yesBtn.style.padding = (yesSize/2) + "px " + yesSize + "px";
}

noBtn.addEventListener("mouseover", moveNoButton);
noBtn.addEventListener("click", moveNoButton);

/* YES clicked */
yesBtn.addEventListener("click", () => {
    document.getElementById("main").style.display = "none";
    message.style.display = "block";
    bobu.style.display = "block";
});

/* Falling hearts */
function createHeart() {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤️";

    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random()*3 + 3) + "s";

    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
}

setInterval(createHeart, 200);
</script>

</body>
</html>
