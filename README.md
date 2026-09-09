# YukiZaku
This place for save & show my WORK!! - RMUTR_1112Jiranan -
```html
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Jiranun Portfolio | Palm</title>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600&family=Playfair+Display:wght@600;700&display=swap');

    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        overflow: hidden;
        font-family: 'Kanit', sans-serif;
        background:
            radial-gradient(circle at top, #f6e7d2, #c9a77c 60%, #7b5b45);
        color: #4a3528;
    }

    canvas {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 0;
    }

    /* Overlay */
    .overlay {
        position: fixed;
        inset: 0;
        z-index: 2;
        pointer-events: none;
    }

    /* Navigation */
    nav {
        position: absolute;
        top: 25px;
        left: 50%;
        transform: translateX(-50%);

        display: flex;
        gap: 12px;

        background: rgba(255, 248, 235, 0.65);
        backdrop-filter: blur(12px);

        padding: 10px 18px;
        border-radius: 50px;

        border: 1px solid rgba(255,255,255,0.5);

        pointer-events: auto;

        box-shadow:
            0 8px 30px rgba(74, 53, 40, 0.18);
    }

    nav button {
        border: none;
        background: transparent;
        padding: 8px 15px;
        border-radius: 20px;

        font-family: 'Kanit', sans-serif;
        cursor: pointer;

        color: #6b4f3b;
        transition: 0.3s;
    }

    nav button:hover {
        background: #c99563;
        color: white;
    }

    /* Main Card */
    .hero {
        position: absolute;
        left: 8%;
        top: 50%;
        transform: translateY(-50%);

        max-width: 520px;

        padding: 38px;

        background: rgba(255, 248, 235, 0.72);
        backdrop-filter: blur(16px);

        border-radius: 35px;

        border: 1px solid rgba(255,255,255,0.7);

        box-shadow:
            0 20px 60px rgba(66, 45, 30, 0.25);

        pointer-events: auto;

        animation: floatCard 4s ease-in-out infinite;
    }

    @keyframes floatCard {
        0%, 100% {
            transform: translateY(-50%);
        }

        50% {
            transform: translateY(calc(-50% - 10px));
        }
    }

    .tag {
        display: inline-block;

        padding: 6px 14px;
        border-radius: 20px;

        background: #e7c9a9;

        font-size: 14px;
        color: #654332;

        margin-bottom: 15px;
    }

    h1 {
        font-family: 'Playfair Display', serif;
        font-size: clamp(42px, 5vw, 72px);
        line-height: 1.05;

        color: #5b3d2e;
        margin-bottom: 10px;
    }

    .nickname {
        font-size: 24px;
        color: #a56745;
        margin-bottom: 18px;
    }

    .description {
        font-size: 17px;
        line-height: 1.8;
        color: #60493a;
    }

    .info-box {
        margin-top: 22px;

        padding: 18px;

        background: rgba(231, 201, 169, 0.45);

        border-radius: 20px;

        border-left: 5px solid #a66a48;
    }

    .info-box p {
        margin: 6px 0;
        font-size: 15px;
    }

    .scroll-text {
        position: absolute;
        bottom: 30px;
        left: 8%;

        color: #fff7ec;
        font-size: 14px;

        text-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }

    /* Right title */
    .scene-text {
        position: absolute;
        right: 7%;
        bottom: 8%;

        text-align: right;
        color: white;

        text-shadow:
            0 4px 15px rgba(60,40,30,0.4);
    }

    .scene-text h2 {
        font-family: 'Playfair Display', serif;
        font-size: 38px;
    }

    .scene-text p {
        opacity: 0.9;
        font-size: 16px;
    }

    /* Decorative leaves */
    .leaf {
        position: absolute;
        font-size: 35px;

        animation: leafFloat 5s ease-in-out infinite;
    }

    .leaf.one {
        top: 18%;
        right: 12%;
    }

    .leaf.two {
        bottom: 25%;
        right: 35%;
        animation-delay: 1s;
    }

    @keyframes leafFloat {
        0%, 100% {
            transform: translateY(0) rotate(0deg);
        }

        50% {
            transform: translateY(-15px) rotate(10deg);
        }
    }

    /* Responsive */
    @media (max-width: 768px) {

        nav {
            width: 90%;
            justify-content: center;
            flex-wrap: wrap;
        }

        .hero {
            left: 5%;
            right: 5%;
            max-width: none;

            padding: 25px;
        }

        .scene-text {
            display: none;
        }

        h1 {
            font-size: 48px;
        }
    }

</style>
</head>

<body>

<div class="overlay">

    <nav>
        <button onclick="focusScene('home')">Home</button>
        <button onclick="focusScene('about')">About Me</button>
        <button onclick="focusScene('work')">Portfolio</button>
    </nav>

    <div class="hero">

        <div class="tag">
            ✦ GAME & ANIMATION STUDENT
        </div>

        <h1>
            Jiranun<br>
            Jamprasert
        </h1>

        <div class="nickname">
            🌿 Hi! I'm Palm
        </div>

        <p class="description">
            สวัสดีค่ะ! ฉันชื่อ <b>จิรนันท์ แจ่มประเสริฐ</b>
            หรือเรียกฉันว่า <b>ปาล์ม</b> 🌱
        </p>

        <div class="info-box">

            <p>🎓 นักศึกษาชั้นปีที่ 4</p>

            <p>
                🎮 สาขาวิชาการออกแบบเกมและแอนิเมชัน
            </p>

            <p>
                🏫 Rajamangala University of Technology Rattanakosin
            </p>

        </div>

    </div>

    <div class="scene-text">
        <h2>My Cozy Creative World 🏡</h2>
        <p>Explore • Create • Imagine</p>
    </div>

    <div class="scroll-text">
        🖱 Drag to explore the cozy world
    </div>

    <div class="leaf one">🍂</div>
    <div class="leaf two">🌿</div>

</div>


<!-- THREE.JS -->
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js"></script>

<script>

/* =========================
   BASIC SETUP
========================= */

const scene = new THREE.Scene();

scene.fog = new THREE.Fog(
    0xcfa87b,
    8,
    35
);


const camera = new THREE.PerspectiveCamera(
    60,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
);

camera.position.set(0, 5, 13);


const renderer = new THREE.WebGLRenderer({
    antialias: true,
    alpha: true
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
   LIGHTING
========================= */

const ambientLight = new THREE.AmbientLight(
    0xffe8c2,
    2.2
);

scene.add(ambientLight);


const sunLight = new THREE.DirectionalLight(
    0xffc47d,
    3
);

sunLight.position.set(
    6,
    12,
    5
);

sunLight.castShadow = true;

scene.add(sunLight);


/* =========================
   GROUND
========================= */

const groundGeometry =
    new THREE.CircleGeometry(18, 64);

const groundMaterial =
    new THREE.MeshStandardMaterial({
        color: 0x718c5b,
        roughness: 1
    });

const ground = new THREE.Mesh(
    groundGeometry,
    groundMaterial
);

ground.rotation.x = -Math.PI / 2;

ground.receiveShadow = true;

scene.add(ground);


/* =========================
   COZY COTTAGE HOUSE
========================= */

const house = new THREE.Group();


/* House body */

const houseBody =
    new THREE.Mesh(

        new THREE.BoxGeometry(
            4,
            3.5,
            3.5
        ),

        new THREE.MeshStandardMaterial({
            color: 0xd6a36f,
            roughness: 0.8
        })

    );

houseBody.position.y = 2;

houseBody.castShadow = true;

house.add(houseBody);


/* Roof */

const roof =
    new THREE.Mesh(

        new THREE.ConeGeometry(
            3.5,
            2.5,
            4
        ),

        new THREE.MeshStandardMaterial({
            color: 0x6b4030,
            roughness: 0.9
        })

    );

roof.position.y = 5;

roof.rotation.y =
    Math.PI / 4;

roof.castShadow = true;

house.add(roof);


/* Door */

const door =
    new THREE.Mesh(

        new THREE.BoxGeometry(
            0.9,
            1.7,
            0.15
        ),

        new THREE.MeshStandardMaterial({
            color: 0x6b432b
        })

    );

door.position.set(
    0,
    1.2,
    1.78
);

house.add(door);


/* Windows */

function createWindow(x, y, z) {

    const windowMesh =
        new THREE.Mesh(

            new THREE.BoxGeometry(
                0.8,
                0.8,
                0.12
            ),

            new THREE.MeshStandardMaterial({
                color: 0xffd77a,
                emissive: 0xffb347,
                emissiveIntensity: 0.5
            })

        );

    windowMesh.position.set(
        x,
        y,
        z
    );

    house.add(windowMesh);
}


createWindow(
    -1.2,
    2.5,
    1.78
);

createWindow(
    1.2,
    2.5,
    1.78
);


house.position.set(
    4,
    0,
    -2
);

scene.add(house);


/* =========================
   TREES
========================= */

function createTree(x, z, scale = 1) {

    const tree =
        new THREE.Group();


    const trunk =
        new THREE.Mesh(

            new THREE.CylinderGeometry(
                0.25 * scale,
                0.35 * scale,
                2 * scale,
                8
            ),

            new THREE.MeshStandardMaterial({
                color: 0x70492d
            })

        );

    trunk.position.y =
        1 * scale;


    const leaves =
        new THREE.Mesh(

            new THREE.SphereGeometry(
                1.3 * scale,
                16,
                16
            ),

            new THREE.MeshStandardMaterial({
                color: 0x56734d,
                roughness: 1
            })

        );

    leaves.position.y =
        3 * scale;


    trunk.castShadow = true;

    leaves.castShadow = true;


    tree.add(trunk);

    tree.add(leaves);


    tree.position.set(
        x,
        0,
        z
    );


    scene.add(tree);

}


createTree(-6, -2, 1.2);

createTree(-7, 4, 0.9);

createTree(7, 3, 1.4);

createTree(5, -6, 1);


/* =========================
   FLOWERS
========================= */

function createFlower(x, z) {

    const flower =
        new THREE.Group();


    const stem =
        new THREE.Mesh(

            new THREE.CylinderGeometry(
                0.04,
                0.04,
                0.7,
                6
            ),

            new THREE.MeshStandardMaterial({
                color: 0x426b3e
            })

        );

    stem.position.y = 0.35;


    const petalColors = [
        0xffb6c1,
        0xffd1dc,
        0xf7c873
    ];


    const petal =
        new THREE.Mesh(

            new THREE.SphereGeometry(
                0.18,
                8,
                8
            ),

            new THREE.MeshStandardMaterial({
                color:
                    petalColors[
                        Math.floor(
                            Math.random() *
                            petalColors.length
                        )
                    ]
            })

        );

    petal.position.y = 0.75;


    flower.add(stem);

    flower.add(petal);


    flower.position.set(
        x,
        0,
        z
    );


    scene.add(flower);

}


for (let i = 0; i < 35; i++) {

    createFlower(

        (Math.random() - 0.5) * 16,

        (Math.random() - 0.5) * 12

    );

}


/* =========================
   FLOATING FIREFLIES
========================= */

const fireflies = [];


for (let i = 0; i < 45; i++) {

    const firefly =
        new THREE.Mesh(

            new THREE.SphereGeometry(
                0.06,
                8,
                8
            ),

            new THREE.MeshBasicMaterial({
                color: 0xffdd77
            })

        );


    firefly.position.set(

        (Math.random() - 0.5) * 18,

        Math.random() * 6 + 0.5,

        (Math.random() - 0.5) * 14

    );


    fireflies.push({

        mesh: firefly,

        speed:
            0.5 +
            Math.random()

    });


    scene.add(firefly);

}


/* =========================
   MOUSE MOVEMENT
========================= */

let mouseX = 0;

let mouseY = 0;


document.addEventListener(
    "mousemove",
    (event) => {

        mouseX =
            (event.clientX /
            window.innerWidth - 0.5) * 2;

        mouseY =
            (event.clientY /
            window.innerHeight - 0.5) * 2;

    }
);


/* =========================
   CAMERA BUTTONS
========================= */

function focusScene(type) {

    if (type === "home") {

        camera.position.set(
            0,
            5,
            13
        );

    }


    if (type === "about") {

        camera.position.set(
            -3,
            4,
            10
        );

    }


    if (type === "work") {

        camera.position.set(
            5,
            5,
            10
        );

    }

}


/* =========================
   ANIMATION
========================= */

const clock =
    new THREE.Clock();


function animate() {

    requestAnimationFrame(
        animate
    );


    const elapsed =
        clock.getElapsedTime();


    /* Camera movement */

    camera.position.x +=
        (mouseX * 1.5 -
        camera.position.x) * 0.01;


    camera.position.y +=
        (-mouseY * 0.5 + 5 -
        camera.position.y) * 0.01;


    camera.lookAt(
        0,
        2,
        0
    );


    /* House movement */

    house.rotation.y =
        Math.sin(elapsed * 0.3) *
        0.08;


    /* Fireflies */

    fireflies.forEach(
        (firefly, index) => {

            firefly.mesh.position.y +=
                Math.sin(
                    elapsed *
                    firefly.speed +
                    index
                ) * 0.01;


            firefly.mesh.position.x +=
                Math.cos(
                    elapsed *
                    0.5 +
                    index
                ) * 0.002;

        }
    );


    renderer.render(
        scene,
        camera
    );

}


animate();


/* =========================
   RESPONSIVE
========================= */

window.addEventListener(
    "resize",
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

</script>

</body>
</html>
