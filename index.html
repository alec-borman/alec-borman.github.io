<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alec Borman | The Black Box Architect</title>
    
    <!-- SEO & Metadata -->
    <meta name="description" content="Alec Borman is a Senior Salesforce Architect who builds scalable revenue engines using the 'Black Box' methodology. Expert in Apex, LWC, and Systems Design.">
    <meta name="keywords" content="Alec Borman, Salesforce Architect, Black Box Architect, Apex, LWC, Hydrolix, RevOps, Zapier, Houston, Systems Thinking">
    <meta name="author" content="Alec Borman">
    <meta name="robots" content="index, follow">
    <meta name="theme-color" content="#0F172A">

    <!-- Social Graph (Open Graph / Twitter) -->
    <meta property="og:type" content="website">
    <meta property="og:title" content="Alec Borman | The Black Box Architect">
    <meta property="og:description" content="Translating chaotic business needs into secure, scalable engines.">
    <meta property="og:url" content="https://alecborman.com">
    <meta property="og:image" content="https://alecborman.com/og-image.jpg"> <!-- Placeholder for your actual OG image -->
    <meta property="twitter:card" content="summary_large_image">

    <!-- Favicon (SVG Data URI for performance) -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⚡</text></svg>">
    
    <!-- External Resources (Version Locked for Security) -->
    <script src="https://cdn.tailwindcss.com?plugins=typography"></script>
    <script src="https://unpkg.com/lucide-icons@0.300.0/dist/umd/lucide.min.js" defer></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js" defer></script>

    <!-- Typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">

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
                        slate: { 
                            850: '#151e2e', // Deep matte background
                            900: '#0F172A',
                            950: '#020617'  // Void background
                        }
                    },
                    animation: {
                        'pulse-slow': 'pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                    }
                },
            },
        }
    </script>
    
    <style>
        /* --- CORE SYSTEM --- */
        body { 
            font-family: 'Inter', sans-serif; 
            scroll-padding-top: 80px; 
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* --- THEME VARIABLES --- */
        :root { --accent: #38bdf8; } /* Sky-400 */
        .dark body { background-color: #0F172A; color: #CBD5E1; }
        .light body { background-color: #F8FAFC; color: #1E293B; }
        
        /* --- UI MODULE: BACKGROUND ENGINE --- */
        #bg-canvas { 
            position: fixed; top: 0; left: 0; width: 100%; height: 100%; 
            z-index: -10; opacity: 0.4; pointer-events: none; 
            transition: opacity 0.5s ease;
        }
        .light #bg-canvas { opacity: 0.2; }

        /* --- UI MODULE: CURSOR SYSTEM (Desktop Only) --- */
        body.custom-cursor-active { cursor: none; }
        #cursor-dot, #cursor-outline { 
            position: fixed; top: 0; left: 0; transform: translate(-50%, -50%); 
            border-radius: 50%; pointer-events: none; z-index: 9999; opacity: 0; 
            will-change: transform;
        }
        body.custom-cursor-active #cursor-dot, 
        body.custom-cursor-active #cursor-outline { opacity: 1; }
        
        #cursor-dot { width: 8px; height: 8px; background-color: var(--accent); transition: opacity 0.3s; }
        #cursor-outline { 
            width: 40px; height: 40px; border: 2px solid var(--accent); opacity: 0.5; 
            transition: width 0.3s, height 0.3s, background-color 0.3s; 
        }
        body.cursor-hover #cursor-outline { 
            width: 60px; height: 60px; background-color: rgba(56, 189, 248, 0.1); border-color: #818cf8; 
        }

        /* --- UI MODULE: SCROLL & NAV --- */
        #scroll-progress { 
            position: fixed; top: 0; left: 0; height: 3px; 
            background: linear-gradient(90deg, #38bdf8, #818cf8); 
            width: 0%; z-index: 10000; transition: width 0.1s linear; 
        }
        .nav-link { position: relative; font-weight: 500; transition: color 0.3s; }
        .nav-link::after { 
            content: ''; position: absolute; width: 0; height: 2px; 
            bottom: -4px; left: 0; background-color: var(--accent); 
            transition: width 0.3s; 
        }
        .nav-link:hover::after, .nav-link.active::after { width: 100%; }
        .nav-link.active { color: var(--accent); }

        /* --- UI MODULE: COMMAND PALETTE --- */
        #command-palette { 
            position: fixed; top: 20%; left: 50%; 
            transform: translate(-50%, -50%) scale(0.95); 
            width: 90%; max-width: 500px; z-index: 10001; 
            opacity: 0; pointer-events: none; transition: all 0.2s ease-out; 
            box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5); 
        }
        #command-palette.visible { transform: translate(-50%, -50%) scale(1); opacity: 1; pointer-events: all; }
        .cmd-palette-content { backdrop-filter: blur(12px); border-radius: 12px; overflow: hidden; }
        .dark .cmd-palette-content { background-color: rgba(15, 23, 42, 0.95); border: 1px solid #334155; }
        .light .cmd-palette-content { background-color: rgba(255, 255, 255, 0.95); border: 1px solid #CBD5E1; }
        #command-palette-input { background: transparent; border: none; padding: 1.25rem; width: 100%; outline: none; font-size: 1.1rem; }
        .dark #command-palette-input { color: white; border-bottom: 1px solid #334155; }
        .light #command-palette-input { color: #0F172A; border-bottom: 1px solid #E2E8F0; }
        
        .command-item { 
            padding: 0.75rem 1.25rem; cursor: pointer; display: flex; align-items: center; gap: 0.75rem; transition: all 0.15s; 
            scroll-margin-top: 50px;
        }
        .command-item:hover, .command-item.selected { 
            background-color: rgba(56, 189, 248, 0.15); color: #38bdf8; border-left: 3px solid #38bdf8; padding-left: 1.1rem;
        }
        
        #command-palette-overlay { 
            position: fixed; inset: 0; background-color: rgba(0,0,0,0.6); z-index: 10000; 
            opacity: 0; pointer-events: none; transition: opacity 0.2s; backdrop-filter: blur(2px); 
        }
        #command-palette-overlay.visible { opacity: 1; pointer-events: all; }
        kbd { font-family: 'Fira Code', monospace; background: rgba(128,128,128,0.2); padding: 2px 6px; border-radius: 4px; font-size: 0.75rem; margin-left: auto; }

        /* --- UI MODULE: ANIMATIONS & COMPONENTS --- */
        [data-stagger-reveal] { 
            opacity: 0; transform: translateY(20px); 
            transition: opacity 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1); 
            will-change: opacity, transform;
        }
        [data-stagger-reveal].is-revealed { opacity: 1; transform: translateY(0); }

        .project-card { 
            border: 1px solid transparent; display: flex; flex-direction: column; 
            transition: transform 0.3s, box-shadow 0.3s; border-radius: 0.75rem; overflow: hidden; 
        }
        .dark .project-card { background: linear-gradient(#1E293B, #1E293B) padding-box, linear-gradient(135deg, #38bdf8, #818cf8) border-box; }
        .light .project-card { background: white; border: 1px solid #E2E8F0; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }
        .project-card:hover { transform: translateY(-5px); box-shadow: 0 10px 30px -10px rgba(56, 189, 248, 0.3); }

        .timeline-item { position: relative; padding-left: 2rem; padding-bottom: 3rem; border-left: 2px solid; }
        .dark .timeline-item { border-color: #334155; }
        .light .timeline-item { border-color: #E2E8F0; }
        .timeline-item:last-child { border-color: transparent; }
        .timeline-dot { 
            position: absolute; left: -9px; top: 5px; width: 16px; height: 16px; 
            background: var(--accent); border-radius: 50%; border: 4px solid; 
        }
        .dark .timeline-dot { border-color: #0F172A; }
        .light .timeline-dot { border-color: #F8FAFC; }

        /* --- UI MODULE: EDITORIAL TYPOGRAPHY --- */
        .prose h2 { font-size: 1.8rem; font-weight: 800; margin-bottom: 1rem; color: var(--accent); letter-spacing: -0.025em; }
        .prose h3 { font-size: 1.5rem; font-weight: 700; margin-top: 2rem; margin-bottom: 1rem; }
        .prose p { margin-bottom: 1.25rem; line-height: 1.7; font-size: 1.05rem; }
        .prose blockquote { 
            border-left: 4px solid var(--accent); padding-left: 1.5rem; 
            font-style: italic; margin: 2rem 0; opacity: 0.9; font-size: 1.1rem;
        }
        .prose code { background: rgba(56, 189, 248, 0.1); color: var(--accent); padding: 0.2rem 0.4rem; border-radius: 4px; font-family: 'Fira Code', monospace; font-size: 0.85em; }

        /* Accessibility: Reduced Motion */
        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; scroll-behavior: auto !important; }
            #bg-canvas, #cursor-dot, #cursor-outline { display: none !important; }
            body { cursor: auto !important; }
        }
    </style>
</head>
<body class="antialiased dark selection:bg-sky-500/30 selection:text-sky-300">

    <div id="scroll-progress"></div>
    <div id="cursor-dot" aria-hidden="true"></div>
    <div id="cursor-outline" aria-hidden="true"></div>
    <canvas id="bg-canvas" aria-hidden="true"></canvas>
    
    <div id="command-palette-overlay" aria-hidden="true"></div>
    <div id="command-palette" role="dialog" aria-modal="true" aria-labelledby="command-palette-input">
        <div class="cmd-palette-content">
            <input type="text" id="command-palette-input" placeholder="Jump to... (Ctrl+K)" autocomplete="off">
            <div id="command-palette-list" role="listbox">
                <a href="#home" class="command-item" role="option"><i data-lucide="home" class="w-4 h-4"></i>Home<kbd>H</kbd></a>
                <a href="#about" class="command-item" role="option"><i data-lucide="user" class="w-4 h-4"></i>About<kbd>A</kbd></a>
                <a href="#experience" class="command-item" role="option"><i data-lucide="briefcase" class="w-4 h-4"></i>Experience<kbd>E</kbd></a>
                <a href="#projects" class="command-item" role="option"><i data-lucide="layers" class="w-4 h-4"></i>Projects<kbd>P</kbd></a>
                <a href="#book" class="command-item" role="option"><i data-lucide="book" class="w-4 h-4"></i>Book<kbd>B</kbd></a>
                <a href="#contact" class="command-item" role="option"><i data-lucide="mail" class="w-4 h-4"></i>Contact<kbd>C</kbd></a>
            </div>
        </div>
    </div>

    <header id="header" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 border-b border-transparent">
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
                
                <button id="theme-toggle" class="p-2 rounded-full hover:bg-sky-500/10 transition-colors" data-magnetic aria-label="Toggle Theme">
                    <i data-lucide="sun" class="w-5 h-5 hidden dark:block text-sky-400"></i>
                    <i data-lucide="moon" class="w-5 h-5 block dark:hidden text-slate-700"></i>
                </button>
            </div>

            <button id="mobile-menu-btn" class="md:hidden p-2 light:text-slate-700 dark:text-white relative z-50" aria-label="Toggle Menu">
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
            <button id="theme-toggle-mobile" class="text-xl font-medium flex items-center gap-2 mt-8 text-sky-400">Switch Theme</button>
        </div>
    </header>

    <main class="container mx-auto px-6 relative z-10">

        <section id="home" class="min-h-screen flex items-center justify-center pt-20">
            <div data-stagger-container class="max-w-4xl w-full">
                <div data-stagger-reveal class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-sky-500/30 bg-sky-500/10 text-sky-400 text-xs font-bold uppercase tracking-widest mb-6">
                    <span class="w-2 h-2 rounded-full bg-sky-400 animate-pulse-slow"></span>
                    Available for Contracts
                </div>
                <h1 data-stagger-reveal class="text-5xl md:text-7xl lg:text-8xl font-black tracking-tight mb-8 light:text-slate-900 dark:text-white leading-[1.1]">
                    Systems.<br><span class="text-transparent bg-clip-text bg-gradient-to-r from-sky-400 to-indigo-500">Architected.</span>
                </h1>
                <p data-stagger-reveal class="text-lg md:text-xl font-light light:text-slate-600 dark:text-slate-400 max-w-2xl mb-10 leading-relaxed">
                    I translate chaotic business needs into secure, scalable engines. I don't just fix tickets; I apply the <strong>"Black Box"</strong> methodology to build the operational backbone of high-growth companies.
                </p>
                <div data-stagger-reveal class="flex flex-col sm:flex-row gap-5">
                    <a href="#projects" class="px-8 py-4 bg-sky-500 text-white font-semibold rounded-lg shadow-lg hover:shadow-sky-500/40 hover:-translate-y-1 transition-all flex items-center justify-center gap-2" data-magnetic>
                        <span>View Projects</span>
                    </a>
                    <a href="#contact" class="px-8 py-4 font-semibold rounded-lg border light:border-slate-300 dark:border-slate-700 hover:bg-slate-100 dark:hover:bg-slate-800 transition-all hover:-translate-y-1 flex items-center justify-center" data-magnetic>
                        Get In Touch
                    </a>
                </div>
            </div>
        </section>

        <section id="about" class="py-24">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center" data-stagger-container>
                <div data-stagger-reveal>
                    <h2 class="text-3xl font-bold mb-8 light:text-slate-900 dark:text-white">
                        <span class="text-sky-400 font-mono text-2xl mr-2">01.</span> About Me
                    </h2>
                    <div class="space-y-4 text-lg light:text-slate-600 dark:text-slate-400 leading-relaxed">
                        <p>I am a Salesforce Architect and UT Dallas CS graduate. My career evolved from front-line IT and DevOps to architecting the revenue engines for companies like Hydrolix.</p>
                        <p>I specialize in tuning out "visual noise" to understand the shape of data. This allows me to build systems that don't just work today, but scale for the next decade.</p>
                        <p>I believe that a system is only as good as the trust the users place in it. My goal is to build that trust through robust automation and intuitive design.</p>
                    </div>
                </div>
                <div data-stagger-reveal class="relative group">
                    <div class="absolute inset-0 bg-sky-500/20 rounded-lg transform translate-x-3 translate-y-3 transition-transform group-hover:translate-x-2 group-hover:translate-y-2"></div>
                    <div class="relative bg-slate-800 p-8 rounded-lg border border-slate-700 hover:border-sky-400/50 transition-colors">
                        <h3 class="text-white font-bold mb-6 flex items-center gap-2">
                            <i data-lucide="cpu" class="text-sky-400"></i> Core Stack
                        </h3>
                        <ul class="grid grid-cols-2 gap-4 font-mono text-sm text-slate-400">
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Salesforce Arch</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Apex & LWC</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Zapier Logic</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Glovia OM / ERP</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>Flow Builder</li>
                            <li class="flex items-center gap-2"><i data-lucide="check-circle" class="w-4 h-4 text-sky-400"></i>REST APIs</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="experience" class="py-24">
            <h2 class="text-3xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                <span class="text-sky-400 font-mono text-2xl mr-2">02.</span> Experience
            </h2>
            <div class="max-w-3xl mx-auto" data-stagger-container>
                
                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Oct 2024 – Nov 2025</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Business Systems Architect</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Hydrolix (Remote)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li><strong>Strategic Pivot:</strong> Owned the Salesforce infrastructure for the "Custom Solutions" division. Following the successful maturation of these processes and the company's strategic pivot toward a pure-play App model, I oversaw the transition and documentation of these systems.</li>
                        <li><strong>Deployment Engine:</strong> Built end-to-end automation handling POC credit approvals, usage quota tracking (TB/month), and automated customer communications.</li>
                        <li><strong>Lead Velocity:</strong> Designed a high-speed ingestion process cutting response time by 40%.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Sep 2022 – Nov 2025</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Salesforce Consultant / Developer</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">GIVE US PAWS (Contract)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li>Implemented a full Salesforce lifecycle for a 501c nonprofit, migrating them from spreadsheets to a managed "Dog and Client Tracker" package.</li>
                        <li>Built custom reports and dashboards to track service dog training progress for disabled veterans.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Jun 2024 – Aug 2024</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Salesforce Architect</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Jaco Aerospace (Contract)</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li><strong>Surgical Intervention:</strong> Hired specifically to untangle a critical ERP scale-up utilizing Glovia OM.</li>
                        <li>Designed custom Apex logic to bypass managed package limitations that were bottlenecking the warehouse team.</li>
                        <li>Configured Work Orders, RMAs, and Reorder Point Planning, effectively stabilizing their Order Management system during a high-growth period.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">Mar 2022 – Oct 2023</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">Salesforce Developer & Support Lead</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Fujitsu / Royal Canin</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li><strong>Mastery Through Operations:</strong> Co-managed the entire Tier 1 Support department (2-person team) for the Glovia OM managed package. This role provided deep, "under-the-hood" exposure to how enterprise ERPs fail—and how to fix them.</li>
                        <li>Contracted to Royal Canin to resolve complex supply chain logic issues and integrate Order Management features.</li>
                        <li>This operational pressure cooker honed my ability to diagnose "Black Box" issues instantly.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">May 2019 – Aug 2019</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">IT Intern</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Austin Industrial, Inc.</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li>Foundational hardware and network diagnostics. Deployed devices and tracked assets via inventory management software.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">May 2018 – Aug 2018</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">DevOps Intern</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">Austin Industrial, Inc.</p>
                    <ul class="list-disc list-outside ml-4 text-slate-500 dark:text-slate-400 space-y-3 leading-relaxed">
                        <li><strong>Early Systems Exposure:</strong> Researched and deployed intrinsically safe hardware for RFID site tracking.</li>
                        <li>Digitized Job Safety Analysis (JSA) audits, transitioning the company from paper to iOS applications.</li>
                    </ul>
                </div>

                <div class="timeline-item" data-stagger-reveal>
                    <div class="timeline-dot"></div>
                    <span class="text-sky-400 font-mono text-sm mb-1 block">2016 – 2021</span>
                    <h3 class="text-xl font-bold light:text-slate-900 dark:text-white mb-1">BS Computer Science</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-4 font-medium">University of Texas at Dallas</p>
                </div>

            </div>
        </section>

        <section id="projects" class="py-24">
             <h2 class="text-3xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                <span class="text-sky-400 font-mono text-2xl mr-2">03.</span> Select Projects
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8" data-stagger-container>
                
                <div class="project-card p-8 group" data-stagger-reveal>
                    <div class="flex justify-between items-start mb-6">
                        <div class="p-3 bg-sky-500/10 rounded-lg text-sky-400">
                            <i data-lucide="server" class="w-8 h-8"></i>
                        </div>
                        <i data-lucide="external-link" class="w-5 h-5 text-slate-500 group-hover:text-sky-400 transition-colors"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3 light:text-slate-900 dark:text-white">Deployment Lifecycle Engine</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-6 text-sm leading-relaxed">
                        End-to-end automation for Hydrolix involving credit approvals, usage quota tracking, and automated email triggers via Zapier and Apex. Reduced manual ops time by 60%.
                    </p>
                    <div class="mt-auto flex gap-3 text-xs font-mono text-sky-400">
                        <span>Apex</span><span>Flow</span><span>Zapier</span>
                    </div>
                </div>
                
                 <div class="project-card p-8 group" data-stagger-reveal>
                    <div class="flex justify-between items-start mb-6">
                        <div class="p-3 bg-sky-500/10 rounded-lg text-sky-400">
                            <i data-lucide="heart-handshake" class="w-8 h-8"></i>
                        </div>
                        <i data-lucide="external-link" class="w-5 h-5 text-slate-500 group-hover:text-sky-400 transition-colors"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3 light:text-slate-900 dark:text-white">Veteran Dog Tracker</h3>
                    <p class="text-slate-500 dark:text-slate-400 mb-6 text-sm leading-relaxed">
                        Implementation for a 501c nonprofit using a managed package to track service dog training progress for disabled veterans. Full lifecycle management from license acquisition to data migration.
                    </p>
                    <div class="mt-auto flex gap-3 text-xs font-mono text-sky-400">
                        <span>NPSP</span><span>Reports</span><span>Data Import</span>
                    </div>
                </div>

            </div>
        </section>

        <section id="book" class="py-24">
            <div data-stagger-container>
                <h2 class="text-3xl font-bold mb-16 light:text-slate-900 dark:text-white" data-stagger-reveal>
                    <span class="text-sky-400 font-mono text-2xl mr-2">04.</span> The Black Box
                </h2>
                
                <div class="prose max-w-3xl mx-auto light:text-slate-700 dark:text-slate-300" data-stagger-reveal>
                    <div class="font-mono text-xs text-sky-400 mb-6 border-b border-sky-500/20 pb-2 uppercase tracking-wide">Excerpt from Chapter 1</div>
                    
                    <h2>The "Black Box" Mindset</h2>
                    <p>The meeting request is vague: "Discuss Sales-to-Ops Handoff." The VP of Sales wants a Zap to copy data to a Google Sheet. "It seems simple," he says. "Just move the fields."</p>

                    <p>The <strong>Technician</strong> hears this and is already building the Zap in their head. Trigger: <code>Closed Won</code>. Action: <code>Create Row</code>. Five-minute fix. Ticket closed. But they created a "Data Trap"—a fractured process that breaks the moment a deal is updated.</p>
                    
                    <p>The <strong>Architect</strong> makes a different choice.</p>
                    
                    <blockquote>"The technician gets to be the hero for a day. The architect has to live with the consequences for a decade."</blockquote>

                    <h3>Choosing Focus: The Superior Method</h3>
                    <p>The Architect employs the "Black Box" mindset. They tune out the visual noise (the icons for Zapier, Google Sheets, Slack) and feel for the shape of the data.</p>
                    
                    <ol>
                        <li><strong>Shape:</strong> Is it a transaction or a state? (It's a state).</li>
                        <li><strong>Weight:</strong> What is the pain? (Blindness, not manual entry).</li>
                        <li><strong>Texture:</strong> What is the System of Record? (Salesforce).</li>
                    </ol>
                    
                    <p>The solution is not a Zap. The solution is a shared object inside Salesforce—a "Deployment" record triggered by Flow. One source of truth. Zero data drift. This is how you build for the decade, not the day.</p>
                </div>
            </div>
        </section>

        <section id="contact" class="py-24 mb-20">
             <div class="max-w-2xl mx-auto text-center" data-stagger-container>
                <h2 class="text-3xl font-bold mb-6 light:text-slate-900 dark:text-white" data-stagger-reveal>Get In Touch</h2>
                <p class="text-lg text-slate-500 dark:text-slate-400 mb-12" data-stagger-reveal>
                    I'm open to discussing new projects, Salesforce architecture, or full-time opportunities.
                </p>
                
                <div class="flex flex-col md:flex-row justify-center gap-6" data-stagger-reveal>
                     <button class="group flex items-center gap-4 bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 p-4 rounded-lg cursor-pointer w-full hover:border-sky-400/50 transition-all" onclick="copyToClipboard('2175087210', this)" aria-label="Copy Phone Number">
                        <div class="p-3 bg-white dark:bg-slate-900 rounded-full text-sky-400 group-hover:scale-110 transition-transform"><i data-lucide="phone" class="w-5 h-5"></i></div>
                        <div class="text-left">
                            <div class="text-xs uppercase font-bold text-slate-500">Phone</div>
                            <div class="font-mono text-sm light:text-slate-900 dark:text-white">(217) 508-7210</div>
                        </div>
                        <span class="copy-feedback text-xs text-sky-400 opacity-0 ml-auto transition-opacity">Copied!</span>
                     </button>
                     
                     <button class="group flex items-center gap-4 bg-slate-100 dark:bg-slate-800 border light:border-slate-200 dark:border-slate-700 p-4 rounded-lg cursor-pointer w-full hover:border-sky-400/50 transition-all" onclick="copyToClipboard('alecborman97@gmail.com', this)" aria-label="Copy Email">
                        <div class="p-3 bg-white dark:bg-slate-900 rounded-full text-sky-400 group-hover:scale-110 transition-transform"><i data-lucide="mail" class="w-5 h-5"></i></div>
                        <div class="text-left">
                            <div class="text-xs uppercase font-bold text-slate-500">Email</div>
                            <div class="font-mono text-sm light:text-slate-900 dark:text-white">alecborman97@gmail.com</div>
                        </div>
                        <span class="copy-feedback text-xs text-sky-400 opacity-0 ml-auto transition-opacity">Copied!</span>
                     </button>
                </div>
                
                <div class="mt-12" data-stagger-reveal>
                    <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 text-slate-500 hover:text-sky-400 transition-colors">
                        <i data-lucide="linkedin" class="w-5 h-5"></i>
                        <span>Connect on LinkedIn</span>
                    </a>
                </div>
             </div>
        </section>
    </main>

    <footer class="py-8 text-center text-sm text-slate-500 relative z-10 border-t light:border-slate-200 dark:border-slate-800">
        <p>&copy; <span id="year"></span> Alec Borman. Built with <span class="text-sky-400">♥</span> and Logic.</p>
    </footer>

    <script>
        // --- MODULE: UTILITIES ---
        const Utils = {
            lerp: (start, end, t) => (1 - t) * start + t * end,
            isTouch: () => ('ontouchstart' in window) || (navigator.maxTouchPoints > 0),
            prefersReducedMotion: () => window.matchMedia("(prefers-reduced-motion: reduce)").matches
        };

        // --- MODULE: THEME ENGINE ---
        const ThemeEngine = {
            init() {
                const toggleBtn = document.getElementById('theme-toggle');
                const mobileBtn = document.getElementById('theme-toggle-mobile');
                const html = document.documentElement;

                // Load saved preference
                const saved = localStorage.getItem('theme') || 'dark';
                html.classList.add(saved);

                const switchTheme = () => {
                    const isDark = html.classList.contains('dark');
                    html.classList.remove(isDark ? 'dark' : 'light');
                    html.classList.add(isDark ? 'light' : 'dark');
                    localStorage.setItem('theme', isDark ? 'light' : 'dark');
                };

                if(toggleBtn) toggleBtn.addEventListener('click', switchTheme);
                if(mobileBtn) mobileBtn.addEventListener('click', switchTheme);
            }
        };

        // --- MODULE: CURSOR SYSTEM ---
        const CursorSystem = {
            init() {
                if (Utils.isTouch() || Utils.prefersReducedMotion()) return;
                
                document.body.classList.add('custom-cursor-active');
                const dot = document.getElementById('cursor-dot');
                const outline = document.getElementById('cursor-outline');
                
                let dotPos = { x: window.innerWidth/2, y: window.innerHeight/2 };
                let outPos = { x: window.innerWidth/2, y: window.innerHeight/2 };
                let targetPos = { x: window.innerWidth/2, y: window.innerHeight/2 };

                window.addEventListener('mousemove', e => {
                    targetPos.x = e.clientX;
                    targetPos.y = e.clientY;
                    dotPos.x = targetPos.x;
                    dotPos.y = targetPos.y;
                    dot.style.transform = `translate(${dotPos.x}px, ${dotPos.y}px)`;
                });

                const loop = () => {
                    // Outline follows with lerp
                    outPos.x = Utils.lerp(outPos.x, targetPos.x, 0.15);
                    outPos.y = Utils.lerp(outPos.y, targetPos.y, 0.15);
                    outline.style.transform = `translate(${outPos.x}px, ${outPos.y}px)`;
                    requestAnimationFrame(loop);
                };
                loop();

                // Interactive hovers
                document.querySelectorAll('a, button, [role="button"], .project-card').forEach(el => {
                    el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
                    el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
                });
            }
        };

        // --- MODULE: BACKGROUND ENGINE (Three.js) ---
        const BgEngine = {
            init() {
                if (Utils.prefersReducedMotion() || typeof THREE === 'undefined') return;

                const canvas = document.getElementById('bg-canvas');
                const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: false }); // Antialias off for performance
                renderer.setSize(window.innerWidth, window.innerHeight);
                renderer.setPixelRatio(Math.min(window.devicePixelRatio, 1.5)); // Cap pixel ratio for stability

                const scene = new THREE.Scene();
                const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 100);
                camera.position.z = 3;

                // Particle System
                const count = Utils.isTouch() ? 800 : 2000;
                const geometry = new THREE.BufferGeometry();
                const positions = new Float32Array(count * 3);
                
                for(let i=0; i<count*3; i++) {
                    positions[i] = (Math.random() - 0.5) * 10;
                }
                geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
                
                const material = new THREE.PointsMaterial({
                    size: 0.015,
                    color: 0x38bdf8, // Sky-400
                    transparent: true,
                    opacity: 0.5,
                    blending: THREE.AdditiveBlending
                });
                
                const mesh = new THREE.Points(geometry, material);
                scene.add(mesh);

                // Mouse interaction
                let mouseX = 0, mouseY = 0;
                if(!Utils.isTouch()) {
                    window.addEventListener('mousemove', e => {
                        mouseX = (e.clientX / window.innerWidth) - 0.5;
                        mouseY = (e.clientY / window.innerHeight) - 0.5;
                    });
                }

                // Animation Loop with Stability Check
                const animate = () => {
                    if(document.hidden) return; // Optimization: Pause when tab hidden

                    mesh.rotation.y += 0.001;
                    mesh.rotation.x += 0.0005;
                    
                    // Parallax
                    camera.position.x += (mouseX * 0.5 - camera.position.x) * 0.05;
                    camera.position.y += (-mouseY * 0.5 - camera.position.y) * 0.05;
                    camera.lookAt(scene.position);

                    renderer.render(scene, camera);
                    requestAnimationFrame(animate);
                };
                animate();

                // Resize handler
                window.addEventListener('resize', () => {
                    camera.aspect = window.innerWidth / window.innerHeight;
                    camera.updateProjectionMatrix();
                    renderer.setSize(window.innerWidth, window.innerHeight);
                });
            }
        };

        // --- MODULE: UI SYSTEMS ---
        const UISystems = {
            initMobileMenu() {
                const btn = document.getElementById('mobile-menu-btn');
                const menu = document.getElementById('mobile-menu');
                const links = document.querySelectorAll('.nav-link-mobile');
                let isOpen = false;

                const toggle = () => {
                    isOpen = !isOpen;
                    menu.classList.toggle('translate-x-full', !isOpen);
                    document.body.style.overflow = isOpen ? 'hidden' : '';
                    btn.setAttribute('aria-expanded', isOpen);
                };

                if(btn) btn.addEventListener('click', toggle);
                links.forEach(l => l.addEventListener('click', toggle));
            },

            initScroll() {
                const progressBar = document.getElementById('scroll-progress');
                const header = document.getElementById('header');
                const revealElements = document.querySelectorAll('[data-stagger-reveal]');
                
                // Throttled Scroll Listener (dx/dt Stability)
                let ticking = false;
                window.addEventListener('scroll', () => {
                    if (!ticking) {
                        window.requestAnimationFrame(() => {
                            const scrollTop = window.scrollY;
                            const docHeight = document.documentElement.scrollHeight - window.innerHeight;
                            const progress = (scrollTop / docHeight) * 100;
                            
                            if(progressBar) progressBar.style.width = `${progress}%`;

                            if(scrollTop > 50) {
                                header.classList.add('backdrop-blur-md', 'bg-white/80', 'dark:bg-slate-900/80', 'shadow-md', 'border-slate-200', 'dark:border-slate-800');
                                header.classList.remove('border-transparent');
                            } else {
                                header.classList.remove('backdrop-blur-md', 'bg-white/80', 'dark:bg-slate-900/80', 'shadow-md', 'border-slate-200', 'dark:border-slate-800');
                                header.classList.add('border-transparent');
                            }
                            ticking = false;
                        });
                        ticking = true;
                    }
                });

                // Intersection Observer for Reveals
                const observer = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if(entry.isIntersecting) {
                            entry.target.classList.add('is-revealed');
                            observer.unobserve(entry.target); // Efficiency: One-shot observation
                        }
                    });
                }, { threshold: 0.1 });

                revealElements.forEach(el => observer.observe(el));
            },

            initCommandPalette() {
                const palette = document.getElementById('command-palette');
                const overlay = document.getElementById('command-palette-overlay');
                const input = document.getElementById('command-palette-input');
                const allItems = Array.from(document.querySelectorAll('.command-item'));
                let visibleItems = [];
                let selectedIndex = 0;

                const open = () => {
                    palette.classList.add('visible');
                    overlay.classList.add('visible');
                    input.focus();
                    input.value = '';
                    filterItems('');
                };

                const close = () => {
                    palette.classList.remove('visible');
                    overlay.classList.remove('visible');
                };

                const updateSelection = () => {
                    allItems.forEach(item => item.classList.remove('selected'));
                    if (visibleItems.length > 0 && visibleItems[selectedIndex]) {
                        visibleItems[selectedIndex].classList.add('selected');
                        visibleItems[selectedIndex].scrollIntoView({ block: 'nearest' });
                    }
                };

                const filterItems = (query) => {
                    const lowerQuery = query.toLowerCase();
                    visibleItems = allItems.filter(item => {
                        const match = item.textContent.toLowerCase().includes(lowerQuery);
                        item.style.display = match ? 'flex' : 'none';
                        return match;
                    });
                    selectedIndex = 0;
                    updateSelection();
                };

                // Keyboard Logic (Symbolic Completion)
                window.addEventListener('keydown', e => {
                    if((e.ctrlKey || e.metaKey) && e.key === 'k') {
                        e.preventDefault();
                        palette.classList.contains('visible') ? close() : open();
                    }
                    if(e.key === 'Escape' && palette.classList.contains('visible')) close();
                    
                    if(palette.classList.contains('visible')) {
                        if(e.key === 'ArrowDown') {
                            e.preventDefault();
                            selectedIndex = (selectedIndex + 1) % visibleItems.length;
                            updateSelection();
                        }
                        if(e.key === 'ArrowUp') {
                            e.preventDefault();
                            selectedIndex = (selectedIndex - 1 + visibleItems.length) % visibleItems.length;
                            updateSelection();
                        }
                        if(e.key === 'Enter') {
                            e.preventDefault();
                            if(visibleItems[selectedIndex]) {
                                visibleItems[selectedIndex].click();
                            }
                        }
                    }
                });

                input.addEventListener('input', (e) => filterItems(e.target.value));
                overlay.addEventListener('click', close);
                allItems.forEach(item => {
                    item.addEventListener('click', () => {
                        close();
                        const target = document.querySelector(item.getAttribute('href'));
                        if(target) setTimeout(() => target.scrollIntoView({behavior: 'smooth'}), 10);
                    });
                });
            }
        };

        // --- GLOBAL HELPER: CLIPBOARD ---
        window.copyToClipboard = (text, el) => {
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(text).then(() => {
                    const feedback = el.querySelector('.copy-feedback');
                    if(feedback) {
                        feedback.style.opacity = '1';
                        setTimeout(() => feedback.style.opacity = '0', 2000);
                    }
                }).catch(err => console.error('Clipboard failed', err));
            } else {
                // Fallback for older browsers
                const textArea = document.createElement("textarea");
                textArea.value = text;
                document.body.appendChild(textArea);
                textArea.select();
                try {
                    document.execCommand("copy");
                    const feedback = el.querySelector('.copy-feedback');
                    if(feedback) {
                        feedback.style.opacity = '1';
                        setTimeout(() => feedback.style.opacity = '0', 2000);
                    }
                } catch (err) {
                    console.error('Fallback clipboard failed', err);
                }
                document.body.removeChild(textArea);
            }
        };

        // --- SYSTEM BOOTSTRAP ---
        window.onload = () => {
            try { lucide.createIcons(); } catch(e) { console.warn('Icons failed to load'); }
            document.getElementById('year').textContent = new Date().getFullYear();
            
            ThemeEngine.init();
            CursorSystem.init();
            BgEngine.init();
            UISystems.initMobileMenu();
            UISystems.initScroll();
            UISystems.initCommandPalette();

            // Magnetic Button Effect
            if(!Utils.isTouch()) {
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
        };
    </script>
</body>
</html>
