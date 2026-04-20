<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Adarsh Verma | Electronics Engineer Portfolio</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Three.js Core for 3D background effect -->
  <script type="importmap">
    {
      "imports": {
        "three": "https://unpkg.com/three@0.128.0/build/three.module.js"
      }
    }
  </script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', 'Space Grotesk', sans-serif;
      background: radial-gradient(circle at 20% 30%, #0a0f1e, #03050b);
      color: #eef5ff;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    /* 3D canvas background */
    #canvas-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      pointer-events: none;
      opacity: 0.35;
    }

    /* main content layer */
    .content {
      position: relative;
      z-index: 2;
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 1.5rem 4rem;
    }

    /* glassmorphism + 3D card style */
    .glass-card {
      background: rgba(15, 25, 45, 0.55);
      backdrop-filter: blur(12px);
      border-radius: 2rem;
      border: 1px solid rgba(0, 247, 255, 0.25);
      box-shadow: 0 25px 40px -12px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(0, 247, 255, 0.1) inset;
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      border-color: rgba(0, 247, 255, 0.6);
      box-shadow: 0 30px 45px -12px rgba(0, 200, 255, 0.2), 0 0 0 1px rgba(0, 247, 255, 0.3) inset;
      transform: translateY(-5px);
    }

    /* 3D tilt effect on cards (subtle) */
    .tilt-3d {
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .hero-section {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 2rem;
      margin-bottom: 3rem;
      padding: 2rem;
    }

    .hero-left h1 {
      font-size: 3.2rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #00f7ff, #3a86ff);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
    }

    .badge {
      display: inline-block;
      background: rgba(0, 247, 255, 0.2);
      border-left: 3px solid #00f7ff;
      padding: 0.3rem 1rem;
      border-radius: 2rem;
      font-size: 0.9rem;
      font-weight: 500;
      margin: 1rem 0;
    }

    .contact-info {
      display: flex;
      gap: 1.2rem;
      flex-wrap: wrap;
      margin-top: 1rem;
    }

    .contact-info a {
      color: #b9e2ff;
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.95rem;
      background: rgba(255,255,255,0.05);
      padding: 6px 14px;
      border-radius: 40px;
      transition: 0.2s;
    }

    .contact-info a:hover {
      background: #00f7ff20;
      color: #00f7ff;
      transform: scale(1.02);
    }

    .section-title {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 1.5rem;
      display: inline-block;
      background: linear-gradient(120deg, #fff, #00f7ff);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.3px;
      border-left: 5px solid #00f7ff;
      padding-left: 1rem;
    }

    /* grid layouts */
    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 2rem;
      margin-top: 1rem;
    }

    .skills-container {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      margin: 1.5rem 0;
    }

    .skill-icon {
      display: flex;
      flex-direction: column;
      align-items: center;
      background: rgba(0, 30, 50, 0.6);
      backdrop-filter: blur(4px);
      padding: 0.8rem 1.2rem;
      border-radius: 1.5rem;
      transition: all 0.2s ease;
      border: 1px solid rgba(0,247,255,0.2);
      min-width: 85px;
    }

    .skill-icon i, .skill-icon svg {
      font-size: 2.2rem;
      margin-bottom: 8px;
    }

    .skill-icon span {
      font-size: 0.8rem;
      font-weight: 500;
    }

    .skill-icon:hover {
      transform: translateY(-6px) scale(1.02);
      background: rgba(0, 247, 255, 0.15);
      border-color: #00f7ff;
      box-shadow: 0 10px 20px -5px rgba(0,247,255,0.3);
    }

    .project-highlight {
      background: rgba(0,0,0,0.3);
      padding: 1.2rem;
      border-radius: 1.5rem;
      margin-top: 1rem;
      border-left: 3px solid #00f7ff;
    }

    .footer-note {
      text-align: center;
      margin-top: 4rem;
      font-size: 0.85rem;
      opacity: 0.7;
    }

    /* Responsive */
    @media (max-width: 760px) {
      .hero-left h1 {
        font-size: 2.2rem;
      }
      .content {
        padding: 1rem;
      }
      .hero-section {
        flex-direction: column;
        text-align: center;
      }
      .contact-info {
        justify-content: center;
      }
    }

    /* custom scroll */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #0a0f1e;
    }
    ::-webkit-scrollbar-thumb {
      background: #00f7ff;
      border-radius: 10px;
    }
  </style>
</head>
<body>

<div id="canvas-container"></div>

<div class="content">
  <!-- Hero Section -->
  <div class="glass-card hero-section tilt-3d">
    <div class="hero-left">
      <h1>Adarsh Verma <span style="font-size: 2rem;">⚡</span></h1>
      <div class="badge">
        <i class="fas fa-microchip"></i> B.Tech (ECE) | Embedded Systems & IoT Enthusiast
      </div>
      <p style="max-width: 550px; margin-top: 0.5rem; line-height: 1.5;">
        Aspiring Electronics Engineer | Circuit Design | Hardware-Software Integration
      </p>
      <div class="contact-info">
        <a href="#"><i class="fas fa-map-marker-alt"></i> Delhi, India</a>
        <a href="mailto:adarsh.verma@example.com"><i class="fas fa-envelope"></i> adarsh.verma@edu.in</a>
        <a href="#"><i class="fab fa-linkedin"></i> LinkedIn</a>
        <a href="#"><i class="fab fa-github"></i> GitHub</a>
      </div>
    </div>
    <div style="font-size: 4rem; opacity: 0.8;">
      <i class="fas fa-microchip"></i> 
      <i class="fas fa-robot"></i>
    </div>
  </div>

  <!-- About + Education grid -->
  <div class="grid-2">
    <!-- About Card -->
    <div class="glass-card tilt-3d" style="padding: 1.8rem;">
      <h2 class="section-title" style="border-left: none; padding-left:0; background: none; color:#00f7ff; font-size: 1.7rem;"><i class="fas fa-user-astronaut"></i> About</h2>
      <p style="line-height: 1.6; margin-top: 0.5rem;">
        I am a motivated B.Tech student in Electronics and Communication Engineering at <strong>Gautam Buddha University</strong> with a strong interest in embedded systems, circuit design, and emerging communication technologies.
      </p>
      <div class="project-highlight">
        <i class="fas fa-heartbeat" style="color: #00f7ff; margin-right: 8px;"></i> <strong>Dual Display Smart Health Monitoring System with Alert Mechanism</strong>
        <p style="font-size: 0.9rem; margin-top: 8px;">Sensor integration, microcontroller interfacing, real-time alert system — strengthened hardware-software integration and system optimization.</p>
      </div>
      <p style="margin-top: 1rem;">
        I continuously enhance my technical skills in embedded systems, IoT, and programming. Seeking internships, research collaborations where I can contribute, learn, and grow as a future electronics engineer.
      </p>
    </div>

    <!-- Education Card -->
    <div class="glass-card tilt-3d" style="padding: 1.8rem;">
      <h2 class="section-title" style="border-left: none; padding-left:0; background: none; color:#00f7ff; font-size: 1.7rem;"><i class="fas fa-graduation-cap"></i> Education</h2>
      <div style="margin-bottom: 1rem;">
        <h3 style="font-size: 1.4rem; font-weight: 700;">Gautam Buddha University</h3>
        <p style="color: #bbf0ff;">Bachelor of Technology - B.Tech, Electrical and Electronics Engineering (ECE)<br>2025 – Present</p>
      </div>
      <div>
        <strong>Core Coursework & Skills:</strong>
        <div class="skills-container" style="margin-top: 0.5rem; gap: 0.6rem;">
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">🐍 Python</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">⚡ C Programming</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">🌐 HTML</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">🔌 Embedded Systems</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">📡 Analog Electronics</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">📶 Signal & Systems</span>
          <span class="skill-icon" style="padding: 0.4rem 0.8rem; min-width: auto;">🌍 IoT Basics</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Skills & Tech Stack (with Canva, Python, C, HTML, VS Code logos) -->
  <div class="glass-card tilt-3d" style="margin-top: 2rem; padding: 1.8rem;">
    <h2 class="section-title" style="border-left: none; padding-left:0; background: none; color:#00f7ff;"><i class="fas fa-cogs"></i> Tech Stack & Tools</h2>
    <div class="skills-container" style="justify-content: flex-start;">
      <!-- Python -->
      <div class="skill-icon"><i class="fab fa-python"></i><span>Python</span></div>
      <!-- C / C++ style (using code icon) -->
      <div class="skill-icon"><i class="fas fa-code"></i><span>C Language</span></div>
      <!-- HTML5 -->
      <div class="skill-icon"><i class="fab fa-html5"></i><span>HTML5</span></div>
      <!-- Canva (custom via brand) -->
      <div class="skill-icon"><i class="fab fa-canva"></i><span>Canva</span></div>
      <!-- VS Code -->
      <div class="skill-icon"><i class="fas fa-code-branch"></i><span>VS Code</span></div>
      <!-- Embedded Systems (custom icon) -->
      <div class="skill-icon"><i class="fas fa-microchip"></i><span>Embedded</span></div>
      <!-- IoT -->
      <div class="skill-icon"><i class="fas fa-wifi"></i><span>IoT</span></div>
      <!-- Circuit Design -->
      <div class="skill-icon"><i class="fas fa-bolt"></i><span>Circuit Design</span></div>
    </div>
    <p style="margin-top: 1rem; font-size: 0.9rem;"><i class="fas fa-tools"></i> Also experienced with Microcontrollers, Sensor Interfacing, Arduino, and real-time alert systems.</p>
  </div>

  <!-- Additional: Core Skills & Strengths (from the student description) -->
  <div class="grid-2" style="margin-top: 2rem;">
    <div class="glass-card tilt-3d" style="padding: 1.8rem;">
      <h3 style="font-size: 1.4rem; margin-bottom: 1rem; display: flex; gap: 10px;"><i class="fas fa-chalkboard-user"></i> Technical Strengths</h3>
      <ul style="list-style: none; line-height: 2;">
        <li><i class="fas fa-check-circle" style="color:#00f7ff;"></i> Embedded C & Microcontroller Programming</li>
        <li><i class="fas fa-check-circle" style="color:#00f7ff;"></i> Analog & Digital Circuit Design</li>
        <li><i class="fas fa-check-circle" style="color:#00f7ff;"></i> Sensor Integration & Real-time Alerts</li>
        <li><i class="fas fa-check-circle" style="color:#00f7ff;"></i> IoT Basics (MQTT, cloud connectivity)</li>
        <li><i class="fas fa-check-circle" style="color:#00f7ff;"></i> Hardware-Software Co-design</li>
      </ul>
    </div>
    <div class="glass-card tilt-3d" style="padding: 1.8rem;">
      <h3 style="font-size: 1.4rem; margin-bottom: 1rem;"><i class="fas fa-bullhorn"></i> Beyond Academics</h3>
      <p>Passionate about emerging communication technologies, always eager to learn new microcontrollers, RTOS concepts, and contribute to open-source hardware projects. Looking forward to building impactful electronics solutions for healthcare and automation.</p>
      <div style="margin-top: 1rem;">
        <span class="badge" style="background:#00f7ff10;">🔍 Open for Internships</span>
        <span class="badge" style="background:#00f7ff10;">🤝 Research Collaborations</span>
      </div>
    </div>
  </div>

  <!-- mini footer / social / animated 3d effect citation -->
  <div class="footer-note">
    <i class="fas fa-microchip"></i> Adarsh Verma — Embedded Systems & Electronics | “Innovating at the intersection of hardware and intelligence”
    <br><span style="font-size: 0.7rem;">⚡ 3D Interactive Background | Built with Three.js</span>
  </div>
</div>

<!-- Three.js Dynamic 3D Scene (floating particles, cubes, tech vibe) -->
<script type="module">
  import * as THREE from 'three';

  const container = document.getElementById('canvas-container');
  const scene = new THREE.Scene();
  scene.background = null; // transparent to show gradient body
  scene.fog = new THREE.FogExp2(0x03050b, 0.003); // subtle depth

  const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
  camera.position.set(0, 2, 12);
  camera.lookAt(0, 0, 0);

  const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.setPixelRatio(window.devicePixelRatio);
  renderer.setClearColor(0x000000, 0);
  container.appendChild(renderer.domElement);

  // --- Objects: floating rings, toruses, microchip-like geometries for 3D effect ---
  const group = new THREE.Group();

  // Central glowing torus knot (electronics vibe)
  const geometryKnot = new THREE.TorusKnotGeometry(1.2, 0.28, 180, 24, 3, 4);
  const materialKnot = new THREE.MeshStandardMaterial({ color: 0x00aaff, emissive: 0x004466, roughness: 0.3, metalness: 0.7 });
  const knot = new THREE.Mesh(geometryKnot, materialKnot);
  knot.position.x = -1.2;
  knot.position.y = -0.2;
  group.add(knot);

  // Floating rings
  const ringGeo = new THREE.TorusGeometry(1.8, 0.08, 64, 200);
  const ringMat = new THREE.MeshStandardMaterial({ color: 0x00f7ff, emissive: 0x005577 });
  const ring = new THREE.Mesh(ringGeo, ringMat);
  ring.rotation.x = Math.PI / 2;
  ring.position.x = 1.5;
  ring.position.y = 0.5;
  group.add(ring);

  const ring2Geo = new THREE.TorusGeometry(2.1, 0.06, 64, 200);
  const ring2Mat = new THREE.MeshStandardMaterial({ color: 0x3a86ff, emissive: 0x002244 });
  const ring2 = new THREE.Mesh(ring2Geo, ring2Mat);
  ring2.rotation.z = Math.PI / 3;
  ring2.rotation.x = 0.8;
  ring2.position.set(-0.5, -1, -1);
  group.add(ring2);

  // small cubes (representing chips)
  const chipMat = new THREE.MeshStandardMaterial({ color: 0x88aaff, emissive: 0x224466, roughness: 0.2 });
  for (let i = 0; i < 45; i++) {
    const size = 0.08 + Math.random() * 0.07;
    const cube = new THREE.Mesh(new THREE.BoxGeometry(size, size, size), chipMat);
    const radius = 3.2 + Math.random() * 1.5;
    const theta = Math.random() * Math.PI * 2;
    const phi = Math.acos(2 * Math.random() - 1);
    cube.position.x = radius * Math.sin(phi) * Math.cos(theta);
    cube.position.y = radius * Math.sin(phi) * Math.sin(theta) * 0.8;
    cube.position.z = radius * Math.cos(phi) - 1;
    cube.userData = { speed: 0.002 + Math.random() * 0.005, axis: Math.random() > 0.5 ? 'y' : 'x' };
    group.add(cube);
  }

  // particles (star field)
  const particleCount = 800;
  const particlesGeometry = new THREE.BufferGeometry();
  const positions = new Float32Array(particleCount * 3);
  for (let i = 0; i < particleCount; i++) {
    positions[i*3] = (Math.random() - 0.5) * 50;
    positions[i*3+1] = (Math.random() - 0.5) * 25;
    positions[i*3+2] = (Math.random() - 0.5) * 30 - 15;
  }
  particlesGeometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  const particleMat = new THREE.PointsMaterial({ color: 0x66ccff, size: 0.08, transparent: true, opacity: 0.5 });
  const particles = new THREE.Points(particlesGeometry, particleMat);
  group.add(particles);

  // Additional glowing sphere (ambient light effect)
  const glowGeo = new THREE.SphereGeometry(0.45, 16, 16);
  const glowMat = new THREE.MeshStandardMaterial({ color: 0x00ccff, emissive: 0x0077aa });
  const coreGlow = new THREE.Mesh(glowGeo, glowMat);
  coreGlow.position.set(1.8, 1.2, -1.5);
  group.add(coreGlow);

  scene.add(group);

  // Lighting: dynamic colors
  const ambientLight = new THREE.AmbientLight(0x111122);
  scene.add(ambientLight);
  const dirLight = new THREE.DirectionalLight(0xffffff, 1);
  dirLight.position.set(2, 5, 3);
  scene.add(dirLight);
  const backLight = new THREE.PointLight(0x2266ff, 0.6);
  backLight.position.set(-2, 1, -4);
  scene.add(backLight);
  const fillLight = new THREE.PointLight(0xffaa33, 0.4);
  fillLight.position.set(1, 2, 2);
  scene.add(fillLight);
  
  const colorLight = new THREE.PointLight(0x00f7ff, 0.5);
  colorLight.position.set(0.5, 1, 2);
  scene.add(colorLight);

  let time = 0;
  function animate() {
    requestAnimationFrame(animate);
    time += 0.008;
    
    // rotate main knot and rings for dynamic 3D feel
    knot.rotation.x += 0.005;
    knot.rotation.y += 0.007;
    knot.rotation.z += 0.003;
    ring.rotation.z += 0.004;
    ring2.rotation.x += 0.003;
    ring2.rotation.y += 0.002;
    coreGlow.scale.setScalar(1 + Math.sin(time * 3) * 0.05);
    
    // rotate particles slowly
    particles.rotation.y += 0.0005;
    particles.rotation.x += 0.0003;
    
    // floating cubes rotation individually (extra)
    group.children.forEach(child => {
      if (child.isMesh && child.geometry.type === 'BoxGeometry' && child !== knot && child !== ring && child !== ring2) {
        child.rotation.x += 0.01;
        child.rotation.y += 0.015;
      }
    });
    
    // subtle camera motion
    camera.position.x += (0 - camera.position.x) * 0.02;
    camera.position.y += (0.2 - camera.position.y) * 0.02;
    camera.lookAt(0, 0, 0);
    
    renderer.render(scene, camera);
  }
  
  animate();

  window.addEventListener('resize', onWindowResize, false);
  function onWindowResize() {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  }
  
  // little mouse parallax (extra 3D feel)
  document.addEventListener('mousemove', (event) => {
    const mouseX = (event.clientX / window.innerWidth) * 2 - 1;
    const mouseY = (event.clientY / window.innerHeight) * 2 - 1;
    group.rotation.y = mouseX * 0.2;
    group.rotation.x = mouseY * 0.1;
  });
</script>

<!-- Additional simple tilt effect for cards using vanilla JS (optional) -->
<script>
  // subtle 3D card tilt on hover (based on mouse movement)
  const cards = document.querySelectorAll('.tilt-3d');
  cards.forEach(card => {
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      const centerX = rect.width / 2;
      const centerY = rect.height / 2;
      const rotateX = (y - centerY) / 25;
      const rotateY = (centerX - x) / 25;
      card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-4px)`;
    });
    card.addEventListener('mouseleave', () => {
      card.style.transform = 'perspective(1000px) rotateX(0deg) rotateY(0deg) translateY(0px)';
    });
  });
</script>

</body>
</html>
