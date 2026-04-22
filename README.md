import React, { useState } from 'react';

const App = () => {
  const [filter, setFilter] = useState('TOUS');
  const [selectedProduct, setSelectedProduct] = useState(null);
  const [activeTab, setActiveTab] = useState('PHONES');
  const [showLegal, setShowLegal] = useState(false);
  
  const [appointmentStep, setAppointmentStep] = useState('IDLE');
  const [appointmentData, setAppointmentData] = useState({
    model: '',
    service: 'Écran',
    time: '10:00'
  });

  const inventory = [
    { id: 1, name: "Samsung Galaxy S25", price: "579€", brand: "SAMSUNG", specs: "Neuf - Garantie 6 mois", promo: true },
    { id: 2, name: "Samsung Galaxy S24 Ultra", price: "689€", brand: "SAMSUNG", specs: "Titane - Garantie 6 mois", promo: false },
    { id: 3, name: "Samsung Galaxy S24 FE", price: "389€", brand: "SAMSUNG", specs: "128 Go - Garantie 6 mois", promo: true },
    { id: 4, name: "Samsung Galaxy A55 5G", price: "319€", brand: "SAMSUNG", specs: "256 Go - Garantie 6 mois", promo: false },
    { id: 5, name: "Samsung Galaxy A35 5G", price: "249€", brand: "SAMSUNG", specs: "128 Go - Garantie 6 mois", promo: false },
    { id: 6, name: "Samsung Galaxy A25 5G", price: "219€", brand: "SAMSUNG", specs: "AMOLED - Garantie 6 mois", promo: false },
    { id: 7, name: "Redmi Note 13 Pro 5G", price: "259€", brand: "XIAOMI", specs: "200MP - Garantie 6 mois", promo: false },
    { id: 8, name: "Honor 200 Lite", price: "199€", brand: "HONOR", specs: "256 Go - Garantie 6 mois", promo: true },
    { id: 9, name: "Honor X8b", price: "179€", brand: "HONOR", specs: "Ultra-mince - Garantie 6 mois", promo: false },
    { id: 10, name: "Redmi Note 13", price: "169€", brand: "XIAOMI", specs: "Garantie 6 mois", promo: true },
    { id: 11, name: "Samsung Galaxy M15 5G", price: "169€", brand: "SAMSUNG", specs: "6000mAh - Garantie 6 mois", promo: true },
    { id: 12, name: "Samsung Galaxy A16 5G", price: "159€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: false },
    { id: 13, name: "Oppo A58", price: "159€", brand: "OPPO", specs: "128 Go - Garantie 6 mois", promo: false },
    { id: 14, name: "Honor 90 Smart 5G", price: "149€", brand: "HONOR", specs: "Garantie 6 mois", promo: false },
    { id: 15, name: "Samsung Galaxy A15", price: "139€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: false },
    { id: 16, name: "Oppo A38", price: "129€", brand: "OPPO", specs: "Garantie 6 mois", promo: false },
    { id: 17, name: "Samsung Galaxy A05s", price: "129€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: false },
    { id: 18, name: "Samsung Galaxy A06", price: "119€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: false },
    { id: 19, name: "Oppo A18", price: "109€", brand: "OPPO", specs: "Garantie 6 mois", promo: true },
    { id: 20, name: "Samsung Galaxy A05", price: "109€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: false },
    { id: 21, name: "Redmi 13C", price: "109€", brand: "XIAOMI", specs: "Garantie 6 mois", promo: false },
    { id: 22, name: "Samsung Galaxy A07", price: "95€", brand: "SAMSUNG", specs: "Garantie 6 mois", promo: true },
    { id: 23, name: "Redmi A3", price: "89€", brand: "XIAOMI", specs: "Garantie 6 mois", promo: false },
    { id: 24, name: "Logicom Le Kay", price: "29€", brand: "AUTRES", specs: "Clavier - Garantie 6 mois", promo: false }
  ];

  const repairExpertise = [
    { 
      category: "ÉLECTRONIQUE & MATÉRIEL", 
      items: [
        { name: "Écrans & Vitres Tactiles", desc: "Original ou Compatible haute qualité" },
        { name: "Batteries haute capacité", desc: "Perte d'autonomie, gonflement" },
        { name: "Connecteurs de charge", desc: "Le téléphone ne charge plus" },
        { name: "Micro-soudure carte mère", desc: "Réparation composants invisibles" }
      ] 
    },
    { 
      category: "LOGICIEL & SÉCURITÉ", 
      items: [
        { name: "Déblocage de compte", desc: "Google, iCloud, Mot de passe oublié" },
        { name: "Récupération de données", desc: "Photos et contacts perdus" },
        { name: "Mises à jour & Flashage", desc: "Bug système, blocage logo" }
      ] 
    },
    { 
      category: "INTERVENTIONS SPÉCIALES", 
      items: [
        { name: "Désoxydation complète", desc: "Téléphone tombé dans l'eau" },
        { name: "Châssis & Vitre Arrière", desc: "Remise à neuf esthétique" },
        { name: "Haut-parleur & Micro", desc: "On ne vous entend plus ?" }
      ] 
    }
  ];

  const handleBooking = (e) => {
    e.preventDefault();
    setAppointmentStep('SUCCESS');
  };

  return (
    <div className="min-h-screen bg-[#020202] text-white font-sans pb-44">
      {/* Header with store info */}
      <header className="sticky top-0 z-50 bg-black/90 backdrop-blur-lg border-b border-white/5 shadow-2xl">
        <div className="max-w-2xl mx-auto p-6 flex justify-between items-center">
          <div className="flex flex-col">
            <h1 className="text-3xl font-black italic text-cyan-400 tracking-tighter uppercase leading-none">GSM STORE</h1>
            <p className="text-[10px] font-bold opacity-50 uppercase tracking-[0.4em] mt-2 italic">180 BD National, 13003</p>
          </div>
          <div className="text-right">
             <span className="text-[10px] font-black text-green-500 uppercase italic tracking-widest block">OUVERT</span>
             <span className="text-[8px] opacity-30 font-bold uppercase tracking-widest italic">Devis Immédiat</span>
          </div>
        </div>
      </header>

      {/* Main Tab Navigation */}
      <div className="max-w-2xl mx-auto p-4 flex gap-4 mt-2">
        <button 
          onClick={() => setActiveTab('PHONES')}
          className={`flex-1 py-5 rounded-[2.5rem] font-black italic text-[11px] uppercase tracking-[0.2em] transition-all border ${activeTab === 'PHONES' ? 'bg-white text-black border-white shadow-xl scale-[1.02]' : 'bg-zinc-950 text-white/40 border-white/5'}`}
        >
          Catalogue
        </button>
        <button 
          onClick={() => setActiveTab('REPAIR')}
          className={`flex-1 py-5 rounded-[2.5rem] font-black italic text-[11px] uppercase tracking-[0.2em] transition-all border ${activeTab === 'REPAIR' ? 'bg-cyan-500 text-black border-cyan-500 shadow-xl scale-[1.02]' : 'bg-zinc-950 text-white/40 border-white/5'}`}
        >
          Réparation
        </button>
      </div>

      {activeTab === 'PHONES' ? (
        <div className="animate-in fade-in slide-in-from-bottom-4 duration-500">
          <nav className="p-4 flex gap-2 overflow-x-auto no-scrollbar max-w-2xl mx-auto">
            {['TOUS', 'SAMSUNG', 'HONOR', 'XIAOMI', 'OPPO', 'AUTRES'].map(cat => (
              <button 
                key={cat}
                onClick={() => setFilter(cat)}
                className={`px-7 py-3.5 rounded-2xl text-[10px] font-black uppercase italic border transition-all shrink-0 ${
                  filter === cat ? 'bg-cyan-500 text-black border-cyan-500 shadow-md shadow-cyan-500/30' : 'bg-zinc-900/50 text-white/40 border-white/5'
                }`}
              >
                {cat}
              </button>
            ))}
          </nav>

          <main className="p-4 max-w-2xl mx-auto space-y-4">
            {inventory.filter(p => filter === 'TOUS' || p.brand === filter).map(item => (
              <div 
                key={item.id}
                onClick={() => setSelectedProduct(item)}
                className="group relative bg-zinc-900/40 border border-white/5 p-7 rounded-[2.5rem] flex justify-between items-center transition-all hover:bg-zinc-800/60 active:scale-[0.98] cursor-pointer"
              >
                <div className="flex items-center gap-6">
                  <div className={`w-1.5 h-12 rounded-full ${item.promo ? 'bg-red-500 shadow-[0_0_15px_rgba(239,68,68,0.3)]' : 'bg-cyan-500 shadow-[0_0_15px_rgba(6,182,212,0.2)]'}`} />
                  <div>
                    <span className="text-[8px] font-black text-cyan-400/60 uppercase tracking-[0.3em] italic">{item.brand}</span>
                    <h2 className="text-xl font-black uppercase italic tracking-tighter text-white leading-none mt-1 group-hover:text-cyan-400 transition-colors">{item.name}</h2>
                    <p className="text-[9px] font-bold opacity-30 uppercase mt-2 italic">Garantie 6 mois</p>
                  </div>
                </div>
                <div className="text-right font-black italic tracking-tighter text-3xl">{item.price}</div>
              </div>
            ))}
          </main>
        </div>
      ) : (
        <main className="p-4 max-w-2xl mx-auto space-y-6 animate-in fade-in slide-in-from-bottom-4">
          <div className="bg-zinc-900/60 border border-cyan-500/20 p-10 rounded-[3.5rem] text-center shadow-2xl relative">
             <h3 className="text-3xl font-black italic uppercase tracking-tighter leading-none">Réparation Express</h3>
             <p className="text-cyan-400 text-[11px] font-black uppercase mt-3 tracking-[0.4em] italic underline underline-offset-8">Garantie 6 Mois GSM STORE</p>
             
             <div className="mt-12 space-y-4">
               {/* Primary direct call button */}
               <a 
                 href="tel:0758363736" 
                 className="block w-full py-5 bg-white text-black rounded-[2rem] font-black italic uppercase text-xs tracking-[0.2em] shadow-xl active:scale-95 transition-all text-center"
               >
                Appeler pour un prix
               </a>
               
               {appointmentStep === 'IDLE' && (
                 <button 
                  onClick={() => setAppointmentStep('FORM')}
                  className="w-full py-4 bg-zinc-800 text-white/60 rounded-[2rem] font-black italic uppercase text-[10px] tracking-[0.2em] active:scale-95 transition-all"
                 >
                  Prendre Rendez-vous (30min)
                 </button>
               )}
             </div>

             {appointmentStep === 'FORM' && (
               <form onSubmit={handleBooking} className="mt-10 space-y-4 text-left animate-in zoom-in-95">
                  <div className="space-y-4">
                    <input required type="text" placeholder="Votre modèle (iPhone, Samsung...)" className="w-full bg-black border border-white/10 rounded-2xl py-4 px-6 text-sm outline-none focus:border-cyan-500" onChange={(e) => setAppointmentData({...appointmentData, model: e.target.value})}/>
                    <div className="grid grid-cols-2 gap-4">
                      <select className="bg-black border border-white/10 rounded-2xl py-4 px-4 text-[10px] uppercase font-black italic outline-none" onChange={(e) => setAppointmentData({...appointmentData, service: e.target.value})}>
                        <option>Écran</option><option>Batterie</option><option>Eau/Oxydation</option><option>Micro-Soudure</option><option>Logiciel</option>
                      </select>
                      <input type="time" className="bg-black border border-white/10 rounded-2xl py-4 px-4 text-xs outline-none" onChange={(e) => setAppointmentData({...appointmentData, time: e.target.value})}/>
                    </div>
                  </div>
                  <button className="w-full bg-cyan-500 text-black py-5 rounded-2xl font-black uppercase italic text-xs tracking-widest shadow-lg mt-4">Confirmer le passage</button>
                  <button type="button" onClick={() => setAppointmentStep('IDLE')} className="w-full text-[9px] opacity-30 uppercase font-black tracking-widest pt-2">Fermer</button>
               </form>
             )}

             {appointmentStep === 'SUCCESS' && (
               <div className="mt-10 p-8 bg-green-500/10 border border-green-500/20 rounded-[2.5rem] animate-in zoom-in-95 text-center">
                  <p className="text-green-500 font-black italic uppercase text-sm tracking-widest">C'est validé !</p>
                  <p className="text-[10px] mt-2 opacity-70 italic leading-relaxed">
                    RDV à <span className="text-white">{appointmentData.time}</span> pour votre <span className="text-white">{appointmentData.model}</span>.<br/>Le devis est gratuit sur place.
                  </p>
                  <button onClick={() => setAppointmentStep('IDLE')} className="mt-6 text-[10px] font-black uppercase underline tracking-widest opacity-40 hover:opacity-100 transition-opacity">OK</button>
               </div>
             )}
          </div>

          <div className="space-y-8 pb-10">
            {repairExpertise.map((cat, i) => (
              <div key={i} className="space-y-4">
                <h4 className="text-[10px] font-black uppercase tracking-[0.4em] text-cyan-400 italic ml-6">{cat.category}</h4>
                <div className="grid gap-3">
                  {cat.items.map((item, j) => (
                    <div key={j} className="bg-zinc-900/30 border border-white/5 p-6 rounded-[2.5rem] flex justify-between items-center group hover:bg-zinc-900/50 transition-all">
                      <div className="flex flex-col">
                        <span className="font-black italic uppercase text-sm tracking-tight">{item.name}</span>
                        <span className="text-[9px] opacity-40 uppercase font-bold mt-1 tracking-wider">{item.desc}</span>
                      </div>
                      
                      {/* Individual quote direct call button */}
                      <a 
                        href="tel:0758363736" 
                        className="flex items-center gap-2 bg-white/5 px-4 py-2.5 rounded-2xl border border-white/10 active:scale-95 transition-all"
                      >
                        <span className="text-white font-black italic text-[8px] uppercase tracking-widest">DEVIS</span>
                        <svg className="w-3 h-3 text-cyan-400" fill="currentColor" viewBox="0 0 20 20">
                          <path d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z" />
                        </svg>
                      </a>
                    </div>
                  ))}
                </div>
              </div>
            ))}
          </div>
        </main>
      )}

      {/* Floating direct call footer */}
      <footer className="fixed bottom-0 left-0 right-0 p-8 bg-gradient-to-t from-black via-black/95 to-transparent z-[80]">
        <div className="max-w-md mx-auto space-y-4">
          <a href="tel:0758363736" className="flex items-center justify-between bg-white text-black h-20 px-10 rounded-[2.5rem] shadow-[0_20px_50px_rgba(255,255,255,0.1)] active:scale-95 transition-all group">
            <div className="flex flex-col items-start leading-none">
              <p className="text-[9px] font-black uppercase tracking-[0.3em] opacity-30 mb-1 italic">CONTACT GSM STORE</p>
              <p className="text-2xl font-black italic uppercase tracking-tighter leading-none group-active:text-cyan-600 transition-colors">07 58 36 37 36</p>
            </div>
            <div className="bg-cyan-500 text-black p-4 rounded-2xl shadow-xl animate-bounce">
                <svg className="w-7 h-7" fill="currentColor" viewBox="0 0 20 20"><path d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z" /></svg>
            </div>
          </a>
          <button onClick={() => setShowLegal(true)} className="w-full text-center text-[9px] font-black uppercase tracking-[0.4em] opacity-20 py-2 hover:opacity-100 transition-opacity italic underline underline-offset-4">
            Horaires & Garanties • Marseille
          </button>
        </div>
      </footer>

      {/* Info Modal */}
      {showLegal && (
        <div className="fixed inset-0 z-[110] flex items-center justify-center p-4">
          <div className="absolute inset-0 bg-black/99" onClick={() => setShowLegal(false)}></div>
          <div className="relative bg-zinc-950 w-full max-w-2xl max-h-[80vh] overflow-y-auto rounded-[3.5rem] border border-white/10 p-10">
            <h2 className="text-2xl font-black italic uppercase tracking-tighter text-cyan-400 mb-8 border-b border-white/5 pb-4">INFOS MAGASIN</h2>
            <div className="space-y-6 text-white/40 text-[11px] leading-relaxed italic">
              <p><strong className="text-white">ADRESSE :</strong> 180 Boulevard National, 13003 Marseille.</p>
              <p><strong className="text-white">REPARATION :</strong> Tous domaines (Écrans, Micro-soudure, Déblocage).</p>
              <p><strong className="text-white">GARANTIE :</strong> 6 mois sur toutes les pièces remplacées.</p>
              <p><strong className="text-white">DEVIS :</strong> Gratuit et immédiat en boutique ou par téléphone.</p>
            </div>
            <button onClick={() => setShowLegal(false)} className="mt-10 w-full py-5 bg-zinc-900 rounded-[2rem] font-black uppercase text-[10px] tracking-widest italic">Fermer</button>
          </div>
        </div>
      )}

      {/* Product Detail Modal */}
      {selectedProduct && (
        <div className="fixed inset-0 z-[100] flex items-center justify-center p-4">
          <div className="absolute inset-0 bg-black/98 backdrop-blur-xl" onClick={() => setSelectedProduct(null)}></div>
          <div className="relative bg-zinc-950 w-full max-w-md rounded-[4rem] border border-white/10 p-10 shadow-2xl animate-in zoom-in-95 duration-300">
            <button onClick={() => setSelectedProduct(null)} className="absolute top-10 right-10 text-white/30 text-2xl">✕</button>
            <div className="text-center mt-6">
               <span className="text-cyan-400 text-[10px] font-black uppercase tracking-[0.4em] italic">{selectedProduct.brand}</span>
               <h3 className="text-4xl font-black uppercase italic tracking-tighter leading-none mt-3">{selectedProduct.name}</h3>
               <p className="text-6xl font-black text-white italic tracking-tighter leading-none mt-8">{selectedProduct.price}</p>
            </div>
            <a href="tel:0758363736" className="block w-full bg-white text-black text-center font-black uppercase italic py-6 rounded-3xl text-xs tracking-[0.2em] mt-10 active:scale-95 transition-all shadow-2xl">
              Réserver par téléphone
            </a>
          </div>
        </div>
      )}
    </div>
  );
};

export default App;
