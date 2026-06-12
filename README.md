[preview.html](https://github.com/user-attachments/files/28863429/preview.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>I LOVE YOU</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    height:100vh;
    overflow:hidden;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    font-family:Arial,sans-serif;
}

.btn{
    padding:15px 30px;
    border:none;
    border-radius:50px;
    background:#ff2d55;
    color:#fff;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
    box-shadow:0 5px 15px rgba(0,0,0,.2);
}

.popup{
    position:fixed;
    inset:0;
    display:none;
    justify-content:center;
    align-items:center;
    background:rgba(0,0,0,.3);
}

.heart{
    position:relative;
    width:220px;
    height:220px;
    background:#ff1744;
    transform:rotate(-45deg);
    animation:heartbeat 1s infinite;
}

.heart:before,
.heart:after{
    content:"";
    position:absolute;
    width:220px;
    height:220px;
    background:#ff1744;
    border-radius:50%;
}

.heart:before{
    top:-110px;
    left:0;
}

.heart:after{
    left:110px;
    top:0;
}

.text{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%) rotate(45deg);
    color:#fff;
    text-align:center;
    font-size:18px;
    font-weight:bold;
    z-index:10;
    width:160px;
}

@keyframes heartbeat{
    0%,100%{
        transform:rotate(-45deg) scale(1);
    }
    50%{
        transform:rotate(-45deg) scale(1.1);
    }
}

.falling-heart{
    position:fixed;
    top:-20px;
    color:red;
    font-size:24px;
    animation:fall linear forwards;
    pointer-events:none;
}

@keyframes fall{
    to{
        transform:translateY(110vh);
    }
}
</style>
</head>
<body>

<button class="btn" id="loveBtn">
❤️ BẤM VÀO ĐÂY ❤️
</button>

<div class="popup" id="popup">
    <div class="heart">
        <div class="text">
            I LOVE YOU<br>
            ASAWA KO CUTE
        </div>
    </div>
</div>

<script>
const btn = document.getElementById("loveBtn");
const popup = document.getElementById("popup");

btn.addEventListener("click", showLove);
btn.addEventListener("touchstart", showLove);

function showLove(e){
    e.preventDefault();
    popup.style.display = "flex";
}

function createHeart(){
    const heart = document.createElement("div");
    heart.className = "falling-heart";
    heart.innerHTML = "❤️";

    heart.style.left = Math.random()*100 + "vw";
    heart.style.animationDuration =
        (Math.random()*3+2) + "s";

    document.body.appendChild(heart);

    setTimeout(()=>{
        heart.remove();
    },5000);
}

setInterval(createHeart,300);
</script>

</body>
</html>
