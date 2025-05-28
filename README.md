https://cdn.jsdelivr.net/npm/pintura@10.0.0/pintura.cssmini-windows/
│
├── index.html
├── style.css
└── script.js <!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mini Windows</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="desktop">
    <div class="icon" onclick="abrirJanela('meusDocumentos')">
      📁<br>Meus Documentos
    </div>

    <div class="janela" id="meusDocumentos">
      <div class="barra">
        Meus Documentos
        <button onclick="fecharJanela('meusDocumentos')">X</button>
      </div>
      <div class="conteudo">
        <p>Esta é a janela de documentos!</p>
      </div>
    </div>
  </div>

  <div class="barra-tarefas">
    <div id="relogio"></div>
  </div>

  <script src="script.js"></script>
</body>
</html>body {
  margin: 0;
  font-family: sans-serif;
  background: #0080ff;
}

.desktop {
  height: 100vh;
  padding: 20px;
  position: relative;
  box-sizing: border-box;
}

.icon {
  width: 80px;
  text-align: center;
  cursor: pointer;
  color: white;
}

.janela {
  width: 300px;
  background: white;
  border: 1px solid black;
  position: absolute;
  top: 100px;
  left: 100px;
  display: none;
  z-index: 10;
}

.barra {
  background: #004080;
  color: white;
  padding: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: move;
}

.conteudo {
  padding: 10px;
}

.barra-tarefas {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background: #222;
  color: white;
  padding: 5px;
  text-align: right;
  font-size: 14px;
}function abrirJanela(id) {
  document.getElementById(id).style.display = 'block';
}

function fecharJanela(id) {
  document.getElementById(id).style.display = 'none';
}

function atualizarRelogio() {
  const agora = new Date();
  const horas = agora.getHours().toString().padStart(2, '0');
  const minutos = agora.getMinutes().toString().padStart(2, '0');
  document.getElementById('relogio').textContent = `${horas}:${minutos}`;
}

setInterval(atualizarRelogio, 1000);
atualizarRelogio();<link rel="manifest" href="manifest.json">
{
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "start_url": "./index.html",
  "display": "standalone",
  "background_color": "#202020",
  "theme_color": "#303030",
  "icons": [
    {
      "src": "icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
{
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "start_url": "index.html",
  "display": "standalone",
  "background_color": "#1e1e1e",
  "theme_color": "#1e1e1e",
  "orientation": "landscape",
  "icons": [
    {
      "src": "icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icons/icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
<link rel="manifest" href="manifest.json">
<meta name="theme-color" content="#1e1e1e">
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>MiniWin Navegador</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #1e1e1e;
      color: white;
      overflow: hidden;
    }
    #nav-bar {
      display: flex;
      align-items: center;
      background-color: #2d2d2d;
      padding: 8px;
      gap: 8px;
    }
    #url-input {
      flex: 1;
      padding: 8px;
      border: none;
      border-radius: 4px;
      font-size: 14px;
      outline: none;
    }
    button {
      padding: 6px 10px;
      border: none;
      background-color: #0078d7;
      color: white;
      border-radius: 4px;
      cursor: pointer;
      font-size: 14px;
    }
    #tabs {
      display: flex;
      background-color: #1c1c1c;
      overflow-x: auto;
      border-bottom: 1px solid #333;
    }
    .tab {
      padding: 8px 12px;
      cursor: pointer;
      white-space: nowrap;
      background-color: #2a2a2a;
      border-right: 1px solid #444;
    }
    .tab.active {
      background-color: #0078d7;
    }
    #iframe-container {
      width: 100%;
      height: calc(100vh - 90px);
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <div id="nav-bar">
    <input type="text" id="url-input" placeholder="Digite uma URL ou arquivo local">
    <button onclick="novaAba()">Nova Aba</button>
    <button onclick="navegar()">Ir</button>
  </div>
  <div id="tabs"></div>
  <div id="iframe-container"></div>  <script>
    let abas = [];
    let abaAtiva = null;

    function novaAba(url = '') {
      const id = 'aba-' + Date.now();
      const iframe = document.createElement('iframe');
      iframe.id = id;
      iframe.src = url || 'about:
<button id="installBtn" hidden>Instalar Mini Windows</button>
{
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#1a1a1a",
  "icons": [
    {
      "src": "icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icons/icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
<div id="config-panel" class="settings">
  <h2>Configurações</h2>

  <label>Tema:
    <select id="theme-select">
      <option value="light">Claro</option>
      <option value="dark">Escuro</option>
      <option value="custom">Personalizado</option>
    </select>
  </label>

  <label>Cor personalizada:
    <input type="color" id="custom-color" value="#1a73e8">
  </label>

  <label>Papel de parede:
    <input type="file" id="wallpaper-upload" accept="image/*">
  </label>

  <label>
    <input type="checkbox" id="toggle-animations"> Desativar animações
  </label>

  <label>
    <input type="checkbox" id="toggle-start-menu"> Mostrar menu iniciar
  </label>
:root {
  --theme-color: #ffffff;
  --background-image: none;
  --animations: all 0.3s ease;
}

body {
  background-color: var(--theme-color);
  background-image: var(--background-image);
  background-size: cover;
  background-position: center;
  transition: var(--animations);
}

.no-animations * {
  transition: none !important;
  animation: none !important;
}

#start-menu {
  display: block;
}

#start-menu.hidden {
  display: none;
}

.settings {
  background: rgba(255,255,255,0.9);
  padding: 1em;
  max-width: 300px;
  border-radius: 10px;
}
  <button onclick="resetSettings()">Redefinir</button>
</div>
<script>
(function optimizeMiniWindows() {
  // 1. Remove animações e transições pesadas
  const disableAnimations = () => {
    const style = document.createElement('style');
    style.innerHTML = `
      * {
        transition: none !important;
        animation: none !important;
        will-change: auto !important;
      }
    `;
    document.head.appendChild(style);
  };

  // 2. Remove elementos ocultos do DOM para liberar memória
  const cleanHiddenElements = () => {
    document.querySelectorAll('body *').forEach(el => {
      const style = getComputedStyle(el);
      if (style.display === 'none' || style.visibility === 'hidden') {
        el.remove();
      }
    });
  };

  // 3. Lazy load de imagens
  const enableLazyLoad = () => {
    document.querySelectorAll('img').forEach(img => {
      if (!img.loading) img.loading = "lazy";
    });
  };

  // 4. Compactar grandes estruturas em fragmentos
  const fragmentWrap = (parentSelector) => {
    const parent = document.query
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pintura@10.0.0/pintura.css" />
<script src="https://cdn.jsdelivr.net/npm/pintura@10.0.0/pintura.iife.js"></script>
<button onclick="abrirEditorImagem()">Abrir Editor de Imagem</button>
<input type="file" id="imagemInput" accept="image/*" hidden>
