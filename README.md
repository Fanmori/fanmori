<!DOCTYPE html>
<html lang="fa" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Profile — Network & Backend Engineer</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@200;300;400;500;600;700&family=Vazirmatn:wght@200;300;400;500;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'Vazirmatn', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        :root {
            --neon-lime: #84cc16;
            --neon-glow: 0 0 10px rgba(132, 204, 22, 0.5), 0 0 20px rgba(132, 204, 22, 0.3);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            background: #0a0a0a;
            color: #e5e5e5;
            font-family: 'Inter', 'Vazirmatn', sans-serif;
            overflow-x: hidden;
        }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #0a0a0a; }
        ::-webkit-scrollbar-thumb { background: #84cc16; border-radius: 3px; }

        /* Noise Texture */
        .noise-overlay {
            position: fixed;
            inset: 0;
            z-index: 50;
            pointer-events: none;
            opacity: 0.04;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
        }

        /* Scanlines */
        .scanlines {
            position: fixed;
            inset: 0;
            z-index: 49;
            pointer-events: none;
            background: linear-gradient(rgba(18,16,16,0) 50%, rgba(0,0,0,0.25) 50%),
                        linear-gradient(90deg, rgba(255,0,0,0.06), rgba(0,255,0,0.02), rgba(0,0,255,0.06));
            background-size: 100% 2px, 3px 100%;
            opacity: 0.2;
        }

        /* Animated Background Grid */
        .bg-grid {
            position: fixed;
            inset: 0;
            z-index: 0;
            background-image: 
                linear-gradient(rgba(132,204,22,0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(132,204,22,0.03) 1px, transparent 1px);
            background-size: 60px 60px;
            animation: gridMove 20s linear infinite;
        }

        @keyframes gridMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(60px, 60px); }
        }

        /* Neon Text */
        .neon-text {
            text-shadow: 0 0 10px rgba(132,204,22,0.5), 0 0 20px rgba(132,204,22,0.3), 0 0 40px rgba(132,204,22,0.15);
        }

        .neon-text-white {
            text-shadow: 0 0 10px rgba(255,255,255,0.3), 0 0 20px rgba(255,255,255,0.15);
        }

        /* Glass Panel */
        .glass-panel {
            background: rgba(23, 23, 23, 0.6);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .glass-panel-hover:hover {
            border-color: rgba(132, 204, 22, 0.4);
            box-shadow: 0 0 30px rgba(132, 204, 22, 0.1);
        }

        /* Terminal Cursor */
        .cursor-blink {
            display: inline-block;
            width: 10px;
            height: 20px;
            background: #84cc16;
            animation: blink 1s step-end infinite;
            vertical-align: middle;
            margin-left: 4px;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        /* Typing Animation */
        .typing-line {
            overflow: hidden;
            white-space: nowrap;
            animation: typing 2s steps(40) forwards;
            width: 0;
        }

        @keyframes typing {
            to { width: 100%; }
        }

        /* Contribution Graph */
        .contrib-cell {
            width: 12px;
            height: 12px;
            border-radius: 2px;
            transition: all 0.2s;
        }

        .contrib-cell:hover {
            transform: scale(1.8);
            z-index: 10;
        }

        .contrib-0 { background: rgba(255,255,255,0.04); }
        .contrib-1 { background: rgba(132,204,22,0.15); }
        .contrib-2 { background: rgba(132,204,22,0.35); }
        .contrib-3 { background: rgba(132,204,22,0.55); }
        .contrib-4 { background: rgba(132,204,22,0.85); }

        /* Skill Bar */
        .skill-bar {
            height: 4px;
            background: rgba(255,255,255,0.06);
            border-radius: 2px;
            overflow: hidden;
        }

        .skill-fill {
            height: 100%;
            background: linear-gradient(90deg, #84cc16, #059669);
            border-radius: 2px;
            box-shadow: 0 0 10px rgba(132,204,22,0.4);
            transition: width 1.5s cubic-bezier(0.4, 0, 0.2, 1);
            width: 0;
        }

        .skill-fill.animated {
            /* width set via JS */
        }

        /* Pulse Ring */
        .pulse-ring {
            animation: pulseRing 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }

        @keyframes pulseRing {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        /* Status Indicator */
        .status-dot {
            width: 8px;
            height: 8px;
            background: #84cc16;
            border-radius: 50%;
            box-shadow: 0 0 8px rgba(132,204,22,0.8);
            animation: statusPulse 2s ease-in-out infinite;
        }

        @keyframes statusPulse {
            0%, 100% { box-shadow: 0 0 4px rgba(132,204,22,0.6); }
            50% { box-shadow: 0 0 16px rgba(132,204,22,1); }
        }

        /* Network Lines */
        .network-line {
            position: absolute;
            background: linear-gradient(90deg, transparent, rgba(132,204,22,0.15), transparent);
            height: 1px;
            animation: networkFlow 3s linear infinite;
        }

        @keyframes networkFlow {
            0% { transform: translateX(-100%); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateX(100%); opacity: 0; }
        }

        /* Project Card Glow */
        .project-glow {
            position: absolute;
            inset: -1px;
            border-radius: 12px;
            background: linear-gradient(135deg, rgba(132,204,22,0.15), transparent, rgba(5,150,105,0.15));
            opacity: 0;
            transition: opacity 0.5s;
        }

        .project-card:hover .project-glow {
            opacity: 1;
        }

        /* Fade In */
        .fade-section {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .fade-section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Activity Graph Line */
        .activity-line {
            stroke-dasharray: 1000;
            stroke-dashoffset: 1000;
            animation: drawLine 3s ease forwards;
        }

        @keyframes drawLine {
            to { stroke-dashoffset: 0; }
        }

        /* Orbit Animation */
        .orbit {
            animation: orbit 20s linear infinite;
        }

        @keyframes orbit {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .orbit-reverse {
            animation: orbitReverse 15s linear infinite;
        }

        @keyframes orbitReverse {
            from { transform: rotate(360deg); }
            to { transform: rotate(0deg); }
        }

        /* Floating */
        .float-slow {
            animation: floatSlow 6s ease-in-out infinite;
        }

        @keyframes floatSlow {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-12px); }
        }

        .float-medium {
            animation: floatMedium 4s ease-in-out infinite;
        }

        @keyframes floatMedium {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        /* Code block style */
        .code-keyword { color: #c084fc; }
        .code-string { color: #84cc16; }
        .code-comment { color: #525252; }
        .code-function { color: #60a5fa; }
        .code-number { color: #fb923c; }
        .code-type { color: #2dd4bf; }

        /* Tooltip */
        .tooltip-container {
            position: relative;
        }
        .tooltip-container .tooltip-text {
            visibility: hidden;
            opacity: 0;
            position: absolute;
            bottom: calc(100% + 8px);
            left: 50%;
            transform: translateX(-50%);
            background: rgba(23,23,23,0.95);
            border: 1px solid rgba(255,255,255,0.1);
            color: #e5e5e5;
            font-size: 10px;
            padding: 4px 8px;
            border-radius: 6px;
            white-space: nowrap;
            transition: all 0.2s;
            pointer-events: none;
        }
        .tooltip-container:hover .tooltip-text {
            visibility: visible;
            opacity: 1;
        }

        /* Nav indicator */
        .nav-link.active {
            color: #84cc16;
        }
        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            right: 0;
            height: 1px;
            background: #84cc16;
            box-shadow: 0 0 8px rgba(132,204,22,0.5);
        }

        /* Stat counter animation */
        .stat-number {
            font-variant-numeric: tabular-nums;
        }
    </style>
</head>
<body class="relative">
    <!-- Effects Layers -->
    <div class="bg-grid"></div>
    <div class="scanlines"></div>
    <div class="noise-overlay"></div>

    <!-- Decorative Orbs -->
    <div class="fixed top-20 left-10 w-96 h-96 bg-lime-900/10 rounded-full blur-[120px] mix-blend-screen pointer-events-none"></div>
    <div class="fixed bottom-20 right-10 w-80 h-80 bg-emerald-900/10 rounded-full blur-[100px] mix-blend-screen pointer-events-none"></div>

    <!-- Navigation -->
    <nav class="fixed top-0 left-0 right-0 z-40 glass-panel border-b border-white/5">
        <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
            <div class="flex items-center gap-3">
                <div class="relative">
                    <i data-lucide="terminal" class="w-5 h-5 text-lime-500"></i>
                </div>
                <span class="text-sm font-semibold tracking-tight text-white">dev.profile</span>
                <span class="text-xs text-neutral-600 font-mono">v2.0</span>
            </div>
            <div class="hidden md:flex items-center gap-8">
                <a href="#about" class="nav-link relative text-xs font-medium text-neutral-400 hover:text-lime-400 transition-colors uppercase tracking-widest">About</a>
                <a href="#skills" class="nav-link relative text-xs font-medium text-neutral-400 hover:text-lime-400 transition-colors uppercase tracking-widest">Skills</a>
                <a href="#projects" class="nav-link relative text-xs font-medium text-neutral-400 hover:text-lime-400 transition-colors uppercase tracking-widest">Projects</a>
                <a href="#activity" class="nav-link relative text-xs font-medium text-neutral-400 hover:text-lime-400 transition-colors uppercase tracking-widest">Activity</a>
                <a href="#connect" class="nav-link relative text-xs font-medium text-neutral-400 hover:text-lime-400 transition-colors uppercase tracking-widest">Connect</a>
            </div>
            <div class="flex items-center gap-4">
                <div class="flex items-center gap-2">
                    <div class="status-dot"></div>
                    <span class="text-xs text-lime-400 font-medium">Available</span>
                </div>
            </div>
        </div>
    </nav>

    <main class="relative z-10">
        <!-- Hero Section -->
        <section class="min-h-screen flex items-center justify-center pt-20 pb-12 px-6">
            <div class="max-w-6xl mx-auto w-full">
                <div class="grid lg:grid-cols-12 gap-8 items-center">
                    <!-- Left: Info -->
                    <div class="lg:col-span-7 space-y-8">
                        <!-- Terminal Header -->
                        <div class="glass-panel rounded-xl overflow-hidden">
                            <div class="flex items-center gap-2 px-4 py-3 border-b border-white/5">
                                <div class="w-3 h-3 rounded-full bg-red-500/60"></div>
                                <div class="w-3 h-3 rounded-full bg-yellow-500/60"></div>
                                <div class="w-3 h-3 rounded-full bg-green-500/60"></div>
                                <span class="text-[10px] text-neutral-600 font-mono ml-2">~/profile/README.md</span>
                            </div>
                            <div class="p-6 space-y-3">
                                <p class="text-xs font-mono text-neutral-600">$ cat profile.md</p>
                                <div class="space-y-2">
                                    <h1 class="text-4xl md:text-6xl font-semibold text-white neon-text-white tracking-tight leading-tight">
                                        Hi, I'm <span class="text-lime-400 neon-text">@devuser</span>
                                    </h1>
                                    <div class="flex items-center gap-3 mt-4">
                                        <i data-lucide="network" class="w-5 h-5 text-lime-500"></i>
                                        <p class="text-lg md:text-xl text-neutral-300 font-light">
                                            Network Engineer & Backend Developer
                                        </p>
                                    </div>
                                </div>
                                <div class="mt-6 font-mono text-sm space-y-1.5 text-neutral-400">
                                    <p><span class="code-keyword">const</span> <span class="code-function">developer</span> = {</p>
                                    <p class="pl-4"><span class="code-type">focus</span>: <span class="code-string">"Backend & Infrastructure"</span>,</p>
                                    <p class="pl-4"><span class="code-type">passion</span>: <span class="code-string">"Network Architecture"</span>,</p>
                                    <p class="pl-4"><span class="code-type">loves</span>: [<span class="code-string">"TCP/IP"</span>, <span class="code-string">"Distributed Systems"</span>, <span class="code-string">"Go"</span>],</p>
                                    <p class="pl-4"><span class="code-type">currentProject</span>: <span class="code-string">"Microservices Orchestrator"</span></p>
                                    <p>};<span class="cursor-blink"></span></p>
                                </div>
                            </div>
                        </div>

                        <!-- Quick Stats -->
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-3">
                            <div class="glass-panel rounded-xl p-4 text-center glass-panel-hover transition-all duration-300">
                                <p class="stat-number text-2xl md:text-3xl font-semibold text-lime-400 neon-text" data-target="247">0</p>
                                <p class="text-[10px] uppercase tracking-widest text-neutral-500 mt-1">Repositories</p>
                            </div>
                            <div class="glass-panel rounded-xl p-4 text-center glass-panel-hover transition-all duration-300">
                                <p class="stat-number text-2xl md:text-3xl font-semibold text-lime-400 neon-text" data-target="1842">0</p>
                                <p class="text-[10px] uppercase tracking-widest text-neutral-500 mt-1">Commits</p>
                            </div>
                            <div class="glass-panel rounded-xl p-4 text-center glass-panel-hover transition-all duration-300">
                                <p class="stat-number text-2xl md:text-3xl font-semibold text-lime-400 neon-text" data-target="89">0</p>
                                <p class="text-[10px] uppercase tracking-widest text-neutral-500 mt-1">PRs Merged</p>
                            </div>
                            <div class="glass-panel rounded-xl p-4 text-center glass-panel-hover transition-all duration-300">
                                <p class="stat-number text-2xl md:text-3xl font-semibold text-lime-400 neon-text" data-target="56">0</p>
                                <p class="text-[10px] uppercase tracking-widest text-neutral-500 mt-1">Stars</p>
                            </div>
                        </div>
                    </div>

                    <!-- Right: Visual -->
                    <div class="lg:col-span-5 flex items-center justify-center">
                        <div class="relative w-72 h-72 md:w-80 md:h-80">
                            <!-- Orbit Rings -->
                            <div class="absolute inset-0 border border-lime-500/10 rounded-full orbit"></div>
                            <div class="absolute inset-6 border border-lime-500/5 rounded-full orbit-reverse"></div>
                            <div class="absolute inset-12 border border-emerald-500/10 rounded-full orbit" style="animation-duration: 25s;"></div>

                            <!-- Avatar -->
                            <div class="absolute inset-0 flex items-center justify-center">
                                <div class="relative">
                                    <div class="w-36 h-36 md:w-40 md:h-40 rounded-full overflow-hidden border-2 border-lime-500/30 float-slow" style="box-shadow: 0 0 40px rgba(132,204,22,0.15);">
                                        <img src="https://picsum.photos/seed/devprofile42/400/400.jpg" alt="Profile" class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700">
                                    </div>
                                    <!-- Status Badge -->
                                    <div class="absolute -bottom-1 left-1/2 -translate-x-1/2 glass-panel rounded-full px-3 py-1 flex items-center gap-1.5">
                                        <div class="status-dot" style="width:6px;height:6px;"></div>
                                        <span class="text-[9px] font-medium text-lime-400 uppercase tracking-wider">Building</span>
                                    </div>
                                </div>
                            </div>

                            <!-- Orbiting Icons -->
                            <div class="absolute top-2 left-1/2 -translate-x-1/2 orbit" style="animation-duration: 20s;">
                                <div class="w-10 h-10 glass-panel rounded-lg flex items-center justify-center" style="box-shadow: 0 0 15px rgba(132,204,22,0.1);">
                                    <i data-lucide="server" class="w-4 h-4 text-lime-500"></i>
                                </div>
                            </div>
                            <div class="absolute bottom-2 left-1/2 -translate-x-1/2 orbit-reverse">
                                <div class="w-10 h-10 glass-panel rounded-lg flex items-center justify-center" style="box-shadow: 0 0 15px rgba(5,150,105,0.1);">
                                    <i data-lucide="database" class="w-4 h-4 text-emerald-500"></i>
                                </div>
                            </div>
                            <div class="absolute top-1/2 -translate-y-1/2 left-0 orbit" style="animation-duration: 15s;">
                                <div class="w-10 h-10 glass-panel rounded-lg flex items-center justify-center" style="box-shadow: 0 0 15px rgba(96,165,250,0.1);">
                                    <i data-lucide="globe" class="w-4 h-4 text-blue-400"></i>
                                </div>
                            </div>
                            <div class="absolute top-1/2 -translate-y-1/2 right-0 orbit-reverse" style="animation-duration: 18s;">
                                <div class="w-10 h-10 glass-panel rounded-lg flex items-center justify-center" style="box-shadow: 0 0 15px rgba(192,132,252,0.1);">
                                    <i data-lucide="shield" class="w-4 h-4 text-purple-400"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Scroll Indicator -->
                <div class="flex justify-center mt-16">
                    <div class="flex flex-col items-center gap-2 text-neutral-600">
                        <span class="text-[9px] uppercase tracking-[0.3em]">Scroll</span>
                        <div class="w-5 h-8 rounded-full border border-neutral-700 flex items-start justify-center p-1.5">
                            <div class="w-1 h-1.5 bg-lime-500 rounded-full animate-bounce"></div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="py-24 px-6 fade-section">
            <div class="max-w-6xl mx-auto">
                <div class="flex items-center gap-3 mb-12">
                    <div class="w-8 h-8 rounded-lg bg-lime-500/10 flex items-center justify-center">
                        <i data-lucide="user" class="w-4 h-4 text-lime-500"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-semibold text-white tracking-tight">About Me</h2>
                    <div class="flex-1 h-px bg-gradient-to-r from-lime-500/20 to-transparent ml-4"></div>
                </div>

                <div class="grid lg:grid-cols-2 gap-6">
                    <!-- Bio -->
                    <div class="glass-panel rounded-2xl p-8 glass-panel-hover transition-all duration-300">
                        <div class="flex items-start gap-4 mb-6">
                            <div class="w-12 h-12 rounded-xl bg-lime-500/10 flex items-center justify-center flex-shrink-0">
                                <i data-lucide="code-2" class="w-6 h-6 text-lime-500"></i>
                            </div>
                            <div>
                                <h3 class="text-lg font-semibold text-white mb-2">Backend & Network Engineer</h3>
                                <p class="text-sm text-neutral-400 leading-relaxed">
                                    I architect and build robust backend systems and network infrastructures. With deep expertise in 
                                    distributed systems, TCP/IP networking, and cloud infrastructure, I create scalable solutions 
                                    that handle millions of requests. Passionate about clean code, system optimization, and 
                                    security-first design.
                                </p>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 gap-4 mt-6">
                            <div class="flex items-center gap-2 text-sm text-neutral-400">
                                <i data-lucide="map-pin" class="w-3.5 h-3.5 text-lime-500/70"></i>
                                <span>Iran, Tehran</span>
                            </div>
                            <div class="flex items-center gap-2 text-sm text-neutral-400">
                                <i data-lucide="building-2" class="w-3.5 h-3.5 text-lime-500/70"></i>
                                <span>Freelance / Remote</span>
                            </div>
                            <div class="flex items-center gap-2 text-sm text-neutral-400">
                                <i data-lucide="graduation-cap" class="w-3.5 h-3.5 text-lime-500/70"></i>
                                <span>BSc Computer Engineering</span>
                            </div>
                            <div class="flex items-center gap-2 text-sm text-neutral-400">
                                <i data-lucide="mail" class="w-3.5 h-3.5 text-lime-500/70"></i>
                                <span>dev@network.io</span>
                            </div>
                        </div>
                    </div>

                    <!-- Current Setup -->
                    <div class="glass-panel rounded-2xl p-8 glass-panel-hover transition-all duration-300">
                        <div class="flex items-center gap-3 mb-6">
                            <i data-lucide="monitor" class="w-5 h-5 text-lime-500"></i>
                            <h3 class="text-lg font-semibold text-white">Current Setup</h3>
                        </div>
                        <div class="space-y-4">
                            <div class="flex items-center gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/5">
                                <div class="w-8 h-8 rounded-md bg-blue-500/10 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="laptop" class="w-4 h-4 text-blue-400"></i>
                                </div>
                                <div class="flex-1">
                                    <p class="text-sm font-medium text-white">Editor</p>
                                    <p class="text-xs text-neutral-500">Neovim + VS Code</p>
                                </div>
                            </div>
                            <div class="flex items-center gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/5">
                                <div class="w-8 h-8 rounded-md bg-purple-500/10 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="terminal" class="w-4 h-4 text-purple-400"></i>
                                </div>
                                <div class="flex-1">
                                    <p class="text-sm font-medium text-white">Terminal</p>
                                    <p class="text-xs text-neutral-500">Alacritty + Tmux + Zsh</p>
                                </div>
                            </div>
                            <div class="flex items-center gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/5">
                                <div class="w-8 h-8 rounded-md bg-orange-500/10 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="container" class="w-4 h-4 text-orange-400"></i>
                                </div>
                                <div class="flex-1">
                                    <p class="text-sm font-medium text-white">DevOps</p>
                                    <p class="text-xs text-neutral-500">Docker + Kubernetes + GitHub Actions</p>
                                </div>
                            </div>
                            <div class="flex items-center gap-3 p-3 rounded-lg bg-white/[0.02] border border-white/5">
                                <div class="w-8 h-8 rounded-md bg-cyan-500/10 flex items-center justify-center flex-shrink-0">
                                    <i data-lucide="cloud" class="w-4 h-4 text-cyan-400"></i>
                                </div>
                                <div class="flex-1">
                                    <p class="text-sm font-medium text-white">Cloud</p>
                                    <p class="text-xs text-neutral-500">AWS + Hetzner + Cloudflare</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section id="skills" class="py-24 px-6 fade-section">
            <div class="max-w-6xl mx-auto">
                <div class="flex items-center gap-3 mb-12">
                    <div class="w-8 h-8 rounded-lg bg-lime-500/10 flex items-center justify-center">
                        <i data-lucide="layers" class="w-4 h-4 text-lime-500"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-semibold text-white tracking-tight">Tech Stack</h2>
                    <div class="flex-1 h-px bg-gradient-to-r from-lime-500/20 to-transparent ml-4"></div>
                </div>

                <!-- Skill Categories -->
                <div class="space-y-6">
                    <!-- Backend -->
                    <div class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300">
                        <div class="flex items-center gap-3 mb-6">
                            <i data-lucide="server" class="w-5 h-5 text-lime-500"></i>
                            <h3 class="text-base font-semibold text-white">Backend Development</h3>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-3">
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🐹</div>
                                <p class="text-xs font-medium text-neutral-300">Go</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="95%"></div></div>
                            </div>
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🐍</div>
                                <p class="text-xs font-medium text-neutral-300">Python</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="90%"></div></div>
                            </div>
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🦀</div>
                                <p class="text-xs font-medium text-neutral-300">Rust</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="75%"></div></div>
                            </div>
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🟢</div>
                                <p class="text-xs font-medium text-neutral-300">Node.js</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="85%"></div></div>
                            </div>
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">☕</div>
                                <p class="text-xs font-medium text-neutral-300">Java</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="70%"></div></div>
                            </div>
                            <div class="tooltip-container group p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-lime-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🔷</div>
                                <p class="text-xs font-medium text-neutral-300">C#</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="65%"></div></div>
                            </div>
                        </div>
                    </div>

                    <!-- Network & Infrastructure -->
                    <div class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300">
                        <div class="flex items-center gap-3 mb-6">
                            <i data-lucide="network" class="w-5 h-5 text-emerald-500"></i>
                            <h3 class="text-base font-semibold text-white">Network & Infrastructure</h3>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-3">
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🌐</div>
                                <p class="text-xs font-medium text-neutral-300">TCP/IP</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="95%"></div></div>
                            </div>
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🔥</div>
                                <p class="text-xs font-medium text-neutral-300">iptables</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="88%"></div></div>
                            </div>
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🔒</div>
                                <p class="text-xs font-medium text-neutral-300">VPN/WireGuard</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="92%"></div></div>
                            </div>
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">⚖️</div>
                                <p class="text-xs font-medium text-neutral-300">HAProxy</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="85%"></div></div>
                            </div>
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🐧</div>
                                <p class="text-xs font-medium text-neutral-300">Linux</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="96%"></div></div>
                            </div>
                            <div class="p-4 rounded-xl bg-white/[0.02] border border-white/5 hover:border-emerald-500/30 transition-all duration-300 text-center cursor-default">
                                <div class="text-2xl mb-2">🐳</div>
                                <p class="text-xs font-medium text-neutral-300">Docker/K8s</p>
                                <div class="skill-bar mt-2"><div class="skill-fill" data-width="90%"></div></div>
                            </div>
                        </div>
                    </div>

                    <!-- Databases & Tools -->
                    <div class="grid md:grid-cols-2 gap-6">
                        <div class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300">
                            <div class="flex items-center gap-3 mb-6">
                                <i data-lucide="database" class="w-5 h-5 text-blue-400"></i>
                                <h3 class="text-base font-semibold text-white">Databases</h3>
                            </div>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">PostgreSQL</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">Redis</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">MongoDB</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">MySQL</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">Cassandra</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">InfluxDB</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">RabbitMQ</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-blue-500/30 transition-all cursor-default">Kafka</span>
                            </div>
                        </div>
                        <div class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300">
                            <div class="flex items-center gap-3 mb-6">
                                <i data-lucide="wrench" class="w-5 h-5 text-orange-400"></i>
                                <h3 class="text-base font-semibold text-white">Tools & Platforms</h3>
                            </div>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Git</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Prometheus</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Grafana</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Nginx</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">CI/CD</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Ansible</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Terraform</span>
                                <span class="px-3 py-1.5 rounded-lg bg-white/[0.03] border border-white/5 text-xs text-neutral-300 hover:border-orange-500/30 transition-all cursor-default">Wireshark</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="py-24 px-6 fade-section">
            <div class="max-w-6xl mx-auto">
                <div class="flex items-center gap-3 mb-12">
                    <div class="w-8 h-8 rounded-lg bg-lime-500/10 flex items-center justify-center">
                        <i data-lucide="folder-git-2" class="w-4 h-4 text-lime-500"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-semibold text-white tracking-tight">Featured Projects</h2>
                    <div class="flex-1 h-px bg-gradient-to-r from-lime-500/20 to-transparent ml-4"></div>
                </div>

                <div class="grid md:grid-cols-2 gap-6">
                    <!-- Project 1 -->
                    <div class="project-card relative glass-panel rounded-2xl overflow-hidden glass-panel-hover transition-all duration-500 group">
                        <div class="project-glow"></div>
                        <div class="relative p-6 md:p-8">
                            <div class="flex items-start justify-between mb-4">
                                <div class="w-12 h-12 rounded-xl bg-lime-500/10 flex items-center justify-center">
                                    <i data-lucide="route" class="w-6 h-6 text-lime-500"></i>
                                </div>
                                <div class="flex items-center gap-3">
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="star" class="w-3 h-3"></i>
                                        <span>24</span>
                                    </div>
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="git-fork" class="w-3 h-3"></i>
                                        <span>8</span>
                                    </div>
                                </div>
                            </div>
                            <h3 class="text-lg font-semibold text-white mb-2 group-hover:text-lime-400 transition-colors">NetRouter</h3>
                            <p class="text-sm text-neutral-400 leading-relaxed mb-4">
                                High-performance HTTP/TCP reverse proxy with dynamic routing, load balancing, and real-time health checks. Written in Go.
                            </p>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="px-2 py-1 rounded-md bg-lime-500/10 text-[10px] font-medium text-lime-400 uppercase tracking-wider">Go</span>
                                <span class="px-2 py-1 rounded-md bg-blue-500/10 text-[10px] font-medium text-blue-400 uppercase tracking-wider">TCP/IP</span>
                                <span class="px-2 py-1 rounded-md bg-purple-500/10 text-[10px] font-medium text-purple-400 uppercase tracking-wider">gRPC</span>
                            </div>
                            <div class="flex items-center gap-4">
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="external-link" class="w-3.5 h-3.5"></i>
                                    <span>Live Demo</span>
                                </a>
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="github" class="w-3.5 h-3.5"></i>
                                    <span>Source</span>
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- Project 2 -->
                    <div class="project-card relative glass-panel rounded-2xl overflow-hidden glass-panel-hover transition-all duration-500 group">
                        <div class="project-glow"></div>
                        <div class="relative p-6 md:p-8">
                            <div class="flex items-start justify-between mb-4">
                                <div class="w-12 h-12 rounded-xl bg-emerald-500/10 flex items-center justify-center">
                                    <i data-lucide="shield-check" class="w-6 h-6 text-emerald-500"></i>
                                </div>
                                <div class="flex items-center gap-3">
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="star" class="w-3 h-3"></i>
                                        <span>18</span>
                                    </div>
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="git-fork" class="w-3 h-3"></i>
                                        <span>5</span>
                                    </div>
                                </div>
                            </div>
                            <h3 class="text-lg font-semibold text-white mb-2 group-hover:text-lime-400 transition-colors">SecureGate</h3>
                            <p class="text-sm text-neutral-400 leading-relaxed mb-4">
                                Zero-trust network access controller with WireGuard integration, SSO authentication, and granular access policies.
                            </p>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="px-2 py-1 rounded-md bg-rust-500/10 text-[10px] font-medium text-orange-400 uppercase tracking-wider">Rust</span>
                                <span class="px-2 py-1 rounded-md bg-emerald-500/10 text-[10px] font-medium text-emerald-400 uppercase tracking-wider">WireGuard</span>
                                <span class="px-2 py-1 rounded-md bg-cyan-500/10 text-[10px] font-medium text-cyan-400 uppercase tracking-wider">OAuth2</span>
                            </div>
                            <div class="flex items-center gap-4">
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="external-link" class="w-3.5 h-3.5"></i>
                                    <span>Live Demo</span>
                                </a>
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="github" class="w-3.5 h-3.5"></i>
                                    <span>Source</span>
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- Project 3 -->
                    <div class="project-card relative glass-panel rounded-2xl overflow-hidden glass-panel-hover transition-all duration-500 group">
                        <div class="project-glow"></div>
                        <div class="relative p-6 md:p-8">
                            <div class="flex items-start justify-between mb-4">
                                <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center">
                                    <i data-lucide="activity" class="w-6 h-6 text-blue-400"></i>
                                </div>
                                <div class="flex items-center gap-3">
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="star" class="w-3 h-3"></i>
                                        <span>12</span>
                                    </div>
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="git-fork" class="w-3 h-3"></i>
                                        <span>3</span>
                                    </div>
                                </div>
                            </div>
                            <h3 class="text-lg font-semibold text-white mb-2 group-hover:text-lime-400 transition-colors">FlowMetrics</h3>
                            <p class="text-sm text-neutral-400 leading-relaxed mb-4">
                                Real-time network traffic analyzer and monitoring dashboard with sFlow/NetFlow support and anomaly detection.
                            </p>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="px-2 py-1 rounded-md bg-yellow-500/10 text-[10px] font-medium text-yellow-400 uppercase tracking-wider">Python</span>
                                <span class="px-2 py-1 rounded-md bg-red-500/10 text-[10px] font-medium text-red-400 uppercase tracking-wider">Kafka</span>
                                <span class="px-2 py-1 rounded-md bg-teal-500/10 text-[10px] font-medium text-teal-400 uppercase tracking-wider">ClickHouse</span>
                            </div>
                            <div class="flex items-center gap-4">
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="external-link" class="w-3.5 h-3.5"></i>
                                    <span>Live Demo</span>
                                </a>
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="github" class="w-3.5 h-3.5"></i>
                                    <span>Source</span>
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- Project 4 -->
                    <div class="project-card relative glass-panel rounded-2xl overflow-hidden glass-panel-hover transition-all duration-500 group">
                        <div class="project-glow"></div>
                        <div class="relative p-6 md:p-8">
                            <div class="flex items-start justify-between mb-4">
                                <div class="w-12 h-12 rounded-xl bg-purple-500/10 flex items-center justify-center">
                                    <i data-lucide="boxes" class="w-6 h-6 text-purple-400"></i>
                                </div>
                                <div class="flex items-center gap-3">
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="star" class="w-3 h-3"></i>
                                        <span>9</span>
                                    </div>
                                    <div class="flex items-center gap-1 text-xs text-neutral-500">
                                        <i data-lucide="git-fork" class="w-3 h-3"></i>
                                        <span>2</span>
                                    </div>
                                </div>
                            </div>
                            <h3 class="text-lg font-semibold text-white mb-2 group-hover:text-lime-400 transition-colors">MicroOrch</h3>
                            <p class="text-sm text-neutral-400 leading-relaxed mb-4">
                                Lightweight microservices orchestrator with service mesh, circuit breaking, and distributed tracing built-in.
                            </p>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="px-2 py-1 rounded-md bg-lime-500/10 text-[10px] font-medium text-lime-400 uppercase tracking-wider">Go</span>
                                <span class="px-2 py-1 rounded-md bg-purple-500/10 text-[10px] font-medium text-purple-400 uppercase tracking-wider">gRPC</span>
                                <span class="px-2 py-1 rounded-md bg-pink-500/10 text-[10px] font-medium text-pink-400 uppercase tracking-wider">etcd</span>
                            </div>
                            <div class="flex items-center gap-4">
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="external-link" class="w-3.5 h-3.5"></i>
                                    <span>Live Demo</span>
                                </a>
                                <a href="#" class="flex items-center gap-1.5 text-xs text-neutral-400 hover:text-lime-400 transition-colors">
                                    <i data-lucide="github" class="w-3.5 h-3.5"></i>
                                    <span>Source</span>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Activity / Contribution Section -->
        <section id="activity" class="py-24 px-6 fade-section">
            <div class="max-w-6xl mx-auto">
                <div class="flex items-center gap-3 mb-12">
                    <div class="w-8 h-8 rounded-lg bg-lime-500/10 flex items-center justify-center">
                        <i data-lucide="bar-chart-3" class="w-4 h-4 text-lime-500"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-semibold text-white tracking-tight">Activity & Stats</h2>
                    <div class="flex-1 h-px bg-gradient-to-r from-lime-500/20 to-transparent ml-4"></div>
                </div>

                <div class="space-y-6">
                    <!-- Contribution Graph -->
                    <div class="glass-panel rounded-2xl p-6 md:p-8">
                        <div class="flex items-center justify-between mb-6">
                            <h3 class="text-sm font-semibold text-white">Contribution Graph</h3>
                            <span class="text-[10px] text-neutral-600 font-mono">2024</span>
                        </div>
                        <div class="overflow-x-auto pb-2">
                            <div id="contribGraph" class="flex gap-[3px]" style="min-width: 700px;"></div>
                        </div>
                        <div class="flex items-center justify-end gap-2 mt-4">
                            <span class="text-[10px] text-neutral-600">Less</span>
                            <div class="contrib-cell contrib-0"></div>
                            <div class="contrib-cell contrib-1"></div>
                            <div class="contrib-cell contrib-2"></div>
                            <div class="contrib-cell contrib-3"></div>
                            <div class="contrib-cell contrib-4"></div>
                            <span class="text-[10px] text-neutral-600">More</span>
                        </div>
                    </div>

                    <!-- Stats Cards -->
                    <div class="grid md:grid-cols-2 gap-6">
                        <!-- Language Stats -->
                        <div class="glass-panel rounded-2xl p-6 md:p-8">
                            <div class="flex items-center gap-3 mb-6">
                                <i data-lucide="pie-chart" class="w-5 h-5 text-lime-500"></i>
                                <h3 class="text-sm font-semibold text-white">Most Used Languages</h3>
                            </div>
                            <div class="space-y-4">
                                <div>
                                    <div class="flex justify-between text-xs mb-1.5">
                                        <span class="text-neutral-300">Go</span>
                                        <span class="text-neutral-500 font-mono">42.3%</span>
                                    </div>
                                    <div class="h-2 rounded-full bg-white/5 overflow-hidden">
                                        <div class="h-full rounded-full bg-lime-500 transition-all duration-1000" style="width: 42.3%; box-shadow: 0 0 10px rgba(132,204,22,0.4);"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between text-xs mb-1.5">
                                        <span class="text-neutral-300">Python</span>
                                        <span class="text-neutral-500 font-mono">28.1%</span>
                                    </div>
                                    <div class="h-2 rounded-full bg-white/5 overflow-hidden">
                                        <div class="h-full rounded-full bg-blue-500 transition-all duration-1000" style="width: 28.1%;"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between text-xs mb-1.5">
                                        <span class="text-neutral-300">Rust</span>
                                        <span class="text-neutral-500 font-mono">14.7%</span>
                                    </div>
                                    <div class="h-2 rounded-full bg-white/5 overflow-hidden">
                                        <div class="h-full rounded-full bg-orange-500 transition-all duration-1000" style="width: 14.7%;"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between text-xs mb-1.5">
                                        <span class="text-neutral-300">TypeScript</span>
                                        <span class="text-neutral-500 font-mono">9.5%</span>
                                    </div>
                                    <div class="h-2 rounded-full bg-white/5 overflow-hidden">
                                        <div class="h-full rounded-full bg-cyan-500 transition-all duration-1000" style="width: 9.5%;"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between text-xs mb-1.5">
                                        <span class="text-neutral-300">Shell</span>
                                        <span class="text-neutral-500 font-mono">5.4%</span>
                                    </div>
                                    <div class="h-2 rounded-full bg-white/5 overflow-hidden">
                                        <div class="h-full rounded-full bg-purple-500 transition-all duration-1000" style="width: 5.4%;"></div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Activity SVG Graph -->
                        <div class="glass-panel rounded-2xl p-6 md:p-8">
                            <div class="flex items-center gap-3 mb-6">
                                <i data-lucide="trending-up" class="w-5 h-5 text-lime-500"></i>
                                <h3 class="text-sm font-semibold text-white">Commit Activity</h3>
                            </div>
                            <svg viewBox="0 0 400 160" class="w-full">
                                <defs>
                                    <linearGradient id="chartGrad" x1="0%" y1="0%" x2="0%" y2="100%">
                                        <stop offset="0%" style="stop-color:rgba(132,204,22,0.3)"/>
                                        <stop offset="100%" style="stop-color:rgba(132,204,22,0)"/>
                                    </linearGradient>
                                </defs>
                                <!-- Grid lines -->
                                <line x1="0" y1="40" x2="400" y2="40" stroke="rgba(255,255,255,0.03)" stroke-width="1"/>
                                <line x1="0" y1="80" x2="400" y2="80" stroke="rgba(255,255,255,0.03)" stroke-width="1"/>
                                <line x1="0" y1="120" x2="400" y2="120" stroke="rgba(255,255,255,0.03)" stroke-width="1"/>
                                <!-- Area -->
                                <path d="M0,140 L30,120 L60,100 L90,110 L120,80 L150,60 L180,70 L210,40 L240,55 L270,30 L300,45 L330,25 L360,35 L400,20 L400,160 L0,160 Z" fill="url(#chartGrad)" class="activity-line" style="stroke-dasharray:0;stroke-dashoffset:0;animation:none;"/>
                                <!-- Line -->
                                <path d="M0,140 L30,120 L60,100 L90,110 L120,80 L150,60 L180,70 L210,40 L240,55 L270,30 L300,45 L330,25 L360,35 L400,20" fill="none" stroke="#84cc16" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="activity-line"/>
                                <!-- Dots -->
                                <circle cx="270" cy="30" r="4" fill="#84cc16" style="filter: drop-shadow(0 0 6px rgba(132,204,22,0.6));"/>
                                <circle cx="330" cy="25" r="4" fill="#84cc16" style="filter: drop-shadow(0 0 6px rgba(132,204,22,0.6));"/>
                                <circle cx="400" cy="20" r="4" fill="#84cc16" style="filter: drop-shadow(0 0 6px rgba(132,204,22,0.6));"/>
                                <!-- Labels -->
                                <text x="0" y="155" fill="#525252" font-size="8" font-family="Inter">Jan</text>
                                <text x="60" y="155" fill="#525252" font-size="8" font-family="Inter">Mar</text>
                                <text x="120" y="155" fill="#525252" font-size="8" font-family="Inter">May</text>
                                <text x="180" y="155" fill="#525252" font-size="8" font-family="Inter">Jul</text>
                                <text x="240" y="155" fill="#525252" font-size="8" font-family="Inter">Sep</text>
                                <text x="300" y="155" fill="#525252" font-size="8" font-family="Inter">Nov</text>
                                <text x="370" y="155" fill="#525252" font-size="8" font-family="Inter">Dec</text>
                            </svg>
                        </div>
                    </div>

                    <!-- Recent Activity Timeline -->
                    <div class="glass-panel rounded-2xl p-6 md:p-8">
                        <div class="flex items-center gap-3 mb-6">
                            <i data-lucide="clock" class="w-5 h-5 text-lime-500"></i>
                            <h3 class="text-sm font-semibold text-white">Recent Activity</h3>
                        </div>
                        <div class="space-y-0">
                            <div class="flex items-start gap-4 py-3 border-l-2 border-lime-500/20 pl-4 relative">
                                <div class="absolute left-0 top-1/2 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-lime-500 border-2 border-neutral-900"></div>
                                <div class="flex-1">
                                    <div class="flex items-center gap-2 mb-1">
                                        <i data-lucide="git-commit" class="w-3.5 h-3.5 text-lime-500"></i>
                                        <span class="text-xs text-neutral-300 font-medium">Pushed 3 commits to NetRouter</span>
                                    </div>
                                    <p class="text-[10px] text-neutral-600 font-mono">feat: add WebSocket proxy support — 2 hours ago</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 py-3 border-l-2 border-emerald-500/20 pl-4 relative">
                                <div class="absolute left-0 top-1/2 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-emerald-500 border-2 border-neutral-900"></div>
                                <div class="flex-1">
                                    <div class="flex items-center gap-2 mb-1">
                                        <i data-lucide="git-pull-request" class="w-3.5 h-3.5 text-emerald-500"></i>
                                        <span class="text-xs text-neutral-300 font-medium">Merged PR #42 in SecureGate</span>
                                    </div>
                                    <p class="text-[10px] text-neutral-600 font-mono">fix: wireguard key rotation race condition — 5 hours ago</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 py-3 border-l-2 border-blue-500/20 pl-4 relative">
                                <div class="absolute left-0 top-1/2 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-blue-500 border-2 border-neutral-900"></div>
                                <div class="flex-1">
                                    <div class="flex items-center gap-2 mb-1">
                                        <i data-lucide="code-2" class="w-3.5 h-3.5 text-blue-400"></i>
                                        <span class="text-xs text-neutral-300 font-medium">Created repo FlowMetrics v2</span>
                                    </div>
                                    <p class="text-[10px] text-neutral-600 font-mono">init: real-time traffic analyzer — 1 day ago</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 py-3 border-l-2 border-purple-500/20 pl-4 relative">
                                <div class="absolute left-0 top-1/2 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-purple-500 border-2 border-neutral-900"></div>
                                <div class="flex-1">
                                    <div class="flex items-center gap-2 mb-1">
                                        <i data-lucide="star" class="w-3.5 h-3.5 text-purple-400"></i>
                                        <span class="text-xs text-neutral-300 font-medium">Starred cilium/cilium</span>
                                    </div>
                                    <p class="text-[10px] text-neutral-600 font-mono">eBPF-based networking — 2 days ago</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4 py-3 border-l-2 border-white/5 pl-4 relative">
                                <div class="absolute left-0 top-1/2 -translate-x-1/2 w-2.5 h-2.5 rounded-full bg-orange-500 border-2 border-neutral-900"></div>
                                <div class="flex-1">
                                    <div class="flex items-center gap-2 mb-1">
                                        <i data-lucide="git-commit" class="w-3.5 h-3.5 text-orange-400"></i>
                                        <span class="text-xs text-neutral-300 font-medium">Pushed 7 commits to MicroOrch</span>
                                    </div>
                                    <p class="text-[10px] text-neutral-600 font-mono">refactor: circuit breaker implementation — 3 days ago</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Connect Section -->
        <section id="connect" class="py-24 px-6 fade-section">
            <div class="max-w-6xl mx-auto">
                <div class="flex items-center gap-3 mb-12">
                    <div class="w-8 h-8 rounded-lg bg-lime-500/10 flex items-center justify-center">
                        <i data-lucide="link" class="w-4 h-4 text-lime-500"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-semibold text-white tracking-tight">Let's Connect</h2>
                    <div class="flex-1 h-px bg-gradient-to-r from-lime-500/20 to-transparent ml-4"></div>
                </div>

                <div class="grid md:grid-cols-3 gap-6">
                    <!-- GitHub -->
                    <a href="#" class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300 group text-center">
                        <div class="w-14 h-14 rounded-xl bg-white/5 flex items-center justify-center mx-auto mb-4 group-hover:bg-lime-500/10 transition-colors">
                            <i data-lucide="github" class="w-7 h-7 text-neutral-400 group-hover:text-lime-400 transition-colors"></i>
                        </div>
                        <h3 class="text-base font-semibold text-white mb-1">GitHub</h3>
                        <p class="text-xs text-neutral-500">@devuser</p>
                    </a>

                    <!-- LinkedIn -->
                    <a href="#" class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300 group text-center">
                        <div class="w-14 h-14 rounded-xl bg-white/5 flex items-center justify-center mx-auto mb-4 group-hover:bg-blue-500/10 transition-colors">
                            <i data-lucide="linkedin" class="w-7 h-7 text-neutral-400 group-hover:text-blue-400 transition-colors"></i>
                        </div>
                        <h3 class="text-base font-semibold text-white mb-1">LinkedIn</h3>
                        <p class="text-xs text-neutral-500">in/devuser</p>
                    </a>

                    <!-- Email/Telegram -->
                    <a href="#" class="glass-panel rounded-2xl p-6 md:p-8 glass-panel-hover transition-all duration-300 group text-center">
                        <div class="w-14 h-14 rounded-xl bg-white/5 flex items-center justify-center mx-auto mb-4 group-hover:bg-sky-500/10 transition-colors">
                            <i data-lucide="send" class="w-7 h-7 text-neutral-400 group-hover:text-sky-400 transition-colors"></i>
                        </div>
                        <h3 class="text-base font-semibold text-white mb-1">Telegram</h3>
                        <p class="text-xs text-neutral-500">@devuser</p>
                    </a>
                </div>

                <!-- CTA -->
                <div class="mt-12 text-center">
                    <div class="glass-panel rounded-2xl p-8 md:p-12 max-w-2xl mx-auto relative overflow-hidden">
                        <div class="absolute inset-0 bg-gradient-to-br from-lime-500/5 to-emerald-500/5"></div>
                        <div class="relative">
                            <div class="font-mono text-sm mb-4">
                                <span class="code-comment">// open to collaborate</span>
                            </div>
                            <p class="text-lg md:text-xl text-white font-medium mb-2">Interested in network & backend projects?</p>
                            <p class="text-sm text-neutral-400 mb-6">I'm always open to discussing new projects, creative ideas, or opportunities to be part of your vision.</p>
                            <a href="mailto:dev@network.io" class="inline-flex items-center gap-2 bg-lime-600 hover:bg-lime-500 text-black text-sm font-bold px-8 py-3.5 rounded-xl transition-all duration-300 uppercase tracking-wider" style="box-shadow: 0 0 20px rgba(132,204,22,0.3);">
                                <i data-lucide="mail" class="w-4 h-4"></i>
                                Get In Touch
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="py-12 px-6 border-t border-white/5">
            <div class="max-w-6xl mx-auto text-center">
                <div class="flex items-center justify-center gap-2 mb-4">
                    <i data-lucide="terminal" class="w-4 h-4 text-lime-500"></i>
                    <span class="text-sm font-semibold text-white tracking-tight">dev.profile</span>
                </div>
                <p class="text-xs text-neutral-600 font-mono">
                    Built with <span class="text-lime-500">♥</span> and lots of <span class="text-neutral-500">caffeine</span>
                </p>
                <p class="text-[10px] text-neutral-700 font-mono mt-2">
                    © 2024 — Designed for GitHub README
                </p>
            </div>
        </footer>
    </main>

    <script>
        // Initialize Lucide Icons
        lucide.createIcons();

        // Contribution Graph Generator
        function generateContribGraph() {
            const container = document.getElementById('contribGraph');
            const weeks = 52;
            const days = 7;
            
            for (let w = 0; w < weeks; w++) {
                const weekDiv = document.createElement('div');
                weekDiv.className = 'flex flex-col gap-[3px]';
                
                for (let d = 0; d < days; d++) {
                    const cell = document.createElement('div');
                    const rand = Math.random();
                    let level;
                    if (rand < 0.35) level = 0;
                    else if (rand < 0.55) level = 1;
                    else if (rand < 0.75) level = 2;
                    else if (rand < 0.9) level = 3;
                    else level = 4;
                    
                    cell.className = `contrib-cell contrib-${level} tooltip-container`;
                    cell.innerHTML = `<span class="tooltip-text">${Math.floor(Math.random() * 12)} contributions</span>`;
                    weekDiv.appendChild(cell);
                }
                container.appendChild(weekDiv);
            }
        }
        generateContribGraph();

        // Counter Animation
        function animateCounters() {
            const counters = document.querySelectorAll('.stat-number[data-target]');
            counters.forEach(counter => {
                const target = parseInt(counter.getAttribute('data-target'));
                const duration = 2000;
                const start = performance.now();
                
                function update(now) {
                    const elapsed = now - start;
                    const progress = Math.min(elapsed / duration, 1);
                    const eased = 1 - Math.pow(1 - progress, 3);
                    counter.textContent = Math.floor(target * eased).toLocaleString();
                    
                    if (progress < 1) {
                        requestAnimationFrame(update);
                    } else {
                        counter.textContent = target.toLocaleString();
                    }
                }
                requestAnimationFrame(update);
            });
        }

        // Skill Bar Animation
        function animateSkillBars() {
            const skillFills = document.querySelectorAll('.skill-fill[data-width]');
            skillFills.forEach((fill, index) => {
                setTimeout(() => {
                    fill.style.width = fill.getAttribute('data-width');
                    fill.classList.add('animated');
                }, index * 100);
            });
        }

        // Scroll Animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    
                    // Trigger skill bars when skills section visible
                    if (entry.target.id === 'skills' || entry.target.querySelector('.skill-fill')) {
                        setTimeout(animateSkillBars, 300);
                    }
                }
            });
        }, { threshold: 0.1 });

        document.querySelectorAll('.fade-section').forEach(section => {
            observer.observe(section);
        });

        // Active Nav Link
        const navLinks = document.querySelectorAll('.nav-link');
        const sections = document.querySelectorAll('section[id]');

        window.addEventListener('scroll', () => {
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop - 100;
                if (scrollY >= sectionTop) {
                    current = section.getAttribute('id');
                }
            });
            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === `#${current}`) {
                    link.classList.add('active');
                }
            });
        });

        // Start counter animation on load
        setTimeout(animateCounters, 500);

        // Smooth scroll for nav links
        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const targetId = link.getAttribute('href');
                const target = document.querySelector(targetId);
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });
    </script>
</body>
</html>
