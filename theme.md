import React, { useState, useEffect, useRef } from 'react';
import { Terminal, Shield, Activity, Settings, Layout, Fingerprint, Sun, Moon } from 'lucide-react';

// --- CSS Styles ---
// I've incorporated your specific theme definitions and added standard utility mappings.
const cssStyles = `
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Orbitron:wght@400;700;900&display=swap');

  /* Base Transitions */
  * {
    transition: background-color 0.5s ease, color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
  }

  /* --- YOUR THEME DEFINITIONS --- */
  
  /* Theme: Voyager (Immersive) */
  [data-theme='voyager'] {
    --bg-primary: #0b0c15;
    --text-primary: #00f3ff;
    --text-secondary: rgba(0, 243, 255, 0.7);
    --panel-glass: rgba(11, 12, 21, 0.65);
    --panel-border: rgba(0, 243, 255, 0.3);
    --accent: #00f3ff;
    --font-display: 'Orbitron', sans-serif;
    --font-body: 'Orbitron', sans-serif; /* Using Orbitron for body in Voyager for full effect */
    --visualization-opacity: 1.0;
    --glow: 0 0 20px rgba(0, 243, 255, 0.15);
  }

  /* Theme: Professional (Classic) */
  [data-theme='professional'] {
    --bg-primary: #f0f2f5;
    --text-primary: #1a1a1a;
    --text-secondary: #555555;
    --panel-glass: #ffffff;
    --panel-border: #e0e0e0;
    --accent: #2563eb;
    --font-display: 'Inter', sans-serif;
    --font-body: 'Inter', sans-serif;
    --visualization-opacity: 0.0;
    --glow: none;
  }

  /* --- UTILITY CLASSES MAPPED TO VARIABLES --- */
  
  body, .app-container {
    background-color: var(--bg-primary);
    color: var(--text-primary);
    font-family: var(--font-body);
  }

  h1, h2, h3, .display-font {
    font-family: var(--font-display);
  }

  .glass-panel {
    background: var(--panel-glass);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid var(--panel-border);
    box-shadow: var(--glow);
  }

  .accent-text {
    color: var(--accent);
  }

  .accent-border {
    border-color: var(--accent);
  }

  .viz-layer {
    opacity: var(--visualization-opacity);
    transition: opacity 0.8s ease-in-out;
  }
`;

// --- Particle Visualization Component ---
// This renders a starfield/data stream that is only visible in Voyager mode
const Visualization = () => {
  const canvasRef = useRef(null);

  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    let animationFrameId;
    let particles = [];

    const resize = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };
    
    window.addEventListener('resize', resize);
    resize();

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 2;
        this.speedY = Math.random() * 0.5 + 0.1;
        this.opacity = Math.random() * 0.5 + 0.1;
      }
      update() {
        this.y -= this.speedY; // Move up
        if (this.y < 0) this.y = canvas.height;
      }
      draw() {
        ctx.fillStyle = `rgba(0, 243, 255, ${this.opacity})`;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    // Initialize particles
    for (let i = 0; i < 100; i++) {
      particles.push(new Particle());
    }

    const animate = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      
      // Draw grid lines
      ctx.strokeStyle = 'rgba(0, 243, 255, 0.03)';
      ctx.lineWidth = 1;
      const gridSize = 100;
      
      for(let x = 0; x < canvas.width; x += gridSize) {
        ctx.beginPath();
        ctx.moveTo(x, 0);
        ctx.lineTo(x, canvas.height);
        ctx.stroke();
      }
      
      animationFrameId = requestAnimationFrame(animate);
    };

    animate();

    return () => {
      window.removeEventListener('resize', resize);
      cancelAnimationFrame(animationFrameId);
    };
  }, []);

  return (
    <canvas 
      ref={canvasRef} 
      className="fixed inset-0 pointer-events-none viz-layer z-0"
    />
  );
};

// --- Main Application Component ---
const App = () => {
  const [theme, setTheme] = useState('voyager');

  const toggleTheme = () => {
    setTheme(prev => prev === 'voyager' ? 'professional' : 'voyager');
  };

  return (
    <div className="app-container min-h-screen relative overflow-hidden" data-theme={theme}>
      <style>{cssStyles}</style>
      
      {/* Background Visualization */}
      <Visualization />

      <div className="relative z-10 p-4 md:p-10 max-w-7xl mx-auto flex flex-col h-screen">
        
        {/* Header */}
        <header className="flex justify-between items-center mb-10 glass-panel p-6 rounded-2xl">
          <div className="flex items-center gap-4">
            <div className="p-3 rounded-full border border-[var(--text-primary)]">
              {theme === 'voyager' ? <Activity size={24} /> : <Layout size={24} />}
            </div>
            <div>
              <h1 className="text-2xl md:text-3xl font-bold tracking-wider uppercase">
                {theme === 'voyager' ? 'VoyagerOS' : 'Enterprise Dashboard'}
              </h1>
              <p className="text-sm opacity-70">
                {theme === 'voyager' ? 'v.9.2.1 // ORBITAL LINK ACTIVE' : 'Admin Portal • Version 2.0'}
              </p>
            </div>
          </div>
          
          <button 
            onClick={toggleTheme}
            className="flex items-center gap-2 px-6 py-3 rounded-lg border border-[var(--panel-border)] hover:bg-[var(--text-primary)] hover:text-[var(--bg-primary)] transition-all font-bold uppercase tracking-widest text-xs md:text-sm"
          >
            {theme === 'voyager' ? <Moon size={16}/> : <Sun size={16}/>}
            {theme === 'voyager' ? 'Disengage Immersive' : 'Engage Immersive'}
          </button>
        </header>

        {/* Main Grid */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6 flex-grow">
          
          {/* Sidebar / Stats */}
          <div className="space-y-6">
             <div className="glass-panel p-6 rounded-2xl h-full flex flex-col justify-between">
                <div>
                  <h2 className="text-xl mb-6 flex items-center gap-2 opacity-80 uppercase tracking-widest border-b border-[var(--panel-border)] pb-4">
                    <Terminal size={18} /> System Diagnostics
                  </h2>
                  <ul className="space-y-4 font-mono text-sm opacity-80">
                    <li className="flex justify-between">
                      <span>CPU_LOAD</span>
                      <span className="accent-text">12%</span>
                    </li>
                    <li className="flex justify-between">
                      <span>MEM_ALLOC</span>
                      <span className="accent-text">4.2GB</span>
                    </li>
                    <li className="flex justify-between">
                      <span>NET_LATENCY</span>
                      <span className="accent-text">24ms</span>
                    </li>
                    <li className="flex justify-between">
                      <span>ENCRYPTION</span>
                      <span className="accent-text">AES-256</span>
                    </li>
                  </ul>
                </div>
                
                <div className="mt-8">
                  <div className="w-full bg-[var(--panel-border)] h-1 rounded-full overflow-hidden">
                    <div className="h-full bg-[var(--accent)] w-2/3 animate-pulse"></div>
                  </div>
                  <p className="text-right text-xs mt-2 opacity-60">BUFFER STATUS: STABLE</p>
                </div>
             </div>
          </div>

          {/* Main Content Area */}
          <div className="md:col-span-2 glass-panel p-8 rounded-2xl flex flex-col justify-center items-center text-center relative overflow-hidden">
            {/* Decorative decorative circle for Voyager */}
            {theme === 'voyager' && (
              <div className="absolute w-[500px] h-[500px] border border-[var(--panel-border)] rounded-full opacity-20 animate-spin-slow pointer-events-none" style={{animationDuration: '30s'}}></div>
            )}
            
            <div className="relative z-10 max-w-lg">
              <div className="mb-6 mx-auto w-16 h-16 rounded-full border-2 border-[var(--accent)] flex items-center justify-center">
                <Shield size={32} className="accent-text" />
              </div>
              
              <h2 className="text-4xl md:text-5xl font-bold mb-6 display-font">
                {theme === 'voyager' ? 'SECURE LINK' : 'Welcome Back'}
              </h2>
              
              <p className="text-lg opacity-70 mb-8 leading-relaxed">
                {theme === 'voyager' 
                  ? 'Biometric scan complete. Identity confirmed. Welcome to the Nexus, Commander. The data streams are currently synchronized with the orbital station.' 
                  : 'Please review the latest quarterly reports and update your team availability. The system has been updated to the latest security patch.'}
              </p>

              <div className="flex gap-4 justify-center">
                <button className="px-8 py-3 bg-[var(--accent)] text-[var(--bg-primary)] font-bold rounded hover:opacity-90 transition-opacity">
                  {theme === 'voyager' ? 'INITIALIZE' : 'View Reports'}
                </button>
                <button className="px-8 py-3 border border-[var(--panel-border)] rounded hover:bg-[var(--panel-border)] transition-colors">
                  {theme === 'voyager' ? 'ABORT' : 'Settings'}
                </button>
              </div>
            </div>
          </div>

          {/* Bottom Grid Items */}
          <div className="glass-panel p-6 rounded-2xl flex items-center gap-4">
             <div className="p-3 bg-[var(--panel-border)] rounded-lg">
                <Settings size={24} className="accent-text" />
             </div>
             <div>
               <h3 className="font-bold uppercase text-sm">Configuration</h3>
               <p className="text-xs opacity-60">Last updated 2m ago</p>
             </div>
          </div>

          <div className="glass-panel p-6 rounded-2xl flex items-center gap-4">
             <div className="p-3 bg-[var(--panel-border)] rounded-lg">
                <Fingerprint size={24} className="accent-text" />
             </div>
             <div>
               <h3 className="font-bold uppercase text-sm">Security</h3>
               <p className="text-xs opacity-60">Level 5 Clearance</p>
             </div>
          </div>

          <div className="glass-panel p-6 rounded-2xl flex items-center justify-between">
             <div>
               <h3 className="font-bold uppercase text-sm">Uptime</h3>
               <p className="text-xs opacity-60">99.998%</p>
             </div>
             <div className="text-2xl font-bold accent-text display-font">24:01:55</div>
          </div>

        </div>
      </div>
    </div>
  );
};

export default App;
