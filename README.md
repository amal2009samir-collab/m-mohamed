<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SULTAN_OS | ARCHITECTED BY AMAL</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&family=Orbitron:wght@400;900&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

    <style>
        :root {
            --p: #00f2ff; --s: #7000ff; --t: #ff0077;
            --bg: #01020a; --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(0, 242, 255, 0.2);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { background: var(--bg); color: #fff; font-family: 'Cairo', sans-serif; overflow-x: hidden; width: 100%; display: flex; flex-direction: column; align-items: center; }
        
        #core-canvas { position: fixed; inset: 0; z-index: -1; }

        /* --- Navigation --- */
        nav {
            position: fixed; top: 0; width: 100%; height: 60px;
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 20px; z-index: 9999;
            background: rgba(1, 2, 10, 0.9); backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border);
        }
        .nav-logo { font-family: 'Orbitron'; font-weight: 900; color: var(--p); font-size: 0.9rem; }
        .amal-sig { color: var(--t); font-size: 0.6rem; font-family: 'Orbitron'; }

        /* --- Hero --- */
        .hero { height: 80vh; width: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; }
        #hero-3d { width: 100%; height: 350px; }
        .hero h1 { font-size: 3rem; font-weight: 900; background: linear-gradient(#fff, var(--p)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }

        /* --- Schedule Section --- */
        .card-container { width: 100%; max-width: 400px; padding: 15px; display: flex; flex-direction: column; gap: 20px; }
        .mega-card {
            background: var(--glass); border: 1px solid var(--border);
            border-radius: 30px; padding: 20px; width: 100%;
            backdrop-filter: blur(10px);
        }
        .mega-card h2 { color: var(--p); font-size: 1.6rem; text-align: center; margin-bottom: 5px; }
        .sub-loc { font-size: 0.7rem; color: var(--t); text-align: center; display: block; margin-bottom: 15px; }

        /* تصغير المربعات عشان تيجي في النص */
        .time-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; }
        .slot { background: rgba(255,255,255,0.02); padding: 12px; border-radius: 15px; border: 1px solid rgba(255,255,255,0.05); text-align: center; }
        .slot b { font-family: 'Orbitron'; font-size: 1.1rem; display: block; }
        .slot span { font-size: 0.6rem; color: var(--p); opacity: 0.8; }

        /* --- Gallery with Text Overlay --- */
        .photo-gallery { width: 100%; max-width: 400px; padding: 20px; }
        .photo-item { border-radius: 25px; overflow: hidden; margin-bottom: 25px; border: 1px solid var(--border); position: relative; }
        .photo-item img { width: 100%; display: block; opacity: 0.8; }
        .overlay-text { 
            position: absolute; bottom: 0; width: 100%; 
            background: linear-gradient(transparent, rgba(0,0,0,0.9)); 
            padding: 20px 10px; text-align: center; 
            color: var(--p); font-weight: 900; font-size: 1.1rem;
        }

        .portal-btn {
            display: inline-block; margin: 40px 0; padding: 20px 60px; background: #fff; color: #000;
            font-family: 'Orbitron'; font-weight: 900; border-radius: 50px; text-decoration: none;
        }

        footer { padding: 40px; text-align: center; font-size: 0.7rem; opacity: 0.5; font-family: 'Orbitron'; }
    </style>
</head>
<body>

    <canvas id="core-canvas"></canvas>

    <nav>
        <div class="nav-logo">SULTAN_CORE</div>
        <div class="amal-sig">CODED_BY_AMAL</div>
    </nav>

    <section class="hero">
        <div id="hero-3d"></div>
        <h1>م/ محمد سلطان</h1>
        <p style="font-family: 'Orbitron'; color: var(--p); letter-spacing: 3px; font-size: 0.8rem;">BIOLOGY MULTIVERSE</p>
    </section>

    <div class="card-container">
        <div class="mega-card">
            <h2>سنتر مكة</h2>
            <span class="sub-loc">المنزلة - شارع العاشر (الإثنين والخميس)</span>
            <div class="time-grid">
                <div class="slot"><b>01:00</b><span>الساعة ١</span></div>
                <div class="slot"><b>02:00</b><span>الساعة ٢</span></div>
                <div class="slot"><b>03:00</b><span>الساعة ٣</span></div>
                <div class="slot"><b>05:00</b><span>الساعة ٥</span></div>
            </div>
        </div>

        <div class="mega-card" style="border-color: var(--s);">
            <h2 style="color: var(--s);">الجمالية</h2>
            <span class="sub-loc">سنتر A2Z القديم (السبت والثلاثاء)</span>
            <div class="time-grid">
                <div class="slot"><b>01:00</b><span>الساعة ١</span></div>
                <div class="slot"><b>02:00</b><span>الساعة ٢</span></div>
            </div>
        </div>

        <div class="mega-card" style="border-color: var(--t);">
            <h2 style="color: var(--t);">الفروسات</h2>
            <span class="sub-loc">الأحد والأربعاء</span>
            <div class="time-grid" style="grid-template-columns: 1fr;">
                <div class="slot"><b>04:00</b><span>الساعة ٤</span></div>
            </div>
        </div>

        <div class="mega-card" style="border-color: #fff;">
            <h2 style="color: #fff;">سنتر فيوتشر</h2>
            <span class="sub-loc">الصف الثالث الثانوي فقط</span>
            <div class="time-grid" style="grid-template-columns: 1fr;">
                <div class="slot"><b>ELITE CLASS</b><span>2026</span></div>
            </div>
        </div>
    </div>

    <div class="photo-gallery">
        <div class="photo-item">
            <img src="https://i.postimg.cc/6Q7pcnD4/IMG-20260415-WA0034.jpg">
            <div class="overlay-text">فن شرح العلوم المتكاملة</div>
        </div>
        <div class="photo-item">
            <img src="https://i.postimg.cc/WbbjS0kX/IMG-20260118-WA0027.jpg">
            <div class="overlay-text">فن تلخيص الأحياء</div>
        </div>
    </div>

    <a href="https://wa.me/201226694136" class="portal-btn">CONTACT</a>

    <footer>
        DESIGNED BY AMAL | 2026
    </footer>

    <script>
        // Particles Engine
        const canvas = document.getElementById('core-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        function init() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
        window.addEventListener('resize', init); init();
        class P {
            constructor() { this.x = Math.random()*canvas.width; this.y = Math.random()*canvas.height; this.v = 0.5; }
            update() { this.y -= this.v; if(this.y<0) this.y=canvas.height; }
            draw() { ctx.fillStyle='rgba(0,242,255,0.2)'; ctx.fillRect(this.x,this.y,2,2); }
        }
        for(let i=0; i<50; i++) particles.push(new P());
        function anim() { ctx.clearRect(0,0,canvas.width,canvas.height); particles.forEach(p=>{p.update();p.draw();}); requestAnimationFrame(anim); }
        anim();

        // 3D Donut
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / 350, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, 350);
        document.getElementById('hero-3d').appendChild(renderer.domElement);
        const geo = new THREE.TorusKnotGeometry(1, 0.3, 100, 16);
        const mat = new THREE.MeshPhongMaterial({ color: 0x00f2ff, wireframe: true });
        const mesh = new THREE.Mesh(geo, mat);
        scene.add(mesh);
        scene.add(new THREE.PointLight(0xffffff, 1), new THREE.AmbientLight(0xffffff, 0.5));
        camera.position.z = 3.5;
        function render() { requestAnimationFrame(render); mesh.rotation.y += 0.01; renderer.render(scene, camera); }
        render();
    </script>
</body>
</html>
