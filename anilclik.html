import React, { useState, useEffect, useRef } from 'react';
import { 
  Zap, Timer, Skull, Coins, Package, 
  TrendingUp, ShoppingCart, Star, Info
} from 'lucide-react';

/**
 * CLICKER SIMULATOR ULTIMATE - RESPONSIVE & ALL-IN-ONE
 * Standard Assets: 17400.png, 17473.jpg, 17474.jpg, 15822, 15821, 15817
 */

const ASSETS = {
  clickTarget: "https://i.ibb.co/6RcKH1Hy/17400.png",
  gambleIntro: "https://i.ibb.co/GvPptxxH/17473.jpg",
  slotBg: "https://i.ibb.co/twPq3Fyz/17474.jpg",
  slotIcons: [
    "https://i.ibb.co/pBZkrC9y/15822.png",
    "https://i.ibb.co/8n0MhXMj/15821.png",
    "https://i.ibb.co/wNFhpkH2/15817.png"
  ],
  crateItems: [
    { name: "Sıradan", color: "#94a3b8", multi: 1.1 },
    { name: "Nadir", color: "#3b82f6", multi: 2.0 },
    { name: "Epik", color: "#a855f7", multi: 5.0 },
    { name: "Efsanevi", color: "#eab308", multi: 15.0 },
    { name: "Antik", color: "#ef4444", multi: 50.0 }
  ]
};

const formatNumber = (num) => {
  if (num >= 1e9) return (num / 1e9).toFixed(2) + 'B';
  if (num >= 1e6) return (num / 1e6).toFixed(2) + 'M';
  if (num >= 1e3) return (num / 1e3).toFixed(1) + 'k';
  return Math.floor(num).toLocaleString();
};

export default function App() {
  // Game Logic State
  const [score, setScore] = useState(0);
  const [clickPower, setClickPower] = useState(1);
  const [autoRate, setAutoRate] = useState(0);
  const [eggMulti, setEggMulti] = useState(1.0);
  const [buff, setBuff] = useState({ active: false, endsAt: null });
  const [timeLeft, setTimeLeft] = useState(0);

  // UI State
  const [gambleStage, setGambleStage] = useState('idle'); // idle | intro | slots | lose
  const [slotIndices, setSlotIndices] = useState([0, 0, 0]);
  const [attempt, setAttempt] = useState(0);
  const [isOpeningCrate, setIsOpeningCrate] = useState(false);
  const [crateList, setCrateList] = useState([]);
  const [wonItem, setWonItem] = useState(null);
  const [shake, setShake] = useState(false);

  const totalMultiplier = (buff.active ? 10 : 1) * eggMulti;

  // Global Game Loop
  useEffect(() => {
    const ticker = setInterval(() => {
      if (gambleStage === 'idle') {
        setScore(prev => prev + (autoRate * totalMultiplier) / 10);
      }
      if (buff.active && buff.endsAt) {
        const rem = Math.max(0, buff.endsAt - Date.now());
        setTimeLeft(rem);
        if (rem === 0) setBuff({ active: false, endsAt: null });
      }
    }, 100);
    return () => clearInterval(ticker);
  }, [autoRate, totalMultiplier, buff, gambleStage]);

  // Actions
  const handleMainClick = (e) => {
    if (gambleStage !== 'idle' || isOpeningCrate) return;
    setScore(prev => prev + (clickPower * totalMultiplier));
    setShake(true);
    setTimeout(() => setShake(false), 50);
  };

  const buyUpgrade = (cost, type, amount) => {
    if (score >= cost) {
      setScore(prev => prev - cost);
      if (type === 'click') setClickPower(p => p + amount);
      if (type === 'auto') setAutoRate(p => p + amount);
    }
  };

  // Crate Mechanic
  const openCrate = () => {
    if (score < 5000 || isOpeningCrate) return;
    setScore(prev => prev - 5000);
    setIsOpeningCrate(true);
    setWonItem(null);

    const generated = Array.from({ length: 60 }, () => {
      const r = Math.random() * 100;
      if (r < 1) return ASSETS.crateItems[4];
      if (r < 5) return ASSETS.crateItems[3];
      if (r < 15) return ASSETS.crateItems[2];
      if (r < 40) return ASSETS.crateItems[1];
      return ASSETS.crateItems[0];
    });
    setCrateList(generated);
    const winner = generated[55];

    setTimeout(() => {
      setWonItem(winner);
      setEggMulti(winner.multi);
      setIsOpeningCrate(false);
    }, 5500);
  };

  // Classic Gamble Mechanic
  const startGamble = () => {
    if (score <= 0 || buff.active) return;
    const current = score;
    setScore(0);
    setGambleStage('intro');
    setTimeout(() => {
      setGambleStage('slots');
      runSlots(current, 1);
    }, 2000);
  };

  const runSlots = (stashed, currentAttempt) => {
    setAttempt(currentAttempt);
    let spins = 0;
    const interval = setInterval(() => {
      setSlotIndices([Math.floor(Math.random()*3), Math.floor(Math.random()*3), Math.floor(Math.random()*3)]);
      spins++;
      if (spins > 10) {
        clearInterval(interval);
        const final = [Math.floor(Math.random()*3), Math.floor(Math.random()*3), Math.floor(Math.random()*3)];
        setSlotIndices(final);
        if (final[0] === final[1] && final[1] === final[2]) {
          setScore(stashed);
          setBuff({ active: true, endsAt: Date.now() + 251000 });
          setTimeout(() => setGambleStage('idle'), 2000);
        } else if (currentAttempt < 10) {
          setTimeout(() => runSlots(stashed, currentAttempt + 1), 700);
        } else {
          setGambleStage('lose');
          setTimeout(() => setGambleStage('idle'), 3000);
        }
      }
    }, 100);
  };

  return (
    <div className={`min-h-screen bg-[#09090b] text-slate-100 flex flex-col font-sans selection:bg-blue-500/30 overflow-x-hidden transition-all duration-500
      ${buff.active ? 'ring-[8px] ring-green-500/40 ring-inset' : ''}
      ${shake ? 'translate-y-0.5' : ''}
    `}>
      
      {/* Background FX */}
      <div className={`fixed inset-0 pointer-events-none transition-opacity duration-1000 z-0 
        ${buff.active ? 'opacity-20' : 'opacity-0'}`} 
        style={{ background: 'radial-gradient(circle, #22c55e 0%, transparent 70%)' }} 
      />

      {/* HEADER HUD - Fixed at Top */}
      <header className="sticky top-0 z-50 bg-black/60 backdrop-blur-xl border-b border-white/5 p-4 md:px-8 flex justify-between items-center">
        <div className="flex flex-col">
          <div className="flex items-center gap-2">
            <Coins className="text-yellow-400 w-6 h-6 animate-pulse" />
            <span className="text-2xl md:text-3xl font-black font-mono tracking-tighter">{formatNumber(score)}</span>
          </div>
          <div className="flex gap-3 text-[10px] font-bold text-slate-400 uppercase tracking-widest mt-1">
            <span className="text-blue-400">Power: {formatNumber(clickPower * totalMultiplier)}</span>
            <span className="text-purple-400">Auto: {formatNumber(autoRate * totalMultiplier)}/s</span>
          </div>
        </div>

        <div className="flex items-center gap-3">
          {buff.active && (
            <div className="hidden sm:flex bg-green-500/10 border border-green-500/30 px-3 py-1 rounded-full text-green-400 text-xs font-black animate-pulse">
              10X: {Math.floor(timeLeft/60000)}:{(Math.floor((timeLeft%60000)/1000)).toString().padStart(2,'0')}
            </div>
          )}
          <div className="bg-yellow-500/10 border border-yellow-500/30 px-3 py-1 rounded-full text-yellow-500 text-xs font-black italic">
            Yumurta: {eggMulti}x
          </div>
        </div>
      </header>

      {/* MAIN CONTENT AREA */}
      <main className="flex-1 p-4 md:p-8 flex flex-col lg:flex-row gap-6 lg:gap-8 z-10 max-w-7xl mx-auto w-full">
        
        {/* LEFT COLUMN: UPGRADES */}
        <section className="flex-1 order-2 lg:order-1 flex flex-col gap-4">
          <div className="flex items-center gap-2 mb-2">
            <ShoppingCart className="text-blue-500 w-5 h-5" />
            <h2 className="text-xl font-black uppercase tracking-tighter">Mağaza</h2>
          </div>
          <div className="space-y-3 overflow-y-auto max-h-[400px] lg:max-h-none pr-2 custom-scroll">
            <UpgradeItem 
              title="Gelişmiş Tık" 
              icon={<Zap/>} 
              lvl={clickPower} 
              cost={Math.floor(15 * Math.pow(1.5, clickPower-1))}
              onBuy={() => buyUpgrade(Math.floor(15 * Math.pow(1.5, clickPower-1)), 'click', 1)}
              canBuy={score >= Math.floor(15 * Math.pow(1.5, clickPower-1))}
            />
            <UpgradeItem 
              title="Otomatik Tık" 
              icon={<Timer/>} 
              lvl={autoRate} 
              cost={Math.floor(100 * Math.pow(1.6, autoRate))}
              onBuy={() => buyUpgrade(Math.floor(100 * Math.pow(1.6, autoRate)), 'auto', 1)}
              canBuy={score >= Math.floor(100 * Math.pow(1.6, autoRate))}
            />
            <UpgradeItem 
              title="Mega Fabrika" 
              icon={<TrendingUp/>} 
              lvl={Math.floor(autoRate/10)} 
              cost={Math.floor(5000 * Math.pow(1.8, autoRate/10))}
              onBuy={() => buyUpgrade(Math.floor(5000 * Math.pow(1.8, autoRate/10)), 'auto', 10)}
              canBuy={score >= Math.floor(5000 * Math.pow(1.8, autoRate/10))}
            />
          </div>
        </section>

        {/* CENTER COLUMN: CLICKER & GAMBLE */}
        <section className="flex-[1.5] order-1 lg:order-2 flex flex-col items-center justify-center gap-8 py-6">
          <div className="relative cursor-pointer transition-transform active:scale-90" onClick={handleMainClick}>
            <div className={`absolute inset-0 blur-[80px] rounded-full transition-all duration-700 ${buff.active ? 'bg-green-500/30 scale-150' : 'bg-blue-600/10'}`} />
            <img src={ASSETS.clickTarget} className="w-48 md:w-64 lg:w-80 relative z-10 drop-shadow-2xl" alt="Click Me" />
          </div>

          <div className="w-full max-w-sm flex flex-col gap-4">
            <button 
              onClick={startGamble}
              disabled={score <= 0 || buff.active}
              className={`w-full py-4 rounded-2xl font-black text-xl flex items-center justify-center gap-3 shadow-lg transition-all
                ${buff.active 
                  ? 'bg-slate-800 text-slate-500 cursor-not-allowed border border-white/5' 
                  : 'bg-red-600 hover:bg-red-500 active:scale-95 text-white'}
              `}
            >
              <Skull className="w-6 h-6" />
              {buff.active ? "BUFF AKTİF" : "KUMAR OYNA (TÜMÜ)"}
            </button>
            <p className="text-center text-red-500/70 text-[10px] font-bold uppercase tracking-[0.2em] animate-pulse">
              Kazanırsan 10X Buff • Kaybedersen 0
            </p>
          </div>
        </section>

        {/* RIGHT COLUMN: CRATE OPENING */}
        <section className="flex-1 order-3 flex flex-col gap-4">
          <div className="flex items-center gap-2 mb-2">
            <Package className="text-purple-500 w-5 h-5" />
            <h2 className="text-xl font-black uppercase tracking-tighter">Yumurta Kasası</h2>
          </div>

          <div className="bg-white/5 rounded-3xl p-6 border border-white/10 flex flex-col items-center gap-6">
            <div className="relative w-full h-32 bg-black/40 rounded-xl overflow-hidden flex items-center border border-white/5">
              <div className="absolute left-1/2 top-0 bottom-0 w-0.5 bg-yellow-500 z-30 shadow-[0_0_8px_yellow]" />
              <div 
                className={`flex gap-1 px-[50%] transition-transform duration-[5000ms] ease-[cubic-bezier(0.1,0,0.1,1)]`}
                style={{ transform: isOpeningCrate || wonItem ? `translateX(-${55 * 84}px)` : 'translateX(0px)' }}
              >
                {crateList.map((item, i) => (
                  <div key={i} className="w-20 h-20 flex-shrink-0 flex flex-col items-center justify-center bg-slate-800/80 rounded-lg border-b-4"
                    style={{ borderBottomColor: item.color }}>
                    <div className="w-8 h-10 bg-gradient-to-t from-white/10 to-transparent rounded-full border border-white/10 mb-1" />
                    <span className="text-[7px] font-black uppercase text-slate-400">{item.name}</span>
                    <span className="text-[10px] font-bold">{item.multi}x</span>
                  </div>
                ))}
              </div>
            </div>

            <button 
              onClick={openCrate}
              disabled={score < 5000 || isOpeningCrate}
              className="w-full py-4 bg-purple-600 hover:bg-purple-500 disabled:opacity-30 rounded-2xl font-black text-white shadow-xl transition-all"
            >
              KASA AÇ (5k)
            </button>

            {wonItem && !isOpeningCrate && (
              <div className="text-center animate-in zoom-in">
                <p className="text-[10px] text-slate-400 uppercase font-bold mb-1 tracking-widest">Kazanılan Çarpan</p>
                <p className="text-xl font-black" style={{ color: wonItem.color }}>{wonItem.name} {wonItem.multi}x</p>
              </div>
            )}
          </div>
        </section>
      </main>

      {/* OVERLAYS (FULLSCREEN) */}

      {/* 1. Gamble Intro */}
      {gambleStage === 'intro' && (
        <div className="fixed inset-0 z-[100] flex items-center justify-center bg-black animate-in fade-in duration-500">
          <img src={ASSETS.gambleIntro} className="absolute inset-0 w-full h-full object-cover opacity-50" alt="Gamble Intro" />
          <h1 className="relative text-4xl md:text-7xl font-black text-red-600 border-y-4 md:border-y-8 border-red-600 py-4 px-8 md:px-12 italic">KUMAR BAŞLASIN</h1>
        </div>
      )}

      {/* 2. Slot Rolling */}
      {gambleStage === 'slots' && (
        <div className="fixed inset-0 z-[100] flex flex-col items-center justify-center bg-[#050505] p-6">
          <img src={ASSETS.slotBg} className="absolute inset-0 w-full h-full object-cover opacity-20" alt="Slots" />
          <div className="relative z-10 w-full max-w-md bg-slate-900/90 p-8 rounded-[40px] border-4 border-yellow-600 shadow-2xl text-center">
            <h2 className="text-2xl font-black text-yellow-500 mb-8 italic uppercase tracking-widest">ALAN GENİŞLETME</h2>
            <div className="flex gap-3 justify-center mb-8">
              {slotIndices.map((idx, i) => (
                <div key={i} className="w-20 h-20 md:w-24 md:h-24 bg-black rounded-2xl border border-white/10 flex items-center justify-center p-2">
                  <img src={ASSETS.slotIcons[idx]} className="w-full h-full object-contain" alt="icon" />
                </div>
              ))}
            </div>
            <div className="flex items-center justify-center gap-2 text-slate-400 font-mono">
              <span className="text-xs uppercase">Deneme</span>
              <span className="text-xl font-black text-red-500">{attempt}</span>
              <span className="text-xs uppercase">/ 10</span>
            </div>
          </div>
        </div>
      )}

      {/* 3. Lose Overlay */}
      {gambleStage === 'lose' && (
        <div className="fixed inset-0 z-[100] bg-black flex flex-col items-center justify-center p-6 animate-in zoom-in duration-300">
          <Skull className="w-24 h-24 text-red-600 mb-6 drop-shadow-[0_0_20px_rgba(220,38,38,0.5)]" />
          <h1 className="text-4xl md:text-6xl font-black text-white text-center italic">HER ŞEY BİTTİ</h1>
          <p className="text-red-600 font-mono tracking-[1em] text-xs md:text-sm mt-6 uppercase">Kaybettin</p>
        </div>
      )}

      <style>{`
        .custom-scroll::-webkit-scrollbar { width: 4px; }
        .custom-scroll::-webkit-scrollbar-track { background: transparent; }
        .custom-scroll::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 10px; }
      `}</style>
    </div>
  );
}

function UpgradeItem({ title, icon, lvl, cost, onBuy, canBuy }) {
  return (
    <div 
      onClick={onBuy}
      className={`p-4 rounded-2xl border transition-all duration-200 group
        ${canBuy ? 'bg-white/5 border-white/10 hover:bg-white/10 cursor-pointer active:scale-95' : 'bg-black/20 border-white/5 opacity-40 cursor-not-allowed'}
      `}
    >
      <div className="flex justify-between items-center mb-3">
        <div className="flex items-center gap-3">
          <div className="p-2 bg-blue-500/20 text-blue-400 rounded-lg group-hover:scale-110 transition-transform">
            {icon}
          </div>
          <div>
            <h4 className="font-black text-sm uppercase leading-none mb-1">{title}</h4>
            <p className="text-[10px] text-slate-500 font-mono uppercase">Seviye {lvl}</p>
          </div>
        </div>
      </div>
      <div className="flex justify-between items-center">
        <div className="flex items-center gap-1">
          <Coins className="w-3 h-3 text-yellow-500" />
          <span className="text-sm font-black">{formatNumber(cost)}</span>
        </div>
        <div className={`px-4 py-1 rounded-lg text-[10px] font-black uppercase tracking-tighter transition-colors
          ${canBuy ? 'bg-blue-600 text-white group-hover:bg-blue-500' : 'bg-slate-800 text-slate-500'}
        `}>Satın Al</div>
      </div>
    </div>
  );
}

