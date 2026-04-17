<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>CT241 - Portail Logistique Gabon</title>
    
    <!-- Meta tags pour PWA -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="CT241 Gabon">
    <meta name="theme-color" content="#36a100">
    
    <!-- Favicon et Icônes -->
    <link rel="icon" type="image/png" href="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png">
    <link rel="apple-touch-icon" href="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png">

    <!-- Manifeste PWA amélioré -->
    <script>
        const manifest = {
            "name": "CT241 - Logistique Gabon",
            "short_name": "CT241",
            "description": "Portail logistique premium aux couleurs du Gabon",
            "start_url": "./index.html",
            "display": "standalone",
            "background_color": "#ffffff",
            "theme_color": "#36a100",
            "icons": [
                {
                    "src": "https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png",
                    "sizes": "192x192",
                    "type": "image/png",
                    "purpose": "any maskable"
                },
                {
                    "src": "https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png",
                    "sizes": "512x512",
                    "type": "image/png",
                    "purpose": "any"
                }
            ],
            "screenshots": [
                {
                    "src": "https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png",
                    "sizes": "1024x1024",
                    "type": "image/png",
                    "form_factor": "wide",
                    "label": "Dashboard CT241 Gabon"
                }
            ]
        };
        const stringManifest = JSON.stringify(manifest);
        const blob = new Blob([stringManifest], {type: 'application/json'});
        const manifestURL = URL.createObjectURL(blob);
        const link = document.createElement('link');
        link.rel = 'manifest';
        link.href = manifestURL;
        document.head.appendChild(link);
    </script>

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gabon: {
                            green: '#36a100', // Vert drapeau
                            yellow: '#ffcf00', // Jaune drapeau
                            blue: '#007fff',   // Bleu drapeau
                        },
                        ct241: {
                            dark: '#1a1a1a'
                        }
                    }
                }
            }
        }
    </script>

    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.7s ease-out forwards;
        }
        .gabon-gradient {
            background: linear-gradient(135deg, #36a100 0%, #ffcf00 50%, #007fff 100%);
        }
        .gabon-border {
            border-image: linear-gradient(to right, #36a100, #ffcf00, #007fff) 1;
        }
        body {
            -webkit-tap-highlight-color: transparent;
            user-select: none;
        }
        .logo-glow {
            box-shadow: 0 0 20px rgba(54, 161, 0, 0.3);
        }
    </style>
</head>
<body class="bg-slate-50 font-sans text-slate-900 overflow-x-hidden">

    <!-- Splash Screen aux couleurs du Gabon -->
    <div id="loader" class="fixed inset-0 bg-white z-[100] flex flex-col items-center justify-center p-6 transition-opacity duration-700">
        <div class="w-full max-w-md text-center">
            <div class="mb-10 animate-pulse">
                <img src="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png" alt="Logo CT241" class="w-36 h-36 object-contain mx-auto rounded-3xl logo-glow">
            </div>
            <h2 class="text-3xl font-black mb-1 tracking-tighter">
                <span class="text-gabon-green">CT</span><span class="text-gabon-yellow">2</span><span class="text-gabon-blue">41</span>
            </h2>
            <p id="loading-message" class="text-slate-400 mb-8 text-xs font-bold tracking-[0.2em] uppercase">Bienvenue au Gabon</p>
            
            <!-- Barre de progression tricolore -->
            <div class="w-full bg-slate-100 rounded-full h-2 mb-4 overflow-hidden max-w-[280px] mx-auto flex">
                <div id="progress-bar-green" class="h-full w-0 bg-gabon-green transition-all duration-300"></div>
                <div id="progress-bar-yellow" class="h-full w-0 bg-gabon-yellow transition-all duration-300"></div>
                <div id="progress-bar-blue" class="h-full w-0 bg-gabon-blue transition-all duration-300"></div>
            </div>
            <p id="progress-text" class="text-slate-400 text-[10px] font-mono font-bold">SYSTÈME EN COURS...</p>
        </div>
    </div>

    <!-- Bannière d'installation stylisée -->
    <div id="install-banner" class="fixed bottom-8 left-6 right-6 gabon-gradient p-0.5 rounded-3xl shadow-2xl z-[60] hidden animate-fade-in">
        <div class="bg-white p-4 rounded-[1.4rem] flex items-center justify-between">
            <div class="flex items-center gap-4">
                <div class="bg-slate-50 p-1.5 rounded-xl border border-slate-100">
                    <img src="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png" class="w-10 h-10 object-contain">
                </div>
                <div>
                    <p class="font-black text-slate-800 text-sm">Installer CT241</p>
                    <p class="text-[10px] text-slate-400 font-bold uppercase tracking-wider">L'app officielle du Gabon</p>
                </div>
            </div>
            <button id="btn-install" class="gabon-gradient text-white px-5 py-2.5 rounded-xl text-xs font-black shadow-lg active:scale-95 transition-all">
                INSTALLER
            </button>
        </div>
    </div>

    <!-- Modal de Bienvenue Gabon -->
    <div id="tuto-modal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-900/60 backdrop-blur-xl transition-all">
        <div class="bg-white rounded-[3rem] max-w-lg w-full shadow-2xl overflow-hidden scale-95 transition-transform duration-500">
            <div class="p-10 text-center">
                <div class="mb-6 relative inline-block">
                    <img src="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png" class="w-24 h-24 object-contain mx-auto rounded-2xl logo-glow relative z-10">
                    <div class="absolute -inset-2 gabon-gradient blur-xl opacity-20"></div>
                </div>
                
                <h3 class="text-3xl font-black text-slate-800 tracking-tight mb-2">Bienvenue au Gabon</h3>
                <p class="text-slate-500 text-sm font-medium mb-8">Votre partenaire logistique national de confiance.</p>

                <div class="grid grid-cols-3 gap-3 mb-10">
                    <div class="p-4 bg-emerald-50 rounded-2xl border border-emerald-100">
                        <i data-lucide="shield-check" class="w-6 h-6 mx-auto text-gabon-green mb-2"></i>
                        <p class="text-[9px] font-black text-emerald-800 uppercase">Sécurité</p>
                    </div>
                    <div class="p-4 bg-amber-50 rounded-2xl border border-amber-100">
                        <i data-lucide="zap" class="w-6 h-6 mx-auto text-gabon-yellow mb-2"></i>
                        <p class="text-[9px] font-black text-amber-800 uppercase">Vitesse</p>
                    </div>
                    <div class="p-4 bg-blue-50 rounded-2xl border border-blue-100">
                        <i data-lucide="map-pin" class="w-6 h-6 mx-auto text-gabon-blue mb-2"></i>
                        <p class="text-[9px] font-black text-blue-800 uppercase">Local</p>
                    </div>
                </div>

                <button onclick="closeTuto()" class="w-full gabon-gradient text-white py-5 rounded-2xl font-black text-sm tracking-widest shadow-xl shadow-blue-500/20 active:scale-95 transition-all">
                    DÉMARRER L'EXPÉRIENCE
                </button>
            </div>
        </div>
    </div>

    <!-- Contenu Principal -->
    <div id="main-content" class="invisible">
        <header class="bg-white/80 backdrop-blur-md border-b border-slate-100 py-5 px-8 mb-8 sticky top-0 z-40">
            <div class="max-w-6xl mx-auto flex items-center justify-between">
                <div class="flex items-center gap-4">
                    <div class="p-1 gabon-gradient rounded-xl">
                        <img src="https://i.ibb.co/xKY76DgR/Gemini-Generated-Image-1pvtp31pvtp31pvt-1.png" alt="Logo" class="w-10 h-10 object-contain rounded-lg bg-white p-0.5">
                    </div>
                    <h1 class="text-xl font-black tracking-tighter">
                        <span class="text-gabon-green">CT</span><span class="text-gabon-yellow">2</span><span class="text-gabon-blue">41</span>
                    </h1>
                </div>
                <div class="flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-gabon-green animate-pulse"></span>
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-widest">Connecté</span>
                </div>
            </div>
        </header>

        <main class="max-w-6xl mx-auto px-6 pb-28 animate-fade-in">
            <div class="mb-12">
                <h2 class="text-3xl font-black text-slate-900 tracking-tight mb-2">Services <span class="text-gabon-green">Premium</span></h2>
                <div class="h-1 w-20 gabon-gradient rounded-full"></div>
            </div>

            <div id="apps-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Cartes injectées par JS -->
            </div>
        </main>

        <!-- Navigation mobile flottante style "GABON" -->
        <div class="fixed bottom-6 left-1/2 -translate-x-1/2 w-[90%] max-w-md bg-white/90 backdrop-blur-lg border border-slate-200/50 rounded-full px-8 py-4 flex justify-between items-center shadow-2xl z-40 md:hidden">
            <div class="text-gabon-green flex flex-col items-center gap-1">
                <div class="bg-gabon-green/10 p-2 rounded-full"><i data-lucide="layout-grid" class="w-5 h-5"></i></div>
            </div>
            <div class="text-slate-300 flex flex-col items-center gap-1">
                <i data-lucide="package" class="w-6 h-6"></i>
            </div>
            <div class="text-slate-300 flex flex-col items-center gap-1" onclick="openTuto()">
                <i data-lucide="info" class="w-6 h-6"></i>
            </div>
        </div>
    </div>

    <script>
        // PWA - Enregistrement Service Worker
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                const swCode = `
                    self.addEventListener('install', (e) => self.skipWaiting());
                    self.addEventListener('fetch', (e) => e.respondWith(fetch(e.request)));
                `;
                const blob = new Blob([swCode], { type: 'text/javascript' });
                navigator.serviceWorker.register(URL.createObjectURL(blob));
            });
        }

        const apps = [
            { 
                title: "Commander", 
                url: "https://newsmiley21-star.github.io/commandes.html", 
                icon: "shopping-bag", 
                color: "text-gabon-blue", 
                bg: "bg-blue-50", 
                desc: "Gestion des flux de commandes nationales." 
            },
            { 
                title: "Reservé au personnel", 
                url: "https://newsmiley21-star.github.io/livraison.index.html", 
                icon: "truck", 
                color: "text-gabon-green", 
                bg: "bg-emerald-50", 
                desc: "Traitement et Suivi des expéditions à travers le Gabon." 
            }, 
            { 
                title: "Reservé au personnel", 
                url: "https://newsmiley21-star.github.io/index.html/#suivi-des-gains", 
                icon: "motorbike", 
                color: "text-gabon-yellow", 
                bg: "bg-blue-50", 
                desc: "Gestion des livraisons express ... " 
            },
            { 
                title: "comptabilité & management", 
                url: "https://newsmiley21-star.github.io/suivi-des-performances-/", 
                icon: "trending-up", 
                color: "text-gabon-yellow", 
                bg: "bg-amber-50", 
                desc: "Analytiques et performances logistiques." 
            }
        ];

        let deferredPrompt;
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('install-banner').classList.remove('hidden');
        });

        document.getElementById('btn-install').addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') document.getElementById('install-banner').classList.add('hidden');
                deferredPrompt = null;
            }
        });

        function initGrid() {
            const grid = document.getElementById('apps-grid');
            grid.innerHTML = apps.map(app => `
                <a href="${app.url}" class="group block bg-white border border-slate-100 rounded-[2.5rem] p-8 shadow-sm transition-all duration-500 hover:shadow-2xl hover:border-gabon-yellow/20 hover:-translate-y-2 relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-32 h-32 gabon-gradient opacity-0 group-hover:opacity-5 transition-opacity blur-3xl"></div>
                    <div class="flex items-center gap-6 relative z-10">
                        <div class="${app.bg} ${app.color} w-20 h-20 rounded-3xl flex items-center justify-center shadow-inner group-hover:scale-110 transition-transform duration-500">
                            <i data-lucide="${app.icon}" class="w-10 h-10"></i>
                        </div>
                        <div class="flex-1">
                            <h3 class="font-black text-slate-900 text-xl tracking-tight leading-tight">${app.title}</h3>
                            <p class="text-[11px] text-slate-400 font-bold uppercase tracking-wide mt-1">${app.desc}</p>
                        </div>
                    </div>
                </a>
            `).join('');
            lucide.createIcons();
        }

        function startLoading() {
            const barG = document.getElementById('progress-bar-green');
            const barY = document.getElementById('progress-bar-yellow');
            const barB = document.getElementById('progress-bar-blue');
            const text = document.getElementById('progress-text');
            let p = 0;
            const int = setInterval(() => {
                p += 4;
                if (p >= 100) {
                    p = 100;
                    clearInterval(int);
                    setTimeout(finishLoading, 600);
                }
                
                // On remplit les barres successivement pour simuler le drapeau
                if(p <= 33) barG.style.width = (p * 3) + '%';
                else if(p <= 66) {
                    barG.style.width = '100%';
                    barY.style.width = ((p - 33) * 3) + '%';
                } else {
                    barY.style.width = '100%';
                    barB.style.width = ((p - 66) * 3) + '%';
                }
                
                text.innerText = p + '% - CHARGEMENT GABON';
            }, 80);
        }

        function finishLoading() {
            const loader = document.getElementById('loader');
            loader.style.opacity = '0';
            setTimeout(() => {
                loader.style.display = 'none';
                document.getElementById('main-content').classList.remove('invisible');
                if(!localStorage.getItem('gabon_pwa_v1')) {
                    openTuto();
                    localStorage.setItem('gabon_pwa_v1', 'true');
                }
            }, 700);
        }

        function openTuto() {
            const m = document.getElementById('tuto-modal');
            m.classList.replace('hidden', 'flex');
        }

        function closeTuto() {
            const m = document.getElementById('tuto-modal');
            m.classList.replace('flex', 'hidden');
        }

        window.onload = () => {
            initGrid();
            startLoading();
        };
    </script>
</body>
</html>
