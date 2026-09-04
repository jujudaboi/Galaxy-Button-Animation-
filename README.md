<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Universe Button Animation</title>

<style>
* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    font-family: Arial, sans-serif;
    background: #000;
}

/* =========================
   SPACE
========================= */

.space {
    position: fixed;
    inset: 0;
    background:
        radial-gradient(
            ellipse at center,
            #10162f 0%,
            #050714 35%,
            #010207 70%,
            #000 100%
        );
    overflow: hidden;
}

/* =========================
   NEBULA
========================= */

.nebula {
    position: absolute;
    inset: -30%;
    background:
        radial-gradient(
            ellipse at 25% 40%,
            rgba(90, 30, 255, .22),
            transparent 28%
        ),
        radial-gradient(
            ellipse at 70% 35%,
            rgba(0, 120, 255, .18),
            transparent 30%
        ),
        radial-gradient(
            ellipse at 60% 75%,
            rgba(190, 20, 180, .16),
            transparent 25%
        ),
        radial-gradient(
            ellipse at 35% 80%,
            rgba(0, 200, 255, .10),
            transparent 30%
        );

    filter: blur(45px);
    transform: scale(1.1);
    transition: transform 8s ease-in;
}

/* =========================
   REALISTIC STAR FIELD
========================= */

.stars {
    position: absolute;
    inset: 0;
}

.stars::before,
.stars::after {
    content: "";
    position: absolute;
    inset: -50%;

    background-image:
        radial-gradient(circle, white 0 1px, transparent 1.5px),
        radial-gradient(circle, rgba(255,255,255,.8) 0 1px, transparent 1.5px),
        radial-gradient(circle, rgba(150,200,255,.7) 0 1px, transparent 1.5px);

    background-size:
        97px 113px,
        151px 173px,
        223px 197px;

    background-position:
        20px 30px,
        80px 100px,
        150px 40px;

    opacity: .7;
}

.stars::after {
    transform: rotate(180deg);
    opacity: .4;
}

/* =========================
   DISTANT GALAXY
========================= */

.galaxy {
    position: absolute;

    width: 240px;
    height: 90px;

    left: 15%;
    top: 18%;

    border-radius: 50%;

    background:
        radial-gradient(
            ellipse,
            rgba(255,255,255,.9) 0%,
            rgba(120,170,255,.35) 10%,
            rgba(90,30,255,.15) 35%,
            transparent 70%
        );

    transform: rotate(-25deg);
    filter: blur(2px);

    box-shadow:
        0 0 40px rgba(100,130,255,.25);
}

.galaxy::after {
    content: "";

    position: absolute;
    inset: 20px -40px;

    border-radius: 50%;

    border-top: 2px solid rgba(150,180,255,.25);
    border-bottom: 2px solid rgba(150,180,255,.15);
}


/* =========================
   PLANET
========================= */

.planet {
    position: absolute;

    width: 230px;
    height: 230px;

    right: -100px;
    bottom: -80px;

    border-radius: 50%;

    background:
        radial-gradient(
            circle at 30% 25%,
            #d7f3ff 0%,
            #4f9ed8 18%,
            #174b87 45%,
            #07162e 72%,
            #000 100%
        );

    box-shadow:
        -20px -10px 40px rgba(60,160,255,.35),
        inset -30px -20px 50px rgba(0,0,0,.7);

    transition:
        transform 7s ease-in,
        opacity 7s ease-in;
}

.planet::after {
    content: "";

    position: absolute;

    width: 330px;
    height: 75px;

    left: -50px;
    top: 80px;

    border: 3px solid rgba(160,210,255,.35);
    border-radius: 50%;

    transform: rotate(-18deg);
}


/* =========================
   VIGNETTE
========================= */

.vignette {
    position: absolute;
    inset: 0;

    background:
        radial-gradient(
            circle,
            transparent 25%,
            rgba(0,0,0,.45) 75%,
            rgba(0,0,0,.9) 100%
        );

    pointer-events: none;
}


/* =========================
   BUTTON
========================= */

.menu {
    position: relative;
    z-index: 20;

    width: 100%;
    height: 100%;

    display: flex;
    justify-content: center;
    align-items: center;

    transition:
        opacity 1s ease,
        transform 1s ease;
}

.button-container {
    position: relative;
}

.button-container::before {
    content: "";

    position: absolute;
    inset: -6px;

    border-radius: 20px;

    background:
        linear-gradient(
            90deg,
            #7b2cff,
            #00bfff,
            #7b2cff
        );

    background-size: 200%;

    filter: blur(15px);
    opacity: .7;

    animation: glow 3s linear infinite;
}

@keyframes glow {
    from {
        background-position: 0%;
    }

    to {
        background-position: 200%;
    }
}

button {
    position: relative;
    z-index: 2;

    padding: 20px 48px;

    border: 1px solid rgba(255,255,255,.3);
    border-radius: 16px;

    color: white;

    font-size: 19px;
    font-weight: bold;
    letter-spacing: 2px;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.14),
            rgba(255,255,255,.04)
        );

    backdrop-filter: blur(20px);

    cursor: pointer;

    box-shadow:
        inset 0 1px rgba(255,255,255,.35),
        0 15px 50px rgba(0,0,0,.5);

    transition:
        transform .3s ease,
        box-shadow .3s ease;
}

button:hover {
    transform: translateY(-6px) scale(1.05);

    box-shadow:
        inset 0 1px rgba(255,255,255,.5),
        0 0 30px rgba(0,190,255,.6),
        0 20px 60px rgba(0,0,0,.6);
}

button:active {
    transform: scale(.94);
}


/* =========================
   HYPERSPACE
========================= */

.warp {
    position: absolute;
    inset: -100%;

    opacity: 0;

    background:
        repeating-radial-gradient(
            circle at center,
            transparent 0,
            transparent 8px,
            rgba(255,255,255,.12) 9px,
            transparent 11px
        );

    transform: scale(.1);
}


/* =========================
   FLYING ANIMATION
========================= */

body.flying .menu {
    opacity: 0;
    transform: scale(3);
}

body.flying .nebula {
    transform: scale(3);
}

body.flying .stars::before {
    animation: starsForward 3s cubic-bezier(.2,.8,.2,1) forwards;
}

body.flying .stars::after {
    animation: starsForward 2.5s cubic-bezier(.2,.8,.2,1) forwards;
}

body.flying .galaxy {
    animation: galaxyFly 5s ease-in forwards;
}

body.flying .planet {
    animation: planetFly 6s ease-in forwards;
}

body.flying .warp {
    animation: warp 5s ease-in forwards;
}


/* =========================
   ANIMATIONS
========================= */

@keyframes starsForward {

    0% {
        transform: scale(1);
        opacity: .6;
    }

    35% {
        opacity: .8;
    }

    100% {
        transform: scale(5);
        opacity: 0;
    }
}

@keyframes galaxyFly {

    0% {
        transform:
            translate(0,0)
            rotate(-25deg)
            scale(1);

        opacity: .7;
    }

    100% {
        transform:
            translate(-20vw,-10vh)
            rotate(-25deg)
            scale(5);

        opacity: 0;
    }
}

@keyframes planetFly {

    0% {
        transform: scale(1);
        opacity: 1;
    }

    70% {
        opacity: .8;
    }

    100% {
        transform: scale(8) translate(-5vw,-5vh);
        opacity: 0;
    }
}

@keyframes warp {

    0% {
        opacity: 0;
        transform: scale(.1) rotate(0deg);
    }

    20% {
        opacity: .25;
    }

    60% {
        opacity: .5;
    }

    100% {
        opacity: 0;
        transform: scale(5) rotate(45deg);
    }
}

</style>
</head>

<body>

<div class="space">

    <div class="nebula"></div>

    <div class="stars"></div>

    <div class="galaxy"></div>

    <div class="planet"></div>

    <div class="warp"></div>

    <div class="vignette"></div>

</div>


<div class="menu">

    <div class="button-container">

        <button onclick="fly()">
            ENTER THE UNIVERSE
        </button>

    </div>

</div>


<script>

function fly() {

    document.body.classList.add("flying");

    /*
      After the flight finishes,
      you could load another page here.

      Example:

      setTimeout(() => {
          window.location.href = "home.html";
      }, 7000);
    */

}

</script>

</body>
</html>
