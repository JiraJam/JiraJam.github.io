# YukiZaku
This place for save & show my WORK!! - RMUTR_1112Jiranan -
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Jiranan Palm | 3D Portfolio</title>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Mali:wght@400;500;600;700&family=Quicksand:wght@400;500;600;700&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            overflow: hidden;
            font-family: "Mali", "Quicksand", sans-serif;
            background: #cfe6c8;
            color: #4d3928;
        }

        canvas {
            display: block;
        }

        /* =========================
           UI
        ========================= */

        .ui {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 10;
        }

        /* NAV */

        nav {
            position: absolute;
            top: 25px;
            left: 50%;
            transform: translateX(-50%);
            width: min(900px, 90%);
            display: flex;
            justify-content: space-between;
            align-items: center;

            padding: 15px 25px;

            background: rgba(255, 250, 240, 0.72);
            backdrop-filter: blur(12px);

            border: 2px solid rgba(255,255,255,0.7);
            border-radius: 25px;

            box-shadow: 0 8px 30px rgba(82, 57, 35, 0.15);

            pointer-events: auto;
        }

        .logo {
            font-size: 20px;
            font-weight: 700;
            color: #6b4f36;
        }

        .nav-links {
            display: flex;
            gap: 20px;
        }

        .nav-links button {
            border: none;
            background: transparent;
            font-family: inherit;
            font-size: 14px;
            color: #6b4f36;
            cursor: pointer;
            transition: 0.3s;
        }

        .nav-links button:hover {
            color: #a5673f;
            transform: translateY(-2px);
        }

        /* HERO */

        .hero {
            position: absolute;
            top: 50%;
            left: 8%;
            transform: translateY(-50%);
            max-width: 550px;

            pointer-events: auto;
        }

        .badge {
            display: inline-block;
            padding: 8px 18px;
            margin-bottom: 18px;

            background: #fff4df;
            border-radius: 30px;

            color: #8b6044;
            font-size: 14px;

            box-shadow: 0 5px 15px rgba(80, 50, 30, 0.1);
        }

        h1 {
            font-size: clamp(42px, 6vw, 82px);
            line-height: 1.1;
            color: #5d422d;
            margin-bottom: 15px;
        }

        h1 span {
            color: #b8754d;
        }

        .nickname {
            font-size: 22px;
            color: #876047;
            margin-bottom: 20px;
        }

        .description {
            font-size: 16px;
            line-height: 1.8;
            color: #684f3d;
            max-width: 500px;
        }

        .buttons {
            margin-top: 30px;
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }

        .btn {
            padding: 14px 24px;
            border-radius: 30px;
            border: none;

            font-family: inherit;
            font-size: 15px;
            font-weight: 600;

            cursor: pointer;
            pointer-events: auto;

            transition: 0.3s;
        }

        .btn-primary {
            background: #9b6b4d;
            color: white;
            box-shadow: 0 8px 20px rgba(100, 65, 40, 0.25);
        }

        .btn-secondary {
            background: #fff8ec;
            color: #79553d;
            box-shadow: 0 8px 20px rgba(100, 65, 40, 0.12);
        }

        .btn:hover {
            transform: translateY(-4px) scale(1.03);
        }

        /* INFO CARD */

        .info-card {
            position: absolute;
            right: 6%;
            bottom: 8%;

            width: 300px;

            padding: 25px;

            background: rgba(255, 248, 235, 0.82);
            backdrop-filter: blur(12px);

            border-radius: 25px;
            border: 2px solid rgba(255,255,255,0.8);

            box-shadow: 0 10px 40px rgba(70, 50, 30, 0.15);

            pointer-events: auto;
        }

        .info-card h2 {
            font-size: 20px;
            margin-bottom: 15px;
            color: #68472f;
        }

        .info-item {
            margin-bottom: 12px;
            font-size: 14px;
            line-height: 1.6;
        }

        .info-item strong {
            display: block;
            color: #9a6b4c;
        }

        /* PROJECT PANEL */

        .project-panel {
            position: absolute;
            right: 6%;
            top: 130px;

            width: 260px;

            padding: 20px;

            background: rgba(255, 248, 235, 0.78);
            backdrop-filter: blur(10px);

            border-radius: 22px;

            opacity: 0;
            transform: translateX(30px);

            transition: 0.5s;

            pointer-events: auto;
        }

        .project-panel.active {
            opacity: 1;
            transform: translateX(0);
        }

        .project-panel h3 {
            color: #68472f;
            margin-bottom: 10px;
        }

        .project-panel p {
            font-size: 13px;
            line-height: 1.7;
        }

        /* CONTROLS */

        .controls {
            position: absolute;
            bottom: 25px;
            left: 50%;
            transform: translateX(-50%);

            padding: 10px 20px;

            background: rgba(255,255,255,0.6);
            border-radius: 25px;

            font-size: 12px;
            color: #6f533e;

            backdrop-filter: blur(10px);
        }

        /* LOADING */

        #loading {
            position: fixed;
            inset: 0;

            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;

            background: #d9ebd2;

            z-index: 100;

            transition: 1s;
        }

        .loading-house {
            font-size: 70px;
            animation: bounce 1.5s infinite;
        }

        #loading p {
            margin-top: 15px;
            color: #68472f;
        }

        @keyframes bounce {
            50% {
                transform: translateY(-15px);
            }
        }

        /* RESPONSIVE */

        @media (max-width: 768px) {

            nav {
                top: 15px;
                padding: 12px 18px;
            }

            .nav-links {
                gap: 10px;
            }

            .nav-links button {
                font-size: 11px;
            }

            .hero {
                left: 7%;
                top: 42%;
                max-width: 85%;
            }

            h1 {
                font-size: 42px;
            }

            .description {
                font-size: 13px;
            }

            .info-card {
                display: none;
            }

            .project-panel {
                display: none;
            }

            .controls {
                width: 90%;
                text-align: center;
            }

        }

    </style>
</head>

<body>

<!-- =========================
     LOADING SCREEN
========================= -->

<div id="loading">
    <div class="loading-house">🏡</div>
    <p>Welcome to my cozy world...</p>
</div>


<!-- =========================
     UI
========================= -->

<div class="ui">

    <nav>
        <div class="logo">🌿 PALM PORTFOLIO</div>

        <div class="nav-links">
            <button onclick="showHome()">Home</button>
            <button onclick="showProjects()">Projects</button>
            <button onclick="showAbout()">About</button>
        </div>
    </nav>


    <!-- HERO -->

    <section class="hero">

        <div class="badge">
            ✨ Game & Animation Designer
        </div>

        <h1>
            Hello, I'm<br>
            <span>Jiranan</span>
        </h1>

        <div class="nickname">
            🌼 Nickname: Palm (ปาล์ม)
        </div>

        <p class="description">
            นักศึกษาชั้นปีที่ 4 สาขาวิชาการออกแบบเกมและแอนิเมชัน
            ผู้ที่หลงใหลในการสร้างสรรค์โลก 3D เกม และแอนิเมชัน
            ผ่านจินตนาการและการออกแบบ
        </p>

        <div class="buttons">

            <button class="btn btn-primary" onclick="showProjects()">
                🎮 ดูผลงาน
            </button>

            <button class="btn btn-secondary" onclick="showAbout()">
                🌿 เกี่ยวกับฉัน
            </button>

        </div>

    </section>


    <!-- PROJECT PANEL -->

    <div class="project-panel" id="projectPanel">

        <h3>🌿 My Creative World</h3>

        <p>
            ผลงานของฉันเกี่ยวกับ
            Game Design, 3D Modeling,
            Animation และ Creative Design
        </p>

        <br>

        <p>
            ✨ คลิกที่วัตถุ 3D ในโลกเพื่อสำรวจ
        </p>

    </div>


    <!-- INFO CARD -->

    <div class="info-card">

        <h2>🏡 About Me</h2>

        <div class="info-item">
            <strong>👤 Name</strong>
            จิรนันท์ แจ่มประเสริฐ
        </div>

        <div class="info-item">
            <strong>🌼 Nickname</strong>
            ปาล์ม (Palm)
        </div>

        <div class="info-item">
            <strong>🎓 Education</strong>
            Rajamangala University of Technology Rattanakosin
        </div>

        <div class="info-item">
            <strong>🕹️ Major</strong>
            Game and Animation Design
        </div>

    </div>


    <div class="controls">
        🖱️ ลากเมาส์เพื่อหมุนมุมมอง • Scroll เพื่อ Zoom
    </div>

</div>


<!-- =========================
     THREE.JS
========================= -->

<script type="module">

import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js';

import { OrbitControls } from
'https://cdn.jsdelivr.net/npm/three@0.160.0/examples/jsm/controls/OrbitControls.js';


/* =========================
   SCENE
========================= */

const scene = new THREE.Scene();

scene.background = new THREE.Color(0xcfe6c8);

scene.fog = new THREE.Fog(0xcfe6c8, 15, 55);


/* =========================
   CAMERA
========================= */

const camera = new THREE.PerspectiveCamera(
    45,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
);

camera.position.set(10, 8, 14);


/* =========================
   RENDERER
========================= */

const renderer = new THREE.WebGLRenderer({
    antialias: true
});

renderer.setSize(
    window.innerWidth,
    window.innerHeight
);

renderer.setPixelRatio(
    Math.min(window.devicePixelRatio, 2)
);

renderer.shadowMap.enabled = true;

document.body.appendChild(renderer.domElement);


/* =========================
   CONTROLS
========================= */

const controls = new OrbitControls(
    camera,
    renderer.domElement
);

controls.enableDamping = true;

controls.dampingFactor = 0.05;

controls.target.set(0, 2, 0);

controls.maxDistance = 25;
controls.minDistance = 7;


/* =========================
   LIGHTS
========================= */

const ambientLight = new THREE.HemisphereLight(
    0xfff4dd,
    0x6d8c59,
    2.2
);

scene.add(ambientLight);


const sunLight = new THREE.DirectionalLight(
    0xffe4a8,
    3
);

sunLight.position.set(8, 12, 6);

sunLight.castShadow = true;

scene.add(sunLight);


/* =========================
   MATERIALS
========================= */

const grassMaterial = new THREE.MeshStandardMaterial({
    color: 0x7fa66b,
    roughness: 1
});

const woodMaterial = new THREE.MeshStandardMaterial({
    color: 0x9b6a4b,
    roughness: 0.9
});

const roofMaterial = new THREE.MeshStandardMaterial({
    color: 0x8d5a45,
    roughness: 0.8
});

const wallMaterial = new THREE.MeshStandardMaterial({
    color: 0xffe8bd,
    roughness: 0.9
});

const leafMaterial = new THREE.MeshStandardMaterial({
    color: 0x6f995b,
    roughness: 1
});


/* =========================
   GROUND
========================= */

const ground = new THREE.Mesh(

    new THREE.CircleGeometry(18, 64),

    grassMaterial

);

ground.rotation.x = -Math.PI / 2;

ground.receiveShadow = true;

scene.add(ground);


/* =========================
   COTTAGE HOUSE
========================= */

const house = new THREE.Group();

scene.add(house);


/* House Body */

const houseBody = new THREE.Mesh(

    new THREE.BoxGeometry(5, 3.5, 4),

    wallMaterial

);

houseBody.position.y = 2;

houseBody.castShadow = true;
houseBody.receiveShadow = true;

house.add(houseBody);


/* Roof */

const roof = new THREE.Mesh(

    new THREE.ConeGeometry(
        4.2,
        2.6,
        4
    ),

    roofMaterial

);

roof.rotation.y = Math.PI / 4;

roof.position.y = 5;

roof.castShadow = true;

house.add(roof);


/* Door */

const door = new THREE.Mesh(

    new THREE.BoxGeometry(0.9, 1.8, 0.15),

    woodMaterial

);

door.position.set(0, 1.2, 2.05);

house.add(door);


/* Windows */

function createWindow(x, y, z) {

    const windowMesh = new THREE.Mesh(

        new THREE.BoxGeometry(
            0.9,
            0.9,
            0.12
        ),

        new THREE.MeshStandardMaterial({
            color: 0x9dd8e8,
            emissive: 0x27434a,
            emissiveIntensity: 0.3
        })

    );

    windowMesh.position.set(x, y, z);

    house.add(windowMesh);

}

createWindow(-1.5, 2.4, 2.05);
createWindow(1.5, 2.4, 2.05);


/* =========================
   TREES
========================= */

function createTree(x, z, scale = 1) {

    const tree = new THREE.Group();


    const trunk = new THREE.Mesh(

        new THREE.CylinderGeometry(
            0.35 * scale,
            0.45 * scale,
            2.5 * scale,
            8
        ),

        woodMaterial

    );

    trunk.position.y = 1.25 * scale;

    trunk.castShadow = true;

    tree.add(trunk);


    const leaves = new THREE.Mesh(

        new THREE.ConeGeometry(
            1.8 * scale,
            4 * scale,
            10
        ),

        leafMaterial

    );

    leaves.position.y = 4 * scale;

    leaves.castShadow = true;

    tree.add(leaves);


    tree.position.set(x, 0, z);

    scene.add(tree);

}

createTree(-7, -3, 1.2);
createTree(7, -4, 1);
createTree(-6, 5, 0.9);
createTree(8, 4, 1.3);


/* =========================
   FLOWERS
========================= */

const flowerColors = [
    0xff9eb5,
    0xffd166,
    0xf7b2ff,
    0xffffff
];

function createFlower(x, z) {

    const flower = new THREE.Group();

    const stem = new THREE.Mesh(

        new THREE.CylinderGeometry(
            0.04,
            0.04,
            0.6,
            6
        ),

        new THREE.MeshStandardMaterial({
            color: 0x4f8a4d
        })

    );

    stem.position.y = 0.3;

    flower.add(stem);


    const color =
        flowerColors[
            Math.floor(
                Math.random() * flowerColors.length
            )
        ];


    const petalMaterial =
        new THREE.MeshStandardMaterial({
            color
        });


    for(let i = 0; i < 5; i++) {

        const petal = new THREE.Mesh(

            new THREE.SphereGeometry(
                0.15,
                8,
                8
            ),

            petalMaterial

        );

        const angle =
            (i / 5) * Math.PI * 2;

        petal.position.set(

            Math.cos(angle) * 0.2,

            0.65,

            Math.sin(angle) * 0.2

        );

        flower.add(petal);

    }


    const center = new THREE.Mesh(

        new THREE.SphereGeometry(
            0.12,
            8,
            8
        ),

        new THREE.MeshStandardMaterial({
            color: 0xffc84d
        })

    );

    center.position.y = 0.65;

    flower.add(center);


    flower.position.set(x, 0, z);

    scene.add(flower);

}


/* Random Flowers */

for(let i = 0; i < 70; i++) {

    const angle =
        Math.random() * Math.PI * 2;

    const radius =
        4 + Math.random() * 12;

    const x =
        Math.cos(angle) * radius;

    const z =
        Math.sin(angle) * radius;

    createFlower(x, z);

}


/* =========================
   FLOATING PORTFOLIO OBJECTS
========================= */

const portfolioObjects = [];


/* GAME CONTROLLER */

const controllerGroup = new THREE.Group();

const controller = new THREE.Mesh(

    new THREE.BoxGeometry(
        2,
        0.6,
        1
    ),

    new THREE.MeshStandardMaterial({
        color: 0x8b6b8a
    })

);

controllerGroup.add(controller);

controllerGroup.position.set(
    -5,
    4,
    2
);

scene.add(controllerGroup);

portfolioObjects.push(controllerGroup);


/* CUBE - 3D */

const cube = new THREE.Mesh(

    new THREE.BoxGeometry(
        1.5,
        1.5,
        1.5
    ),

    new THREE.MeshStandardMaterial({
        color: 0xd28a5d,
        roughness: 0.5
    })

);

cube.position.set(
    5,
    4,
    2
);

cube.castShadow = true;

scene.add(cube);

portfolioObjects.push(cube);


/* ANIMATION SPHERE */

const animationSphere = new THREE.Mesh(

    new THREE.SphereGeometry(
        1,
        32,
        32
    ),

    new THREE.MeshStandardMaterial({
        color: 0xf3b6b6,
        roughness: 0.4
    })

);

animationSphere.position.set(
    4,
    3,
    -4
);

scene.add(animationSphere);

portfolioObjects.push(animationSphere);


/* =========================
   FIREFLIES
========================= */

const fireflyGeometry =
    new THREE.SphereGeometry(
        0.04,
        8,
        8
    );

const fireflyMaterial =
    new THREE.MeshBasicMaterial({
        color: 0xfff3a6
    });


const fireflies = [];

for(let i = 0; i < 80; i++) {

    const firefly =
        new THREE.Mesh(
            fireflyGeometry,
            fireflyMaterial
        );

    firefly.position.set(

        (Math.random() - 0.5) * 20,

        Math.random() * 6 + 0.5,

        (Math.random() - 0.5) * 20

    );

    scene.add(firefly);

    fireflies.push(firefly);

}


/* =========================
   INTERACTION
========================= */

const raycaster = new THREE.Raycaster();

const mouse = new THREE.Vector2();


window.addEventListener(
    'click',
    (event) => {

        mouse.x =
            (event.clientX /
            window.innerWidth) * 2 - 1;

        mouse.y =
            -(event.clientY /
            window.innerHeight) * 2 + 1;


        raycaster.setFromCamera(
            mouse,
            camera
        );


        const intersects =
            raycaster.intersectObjects(
                portfolioObjects,
                true
            );


        if(intersects.length > 0) {

            const panel =
                document.getElementById(
                    'projectPanel'
                );

            panel.classList.toggle('active');

        }

    }
);


/* =========================
   UI FUNCTIONS
========================= */

window.showHome = function() {

    document
        .getElementById('projectPanel')
        .classList.remove('active');


    camera.position.set(
        10,
        8,
        14
    );

};


window.showProjects = function() {

    document
        .getElementById('projectPanel')
        .classList.add('active');


    camera.position.set(
        12,
        7,
        10
    );

};


window.showAbout = function() {

    alert(
`🌿 About Me

ชื่อ: จิรนันท์ แจ่มประเสริฐ
ชื่อเล่น: ปาล์ม

นักศึกษาชั้นปีที่ 4

สาขาวิชาการออกแบบเกมและแอนิเมชัน

Rajamangala University of Technology Rattanakosin

✨ สนใจด้าน Game Design,
3D Modeling และ Animation`
    );

};


/* =========================
   ANIMATION
========================= */

const clock = new THREE.Clock();


function animate() {

    requestAnimationFrame(animate);


    const time =
        clock.getElapsedTime();


    /* Floating Objects */

    controllerGroup.rotation.y =
        time * 0.6;

    controllerGroup.position.y =
        4 + Math.sin(time) * 0.4;


    cube.rotation.x =
        time * 0.7;

    cube.rotation.y =
        time * 0.5;

    cube.position.y =
        4 + Math.sin(time * 1.5) * 0.5;


    animationSphere.position.y =
        3 + Math.sin(time * 2) * 0.4;


    /* Fireflies */

    fireflies.forEach(
        (firefly, index) => {

            firefly.position.y +=
                Math.sin(
                    time +
                    index
                ) * 0.002;

        }
    );


    /* House breathing effect */

    house.rotation.y =
        Math.sin(time * 0.2) * 0.03;


    controls.update();

    renderer.render(
        scene,
        camera
    );

}


animate();


/* =========================
   RESIZE
========================= */

window.addEventListener(
    'resize',
    () => {

        camera.aspect =
            window.innerWidth /
            window.innerHeight;

        camera.updateProjectionMatrix();


        renderer.setSize(
            window.innerWidth,
            window.innerHeight
        );

    }
);


/* =========================
   REMOVE LOADING
========================= */

window.addEventListener(
    'load',
    () => {

        setTimeout(() => {

            const loading =
                document.getElementById(
                    'loading'
                );

            loading.style.opacity = '0';

            setTimeout(() => {

                loading.style.display =
                    'none';

            }, 1000);

        }, 1200);

    }
);

</script>
