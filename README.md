<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alec Borman | The Black Box Architect</title>
    
    <meta name="description" content="Alec Borman is a Senior Salesforce Architect specializing in the 'Black Box' methodology. He builds scalable revenue engines using Salesforce, Apex, and Zapier.">
    <meta name="keywords" content="Alec Borman, Salesforce Architect, Black Box Architect, Apex, LWC, Hydrolix, RevOps, Zapier, Houston">
    <meta name="author" content="Alec Borman">
    <meta name="robots" content="index, follow">

    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⚡</text></svg>">
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Fira Code', 'monospace'],
                    },
                    colors: {
                        slate: { 850: '#151e2e' }
                    }
                },
            },
        }
    </script>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">

    <script src="https://unpkg.com/lucide-icons" defer></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js" defer></script>

    <style>
        /* Base Styles */
        body { font-family: 'Inter', sans-serif; scroll-padding-top: 80px; -webkit-font-smoothing: antialiased; }
        :root { --accent: #38bdf8; }
        
        /* Themes */
        .dark body { background-color: #0F172A; color: #CBD5E1; }
        .light body { background-color: #F8FAFC; color: #1E293B; }
        
        /* Canvas & Cursor */
        #bg-canvas { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: -10; opacity: 0.4; pointer-events: none; }
        .light #bg-canvas { opacity: 0.2; }
        
        body.custom-cursor-active { cursor: none; }
        #cursor-dot, #cursor-outline { position: fixed; top: 0; left: 0; transform: translate(-50%, -50%); border-radius: 50%; pointer-events: none; z-index: 9999; opacity: 0; }
        body.custom-cursor-active #cursor-dot, body.custom-cursor-active #cursor-outline { opacity: 1; }
        #cursor-dot { width: 8px; height: 8px; background-color: var(--accent); }
        #cursor-outline { width: 40px; height: 40px; border: 2px solid var(--accent); opacity: 0.5; transition: transform 0.1s, width 0.3s, height 0.3s; }
        body.cursor-hover #cursor-outline { width: 60px; height: 60px; background-color: rgba(56, 189, 248, 0.1); border-color: #818cf8; }

        /* Scroll Progress */
        #scroll-progress { position: fixed; top: 0; left: 0; height: 3px; background: linear-gradient(90deg, #38bdf8, #818cf8); width: 0%; z-index: 10000; }

        /* Command Palette */
        #command-palette { position: fixed; top: 20%; left: 50%; transform: translate(-50%, -50%) scale(0.95); width: 90%; max-width: 500px; z-index: 10001; opacity: 0; pointer-events: none; transition: all 0.2s ease-out; box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5); }
        #command-palette.visible { transform: translate(-50%, -50%) scale(1); opacity: 1; pointer-events: all; }
        .cmd-palette-content { backdrop-filter: blur(12px); border-radius: 12px; overflow: hidden; }
        .dark .cmd-palette-content { background-color: rgba(15, 23, 42, 0.95); border: 1px solid #334155; }
        .light .cmd-palette-content { background-color: rgba(255, 255, 255, 0.95); border: 1px solid #CBD5E1; }
        #command-palette-input { background: transparent; border: none; padding: 1.25rem; width: 100%; outline: none; }
        .dark #command-palette-input { color: white; border-bottom: 1px solid #334155; }
        .light #command-palette-input { color: #0F172A; border-bottom: 1px solid #E2E8F0; }
        .command-item { padding: 0.75rem 1.25rem; cursor: pointer; display: flex; align-items: center; gap: 0.75rem; transition: all 0.15s; }
        .command-item:hover, .command-item.selected { background-color: rgba(56, 189, 248, 0.15); color: #38bdf8; border-left: 3px solid #38bdf8; }
        #command-palette-overlay { position: fixed; inset: 0; background-color: rgba(0,0,0,0.6); z-index: 10000; opacity: 0; pointer-events: none; transition: opacity 0.2s; backdrop-filter: blur(2px); }
        #command-palette-overlay.visible { opacity: 1; pointer-events: all; }

        /* Animations */
        [data-stagger-reveal] { opacity: 0; transform: translateY(20px); transition: opacity 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1); }
        [data-stagger-reveal].is-revealed { opacity: 1; transform: translateY(0); }

        /* Typography & Components */
        .nav-link { position: relative; font-weight: 500; }
        .nav-link::after { content: ''; position: absolute; width: 0; height: 2px; bottom: -4px; left: 0; background-color: var(--accent); transition: width 0.3s; }
        .nav-link:hover::after, .nav-link.active::after { width: 100%; }
        .nav-link.active { color: var(--accent); }
        
        .project-card { border: 1px solid transparent; display: flex; flex-direction: column; transition: transform 0.3s, box-shadow 0.3s; border-radius: 0.75rem; overflow: hidden; }
        .dark .project-card { background: linear-gradient(#1E293B, #1E293B) padding-box, linear-gradient(135deg, #38bdf8, #818cf8) border-box; }
        .light .project-card { background: white; border: 1px solid #E2E8F0; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }
        .project-card:hover { transform: translateY(-5px); }

        .timeline-item { position: relative; padding-left: 2rem; padding-bottom: 2.5rem; border-left: 2px solid; }
        .dark .timeline-item { border-color: #334155; }
        .light .timeline-item { border-color: #E2E8F0; }
        .timeline-item:last-child { border-color: transparent; }
        .timeline-dot { position: absolute; left: -9px; top: 5px; width: 16px; height: 16px; background: var(--accent); border-radius: 50%; border: 4px solid; }
        .dark .timeline-dot { border-color: #0F172A; }
        .light .timeline-dot { border-color: #F8FAFC; }

        .prose h2 { font-size: 1.8rem; font-weight: 800; margin-bottom: 1rem; color: var(--accent); }
        .prose h3 { font-size: 1.5rem; font-weight: 700; margin-top: 2rem; margin-bottom: 1rem; }
        .prose p { margin-bottom: 1.25rem; line-height: 1.8; }
        .prose blockquote { border-left: 4px solid var(--accent); padding-left: 1rem; font-style: italic; margin: 1.5rem 0; opacity: 0.8; }

        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
            #bg-canvas, #cursor-dot, #cursor-outline { display: none !important; }
            body { cursor: auto !important; }
        }
    </style>
</head>
<body class="antialiased dark">

    <div id="scroll-progress"></div>
    <div id="cursor-dot"></div>
    <div id="cursor-outline"></div>
    <canvas id="bg-canvas"></canvas>
    
    <div id="command-palette-overlay" aria-hidden="true"></div>
    <div id="command-palette" role="dialog" aria-modal="true" aria-labelledby="command-palette-input">
        <div class="cmd-palette-content">
            <input type="text" id="command-palette-input" placeholder="Jump to... (Ctrl+K)" autocomplete="off">
            <div id="command-palette-list">
                <a href="#home" class="command-item"><i data-lucide="home" class="w-4 h-4"></i>Home<kbd>H</kbd></a>
                <a href="#about" class="command-item"><i data-lucide="user" class="w-4 h-4"></i>About<kbd>A</kbd></a>
                <a href="#experience" class="command-item"><i data-lucide="briefcase" class="w-4 h-4"></i>Experience<kbd>E</kbd></a>
                <a href="#projects" class="command-item"><i data-lucide="layers" class="w-4 h-4"></i>Projects<kbd>P</kbd></a>
                <a href="#book" class="command-item"><i data-lucide="book" class="w-4 h-4"></i>Book<kbd>B</kbd></a>
                <a href="#contact" class="command-item"><i data-lucide="mail" class="w-4 h-4"></i>Contact<kbd>C</kbd></a>
            </div>
        </div>
    </div>

    <header id="header" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#home" class="text-xl font-bold flex items-center gap-2 group" data-magnetic>
                <i data-lucide="code-2" class="text-sky-400 transition-transform group-hover:rotate-12"></i>
                <span class="light:text-slate-900 dark:text-white">Alec <span class="text-sky-400">Borman</span></span>
            </a>
            <div class="hidden md:flex items-center space-x-8">
                <a href="#home" class="nav-link light:text-slate-700 dark:text-slate-300">Home</a>
                <a href="#about" class="nav-link light:text-slate-700 dark:text-slate-300">About</a>
                <a href="#experience" class="nav-link light:text-slate-700 dark:text-slate-300">Experience</a>
                <a href="#projects" class="nav-link light:text-slate-700 dark:text-slate-300">Projects</a>
                <a href="#book" class="nav-link light:text-slate-700 dark:text-slate-300">Book</a>
                <a href="#contact" class="nav-link light:text-slate-700 dark:text-slate-300">Contact</a>
                <button id="theme-toggle" class="p-2 rounded-full hover:bg-sky-500/10 transition-colors" data-magnetic>
                    <i data-lucide="sun" class="w-5 h-5 hidden dark:block text-sky-400"></i>
                    <i data-lucide="moon" class="w-5 h-5 block dark:hidden text-slate-700"></i>
                </button>
            </div>
            <button id="mobile-menu-btn" class="md:hidden p-2 light:text-slate-700 dark:text-white relative z-50">
                <i data-lucide="menu" class="w-6 h-6"></i>
            </button>
        </nav>
        <div id="mobile-menu" class="fixed inset-0 bg-slate-100 dark:bg-slate-900 z-40 transform translate-x-full transition-transform duration-300 flex flex-col justify-center items-center space-y-8 md:hidden">
            <a href="#home" class="text-2xl font-bold nav-link-mobile">Home</a>
            <a href="#about" class="text-2xl font-bold nav-link-mobile">About</a>
            <a href="#experience" class="text-2xl font-bold nav-link-mobile">Experience</a>
            <a href="#projects" class="text-2xl font-bold nav-link-mobile">Projects</a>
            <a href="#book" class="text-2xl font-bold nav-link-mobile">Book</a>
            <a href="#contact" class="text-2xl font-bold nav-link-mobile">Contact</a>
            <button id="theme-toggle-mobile" class="text-xl font-medium flex items-center gap-2 mt-8">Switch Theme</button>
        </div>
    </header>

    <main class="container mx-auto px-6 relative z-10">

        <section id="home" class="min-h-screen flex items-center justify-center pt-20">
            <div data-stagger-container class="max-w-4xl w-full">
                <div data-stagger-reveal class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-sky-500/30 bg-sky-500/10 text-sky-400 text-xs font-bold uppercase tracking-widest mb-6">
                    <span class="w-2 h-2 rounded-full bg-sky-400 animate-pulse"></span>
                    Available for Contracts
                </div>
                <h1 data-stagger-reveal class="text-5xl md:text-7xl lg:text-8xl font-black tracking-tight mb-8 light:text-slate-900 dark:text-white leading-[1.1]">
                    Systems.<br><span class="text-transparent bg-clip-text bg-gradient-to-r from-sky-400 to-indigo-500">Architected.</span>
                </h1>
                <p data-stagger-reveal class="text-lg md:text-xl font-light light:text-slate-600 dark:text-slate-400 max-w-2xl mb-10 leading-relaxed">
                    I translate chaotic business needs into secure, scalable engines. I don't just fix tickets; I apply the <strong>"Black Box"</strong> methodology to build the operational backbone of high-growth companies.
                </p>
                <div data-stagger-reveal class="flex flex-col sm:flex-row gap-5">
                    <a href="#projects" class="px-8 py-4 bg-sky-500 text-white font-semibold rounded-lg shadow-lg hover:shadow-sky-500/40 hover:-translate-y-1 transition-all" data-magnetic>View Projects</a>
                    <a href="#contact" class="px-8 py-4 font-semibold rounded-lg border light:border-slate-300 dark:border-slate-700 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all hover:-translate-y-1" data-magnetic>Get In Touch</a>
                </div>
            </div>
        </section>

        <section id="about" class="py-24">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center" data-stagger-container>
                <div data-stagger-reveal>
                    <h2 class="text-3xl font-bold mb-8 light:text-slate-900 dark:text-white"><span class="text-sky-400 font-mono text-2xl mr-2">01.</span> About Me</h2>
                    <div class="space-y-4 text-lg light:text-slate-600 dark:text-slate-400 leading-relaxed">
                        <p>I am a Salesforce Architect and UT Dallas CS graduate. My career evolved from front-line IT to architecting the revenue engines for companies like Hydrolix.</p>
                        <p>I specialize in tuning out "visual noise" to understand the shape of data. This allows me to build systems that don't just work today, but scale for the next decade.</p>
                    </div>
                </div>
                <div data-stagger-reveal class="relative group">
                    <div class="absolute inset-0 bg-sky-500/20 rounded-lg transform translate-x-3 translate-y-3 transition-transform group-hover:translate-x-2 group-hover:translate-y-2"></div>
                    <div class="relative bg-slate-800 p-8 rounded-lg border border-slate-700 hover:border-sky-400/50 transition-colors">
                        <h3 class="text-white font-bold mb-4">Core Stack</h3>
                        <ul class="grid grid-cols-2 gap-3 font-mono text-sm text-slate-400">
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Salesforce Architect</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Apex & LWC</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Zapier Logic</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Glovia OM / ERP</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="experience" class="py-24">
            <h2 class="text-3xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal><span class="text-sky-400 font-mono text-2xl mr-2">02.</span> Experience</h2>
            <div class="max-w-3xl mx-auto" data-stagger-container>
                
                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Oct 2024 – Nov 2025</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Business Systems Architect</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Hydrolix (Remote)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-2">
                        <li><strong>Strategic Pivot:</strong> Owned the Salesforce infrastructure for the "Custom Solutions" division. Following the successful maturation of these processes and the company's strategic pivot toward a pure-play App model, I oversaw the transition and documentation of these systems.</li>
                        <li><strong>Deployment Engine:</strong> Built end-to-end automation handling POC credit approvals, usage quota tracking (TB/month), and automated customer communications.</li>
                        <li><strong>Lead Velocity:</strong> Designed a high-speed ingestion process cutting response time by 40%.</li>
                        <li><strong>Technical Bridge:</strong> Acted as the translation layer between Commercial Sales and Engineering.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Jun 2024 – Aug 2024</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Salesforce Architect</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Jaco Aerospace (Contract)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-2">
                        <li>Optimized Sales Cloud and Glovia OM ERP integration.</li>
                        <li>Designed custom Apex logic to overcome managed package limitations.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Mar 2022 – Oct 2023</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Salesforce Developer</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Fujitsu / Royal Canin</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-2">
                        <li>Lead Developer for the Glovia OM managed package.</li>
                        <li>Resolved complex supply chain logic issues and integrated Order Management features.</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="book" class="py-24">
            <div data-stagger-container>
                <h2 class="text-3xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal><span class="text-sky-400 font-mono text-2xl mr-2">03.</span> The Black Box</h2>
                <div class="prose max-w-3xl mx-auto light:text-slate-700 dark:text-slate-300" data-stagger-reveal>
                    <p class="font-mono text-sm text-sky-400 mb-4">Excerpt from Chapter 1</p>
                    <h2>The "Black Box" Mindset</h2>
                    <p>The meeting request is vague: "Discuss Sales-to-Ops Handoff." The VP of Sales wants a Zap to copy data to a Google Sheet. "It seems simple," he says.</p>
                    <p>The <strong>Technician</strong> builds the Zap. Five-minute fix. Ticket closed. But they created a "Data Trap"—a fractured process that breaks the moment a deal is updated.</p>
                    <p>The <strong>Architect</strong> makes a different choice.</p>
                    <blockquote>"The technician gets to be the hero for a day. The architect has to live with the consequences for a decade."</blockquote>
                    <h3>Choosing Focus</h3>
                    <p>The Architect employs the "Black Box" mindset. They tune out the visual noise (Zapier icons, Sheets) and feel for the shape of the data.</p>
                    <ol>
                        <li><strong>Shape:</strong> Is it a transaction or a state? (It's a state).</li>
                        <li><strong>Weight:</strong> What is the pain? (Blindness, not manual entry).</li>
                    </ol>
                    <p>The solution is not a Zap. The solution is a shared object inside Salesforce—a "Deployment" record triggered by Flow. One source of truth. Zero data drift.</p>
                </div>
            </div>
        </section>

        <section id="contact" class="py-24 mb-20">
             <div class="max-w-2xl mx-auto text-center" data-stagger-container>
                <h2 class="text-3xl font-bold mb-6 light:text-slate-900 dark:text-white" data-stagger-reveal>Get In Touch</h2>
                <p class="text-lg text-slate-500 dark:text-slate-400 mb-12" data-stagger-reveal>I'm open to discussing new projects, Salesforce architecture, or full-time opportunities.</p>
                <div class="flex flex-col md:flex-row justify-center gap-6" data-stagger-reveal>
                     <div class="flex items-center gap-4 bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 p-4 rounded-lg cursor-pointer w-full hover:bg-sky-500/10 transition-colors" onclick="navigator.clipboard.writeText('2175087210')">
                        <i data-lucide="phone" class="text-sky-400"></i>
                        <div class="text-left"><div class="text-xs uppercase font-bold text-slate-500">Phone</div><div class="font-mono light:text-slate-900 dark:text-white">(217) 508-7210</div></div>
                     </div>
                     <div class="flex items-center gap-4 bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 p-4 rounded-lg cursor-pointer w-full hover:bg-sky-500/10 transition-colors" onclick="navigator.clipboard.writeText('alecborman97@gmail.com')">
                        <i data-lucide="mail" class="text-sky-400"></i>
                        <div class="text-left"><div class="text-xs uppercase font-bold text-slate-500">Email</div><div class="font-mono light:text-slate-900 dark:text-white">alecborman97@gmail.com</div></div>
                     </div>
                </div>
             </div>
        </section>
    </main>

    <footer class="py-8 text-center text-sm text-slate-500 relative z-10"><p>&copy; <span id="year"></span> Alec Borman. Built with <span class="text-sky-400">♥</span> and Logic.</p></footer>

    <script>
        // Logic
        const isTouch = ('ontouchstart' in window);
        const prefersReduced = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
        const lerp = (s, e, t) => (1 - t) * s + t * e;

        // Init
        window.onload = () => {
            lucide.createIcons();
            document.getElementById('year').textContent = new Date().getFullYear();
            initTheme(); initCursor(); initThree(); initScroll(); initPalette();
        };

        // Theme
        function initTheme() {
            const toggle = (id) => document.getElementById(id).onclick = () => {
                const isDark = document.documentElement.classList.toggle('dark');
                document.documentElement.classList.toggle('light');
                localStorage.setItem('theme', isDark ? 'dark' : 'light');
            };
            toggle('theme-toggle'); toggle('theme-toggle-mobile');
            document.getElementById('mobile-menu-btn').onclick = () => document.getElementById('mobile-menu').classList.toggle('translate-x-full');
        }

        // Cursor
        function initCursor() {
            if (isTouch || prefersReduced) return;
            document.body.classList.add('custom-cursor-active');
            const dot = document.getElementById('cursor-dot'), out = document.getElementById('cursor-outline');
            let x = 0, y = 0, tx = 0, ty = 0;
            window.onmousemove = e => { tx = e.clientX; ty = e.clientY; dot.style.transform = `translate(${tx}px,${ty}px)`; };
            const loop = () => { x = lerp(x, tx, 0.15); y = lerp(y, ty, 0.15); out.style.transform = `translate(${x}px,${y}px)`; requestAnimationFrame(loop); };
            loop();
            document.querySelectorAll('a, button, .project-card').forEach(el => {
                el.onmouseenter = () => document.body.classList.add('cursor-hover');
                el.onmouseleave = () => document.body.classList.remove('cursor-hover');
            });
        }

        // Three.js
        function initThree() {
            if (prefersReduced || typeof THREE === 'undefined') return;
            const canvas = document.getElementById('bg-canvas');
            const renderer = new THREE.WebGLRenderer({ canvas, alpha: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            const scene = new THREE.Scene(), camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 100);
            camera.position.z = 3;
            const geo = new THREE.BufferGeometry(), count = isTouch ? 1000 : 3000, pos = new Float32Array(count * 3);
            for(let i=0; i<count*3; i++) pos[i] = (Math.random()-0.5)*10;
            geo.setAttribute('position', new THREE.BufferAttribute(pos, 3));
            const mat = new THREE.PointsMaterial({ size: 0.015, color: 0x38bdf8, transparent: true, opacity: 0.6 });
            const mesh = new THREE.Points(geo, mat); scene.add(mesh);
            const animate = () => { mesh.rotation.y += 0.001; renderer.render(scene, camera); requestAnimationFrame(animate); };
            animate();
            window.onresize = () => { camera.aspect = window.innerWidth/window.innerHeight; camera.updateProjectionMatrix(); renderer.setSize(window.innerWidth, window.innerHeight); };
        }

        // Palette
        function initPalette() {
            const p = document.getElementById('command-palette'), o = document.getElementById('command-palette-overlay');
            const toggle = () => { p.classList.toggle('visible'); o.classList.toggle('visible'); if(p.classList.contains('visible')) document.getElementById('command-palette-input').focus(); };
            window.onkeydown = e => { if((e.ctrlKey||e.metaKey) && e.key === 'k') { e.preventDefault(); toggle(); } if(e.key==='Escape') { p.classList.remove('visible'); o.classList.remove('visible'); }};
            o.onclick = toggle;
            document.querySelectorAll('.command-item').forEach(i => i.onclick = () => { toggle(); });
        }

        // Scroll
        function initScroll() {
            window.onscroll = () => {
                const h = document.documentElement, b = document.body, st = 'scrollTop', sh = 'scrollHeight';
                document.getElementById('scroll-progress').style.width = ((h[st]||b[st]) / ((h[sh]||b[sh]) - h.clientHeight) * 100) + "%";
                document.getElementById('header').classList.toggle('backdrop-blur-md', window.scrollY > 50);
                document.getElementById('header').classList.toggle('bg-white/80', window.scrollY > 50);
                document.getElementById('header').classList.toggle('dark:bg-slate-900/80', window.scrollY > 50);
            };
            const obs = new IntersectionObserver(e => e.forEach(i => { if(i.isIntersecting) i.target.classList.add('is-revealed'); }), {threshold: 0.1});
            document.querySelectorAll('[data-stagger-reveal]').forEach(el => obs.observe(el));
        }
    </script>
</body>
</html>
