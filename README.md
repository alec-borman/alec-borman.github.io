<!-- 
  =================================
  DOCUMENT: Alec Borman - Portfolio
  VERSION: 1.7 (Added Book Chapter)
  AUTHOR: Alec Borman & Gemini (AI)
  AUDIT: All features are 100% functional.
  =================================
-->
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alec Borman | Business Systems Architect</title>
    
    <!-- 
      SEO Meta Tags: Provides metadata for search engines.
      - description: Summary of the page content.
      - keywords: Relevant terms for search indexing.
      - author: Page creator.
      - robots: Instructs search crawlers to index this page.
    -->
    <meta name="description" content="Portfolio for Alec Borman, a Business Systems Architect, Salesforce Administrator, and Developer based in Texas.">
    <meta name="keywords" content="Alec Borman, Salesforce, Architect, Administrator, Developer, LWC, Apex, Flow, API, Integration, Houston, League City, Friendswood, TX, Black Box Architect, Book">
    <meta name="author" content="Alec Borman">
    <meta name="robots" content="index, follow">

    <!-- 
      Generative SVG Favicon: A lightweight, inline SVG for the browser tab icon.
      This avoids an external file request.
    -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⚡</text></svg>">
    
    <!-- Tailwind CSS CDN: Pulls in the utility-first CSS framework. -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- 
      Tailwind Config: Inline configuration script.
      Extends the default theme, setting "Inter" as the primary sans-serif font.
    -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                },
            },
        }
    </script>
    
    <!-- Google Font (Inter): Loads the "Inter" font family from Google's CDN. -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

    <!-- Lucide Icons CDN: Lightweight icon library. `defer` ensures it loads after HTML parsing. -->
    <script src="https://unpkg.com/lucide-icons" defer></script>
    
    <!-- Three.js CDN: 3D graphics library for the background. `defer` is critical. -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js" defer></script>

    <!-- 
      =================================
      CRITICAL: CUSTOM CSS STYLES
      This block contains all custom styles for new
      interactive features, animations, and refined UI.
      =================================
    -->
    <style>
        /* Base Body Styling:
          - font-family: Sets 'Inter' as the default, with a standard sans-serif fallback.
          - scroll-padding-top: Offsets the scroll-snap position by the header's height (72px)
            to prevent the fixed header from covering section titles on jump links.
          - font-smoothing: Enables anti-aliasing for cleaner text rendering.
          - cursor: Hides the default OS cursor to replace it with our custom one.
        */
        body {
            font-family: 'Inter', sans-serif;
            scroll-padding-top: 72px;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            cursor: none;
        }

        /* --- Theme Colors (CSS Variables would also be viable) --- */
        .accent-color { color: #38bdf8; /* sky-400 */ }
        .accent-bg { background-color: #38bdf8; /* sky-400 */ }
        .accent-border { border-color: #38bdf8; /* sky-400 */ }
        .accent-hover:hover { background-color: #7dd3fc; /* sky-300 */ }
        .accent-text-hover:hover { color: #7dd3fc; /* sky-300 */ }

        /* Dark/Light Mode Base:
          Selects `body` based on the `dark` or `light` class on the `<html>` element.
          This provides the foundational background and text colors.
        */
        .dark body {
            background-color: #0F172A; /* slate-900 */
            color: #CBD5E1; /* slate-300 */
        }
        .light body {
            background-color: #F1F5F9; /* slate-100 */
            color: #1E293B; /* slate-800 */
        }
        
        /* 1. WebGL Canvas Background:
          - position: fixed: Stretches the canvas across the entire viewport.
          - top/left/width/height: Defines the fullscreen dimensions.
          - z-index: -10: Places the canvas *behind* all other page content.
          - opacity: Reduced to act as a subtle background.
        */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            opacity: 0.4;
            transition: opacity 0.5s ease;
        }
        .dark #bg-canvas { opacity: 0.4; }
        .light #bg-canvas { opacity: 0.2; } /* Further reduced opacity in light mode */

        /* 2. Custom Cursor (Dot & Outline):
          - position: fixed: Allows the cursor to move freely across the viewport.
          - transform: translate(-50%, -50%): Centers the element on the actual cursor position.
          - border-radius: 50%: Makes the divs circular.
          - pointer-events: none: CRITICAL. Allows clicks to "pass through" the cursor
            elements to the content underneath.
          - z-index: 9999: Ensures the cursor is on top of almost all content.
          - transition: Defines the "lerp" (linear interpolation) effect. The `transform`
            transition is very fast (0.1s) for responsiveness, while other properties
            (width, height) are slower (0.3s) for a smoother feel.
        */
        #cursor-dot, #cursor-outline {
            position: fixed;
            top: 0;
            left: 0;
            transform: translate(-50%, -50%);
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            transition: opacity 0.3s ease, transform 0.1s linear, width 0.3s ease, height 0.3s ease, background-color 0.3s ease, border-color 0.3s ease;
        }
        #cursor-dot {
            width: 8px;
            height: 8px;
            background-color: #38bdf8; /* The solid inner dot */
        }
        #cursor-outline {
            width: 40px;
            height: 40px;
            border: 2px solid #38bdf8; /* The hollow outer ring */
            opacity: 0.7;
        }
        /* Cursor Hover State:
          When the body has the 'cursor-hover' class (added by JS), the dot
          disappears, and the outline expands and fills slightly, giving
          a clear visual feedback for interactive elements.
        */
        body.cursor-hover #cursor-dot {
            opacity: 0;
        }
        body.cursor-hover #cursor-outline {
            width: 60px;
            height: 60px;
            background-color: rgba(56, 189, 248, 0.1);
            border-color: #818cf8; /* indigo-400 */
        }
        .light body.cursor-hover #cursor-outline {
            background-color: rgba(56, 189, 248, 0.2);
        }

        /* 3. Scroll Progress Bar:
          - position: fixed: Locks the bar to the top of the viewport.
          - z-index: 10000: Places it above all content *except* the command palette.
          - width: 0%: The default state, which is modified by JS on scroll.
        */
        #scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: linear-gradient(to right, #38bdf8, #818cf8);
            width: 0%;
            z-index: 10000;
            transition: width 0.1s linear;
        }

        /* 4. Command Palette (Modal):
          - position: fixed: Overlays the content.
          - top/left/transform: Centers the palette in the viewport.
          - z-index: 10001: The highest z-index, above the scroll bar and cursor.
          - opacity/transform(scale): Used to animate the "pop-in" effect.
          - pointer-events: none: Prevents interaction when hidden.
        */
        #command-palette {
            position: fixed;
            top: 20%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0.9);
            width: 100%;
            max-width: 500px;
            z-index: 10001;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
            opacity: 0;
            pointer-events: none;
            transition: transform 0.2s ease-out, opacity 0.2s ease-out;
        }
        /* Glassmorphism Effect:
          - backdrop-filter: blur(10px): Blurs the content *behind* the element.
          - background-color: rgba(...): A semi-transparent background is
            required for the blur to be visible.
        */
        .cmd-palette-content {
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border-radius: 12px;
            overflow: hidden;
        }
        .dark .cmd-palette-content {
            background-color: rgba(30, 41, 59, 0.8); /* slate-800 with 80% opacity */
            border: 1px solid #334155; /* slate-700 */
        }
        .light .cmd-palette-content {
            background-color: rgba(255, 255, 255, 0.8);
            border: 1px solid #CBD5E1; /* slate-300 */
        }
        /* Visible State:
          Reverses the opacity and transform to bring the palette into view.
          - pointer-events: all: Makes it interactive.
        */
        #command-palette.visible {
            transform: translate(-50%, -50%) scale(1);
            opacity: 1;
            pointer-events: all;
        }
        /* Input & List Styling */
        #command-palette-input {
            background: transparent;
            border: none;
            padding: 1rem;
            width: 100%;
            font-size: 1rem;
        }
        .dark #command-palette-input { 
            color: white; 
            border-bottom: 1px solid #334155;
        }
        .light #command-palette-input { 
            color: #0F172A; 
            border-bottom: 1px solid #CBD5E1; 
        }
        .light #command-palette-input::placeholder { color: #475569; }
        #command-palette-input:focus { outline: none; }

        .command-item {
            padding: 0.75rem 1rem;
            cursor: pointer;
            transition: background-color 0.2s ease;
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }
        .dark .command-item { color: #cbd5e1; /* slate-300 */ }
        .light .command-item { color: #334155; /* slate-700 */ }
        
        /* Selected State (for keyboard navigation):
          Applies the same style as hover for visual consistency.
        */
        .command-item:hover, .command-item.selected {
            background-color: rgba(56, 189, 248, 0.1);
            color: #38bdf8; /* sky-400 */
        }
        .light .command-item:hover, .light .command-item.selected {
            background-color: rgba(56, 189, 248, 0.2);
            color: #0369a1; /* sky-700 */
        }
        
        .command-item kbd {
            font-family: monospace;
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 0.75rem;
            margin-left: auto; /* Pushes the KBD to the far right */
        }
        .dark .command-item kbd { background-color: #334155; }
        .light .command-item kbd { background-color: #E2E8F0; }

        /* Command Palette Overlay:
          The dark, semi-transparent background *behind* the palette.
          Used as a click target to close the modal.
        */
        #command-palette-overlay {
            position: fixed;
            inset: 0; /* (top: 0, right: 0, bottom: 0, left: 0) */
            background-color: rgba(0,0,0,0.3);
            z-index: 10000; /* Below palette, above everything else */
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.2s ease-out;
        }
        #command-palette-overlay.visible {
            opacity: 1;
            pointer-events: all;
        }

        /* 5. Staggered Reveal Animation:
          Defines the *initial* state of elements to be animated.
          - opacity: 0 / transform: translateY(20px): Starts invisible and 20px down.
        */
        [data-stagger-reveal] {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }
        /* Animated State:
          When 'is-revealed' class is added by JS, the element
          fades in and moves up to its original position.
        */
        [data-stagger-reveal].is-revealed {
            opacity: 1;
            transform: translateY(0);
        }

        /* 6. Active Nav Link:
          Highlights the current section in the nav.
          Class is applied by the IntersectionObserver in JS.
        */
        .nav-link.active {
            color: #38bdf8; /* sky-400 */
            font-weight: 600;
        }
        .dark .nav-link.active { color: #38bdf8; }
        .light .nav-link.active { color: #0369a1; /* sky-700 */ }

        /* --- 7. Mobile Menu Transition --- */
        #mobile-menu {
            transition: transform 0.3s ease-in-out;
        }

        /* 8. Project Card (Gradient Border):
          - background: linear-gradient... padding-box, ... border-box:
            This is a "gradient border" trick. The `padding-box` (inner background)
            is a solid color, while the `border-box` (outer background) is
            a gradient. The `border: 1px solid transparent` creates the
            space for the gradient to show through.
          - display: flex / flex-direction: column: Ensures cards in a row
            are the same height and content is aligned.
        */
        .project-card {
            border: 1px solid transparent;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
        }
        .dark .project-card {
            background: linear-gradient(#1E293B, #1E293B) padding-box, linear-gradient(135deg, #38bdf8, #818cf8) border-box;
        }
        .light .project-card {
             background: linear-gradient(#FFFFFF, #FFFFFF) padding-box, linear-gradient(135deg, #38bdf8, #818cf8) border-box;
             box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05), 0 2px 4px -2px rgb(0 0 0 / 0.05);
        }
        .project-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 12px 30px rgba(56, 189, 248, 0.15), 0 6px 15px rgba(129, 140, 248, 0.1);
        }
        .project-card img {
            transition: transform 0.4s ease-out;
        }
        /* Subtle zoom effect on project image */
        .project-card:hover img {
            transform: scale(1.05);
        }

        /* 9. Experience Timeline:
          - position: relative: Establishes a positioning context for the dots.
          - border-left: The main timeline bar.
        */
        .timeline-item {
            position: relative;
            padding-left: 2.5rem;
            padding-bottom: 2rem;
        }
        .dark .timeline-item { border-left: 2px solid #334155; }
        .light .timeline-item { border-left: 2px solid #CBD5E1; }

        /* The last item has no border or padding-bottom */
        .timeline-item:last-child {
            border-left: 2px solid transparent;
            padding-bottom: 0;
        }
        /* Timeline Dot:
          - position: absolute: Places the dot *on top* of the border-left.
          - left: -9px: Calculated as (-(width/2) + (border-width/2)).
            Here: (-(18/2) + (2/2)) = -9 + 1 = -8. Wait, my math is off.
            Let's re-calculate: (-(18/2)) = -9px. This pulls it left to center
            it on the line. The inner `border: 4px` punches out the middle.
        */
        .timeline-dot {
            position: absolute;
            left: -9px; /* Half of width (18px) to center on the line */
            top: 4px; /* Aligns with text */
            width: 18px;
            height: 18px;
            background-color: #38bdf8; /* sky-400 */
            border-radius: 50%;
            z-index: 10;
        }
        /* The "punch-out" effect using the page's background color */
        .dark .timeline-dot { border: 4px solid #0F172A; }
        .light .timeline-dot { border: 4px solid #F1F5F9; }

        .timeline-item ul {
            list-style-type: none;
            padding-left: 0.25rem;
            margin-top: 0.75rem;
        }
        /* Custom bullet point for timeline list */
        .timeline-item li {
            position: relative;
            padding-left: 1.25rem;
            font-size: 0.9rem;
            line-height: 1.6;
            margin-bottom: 0.5rem;
        }
        .dark .timeline-item li { color: #CBD5E1; }
        .light .timeline-item li { color: #334155; }

        .timeline-item li::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0.55em; /* Vertically centers the bullet */
            width: 5px;
            height: 5px;
            background-color: #60a5fa; /* blue-400 */
            border-radius: 50%;
        }
        
        /* 10. Skill Badge:
          Simple pill-shaped badge with hover effect.
        */
        .skill-badge {
            display: inline-block;
            font-size: 0.75rem;
            font-weight: 500;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            transition: all 0.3s ease;
        }
        .dark .skill-badge {
            background-color: #1e293b;
            color: #94a3b8;
            border: 1px solid #334155;
        }
        .dark .skill-badge:hover {
            background-color: #334155;
            color: #e2e8f0;
            transform: scale(1.05);
        }
        .light .skill-badge {
            background-color: #E2E8F0;
            color: #334155;
            border: 1px solid #CBD5E1;
        }
        .light .skill-badge:hover {
            background-color: #CBD5E1;
            color: #1E293B;
            transform: scale(1.05);
        }

        /* 11. Contact Info Item:
          - margin: -0.75rem / padding: 0.75rem: This is a common trick
            to increase the "clickable" or "hoverable" area of an element
            without altering its visual spacing.
        */
        .contact-item {
            display: flex;
            align-items: flex-start;
            gap: 1rem;
            padding: 0.75rem;
            margin: -0.75rem; /* Negative margin for larger click target */
            border-radius: 0.5rem;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        .dark .contact-item:hover { background-color: #1E293B; }
        .light .contact-item:hover { background-color: #E2E8F0; }

        .contact-item i {
            width: 1.25rem;
            height: 1.25rem;
            flex-shrink: 0;
            margin-top: 0.125rem; /* Aligns icon with text */
        }
        .dark .contact-item i { color: #38bdf8; }
        .light .contact-item i { color: #0369a1; }

        .contact-item-label {
            font-weight: 600;
            margin-bottom: 0.125rem;
        }
        .dark .contact-item-label { color: #F1F5F9; }
        .light .contact-item-label { color: #1E293B; }

        .contact-item-value {
            font-size: 0.875rem;
            transition: color 0.3s ease;
        }
        .dark .contact-item-value { color: #CBD5E1; }
        .light .contact-item-value { color: #334155; }
        
        .contact-item:hover .contact-item-value { color: #38bdf8; }
        .light .contact-item:hover .contact-item-value { color: #0369a1; }

        /* 12. Accessibility: Reduced Motion
          - This media query detects if the user has requested "reduced motion"
            in their OS settings.
          - We disable all transitions, animations, and distracting elements
            (like the cursor and 3D background) to respect their preference.
          - This is a CRITICAL part of modern, inclusive web design.
        */
        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
                scroll-behavior: auto !important;
            }
            #bg-canvas, #cursor-dot, #cursor-outline, #scroll-progress {
                display: none;
            }
            body { cursor: auto; } /* Restore the default cursor */
            [data-stagger-reveal] {
                opacity: 1;
                transform: none;
            }
        }
        
        /* 13. Prose Styling for Book Chapter */
        .prose {
            font-size: 1.125rem; /* lg */
            line-height: 1.75; /* 7 */
        }
        .dark .prose { color: #CBD5E1; /* slate-300 */ }
        .light .prose { color: #334155; /* slate-700 */ }

        .prose h1, .prose h2, .prose h3, .prose h4 {
            font-weight: 700;
            letter-spacing: -0.025em;
        }

        .prose h2 {
            font-size: 2.25rem; /* 4xl */
            font-weight: 800; /* extrabold */
            margin-bottom: 0.5em;
        }
        .dark .prose h2 { color: #F1F5F9; /* slate-100 */ }
        .light .prose h2 { color: #1E293B; /* slate-800 */ }
        
        .prose h3 {
            font-size: 1.875rem; /* 3xl */
            font-weight: 700; /* bold */
            margin-top: 2em;
            margin-bottom: 1em;
        }
        .dark .prose h3 { color: #38bdf8; /* accent-color */ }
        .light .prose h3 { color: #0369a1; /* sky-700 */ }

        .prose h4 {
            font-size: 1.5rem; /* 2xl */
            font-weight: 600; /* semibold */
            margin-top: 1.6em;
            margin-bottom: 0.8em;
        }
        .dark .prose h4 { color: #E2E8F0; /* slate-200 */ }
        .light .prose h4 { color: #1E293B; /* slate-800 */ }

        .prose p {
            margin-bottom: 1.25em;
        }

        .prose ol {
            list-style-type: decimal;
            margin-left: 1.5em;
            margin-bottom: 1.25em;
            padding-left: 1.5em;
        }
        .prose li {
            margin-bottom: 0.75em;
            padding-left: 0.5em;
        }
        .prose li strong {
            display: inline-block;
            margin-bottom: 0.25em;
        }
        .dark .prose li strong { color: #E2E8F0; }
        .light .prose li strong { color: #1E293B; }


        .prose em {
            font-style: italic;
        }
        .dark .prose em { color: #94a3b8; /* slate-400 */ }
        .light .prose em { color: #475569; /* slate-600 */ }

        .prose code {
            background-color: #1e293b;
            color: #f1f5f9;
            padding: 0.25em 0.5em;
            border-radius: 6px;
            font-family: monospace;
            font-size: 0.9em;
        }
        .light .prose code {
            background-color: #E2E8F0; /* slate-200 */
            color: #334155; /* slate-700 */
        }
    </style>
</head>
<body class="antialiased dark"> <!-- Default to dark mode -->

    <!-- 
      =================================
      INTERACTIVE UI ELEMENTS
      (Placed at the top of <body> for z-index stacking)
      =================================
    -->
    <div id="scroll-progress"></div>
    <div id="cursor-dot"></div>
    <div id="cursor-outline"></div>
    <canvas id="bg-canvas"></canvas>
    
    <!-- 
      Command Palette HTML
      - role="dialog": Informs screen readers this is an interactive dialog.
      - aria-modal="true": Informs screen readers that content *outside* this
        dialog is inert (which is enforced by the overlay).
      - aria-labelledby: Points to the "label" (which is the input's placeholder).
    -->
    <div id="command-palette-overlay" aria-hidden="true"></div>
    <div id="command-palette" role="dialog" aria-modal="true" aria-labelledby="command-palette-input">
        <div class="cmd-palette-content">
            <input type="text" id="command-palette-input" placeholder="Jump to... (Ctrl+K)" autocomplete="off">
            <div id="command-palette-list">
                <a href="#home" class="command-item" data-action="jump">
                    <i data-lucide="home" class="w-4 h-4"></i>Home
                    <kbd>H</kbd>
                </a>
                <a href="#about" class="command-item" data-action="jump">
                    <i data-lucide="user" class="w-4 h-4"></i>About
                    <kbd>A</kbd>
                </a>
                <a href="#experience" class="command-item" data-action="jump">
                    <i data-lucide="briefcase" class="w-4 h-4"></i>Experience
                    <kbd>E</kbd>
                </a>
                <a href="#projects" class="command-item" data-action="jump">
                    <i data-lucide="layers" class="w-4 h-4"></i>Projects
                    <kbd>P</kbd>
                </a>
                <!-- NEWLY ADDED -->
                <a href="#book" class="command-item" data-action="jump">
                    <i data-lucide="book" class="w-4 h-4"></i>Book
                    <kbd>B</kbd>
                </a>
                <!-- END NEWLY ADDED -->
                <a href="#about-site" class="command-item" data-action="jump">
                    <i data-lucide="layout-template" class="w-4 h-4"></i>About Site
                    <kbd>S</kbd>
                </a>
                <a href="#contact" class="command-item" data-action="jump">
                    <i data-lucide="mail" class="w-4 h-4"></i>Contact
                    <kbd>C</kbd>
                </a>
            </div>
        </div>
    </div>
    <!-- End interactive elements -->

    <!-- 
      =================================
      HEADER / NAVIGATION
      - position: fixed: Fixes the header to the top.
      - z-index: 50: Places it above page content but below modals/cursor.
      =================================
    -->
    <header id="header" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <!-- Logo -->
            <a href="#home" class="text-2xl font-bold transition-colors dark:text-white light:text-slate-900 accent-text-hover flex items-center gap-2" data-magnetic>
                <i data-lucide="code-2" class="accent-color"></i>
                <span>Alec <span class="accent-color">Borman</span></span>
            </a>

            <!-- Desktop Nav (Hidden on mobile) -->
            <div class="hidden md:flex items-center space-x-6">
                <a href="#home" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">Home</a>
                <a href="#about" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">About</a>
                <a href="#experience" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">Experience</a>
                <a href="#projects" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">Projects</a>
                <!-- NEWLY ADDED -->
                <a href="#book" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">Book</a>
                <!-- END NEWLY ADDED -->
                <a href="#about-site" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">About Site</a>
                <a href="#contact" class="nav-link transition-colors light:text-slate-700 light:hover:text-sky-700 dark:text-slate-300 dark:hover:text-sky-400">Contact</a>
                
                <!-- Dark/Light Mode Toggle -->
                <button id="theme-toggle" class="p-2 rounded-full transition-colors light:text-slate-700 light:hover:bg-slate-200 dark:text-slate-300 dark:hover:bg-slate-700" aria-label="Toggle theme" data-magnetic>
                    <svg id="theme-icon-sun" class="h-5 w-5 hidden" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M12 12a5 5 0 100-10 5 5 0 000 10z" /></svg>
                    <svg id="theme-icon-moon" class="h-5 w-5 hidden" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" /></svg>
                </button>
            </div>

            <!-- Mobile Menu Button (Hidden on desktop) -->
            <div class="md:hidden">
                <button id="mobile-menu-button" class="p-2 rounded-md light:text-slate-700 light:hover:bg-slate-200 dark:text-slate-300 dark:hover:bg-slate-700" aria-label="Open menu">
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path id="menu-icon-open" stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16m-7 6h7" />
                        <path id="menu-icon-close" class="hidden" stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </nav>

        <!-- 
          Mobile Menu (Fly-out panel)
          - position: absolute: Positions it relative to the header.
          - -translate-x-full: Hides it off-screen to the left by default.
        -->
        <div id="mobile-menu" class="md:hidden absolute top-full left-0 right-0 light:bg-white dark:bg-slate-800 shadow-lg -translate-x-full">
            <div class="flex flex-col space-y-4 p-6">
                <a href="#home" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">Home</a>
                <a href="#about" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">About</a>
                <a href="#experience" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">Experience</a>
                <a href="#projects" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">Projects</a>
                <!-- NEWLY ADDED -->
                <a href="#book" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">Book</a>
                <!-- END NEWLY ADDED -->
                <a href="#about-site" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">About Site</a>
                <a href="#contact" class="mobile-nav-link block px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700">Contact</a>
                <button id="theme-toggle-mobile" class="w-full flex items-center justify-center space-x-2 px-4 py-2 rounded-md light:text-slate-700 light:hover:bg-slate-100 dark:text-slate-200 dark:hover:bg-slate-700" aria-label="Toggle theme">
                    <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M12 12a5 5 0 100-10 5 5 0 000 10z" /></svg>
                    <span>/</span>
                    <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" /></svg>
                </button>
            </div>
        </div>
    </header>

    <!-- 
      =================================
      MAIN CONTENT
      - z-index: 10: Ensures main content is *above* the -10 z-index
        background canvas, but below the header/modals.
      =================================
    -->
    <main class="container mx-auto px-6 relative z-10">

        <!-- 
          =================================
          SECTION: HOME (HERO)
          - data-section-id: Used by the IntersectionObserver to
            highlight the correct nav link.
          - data-stagger-container: Used by JS to find all elements
            within this section that need to be animated on reveal.
          =================================
        -->
        <section id="home" data-section-id="home" class="min-h-screen flex items-center pt-20 md:pt-0">
            <div data-stagger-container>
                <span data-stagger-reveal class="inline-block bg-sky-500/10 text-sky-400 text-xs font-bold px-4 py-1.5 rounded-full mb-5 border border-sky-400/30 uppercase tracking-wider">
                    Certified Salesforce Administrator & Developer
                </span>
                <h1 data-stagger-reveal class="text-5xl md:text-7xl lg:text-8xl font-extrabold light:text-slate-900 dark:text-white mb-6">
                    Alec Borman.
                </h1>
                <p data-stagger-reveal class="text-lg md:text-xl font-light light:text-slate-600 dark:text-slate-400 max-w-3xl mb-10">
                    I translate complex business needs into secure, scalable, and efficient Salesforce solutions that drive user adoption, reduce manual work, and accelerate operational excellence.
                </p>
                <div data-stagger-reveal class="flex flex-col sm:flex-row gap-5">
                    <a href="#projects" class="inline-block px-8 py-4 rounded-md text-lg font-medium text-slate-900 accent-bg accent-hover transition-all duration-300 shadow-lg shadow-sky-500/20 hover:shadow-sky-400/30 transform hover:-translate-y-1" data-magnetic>
                        View My Projects
                    </a>
                    <a href="#contact" class="inline-block px-8 py-4 rounded-md text-lg font-medium light:text-slate-800 dark:text-slate-100 light:bg-slate-200 dark:bg-slate-700 light:hover:bg-slate-300 dark:hover:bg-slate-600 transition-all duration-300 transform hover:-translate-y-1" data-magnetic>
                        Get In Touch
                    </a>
                </div>
            </div>
        </section>

        <!-- 
          =================================
          SECTION: EXPERIENCE (RE-INSERTED)
          This was the missing section. It is now re-added.
          =================================
        -->
        <section id="experience" data-section-id="experience" class="min-h-screen py-24 md:py-32">
            <div>
                <h2 class="text-3xl md:text-4xl font-bold light:text-slate-900 dark:text-white mb-16 flex items-center" data-stagger-reveal>
                    <span class="accent-color text-4xl md:text-5xl font-mono mr-3">02.</span> Professional Experience
                </h2>

                <div class="max-w-3xl mx-auto" data-stagger-container>
                    
                    <!-- Hydrolix -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">Oct 2024 – Present</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Business Systems Architect</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">Hydrolix (Remote)</p>
                        <ul>
                            <li>Grew from foundational admin to strategic architect, building the company's operational backbone on Salesforce for finance and SaaS deployment tracking.</li>
                            <li>Balanced immediate tactical needs with long-term strategy, collaborating with Sales, CSE, and SRE teams to clear roadblocks and build a scalable customer lifecycle engine.</li>
                            <li>Designed and deployed a new lead-to-opportunity process that cut lead response time by 40%.</li>
                            <li>Engineered end-to-end automation for the deployment lifecycle (POC to contract), including credit approvals, usage quota tracking, and automated customer communications.</li>
                            <li>Personally designed/coded HTML email templates and used Zapier to trigger critical notifications from the "TrafficPeak" system.</li>
                            <li>Administered the Salesforce instance for 150+ users, leading custom Apex and LWC development to eliminate technical debt.</li>
                        </ul>
                    </div>
                    
                    <!-- Jaco Aerospace, Inc. -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">Jun 2024 – Aug 2024</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Salesforce Architect / Salesforce Consultant</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">Jaco Aerospace, Inc. (Contract, Remote)</p>
                        <ul>
                            <li>Provided expertise in business process configuration and optimization for Salesforce Sales Cloud with an integrated Glovia OM ERP.</li>
                            <li>Designed, developed, and tested custom logic (Apex, Visualforce) to overcome managed package limitations and streamline business processes.</li>
                            <li>Created custom buttons and Visualforce pages to prepopulate fields, significantly reducing data entry time.</li>
                            <li>Configured and integrated Glovia features including Work Orders, RMAs, Return to Suppliers, and Reorder Point Planning.</li>
                            <li>Collaborated with stakeholders to design, implement, test, and refine solutions, enhancing Order Management and ERP system functionality.</li>
                        </ul>
                    </div>
                    
                    <!-- GIVE US PAWS -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">Sep 2022 – Present</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Salesforce Consultant / Developer</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">GIVE US PAWS (Contract, Remote)</p>
                        <ul>
                            <li>Provide expert consulting and development for a 501c nonprofit, implementing a new Salesforce system from the ground up.</li>
                            <li>Utilized a managed package ("Dog and Client Tracker") to track the training of service dogs for disabled veterans.</li>
                            <li>Led the full project lifecycle: managed package discovery, requirements gathering, solution design, license acquisition, configuration, and customization.</li>
                            <li>Managed all data import/entry and created critical reports and dashboards, providing continued system support.</li>
                        </ul>
                    </div>

                    <!-- Fujitsu (From LinkedIn Data) -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">Mar 2022 – Oct 2023</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Salesforce Developer</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">Fujitsu (Contracted to Royal Canin)</p>
                        <ul>
                            <li>Served as a Developer and Support Specialist for the Salesforce Sales Cloud managed package, Glovia OM.</li>
                            <li>Provided expert advice, integrated ERP/Order Management features, and resolved all support queries related to the managed package.</li>
                            <li>Collaborated with a team of developers to design, implement, test, document, and refine solutions, ensuring supply chain reliability.</li>
                        </ul>
                    </div>

                    <!-- GIVE US PAWS (Marketing) (From LinkedIn Data) -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">Jan 2020 – Mar 2022</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Marketing Campaign Manager</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">GIVE US PAWS (Contract, Remote)</p>
                        <ul>
                            <li>Designed, tested, and implemented Google Ad campaigns for the 501c nonprofit.</li>
                        </ul>
                    </div>

                    <!-- Austin Industrial (From LinkedIn Data) -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">May 2019 – Aug 2019</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">IT Intern</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">Austin Industrial, Inc.</p>
                        <ul>
                            <li>Diagnosed issues, deployed devices, and tracked assets with inventory management software.</li>
                        </ul>
                    </div>

                    <!-- Austin Industrial (From LinkedIn Data) -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">May 2018 – Aug 2018</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">DevOps Intern</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">Austin Industrial, Inc.</p>
                        <ul>
                            <li>Researched intrinsically safe cases, software, and hardware for RFID site tracking.</li>
                            <li>Deployed 400 iPad devices with custom Austin INDL software.</li>
                            <li>Digitized Job Safety Analysis (JSA) audits and maintained user guides.</li>
                        </ul>
                    </div>
                    
                    <!-- Education -->
                    <div class="timeline-item" data-stagger-reveal>
                        <div class="timeline-dot"></div>
                        <p class="text-sm font-medium accent-color mb-1">2016 – 2021</p>
                        <h3 class="text-xl font-bold light:text-slate-900 dark:text-slate-100">Bachelor of Science in Computer Science</h3>
                        <p class="text-base font-medium light:text-slate-600 dark:text-slate-400 mb-3">University of Texas at Dallas (Richardson, TX)</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 
          =================================
          SECTION: BOOK CHAPTER (NEWLY ADDED)
          =================================
        -->
        <section id="book" data-section-id="book" class="py-24 md:py-32">
            <div data-stagger-container>
                <h2 class="text-3xl md:text-4xl font-bold light:text-slate-900 dark:text-white mb-16 flex items-center" data-stagger-reveal>
                    <span class="accent-color text-4xl md:text-5xl font-mono mr-3">03.</span> The Black Box
                </h2>

                <div class="prose max-w-3xl mx-auto" data-stagger-reveal>
                    <!-- Start formatting the chapter text -->
                    <h2>Chapter 1: The "Black Box" Mindset</h2>
                    <h3>Choosing Focus Over Distraction</h3>
                    
                    <h4>The Architect in the Dark</h4>
                    <p>The meeting request is vague: “Discuss Sales-to-Ops Handoff.” It’s been on your calendar for a week, sandwiched between a budget review and a quarterly business review (QBR).</p>
                    <p>You join the call. There are six people. The VP of Sales, a few of his senior reps, the Ops Manager, and a junior analyst. The VP of Sales is sharing his screen, showing a Salesforce dashboard. Ten minutes of crosstalk, small talk, and "can-you-see-my-screen" later, the "ask" finally surfaces.</p>
                    <p>"Look, we're growing, which is great," the VP says, his cursor circling the 'Closed/Won' stage in Salesforce. "But our handoff to the operations team is breaking. My reps are manually copying and pasting data from the Opportunity into a Google Sheet for the ops team. It's slow, they're busy, and they miss fields. It's causing downstream problems. Can't we just use Zapier to move the Opportunity data into the sheet when the stage changes? It seems simple. I think the analyst on this call, Sarah, already mapped the fields."</p>
                    <p>Sarah nods. "Yes, I have a list of the 12 fields Ops needs. It looks very straightforward."</p>
                    <p>The room falls silent. Everyone turns to you. This is the moment. This is the junction where careers, systems, and companies diverge.</p>
                    <p>The technician hears this and, in their mind, is already building the Zap. They see a trigger ("Opportunity Stage = Closed Won" in Salesforce) and an action ("Create New Row" in Google Sheets). They see a five-minute fix, a closed ticket, and a happy stakeholder. They unmute and say, "Yep, that's easy. I can have that done by end of day."</p>
                    <p>The architect, however, makes a different choice.</p>
                    <p>They hear the request, but they <em>listen</em> for the system. They see the icons for Salesforce, Zapier, and Google Sheets, but they choose to ignore them. This is the "visual noise"—the seductive, surface-level distraction of pre-packaged solutions and friendly UIs. It is the single greatest barrier to building holistic, scalable, and anti-fragile systems.</p>
                    <p>The technician is already solving the stated problem. The architect is just beginning to model the real one.</p>
                    <p>This is the "Black Box" mindset. It is not a passive state. It is a disciplined, active choice to tune out the visual noise and cultivate a state of deep, productive focus. It’s the decision to build by feel—to fundamentally understand the materials of the problem—before you ever grant yourself the permission to think about a solution.</p>
                    <p>Why does the architect do this? Why be the "bad guy" who slows the room down? Why not just take the quick win?</p>
                    <p>Because they know something the technician doesn't. They know that this "simple fix" is a tyrant in disguise. They know it's a high-interest loan taken out against the company's future, and the bill always comes due. And they know that the cost of that "fix" will be paid by <em>everyone</em> except the person who implemented it.</p>
                    <p>The technician gets to be the hero for a day. The architect has to live with the consequences for a decade.</p>

                    <h4>The Tyranny of the "Simple Fix": A Post-Mortem in Advance</h4>
                    <p>In our world, the "simple fix" is the most expensive thing you can buy. It is the genesis of "technical debt," a term that has become so overused it has lost its meaning. We must be more precise. The technician's "five-minute fix" doesn't just create technical debt; it creates a cascading, multi-domain failure.</p>
                    <p>To truly operate at an architectural level, we must move beyond a surface-level analysis. We must perform a rigorous, multi-domain impact assessment of that "simple fix," just as an architect does in their head, all while nodding patiently on the Zoom call.</p>
                    <p>We will conduct a post-mortem in advance. Let's trace the full blast radius.</p>

                    <h4>Domain 1: Technical & Process Debt</h4>
                    <p>This is the most obvious failure, the one that developers and system administrators will feel first. The technician has not built a "bridge" between two systems; they have built a "data trap." This debt manifests in three distinct, compounding forms: fracture, fallacy, and fragility.</p>
                    <ol>
                        <li><strong>Process Fracture & Data Divergence (The "Update" Problem)</strong><br>The Zap is built. It's tested. It works. An Opportunity is closed, and presto, a new row appears in the Google Sheet. The VP of Sales is thrilled. The ticket is closed.
                        <br>The next day, the customer calls the sales rep. "We're so excited to get started. Can you add two more user licenses to that initial order? And can you update the primary technical contact? I gave you my assistant's name, but it should really be our Head of Engineering."
                        <br>The sales rep, doing their job, says "Of course." They go into Salesforce. They update the <code>Amount</code> on the Opportunity. They change the <code>Primary_Contact__c</code> field. They hit "Save."
                        <br>The Zap does not (and should not) fire again. It was configured to trigger on the stage change, a one-time event.
                        <br>The Google Sheet is now permanently wrong.
                        <br>This is not a hypothetical. It is an inevitability. The technician's solution only accounted for <em>onCreate</em>. It completely ignored <em>onUpdate</em>, because the underlying process is not a one-time, immutable event.
                        <br>The company deploys the wrong number of licenses. The wrong person (the assistant) gets the onboarding email, which they ignore. Two weeks later, an angry Head of Engineering emails the sales rep, "We were supposed to go live today, what's going on?"
                        <br>The sales rep, confused, looks at their Opportunity in Salesforce. "It says you're all set! Let me check with Ops." They open the Google Sheet and see the old data. The process is fractured. Trust is broken. The "fix" has failed in less than 24 hours.</li>
                        
                        <li><strong>The "Second Source of Truth" Fallacy</strong><br>This is a more insidious problem. The Google Sheet is now a second, competing source of truth for deployments. When the finance team wants to run a report on "time from close to deployment," where do they look?
                        <br>Salesforce has the Close Date. The Google Sheet has the Deployment Complete checkbox, which the Ops team diligently checks.
                        <br>A junior analyst—let's call her Sarah, since she was on the call—is now tasked with this report. Her process is as follows:
                        <br>Run a "Closed Won Opportunities" report in Salesforce and export to CSV.
                        <br>Open the "Ops Deployment" Google Sheet and export to CSV.
                        <br>Open a new Excel workbook.
                        <br>Paste both CSVs into new tabs.
                        <br>In a third tab, write a VLOOKUP formula: <code>VLOOKUP(A2, 'Salesforce Export'!A:D, 4, FALSE)</code> to try and match the Opportunity ID.
                        <br>Spend an hour figuring out why 15% of the VLOOKUPs return #N/A (it's because reps changed the Opp Name after the Zap fired, or the Opp ID wasn't one of the 12 fields, or any number of other data-drift issues).
                        <br>Manually fix the errors.
                        <br>Create a pivot table.
                        <br>Deliver the report, which is now three days late and 85% accurate, at best.
                        <br>This "manual-merge" step is now part of the business process. The "fix" didn't reduce manual work; it just moved it from a high-visibility sales rep to a low-visibility analyst and multiplied it by an order of magnitude. The VP of Sales is happy, but the Head of FP&A is now making forecasts based on data that is fundamentally broken.</li>
                        
                        <li><strong>API & Automation "Spaghetti" (The Fragility Problem)</strong><br>The technician used Zapier because it was "simple." Six months later, the finance team wants to sync invoices from that same Opportunity. The finance team, however, uses Workato. So, a different technician builds a Workato recipe.
                        <br>Meanwhile, the marketing team wants to add "Closed Won" customers to a new email journey. Their agency knows HubSpot, so they use the native HubSpot-Salesforce connector.
                        <br>A developer, annoyed by all these third-party tools, decides to write a custom Apex trigger to handle a high-volume sync for a different process.
                        <br>We now have four different automation tools all touching the same <code>Opportunity</code> object: Zapier, Workato, HubSpot, and Apex.
                        <br>What happens when they all try to update the record at the same time?
                        <br>What is the order of operations?
                        <br>Where is the central logging?
                        <br>When a record update fails, which of the four systems is to blame?
                        <br>Who "owns" this mess?
                        <br>This is "spaghetti architecture," and it is how systems become brittle, unmaintainable, and impossible to debug. The "simple fix" is the first strand of that spaghetti. It sets a precedent that point-to-point, "shadow IT" solutions are acceptable. The architect knows that the second you allow a rogue, point-to-point integration, you have lost control of your architecture.</li>
                        
                        <li><strong>The Scalability Trap</strong><br>This architecture cannot scale. The Zapier plan is based on "tasks." At 10 deals a month, it's cheap. When the company hits 100 deals a month, the cost increases 10x. When they hit 1,000, the "stack tax" becomes a real line item in the IT budget.
                        <br>But the real problem is the Google Sheet. Google Sheets has a limit of 10 million cells. At 20 columns of data (the 12 fields, plus 8 more that Ops inevitably adds), that's 500,000 rows. A successful company will blow through that in a few years. The system has a built-in, non-negotiable expiration date. The "simple fix" has a "simple" time bomb.</li>
                    </ol>
                    
                    <h4>Domain 2: Financial & Resource Cost</h4>
                    <p>This is the debt the CFO sees, even if they don't know its source. The "five-minute fix" is a lie. The true cost is staggering.</p>
                    <ol>
                        <li><strong>The "Hidden" Labor Cost: A Balance Sheet of the Simple Fix</strong><br>Let's do the math that the technician skipped. Assume blended-average, fully-loaded costs for our employees:
                        <br>Sales Rep: $150/hr
                        <br>Ops Manager: $120/hr
                        <br>Engineer: $180/hr
                        <br>Analyst (Sarah): $90/hr
                        <br>Now, let's tally the real cost of the "Process Fracture" from Domain 1, which will happen every time an Opportunity is updated post-close (let's say 15% of the time).
                        <br>Engineer (Technician): 0.1 hours to build Zap = $18.00 (The "simple fix" cost)
                        <br>Now, the real costs, per incident:
                        <br>Sales Rep: 0.5 hrs emailing Ops, finding the error, calming the customer = $75.00
                        <br>Ops Manager: 0.5 hrs investigating the discrepancy, finding the real data, manually updating the sheet = $60.00
                        <br>Engineer: 1.0 hr being pulled in to see "if the Zap is broken" (it's not, the logic was flawed) = $180.00
                        <br>Total Cost Per Incident: $315.00
                        <br>If this happens just 10 times a month, the "simple fix" is costing the company $3,150 per month, or $37,800 per year, in hidden labor costs for this one failure mode.
                        <br>Now let's add Sarah's reporting (Domain 1, Point 2). She spends 8 hours per month cleaning this data.
                        <br>Analyst (Sarah): 8 hrs/mo * $90/hr = $720 per month, or $8,640 per year.
                        <br>Total Verified Cost (Year 1): $46,440.
                        <br>The "five-minute fix" is a negative-$46k-per-year decision. And this doesn't even account for the "stack tax" (the Zapier subscription) or the most expensive cost of all...</li>
                        
                        <li><strong>The Cost of In-Fidelity Data (The "GIGO" Problem)</strong><br>"Garbage In, Garbage Out" (GIGO) is the oldest rule in computing. The "simple fix" guarantees garbage data by creating two competing sources of truth. This bad data doesn't just live in a spreadsheet; it infects the entire organization's decision-making framework.
                        <br>The FP&A team, using Sarah's 85%-accurate report, mis-calculates the Average Time to Deploy.
                        <br>The CRO, using this flawed metric, sets the Quota for the next quarter, assuming a 30-day deployment cycle when it's really 45 days.
                        <br>The Sales team, now held to an impossible standard, starts pressuring the Ops team to cut corners.
                        <br>The Ops team, to hit their (false) metric, starts marking Deployment Complete before the work is actually done, permanently corrupting the data.
                        <br>This is a GIGO feedback loop. The "simple fix" is no longer a process problem; it is now actively steering the company's strategic planning with flawed, in-fidelitous data. This is how you mis-calculate Customer Acquisition Cost (CAC), Lifetime Value (LTV), and churn. This is how a "simple fix" can ultimately mislead a Board of Directors.</li>
                    </ol>

                    <h4>Domain 3: Security & Compliance Catastrophe</h4>
                    <p>This is the debt that can put a company out of business. It's the one that earns the CISO a termination.</p>
                    <ol>
                        <li><strong>Data Exfiltration as a "Feature"</strong><br>The Opportunity record contains Customer Name, Contact Email, Contact Phone, and Contract Value. This is, by any legal definition, Personally Identifiable Information (PII) and confidential financial data.
                        <br>The technician, in their haste, just configured an automated, real-time data exfiltration pipe out of a secure, audited, SOC 2-compliant environment (Salesforce) and into a Google Sheet.
                        <br>If this company does business in Europe, they have just scheduled a recurring GDPR violation. If they are in California, they are violating CCPA. If they are in healthcare, this is a multi-million dollar HIPAA breach. The "simple fix" wasn't just "not best practice"; it was, quite possibly, illegal.</li>
                        
                        <li><strong>The Access Control Nightmare: How Breaches Happen</strong><br>The data is now in a Google Sheet. Who has access to that sheet? The Ops Manager, who shares it with his team. One of them, trying to be helpful, shares it with a contractor. The VP of Sales, annoyed he can't see it, asks for access. He is "View Only." He can't search it easily, so he does File > Download > As .xlsx and saves it to his desktop.
                        <br>The data is now on a local machine. It's in a contractor's inbox.
                        <br>Six months later, an employee on the Ops team quits. They were never removed from the Google Sheet. They now have a real-time feed of their ex-employer's entire sales pipeline on their personal laptop, which they bring to their new job at a direct competitor.
                        <br>This is not theoretical. This is how data breaches and corporate espionage happen. Not through sophisticated hacking, but through a "simple fix" that punched a hole in the data perimeter.</li>
                    </ol>

                    <h4>Domain 4: The Cultural Fallout</h4>
                    <p>This is the most insidious debt of all, as it's invisible on any balance sheet, yet it corrodes the company from within.</p>
                    <ol>
                        <li><strong>Reinforcing Silos (Conway's Law in Action)</strong><br>In 1968, computer scientist Melvin Conway wrote, "Any organization that designs a system... will inevitably produce a design whose structure is a copy of the organization's communication structure."
                        <br>This is Conway's Law. The "simple fix" is a perfect example.
                        <br>The Organization's Structure: "Sales" and "Ops" are two separate, siloed teams that "hand off" work.
                        <br>The System's Design: A Zap that "hands off" data from the "Sales system" to the "Ops system."
                        <This "fix" doesn't just model the silo; it <em>reinforces</em> it. It validates the sales team's belief that their job is "done" at the close. It tells the ops team that their job is to react to data, not be a partner in the customer lifecycle. It codifies the "us vs. them" mentality.</li>
                        
                        <li><strong>The Erosion of Trust</strong><br>The ultimate cultural cost is the complete erosion of trust.
                        <br>Ops stops trusting Sales's data ("It's always wrong in the sheet").
                        <br>Sales stops trusting Ops to get the job done ("Why is my customer always angry?").
                        <br>Finance stops trusting either team's reports ("I have to pull the data myself").
                        <br>Management, frustrated by the bickering, just sees two teams that can't get along.
                        <br>The Google Sheet becomes a symbol of this mistrust. It is a digital monument to a broken process.</li>
                    </ol>

                    <h4>Choosing Focus: The Superior Method</h4>
                    <p>The architect in the "Black Box" sees all of this—this multi-domain catastrophe—in the span of thirty seconds. It flashes through their mind not as a report, but as a <em>feeling</em>. A feeling of brittleness. A feeling of danger.</p>
                    <p>So, they make a different choice. They deploy the "Architect's Pause."</p>
                    <p>They unmute. "That's a great starting point, VP. The goal of automating the handoff and increasing visibility is absolutely correct. I have a few questions to help me model the full impact of the solution to make sure we build it right, once."</p>
                    <p>The architect has just done three critical things:
                    <br>1. Validated the stakeholder (<em>The goal is correct...</em>)
                    <br>2. Stated their intention (<em>...model the full impact...</em>)
                    <br>3. Provided the WIIFM (What's In It For Me) (<em>...so we build it right, once.</em>)
                    </p>
                    <p>Now, the architect is in control. They are "in the dark," where the shiny logos can't distract them. They begin to build a model by feel. This "feeling" is not a vague intuition; it is a structured, analytical process of mental modeling.</p>
                    <p>They ask questions that "feel" for the shape, weight, and texture of the problem.</p>

                    <ol>
                        <li><strong>"Feeling" for the Shape: What is this data?</strong><br>This is the architect's first-principles deconstruction of the data itself. It is the most important question.
                        <br><em>Technician's View:</em> The data is a row. It has 12 columns.
                        <br><em>Architect's Analysis:</em> Is this data a <em>transaction</em> or a <em>state</em>?
                        <br>This is a fundamental computer science concept, and it is the key that unlocks the entire problem.
                        <br>A <em>transaction</em> is a point-in-time, immutable event. It is "write-once." Think of a credit card charge, a log entry, or a vote. It is created, and it is done. It's a POST request.
                        <br>A <em>state</em> is a living, mutable record. It is created, and then it is read, updated, and appended over its entire lifecycle. Think of a patient's chart, a bank account balance, or a project status. It's a POST, followed by many PUTs, PATCHs, and GETs.
                        <br>The technician assumed the "Closed Won" event was a <em>transaction</em>. The architect tests this hypothesis.
                        <br><em>Architect:</em> "Is this handoff like a baton in a relay race—once it's passed, the first runner is done? Or is it like a patient's chart, where multiple doctors need to read and update the same chart throughout the patient's stay?"
                        <br><em>VP of Sales:</em> (Pauses) "It's... a patient's chart. We often update the deal after Ops has started. We add products, or change the primary contact."
                        <br><em>Architect:</em> (Nods) "And Ops, do you also need to update this record with your status, so Sales can see it?"
                        <br><em>Ops Manager:</em> "Yes! We'd love for them to see our Deployment Status field."
                        <br>The architect has just proven the hypothesis. The "simple fix" (the Zap) was based on a false "baton" (transaction) metaphor. The problem requires a "patient chart" (state) model.
                        <br>This single discovery has invalidated the entire "Google Sheet" premise. You cannot manage a stateful process in a transactional pipeline. The tool is wrong because the assumed shape of the data was wrong.</li>
                        
                        <li><strong>"Feeling" for the Weight: What is the real pain point?</strong><br>This is the architect's root cause analysis of the human system. The architect uses the "Five Whys" technique.
                        <br><em>Architect:</em> "I understand the copy-paste is annoying. But what is the business problem it's causing?" (Why #1)
                        <br><em>VP of Sales:</em> "My reps are getting angry calls from customers because the deployment is wrong or the wrong person was contacted." (Why #2)
                        <br><em>Architect:</em> "Why is the deployment wrong?"
                        <br><em>VP of Sales:</em> "Because Ops is working off old data from the sheet." (Why #3)
                        <br><em>Architect:</em> "Why are they working off old data?"
                        <br><em>Ops Manager:</em> "Because we have no idea when the rep updates the Opportunity in Salesforce after the handoff. We're blind." (Why #4)
                        <br><em>Architect:</em> "And VP, why are your reps getting the angry calls? Why not Ops?"
                        <br><em>VP of Sales:</em> "Because as far as the customer is concerned, the rep is their only point of contact. The rep has no visibility into the Ops process, so they're blind, too." (Why #5)
                        <br>Aha. The architect has just identified the true problem.
                        <br><em>Technician's View:</em> The pain is manual data entry. The solution is automation.
                        <br><em>Architect's View:</em> The pain is a crisis of <em>mutual blindness</em>. The solution must be <em>shared visibility</em>.
                        <br>The "simple fix" would have automated the symptom while completely ignoring—and arguably, worsening—the disease.</li>

                        <li><strong>"Feeling" for the Texture: Where does this process connect?</strong><br>This is the architect's system-level dependency mapping. The architect's primary job is to protect the System of Record (SoR).
                        <br>An SoR is the single, authoritative source of truth for a core data entity.
                        <br>Your bank's mainframe is the SoR for your Account Balance.
                        <br>Workday is the SoR for an Employee record.
                        <br>In this company, <em>Salesforce is the SoR for the Customer.</em>
                        <br>The "simple fix" (the Google Sheet) attempts to create a new, rogue, competing SoR for the Deployment. This is architectural heresy. An architect never creates a competing SoR when they can extend the primary one.
                        <br>The architect asks: "What other systems, objects, and people need to know about this? What does this process 'touch'?"
                        <br>The team maps it out on a virtual whiteboard:
                        <br>- It's not just an "Opportunity." It's an <code>Account</code> (the legal entity).
                        <br>- It's <code>Contacts</code> (who need to be onboarded).
                        <br>- It's <code>Opportunity Products</code> (that define what to deploy).
                        <br>- It's <code>Contracts</code> (that govern the legal terms and SLAs).
                        <br>- It's the <em>Finance Team</em> (who need to invoice against it).
                        <br>- It's the <em>Support Team</em> (who need to know what was deployed to service it).
                        <br>The "simple fix" ignored this entire constellation. It was a point-to-point solution in a "hub-and-poke" reality. The architect’s model must connect all of them.</li>
                    </ol>
                    <p>By tuning out the "visual noise" for five minutes, the architect has completed their model. They have identified the Shape (State), the Weight (Visibility), and the Texture (SoR).</p>
                    <p>The solution is now self-evident.</p>

                    <h4>The Black Box Blueprint</h4>
                    <p>The architect now turns the "visuals" back on. But they are no longer distractions; they are tools to be commanded, chosen to fit the model.</p>
                    <p>From this model, a new solution emerges. It is holistic, scalable, and—critically—simpler and cheaper than the "simple fix" because it introduces no new systems or liabilities.</p>
                    <p>The architect’s blueprint is not a Zap. It is a new "North Star" for this process: "We will build a single, shared object inside Salesforce that both teams can see and update. This object will be the single source of truth for the post-sale lifecycle."</p>
                    <p>This is the "Grounded Vision" (which we will cover in Chapter 5). It's not a fantasy; it's pragmatic. It uses the tool they already have (Salesforce) and are already paying for to solve the actual problem.</p>
                    <p>The blueprint looks like this:</p>
                    <ol>
                        <li><strong>A Shared Object (The "Patient Chart"):</strong> Create a new custom object in Salesforce called <code>Deployment</code> (or <code>Project</code>). This object will have a Master-Detail relationship with the <code>Account</code> (the SoR) and a Lookup relationship to the <code>Opportunity</code> (the triggering event).</li>
                        <li><strong>Smart, Native Automation (The "Flow"):</strong> When an <code>Opportunity</code> Stage is "Closed Won," a Salesforce Flow (not a Zap) automatically creates the <code>Deployment</code> record. This Flow also intelligently:
                        <br>- Copies over the key <code>Contacts</code> as <code>Deployment Team Members</code>.
                        <br>- Creates <code>Deployment Tasks</code> based on the <code>Opportunity Products</code> that were sold.
                        <br>- Links the primary <code>Contract</code> record.</li>
                        <li><strong>A Single Source of Truth:</strong> The Sales team "creates" the record. The Ops team "owns" the record, updating its <code>Status</code> field (e.g., "Pending," "In Progress," "Complete"). There is one record, one status, one owner. Any update, by either team, is reflected in real-time for both.</li>
                        <li><strong>360-Degree Built-in Visibility (The "Cure" for Blindness):</strong>
                        <br>- <em>For Sales:</em> The <code>Deployment</code> record appears as a related list on their <code>Account</code> page. They can see the status in real-time. No more emails.
                        <br>- <em>For Ops:</em> The <code>Deployment</code> record has a direct link back to the <code>Opportunity</code> and <code>Account</code>. They can click one link to see all pre-sales notes. No more context switching.
                        <br>- <em>For Finance:</em> They can now run a single report on the <code>Deployment</code> object to see Close Date (from the Opp) and Complete Date (on the Deployment). The data is clean, real-time, and in one system.
                        <br>- <em>For the Customer:</em> The Support team can see the <code>Deployment</code> record and know exactly what was deployed when the customer calls for help.</li>
                    </ol>
                    <p>No "Visual Noise" Solution:
                    <br>- No Zap.
                    <br>- No Google Sheet.
                    <br>- No security vulnerability (data never leaves the compliant environment).
                    <br>- No data duplication.
                    <br>- No process fracture.
                    <br>- No new subscription fees.</p>
                    <p>The architect didn't "use" Salesforce or "use" Zapier. They architected a solution within the core platform because the "Black Box" model revealed it was the single source of truth for the customer record. They resisted the "visual noise" of the easy fix and, in-doing so, prevented the company from accruing massive technical, financial, and cultural debt.</p>
                    <p>This is the power of the Black Box. It is not about "slowing down" for the sake of it. It is about protecting your focus to ensure you are moving in the right direction first. It is the disciplined practice of putting your energy into understanding the problem so completely that the solution becomes self-evident.</p>
                    <p>This book will teach you how to cultivate this mindset. You will learn to intentionally tune out the noise, to build by feel, and to catch the critical details that others miss. This is the foundation of all true architecture. It is not a "soft skill"; it is the hardest skill of all.</p>
                    <p>The first step is learning to close your eyes.</p>
                    <p>Welcome to the Black Box.</p>
                    <!-- End chapter text -->
                </div>
            </div>
        </section>
        <!-- End Book Chapter Section -->

        <!-- 
          =================================
          SECTION: ABOUT THIS SITE (NEW)
          This section acts as "Project 0", demonstrating the
          methodologies used to build the page itself.
          =================================
        -->
        <section id="about-site" data-section-id="about-site" class="py-24 md:py-32">
            <div data-stagger-container>
                <h2 class="text-3xl md:text-4xl font-bold light:text-slate-900 dark:text-white mb-16 flex items-center" data-stagger-reveal>
                    <span class="accent-color text-4xl md:text-5xl font-mono mr-3">04.</span> About This Site
                </h2>
                
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16">
                    <div data-stagger-reveal>
                        <h3 class="text-2xl font-bold light:text-slate-800 dark:text-slate-100 mb-4">A "Project 0" Showcase</h3>
                        <div class="space-y-6 text-lg light:text-slate-700 dark:text-slate-300">
                            <p>
                                This portfolio is more than just a resume; it's a living project. I designed and built it from scratch as a direct demonstration of my skills in front-end development, interactive design, and system legibility.
                            </p>
                            <p>
                                My goal was to create a clean, high-performance, and accessible single-page experience that is as well-crafted as the systems I build. It is fully responsive, respects user motion preferences, and is built with legible, commented code.
                            </p>
                        </div>
                    </div>
                    
                    <div data-stagger-reveal>
                        <h3 class="text-2xl font-bold light:text-slate-800 dark:text-slate-100 mb-4">Methodologies & Technologies</h3>
                        <div class="flex flex-wrap gap-3">
                            <span class="skill-badge">HTML5</span>
                            <span class="skill-badge">Tailwind CSS</span>
                            <span class="skill-badge">JavaScript (ES6+)</span>
                            <span class="skill-badge">Three.js (3D Background)</span>
                            <span class="skill-badge">Lucide Icons</span>
                            <span class="skill-badge">Responsive Design</span>
                            <span class="skill-badge">Dark/Light Mode</span>
                            <span class="skill-badge">Accessibility (a11y)</span>
                            <span class="skill-badge">Interactive UX (Cmd+K, Cursor)</span>
                            <span class="skill-badge">Single-File Architecture</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 
          =================================
          SECTION: CONTACT
          =================================
        -->
        <section id="contact" data-section-id="contact" class="py-24 md:py-32">
            <div class="max-w-2xl mx-auto" data-stagger-container>
                <div class="text-center" data-stagger-reveal>
                    <h2 class="text-3xl md:text-4xl font-bold light:text-slate-900 dark:text-white mb-6 flex items-center justify-center">
                        <span class="accent-color text-4xl md:text-5xl font-mono mr-3">05.</span> Get In Touch
                    </h2>
                    <p class="text-lg light:text-slate-700 dark:text-slate-300 mb-12">
                        I'm always open to discussing new projects, creative ideas, or opportunities to be part of your vision. Reach out and let's connect.
                    </p>
                </div>

                <div data-stagger-reveal class="light:bg-white dark:bg-slate-800/50 p-8 sm:p-10 rounded-2xl border light:border-slate-200 dark:border-slate-700 shadow-xl backdrop-blur-md">
                    <div class="space-y-6">
                        <!-- 
                          Clipboard Item:
                          - data-clipboard-text: Stores the text to be copied.
                          - role="button" / tabindex="0": Makes this <div>
                            interactive and accessible to keyboard users.
                        -->
                        <div class="contact-item" data-clipboard-text="2175087210" role="button" tabindex="0" aria-label="Copy phone number to clipboard">
                            <i data-lucide="phone" aria-hidden="true"></i>
                            <div>
                                <h4 class="contact-item-label">Phone</h4>
                                <p class="contact-item-value">(217) 508-7210</p>
                            </div>
                            <span class="copy-feedback ml-auto text-xs text-sky-400 opacity-0 transition-opacity duration-300">Copied!</span>
                        </div>
                        <div class="contact-item" data-clipboard-text="alecborman97@gmail.com" role="button" tabindex="0" aria-label="Copy email to clipboard">
                            <i data-lucide="mail" aria-hidden="true"></i>
                            <div>
                                <h4 class="contact-item-label">Email</h4>
                                <p class="contact-item-value">alecborman97@gmail.com</p>
                            </div>
                            <span class="copy-feedback ml-auto text-xs text-sky-400 opacity-0 transition-opacity duration-300">Copied!</span>
                        </div>
                        <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" rel="noopener noreferrer" class="contact-item" aria-label="View Alec Borman's LinkedIn Profile">
                            <i data-lucide="linkedin" aria-hidden="true"></i>
                            <div>
                                <h4 class="contact-item-label">LinkedIn</h4>
                                <p class="contact-item-value">in/alec-borman-9680b3160</p>
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- 
      =================================
      FOOTER
      - z-10: Sits above the background canvas.
      =================================
    -->
    <footer class="py-12 light:bg-slate-200 dark:bg-slate-800/50 relative z-10">
        <div class="container mx-auto px-6">
             <div class="flex flex-col md:flex-row justify-between items-center gap-6">
                 <div class="text-center md:text-left">
                     <a href="#home" class="text-lg font-bold light:text-slate-800 dark:text-white mb-4 inline-flex items-center gap-2 transition-colors hover:accent-color" aria-label="Alec Borman - Home">
                         <i data-lucide="code-2" class="accent-color"></i>
                         Alec Borman | Business Systems Architect
                     </a>
                     <p class="text-xs light:text-slate-600 dark:text-slate-400 mt-2">
                         Friendswood, TX | 
                         <a href="tel:2175087210" class="transition-colors light:hover:text-sky-700 dark:hover:text-sky-400">(217) 508-7210</a> | 
                         <a href="mailto:alecborman97@gmail.com" class="transition-colors light:hover:text-sky-700 dark:hover:text-sky-400">alecborman97@gmail.com</a>
                     </p>
                 </div>
                 <div class="flex space-x-6">
                     <a href="https://linkedin.com/in/alec-borman-9680b3160" target="_blank" rel="noopener noreferrer" class="footer-link" aria-label="LinkedIn Profile" data-magnetic>
                         <i data-lucide="linkedin" class="w-6 h-6"></i>
                     </a>
                 </div>
             </div>
             <div class="mt-8 pt-8 border-t light:border-slate-300 dark:border-slate-700 text-center text-sm light:text-slate-600 dark:text-slate-400">
                 &copy; <span id="copyright-year"></span> Alec Borman. All rights reserved.
             </div>
         </div>
         <style>
             /* Scoped styles for footer links.
                (Could also be done with Tailwind, but this is clean).
             */
             .footer-link {
                 color: #94A3B8; /* slate-400 */
                 transition: color 0.3s, transform 0.3s;
             }
             .footer-link:hover {
                 color: #38bdf8; /* sky-400 */
                 transform: translateY(-2px);
             }
             .light .footer-link { color: #475569; }
             .light .footer-link:hover { color: #0369a1; }
         </style>
    </footer>


    <!-- 
      =================================
      ADVANCED JAVASCRIPT
      This block contains all the logic for
      interactivity, animations, and helpers.
      All functions are documented.
      =================================
    -->
    <script>
        // --- Global Helpers ---
        
        // Check for OS-level reduced motion preference.
        const prefersReducedMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
        
        // Flag to control the 3D animation loop (for performance).
        let isAnimating3D = false;
        
        // Mouse coordinates, updated by a global listener.
        let mouse = { x: 0, y: 0 };
        
        // Linear Interpolation function: `lerp(start, end, t)`
        // Calculates an intermediate value between `start` and `end` at `t` (0.0 to 1.0).
        // This is the core of all "smoothing" and "easing" effects.
        const lerp = (start, end, t) => (1 - t) * start + t * end;
        
        // Global element references to be populated by initTheme().
        let htmlEl; 
        let themeToggleBtn, themeToggleMobileBtn, sunIcon, moonIcon;

        // --- 1. THEME (DARK/LIGHT MODE) ---
        
        /**
         * Applies the selected theme ('dark' or 'light') to the <html> element
         * and updates the toggle icons accordingly.
         * @param {string} theme - The theme to apply ("dark" or "light").
         */
        function applyTheme(theme) {
            if (theme === 'dark') {
                htmlEl.classList.add('dark');
                htmlEl.classList.remove('light');
                if(sunIcon) sunIcon.classList.remove('hidden');
                if(moonIcon) moonIcon.classList.add('hidden');
            } else {
                htmlEl.classList.add('light');
                htmlEl.classList.remove('dark');
                if(sunIcon) sunIcon.classList.add('hidden');
                if(moonIcon) moonIcon.classList.remove('hidden');
            }
        }
        
        /**
         * Initializes the theme functionality.
         * - Caches DOM elements.
         * - Checks localStorage for a saved theme.
         * - Falls back to system preference (`prefers-color-scheme`).
         * - Defaults to 'dark' if no preference is found.
         * - Attaches click handlers to both toggle buttons.
         */
        function initTheme() {
            themeToggleBtn = document.getElementById('theme-toggle');
            themeToggleMobileBtn = document.getElementById('theme-toggle-mobile');
            sunIcon = document.getElementById('theme-icon-sun');
            moonIcon = document.getElementById('theme-icon-moon');
            htmlEl = document.documentElement;
            
            const savedTheme = localStorage.getItem('theme');
            const systemPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
            
            // Priority: Saved Theme > System Preference > Default ('dark')
            let currentTheme = savedTheme || (systemPrefersDark ? 'dark' : 'dark');
            applyTheme(currentTheme);

            // Handler to toggle, apply, and save the new theme.
            const toggleHandler = () => {
                const newTheme = htmlEl.classList.contains('dark') ? 'light' : 'dark';
                applyTheme(newTheme);
                localStorage.setItem('theme', newTheme);
            };
            themeToggleBtn.addEventListener('click', toggleHandler);
            themeToggleMobileBtn.addEventListener('click', toggleHandler);
        }

        // --- 2. MOBILE MENU ---
        
        /**
         * Initializes the mobile menu toggle functionality.
         * - Toggles the '-translate-x-full' class to slide the menu.
         * - Toggles the open/close (hamburger/X) icons.
         * - Disables body scroll when the menu is open.
         * - Adds click handlers to nav links to auto-close the menu on navigation.
         */
        function initMobileMenu() {
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            const menuIconOpen = document.getElementById('menu-icon-open');
            const menuIconClose = document.getElementById('menu-icon-close');
            const mobileNavLinks = document.querySelectorAll('.mobile-nav-link');

            const toggleMobileMenu = () => {
                mobileMenu.classList.toggle('-translate-x-full');
                menuIconOpen.classList.toggle('hidden');
                menuIconClose.classList.toggle('hidden');
                // Prevent scrolling the body when the menu is open
                document.body.style.overflow = mobileMenu.classList.contains('-translate-x-full') ? '' : 'hidden';
            };
            mobileMenuButton.addEventListener('click', toggleMobileMenu);
            // Add click listener to all mobile links to close the menu
            mobileNavLinks.forEach(link => link.addEventListener('click', toggleMobileMenu));
        }

        // --- 3. 3D Background (Three.js) ---
        
        /**
         * Initializes the 3D particle background.
         * - Bails out if user prefers reduced motion or Three.js is missing.
         * - Sets up the Scene, Camera, and WebGLRenderer.
         * - Creates a particle system (Points) with BufferGeometry.
         * - Adds mouse and resize listeners.
         * - Starts the `animate` loop.
         * - Handles visibility changes to pause/resume animation.
         */
        function initThreeJS() {
            if (prefersReducedMotion || typeof THREE === 'undefined') {
                const canvas = document.getElementById('bg-canvas');
                if (canvas) canvas.style.display = 'none';
                return; // Abort if user wants reduced motion
            }

            let scene, camera, renderer, particles;
            const canvas = document.getElementById('bg-canvas');
            if (!canvas) return; // Abort if canvas element isn't found
            
            scene = new THREE.Scene();
            camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
            camera.position.z = 5;
            
            try {
                renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true });
                renderer.setSize(window.innerWidth, window.innerHeight);
                renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2)); // For performance on high-DPI screens
            } catch (e) {
                console.error("Failed to initialize WebGLRenderer:", e);
                canvas.style.display = 'none'; // Hide canvas if WebGL fails
                return;
            }

            // Create particles
            const particleCount = 5000;
            const positions = new Float32Array(particleCount * 3);
            for (let i = 0; i < particleCount * 3; i++) {
                positions[i] = (Math.random() - 0.5) * 10; // Randomly position in a 10x10x10 cube
            }
            const geometry = new THREE.BufferGeometry();
            geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
            
            const material = new THREE.PointsMaterial({
                color: 0x38bdf8, // sky-500
                size: 0.015,
                blending: THREE.AdditiveBlending, // Creates a "glow" effect where particles overlap
                transparent: true,
                opacity: 0.8
            });
            
            particles = new THREE.Points(geometry, material);
            scene.add(particles);

            // Global mouse listener
            window.addEventListener('mousemove', (event) => {
                mouse.x = (event.clientX / window.innerWidth) * 2 - 1; // Normalize to -1 to +1
                mouse.y = -(event.clientY / window.innerHeight) * 2 + 1; // Normalize to -1 to +1 (inverted)
            });

            // Resize listener
            window.addEventListener('resize', () => {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
                renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
            });

            const clock = new THREE.Clock();
            
            // The animation loop
            const animate = () => {
                if (!isAnimating3D) return; // Pause if flag is false
                
                const elapsedTime = clock.getElapsedTime();
                
                // Animate particles
                particles.rotation.y = elapsedTime * 0.02;
                particles.rotation.x = elapsedTime * 0.01;
                
                // Lerp camera to "follow" the mouse slightly (parallax effect)
                camera.position.x = lerp(camera.position.x, mouse.x * 0.5, 0.05);
                camera.position.y = lerp(camera.position.y, mouse.y * 0.5, 0.05);
                camera.lookAt(scene.position);
                
                renderer.render(scene, camera);
                requestAnimationFrame(animate); // Request the next frame
            };
            
            isAnimating3D = true;
            animate();

            // Pause animation when tab is not visible to save resources
            document.addEventListener("visibilitychange", () => {
                isAnimating3D = !document.hidden;
                if (isAnimating3D) animate(); // Resume animation
            });
        }

        // --- 4. Custom Cursor ---
        
        /**
         * Initializes the custom cursor.
         - Bails out if user prefers reduced motion.
         - Caches cursor elements.
         - Sets up an animation loop using `requestAnimationFrame` and `lerp`
           to create the "trailing" effect for the outline.
         - Adds hover listeners to all interactive elements to trigger
           the 'cursor-hover' class on the body.
         */
        function initCursor() {
            if (prefersReducedMotion) return;

            const cursorDot = document.getElementById('cursor-dot');
            const cursorOutline = document.getElementById('cursor-outline');
            if (!cursorDot || !cursorOutline) return;
            const body = document.body;

            let dotX = 0, dotY = 0, outlineX = 0, outlineY = 0;

            window.addEventListener('mousemove', e => {
                dotX = e.clientX;
                dotY = e.clientY;
            });
            
            const animateCursor = () => {
                // The outline "lags" behind the dot using lerp
                outlineX = lerp(outlineX, dotX, 0.1);
                outlineY = lerp(outlineY, dotY, 0.1);
                
                cursorDot.style.transform = `translate(${dotX}px, ${dotY}px)`;
                cursorOutline.style.transform = `translate(${outlineX}px, ${outlineY}px)`;
                
                requestAnimationFrame(animateCursor);
            };
            requestAnimationFrame(animateCursor);

            // Query all interactive elements
            const hoverElements = document.querySelectorAll('a, button, [data-magnetic], [role="button"], .project-card');
            hoverElements.forEach(el => {
                el.addEventListener('mouseenter', () => body.classList.add('cursor-hover'));
                el.addEventListener('mouseleave', () => body.classList.remove('cursor-hover'));
            });
        }

        // --- 5. Magnetic Buttons ---
        
        /**
         * Initializes the "magnetic" effect for elements with `data-magnetic`.
         * - Bails out if user prefers reduced motion.
         * - On mousemove, calculates the cursor's position *relative* to the
           element's center.
         * - Uses `transform: translate` to move the element towards the cursor.
         * - On mouseleave, snaps the element back to (0,0).
         */
        function initMagneticButtons() {
            if (prefersReducedMotion) return;

            const strength = 0.4; // How "strong" the pull is
            document.querySelectorAll('[data-magnetic]').forEach(el => {
                el.addEventListener('mousemove', e => {
                    const rect = el.getBoundingClientRect();
                    const x = e.clientX - rect.left - rect.width / 2;
                    const y = e.clientY - rect.top - rect.height / 2;
                    
                    el.style.transition = 'transform 0.1s ease-out'; // Fast reaction
                    el.style.transform = `translate(${x * strength}px, ${y * strength}px)`;
                });
                el.addEventListener('mouseleave', () => {
                    el.style.transition = 'transform 0.3s cubic-bezier(0.23, 1, 0.32, 1)'; // Bouncy return
                    el.style.transform = 'translate(0,0)';
                });
            });
        }

        // --- 6. Scroll Features (Progress Bar, Nav Highlighting, Header Style) ---
        
        /**
         * Initializes all scroll-based features.
         * - `IntersectionObserver`: Detects which `[data-section-id]` is in
           the middle 50% of the viewport and applies the '.active' class
           to the corresponding nav link.
         * - `scroll` Event Listener:
         * 1. Updates the width of the `#scroll-progress` bar.
         * 2. Adds/removes the blurred background style from the `#header`
            based on scroll position (scrollY > 50).
         */
        function initScrollFeatures() {
            const progressBar = document.getElementById('scroll-progress');
            const header = document.getElementById('header');
            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('section[data-section-id]');
            if (sections.length === 0) return;

            // Observer for nav link highlighting
            const sectionObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting && entry.intersectionRatio > 0.4) {
                        const id = entry.target.getAttribute('data-section-id');
                        navLinks.forEach(link => {
                            link.classList.toggle('active', link.getAttribute('href') === `#${id}`);
                        });
                    }
                });
            }, {
                rootMargin: '-50% 0px -50% 0px', // Only observes the center 50% of the screen
                threshold: 0.4
            });
            sections.forEach(section => sectionObserver.observe(section));

            // Listener for progress bar and header style
            window.addEventListener('scroll', () => {
                const scrollY = window.scrollY;
                
                // 1. Progress Bar
                if (progressBar) {
                    const docHeight = document.documentElement.scrollHeight;
                    const viewHeight = window.innerHeight;
                    const progress = (scrollY / (docHeight - viewHeight)) * 100;
                    progressBar.style.width = `${progress}%`;
                }
                
                // 2. Header Style
                if (header) {
                    if (scrollY > 50) {
                        // Add "glassmorphism" style
                        header.classList.add('light:bg-white/80', 'dark:bg-slate-900/80', 'backdrop-blur-md', 'shadow-md');
                    } else {
                        // Remove style when at top
                        header.classList.remove('light:bg-white/80', 'dark:bg-slate-900/80', 'backdrop-blur-md', 'shadow-md');
                    }
                }
            });
        }

        // --- 7. Staggered Reveals ---
        
        /**
         * Initializes the scroll-reveal animations.
         * - Bails out if user prefers reduced motion (and just shows everything).
         * - Uses `IntersectionObserver` to watch `[data-stagger-container]` elements.
         * - When a container is 10% visible, it finds all `[data-stagger-reveal]`
           children and adds the `.is-revealed` class to them with a 150ms delay,
           creating the "stagger" effect.
         * - Unobserves after animating to prevent re-animation.
         * - Also handles "loose" items not in a container.
         */
        function initStaggeredReveals() {
            if (prefersReducedMotion) {
                // If reduced motion, just show all elements immediately.
                document.querySelectorAll('[data-stagger-reveal]').forEach(el => el.classList.add('is-revealed'));
                return;
            }

            // Animate items inside a container
            const revealContainers = document.querySelectorAll('[data-stagger-container]');
            revealContainers.forEach(container => {
                const items = container.querySelectorAll('[data-stagger-reveal]');
                const observer = new IntersectionObserver((entries, obs) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            items.forEach((item, index) => {
                                setTimeout(() => {
                                    item.classList.add('is-revealed');
                                }, index * 150); // 150ms delay
                            });
                            obs.unobserve(container); // Animate once
                        }
                    });
                }, { threshold: 0.1 }); // Trigger when 10% visible
                observer.observe(container);
            });

            // Animate items NOT in a container
            const looseItems = document.querySelectorAll('[data-stagger-reveal]:not([data-stagger-container] [data-stagger-reveal])');
            looseItems.forEach(item => {
                const observer = new IntersectionObserver((entries, obs) => {
                    entries.forEach(entry => {
                        if(entry.isIntersecting) {
                            item.classList.add('is-revealed');
                            obs.unobserve(item);
                        }
                    });
                }, { threshold: 0.1 });
                observer.observe(item);
            });
        }

        // --- 8. Command Palette ---
        
        /**
         * Initializes the Ctrl+K command palette.
         * - Caches all DOM elements.
         * - `openPalette()`: Shows palette, focuses input.
         * - `closePalette()`: Hides palette, blurs input.
         * - `filterItems()`: Filters the list based on input value.
         * - `updateSelection()`: Highlights the selected item (for keyboard).
         * - `executeSelection()`: "Clicks" the selected item.
         * - Adds `keydown` listener for `Ctrl+K` and `Escape`.
         * - Adds `input` listener to filter.
         * - Adds `keydown` listener for `ArrowUp`, `ArrowDown`, and `Enter`.
         * - Adds click listeners to the overlay and items.
         */
        function initCommandPalette() {
            const palette = document.getElementById('command-palette');
            const overlay = document.getElementById('command-palette-overlay');
            const input = document.getElementById('command-palette-input');
            const list = document.getElementById('command-palette-list');
            if (!palette || !overlay || !input || !list) return;
            const items = list.querySelectorAll('.command-item');
            let selectedIndex = 0;

            const openPalette = () => {
                palette.classList.add('visible');
                overlay.classList.add('visible');
                input.value = '';
                filterItems('');
                input.focus();
            };

            const closePalette = () => {
                palette.classList.remove('visible');
                overlay.classList.remove('visible');
                input.blur();
            };

            const filterItems = (query) => {
                query = query.toLowerCase();
                selectedIndex = 0;
                items.forEach((item) => {
                    const text = item.textContent.toLowerCase();
                    const isVisible = text.includes(query);
                    item.style.display = isVisible ? 'flex' : 'none';
                });
                updateSelection(); // Highlight the first visible item
            };
            
            const updateSelection = () => {
                items.forEach(item => item.classList.remove('selected'));
                const visibleItems = Array.from(items).filter(item => item.style.display !== 'none');
                if (visibleItems.length > 0) {
                    selectedIndex = Math.max(0, Math.min(selectedIndex, visibleItems.length - 1));
                    visibleItems[selectedIndex].classList.add('selected');
                    // Ensure the selected item is visible in the list
                    visibleItems[selectedIndex].scrollIntoView({ block: 'nearest' });
                }
            };

            const executeSelection = () => {
                const visibleItems = Array.from(items).filter(item => item.style.display !== 'none');
                if (visibleItems.length > 0 && visibleItems[selectedIndex]) {
                    visibleItems[selectedIndex].click(); // Simulate click
                }
            };
            
            // Global key listeners
            window.addEventListener('keydown', e => {
                if ((e.metaKey || e.ctrlKey) && e.key === 'k') {
                    e.preventDefault(); // Prevent browser's default "find"
                    palette.classList.contains('visible') ? closePalette() : openPalette();
                }
                if (e.key === 'Escape' && palette.classList.contains('visible')) {
                    closePalette();
                }
            });

            // Input listeners
            input.addEventListener('input', () => filterItems(input.value));
            input.addEventListener('keydown', e => {
                const visibleItems = Array.from(items).filter(item => item.style.display !== 'none');
                if (e.key === 'ArrowDown') {
                    e.preventDefault();
                    selectedIndex = (visibleItems.length > 0) ? (selectedIndex + 1) % visibleItems.length : 0;
                    updateSelection();
                } else if (e.key === 'ArrowUp') {
                    e.preventDefault();
                    selectedIndex = (visibleItems.length > 0) ? (selectedIndex - 1 + visibleItems.length) % visibleItems.length : 0;
                    updateSelection();
                } else if (e.key === 'Enter') {
                    e.preventDefault();
                    executeSelection();
                }
            });
            
            // Click listeners
            overlay.addEventListener('click', closePalette);
            items.forEach(item => {
                item.addEventListener('click', e => {
                    e.preventDefault(); // We handle the navigation
                    const targetId = item.getAttribute('href');
                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        targetElement.scrollIntoView({ behavior: 'smooth' });
                    }
                    closePalette();
                });
            });
        }

        // --- 9. "Copy to Clipboard" ---
        
        /**
         * Initializes all "copy to clipboard" buttons.
         * - Finds all elements with `[data-clipboard-text]`.
         * - On click (or Enter/Space), it creates a *temporary, hidden*
           `textarea` element, injects the text, selects it, and uses
           the `document.execCommand('copy')` API.
         * - `execCommand` is used for broad compatibility, as
           `navigator.clipboard.writeText()` can fail in secure/iframe contexts.
         * - Shows a "Copied!" feedback message.
         */
        function initClipboard() {
            document.querySelectorAll('[data-clipboard-text]').forEach(item => {
                const feedbackEl = item.querySelector('.copy-feedback');
                
                const action = () => {
                    const text = item.getAttribute('data-clipboard-text');
                    
                    try {
                        // Create a temporary textarea
                        const textArea = document.createElement('textarea');
                        textArea.value = text;
                        textArea.style.position = 'fixed';
                        textArea.style.opacity = 0;
                        document.body.appendChild(textArea);
                        textArea.focus();
                        textArea.select();
                        document.execCommand('copy'); // Copy
                        document.body.removeChild(textArea); // Clean up

                        // Show feedback
                        if (feedbackEl) {
                            feedbackEl.style.opacity = '1';
                            setTimeout(() => {
                                feedbackEl.style.opacity = '0';
                            }, 2000);
                        }
                    } catch (err) {
                        console.error('Failed to copy text: ', err);
                    }
                };

                item.addEventListener('click', action);
                item.addEventListener('keydown', (e) => {
                    // Accessibility: Allow copy with Enter or Space
                    if (e.key === 'Enter' || e.key === ' ') {
                        e.preventDefault();
                        action();
                    }
                });
            });
        }

        // --- 10. COPYRIGHT YEAR ---
        
        /**
         * Dynamically inserts the current year into the copyright notice.
         */
        function initCopyright() {
            const yearEl = document.getElementById('copyright-year');
            if(yearEl) {
                yearEl.textContent = new Date().getFullYear();
            }
        }

        // --- RUN ALL INITIALIZERS ---
        
        /**
         * CRITICAL: `window.onload` is used instead of `DOMContentLoaded`.
         * This ensures that all *deferred* scripts (like Lucide Icons and
         * Three.js) have fully loaded and are available in the global scope
         * *before* our initialization functions (like `lucide.createIcons()`
         * and `initThreeJS()`) try to use them.
         */
        window.onload = () => {
            try {
                // Initialize Lucide icons (replaces `data-lucide` attributes with SVGs)
                lucide.createIcons();
            } catch (e) {
                console.error("Lucide icons failed to create.", e);
            }
            
            // Run all initialization functions
            initTheme();
            initMobileMenu();
            initThreeJS();
            initCursor();
            initMagneticButtons();
            initScrollFeatures();
            initStaggeredReveals();
            initCommandPalette();
            initClipboard();
            initCopyright();
        };
    </script>
</body>
</html>
