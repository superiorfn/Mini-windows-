<link rel="manifest" href="manifest.json" />
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/service-worker.js');
  }
</script>{
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "description": "Um sistema Mini Windows portátil, leve e avançado.",
  "start_url": "/index.html",
  "display": "standalone",
  "background_color": "#121212",
  "theme_color": "#0078D7",
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
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "description": "Um sistema Mini Windows portátil, leve e avançado.",
  "start_url": "/index.html",
  "display": "standalone",
  "background_color": "#121212",
  "theme_color": "#0078D7",
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
}MiniWindows/
├── index.html
├── manifest.json         ← ⬇️ Abaixo
├── service-worker.js     ← ⬇️ Abaixo
├── script.js
├── style.css
├── icons/
│   ├── icon-192.png
│   └── icon-512.pngsetWallpaper("url-da-imagem.jpg");// Mini Windows Kernel
document.addEventListener("DOMContentLoaded", () => {
  const zIndexStart = 100;
  let zCounter = zIndexStart;

  // Permitir mover janelas
  document.querySelectorAll('.window').forEach(win => {
    const header = win.querySelector('.window-header');
    let isDragging = false, offsetX, offsetY;

    header.addEventListener('mousedown', (e) => {
      isDragging = true;
      offsetX = e.clientX - win.offsetLeft;
      offsetY = e.clientY - win.offsetTop;
      bringToFront(win);
    });

    document.addEventListener('mouseup', () => isDragging = false);
    document.addEventListener('mousemove', (e) => {
      if (isDragging) {
        win.style.left = (e.clientX - offsetX) + 'px';
        win.style.top = (e.clientY - offsetY) + 'px';
      }
    });
  });

  // Traz janela para frente
  function bringToFront(win) {
    zCounter++;
    win.style.zIndex = zCounter;
  }

  // Abrir e fechar
  window.openWindow = (id) => {
    const win = document.getElementById(id);
    if (win) {
      win.style.display = "flex";
      bringToFront(win);
    }
  };

  window.closeWindow = (id) => {
    const win = document.getElementById(id);
    if (win) win.style.display = "none";
  };

  // Salvar configs básicas
  loadWallpaper();

  function loadWallpaper() {
    const bg = localStorage.getItem("mini_bg");
    if (bg) document.body.style.backgroundImage = `url('${bg}')`;
  }

  // Expor função global para mudar wallpaper
  window.setWallpaper = (url) => {
    document.body.style.backgroundImage = `url('${url}')`;
    localStorage.setItem("mini_bg", url);
  };
});MiniWindows/
├── index.html
├── script.js          ← núcleo do sistema (te entrego abaixo)
├── style.css
├── apps/
│   ├── pintura.js
│   ├── vscode.js
│   ├── antivirus.js
│   └── ...
└── manifest.json      ← para tornar instalável<!-- Mini Antivírus -->
<div id="antivirusWindow" class="window">
  <div class="window-header">
    🛡️ Mini Antivírus
    <button class="close-btn" onclick="closeWindow('antivirusWindow')">X</button>
  </div>
  <div class="window-body" style="padding:10px">
    <h3>🔍 Escanear Arquivo</h3>
<!-- Mini Antivírus -->
<div id="antivirusWindow" class="window">
  <div class="window-header">
    🛡️ Mini Antivírus
    <button class="close-btn" onclick="closeWindow('antivirusWindow')">X</button>
  </div>
  <div class="window-body" style="padding:10px">
    <h3>🔍 Escanear Arquivo</h3>
    <input type="file" onchange="escanearArquivo(event)"><br><br>

    <h3>🌐 Verificar Link</h3>
    <input type="text" id="urlInput" placeholder="https://exemplo.com" style="width:90%">
    <button onclick="verificarURL()">Verificar</button><br><br>

    <h3>💻 Analisar Código</h3>
    <textarea id="codeInput" placeholder="Cole aqui seu código..." style="width:100%; height:100px;"></textarea><br>
    <button onclick="analisarCodigo()">Analisar Código</button>

    <hr>
    <div id="antivirusOutput" style="white-space: pre-line;"></div>
  </div>
</div>    <input type="file" onchange="escanearArquivo(event)"><br><br>

    <h3>🌐 Verificar Link</h3>
    <input type="text" id="urlInput" placeholder="https://exemplo.com" style="width:90%">
    <button onclick="verificarURL()">Verificar</button><br><br>

    <h3>💻 Analisar Código</h3>
    <textarea id="codeInput" placeholder="Cole aqui seu código..." style="width:100%; height:100px;"></textarea><br>
    <button onclick="analisarCodigo()">Analisar Código</button>

    <hr>
    <div id="antivirusOutput" style="white-space: pre-line;"></div>
  </div>
</div<script>
  function abrirEditorImagem() {
    document.getElementById('imagemInput').click();
  }

  document.getElementById('imagemInput').addEventListener('change', (e) => {
    const file = e.target.files[0];
    if (!file) return;

    const reader = new FileReader();
    reader.onload = () => {
      Pintura.openDefaultEditor({
        src: reader.result,
        imageReader: Pintura.createDefaultImageReader(),
        imageWriter: Pintura.createDefaultImageWriter(),
        util: Pintura.util,
        locale: Pintura.locales.en, // pode mudar para pt
        onProcess: (output) => {
          const link = document.createElement('a');
          link.href = output.dest;
          link.download = 'imagem-editada.png';
          link.click();
        },
      });
    };
    reader.readAsDataURL(file);
  });
</script>https://cdn.jsdelivr.net/npm/pintura@10.0.0/pintura.cssmini-windows/
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
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mini Windows Avançado</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/pintura@10.0.0/pintura.css" />
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      background: #0e0e0e;
      color: white;
      overflow: hidden;
    }
    .taskbar {
      position: fixed;
      bottom: 0;
      width: 100%;
      background: #1a1a1a;
      padding: 5px;
      display: flex;
      gap: 10px;
      justify-content: center;
      z-index: 1000;
    }
    button {
      background: #333;
      color: white;
      padding: 8px 12px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    .window {
      position: absolute;
      top: 60px;
      left: 50px;
      width: 80%;
      max-width: 800px;
      height: 70%;
      background: #222;
      border: 1px solid #444;
      box-shadow: 0 0 15px #000;
      display: none;
      flex-direction: column;
      z-index: 900;
    }
    .window-header {
      background: #111;
      padding: 8px;
      cursor: move;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .window-body {
      flex: 1;
      overflow: auto;
      background: #1b1b1b;
    }
    .close-btn {
      background: #e00;
      border: none;
      color: white;
      padding: 2px 8px;
      cursor: pointer;
    }
    .resizer {
      width: 100%;
      height: 10px;
      cursor: ns-resize;
    }
    iframe, canvas, div.editor {
      width: 100%;
      height: 100%;
    }
  </style>
</head>
<body>

  <!-- Taskbar -->
  <div class="taskbar">
    <button onclick="openWindow('imageEditor')">🎨 Editor de Imagem</button>
    <button onclick="openWindow('audioEditor')">🎧 Editor de Áudio</button>
    <button onclick="openWindow('codeEditor')">💻 Editor de Código</button>
  </div>

  <!-- Editor de Imagem -->
  <div id="imageEditor" class="window">
    <div class="window-header">
      🎨 Editor de Imagem
      <button class="close-btn" onclick="closeWindow('imageEditor')">X</button>
    </div>
    <div class="window-body">
      <input type="file" accept="
<button onclick="openWindow('antivirusWindow')">🛡️ Mini Antivírus</button>
function escanearArquivo(event) {
  const file = event.target.files[0];
  const output = document.getElementById("antivirusOutput");
  if (!file) return;

  const reader = new FileReader();
  reader.onload = function () {
    const content = reader.result;
    let alerts = [];

    // Verificações básicas
    if (/eval
<script src="script.js"></script>
{
  "name": "Mini Windows",
  "short_name": "MiniOS",
  "start_url": "./index.html",
  "display": "standalone",
  "background_color": "#000000",
  "theme_color": "#0078D7",
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
const CACHE_NAME = "mini-windows-cache-v1";
const urlsToCache = [
  "/",
  "/index.html",
  "/script.js",
  "/style.css",
  "/manifest.json"
];

self.addEventListener("install", (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then((cache) => cache.addAll(urlsToCache))
  );
});

self.addEventListener("fetch", (event) => {
  event.respondWith(
    caches.match(event.request)
      .then((response) => response || fetch(event.request))
  );
});
<link rel="manifest" href="manifest.json">
<meta name="theme-color" content="#0078D7">
<script>
  if ("serviceWorker" in navigator) {
    navigator.serviceWorker.register("service-worker.js")
      .then(() => console.log("✅ Service Worker registrado"))
      .catch((err) => console.error("SW error:", err));
  }
</script>
<div class="window" id="boxedwine">
  <div class="window-header">BoxedWine</div>
  <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:0;"></iframe>
</div>
<div class="window" id="boxedwine">
  <div class="window-header">BoxedWine</div>
  <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:0;"></iframe>
</div><div class="window" id="boxedwine">
  <div class="window-header">BoxedWine</div>
  <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:0;"></iframe>
</div><div class="window" id="boxedwine">
  <div class="window-header">BoxedWine</div>
  <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:0;"></iframe>
</div><div class="window" id="boxedwine">
  <div class="window-header">BoxedWine</div>
  <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:0;"></iframe>
</div>MiniWindows/
└── apps/
    └── boxedwine/
        ├── index.html
        ├── boxedwine.js
        ├── boxedwine.wasm
        ├── wineData/
        └── app.exe  ← (exemplo)
<!-- Janela BoxedWine -->
<div class="window" id="boxedwineWindow">
  <div class="window-header">
    🧪 Emulador BoxedWine
    <button class="close-btn" onclick="closeWindow('boxedwineWindow')">X</button>
  </div>
  <div class="window-body" style="padding:0; height:80vh;">
    <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:none;"></iframe>
  </div>
</div><!-- Janela BoxedWine -->
<div class="window" id="boxedwineWindow">
  <div class="window-header">
    🧪 Emulador BoxedWine
    <button class="close-btn" onclick="closeWindow('boxedwineWindow')">X</button>
  </div>
  <div class="window-body" style="padding:0; height:80vh;">
    <iframe src="apps/boxedwine/index.html" style="width:100%; height:100%; border:none;"></iframe>
calculator.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Calculadora Avançada</title>
  <style>
    body {
      font-family: sans-serif;
      margin: 0;
      background: #121212;
      color: white;
    }
    #calc {
      max-width: 400px;
      margin: auto;
      padding: 20px;
    }
    #display {
      width: 100%;
      height: 60px;
      font-size: 24px;
      margin-bottom: 10px;
      background: #1e1e1e;
      color: white;
      text-align: right;
      padding: 10px;
      box-sizing: border-box;
      border: none;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }
    button {
      padding: 15px;
      font-size: 18px;
<div class="window" id="calcWindow">
  <div class="window-header">
    🧮 Calculadora Avançada
    <button onclick="closeWindow('calcWindow')">X</button>
  </div>
  <div class="window-body" style="height:80vh;padding:0;">
    <iframe src="apps/calculadora/calculator.html" style="width:100%; height:100%; border:none;"></iframe>
  </div>
</div><button onclick="openWindow('calcWindow')">🧮 Calculadora</button>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Calculadora Avançada</title>
  <style>
    :root {
      --bg: #121212;
      --fg: white;
      --btn: #333;
      --btn-hover: #444;
      --accent: #0078D7;
    }
    body.light {
      --bg: #f0f0f0;
      --fg: #111;
      --btn: #ddd;
      --btn-hover: #ccc;
      --accent: #0078D7;
    }

    body {
      font-family: sans-serif;
      margin: 0;
      background: var(--bg);
      color: var(--fg);
    }

    #calc {
      max-width: 420px;
      margin: auto;
      padding: 20px;
    }

    #display {
      width: 100%;
      height: 60px;
      font-size: 24px;
      background: var(--btn);
      color: var(--fg);
      text-align: right;
      padding: 10px;
      border: none;
      box-sizing: border-box;
    }

    #preview {
      text-align: right;
      color: gray;
      font-size: 16px;
      margin-bottom: 5px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 18px;
      background: var(--btn);
      border: none;
      color: var(--fg);
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: var(--btn-hover);
    }

    .equal {
      background: var(--accent);
      grid-column: span 5;
    }

    .equal:hover {
      background: #005fa3;
    }

    #history {
      margin-top: 20px;
      font-size: 14px;
      background: var(--btn);
      padding: 10px;
      max-height: 100px;
      overflow-y: auto;
      border-radius: 5px;
    }

    #themeToggle {
      margin-top: 10px;
      text-align: center;
    }
  </style>
</head>
<body>
  <div id="calc">
    <div id="preview"></div>
    <input type="text" id="display" readonly>

    <div class="buttons">
      <button onclick="input('7')">7</button>
      <button onclick="input('8')">8</button>
      <button onclick="input('9')">9</button>
      <button onclick="input('/')">÷</button>
      <button onclick="clearDisplay()">C</button>

      <button onclick="input('4')">4</button>
      <button onclick="input('5')">5</button>
      <button onclick="input('6')">6</button>
      <button onclick="input('*')">×</button>
      <button onclick="del()">←</button>

      <button onclick="input('1')">1</button>
      <button onclick="input('2')">2</button>
      <button onclick="input('3')">3</button>
      <button onclick="input('-')">−</button>
      <button onclick="input('(')">(</button>

      <button onclick="input('0')">0</button>
      <button onclick="input('.')">.</button>
      <button onclick="input('%')">%</button>
      <button onclick="input('+')">+</button>
      <button onclick="input(')')">)</button>

      <button onclick="func('sqrt')">√</button>
      <button onclick="func('square')">x²</button>
      <button onclick="func('recip')">1/x</button>
      <button onclick="input('Math.PI')">π</button>
      <button onclick="input('Math.E')">e</button>

      <button onclick="func('sin')">sin</button>
      <button onclick="func('cos')">cos</button>
      <button onclick="func('tan')">tan</button>
      <button onclick="func('log')">log</button>
      <button onclick="func('ln')">ln</button>

      <button class="equal" onclick="calculate()">=</button>
    </div>

    <div id="themeToggle">
      <button onclick="toggleTheme()">🌓 Mudar Tema</button>
    </div>

    <div id="history"></div>
  </div>

  <script>
    const display = document.getElementById('display');
    const preview = document.getElementById('preview');
    const history = document.getElementById('history');

    function input(value) {
      display.value += value;
      updatePreview();
    }

    function clearDisplay() {
      display.value = '';
      preview.textContent = '';
    }

    function del() {
      display.value = display.value.slice(0, -1);
      updatePreview();
    }

    function func(name) {
      if (!display.value) return;
      try {
        const x = eval(display.value);
        let result;
        switch (name) {
          case 'sqrt': result = Math.sqrt(x); break;
          case 'square': result = x ** 2; break;
          case 'recip': result = 1 / x; break;
          case 'sin': result = Math.sin(x); break;
          case 'cos': result = Math.cos(x); break;
          case 'tan': result = Math.tan(x); break;
          case 'log': result = Math.log10(x); break;
          case 'ln': result = Math.log(x); break;
        }
        display.value = result;
        preview.textContent = '';
      } catch {
        display.value = 'Erro';
      }
    }

    function calculate() {
      try {
        const expr = display.value;
        const result = eval(expr);
        display.value = result;
        preview.textContent = '';
        history.innerHTML += `<div>${expr} = ${result}</div>`;
      } catch {
        display.value = 'Erro';
      }
    }

    function updatePreview() {
      try {
        const result = eval(display.value);
        preview.textContent = `= ${result}`;
      } catch {
        preview.textContent = '';
      }
    }

    function toggleTheme() {
      document.body.classList.toggle('light');
    }

    // Suporte a teclado físico
    document.addEventListener('keydown', (e) => {
      if (/\d|\+|\-|\*|\/|||\./.test(e.key)) {
        input(e.key);
      } else if (e.key === 'Backspace') {
        del();
      } else if (e.key === 'Enter') {
        e.preventDefault();
        calculate();
      } else if (e.key === 'c' || e.key === 'Escape') {
        clearDisplay();
      }
    });
  </script>
</body>
</html>
const CACHE_NAME = "miniwin-v1";
const ASSETS = [
  "/",
  "/index.html",
  "/manifest.json",
  "/icons/icon-192.png",
  "/icons/icon-512.png",
  "/apps/calculadora/calculator.html"
  // Adicione mais arquivos e apps aqui
];

self.addEventListener("install", (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => cache.addAll(ASSETS))
  );
});

self.addEventListener("fetch", (event) => {
  event.respondWith(
    caches.match(event.request).then(
      (resp) => resp || fetch(event.request)
    )
  );
});
{
  "build": {
    "beforeBuildCommand": "",
    "beforeDevCommand": "",
    "devPath": "../MiniWindows",
    "distDir": "../MiniWindows"
  },
  "package": {
    "productName": "MiniWindows",
    "version": "1.0.0"
  },
  "tauri": {
    "windows": [
      {
        "title": "Mini Windows",
        "width": 1280,
        "height": 800
      }
    ]
  }
}
npm run tauri build
npm install @capacitor/core @capacitor/cli
npx cap init miniwindows com.exemplo.miniwindows
npx cap add android
npx cap copy
npx cap open android
npm create tauri-app
mkdir miniwindows-exe
cd miniwindows-exe
npm create tauri-app 
mkdir miniwindows-exe
cd miniwindows-exe
npm create tauri-app{
  "build": {
    "beforeBuildCommand": "",
    "beforeDevCommand": "",
    "devPath": "../MiniWindows",
    "distDir": "../MiniWindows"
  },
  "package": {
    "productName": "Mini Windows",
    "version": "1.0.0"
  },
  "tauri": {
    "windows": [
      {
        "title": "Mini Windows",
        "width": 1280,
        "height": 800,
        "resizable": true
      }
    ],
    "bundle": {
      "identifier": "com.miniwindows.app",
      "icon": ["icons/icon.ico"],
      "targets": ["msi", "nsis"]
    }
  }
}
npm install
npm run tauri build
{
  "build": {
    "beforeBuildCommand": "",
    "beforeDevCommand": "",
    "devPath": "../MiniWindows",
    "distDir": "../MiniWindows"
  },
  "package": {
    "productName": "Mini Windows",
    "version": "1.0.0"
  },
  "tauri": {
    "windows": [
      {
        "title": "Mini Windows",
        "width": 1280,
        "height": 800,
        "resizable": true
      }
    ],
    "bundle": {
      "identifier": "com.miniwindows.app",
      "icon": ["icons/icon.ico"],
      "targets": ["msi", "nsis"]
    }
  }
}
src-tauri/target/release/bundle/nsis/Mini Windows_1.0.0_x64-setup.exe
// Libera recursos de janelas inativas
function optimizeWindowsMemory() {
  const windows = document.querySelectorAll(".app-window");
  windows.forEach(win => {
    if (!win.classList.contains("active")) {
      // Se a janela estiver oculta ou minimizada, descarrega conteúdo pesado
      const iframes = win.querySelectorAll("iframe, video, audio");
      iframes.forEach(el => {
        el.src = ""; // descarrega recursos pesados
      });
    }
  });
}

// Coleta lixo manual em intervalos (simulado)
function forceMemoryCleanup() {
  if (window.gc) window.gc(); // para navegadores com GC manual (raro)
  console.log("Tentando liberar memória inativa...");
  optimizeWindowsMemory();
}

// Remove listeners antigos
function cleanEventListeners() {
  // Exemplo: remove handlers órfãos
  document.querySelectorAll("*").forEach(el => {
    el.onclick = null;
    el.onmouseover = null;
    el.onmousemove = null;
    el.onkeydown = null;
  });
}

// Reduz uso de memória em loops e timers
function optimizeTimers() {
  let heavyTimers = window.__timers || [];
  heavyTimers.forEach(id => clearInterval(id));
  window.__timers = [];
}

// Rodar automaticamente a cada 30s
setInterval(() => {
  forceMemoryCleanup();
  cleanEventListeners();
  optimizeTimers();
}, 30000);
<script src="scripts/memory-optimizer.js" defer></script>
sudo apt install webp    # Linux
brew install webp        # macOS

# Exemplo de conversão
cwebp wallpaper.jpg -o wallpaper.webp
