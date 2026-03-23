import React, { useState, useEffect } from 'react';
import { 
  ShoppingCart, 
  Truck,  
  TrendingUp, 
  ArrowRight, 
  LayoutDashboard, 
  Loader2, 
  Info, 
  X,
  MousePointerClick,
  Monitor
} from 'lucide-react';

const App = () => {
  const [loading, setLoading] = useState(true);
  const [loadingProgress, setLoadingProgress] = useState(0);
  const [loadingMessage, setLoadingMessage] = useState("Démarrage du système...");
  const [showTuto, setShowTuto] = useState(false);

  // Configuration des applications cibles
  const apps = [
    {
      title: "Portail des Commandes",
      description: "Gérer et visualiser l'ensemble des commandes clients en temps réel.",
      url: "https://newsmiley21-star.github.io/commandes.html",
      icon: <ShoppingCart size={32} />,
      color: "bg-blue-600",
    },
    {
      title: "Service Livraison",
      description: "Suivi logistique, planification des trajets et états de livraison.",
      url: "https://newsmiley21-star.github.io/livraison.index.html",
      icon: <Truck size={32} />,
      color: "bg-emerald-600",
    },
    {
      title: "Espace Personnel",
      description: "Accès réservé au personnel : suivi des gains et performances.",
      url: "https://newsmiley21-star.github.io/index.html#suivi-des-gains",
      icon: <TrendingUp size={32} />,
      color: "bg-amber-600",
    }
  ];

  // Simulation du chargement
  useEffect(() => {
    const messages = [
      "Connexion aux serveurs...",
      "Sécurisation de la liaison...",
      "Chargement des modules de gestion...",
      "Finalisation de l'interface..."
    ];
    
    let progress = 0;
    const interval = setInterval(() => {
      progress += Math.random() * 15;
      if (progress >= 100) {
        progress = 100;
        clearInterval(interval);
        setTimeout(() => {
          setLoading(false);
          setShowTuto(true); // Afficher le tuto après le chargement
        }, 500);
      }
      setLoadingProgress(progress);
      setLoadingMessage(messages[Math.floor((progress / 100) * messages.length)] || messages[messages.length - 1]);
    }, 300);

    return () => clearInterval(interval);
  }, []);

  // Écran de chargement
  if (loading) {
    return (
      <div className="min-h-screen bg-slate-900 flex flex-col items-center justify-center p-6">
        <div className="w-full max-w-md text-center">
          <div className="bg-indigo-600 w-16 h-16 rounded-2xl flex items-center justify-center text-white mx-auto mb-8 animate-pulse shadow-lg shadow-indigo-500/20">
            <LayoutDashboard size={32} />
          </div>
          <h2 className="text-white text-xl font-bold mb-2">Système de Gestion</h2>
          <p className="text-slate-400 mb-8 text-sm italic">{loadingMessage}</p>
          
          <div className="w-full bg-slate-800 rounded-full h-2 mb-4 overflow-hidden">
            <div 
              className="bg-indigo-500 h-full transition-all duration-300 ease-out"
              style={{ width: `${loadingProgress}%` }}
            ></div>
          </div>
          <p className="text-slate-500 text-xs font-mono">{Math.round(loadingProgress)}%</p>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-slate-50 font-sans text-slate-900 animate-in fade-in duration-700">
      
      {/* Modal Tuto / Bienvenue */}
      {showTuto && (
        <div className="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-sm animate-in fade-in duration-300">
          <div className="bg-white rounded-3xl max-w-lg w-full shadow-2xl overflow-hidden animate-in zoom-in-95 duration-300">
            <div className="p-8">
              <div className="flex justify-between items-start mb-6">
                <div>
                  <h3 className="text-2xl font-bold text-slate-800">Bienvenue, Utilisateur</h3>
                  <p className="text-slate-500 text-sm">Guide rapide d'utilisation du portail</p>
                </div>
                <button 
                  onClick={() => setShowTuto(false)}
                  className="p-2 hover:bg-slate-100 rounded-full transition-colors"
                >
                  <X size={20} />
                </button>
              </div>

              <div className="space-y-6 mb-8">
                <div className="flex gap-4">
                  <div className="bg-blue-100 p-3 rounded-xl text-blue-600 h-fit">
                    <Monitor size={20} />
                  </div>
                  <div>
                    <h4 className="font-semibold text-slate-800">Interface Centralisée</h4>
                    <p className="text-sm text-slate-600">Accédez à tous vos services depuis un seul écran sans changer d'URL.</p>
                  </div>
                </div>
                <div className="flex gap-4">
                  <div className="bg-emerald-100 p-3 rounded-xl text-emerald-600 h-fit">
                    <MousePointerClick size={20} />
                  </div>
                  <div>
                    <h4 className="font-semibold text-slate-800">Accès Direct</h4>
                    <p className="text-sm text-slate-600">Cliquez sur une carte pour être redirigé vers le module spécifique.</p>
                  </div>
                </div>
                <div className="flex gap-4">
                  <div className="bg-amber-100 p-3 rounded-xl text-amber-600 h-fit">
                    <Info size={20} />
                  </div>
                  <div>
                    <h4 className="font-semibold text-slate-800">Suivi en Temps Réel</h4>
                    <p className="text-sm text-slate-600">Les données sont synchronisées avec le serveur CT241.</p>
                  </div>
                </div>
              </div>

              <button 
                onClick={() => setShowTuto(false)}
                className="w-full bg-indigo-600 text-white py-4 rounded-xl font-bold hover:bg-indigo-700 transition-colors shadow-lg shadow-indigo-200"
              >
                Compris, c'est parti !
              </button>
            </div>
          </div>
        </div>
      )}

      {/* Header */}
      <header className="bg-white border-b border-slate-200 py-6 px-4 mb-8 shadow-sm">
        <div className="max-w-6xl mx-auto flex items-center justify-between">
          <div className="flex items-center gap-3">
            <div className="bg-indigo-600 p-2 rounded-lg text-white">
              <LayoutDashboard size={24} />
            </div>
            <h1 className="text-2xl font-bold tracking-tight text-slate-800">
              Système de Gestion Intégré
            </h1>
          </div>
          <button 
            onClick={() => setShowTuto(true)}
            className="flex items-center gap-2 text-sm font-medium text-slate-500 hover:text-indigo-600 transition-colors bg-slate-100 px-4 py-2 rounded-lg"
          >
            <Info size={16} /> Aide
          </button>
        </div>
      </header>

      <main className="max-w-6xl mx-auto px-4 pb-12">
        <div className="mb-10 text-center md:text-left">
          <h2 className="text-xl font-semibold text-slate-700 mb-2">Acceuil principal</h2>
          <p className="text-slate-500">Sélectionnez le module opérationnel nécessaire.</p>
        </div>

        {/* Grille des applications */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {apps.map((app, index) => (
            <a 
              key={index}
              href={app.url}
              className="group block bg-white border border-slate-200 rounded-3xl p-6 shadow-sm transition-all duration-500 hover:shadow-2xl hover:border-transparent hover:-translate-y-2"
            >
              <div className="flex flex-col h-full">
                <div className={`${app.color} w-14 h-14 rounded-2xl flex items-center justify-center text-white mb-6 shadow-lg shadow-current/10 transition-transform group-hover:scale-110 group-hover:rotate-3`}>
                  {app.icon}
                </div>
                
                <h3 className="text-xl font-bold mb-3 text-slate-800 group-hover:text-indigo-600 transition-colors">
                  {app.title}
                </h3>
                
                <p className="text-slate-500 text-sm leading-relaxed mb-8">
                  {app.description}
                </p>

                <div className="mt-auto flex items-center text-sm font-bold text-indigo-600 gap-2 opacity-0 group-hover:opacity-100 translate-x-[-10px] group-hover:translate-x-0 transition-all duration-300">
                  Lancer l'application <ArrowRight size={16} />
                </div>
              </div>
            </a>
          ))}
        </div>

        {/* Footer info */}
        <div className="mt-16 pt-8 border-t border-slate-200 text-center">
          <p className="text-xs text-slate-400 uppercase tracking-widest font-medium">
            Interface de Navigation Unifiée • Session Active
          </p>
        </div>
      </main>
    </div>
  );
};

export default App;
