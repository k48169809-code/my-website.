<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Heart Love</title>
<style>
body{
    margin:0;
    background:black;
    overflow:hidden;
}

canvas{
    display:block;
}
</style>
</head>
<body>

<canvas id="c"></canvas>

<script>
const canvas = document.getElementById("c");
const ctx = canvas.getContext("2d");

function resize(){
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}
resize();
window.addEventListener("resize", resize);

const particles = [];

for(let t=0; t<Math.PI*2; t+=0.05){
    let x = 16*Math.pow(Math.sin(t),3);
    let y = -(13*Math.cos(t)-5*Math.cos(2*t)-2*Math.cos(3*t)-Math.cos(4*t));

    particles.push({
        x:x*20,
        y:y*20
    });
}

function draw(){
    ctx.fillStyle="rgba(0,0,0,0.2)";
    ctx.fillRect(0,0,canvas.width,canvas.height);

    ctx.fillStyle="#ff3366";
    ctx.font="14px Arial";

    particles.forEach(p=>{
        ctx.fillText(
            "I love you",
            canvas.width/2+p.x,
            canvas.height/2+p.y
        );
    });

    ctx.fillStyle="white";
    ctx.font="50px Arial";
    ctx.textAlign="center";
    ctx.fillText("Love You", canvas.width/2, canvas.height/2+20);

    requestAnimationFrame(draw);
}

draw();
</script>

</body>
</html>