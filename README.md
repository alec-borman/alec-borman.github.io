<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alec Borman | Salesforce Administrator & Developer Portfolio</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- Google Fonts (Inter) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">

    <!-- Lucide Icons CDN -->
    <script src="https://unpkg.com/lucide-icons"></script>

    <style>
        /* Base styles */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0F172A; /* slate-900 */
            color: #E2E8F0; /* slate-200 */
            scroll-padding-top: 72px; /* Header height */
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* Custom gradient text */
        .gradient-text {
            background: linear-gradient(to right, #38bdf8, #818cf8); /* sky-500 to indigo-400 */
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Custom gradient for borders on cards */
        .gradient-border-card {
            background: linear-gradient(#1E293B, #1E293B) padding-box, /* slate-800 */
                        linear-gradient(135deg, #38bdf8, #818cf8) border-box; /* Brighter gradient border */
            border: 1px solid transparent;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
        }
         .gradient-border-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 25px rgba(56, 189, 248, 0.15), 0 5px 10px rgba(129, 140, 248, 0.1); /* sky/indigo shadow */
        }

        /* Hamburger menu transition */
        .hamburger-line {
            transition: all 0.3s ease-in-out;
            background-color: #ffffff;
            height: 2px;
            border-radius: 1px;
        }
        #menu-btn.open .hamburger-top {
            transform: rotate(45deg) translate(5px, 6px);
        }
        #menu-btn.open .hamburger-middle {
            opacity: 0;
            transform: translateX(-16px);
        }
        #menu-btn.open .hamburger-bottom {
            transform: rotate(-45deg) translate(5px, -6px);
        }
        
        /* Timeline styles for experience */
        .timeline-item {
            position: relative;
            padding-left: 2.5rem; /* 40px */
            padding-bottom: 2rem; /* 32px */
            border-left: 2px solid #334155; /* slate-700 */
        }
        .timeline-item:last-child {
            border-left: 2px solid transparent;
            padding-bottom: 0;
        }
        .timeline-dot {
            position: absolute;
            left: -9px; /* Adjust to center dot on line */
            top: 4px;
            width: 18px;
            height: 18px;
            background-color: #38bdf8; /* sky-500 */
            border-radius: 50%;
            border: 4px solid #0F172A; /* slate-900 */
        }
        .timeline-item h3 {
            color: #f1f5f9; /* slate-100 */
        }
        .timeline-item .company-name {
            color: #94a3b8; /* slate-400 */
        }
        .timeline-item ul {
            list-style-type: none;
            padding-left: 0.25rem;
            margin-top: 0.75rem;
        }
        .timeline-item li {
            position: relative;
            padding-left: 1.25rem;
            color: #cbd5e1; /* slate-300 */
            font-size: 0.875rem; /* text-sm */
            line-height: 1.6;
            margin-bottom: 0.5rem;
        }
        .timeline-item li::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0.55em;
            width: 5px;
            height: 5px;
            background-color: #60a5fa; /* blue-400 */
            border-radius: 50%;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header -->
    <header class="bg-slate-900/80 backdrop-blur-md sticky top-0 z-50 shadow-lg border-b border-slate-700/50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <!-- Logo -->
            <a href="#home" class="text-2xl font-bold text-white flex items-center gap-2 transition-opacity hover:opacity-80">
                <i data-lucide="code-2" class="w-7 h-7 text-sky-400"></i>
                <span class="font-extrabold tracking-tight">Alec</span>
                <span class="gradient-text font-extrabold tracking-tight">Borman</span>
            </a>

            <!-- Desktop Nav -->
            <div class="hidden md:flex space-x-7 items-center">
                <a href="#home" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">Home</a>
                <a href="#about" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">About</a>
                <a href="#philosophy" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">Philosophy</a>
                <a href="#experience" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">Experience</a>
                <a href="#projects" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">Projects</a>
                <a href="#recommendations" class="text-slate-300 hover:text-sky-400 transition-colors text-sm font-medium">Recommendations</a>
                <a href="#contact" class="bg-sky-500 hover:bg-sky-600 text-white font-bold px-6 py-2.5 rounded-md text-sm transition-all shadow-md hover:shadow-lg transform hover:-translate-y-0.5">
                    Contact Me
                </a>
            </div>

            <!-- Mobile Menu Button -->
            <button id="menu-btn" class="md:hidden focus:outline-none flex flex-col justify-center items-center w-6 h-6 z-50" aria-label="Open menu" aria-expanded="false" aria-controls="menu">
                <span class="hamburger-line hamburger-top block w-full rounded-full"></span>
                <span class="hamburger-line hamburger-middle block w-full rounded-full mt-1.5"></span>
                <span class="hamburger-line hamburger-bottom block w-full rounded-full mt-1.5"></span>
            </button>
        </nav>

        <!-- Mobile Nav -->
        <div id="menu" class="hidden md:hidden flex-col absolute top-full left-0 w-full bg-slate-900 shadow-xl pb-4 border-t border-slate-700" aria-hidden="true">
            <a href="#home" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">Home</a>
            <a href="#about" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">About</a>
            <a href="#philosophy" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">Philosophy</a>
            <a href="#experience" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">Experience</a>
            <a href="#projects" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">Projects</a>
            <a href="#recommendations" class="block text-center text-slate-200 py-4 hover:bg-slate-800 transition-colors mobile-nav-link font-medium">Recommendations</a>
            <a href="#contact" class="block text-center bg-sky-500 text-white font-bold px-6 py-3 mx-6 mt-3 rounded-md hover:bg-sky-600 transition-colors mobile-nav-link shadow-lg">
                Contact Me
            </a>
        </div>
    </header>

    <main>
        <!-- ====== Hero Section ====== -->
        <section id="home" class="relative pt-28 pb-36 md:pt-36 md:pb-48 overflow-hidden">
            <!-- Gradient Background -->
            <div class="absolute inset-0 -z-10 opacity-70">
                <div class="absolute top-0 left-0 w-[60rem] h-[60rem] bg-gradient-to-br from-sky-600/20 via-slate-900 to-transparent -translate-x-1/2 -translate-y-1/3 rounded-full blur-3xl"></div>
                <div class="absolute bottom-0 right-0 w-[50rem] h-[50rem] bg-gradient-to-tl from-indigo-700/20 via-slate-900 to-transparent translate-x-1/3 translate-y-1/3 rounded-full blur-3xl"></div>
            </div>

            <div class="container mx-auto px-6 text-center">
                <span class="inline-block bg-sky-500/10 text-sky-400 text-xs font-bold px-4 py-1.5 rounded-full mb-5 border border-sky-400/30 uppercase tracking-wider">Salesforce Administrator & Automation Expert</span>
                <h1 class="text-4xl sm:text-5xl md:text-6xl font-extrabold text-white leading-tight mb-6">
                    Alec Borman
                </h1>
                <p class="text-lg md:text-xl text-slate-300 max-w-3xl mx-auto mb-12 leading-relaxed">
                    I translate complex business needs into secure, scalable, and efficient Salesforce solutions that drive user adoption, reduce manual work, and accelerate operational excellence.
                </p>
                <div class="flex flex-col sm:flex-row justify-center gap-5">
                    <a href="#projects" class="bg-sky-500 hover:bg-sky-600 text-white font-bold px-8 py-3.5 rounded-lg text-base transition-all transform hover:scale-105 shadow-lg hover:shadow-sky-500/30">
                        View My Projects
                    </a>
                    <a href="#contact" class="bg-slate-700 hover:bg-slate-600 text-slate-100 font-bold px-8 py-3.5 rounded-lg text-base transition-all transform hover:scale-105 shadow-lg hover:shadow-slate-500/30 border border-slate-600">
                        Get In Touch
                    </a>
                </div>
            </div>
        </section>

        <!-- ====== About Me & Skills Section ====== -->
        <section id="about" class="py-24 md:py-32 bg-slate-900/70 relative overflow-hidden">
            <!-- Subtle Background Pattern -->
            <div class="absolute inset-0 opacity-[0.02] bg-[url('data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%220%200%2040%2040%22%3E%3Cpath%20fill%3D%22%2394a3b8%22%20d%3D%22M0%200h20v20H0zM20%2020h20v20H20z%22%2F%3E%3C%2Fsvg%3E')]"></div>
            <div class="container mx-auto px-6 relative">
                <div class="grid md:grid-cols-1 lg:grid-cols-5 gap-16 lg:gap-24 items-start">
                    <!-- About Me -->
                    <div class="lg:col-span-3">
                        <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">About Me</span>
                        <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-8">Strategic Business Architect</h2>
                        <div class="space-y-6 text-slate-300 text-base leading-relaxed">
                             <p>A Strategic Business Architect who specializes in building the operational backbone for companies that are ready to scale explosively.</p>
                             <p>I translate complex GTM strategy into foundational, end-to-end technical solutions, building the core internal tooling and automation that accelerates sales velocity and operational excellence.</p>
                        </div>
                        
                        <!-- Pillars of Expertise -->
                        <div class="mt-12">
                            <h3 class="text-2xl font-bold text-white mb-6">Pillars of Expertise</h3>
                            <div class="space-y-6">
                                <!-- Pillar 1 -->
                                <div>
                                    <h4 class="text-lg font-semibold text-slate-100 mb-2 flex items-center gap-3">
                                        <i data-lucide="compass" class="w-5 h-5 text-indigo-400 shrink-0"></i>
                                        Strategic Architecture & Solution Design
                                    </h4>
                                    <p class="text-slate-400 text-sm">Architecting GTM tech stacks and internal tooling ecosystems from the ground up. Expert in stakeholder management and translating high-level strategy into a robust, scalable systems roadmap.</p>
                                </div>
                                <!-- Pillar 2 -->
                                <div>
                                    <h4 class="text-lg font-semibold text-slate-100 mb-2 flex items-center gap-3">
                                        <i data-lucide="code-2" class="w-5 h-5 text-indigo-400 shrink-0"></i>
                                        Full-Stack Systems Development
                                    </h4>
                                    <p class="text-slate-400 text-sm">Building custom, end-to-end solutions within the Salesforce ecosystem (Apex, LWC, Visualforce) to overcome platform limitations and deliver highly tailored user workflows.</p>
                                </div>
                                <!-- Pillar 3 -->
                                <div>
                                    <h4 class="text-lg font-semibold text-slate-100 mb-2 flex items-center gap-3">
                                        <i data-lucide="zap" class="w-5 h-5 text-indigo-400 shrink-0"></i>
                                        Intelligent Automation & Integration
                                    </h4>
                                    <p class="text-slate-400 text-sm">Leveraging AI-driven tools for rapid prototyping and complex API integrations (Zapier) to automate critical workflows, synchronize enterprise data, and eliminate high-cost manual processes.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Core Competencies -->
                    <div class="lg:col-span-2">
                        <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">My Toolkit</span>
                        <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-8">Core Technologies & Methodologies</h2>
                        
                        <div class="space-y-8">
                            <!-- Platforms & Tools -->
                            <div>
                                <h3 class="text-xl font-bold text-slate-100 mb-3 flex items-center gap-3">
                                    <i data-lucide="database" class="w-6 h-6 text-indigo-400"></i>
                                    Platforms & Tools
                                </h3>
                                <div class="flex flex-wrap gap-2">
                                    <span class="skill-badge">Salesforce Ecosystem</span>
                                    <span class="skill-badge">Sales Cloud</span>
                                    <span class="skill-badge">Salesforce Flow</span>
                                    <span class="skill-badge">Apex</span>
                                    <span class="skill-badge">LWC</span>
                                    <span class="skill-badge">Visualforce</span>
                                    <span class="skill-badge">Zapier</span>
                                    <span class="skill-badge">Jira</span>
                                    <span class="skill-badge">HubSpot</span>
                                    <span class="skill-badge">Glovia OM ERP</span>
                                    <span class="skill-badge">Asana</span>
                                </div>
                            </div>
                            
                            <!-- Methodologies -->
                            <div>
                                <h3 class="text-xl font-bold text-slate-100 mb-3 flex items-center gap-3">
                                    <i data-lucide="clipboard-check" class="w-6 h-6 text-indigo-400"></i>
                                    Methodologies
                                </h3>
                                <div class="flex flex-wrap gap-2">
                                    <span class="skill-badge">Agile/Kanban</span>
                                    <span class="skill-badge">GTM Strategy</span>
                                    <span class="skill-badge">Sales Operations</span>
                                    <span class="skill-badge">Presales Engineering</span>
                                    <span class="skill-badge">Business Process Re-engineering</span>
                                    <span class="skill-badge">Gap Analysis</span>
                                    <span class="skill-badge">Requirements Gathering</span>
                                </div>
                            </div>

                            <!-- Concepts -->
                            <div>
                                <h3 class="text-xl font-bold text-slate-100 mb-3 flex items-center gap-3">
                                    <i data-lucide="server" class="w-6 h-6 text-indigo-400"></i>
                                    Concepts
                                </h3>
                                <div class="flex flex-wrap gap-2">
                                    <span class="skill-badge">API Integration</span>
                                    <span class="skill-badge">Data Synchronization</span>
                                    <span class="skill-badge">Order Management</span>
                                    <span class="skill-badge">Business Requirements Documents (BRDs)</span>
                                    <span class="skill-badge">User Story & Acceptance Criteria</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- ====== Philosophy Section ====== -->
        <section id="philosophy" class="py-24 md:py-32 bg-slate-900">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto">
                    <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">My Approach</span>
                    <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-6">An AI-Assisted, First-Principles Approach</h2>
                    <p class="text-lg text-slate-300 mb-12 leading-relaxed">
                        To understand my work, you first have to understand how I think.
                    </p>
                </div>

                <div class="max-w-4xl mx-auto grid md:grid-cols-5 gap-8">
                    <div class="md:col-span-2 flex justify-center md:justify-start">
                        <div class="p-6 bg-slate-800/50 border border-slate-700 rounded-xl">
                            <i data-lucide="brain-circuit" class="w-16 h-16 text-indigo-400 mx-auto mb-4"></i>
                            <blockquote class="text-center italic text-slate-200">
                                "Imagine an architect working inside a pitch-black box. Without sight, they have to learn everything by feel. They have to deeply, fundamentally understand every material and connection to know what they're building."
                            </blockquote>
                        </div>
                    </div>
                    <div class="md:col-span-3 space-y-4 text-slate-300 text-base leading-relaxed">
                        <p>That's how I operate. When I’m in a business meeting, my primary focus is to listen. I’m absorbing the complex systems, the processes, and most importantly, the pain points. My inner architect is quietly working in the background, building a complete model of the problem.</p>
                        <p>Once I fully understand that problem at its root, I translate that fully-formed idea to an AI. I use it as a powerful tool to instantly flesh out my concepts, build documentation, create development guides, and turn those guides into user-friendly manuals.</p>
                        <p>This approach gives me a level of presence and focus that is a strong asset. All my energy goes into modeling the problem, understanding the nuances, and picking up on the small, critical details that are often missed. It allows me to build solutions from a place of true understanding.</p>
                        <p class="text-white font-semibold">Ultimately, I’m an insightful problem-solver and a positive presence, and I'm confident this unique approach makes me a valuable asset to any team.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Skill Badge CSS (injected via <style> for brevity) -->
        <style>
            .skill-badge {
                display: inline-block;
                background-color: #1e293b; /* slate-800 */
                color: #94a3b8; /* slate-400 */
                font-size: 0.75rem; /* text-xs */
                font-weight: 500; /* font-medium */
                padding: 0.25rem 0.75rem; /* px-3 py-1 */
                border-radius: 9999px; /* rounded-full */
                border: 1px solid #334155; /* border-slate-700 */
            }
        </style>

        <!-- ====== Experience Section ====== -->
        <section id="experience" class="py-24 md:py-32 bg-slate-900/90">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto">
                    <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">My Journey</span>
                    <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-16">Professional Experience</h2>
                </div>

                <div class="max-w-3xl mx-auto">
                    <!-- Timeline Start -->
                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">Oct 2024 – Present</p>
                        <h3 class="text-xl font-bold">Business Systems Architect</h3>
                        <p class="company-name text-base font-medium mb-3">Hydrolix (Remote)</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>I joined Hydrolix as the foundational systems administrator and grew into the role of strategic architect, tasked with building the company's operational backbone: Salesforce as the central financial tool and usage tracker for our SaaS deployments. My core challenge was to deliver immediate, tactical solutions to keep the business running while architecting a robust, long-term system.</p>
                            <p><strong>Balanced Immediate Needs with Long-Term Vision:</strong> Designed and deployed a new lead-to-opportunity process that cut lead response time by 40%. This involved creating interim workflows to provide immediate relief to the sales team while the permanent, fully automated architecture was being built in the background.</p>
                            <p><strong>Engineered End-to-End Automation:</strong> Managed deployments from initial POC to active contract. This included building systems for monthly POC credit approvals, tracking contract usage quotas (in TB/month), and orchestrating all automated customer communications. I personally designed and coded the HTML email templates and used Zapier to trigger critical notifications.</p>
                            <p><strong>Served as the Cross-Functional Systems Hub:</strong> Acted as the technical bridge between Sales, CSE, and SRE teams, translating their immediate pain points into quick-win solutions while ensuring those fixes aligned with the larger, strategic systems roadmap.</p>
                        </div>
                    </div>
                    
                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">Sep 2024 – Present</p>
                        <h3 class="text-xl font-bold">Salesforce Consultant / Developer</h3>
                        <p class="company-name text-base font-medium mb-3">GIVE US PAWS (Contract / Volunteer)</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>Provide expert consulting and development services to Give Us Paws, a 501c nonprofit requiring a new Salesforce system. This included managed package discovery, requirements gathering, design, license acquisition, configuration, customization, data import, and continued support for their "Dog and Client Tracker" managed package.</p>
                        </div>
                    </div>

                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">Jun 2024 – Aug 2024</p>
                        <h3 class="text-xl font-bold">Salesforce Architect / Consultant</h3>
                        <p class="company-name text-base font-medium mb-3">Jaco Aerospace, Inc. (Contract)</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>Provided expertise in business processes, configuring and optimizing Salesforce Sales Cloud with Order Management and ERP features, specifically leveraging the managed package Glovia OM. Designed, developed, and tested custom logic to overcome managed package limitations. This included creating Apex controllers, custom buttons, and Visualforce pages to prepopulate fields for new records, significantly reducing data entry time and improving workflow efficiency.</p>
                        </div>
                    </div>

                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">Mar 2022 – Oct 2023</p>
                        <h3 class="text-xl font-bold">Salesforce Developer</h3>
                        <p class="company-name text-base font-medium mb-3">Fujitsu (Contracted to Royal Canin) (Hybrid)</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>As a Salesforce Developer and Support Specialist for the Salesforce Sales Cloud managed package, Glovia OM, I provided expert advice and integrated its ERP and Order Management features. I addressed and resolved support queries, and after completing training, I applied my knowledge by resolving tickets and collaborating with a team of developers to design, implement, test, document, and refine solutions, ensuring supply chain reliability.</p>
                        </div>
                    </div>

                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">Jan 2020 – Mar 2022</p>
                        <h3 class="text-xl font-bold">Marketing Campaign Manager</h3>
                        <p class="company-name text-base font-medium mb-3">GIVE US PAWS (Contract)</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>Designed, tested, and implemented Google ad campaigns for GiveUsPaws, a 501c Non-profit that focuses on training service dogs for disabled veterans.</p>
                        </div>
                    </div>

                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">May 2019 – Aug 2019</p>
                        <h3 class="text-xl font-bold">IT Intern</h3>
                        <p class="company-name text-base font-medium mb-3">Austin Industrial, Inc.</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>Diagnosed issues, deployed devices, and tracked devices with inventory management software.</p>
                        </div>
                    </div>

                    <div class="timeline-item">
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium text-sky-400 mb-1">May 2018 – Aug 2018</p>
                        <h3 class="text-xl font-bold">Devops Intern</h3>
                        <p class="company-name text-base font-medium mb-3">Austin Industrial, Inc.</p>
                        <div class="space-y-4 text-slate-300 text-sm leading-relaxed">
                            <p>Researched intrinsically safe cases, software, and hardware for RFID site tracking. Deployed 400 iPad devices with custom software. Digitized Job Safety Analysis audits and maintained user guides.</p>
                        </div>
                    </div>
                    <!-- Timeline End -->
                </div>
            </div>
        </section>

        <!-- ====== Projects Section ====== -->
        <section id="projects" class="py-24 md:py-32 bg-slate-900/70">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto">
                    <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">My Work</span>
                    <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-16">Featured Projects</h2>
                </div>

                <!-- Projects Grid -->
                <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
                    
                    <!-- Project Card: Hydrolix Decommissioning -->
                    <div class="project-card gradient-border-card rounded-2xl overflow-hidden">
                        <img src="https://placehold.co/600x400/1e293b/38bdf8?text=AI+Automation+Process&font=inter"
                             alt="Hydrolix AI Automation Project"
                             class="w-full h-48 object-cover"
                             onerror="this.src='https://placehold.co/600x400/1e293b/94a3b8?text=Image+Not+Available&font=inter'; this.onerror=null;">
                        <div class="p-6 flex flex-col flex-grow">
                            <span class="text-xs font-medium text-indigo-400 mb-1 uppercase">AI-Driven System Architecture</span>
                            <h3 class="text-xl font-semibold text-white mb-3">Automated Tenant Decommissioning</h3>
                            <p class="text-slate-400 text-sm leading-relaxed mb-4 flex-grow">
                                Architected a fully automated decommissioning process for Hydrolix tenants. Leveraged Google Cloud's Vertex AI within a secure environment to partner with AI, rapidly modeling and building flawless, interconnected logic spanning Salesforce, Zapier, and Jira. This created a scalable, reliable, and predictable experience for teams and customers.
                            </p>
                            <div class="mt-auto pt-4">
                                <span class="skill-badge">Vertex AI</span>
                                <span class="skill-badge">System Architecture</span>
                                <span class="skill-badge">Salesforce</span>
                                <span class="skill-badge">Zapier</span>
                                <span class="skill-badge">Jira</span>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card: HSE Solutions -->
                    <div class="project-card gradient-border-card rounded-2xl overflow-hidden">
                        <img src="https://placehold.co/600x400/1e293b/38bdf8?text=HSE+Solutions+Website&font=inter"
                             alt="HSE Solutions Website Screenshot"
                             class="w-full h-48 object-cover"
                             onerror="this.src='https://placehold.co/600x400/1e293b/94a3b8?text=Image+Not+Available&font=inter'; this.onerror=null;">
                        <div class="p-6 flex flex-col flex-grow">
                            <span class="text-xs font-medium text-indigo-400 mb-1 uppercase">Pro-Bono Web Development</span>
                            <h3 class="text-xl font-semibold text-white mb-3">HSE Solutions, Inc.</h3>
                            <p class="text-slate-400 text-sm leading-relaxed mb-4 flex-grow">
                                Led a pro-bono, end-to-end website redevelopment for a major HSE consulting firm. Designed and built a modern, responsive, single-page application from scratch using HTML, Tailwind CSS, and JavaScript to showcase their comprehensive services and client list.
                            </p>
                            <div class="mt-auto pt-4">
                                <span class="skill-badge">HTML5</span>
                                <span class="skill-badge">Tailwind CSS</span>
                                <span class="skill-badge">JavaScript</span>
                                <span class="skill-badge">UI/UX Design</span>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card: GIVE US PAWS -->
                    <div class="project-card gradient-border-card rounded-2xl overflow-hidden">
                        <img src="https://placehold.co/600x400/1e293b/38bdf8?text=GIVE+US+PAWS+Salesforce&font=inter"
                             alt="GIVE US PAWS Project Screenshot"
                             class="w-full h-48 object-cover"
                             onerror="this.src='https://placehold.co/600x400/1e293b/94a3b8?text=Image+Not+Available&font=inter'; this.onerror=null;">
                        <div class="p-6 flex flex-col flex-grow">
                            <span class="text-xs font-medium text-indigo-400 mb-1 uppercase">Pro-Bono Salesforce Implementation</span>
                            <h3 class="text-xl font-semibold text-white mb-3">GIVE US PAWS</h3>
                            <p class="text-slate-400 text-sm leading-relaxed mb-4 flex-grow">
                                Managed a complete, end-to-end Salesforce implementation for a 501c nonprofit. Handled requirements gathering, license acquisition, configuration, and user training. Heavily customized the "Dog and Client Tracker" managed package to fit their unique operational needs.
                            </p>
                            <div class="mt-auto pt-4">
                                <span class="skill-badge">Salesforce Admin</span>
                                <span class="skill-badge">NPSP</span>
                                <span class="skill-badge">Flow Automation</span>
                                <span class="skill-badge">Managed Packages</span>
                                <span class="skill-badge">Requirements Gathering</span>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card: Jaco Aerospace -->
                    <div class="project-card gradient-border-card rounded-2xl overflow-hidden">
                        <img src="https://placehold.co/600x400/1e293b/38bdf8?text=Jaco+Aerospace+ERP+Integration&font=inter"
                             alt="Jaco Aerospace Project Screenshot"
                             class="w-full h-48 object-cover"
                             onerror="this.src='https://placehold.co/600x400/1e293b/94a3b8?text=Image+Not+Available&font=inter'; this.onerror=null;">
                        <div class="p-6 flex flex-col flex-grow">
                            <span class="text-xs font-medium text-indigo-400 mb-1 uppercase">Salesforce Development & Integration</span>
                            <h3 class="text-xl font-semibold text-white mb-3">Jaco Aerospace, Inc.</h3>
                            <p class="text-slate-400 text-sm leading-relaxed mb-4 flex-grow">
                                Developed custom solutions to streamline a complex Salesforce org with an integrated Glovia OM ERP. Built custom Apex controllers, Visualforce pages, and LWC components to overcome managed package limitations, significantly reducing data entry time and enhancing operational efficiency.
                            </p>
                            <div class="mt-auto pt-4">
                                <span class="skill-badge">Apex</span>
                                <span class="skill-badge">LWC</span>
                                <span class="skill-badge">Visualforce</span>
                                <span class="skill-badge">ERP Integration</span>
                                <span class="skill-badge">Glovia OM</span>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- ====== Recommendations Section ====== -->
        <section id="recommendations" class="py-24 md:py-32 bg-slate-900/70">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto">
                    <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">Testimonials</span>
                    <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-16">What My Colleagues Say</h2>
                </div>

                <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
                    <!-- Recommendation 1: Meg Blanchette -->
                    <div class="gradient-border-card rounded-2xl p-8">
                        <div class="flex items-center mb-4">
                            <img src="https://placehold.co/100x100/38bdf8/0F172A?text=MB&font=inter" alt="Meg Blanchette" class="w-16 h-16 rounded-full border-2 border-slate-700">
                            <div class="ml-4">
                                <h4 class="text-lg font-bold text-white">Meg Blanchette</h4>
                                <p class="text-sm text-slate-400">Messaging & Product Marketing @ Hydrolix.io</p>
                            </div>
                        </div>
                        <blockquote class="text-slate-300 italic leading-relaxed">
                            "Alec was lovely to work with! He was helpful and kind, I highly recommend adding him to your team."
                        </blockquote>
                    </div>

                    <!-- Recommendation 2: Berel Schusterman -->
                    <div class="gradient-border-card rounded-2xl p-8">
                        <div class="flex items-center mb-4">
                            <img src="https://placehold.co/100x100/818cf8/0F172A?text=BS&font=inter" alt="Berel Schusterman" class="w-16 h-16 rounded-full border-2 border-slate-700">
                            <div class="ml-4">
                                <h4 class="text-lg font-bold text-white">Berel Schusterman</h4>
                                <p class="text-sm text-slate-400">Innovative Aerospace & Defense Procurement Expert</p>
                            </div>
                        </div>
                        <blockquote class="text-slate-300 italic leading-relaxed">
                            "Alec's deep expertise with Fujitsu Glovia Software within Salesforce has been invaluable. His ability to navigate and optimize the system has significantly streamlined our processes... His technical knowledge, combined with his proactive approach, made him a crucial resource in our operations."
                        </blockquote>
                    </div>
                </div>
            </div>
        </section>


        <!-- ====== Contact Section ====== -->
        <section id="contact" class="py-24 md:py-32 relative overflow-hidden bg-slate-900">
            <!-- Background elements -->
             <div class="absolute inset-0 -z-10 opacity-50" aria-hidden="true">
                 <div class="absolute -top-60 -left-60 w-[40rem] h-[40rem] bg-gradient-to-r from-sky-600/15 to-transparent rounded-full blur-3xl"></div>
                 <div class="absolute -bottom-60 -right-60 w-[40rem] h-[40rem] bg-gradient-to-l from-indigo-700/15 to-transparent rounded-full blur-3xl"></div>
            </div>

            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto">
                    <span class="text-sm font-semibold text-sky-400 uppercase tracking-widest mb-2 inline-block">Get In Touch</span>
                    <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-1 mb-6">Let's Build Something Together</h2>
                    <p class="text-lg text-slate-300 mb-16 leading-relaxed">
                        Have a project in mind or just want to connect? Feel free to send me a message or reach out through email or LinkedIn.
                    </p>
                </div>

                <div class="grid md:grid-cols-5 gap-12 lg:gap-16 max-w-6xl mx-auto">
                    <!-- Contact Info -->
                    <div class="md:col-span-2 bg-slate-800/50 p-8 rounded-xl border border-slate-700 shadow-xl backdrop-blur-md">
                        <h3 class="text-2xl font-bold text-white mb-8">Contact Information</h3>
                        <div class="space-y-8">
                            <div class="flex items-start gap-4 group">
                                <i data-lucide="map-pin" class="w-5 h-5 text-sky-400 shrink-0 mt-1" aria-hidden="true"></i>
                                <div>
                                    <h4 class="text-base font-semibold text-white mb-1">Location</h4>
                                    <p class="text-slate-300 text-sm">Friendswood, TX (Remote)</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 group">
                                <i data-lucide="phone" class="w-5 h-5 text-sky-400 shrink-0 mt-1" aria-hidden="true"></i>
                                <div>
                                    <h4 class="text-base font-semibold text-white mb-1">Phone</h4>
                                    <a href="tel:2175087210" class="text-slate-300 text-sm hover:text-sky-300 transition-colors">(217) 508-7210</a>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 group">
                                <i data-lucide="mail" class="w-5 h-5 text-sky-400 shrink-0 mt-1" aria-hidden="true"></i>
                                <div>
                                    <h4 class="text-base font-semibold text-white mb-1">Email</h4>
                                    <a href="mailto:alecborman97@gmail.com" class="text-sky-400 hover:text-sky-300 text-sm transition-colors group-hover:underline">alecborman97@gmail.com</a>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 group">
                                <i data-lucide="linkedin" class="w-5 h-5 text-sky-400 shrink-0 mt-1" aria-hidden="true"></i>
                                <div>
                                    <h4 class="text-base font-semibold text-white mb-1">LinkedIn</h4>
                                    <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" rel="noopener noreferrer" class="text-sky-400 hover:text-sky-300 text-sm transition-colors group-hover:underline">in/alec-borman-9680b3160</a>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Contact Form -->
                    <form id="contact-form" class="md:col-span-3 space-y-6">
                        <h3 class="text-2xl font-bold text-white mb-2">Send Me a Message</h3>
                        <div class="grid sm:grid-cols-2 gap-6">
                            <div>
                                <label for="name" class="block text-sm font-medium text-slate-200 mb-2">Full Name*</label>
                                <input type="text" id="name" name="name" placeholder="e.g. Jane Doe" required autocomplete="name"
                                    class="w-full px-4 py-3 rounded-md bg-slate-800 border border-slate-700 text-white text-sm focus:outline-none focus:ring-2 focus:ring-sky-500 transition-colors placeholder-slate-500">
                            </div>
                            <div>
                                <label for="email" class="block text-sm font-medium text-slate-200 mb-2">Email Address*</label>
                                <input type="email" id="email" name="email" placeholder="you@company.com" required autocomplete="email"
                                    class="w-full px-4 py-3 rounded-md bg-slate-800 border border-slate-700 text-white text-sm focus:outline-none focus:ring-2 focus:ring-sky-500 transition-colors placeholder-slate-500">
                            </div>
                        </div>
                        <div>
                            <label for="message" class="block text-sm font-medium text-slate-200 mb-2">Your Message*</label>
                            <textarea id="message" name="message" rows="6" placeholder="Please describe your project or inquiry..." required
                                class="w-full px-4 py-3 rounded-md bg-slate-800 border border-slate-700 text-white text-sm focus:outline-none focus:ring-2 focus:ring-sky-500 transition-colors placeholder-slate-500"></textarea>
                        </div>
                        <div class="pt-2">
                            <button type="submit"
                                class="w-full bg-sky-500 hover:bg-sky-600 text-white font-bold px-8 py-3.5 rounded-md text-base transition-all transform hover:scale-[1.02] shadow-lg hover:shadow-sky-500/40 flex items-center justify-center gap-2">
                                <i data-lucide="send" class="w-5 h-5" aria-hidden="true"></i>
                                Send Message
                            </button>
                        </div>
                        <div id="form-success" class="!mt-4 hidden text-center text-green-400 font-semibold p-4 bg-green-900/50 rounded-lg border border-green-700 text-sm" aria-live="polite">
                            Message Sent Successfully! I'll be in touch shortly.
                        </div>
                         <div id="form-error" class="!mt-4 hidden text-center text-red-400 font-semibold p-4 bg-red-900/50 rounded-lg border border-red-700 text-sm" aria-live="polite">
                            Submission Failed. Please try again or contact me directly.
                        </div>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <!-- ====== Footer ====== -->
     <footer class="bg-slate-900 border-t border-slate-800 pt-16 pb-8">
         <div class="container mx-auto px-6">
             <div class="flex flex-col md:flex-row justify-between items-center">
                 <div class="text-center md:text-left mb-4 md:mb-0">
                     <a href="#home" class="text-lg font-bold text-white mb-4 inline-flex items-center gap-2 transition-opacity hover:opacity-80">
                         <i data-lucide="code-2" class="w-6 h-6 text-sky-400"></i>
                         Alec Borman | Salesforce Professional
                     </a>
                     <p class="text-slate-400 text-xs mt-2">
                         Friendswood, TX | <a href="tel:2175087210" class="hover:text-sky-400">(217) 508-7210</a> | <a href="mailto:alecborman97@gmail.com" class="hover:text-sky-400">alecborman97@gmail.com</a>
                     </p>
                 </div>
                 <div class="flex space-x-6">
                    <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-sky-400 transition-colors" aria-label="LinkedIn Profile">
                        <i data-lucide="linkedin" class="w-6 h-6"></i>
                    </a>
                    <!-- Add other social links like GitHub if you have one -->
                 </div>
             </div>
             <!-- Copyright -->
             <div class="mt-8 pt-8 border-t border-slate-800 text-center text-slate-500 text-sm">
                 &copy; 2025 Alec Borman. All rights reserved.
             </div>
         </div>
     </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {

            // --- Lucide Icons ---
            lucide.createIcons();

            // --- Mobile Menu Logic ---
            const menuBtn = document.getElementById('menu-btn');
            const menu = document.getElementById('menu');
            const mobileNavLinks = document.querySelectorAll('.mobile-nav-link');

            menuBtn.addEventListener('click', () => {
                const isOpened = menuBtn.classList.toggle('open');
                menu.classList.toggle('hidden');
                menu.classList.toggle('flex');
                menuBtn.setAttribute('aria-expanded', isOpened.toString());
                menu.setAttribute('aria-hidden', (!isOpened).toString());
                document.body.style.overflow = isOpened ? 'hidden' : '';
            });

            <!-- Close menu when a nav link is clicked -->
            mobileNavLinks.forEach(link => {
                link.addEventListener('click', () => {
                    if (link.getAttribute('href') && link.getAttribute('href').startsWith('#')) {
                        menuBtn.classList.remove('open');
                        menu.classList.add('hidden');
                        menu.classList.remove('flex');
                        menuBtn.setAttribute('aria-expanded', 'false');
                        menu.setAttribute('aria-hidden', 'true');
                        document.body.style.overflow = '';
                    }
                });
            });
            
            // --- Smooth scrolling for all anchor links ---
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    const targetElement = document.querySelector(targetId);
                    if(targetElement) {
                        targetElement.scrollIntoView({
                            behavior: 'smooth'
                        });
                    }
                });
            });

            // --- Contact Form Logic (Simulation) ---
            const contactForm = document.getElementById('contact-form');
            const successMessage = document.getElementById('form-success');
            const errorMessage = document.getElementById('form-error');

            if (contactForm) {
                contactForm.addEventListener('submit', (e) => {
                    e.preventDefault();
                    
                    // Clear previous messages
                    successMessage.classList.add('hidden');
                    errorMessage.classList.add('hidden');

                    // Get form data
                    const formData = new FormData(contactForm);
                    const name = formData.get('name');
                    const email = formData.get('email');
                    const message = formData.get('message');

                    // Basic validation
                    if (!name || !email || !message) {
                        errorMessage.textContent = "Please fill out all required fields.";
                        errorMessage.classList.remove('hidden');
                        return;
                    }

                    // --- Simulation ---
                    // In a real app, you'd send this data to a backend (e.g., Formspree, Netlify Forms, or a custom API)
                    console.log('Form submitted (simulation):', { name, email, message });

                    // Show success message
                    successMessage.classList.remove('hidden');
                    contactForm.reset();

                    // Hide success message after 5 seconds
                    setTimeout(() => {
                        successMessage.classList.add('hidden');
                    }, 5000);
                });
            }

        });
    </script>
</body>
</html>

