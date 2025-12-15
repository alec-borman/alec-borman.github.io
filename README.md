<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alec Borman | Business Systems Architect</title>
    
    <meta name="description" content="Alec Borman is a Business Systems Architect and Salesforce Developer based in Texas, specializing in scalable, secure, and automated business solutions.">
    <meta name="keywords" content="Alec Borman, Salesforce Architect, Salesforce Developer, Apex, LWC, Business Systems, RevOps, Houston, Texas">
    <meta name="author" content="Alec Borman">
    <meta name="robots" content="index, follow">

    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⚡</text></svg>">
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class', // Manual toggling via class
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Fira Code', 'monospace'], // Added for code snippets
                    },
                    colors: {
                        slate: {
                            850: '#151e2e', // Custom darker slate
                        }
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
        /* --- Base & Reset --- */
        body {
            font-family: 'Inter', sans-serif;
            scroll-padding-top: 80px; /* Increased for breathing room */
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            /* Cursor hiding is applied via JS class only on non-touch devices */
        }

        /* --- Theme Variables --- */
        :root {
            --accent: #38bdf8; /* sky-400 */
            --accent-glow: rgba(56, 189, 248, 0.5);
        }

        /* Dark/Light Contexts */
        .dark body { background-color: #0F172A; color: #CBD5E1; }
        .light body { background-color: #F8FAFC; color: #1E293B; }
        
        /* --- 1. Background Canvas --- */
        #bg-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: -10; opacity: 0.4; transition: opacity 0.5s ease;
            pointer-events: none;
        }
        .light #bg-canvas { opacity: 0.2; }

        /* --- 2. Custom Cursor (Desktop Only) --- */
        /* Only apply 'cursor: none' when the body has the active class */
        body.custom-cursor-active { cursor: none; }
        
        #cursor-dot, #cursor-outline {
            position: fixed; top: 0; left: 0;
            transform: translate(-50%, -50%);
            border-radius: 50%; pointer-events: none; z-index: 9999;
            /* Hidden by default, shown via JS */
            opacity: 0; 
        }
        body.custom-cursor-active #cursor-dot, 
        body.custom-cursor-active #cursor-outline { opacity: 1; }

        #cursor-dot {
            width: 8px; height: 8px; background-color: var(--accent);
            transition: opacity 0.3s;
        }
        #cursor-outline {
            width: 40px; height: 40px; border: 2px solid var(--accent);
            opacity: 0.5;
            transition: transform 0.1s, width 0.3s, height 0.3s, background-color 0.3s;
        }
        
        /* Hover State */
        body.cursor-hover #cursor-dot { opacity: 0; }
        body.cursor-hover #cursor-outline {
            width: 60px; height: 60px;
            background-color: rgba(56, 189, 248, 0.1);
            border-color: #818cf8;
        }

        /* --- 3. Scroll Progress --- */
        #scroll-progress {
            position: fixed; top: 0; left: 0; height: 3px;
            background: linear-gradient(90deg, #38bdf8, #818cf8);
            width: 0%; z-index: 10000; transition: width 0.1s linear;
        }

        /* --- 4. Command Palette --- */
        #command-palette {
            position: fixed; top: 20%; left: 50%;
            transform: translate(-50%, -50%) scale(0.95);
            width: 90%; max-width: 500px;
            z-index: 10001; opacity: 0; pointer-events: none;
            transition: all 0.2s ease-out;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
        }
        #command-palette.visible {
            transform: translate(-50%, -50%) scale(1);
            opacity: 1; pointer-events: all;
        }
        
        .cmd-palette-content {
            backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
            border-radius: 12px; overflow: hidden;
        }
        .dark .cmd-palette-content { background-color: rgba(15, 23, 42, 0.9); border: 1px solid #334155; }
        .light .cmd-palette-content { background-color: rgba(255, 255, 255, 0.9); border: 1px solid #CBD5E1; }

        #command-palette-input {
            background: transparent; border: none; padding: 1.25rem; width: 100%;
            font-size: 1.1rem; outline: none;
        }
        .dark #command-palette-input { color: white; border-bottom: 1px solid #334155; }
        .light #command-palette-input { color: #0F172A; border-bottom: 1px solid #E2E8F0; }

        .command-item {
            padding: 0.75rem 1.25rem; cursor: pointer; display: flex; align-items: center; gap: 0.75rem;
            transition: all 0.15s; font-size: 0.95rem;
        }
        .command-item.selected, .command-item:hover {
            background-color: rgba(56, 189, 248, 0.15); color: #38bdf8; border-left: 3px solid #38bdf8;
        }
        .command-item kbd {
            font-family: 'Fira Code', monospace; font-size: 0.7rem; margin-left: auto;
            padding: 2px 6px; border-radius: 4px;
            background: rgba(128,128,128,0.2);
        }

        #command-palette-overlay {
            position: fixed; inset: 0; background-color: rgba(0,0,0,0.6);
            z-index: 10000; opacity: 0; pointer-events: none; transition: opacity 0.2s;
            backdrop-filter: blur(2px);
        }
        #command-palette-overlay.visible { opacity: 1; pointer-events: all; }

        /* --- 5. Animations --- */
        [data-stagger-reveal] {
            opacity: 0; transform: translateY(20px);
            transition: opacity 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1);
        }
        [data-stagger-reveal].is-revealed { opacity: 1; transform: translateY(0); }

        /* --- 6. Components --- */
        .accent-text { color: var(--accent); }
        .accent-hover:hover { color: var(--accent); }
        
        /* Nav Links */
        .nav-link { position: relative; font-weight: 500; font-size: 0.95rem; }
        .nav-link::after {
            content: ''; position: absolute; width: 0; height: 2px;
            bottom: -4px; left: 0; background-color: var(--accent);
            transition: width 0.3s;
        }
        .nav-link:hover::after, .nav-link.active::after { width: 100%; }
        .nav-link.active { color: var(--accent); }

        /* Project Cards */
        .project-card {
            border: 1px solid transparent; display: flex; flex-direction: column;
            transition: transform 0.3s ease, box-shadow 0.3s ease; overflow: hidden;
            border-radius: 0.75rem;
        }
        .dark .project-card {
            background: linear-gradient(#1E293B, #1E293B) padding-box, linear-gradient(135deg, #38bdf8, #818cf8) border-box;
        }
        .light .project-card {
            background: white; border: 1px solid #E2E8F0;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
        }
        .project-card:hover { transform: translateY(-5px); }

        /* Timeline */
        .timeline-item { position: relative; padding-left: 2rem; padding-bottom: 2.5rem; border-left: 2px solid; }
        .dark .timeline-item { border-color: #334155; }
        .light .timeline-item { border-color: #E2E8F0; }
        .timeline-item:last-child { border-color: transparent; padding-bottom: 0; }
        
        .timeline-dot {
            position: absolute; left: -9px; top: 5px; width: 16px; height: 16px;
            background: var(--accent); border-radius: 50%;
            border: 4px solid; 
        }
        .dark .timeline-dot { border-color: #0F172A; }
        .light .timeline-dot { border-color: #F8FAFC; }

        /* Book Typography (Custom Prose) */
        .prose h2 { font-size: 1.8rem; font-weight: 800; margin-bottom: 1rem; color: var(--accent); }
        .prose h3 { font-size: 1.5rem; font-weight: 700; margin-top: 2rem; margin-bottom: 1rem; }
        .prose h4 { font-size: 1.25rem; font-weight: 600; margin-top: 1.5rem; margin-bottom: 0.75rem; color: #94a3b8; }
        .light .prose h4 { color: #475569; }
        .prose p { margin-bottom: 1.25rem; line-height: 1.8; color: inherit; }
        .prose strong { color: var(--accent); font-weight: 600; }
        .prose ul, .prose ol { margin-left: 1.5rem; margin-bottom: 1.5rem; }
        .prose li { margin-bottom: 0.5rem; padding-left: 0.5rem; }
        .prose blockquote { 
            border-left: 4px solid var(--accent); padding-left: 1rem; font-style: italic; 
            margin: 1.5rem 0; color: #94a3b8;
        }
        
        /* Contact Items */
        .contact-item {
            display: flex; align-items: center; gap: 1rem; padding: 1rem;
            border-radius: 0.5rem; transition: background 0.3s;
            cursor: pointer;
        }
        .contact-item:hover { background-color: rgba(56, 189, 248, 0.1); }
        .copy-feedback { color: var(--accent); font-size: 0.75rem; opacity: 0; transition: opacity 0.3s; margin-left: auto; }

        /* Reduced Motion */
        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after {
                animation-duration: 0.01ms !important;
                transition-duration: 0.01ms !important;
                scroll-behavior: auto !important;
            }
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
                <a href="#about-site" class="command-item"><i data-lucide="layout-template" class="w-4 h-4"></i>About Site<kbd>S</kbd></a>
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
                
                <button id="theme-toggle" class="p-2 rounded-full hover:bg-sky-500/10 transition-colors" aria-label="Toggle theme" data-magnetic>
                    <i data-lucide="sun" class="w-5 h-5 hidden dark:block text-sky-400"></i>
                    <i data-lucide="moon" class="w-5 h-5 block dark:hidden text-slate-700"></i>
                </button>
            </div>

            <button id="mobile-menu-btn" class="md:hidden p-2 light:text-slate-700 dark:text-white z-50 relative">
                <i data-lucide="menu" class="w-6 h-6" id="menu-icon"></i>
            </button>
        </nav>

        <div id="mobile-menu" class="fixed inset-0 bg-slate-100 dark:bg-slate-900 z-40 transform translate-x-full transition-transform duration-300 flex flex-col justify-center items-center space-y-8 md:hidden">
            <a href="#home" class="text-2xl font-bold nav-link-mobile">Home</a>
            <a href="#about" class="text-2xl font-bold nav-link-mobile">About</a>
            <a href="#experience" class="text-2xl font-bold nav-link-mobile">Experience</a>
            <a href="#projects" class="text-2xl font-bold nav-link-mobile">Projects</a>
            <a href="#book" class="text-2xl font-bold nav-link-mobile">Book</a>
            <a href="#contact" class="text-2xl font-bold nav-link-mobile">Contact</a>
            <button id="theme-toggle-mobile" class="text-xl font-medium flex items-center gap-2 mt-8">
                <span>Switch Theme</span>
                <i data-lucide="sun" class="w-5 h-5 dark:hidden"></i>
                <i data-lucide="moon" class="w-5 h-5 hidden dark:block"></i>
            </button>
        </div>
    </header>

    <main class="container mx-auto px-6 relative z-10">

        <section id="home" data-section-id="home" class="min-h-screen flex items-center justify-center pt-20">
            <div data-stagger-container class="max-w-4xl w-full">
                <div data-stagger-reveal class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-sky-500/30 bg-sky-500/10 text-sky-400 text-xs font-bold uppercase tracking-widest mb-6">
                    <span class="w-2 h-2 rounded-full bg-sky-400 animate-pulse"></span>
                    Available for Contracts
                </div>
                
                <h1 data-stagger-reveal class="text-5xl md:text-7xl lg:text-8xl font-black tracking-tight mb-8 light:text-slate-900 dark:text-white leading-[1.1]">
                    Systems.<br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-sky-400 to-indigo-500">Architected.</span>
                </h1>
                
                <p data-stagger-reveal class="text-lg md:text-xl font-light light:text-slate-600 dark:text-slate-400 max-w-2xl mb-10 leading-relaxed">
                    I translate complex business needs into secure, scalable Salesforce solutions. I don't just fix tickets; I build the <strong>Black Box</strong> engines that power operational excellence.
                </p>
                
                <div data-stagger-reveal class="flex flex-col sm:flex-row gap-5">
                    <a href="#projects" class="group relative px-8 py-4 bg-sky-500 text-white font-semibold rounded-lg overflow-hidden shadow-lg shadow-sky-500/25 transition-all hover:shadow-sky-500/40 hover:-translate-y-1" data-magnetic>
                        <div class="absolute inset-0 w-full h-full bg-gradient-to-r from-transparent via-white/20 to-transparent -translate-x-full group-hover:animate-[shimmer_1s_infinite]"></div>
                        <span>View Projects</span>
                    </a>
                    <a href="#contact" class="px-8 py-4 font-semibold rounded-lg border light:border-slate-300 dark:border-slate-700 light:text-slate-700 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all hover:-translate-y-1" data-magnetic>
                        Get In Touch
                    </a>
                </div>
            </div>
        </section>

        <section id="about" data-section-id="about" class="py-24 md:py-32">
             <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center" data-stagger-container>
                <div data-stagger-reveal>
                    <h2 class="text-3xl md:text-4xl font-bold mb-8 light:text-slate-900 dark:text-white">
                        <span class="text-sky-400 font-mono text-2xl mr-2">01.</span> About Me
                    </h2>
                    <div class="space-y-4 text-lg light:text-slate-600 dark:text-slate-400 leading-relaxed">
                        <p>
                            I am a Salesforce Certified Administrator and Developer with a background in Computer Science from <strong class="text-sky-400">UT Dallas</strong>. My career has evolved from front-line IT support to strategic Business Systems Architecture.
                        </p>
                        <p>
                            I specialize in the "Black Box" methodology—tuning out the visual noise of tools to understand the shape and weight of the data underneath. This allows me to build systems that don't just work today, but scale for the next decade.
                        </p>
                        <p>
                            Currently architecting solutions at <strong class="text-sky-400">Hydrolix</strong>.
                        </p>
                    </div>
                </div>
                <div data-stagger-reveal class="relative group">
                    <div class="absolute inset-0 bg-sky-500/20 rounded-lg transform translate-x-3 translate-y-3 transition-transform group-hover:translate-x-2 group-hover:translate-y-2"></div>
                    <div class="relative bg-slate-800 p-8 rounded-lg border border-slate-700 hover:border-sky-400/50 transition-colors">
                        <h3 class="text-white font-bold mb-4">Tech Stack</h3>
                        <ul class="grid grid-cols-2 gap-3 font-mono text-sm text-slate-400">
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Salesforce Admin</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Apex & LWC</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Flow Automation</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Glovia OM / ERP</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>JavaScript (ES6+)</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>REST/SOAP APIs</li>
                        </ul>
                    </div>
                </div>
             </div>
        </section>

        <section id="experience" data-section-id="experience" class="py-24 md:py-32">
            <h2 class="text-3xl md:text-4xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                <span class="text-sky-400 font-mono text-2xl mr-2">02.</span> Experience
            </h2>
            <div class="max-w-3xl mx-auto" data-stagger-container>
                
                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Oct 2024 – Present</span>
                    <h3 class="text-xl font-bold text-white mb-1">Business Systems Architect</h3>
                    <p class="text-slate-400 mb-4 font-medium">Hydrolix (Remote)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-400 space-y-2">
                        <li>Architected the company's operational backbone on Salesforce for finance and SaaS deployment tracking.</li>
                        <li>Designed a lead-to-opportunity process reducing response time by 40%.</li>
                        <li>Automated the deployment lifecycle (POC to contract), handling credit approvals and quota tracking.</li>
                        <li>Developed custom Apex and LWC solutions to eliminate technical debt.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Jun 2024 – Aug 2024</span>
                    <h3 class="text-xl font-bold text-white mb-1">Salesforce Architect</h3>
                    <p class="text-slate-400 mb-4 font-medium">Jaco Aerospace (Contract)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-400 space-y-2">
                        <li>Optimized Salesforce Sales Cloud integrated with Glovia OM ERP.</li>
                        <li>Designed custom logic to overcome managed package limitations.</li>
                        <li>Configured Work Orders, RMAs, and Reorder Point Planning integration.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Mar 2022 – Oct 2023</span>
                    <h3 class="text-xl font-bold text-white mb-1">Salesforce Developer</h3>
                    <p class="text-slate-400 mb-4 font-medium">Fujitsu / Royal Canin</p>
                    <ul class="list-disc list-outside ml-4 text-slate-400 space-y-2">
                        <li>Served as Lead Developer for the Glovia OM managed package.</li>
                        <li>Integrated ERP/Order Management features and resolved complex supply chain logic issues.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">2016 – 2021</span>
                    <h3 class="text-xl font-bold text-white mb-1">BS Computer Science</h3>
                    <p class="text-slate-400 mb-4 font-medium">University of Texas at Dallas</p>
                </div>

            </div>
        </section>

        <section id="projects" data-section-id="projects" class="py-24">
             <h2 class="text-3xl md:text-4xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                <span class="text-sky-400 font-mono text-2xl mr-2">03.</span> Select Projects
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8" data-stagger-container>
                <div class="project-card p-6" data-stagger-reveal>
                    <div class="flex justify-between items-start mb-4">
                        <i data-lucide="folder" class="w-10 h-10 text-sky-400"></i>
                        <div class="flex gap-4">
                            <a href="#" class="hover:text-sky-400 transition-colors"><i data-lucide="github" class="w-5 h-5"></i></a>
                            <a href="#" class="hover:text-sky-400 transition-colors"><i data-lucide="external-link" class="w-5 h-5"></i></a>
                        </div>
                    </div>
                    <h3 class="text-xl font-bold mb-2 light:text-slate-900 dark:text-white">Deployment Lifecycle Engine</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 text-sm">
                        End-to-end automation for Hydrolix involving credit approvals, usage quota tracking, and automated email triggers via Zapier and Apex.
                    </p>
                    <div class="mt-auto flex gap-3 text-xs font-mono text-sky-400">
                        <span>Apex</span>
                        <span>Flow</span>
                        <span>Zapier</span>
                    </div>
                </div>
                
                 <div class="project-card p-6" data-stagger-reveal>
                    <div class="flex justify-between items-start mb-4">
                        <i data-lucide="folder" class="w-10 h-10 text-sky-400"></i>
                        <div class="flex gap-4">
                            <a href="#" class="hover:text-sky-400 transition-colors"><i data-lucide="external-link" class="w-5 h-5"></i></a>
                        </div>
                    </div>
                    <h3 class="text-xl font-bold mb-2 light:text-slate-900 dark:text-white">Veteran Dog Tracker</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 text-sm">
                        Implementation for a 501c nonprofit using a managed package to track service dog training progress for disabled veterans.
                    </p>
                    <div class="mt-auto flex gap-3 text-xs font-mono text-sky-400">
                        <span>Salesforce NPSP</span>
                        <span>Reports</span>
                        <span>Data Import</span>
                    </div>
                </div>
            </div>
        </section>

        <section id="book" data-section-id="book" class="py-24 md:py-32">
            <div data-stagger-container>
                <h2 class="text-3xl md:text-4xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                    <span class="text-sky-400 font-mono text-2xl mr-2">04.</span> The Black Box
                </h2>
                
                <div class="prose max-w-3xl mx-auto light:text-slate-700 dark:text-slate-300" data-stagger-reveal>
                    <p class="font-mono text-sm text-sky-400 mb-4">Excerpt from Chapter 1</p>
                    <h2>The "Black Box" Mindset</h2>
                    
                    <p>The meeting request is vague: "Discuss Sales-to-Ops Handoff." You join. The VP of Sales is sharing a Salesforce dashboard. "Look, we're growing," he says. "But our handoff to Ops is breaking. My reps are manually copying data from Opportunities into a Google Sheet. Can't we just use Zapier to move the data when the stage changes? It seems simple."</p>

                    <p>The technician hears this and is already building the Zap in their head. Trigger: <code>Closed Won</code>. Action: <code>Create Row</code>. Five-minute fix. Ticket closed.</p>
                    
                    <p>The <strong>Architect</strong> makes a different choice.</p>
                    
                    <blockquote>
                        "The technician gets to be the hero for a day. The architect has to live with the consequences for a decade."
                    </blockquote>

                    <h3>The Tyranny of the "Simple Fix"</h3>
                    <p>The "simple fix" is a high-interest loan taken out against the company's future. It creates a <strong>Data Trap</strong>. The Zapier solution assumes the deal is a transaction (write-once). In reality, a deal is a state (living record). When the rep updates the deal two days later, the Google Sheet is permanently wrong. Trust erodes.</p>

                    <h3>Choosing Focus: The Superior Method</h3>
                    <p>The Architect employs the "Black Box" mindset. They tune out the visual noise (the icons for Zapier and Sheets) and feel for the shape of the data.</p>
                    
                    <ol>
                        <li><strong>Shape:</strong> Is it a transaction or a state? (It's a state).</li>
                        <li><strong>Weight:</strong> What is the pain? (Blindness, not manual entry).</li>
                        <li><strong>Texture:</strong> What is the System of Record? (Salesforce).</li>
                    </ol>
                    
                    <p>The solution is not a Zap. The solution is a shared object inside Salesforce—a "Deployment" record triggered by Flow. One source of truth. Zero data drift. This is how you build for the decade, not the day.</p>
                </div>
            </div>
        </section>

        <section id="about-site" data-section-id="about-site" class="py-24">
            <div data-stagger-container class="light:bg-white dark:bg-slate-800/50 p-8 rounded-2xl border light:border-slate-200 dark:border-slate-700">
                <h2 class="text-2xl font-bold mb-6 light:text-slate-900 dark:text-white" data-stagger-reveal>
                    <span class="text-sky-400 font-mono text-xl mr-2">05.</span> About This Site
                </h2>
                <div class="grid lg:grid-cols-2 gap-8" data-stagger-reveal>
                    <div>
                        <p class="mb-4 text-slate-500 dark:text-slate-400">
                            This portfolio is "Project 0." It is a custom-built Single Page Application (SPA) designed to demonstrate front-end proficiency and attention to detail.
                        </p>
                        <p class="text-slate-500 dark:text-slate-400">
                            <strong>No frameworks.</strong> Just HTML, Tailwind CSS, and vanilla JavaScript. Optimized for performance and accessibility.
                        </p>
                    </div>
                    <div>
                        <h4 class="font-bold text-sm uppercase tracking-wide text-sky-400 mb-3">Tech Stack</h4>
                        <div class="flex flex-wrap gap-2">
                            <span class="px-3 py-1 rounded-full text-xs border border-slate-600 bg-slate-700 text-slate-300">HTML5</span>
                            <span class="px-3 py-1 rounded-full text-xs border border-slate-600 bg-slate-700 text-slate-300">Tailwind CSS</span>
                            <span class="px-3 py-1 rounded-full text-xs border border-slate-600 bg-slate-700 text-slate-300">Three.js</span>
                            <span class="px-3 py-1 rounded-full text-xs border border-slate-600 bg-slate-700 text-slate-300">Lucide Icons</span>
                            <span class="px-3 py-1 rounded-full text-xs border border-slate-600 bg-slate-700 text-slate-300">IntersectionObserver</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" data-section-id="contact" class="py-24 md:py-32 mb-20">
             <div class="max-w-2xl mx-auto text-center" data-stagger-container>
                <h2 class="text-3xl md:text-4xl font-bold mb-6 light:text-slate-900 dark:text-white" data-stagger-reveal>Get In Touch</h2>
                <p class="text-lg text-slate-500 dark:text-slate-400 mb-12" data-stagger-reveal>
                    I'm always open to discussing new projects, Salesforce architecture, or full-time opportunities.
                </p>
                
                <div class="flex flex-col md:flex-row justify-center gap-6" data-stagger-reveal>
                     <div class="contact-item bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 w-full" data-clipboard-text="2175087210" tabindex="0">
                        <div class="p-3 bg-sky-500/10 rounded-full text-sky-400"><i data-lucide="phone" class="w-5 h-5"></i></div>
                        <div class="text-left">
                            <div class="text-xs text-slate-500 uppercase font-bold">Phone</div>
                            <div class="font-mono text-sm light:text-slate-900 dark:text-slate-200">(217) 508-7210</div>
                        </div>
                        <span class="copy-feedback">Copied!</span>
                     </div>
                     
                     <div class="contact-item bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 w-full" data-clipboard-text="alecborman97@gmail.com" tabindex="0">
                        <div class="p-3 bg-sky-500/10 rounded-full text-sky-400"><i data-lucide="mail" class="w-5 h-5"></i></div>
                        <div class="text-left">
                            <div class="text-xs text-slate-500 uppercase font-bold">Email</div>
                            <div class="font-mono text-sm light:text-slate-900 dark:text-slate-200">alecborman97@gmail.com</div>
                        </div>
                        <span class="copy-feedback">Copied!</span>
                     </div>
                </div>
                
                <div class="mt-12" data-stagger-reveal>
                    <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" class="inline-flex items-center gap-2 text-slate-500 hover:text-sky-400 transition-colors">
                        <i data-lucide="linkedin" class="w-5 h-5"></i>
                        <span>Connect on LinkedIn</span>
                    </a>
                </div>
             </div>
        </section>

    </main>

    <footer class="py-8 text-center text-sm text-slate-500 dark:text-slate-600 relative z-10">
        <p>&copy; <span id="year"></span> Alec Borman. Built with <span class="text-sky-400">♥</span> and Logic.</p>
    </footer>

    <script>
        // --- 1. Utilities ---
        const lerp = (start, end, t) => (1 - t) * start + t * end;
        const isTouch = ('ontouchstart' in window) || (navigator.maxTouchPoints > 0);
        const prefersReducedMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;

        // --- 2. Theme Manager ---
        function initTheme() {
            const toggle = document.getElementById('theme-toggle');
            const mobileToggle = document.getElementById('theme-toggle-mobile');
            const html = document.documentElement;
            
            // Default to dark, check local storage
            const saved = localStorage.getItem('theme') || 'dark';
            html.classList.add(saved);

            const switchTheme = () => {
                const isDark = html.classList.contains('dark');
                html.classList.remove(isDark ? 'dark' : 'light');
                html.classList.add(isDark ? 'light' : 'dark');
                localStorage.setItem('theme', isDark ? 'light' : 'dark');
            };

            toggle.addEventListener('click', switchTheme);
            mobileToggle.addEventListener('click', switchTheme);
        }

        // --- 3. Custom Cursor (Desktop Only) ---
        function initCursor() {
            if (isTouch || prefersReducedMotion) return;
            
            // Add class to body to hide default cursor
            document.body.classList.add('custom-cursor-active');

            const dot = document.getElementById('cursor-dot');
            const outline = document.getElementById('cursor-outline');
            
            let dotX = window.innerWidth/2, dotY = window.innerHeight/2;
            let outX = window.innerWidth/2, outY = window.innerHeight/2;
            let targetX = window.innerWidth/2, targetY = window.innerHeight/2;

            window.addEventListener('mousemove', e => {
                targetX = e.clientX;
                targetY = e.clientY;
                // Instant update for dot
                dotX = targetX;
                dotY = targetY;
                dot.style.transform = `translate(${dotX}px, ${dotY}px)`;
            });

            const animate = () => {
                outX = lerp(outX, targetX, 0.15);
                outY = lerp(outY, targetY, 0.15);
                outline.style.transform = `translate(${outX}px, ${outY}px)`;
                requestAnimationFrame(animate);
            };
            animate();

            // Hover effects
            document.querySelectorAll('a, button, [role="button"], .project-card').forEach(el => {
                el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
                el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
            });
        }

        // --- 4. Magnetic Buttons ---
        function initMagnetic() {
            if (isTouch || prefersReducedMotion) return;
            
            document.querySelectorAll('[data-magnetic]').forEach(el => {
                el.addEventListener('mousemove', e => {
                    const rect = el.getBoundingClientRect();
                    const x = e.clientX - rect.left - rect.width / 2;
                    const y = e.clientY - rect.top - rect.height / 2;
                    el.style.transform = `translate(${x * 0.3}px, ${y * 0.3}px)`;
                });
                el.addEventListener('mouseleave', () => {
                    el.style.transform = 'translate(0,0)';
                });
            });
        }

        // --- 5. Three.js Background ---
        function initThree() {
            if (prefersReducedMotion || typeof THREE === 'undefined') return;

            const canvas = document.getElementById('bg-canvas');
            const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 100);
            camera.position.z = 3;

            // Geometry
            const count = isTouch ? 1500 : 3000; // Reduce particles on mobile
            const geom = new THREE.BufferGeometry();
            const pos = new Float32Array(count * 3);
            
            for(let i=0; i<count*3; i++) {
                pos[i] = (Math.random() - 0.5) * 10;
            }
            geom.setAttribute('position', new THREE.BufferAttribute(pos, 3));
            
            const mat = new THREE.PointsMaterial({
                size: 0.015,
                color: 0x38bdf8, // Sky-400
                transparent: true,
                opacity: 0.6,
                blending: THREE.AdditiveBlending
            });
            
            const mesh = new THREE.Points(geom, mat);
            scene.add(mesh);

            let mouseX = 0, mouseY = 0;
            if(!isTouch) {
                window.addEventListener('mousemove', e => {
                    mouseX = e.clientX / window.innerWidth - 0.5;
                    mouseY = e.clientY / window.innerHeight - 0.5;
                });
            }

            const clock = new THREE.Clock();
            const animate = () => {
                const t = clock.getElapsedTime();
                mesh.rotation.x = t * 0.05;
                mesh.rotation.y = t * 0.03;
                
                // Parallax
                camera.position.x += (mouseX * 0.5 - camera.position.x) * 0.05;
                camera.position.y += (-mouseY * 0.5 - camera.position.y) * 0.05;
                camera.lookAt(scene.position);

                renderer.render(scene, camera);
                requestAnimationFrame(animate);
            };
            animate();

            window.addEventListener('resize', () => {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
            });
        }

        // --- 6. Mobile Menu ---
        function initMobileMenu() {
            const btn = document.getElementById('mobile-menu-btn');
            const menu = document.getElementById('mobile-menu');
            const links = document.querySelectorAll('.nav-link-mobile');
            let isOpen = false;

            const toggle = () => {
                isOpen = !isOpen;
                if(isOpen) {
                    menu.classList.remove('translate-x-full');
                    document.body.style.overflow = 'hidden';
                } else {
                    menu.classList.add('translate-x-full');
                    document.body.style.overflow = '';
                }
            };

            btn.addEventListener('click', toggle);
            links.forEach(l => l.addEventListener('click', toggle));
        }

        // --- 7. Clipboard ---
        function initClipboard() {
            document.querySelectorAll('[data-clipboard-text]').forEach(el => {
                el.addEventListener('click', () => {
                    const text = el.getAttribute('data-clipboard-text');
                    navigator.clipboard.writeText(text).then(() => {
                        const fb = el.querySelector('.copy-feedback');
                        fb.style.opacity = '1';
                        setTimeout(() => fb.style.opacity = '0', 2000);
                    });
                });
            });
        }

        // --- 8. Command Palette ---
        function initPalette() {
            const palette = document.getElementById('command-palette');
            const overlay = document.getElementById('command-palette-overlay');
            const input = document.getElementById('command-palette-input');
            const items = document.querySelectorAll('.command-item');
            
            const open = () => {
                palette.classList.add('visible');
                overlay.classList.add('visible');
                input.focus();
            };
            
            const close = () => {
                palette.classList.remove('visible');
                overlay.classList.remove('visible');
            };

            // Keyboard Shortcuts
            window.addEventListener('keydown', e => {
                if((e.ctrlKey || e.metaKey) && e.key === 'k') {
                    e.preventDefault();
                    palette.classList.contains('visible') ? close() : open();
                }
                if(e.key === 'Escape') close();
            });

            overlay.addEventListener('click', close);

            // Filtering
            input.addEventListener('input', (e) => {
                const val = e.target.value.toLowerCase();
                items.forEach(item => {
                    const text = item.textContent.toLowerCase();
                    item.style.display = text.includes(val) ? 'flex' : 'none';
                });
            });

            // Click handling
            items.forEach(item => {
                item.addEventListener('click', () => {
                    close();
                    // Smooth scroll is handled by CSS html { scroll-behavior: smooth }
                });
            });
        }

        // --- 9. Stagger & Scroll ---
        function initScroll() {
            // Scroll Progress
            window.addEventListener('scroll', () => {
                const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
                const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
                const scrolled = (winScroll / height) * 100;
                document.getElementById('scroll-progress').style.width = scrolled + "%";
                
                // Header Glass
                const header = document.getElementById('header');
                if(winScroll > 50) {
                    header.classList.add('backdrop-blur-md', 'bg-white/80', 'dark:bg-slate-900/80', 'shadow-md');
                } else {
                    header.classList.remove('backdrop-blur-md', 'bg-white/80', 'dark:bg-slate-900/80', 'shadow-md');
                }
            });

            // Stagger Reveal
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if(entry.isIntersecting) {
                        entry.target.classList.add('is-revealed');
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('[data-stagger-reveal]').forEach(el => observer.observe(el));
            
            // Highlight Nav
            const sections = document.querySelectorAll('section');
            const navLinks = document.querySelectorAll('.nav-link');
            
            const navObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if(entry.isIntersecting) {
                        const id = entry.target.getAttribute('id');
                        navLinks.forEach(link => {
                            link.classList.toggle('active', link.getAttribute('href') === '#' + id);
                        });
                    }
                });
            }, { threshold: 0.5 });
            sections.forEach(s => navObserver.observe(s));
        }

        // --- Initialize ---
        window.onload = () => {
            initTheme();
            initCursor();
            initThree();
            initMagnetic();
            initMobileMenu();
            initClipboard();
            initPalette();
            initScroll();
            
            // Lucide
            lucide.createIcons();
            
            // Year
            document.getElementById('year').textContent = new Date().getFullYear();
        };
    </script>
    
    <style>
        @keyframes shimmer {
            100% { transform: translateX(100%); }
        }
    </style>
</body>
</html>
