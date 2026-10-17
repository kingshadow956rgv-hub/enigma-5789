# enigma-5789
Enigma 5789 World Observer.
package.json {
  "name": "enigma-5789-world-observer",
  "private": true,
  "version": "0.7.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "lucide-react": "^0.344.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/node": "^20.11.24",
    "@types/react": "^18.2.56",
    "@types/react-dom": "^18.2.19",
    "@vitejs/plugin-react": "^4.2.1",
    "typescript": "^5.2.2",
    "vite": "^5.1.4",
    "vite-plugin-pwa": "^0.19.2"
  }
}
vite.config.ts import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import { VitePWA } from 'vite-plugin-pwa';

export default defineConfig({
  plugins: [
    react(),
    VitePWA({
      registerType: 'autoUpdate',
      includeAssets: ['favicon.ico', 'apple-touch-icon.png', 'mask-icon.svg'],
      manifest: {
        name: 'Enigma 5789 — World Observer',
        short_name: 'Enigma5789',
        description: 'Evidence-Centered Geopolitical Observation, Scenario Branching, and Cognitive Mentorship Engine',
        theme_color: '#07090e',
        background_color: '#07090e',
        display: 'standalone',
        orientation: 'portrait-primary',
        icons: [
          {
            src: 'pwa-192x192.png',
            sizes: '192x192',
            type: 'image/png'
          },
          {
            src: 'pwa-512x512.png',
            sizes: '512x512',
            type: 'image/png'
          }
        ]
      }
    })
  ],
  server: {
    port: 3000,
    host: true
  }
});
vercel.json {
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
src/App.tsx import React, { useState } from 'react';

export const App: React.FC = () => {
  const [activeTab, setActiveTab] = useState<'GLOBE' | 'TREE' | 'TOWN_HALL' | 'SCORES'>('GLOBE');
  const [jimmyMessages, setJimmyMessages] = useState<Array<{ sender: 'JIMMY' | 'USER'; text: string }>>([
    {
      sender: 'JIMMY',
      text: "Welcome to Enigma 5789! I'm Jimmy, your cognitive guide and system manager. I can help you evaluate world events, structure kill tests, or adapt learning topics. What are we observing today?",
    },
  ]);
  const [userInput, setUserInput] = useState<string>('');

  const handleJimmySend = () => {
    if (!userInput.trim()) return;
    const newMsgs = [...jimmyMessages, { sender: 'USER' as const, text: userInput }];
    setJimmyMessages(newMsgs);
    setUserInput('');

    setTimeout(() => {
      setJimmyMessages([
        ...newMsgs,
        {
          sender: 'JIMMY',
          text: `I've logged your input: "${userInput}". Cross-referencing OpenAlex research indices and checking historical base rates. Would you like me to construct a multi-layer Kill Test for this hypothesis?`,
        },
      ]);
    }, 800);
  };

  return (
    <div style={{ background: '#07090e', color: '#e2e8f0', minHeight: '100vh', fontFamily: 'monospace', display: 'flex', flexDirection: 'column' }}>
      
      {/* Header */}
      <header style={{ background: '#0f172a', padding: '12px 24px', borderBottom: '1px solid #1e293b', display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
        <div style={{ display: 'flex', alignItems: 'center', gap: '12px' }}>
          <div style={{ width: '12px', height: '12px', borderRadius: '50%', background: '#00e5ff', boxShadow: '0 0 10px #00e5ff' }} />
          <h2 style={{ margin: 0, fontSize: '18px', letterSpacing: '1px', color: '#f8fafc' }}>ENIGMA 5789 // WORLD OBSERVER</h2>
        </div>

        <nav style={{ display: 'flex', gap: '10px' }}>
          {(['GLOBE', 'TREE', 'TOWN_HALL', 'SCORES'] as const).map((tab) => (
            <button
              key={tab}
              onClick={() => setActiveTab(tab)}
              style={{
                background: activeTab === tab ? '#1e293b' : 'transparent',
                color: activeTab === tab ? '#00e5ff' : '#94a3b8',
                border: `1px solid ${activeTab === tab ? '#00e5ff' : '#334155'}`,
                borderRadius: '6px',
                padding: '8px 16px',
                cursor: 'pointer',
                fontFamily: 'monospace',
                fontWeight: 'bold',
              }}
            >
              {tab.replace('_', ' ')}
            </button>
          ))}
        </nav>
      </header>

      {/* Main Layout */}
      <div style={{ flex: 1, display: 'flex', padding: '20px', gap: '20px', overflow: 'hidden' }}>
        <main style={{ flex: 1, overflowY: 'auto', background: '#0f172a', padding: '20px', borderRadius: '12px', border: '1px solid #334155' }}>
          {activeTab === 'GLOBE' && <h3>3D Globe & Observation Windows Active</h3>}
          {activeTab === 'TREE' && <h3>Branching Scenario Tree</h3>}
          {activeTab === 'TOWN_HALL' && <h3>Town Hall Assembly Chamber</h3>}
          {activeTab === 'SCORES' && (
            <div>
              <h3 style={{ color: '#38bdf8', margin: '0 0 15px 0' }}>3-TRACK CORRELATION SCORECARD</h3>
              <p><strong>P ↔ R (Prediction vs Real World):</strong> 84.2% (Strong)</p>
              <p><strong>M ↔ R (Maya Symbolism vs Real World):</strong> 61.5% (Moderate Alignment)</p>
              <p><strong>P ↔ M (Prediction vs Maya Lens):</strong> 58.0% (Independent Alignment)</p>
            </div>
          )}
        </main>

        {/* Jimmy AI Side Panel */}
        <aside style={{ width: '340px', background: '#0f172a', borderRadius: '12px', border: '1px solid #1e293b', display: 'flex', flexDirection: 'column' }}>
          <div style={{ padding: '12px 16px', borderBottom: '1px solid #1e293b', background: '#1e1b4b', borderRadius: '12px 12px 0 0', display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
            <span style={{ color: '#c7d2fe', fontWeight: 'bold' }}>🤖 JIMMY // AI ASSISTANT</span>
            <span style={{ fontSize: '10px', background: '#064e3b', color: '#6ee7b7', padding: '2px 6px', borderRadius: '4px' }}>ONLINE</span>
          </div>

          <div style={{ flex: 1, padding: '15px', overflowY: 'auto', display: 'flex', flexDirection: 'column', gap: '10px' }}>
            {jimmyMessages.map((msg, idx) => (
              <div
                key={idx}
                style={{
                  alignSelf: msg.sender === 'USER' ? 'flex-end' : 'flex-start',
                  background: msg.sender === 'USER' ? '#0284c7' : '#1e293b',
                  color: '#fff',
                  padding: '10px 12px',
                  borderRadius: msg.sender === 'USER' ? '12px 12px 0 12px' : '12px 12px 12px 0',
                  fontSize: '12px',
                  lineHeight: '1.4',
                  maxWidth: '85%',
                }}
              >
                {msg.text}
              </div>
            ))}
          </div>

          <div style={{ padding: '12px', borderTop: '1px solid #1e293b', display: 'flex', gap: '8px' }}>
            <input
              type="text"
              value={userInput}
              onChange={(e) => setUserInput(e.target.value)}
              onKeyDown={(e) => e.key === 'Enter' && handleJimmySend()}
              placeholder="Ask Jimmy or enter prediction..."
              style={{ flex: 1, background: '#020617', color: '#fff', border: '1px solid #334155', borderRadius: '6px', padding: '8px', fontSize: '12px' }}
            />
            <button
              onClick={handleJimmySend}
              style={{ background: '#00e5ff', color: '#000', border: 'none', borderRadius: '6px', padding: '8px 12px', fontWeight: 'bold', cursor: 'pointer' }}
            >
              Send
            </button>
          </div>
        </aside>
      </div>
    </div>
  );
};

