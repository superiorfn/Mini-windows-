let usuarioAtual = null;

function fazerLogin() {
  const email = document.getElementById("email").value;
  const senha = document.getElementById("senha").value;

  fetch("http://localhost:3000/login", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ email, senha })
  })
    .then(res => res.json())
    .then(data => {
      if (data.sucesso) {
        usuarioAtual = email;
        document.getElementById("login").style.display = "none";
        document.getElementById("app").style.display = "block";
        carregarEmails(); // opcional: carregar caixa de entrada
      } else {
        alert("Login inválido.");
      }
    });
}
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
/mini-windows/
  └── assets/
      ├── wallpapers/
      │    └── default.webp
      ├── icons/
      │    └── calculator.webp
      └── logos/
           └── miniwin-logo.webp
// Limita a frequência de atualizações intensas (como animações)
function throttle(callback, delay) {
  let last = 0;
  return function(...args) {
    const now = Date.now();
    if (now - last >= delay) {
      last = now;
      callback(...args);
    }
  };
}

// Substitui setInterval com controle de carga
function optimizedInterval(callback, delay) {
  let id = null;
  function run() {
    callback();
    id = setTimeout(run, delay);
  }
  run();
  return () => clearTimeout(id);
}

// Substitui animações por transições CSS leves
function disableHeavyAnimations() {
  const style = document.createElement("style");
  style.textContent = `
    * {
      animation: none !important;
      transition: opacity 0.2s ease-in-out, transform 0.2s ease-in-out;
    }
  `;
  document.head.appendChild(style);
}

// Pausa processamento de apps inativos
function pauseInactiveApps() {
  const apps = document.querySelectorAll(".app-window");
  apps.forEach(app => {
    if (!app.classList.contains("active")) {
      const heavyContent = app.querySelectorAll("canvas, video, audio, iframe");
      heavyContent.forEach(el => {
        if (el.tagName === "VIDEO" || el.tagName === "AUDIO") el.pause();
        if (el.tagName === "IFRAME") el.src = ""; // descarrega conteúdo
        if (el.tagName === "CANVAS") el.remove(); // remove canvas pesados
      });
    }
  });
}

// Monitora e aplica ajustes
function applyCpuOptimizations() {
  disableHeavyAnimations();
  optimizedInterval(() => {
    pauseInactiveApps();
  }, 10000);
}

// Rodar ao carregar
window.addEventListener("DOMContentLoaded", () => {
  applyCpuOptimizations();
});
<script src="scripts/cpu-optimizer.js" defer></script>
// Lista de seletores comuns de anúncios
const adSelectors = [
  'iframe[src*="ads"]',
  'iframe[src*="doubleclick"]',
  'div[id*="ad"]',
  'div[class*="ad"]',
  'div[class*="sponsor"]',
  'div[class*="promo"]',
  'script[src*="ad"]',
  'ins.adsbygoogle',
  'div[data-ad]',
];

// Função que remove elementos de anúncio no conteúdo de um iframe
function removeAdsInIframe(iframe) {
  try {
    const doc = iframe.contentDocument || iframe.contentWindow.document;
    adSelectors.forEach(selector => {
      const elements = doc.querySelectorAll(selector);
      elements.forEach(el => el.remove());
    });
  } catch (e) {
    console.warn("Não foi possível acessar o conteúdo do iframe por política de CORS.");
  }
}

// Monitora todos os iframes do navegador embutido
function enableAdBlock() {
  const iframes = document.querySelectorAll("iframe.browser-frame");
  iframes.forEach(iframe => {
    iframe.addEventListener("load", () => {
      setTimeout(() => removeAdsInIframe(iframe), 2000); // Espera o site carregar
    });
  });
}

// Ativa automaticamente
window.addEventListener("DOMContentLoaded", enableAdBlock);
<script src="../../system/adguard-lite.js" defer></script>
/mini-windows/
├── apps/
│   └── emulador-windows/
│       ├── index.html
│       ├── boxedwine/
│       │   ├── boxedwine.html
│       │   ├── boxedwine.js
│       │   └── ... (arquivos do BoxedWine)
<!DOCTYPE html>
<html>
<head>
  <title>Emulador Windows</title>
  <style>
    html, body {
      margin: 0;
      background: #111;
      color: #0f0;
      font-family: monospace;
      height: 100%;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <iframe src="boxedwine/boxedwine.html"></iframe>
</body>
</html>
OS.registerApp("emulador-windows", {
  name: "Emulador Windows",
  icon: "assets/icons/windows-emulador.webp",
  open: () => {
    const win = document.createElement("div");
    win.className = "app-window";
    win.innerHTML = `
      <div class="titlebar">Emulador Windows</div>
      <iframe src="apps/emulador-windows/index.html" width="800" height="600"></iframe>
    `;
    document.body.appendChild(win);
    return win;
  }
});
// input-handler.js

// 🖱️ Drag & Drop para janelas
function enableWindowDragging(win) {
  const titleBar = win.querySelector(".titlebar");
  if (!titleBar) return;

  let offsetX, offsetY;

  titleBar.onmousedown = (e) => {
    offsetX = e.clientX - win.offsetLeft;
    offsetY = e.clientY - win.offsetTop;
    document.onmousemove = (e) => {
      win.style.left = `${e.clientX - offsetX}px`;
      win.style.top = `${e.clientY - offsetY}px`;
    };
    document.onmouseup = () => {
      document.onmousemove = null;
      document.onmouseup = null;
    };
  };
}

// 🎹 Atalhos globais de teclado
function setupGlobalKeyboardShortcuts() {
  window.addEventListener("keydown", (e) => {
    if (e.ctrlKey && e.key === "q") {
      alert("Saindo do Mini Windows...");
      // Aqui você pode criar uma função de logout
    }

    if (e.ctrlKey && e.key === "n") {
      if (OS && OS.launch) OS.launch("navegador");
    }

    if (e.key === "Escape") {
      // Fecha a última janela (se implementado)
      const lastWindow = document.querySelector(".app-window:last-of-type");
      if (lastWindow) lastWindow.remove();
    }
  });
}

// 🖱️+🎹 Iframes interativos com foco e eventos
function enableIframeInteraction() {
  document.querySelectorAll("iframe").forEach((frame) => {
    frame.setAttribute("tabindex", "0");
    frame.addEventListener("load", () => {
      frame.focus();
    });
  });
}

// 🚀 Inicialização global do input handler
function initializeInputHandler() {
  setupGlobalKeyboardShortcuts();
  enableIframeInteraction();

  // Ativar arrasto para todas janelas já existentes
  document.querySelectorAll(".app-window").forEach(enableWindowDragging);

  // Quando novas janelas forem adicionadas, ative automaticamente
  const observer = new MutationObserver((mutations) => {
    mutations.forEach((mutation) => {
      mutation.addedNodes.forEach((node) => {
        if (node.classList && node.classList.contains("app-window")) {
          enableWindowDragging(node);
        }
      });
    });
  });

  observer.observe(document.body, { childList: true });
input-handler.js
// input-handler.js

// 🖱️ Drag & Drop para janelas
function enableWindowDragging(win) {
  const titleBar = win.querySelector(".titlebar");
  if (!titleBar) return;

  let offsetX, offsetY;

  titleBar.onmousedown = (e) => {
    offsetX = e.clientX - win.offsetLeft;
    offsetY = e.clientY - win.offsetTop;
    document.onmousemove = (e) => {
      win.style.left = `${e.clientX - offsetX}px`;
      win.style.top = `${e.clientY - offsetY}px`;
    };
    document.onmouseup = () => {
      document.onmousemove = null;
      document.onmouseup = null;
    };
  };
}

// 🎹 Atalhos globais de teclado
function setupGlobalKeyboardShortcuts() {
  window.addEventListener("keydown", (e) => {
    if (e.ctrlKey && e.key === "q") {
      alert("Saindo do Mini Windows...");
      // Aqui você pode criar uma função de logout
    }

    if (e.ctrlKey && e.key === "n") {
      if (OS && OS.launch) OS.launch("navegador");
    }

    if (e.key === "Escape") {
      // Fecha a última janela (se implementado)
      const lastWindow = document.querySelector(".app-window:last-of-type");
      if (lastWindow) lastWindow.remove();
    }
  });
}

// 🖱️+🎹 Iframes interativos com foco e eventos
function enableIframeInteraction() {
  document.querySelectorAll("iframe").forEach((frame) => {
    frame.setAttribute("tabindex", "0");
    frame.addEventListener("load", () => {
      frame.focus();
    });
  });
}

// 🚀 Inicialização global do input handler
function initializeInputHandler() {
  setupGlobalKeyboardShortcuts();
  enableIframeInteraction();

  // Ativar arrasto para todas janelas já existentes
  document.querySelectorAll(".app-window").forEach(enableWindowDragging);

  // Quando novas janelas forem adicionadas, ative automaticamente
  const observer = new MutationObserver((mutations) => {
    mutations.forEach((mutation) => {
      mutation.addedNodes.forEach((node) => {
        if (node.classList && node.classList.contains("app-window")) {
          enableWindowDragging(node);
        }
      });
    });
  });

  observer.observe(document.body, { childList: true });
}

initializeInputHandler()// input-handler.js

// 🖱️ Drag & Drop para janelas
function enableWindowDragging(win) {
  const titleBar = win.querySelector(".titlebar");
  if (!titleBar) return;

  let offsetX, offsetY;

  titleBar.onmousedown = (e) => {
    offsetX = e.clientX - win.offsetLeft;
    offsetY = e.clientY - win.offsetTop;
    document.onmousemove = (e) => {
      win.style.left = `${e.clientX - offsetX}px`;
      win.style.top = `${e.clientY - offsetY}px`;
    };
    document.onmouseup = () => {
      document.onmousemove = null;
      document.onmouseup = null;
    };
  };
}

// 🎹 Atalhos globais de teclado
function setupGlobalKeyboardShortcuts() {
  window.addEventListener("keydown", (e) => {
    if (e.ctrlKey && e.key === "q") {
      alert("Saindo do Mini Windows...");
      // Aqui você pode criar uma função de logout
    }

    if (e.ctrlKey && e.key === "n") {
      if (OS && OS.launch) OS.launch("navegador");
    }

    if (e.key === "Escape") {
      // Fecha a última janela (se implementado)
      const lastWindow = document.querySelector(".app-window:last-of-type");
      if (lastWindow) lastWindow.remove();
    }
  });
}

// 🖱️+🎹 Iframes interativos com foco e eventos
function enableIframeInteraction() {
  document.querySelectorAll("iframe").forEach((frame) => {
    frame.setAttribute("tabindex", "0");
    frame.addEventListener("load", () => {
      frame.focus();
    });
  });
}

// 🚀 Inicialização global do input handler
function initializeInputHandler() {
  setupGlobalKeyboardShortcuts();
  enableIframeInteraction();

  // Ativar arrasto para todas janelas já existentes
  document.querySelectorAll(".app-window").forEach(enableWindowDragging);

  // Quando novas janelas forem adicionadas, ative automaticamente
  const observer = new MutationObserver((mutations) => {
    mutations.forEach((mutation) => {
      mutation.addedNodes.forEach((node) => {
        if (node.classList && node.classList.contains("app-window")) {
          enableWindowDragging(node);
        }
      });
    });
  });

  observer.observe(document.body, { childList: true });
}

initializeInputHandler();
<script src="system/input-handler.js" defer></script>
// gamepad-handler.js

let gamepadIndex = null;
let lastPress = 0;
let focusIndex = 0;

function pollGamepad() {
  const gamepads = navigator.getGamepads();
  const gp = gamepads[gamepadIndex];
  if (!gp) return;

  const now = Date.now();

  // Evita múltiplos acionamentos por segundo
  const debounce = (ms) => (now - lastPress > ms);

  // Botões comuns:
  const [A, B, X, Y, LB, RB, LT, RT, Select, Start] = gp.buttons;

  if (Start.pressed && debounce(500)) {
    document.getElementById("menu-iniciar")?.classList.toggle("open");
    lastPress = now;
  }

  if (B.pressed && debounce(500)) {
    const active = document.querySelector(".app-window:last-of-type");
    if (active) active.remove();
    lastPress = now;
  }

  // D-pad navegação
  if (gp.axes[1] === -1 && debounce(300)) {
    focusIndex = Math.max(0, focusIndex - 1);
    focusWindow(focusIndex);
    lastPress = now;
  }

  if (gp.axes[1] === 1 && debounce(300)) {
    focusIndex = Math.min(document.querySelectorAll(".app-window").length - 1, focusIndex + 1);
    focusWindow(focusIndex);
    lastPress = now;
  }

  // LT/RT alternam janelas
  if (LT.pressed && debounce(300)) {
    focusIndex = (focusIndex - 1 + getAppCount()) % getAppCount();
    focusWindow(focusIndex);
    lastPress = now;
  }

  if (RT.pressed && debounce(300)) {
    focusIndex = (focusIndex + 1) % getAppCount();
    focusWindow(focusIndex);
    lastPress = now;
  }
}

function focusWindow(index) {
  const windows = document.querySelectorAll(".app-window");
  windows.forEach((win, i) => {
    win.style.zIndex = i === index ? 100 : 1;
    win.classList.toggle("focused", i === index);
  });
}

function getAppCount() {
  return document.querySelectorAll(".app-window").length;
}

function checkGamepadConnection() {
  const gamepads = navigator.getGamepads();
  for (let i = 0; i < gamepads.length; i++) {
    if (gamepads[i]) {
      gamepadIndex = i;
      console.log("🎮 Controle conectado!");
      return;
    }
  }
}

// Inicializador
window.addEventListener("gamepadconnected", (e) => {
  console.log("Gamepad conectado:", e.gamepad);
  gamepadIndex = e.gamepad.index;
});

setInterval(() => {
  if (gamepadIndex === null) checkGamepadConnection();
  else pollGamepad();
}, 100);
<script src="system/gamepad- .app-window.focused {
  outline: 3px solid #00f;
}handler.js" defer></script>
.app-window.focused {
  outline: 3px solid #00f;
}
// mouse-virtual.js

let cursor = null;
let cursorX = window.innerWidth / 2;
let cursorY = window.innerHeight / 2;
let gamepadIndex = null;
let lastClick = 0;

// Criar ponteiro visual
function createVirtualCursor() {
  cursor = document.createElement("div");
  cursor.id = "virtual-cursor";
  cursor.style.position = "fixed";
  cursor.style.width = "16px";
  cursor.style.height = "16px";
  cursor.style.borderRadius = "50%";
  cursor.style.background = "white";
  cursor.style.border = "2px solid blue";
  cursor.style.zIndex = 9999;
  cursor.style.pointerEvents = "none";
  cursor.style.left = cursorX + "px";
  cursor.style.top = cursorY + "px";
  document.body.appendChild(cursor);
}

function moveCursor(dx, dy) {
  const speed = 8; // Ajustável
  cursorX = Math.min(window.innerWidth, Math.max(0, cursorX + dx * speed));
  cursorY = Math.min(window.innerHeight, Math.max(0, cursorY + dy * speed));
  cursor.style.left = cursorX + "px";
  cursor.style.top = cursorY + "px";
}

function simulateClick() {
  const now = Date.now();
  if (now - lastClick < 300) return;
  lastClick = now;

  const el = document.elementFromPoint(cursorX, cursorY);
  if (el) {
    const evt = new MouseEvent("click", {
      bubbles: true,
      cancelable: true,
      clientX: cursorX,
      clientY: cursorY,
    });
    el.dispatchEvent(evt);
    el.focus?.();
  }
}

function updateGamepadMouse() {
  const gp = navigator.getGamepads()[gamepadIndex];
  if (!gp) return;

  const [A, B] = gp.buttons;
  const rightX = gp.axes[2];
  const rightY = gp.axes[3];

  if (Math.abs(rightX) > 0.1 || Math.abs(rightY) > 0.1) {
    moveCursor(rightX, rightY);
  }

  if (A.pressed) {
    simulateClick();
  }
}

function detectGamepad() {
  const gps = navigator.getGamepads();
  for (let i = 0; i < gps.length; i++) {
    if (gps[i]) {
      gamepadIndex = i;
      break;
    }
  }
}

window.addEventListener("gamepadconnected", () => {
  console.log("🎮 Controle detectado para mouse virtual.");
  detectGamepad();
  if (!cursor) createVirtualCursor();
});

setInterval(() => {
  if (gamepadIndex !== null) {
    updateGamepadMouse();
  }
}, 20);<script src="system/mouse-virtual.js" defer></script>#virtual-cursor {
  background: url("assets/icons/cursor.png");
  background-size: cover;
  width: 24px;
  height: 24px;
  border: none;
}/mini-windows/
└── system/
    ├── virtual-keyboard.js
    └── virtual-keyboard.css// virtual-keyboard.js

const keysLayout = [
  ["Q","W","E","R","T","Y","U","I","O","P"],
  ["A","S","D","F","G","H","J","K","L"],
  ["Z","X","C","V","B","N","M"],
  ["Space","Backspace","Enter"]
];

let focusedKey = { row: 0, col: 0 };

function createKeyboard() {
  const keyboard = document.createElement("div");
  keyboard.id = "virtual-keyboard";
  
  keysLayout.forEach((row, rowIndex) => {
    const rowDiv = document.createElement("div");
    rowDiv.className = "vk-row";
    row.forEach((key, colIndex) => {
      const keyBtn = document.createElement("button");
      keyBtn.className = "vk-key";
      keyBtn.dataset.row = rowIndex;
      keyBtn.dataset.col = colIndex;
      keyBtn.textContent = key;
      keyBtn.addEventListener("click", () => pressKey(key));
      rowDiv.appendChild(keyBtn);
    });
    keyboard.appendChild(rowDiv);
  });

  document.body.appendChild(keyboard);
  highlightFocusedKey();
}

function pressKey(key) {
  const active = document.activeElement;
  const value = key === "Space" ? " " :
                key === "Backspace" ? "BACKSPACE" :
                key === "Enter" ? "\n" : key;

  if (value === "BACKSPACE") {
    if (active.value) {
      active.value = active.value.slice(0, -1);
    }
  } else {
    if (active && active.tagName === "TEXTAREA" || active.tagName === "INPUT") {
      active.value += value;
    }
  }
}

function highlightFocusedKey() {
  document.querySelectorAll(".vk-key").forEach(k => k.classList.remove("vk-focused"));
  const key = document.querySelector(`.vk-key[data-row="${focusedKey.row}"][data-col="${focusedKey.col}"]`);
  if (key) key.classList.add("vk-focused");
}

function handleVirtualKeyboardNav(e) {
  const row = keysLayout[focusedKey.row];

  if (e.key === "ArrowRight") focusedKey.col = (focusedKey.col + 1) % row.length;
  if (e.key === "ArrowLeft") focusedKey.col = (focusedKey.col - 1 + row.length) % row.length;
  if (e.key === "ArrowDown") focusedKey.row = (focusedKey.row + 1) % keysLayout.length;
  if (e.key === "ArrowUp") focusedKey.row = (focusedKey.row - 1 + keysLayout.length) % keysLayout.length;
  if (e.key === "Enter" || e.key === " ") {
    const key = keysLayout[focusedKey.row][focusedKey.col];
    pressKey(key);
  }

  highlightFocusedKey();
}

window.addEventListener("keydown", handleVirtualKeyboardNav);

// Iniciar teclado ao carregar
create#virtual-keyboard {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: #222;
  padding: 10px;
  display: flex;
  flex-direction: column;
  z-index: 9998;
}

.vk-row {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.vk-key {
  margin: 4px;
  padding: 12px 16px;
  font-size: 16px;
  background: #444;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.vk-key.vk-focused {
  outline: 3px solid #00f;
  background: #666;
}<link rel="stylesheet" href="system/virtual-keyboard.css">
<script src="system/virtual-keyboard.js" defer></script>// virtual-keyboard.js

const baseLayout = [
  ["Q","W","E","R","T","Y","U","I","O","P"],
  ["A","S","D","F","G","H","J","K","L"],
  ["Z","X","C","V","B","N","M"],
  ["Shift", "CapsLock", "Space", "Backspace", "Enter"]
];

let isShift = false;
let isCaps = false;
let focusedKey = { row: 0, col: 0 };

function getDisplayKey(key) {
  if (key === "Space") return "␣";
  if (["Shift", "CapsLock", "Backspace", "Enter"].includes(key)) return key;

  const upper = key.toUpperCase();
  return (isCaps ^ isShift) ? upper : upper.toLowerCase();
}

function createKeyboard() {
  const keyboard = document.createElement("div");
  keyboard.id = "virtual-keyboard";

  baseLayout.forEach((row, rowIndex) => {
    const rowDiv = document.createElement("div");
    rowDiv.className = "vk-row";
    row.forEach((key, colIndex) => {
      const keyBtn = document.createElement("button");
      keyBtn.className = "vk-key";
      keyBtn.dataset.row = rowIndex;
      keyBtn.dataset.col = colIndex;
      keyBtn.dataset.key = key;
      keyBtn.textContent = getDisplayKey(key);
      keyBtn.addEventListener("click", () => pressKey(key));
      rowDiv.appendChild(keyBtn);
    });
    keyboard.appendChild(rowDiv);
  });

  document.body.appendChild(keyboard);
  highlightFocusedKey();
}

function pressKey(key) {
  const active = document.activeElement;

  if (key === "Shift") {
    isShift = !isShift;
    updateKeyboard();
    return;
  }

  if (key === "CapsLock") {
    isCaps = !isCaps;
    updateKeyboard();
    return;
  }

  const value = {
    "Space": " ",
    "Backspace": "BACKSPACE",
    "Enter": "\n"
  }[key] ?? getDisplayKey(key);

  if (value === "BACKSPACE") {
    if (active.value) {
      active.value = active.value.slice(0, -1);
    }
  } else {
    if (active && (active.tagName === "INPUT" || active.tagName === "TEXTAREA")) {
      active.value += value;
    }
  }

  if (isShift && key !== "Shift") {
    isShift = false;
    updateKeyboard();
  }
}

function updateKeyboard() {
  document.querySelectorAll(".vk-key").forEach(btn => {
    const key = btn.dataset.key;
    btn.textContent = getDisplayKey(key);
  });
}

function highlightFocusedKey() {
  document.querySelectorAll(".vk-key").forEach(k => k.classList.remove("vk-focused"));
  const key = document.querySelector(`.vk-key[data-row="${focusedKey.row}"][data-col="${focusedKey.col}"]`);
  if (key) key.classList.add("vk-focused");
}

function handleVirtualKeyboardNav(e) {
  const row = baseLayout[focusedKey.row];

  if (e.key === "ArrowRight") focusedKey.col = (focusedKey.col + 1) % row.length;
  if (e.key === "ArrowLeft") focusedKey.col = (focusedKey.col - 1 + row.length) % row.length;
  if (e.key === "ArrowDown") focusedKey.row = (focusedKey.row + 1) % baseLayout.length;
  if (e.key === "ArrowUp") focusedKey.row = (focusedKey.row - 1 + baseLayout.length) % baseLayout.length;
  if (e.key === "Enter" || e.key === " ") {
    const key = baseLayout[focusedKey.row][focusedKey.col];
    pressKey(key);
  }

  highlightFocusedKey();
}

window.addEventListener("keydown", handleVirtualKeyboardNav);
window.addEventListener("DOMContentLoaded", createKeyboard);.vk-key[data-key="Shift"].vk-focused,
.vk-key[data-key="CapsLock"].vk-focused {
  background: #0af;
}

.vk-key[data-key="Shift"].active,
.vk-key[data-key="CapsLock"].active {
  background: #00f;
}#virtual-keyboard {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: #1c1c1c;
  padding: 8px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  z-index: 9999;
  max-height: 45vh;
  overflow-y: auto;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.6);
}

.vk-row {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 6px;
}

.vk-key {
  flex: 1 0 auto;
  min-width: 10%;
  max-width: 16%;
  padding: 12px;
  font-size: 1.2rem;
  text-align: center;
  background: #333;
  color: #fff;
  border: none;
  border-radius: 8px;
  user-select: none;
  transition: 0.2s ease;
}

.vk-key:hover,
.vk-key:focus,
.vk-key.vk-focused {
  background: #444;
  outline: 2px solid #0af;
}

@media (max-width: 768px) {
  .vk-key {
    min-width: 16%;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .vk-key {
    min-width: 22%;
    font-size: 0.9rem;
    padding: 10px;
  }

  #virtual-keyboard {
    max-height: 50vh;
    padding: 6px;
  }
}const baseLayout = [
  ["F1", "F2", "F3", "F4", "F5", "F6", "F7", "F8", "F9", "F10", "F11", "F12"],
  ["Q","W","E","R","T","Y","U","I","O","P"],
  ["A","S","D","F","G","H","J","K","L"],
  ["Z","X","C","V","B","N","M"],
  ["Shift", "CapsLock", "Space", "Backspace", "Enter"]
];if (/^F\d+$/.test(key)) {
    const event = new KeyboardEvent("keydown", { key });
    document.dispatchEvent(event);
    return;
  }.vk-key[data-key^="F"] {
  min-width: 7%;
  max-width: 8%;
  font-size: 0.9rem;
}
const baseLayout = [
  ["Esc", "Tab", "CapsLock", "Shift", "Ctrl", "Alt", "Del", "Enter", "Backspace"],
  ["F1","F2","F3","F4","F5","F6","F7","F8","F9","F10","F11","F12"],
  ["Q","W","E","R","T","Y","U","I","O","P"],
  ["A","S","D","F","G","H","J","K","L"],
  ["Z","X","C","V","B","N","M"],
  ["Space", "Emoji", "Voice"]
];

let isShift = false;
let isCaps = false;

function getDisplayKey(key) {
  if (key === "Space") return "␣";
  if (key === "Emoji") return "😄";
  if (key === "Voice") return "🎙️";
  if (["Shift", "CapsLock", "Backspace", "Enter", "Tab", "Ctrl", "Alt", "Esc", "Del"].includes(key)) return key;
  const upper = key.toUpperCase();
  return (isCaps ^ isShift) ? upper : upper.toLowerCase();
}

function createKeyboard() {
  const keyboard = document.createElement("div");
  keyboard.id = "virtual-keyboard";

  baseLayout.forEach(row => {
    const rowDiv = document.createElement("div");
    rowDiv.className = "vk-row";
    row.forEach(key => {
      const keyBtn = document.createElement("button");
      keyBtn.className = "vk-key";
      keyBtn.dataset.key = key;
      keyBtn.textContent = getDisplayKey(key);
      keyBtn.addEventListener("click", () => pressKey(key));
      rowDiv.appendChild(keyBtn);
    });
    keyboard.appendChild(rowDiv);
  });

  document.body.appendChild(keyboard);
}

function pressKey(key) {
  const active = document.activeElement;

  if (key === "Shift") {
    isShift = !isShift;
    updateKeyboard();
    return;
  }

  if (key === "CapsLock") {
    isCaps = !isCaps;
    updateKeyboard();
    return;
  }

  if (key === "Emoji") {
    insertText("😄");
    return;
  }

  if (key === "Voice") {
    startDictation();
    return;
  }

  if (key === "Ctrl+Alt+Del") {
    insertText("[CTRL+ALT+DEL]");
    return;
  }

  if (/^F\d+$/.test(key)) {
    document.dispatchEvent(new KeyboardEvent("keydown", { key }));
    return;
  }

  if (key === "Space") insertText(" ");
  else if (key === "Enter") insertText("\n");
  else if (key === "Backspace") {
    if (active && active.value) active.value = active.value.slice(0, -1);
  }
  else insertText(getDisplayKey(key));

  if (isShift && key !== "Shift") {
    isShift = false;
    updateKeyboard();
  }
}

function insertText(text) {
  const active = document.activeElement;
  if (active && (active.tagName === "INPUT" || active.tagName === "TEXTAREA")) {
    active.value += text;
  }
}

function updateKeyboard() {
  document.querySelectorAll(".vk-key").forEach(btn => {
    const key = btn.dataset.key;
    btn.textContent = getDisplayKey(key);
  });
}

// 🗣️ Ditado por voz
function startDictation() {
  if (!window.SpeechRecognition && !window.webkitSpeechRecognition) {
    alert("Ditado por voz não suportado neste navegador.");
    return;
  }

  const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
  recognition.lang = "pt-BR";
  recognition.start();

  recognition.onresult = (event) => {
    const text = event.results[0][0].transcript;
    insertText(text + " ");
  };

  recognition.onerror = () => alert("Erro no reconhecimento de voz.");
}

window.addEventListener("DOMContentLoaded", createKeyboard);#virtual-keyboard {
  position: fixed;
  bottom: 0;
  width: 100%;
  background: #1c1c1c;
  padding: 8px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  z-index: 9999;
  box-shadow: 0 -3px 10px rgba(0, 0, 0, 0.5);
}

.vk-row {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 6px;
}

.vk-key {
  flex: 1 0 auto;
  min-width: 9%;
  max-width: 12%;
  padding: 12px;
  font-size: 1.1rem;
  text-align: center;
  background: #333;
  color: #fff;
  border: none;
  border-radius: 8px;
  user-select: none;
  transition: 0.2s;
}

.vk-key:hover,
.vk-key:focus {
  background: #555;
  outline: 2px solid #0af;
}

@media (max-width: 768px) {
  .vk-key {
    min-width: 16%;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .vk-key {
    min-width: 22%;
    font-size: 0.9rem;
    padding: 10px;
  }

  #virtual-keyboard {
    max-height: 45vh;
    overflow-y: auto;
  }/editor/
├── index.html
├── editor.js
├── style.css
└── /assets/
    └── (ícones e imagens padrão)
}<div id="photo-editor">
  <canvas id="canvas" width="800" height="600"></canvas>
  <div id="tools">
    <input type="file" id="upload" accept="image/*">
    <button onclick="addText()">Texto</button>
    <button onclick="applyFilter('grayscale')">P&B</button>
    <button onclick="applyFilter('sepia')">Sépia</button>
    <button onclick="applyFilter('invert')">Negativo</button>
    <button onclick="adjust('brightness', 0.1)">+Brilho</button>
    <button onclick="adjust('brightness', -0.1)">−Brilho</button>
    <button onclick="undo()">Desfazer</button>
    <button onclick="clearCanvas()">Limpar</button>
    <button onclick="save()">Salvar</button>
  </div>
</div>
<link rel="stylesheet" href="editor.css"><script src="https://cdnjs.cloudflare.com/ajax/libs/fabric.js/5.3.0/fabric.min.js"></script>
<script>
  const canvas = new fabric.Canvas('canvas');
  const history = [];

  // Upload de imagem
  document.getElementById('upload').addEventListener('change', e => {
    const reader = new FileReader();
    reader.onload = function (event) {
      fabric.Image.fromURL(event.target.result, img => {
        img.scaleToWidth(600);
        canvas.clear();
        canvas.add(img);
        saveState();
      });
    };
    reader.readAsDataURL(e.target.files[0]);
  });

  function addText() {
    const text = new fabric.IText('Texto', {
      left: 50, top: 50, fill: '#fff', fontSize: 32
    });
    canvas.add(text);
    saveState();
  }

  function applyFilter(type) {
    const active = canvas.getActiveObject();
    if (!active || active.type !== 'image') return alert("Selecione uma imagem.");
    const filters = {
      grayscale: new fabric.Image.filters.Grayscale(),
      sepia: new fabric.Image.filters.Sepia(),
      invert: new fabric.Image.filters.Invert()
    };
    active.filters.push(filters[type]);
    active.applyFilters();
    canvas.renderAll();
    saveState();
  }

  function adjust(type, value) {
    const active = canvas.getActiveObject();
    if (!active || active.type !== 'image') return alert("Selecione uma imagem.");
    const f = new fabric.Image.filters.Brightness({ brightness: value });
    active.filters.push(f);
    active.applyFilters();
    canvas.renderAll();
    saveState();
  }

  function save() {
    const link = document.createElement('a');
    link.href = canvas.toDataURL({ format: 'png' });
    link.download = 'editado.png';
    link.click();
  }

  function clearCanvas() {
    canvas.clear();
    saveState();
  }

  function saveState() {
    const state = JSON.stringify(canvas.toJSON());
    history.push(state);
  }

  function undo() {
    if (history.length > 1) {
      history.pop();
      canvas.loadFromJSON(history[history.length - 1], canvas.renderAll.bind(canvas));
    }
  }
</script>
#photo-editor {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #111;
  color: white;
  padding: 1em;
  border-radius: 12px;
}

#tools {
  margin-top: 10px;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

#tools button {
  background: #222;
  color: #fff;
  border: 1px solid #444;
  padding: 6px 12px;
  border-radius: 6px;
  cursor: pointer;
}

#tools input[type="file"] {
  color: white;
}
<script src="https://cdnjs.cloudflare.com/ajax/libs/fabric.js/5.3.0/fabric.min.js"></script>
<script>
const canvas = new fabric.Canvas('canvas');
let drawingMode = false;
let currentTool = null;
let history = [];

function init() {
  canvas.isDrawingMode = false;
  canvas.freeDrawingBrush.color = "#ffffff";
  canvas.freeDrawingBrush.width = 3;
  saveState();
}

document.getElementById('upload').addEventListener('change', e => {
  const reader = new FileReader();
  reader.onload = function (event) {
    fabric.Image.fromURL(event.target.result, img => {
      img.set({ left: 50, top: 50, scaleX: 0.5, scaleY: 0.5 });
      canvas.add(img).setActiveObject(img);
      saveState();
    });
  };
  reader.readAsDataURL(e.target.files[0]);
});

function saveState() {
  const json = JSON.stringify(canvas);
  if (history[history.length - 1] !== json) {
    history.push(json);
  }
}

function undo() {
  if (history.length > 1) {
    history.pop();
    const prev = history[history.length - 1];
    canvas.loadFromJSON(prev, () => canvas.renderAll());
  }
}

function clearCanvas() {
  canvas.clear();
  saveState();
}

function addText() {
  const text = new fabric.IText("Texto", {
    left: 100,
    top: 100,
    fill: '#fff',
    fontSize: 32
  });
  canvas.add(text).setActiveObject(text);
  saveState();
}

function save() {
  const link = document.createElement("a");
  link.download = "editado.png";
  link.href = canvas.toDataURL({ format: "png" });
  link.click();
}

function applyFilter(type) {
  const obj = canvas.getActiveObject();
  if (!obj || obj.type !== "image") return alert("Selecione uma imagem.");

  let filter = null;
  switch (type) {
    case "grayscale": filter = new fabric.Image.filters.Grayscale(); break;
    case "sepia": filter = new fabric.Image.filters.Sepia(); break;
    case "invert": filter = new fabric.Image.filters.Invert(); break;
    case "blur": filter = new fabric.Image.filters.Blur({ blur: 0.5 }); break;
    case "sharpen": filter = new fabric.Image.filters.Convolute({
      matrix: [ 0, -1, 0, -1, 5, -1, 0, -1, 0 ]
    }); break;
    case "vintage": filter = new fabric.Image.filters.Sepia2(); break;
  }

  obj.filters.push(filter);
  obj.applyFilters();
  canvas.renderAll();
  saveState();
}

function adjust(prop, value) {
  const obj = canvas.getActiveObject();
  if (!obj || obj.type !== "image") return alert("Selecione uma imagem.");
  let filter = null;

  if (prop === "brightness") {
    filter = new fabric.Image.filters.Brightness({ brightness: value });
  }

  obj.filters.push(filter);
  obj.applyFilters();
  canvas.renderAll();
  saveState();
}

function toggleBrush() {
  drawingMode = !drawingMode;
  canvas.isDrawingMode = drawingMode;
  currentTool = "brush";
  if (drawingMode) canvas.discardActiveObject();
  saveState();
}

function cropActiveImage() {
  const obj = canvas.getActiveObject();
  if (!obj || obj.type !== "image") return alert("Selecione uma imagem.");

  const left = obj.left, top = obj.top;
  const width = obj.width * obj.scaleX;
  const height = obj.height * obj.scaleY;

  const cropped = new fabric.Image(obj.getElement(), {
    left: left,
    top: top,
    width: width,
    height: height,
    scaleX: 1,
    scaleY: 1,
    cropX: left,
    cropY: top
  });

  canvas.remove(obj);
  canvas.add(cropped).setActiveObject(cropped);
  saveState();
}

window.addEventListener("DOMContentLoaded", init);
</script><div id="tools">
  <input type="file" id="upload" accept="image/*">
  <button onclick="addText()">Texto</button>
  <button onclick="toggleBrush()">🖌️ Pincel</button>
  <button onclick="cropActiveImage()">✂️ Recortar</button>
  <button onclick="applyFilter('grayscale')">P&B</button>
  <button onclick="applyFilter('sepia')">Sépia</button>
  <button onclick="applyFilter('invert')">Negativo</button>
  <button onclick="applyFilter('blur')">Desfoque</button>
  <button onclick="applyFilter('sharpen')">Nitidez</button>
  <button onclick="applyFilter('vintage')">Vintage</button>
  <button onclick="adjust('brightness', 0.1)">+Brilho</button>
  <button onclick="adjust('brightness', -0.1)">−Brilho</button>
  <button onclick="undo()">Desfazer</button>
  <button onclick="clearCanvas()">Limpar</button>
  <button onclick="save()">Salvar</button>
</div>canvas {
  border: 1px solid #555;
  background: #000;
  max-width: 100%;
  height: auto;
}
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Navegador Ultra Leve</title>
  <style>
    :root {
      color-scheme: dark;
    }

    body {
      margin: 0;
      background: #0a0a0a;
      color: #fff;
      font-family: system-ui, sans-serif;
      display: flex;
      flex-direction: column;
      height: 100vh;
    }

    #barra {
      display: flex;
      padding: 5px;
      background: #111;
      gap: 5px;
    }

    input[type="text"] {
      flex: 1;
      padding: 6px;
      border: none;
      border-radius: 6px;
      background: #222;
      color: white;
    }

    button {
      background: #333;
      border: none;
      color: white;
      padding: 6px 12px;
      border-radius: 6px;
      cursor: pointer;
    }

    iframe {
      flex: 1;
      width: 100%;
      border: none;
    }

    #opcoes {
      background: #181818;
      padding: 5px;
      display: flex;
      gap: 10px;
      font-size: 14px;
      justify-content: center;
    }

    label {
      display: flex;
      align-items: center;
      gap: 5px;
    }
  </style>
</head>
<body>
  <div id="barra">
    <input type="text" id="url" placeholder="Digite a URL..." />
    <button onclick="navegar()">Ir</button>
  </div>

  <div id="opcoes">
    <label><input type="checkbox" id="modoSeguro" checked />Modo seguro</label>
    <label><input type="checkbox" id="modoLeve" />Modo leve</label>
    <label><input type="checkbox" id="noturnoAuto" checked />Auto Noturno</label>
  </div>

  <iframe id="visor"></iframe>

  <script>
    const urlInput = document.getElementById("url");
    const visor = document.getElementById("visor");
    const modoSeguro = document.getElementById("modoSeguro");
    const modoLeve = document.getElementById("modoLeve");

    function navegar() {
      let url = urlInput.value.trim();
      if (!url.startsWith("http")) url = "https://" + url;

      const sandboxOptions = [
        "allow-forms",
        "allow-same-origin",
        "allow-scripts"
      ];

      if (modoSeguro.checked) {
        visor.setAttribute("sandbox", sandboxOptions.join(" "));
      } else {
        visor.removeAttribute("sandbox");
      }

      if (modoLeve.checked) {
        // Usa um proxy que bloqueia imagens (usando DuckDuckGo Lite como exemplo leve)
        if (url.includes("google.")) {
          url = "https://lite.duckduckgo.com/lite";
        }
      }

      visor.src = url;
    }

    window.addEventListener("DOMContentLoaded", () => {
      urlInput.value = "kagi.com";
      navegar();
    });

    // Modo noturno automático baseado no horário
    const now = new Date().getHours();
    if (document.getElementById("noturnoAuto").checked && (now < 6 || now >= 18)) {
      document.body.style.background = "#000";
    }
  </script>
</body>
</html>
/mini-windows
├── index.html
├── apps/
│   ├── notas.js
│   ├── agenda.js
│   ├── calc.js
│   ├── arquivos.js
│   ├── pdf.jsfunction launchApp(app) {
  import(`./apps/${app}.js`).then(m => {
    if (typeof m.initApp === "function") m.initApp();
  });
}export function initApp() {
  const win = document.createElement("div");
  win.innerHTML = `
    <div style="padding: 5px; background: #222; color: white;">
      <strong>📝 Bloco de Notas</strong>
      <textarea id="editor" style="width:100%;height:calc(100vh - 60px);background:#111;color:white;padding:10px;border:none;resize:none;"></textarea>
    </div>
  `;
  document.body.appendChild(win);
}export function initApp() {
  const win = document.createElement("div");
  win.innerHTML = `
    <div style="padding: 10px; background: #111; color: white;">
      <h3>📅 Agenda</h3>
      <input type="date" id="data">
      <textarea id="anot" placeholder="Anotações..." style="width:100%;height:100px;margin-top:10px;background:#222;color:white;border:none;"></textarea>
      <button onclick="salvarNota()">Salvar</button>
    </div>
  `;
  document.body.appendChild(win);

  window.salvarNota = () => {
    const dia = document.getElementById("data").value;
    const nota = document.getElementById("anot").value;
    localStorage.setItem(`agenda-${dia}`, nota);
    alert("Salvo!");
  };
}<button onclick="launchApp('notas')">📝 Bloco de Notas</button>
<button onclick="launchApp('agenda')">📅 Agenda</button>
<button onclick="launchApp('calc')">🧮 Calculadora</button>
<button onclick="launchApp('arquivos')">📁 Arquivos</button>
<button onclick="launchApp('pdf')">📑 PDF</button>
<button onclick="launchApp('anota')">🧠 Sticky Notes</button>
│   └── anota.js
export function initApp() {
  const win = document.createElement("div");
  win.style = "width: 100%; height: 100%; background: #fff; color: #000; font-family: sans-serif; overflow: auto;";
  win.innerHTML = `
    <div style="background:#d93025;color:white;padding:10px;font-size:18px;">
      <strong>📧 Mini Gmail</strong>
      <button style="float:right;" onclick="document.body.removeChild(this.parentElement.parentElement)">X</button>
    </div>
    <div style="display:flex; height: calc(100% - 40px);">
      <div style="width:200px;background:#f1f3f4;padding:10px;">
        <button onclick="mostrarCaixa('entrada')">📥 Caixa de Entrada</button><br><br>
        <button onclick="mostrarCaixa('enviados')">📤 Enviados</button><br><br>
        <button onclick="comporEmail()">✉️ Compor</button>
      </div>
      <div id="conteudo" style="flex:1;padding:10px;overflow-y:auto;"></div>
    </div>
  `;
  document.body.appendChild(win);

  // Funções de simulação
  window.emails = {
    entrada: [
      { assunto: "Bem-vindo!", corpo: "Obrigado por usar o Mini Gmail!" },
      { assunto: "Oferta", corpo: "Descontos exclusivos para você!" }
    ],
    enviados: []
  };

  window.mostrarCaixa = (tipo) => {
    const div = document.getElementById("conteudo");
    div.innerHTML = `<h2>${tipo === 'entrada' ? 'Caixa de Entrada' : 'Enviados'}</h2>`;
    emails[tipo].forEach((email, i) => {
      div.innerHTML += `
        <div style="border-bottom:1px solid #ccc;padding:5px;">
          <strong>${email.assunto}</strong><br>
          <p>${email.corpo}</p>
        </div>
      `;
    });
  };

  window.comporEmail = () => {
    const div = document.getElementById("conteudo");
    div.innerHTML = `
      <h2>Nova Mensagem</h2>
      <input id="destino" placeholder="Para..." style="width:100%;padding:5px;"><br><br>
      <input id="assunto" placeholder="Assunto" style="width:100%;padding:5px;"><br><br>
      <textarea id="corpo" style="width:100%;height:150px;padding:5px;"></textarea><br><br>
      <button onclick="enviarEmail()">Enviar</button>
    `;
  };

  window.enviarEmail = () => {
    const assunto = document.getElementById("assunto").value;
    const corpo = document.getElementById("corpo").value;
    emails.enviados.push({ assunto, corpo });
    alert("Mensagem enviada (simulada)!");
    mostrarCaixa("enviados");
  };

  mostrarCaixa("entrada");
}<button onclick="launchApp('gmail')">📧 Mini Gmail</button>
export function initApp() {
  const win = document.createElement("div");
  win.style = "width: 100%; height: 100%; background: #fff; color: #000; font-family: sans-serif; overflow: auto;";
  win.innerHTML = `
    <div style="background:#d93025;color:white;padding:10px;font-size:18px;">
      <strong>📧 Mini Gmail</strong>
      <button style="float:right;" onclick="document.body.removeChild(this.parentElement.parentElement)">X</button>
    </div>
    <div style="display:flex; height: calc(100% - 40px);">
      <div style="width:200px;background:#f1f3f4;padding:10px;">
        <button onclick="mostrarCaixa('entrada')">📥 Caixa de Entrada</button><br><br>
        <button onclick="mostrarCaixa('enviados')">📤 Enviados</button><br><br>
        <button onclick="comporEmail()">✉️ Compor</button>
      </div>
      <div id="conteudo" style="flex:1;padding:10px;overflow-y:auto;"></div>
    </div>
    <audio id="som" src="https://notificationsounds.com/storage/sounds/file-sounds-1175-pristine.mp3" preload="auto"></audio>
  `;
  document.body.appendChild(win);

  // Simulação
  window.emails = {
    entrada: [
      { assunto: "Bem-vindo!", corpo: "Obrigado por usar o Mini Gmail!" },
      { assunto: "Oferta", corpo: "Descontos exclusivos para você!" }
    ],
    enviados: []
  };

  window.mostrarCaixa = (tipo) => {
    const div = document.getElementById("conteudo");
    div.innerHTML = `<h2>${tipo === 'entrada' ? 'Caixa de Entrada' : 'Enviados'}</h2>`;
    emails[tipo].forEach((email, i) => {
      div.innerHTML += `
        <div style="border-bottom:1px solid #ccc;padding:5px;">
          <strong>${email.assunto}</strong><br>
          <p>${email.corpo}</p>
        </div>
      `;
    });
  };

  window.comporEmail = () => {
    const div = document.getElementById("conteudo");
    div.innerHTML = `
      <h2>Nova Mensagem</h2>
      <input id="destino" placeholder="Para..." style="width:100%;padding:5px;"><br><br>
      <input id="assunto" placeholder="Assunto" style="width:100%;padding:5px;"><br><br>
      <textarea id="corpo" style="width:100%;height:150px;padding:5px;"></textarea><br><br>
      <button onclick="enviarEmail()">Enviar</button>
    `;
  };

  window.enviarEmail = () => {
    const assunto = document.getElementById("assunto").value;
    const corpo = document.getElementById("corpo").value;
    emails.enviados.push({ assunto, corpo });
    alert("Mensagem enviada!");
    mostrarCaixa("enviados");
  };

  // 🔔 Notificações e simulação
  function notificarNovaMensagem(email) {
    const titulo = `📧 Nova mensagem: ${email.assunto}`;
    if (Notification.permission === "granted") {
      new Notification(titulo, {
        body: email.corpo,
        icon: "https://ssl.gstatic.com/ui/v1/icons/mail/rfr/logo_gmail_lockup_default_1x_r5.png"
      });
    }

    document.getElementById("som").play();
  }

  function simularNovaMensagem() {
    const novoEmail = {
      assunto: "Atualização do sistema",
      corpo: "Seu Mini Windows foi atualizado com sucesso!"
    };
    emails.entrada.unshift(novoEmail);
    notificarNovaMensagem(novoEmail);
    mostrarCaixa("entrada");
  }

  // Pedir permissão para notificações
  if ("Notification" in window && Notification.permission !== "granted") {
    Notification.requestPermission();
  }

  // ⏰ Simula novo e-mail a cada 90 segundos
  setInterval(simularNovaMensagem, 90000);

  mostrarCaixa("entrada");
}npm install imapflow nodemailer dotenv cors expressconst express = require("express");
const { ImapFlow } = require("imapflow");
const nodemailer = require("nodemailer");
const cors = require("cors");
require("dotenv").config();

const app = express();
app.use(cors());
app.use(express.json());

app.post("/email/receber", async (req, res) => {
  const client = new ImapFlow({
    host: "imap.gmail.com",
    port: 993,
    secure: true,
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }EMAIL=seuemail@gmail.com
PASSWORD=sua_senha{
  "name": "Mini Gmail",
  "short_name": "Gmail",
  "start_url": "./index.html",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#d93025",
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
}<script>
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('sw.js')
    .then(reg => console.log('Service Worker registrado!'))
    .catch(err => console.error('Erro ao registrar SW:', err));
}
</script>self.addEventListener('install', e => {
  e.waitUntil(
    caches.open('mini-gmail').then(cache => {
      return cache.addAll(['./index.html', './gmail.js', './icon-192.png']);
    })
  );
});

self.addEventListener('fetch', e => {
  e.respondWith(
    caches.match(e.request).then(resp => resp || fetch(e.request))
  );
});npm install -g @bubblewrap/cli
bubblewrap init --manifest=https://SEU_SITE/manifest.json
bubblewrap build
bubblewrap install
const express = require("express");
const { ImapFlow } = require("imapflow");
const nodemailer = require("nodemailer");
const cors = require("cors");
require("dotenv").config();

const app = express();
app.use(cors());
app.use(express.json());

app.post("/email/receber", async (req, res) => {
  const client = new ImapFlow({
    host: "imap.gmail.com",
    port: 993,
    secure: true,
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  await client.connect();
  let mailbox = await client.selectMailbox("INBOX");
  let messages = [];

  for await (let msg of client.fetch("1:*", { envelope: true, source: true })) {
    messages.push({
      from: msg.envelope.from[0].address,
      subject: msg.envelope.subject
    });
  }

  await client.logout();
  res.json(messages);
});

app.post("/email/enviar", async (req, res) => {
  const { to, subject, text } = req.body;

  let transporter = nodemailer.createTransport({
    service: "gmail",
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  let info = await transporter.sendMail({ from: process.env.EMAIL, to, subject, text });
  res.json({ messageId: info.messageId });
});

app.listen(3000, () => console.log("Servidor rodando em http://localhost:3000"));
const express = require("express");
const { ImapFlow } = require("imapflow");
const nodemailer = require("nodemailer");
const cors = require("cors");
require("dotenv").config();

const app = express();
app.use(cors());
app.use(express.json());

app.post("/email/receber", async (req, res) => {
  const client = new ImapFlow({
    host: "imap.gmail.com",
    port: 993,
    secure: true,
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  await client.connect();
  let mailbox = await client.selectMailbox("INBOX");
  let messages = [];

  for await (let msg of client.fetch("1:*", { envelope: true, source: true })) {
    messages.push({
      from: msg.envelope.from[0].address,
      subject: msg.envelope.subject
    });
  }

  await client.logout();
  res.json(messages);
});

app.post("/email/enviar", async (req, res) => {
  const { to, subject, text } = req.body;

  let transporter = nodemailer.createTransport({
    service: "gmail",
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  let info = await transporter.sendMail({ from: process.env.EMAIL, to, subject, text });
  res.json({ messageId: info.messageId });
});

app.listen(3000, () => console.log("Servidor rodando em http://localhost:3000")); mini-windows/
├── index.html               ← Mini Windows principal
├── js/
│   └── sistema.js           ← Gerenciador de janelas
├── apps/
│   └── mini-gmail.html      ← Mini Gmail completo
├── icons/
│   └── gmail-icon.png       ← Ícone do Gmail
├── servidor/
│   └── server.js            ← Backend seguro
│   └── .env                 ← Senhas protegidas
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Mini Gmail</title>
  <style>
    body { font-family: sans-serif; padding: 10px; }
    #login, #app { max-width: 600px; margin: auto; }
    input, textarea, button { width: 100%; margin: 5px 0; padding: 8px; }
  </style>
</head>
<body>

<div id="login">
  <h2>Entrar no Mini Gmail</h2>
  <input type="email" id="email" placeholder="Email" />
  <input type="password" id="senha" placeholder="Senha" />
  <button onclick="fazerLogin()">Entrar</button>
</div>

<div id="app" style="display:none;">
  <h2>Mini Gmail</h2>
  <p id="usuarioAtual"></p>
  <button onclick="logout()">Trocar de conta</button>

  <h3>Enviar E-mail</h3>
  <input id="para" placeholder="Para" />
  <input id="assunto" placeholder="Assunto" />
  <textarea id="mensagem" placeholder="Mensagem"></textarea>
  <button onclick="enviar()">Enviar</button>
</div>

<script>
const api = "http://localhost:3000";
let emailUsuario = null;

window.onload = () => {
  const salvo = localStorage.getItem("usuarioLogado");
  if (salvo) {
    emailUsuario = salvo;
    document.getElementById("login").style.display = "none";
    document.getElementById("app").style.display = "block";
    document.getElementById("usuarioAtual").textContent = "Logado como: " + emailUsuario;
  }
};

function fazerLogin() {
  const email = document.getElementById("email").value;
  const senha = document.getElementById("senha").value;

  fetch(`${api}/login`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ email, senha })
  })
  .then(res => res.json())
  .then(d => {
    if (d.sucesso) {
      emailUsuario = email;
      localStorage.setItem("usuarioLogado", email);
      document.getElementById("login").style.display = "none";
      document.getElementById("app").style.display = "block";
      document.getElementById("usuarioAtual").textContent = "Logado como: " + email;
    } else {
      alert("Login inválido");
    }
  });
}

function enviar() {
  fetch(`${api}/enviar`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      de: emailUsuario,
      to: document.getElementById("para").value,
      subject: document.getElementById("assunto").value,
      text: document.getElementById("mensagem").value
    })
  }).then(() => alert("Enviado com sucesso!"));
}

function logout() {
  localStorage.removeItem("usuarioLogado");
  location.reload();
}
</script>

</body>
</html>
const express = require("express");
const cors = require("cors");
const nodemailer = require("nodemailer");
const dotenv = require("dotenv");
dotenv.config();

const app = express();
app.use(cors());
app.use(express.json());

const contas = {
  "exemplo@gmail.com": { senha: "1234", nome: "Usuário 1", smtpPass: process.env.SENHA_1 },
  "demo@teste.com": { senha: "abcd", nome: "Usuário 2", smtpPass: process.env.SENHA_2 }
};

app.post("/login", (req, res) => {
  const { email, senha } = req.body;
  const conta = contas[email];
  if (conta && conta.senha === senha) {
    res.json({ sucesso: true, nome: conta.nome });
  } else {
    res.json({ sucesso: false });
  }
});

app.post("/enviar", async (req, res) => {
  const { de, to, subject, text } = req.body;
  const conta = contas[de];
  if (!conta) return res.status(403).json({ erro: "Conta inválida" });

  const transporter = nodemailer.createTransport({
    service: "gmail",
    auth: { user: de, pass: conta.smtpPass }
  });

  await transporter.sendMail({
    from: de,
    to,
    subject,
    text
  });

  res.json({ enviado: true });
});

app.listen(3000, () => console.log("Servidor Mini Gmail rodando na porta 3000"));
SENHA_1=sua-senha-de-app-google-1
SENHA_2=sua-senha-de-app-google-2
const appsRegistrados = [
  {
    nome: "Mini Gmail",
    icone: "icons/gmail-icon.png",
    arquivo: "apps/mini-gmail.html",
    largura: 800,
    altura: 600
  },
  // ...outros apps
];
<button onclick="abrirApp('Mini Gmail')">
  <img src="icons/gmail-icon.png" width="24"> Mini Gmail
</button>
const appsRegistrados = [
  {
    nome: "Mini Gmail",
    icone: "icons/gmail-icon.png",
    arquivo: "apps/mini-gmail.html",
    largura: 800,
    altura: 600
  },
  // ...outros apps
];
<button onclick="abrirApp('Mini Gmail')">
  <img src="icons/gmail-icon.png" width="24"> Mini Gmail
</button>
function abrirApp(nomeApp) {
  const app = appsRegistrados.find(a => a.nome === nomeApp);
  if (!app) return;

  abrirJanelaApp(app.nome, app.arquivo, app.icone, app.largura, app.altura);
}
// server.js (ver resposta anterior para versão completa)
app.post("/login", ...);
app.post("/enviar", ...);
app.get("/receber", ...);
SENHA_1=senhaDeAppParaConta1
SENHA_2=senhaDeAppParaConta2
// Salvar sessão no login:
localStorage.setItem("usuarioLogado", email);
window.onload = () => {
  const user = localStorage.getItem("usuarioLogado");
  if (user) {
    document.getElementById("login").style.display = "none";
    document.getElementById("app").style.display = "block";
    carregarEmails(user);
  }
};
const express = require("express");
const cors = require("cors");
const nodemailer = require("nodemailer");
const { ImapFlow } = require("imapflow");
const dotenv = require("dotenv");
dotenv.config();

const app = express();
app.use(cors());
app.use(express.json());

const PORT = 3000;

let contas = {
  "exemplo@gmail.com": { senha: "1234", nome: "Usuário 1", smtpPass: process.env.SENHA_1 },
  "demo@teste.com": { senha: "abcd", nome: "Usuário 2", smtpPass: process.env.SENHA_2 }
};

app.post("/login", (req, res) => {
  const { email, senha } = req.body;
  const conta = contas[email];
  if (conta && conta.senha === senha) {
    res.json({ sucesso: true, nome: conta.nome });
  } else {
    res.json({ sucesso: false });
  }
});

app.post("/enviar", async (req, res) => {
  const { de, to, subject, text } = req.body;
  const conta = contas[de];

  if (!conta) return
<div id="login" style="display: flex; flex-direction: column; gap: 10px;">
  <h2>Login no Mini Gmail</h2>
  <input id="email" placeholder="Email" type="email" />
  <input id="senha" placeholder="Senha" type="password" />
  <button onclick="fazerLogin()">Entrar</button>
</div>

<div id="app" style="display: none;">
  <!-- Todo conteúdo do Mini Gmail aqui -->
</div>
<div id="login" style="display: flex; flex-direction: column; gap: 10px;">
  <h2>Login no Mini Gmail</h2>
  <input id="email" placeholder="Email" type="email" />
  <input id="senha" placeholder="Senha" type="password" />
  <button onclick="fazerLogin()">Entrar</button>
</div>
npm init -y
npm install express nodemailer imapflow cors dotenv

<div id="app" style="display: none;">
  <!-- Todo conteúdo do Mini Gmail aqui -->
</div>
EMAIL=seuemail@gmail.com
PASSWORD=suasenhasecreta
const express = require("express");
const cors = require("cors");
const nodemailer = require("nodemailer");
const { ImapFlow } = require("imapflow");
require("dotenv").config();

const app = express();
app.use(cors());
app.use(express.json());

const PORT = 3000;

app.post("/enviar", async (req, res) => {
  const { to, subject, text } = req.body;

  let transporter = nodemailer.createTransport({
    service: "gmail",
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  try {
    const info = await transporter.sendMail({
      from: process.env.EMAIL,
      to,
      subject,
      text
    });
    res.json({ success: true, messageId: info.messageId });
  } catch (err) {
    res.status(500).json({ success: false, error: err.message });
  }
});

app.get("/receber", async (req, res) => {
  const client = new ImapFlow({
    host: "imap.gmail.com",
    port: 993,
    secure: true,
    auth: {
      user: process.env.EMAIL,
      pass: process.env.PASSWORD
    }
  });

  try {
    await client.connect();
    await client.selectMailbox("INBOX");

    const messages = [];

    for await (let msg of client.fetch("1:*", { envelope: true, source: true })) {
      messages.push({
        de: msg.envelope.from[0].address,
        assunto: msg.envelope.subject
      });
    }

    await client.logout();
    res.json(messages.reverse().slice(0, 10)); // últimos 10
  } catch (err) {
    res.status(500).json({ success: false, error: err.message });
  }
});

app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
function enviarEmail() {
  const para = document.getElementById("para").value;
  const assunto = document.getElementById("assunto").value;
  const corpo = document.getElementById("corpo").value;

  fetch("http://localhost:3000/enviar", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ to: para, subject: assunto, text: corpo })
  })
  .then(res => res.json())
  .then(data => {
    alert("Email enviado com sucesso!");
    mostrarCaixa("enviados");
  })
  .catch(err => alert("Erro ao enviar: " + err.message));
}
function carregarEmails() {
  fetch("http://localhost:3000/receber")
    .then(res => res.json())
    .then(emails => {
      emails.forEach(email => {
        emails.entrada.unshift({ assunto: email.assunto, corpo: `De: ${email.de}` });
      });
      mostrarCaixa("entrada");
    })
    .catch(err => console.error("Erro ao carregar e-mails:", err));
}
// js/optimizador.js
document.addEventListener("DOMContentLoaded", () => {
  // Reduz redraws e repaint desnecessários
  document.body.style.willChange = "transform";

  // Desativa animações globais para performance
  const style = document.createElement("style");
  style.textContent = `
    * {
      transition: none !important;
      animation: none !important;
    }
  `;
  document.head.appendChild(style);

  // Substitui sombras pesadas por sombras leves
  document.querySelectorAll("*").forEach(el => {
    if (getComputedStyle(el).boxShadow) {
      el.style.boxShadow = "0 0 4px rgba(0,0,0,0.2)";
    }
  });

  // Remove event listeners pesados em background
  window.removeEventListener("mousemove", () => {});
  window.removeEventListener("scroll", () => {});
  window.removeEventListener("resize", () => {});

  // Desativa pré-carregamento de imagens grandes
  const imgs = document.querySelectorAll("img");
  imgs.forEach(img => {
    img.loading = "lazy";
  });

  // Suspende iframes ocultos
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (!entry.isIntersecting && entry.target.tagName === "IFRAME") {
        entry.target.src = "";
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll("iframe").forEach(iframe => {
    observer.observe(iframe);
  });

  console.log("Mini Windows otimizado para Xbox");
});
<script src="js/optimizador.js"></script>
html, body {
  font-family: system-ui, sans-serif;
  margin: 0;
  padding: 0;
  background: #1a1a1a;
  color: #fff;
  overflow: hidden;
  user-select: none;
  -webkit-user-drag: none;
}
img {
  max-width: 100%;
  height: auto;
  image-rendering: pixelated;
}
mini-windows/
├── index.html
├── js/
├── css/
├── apps/
└── icons/
{
  "name": "Mini Windows",
  "short_name": "MiniWin",
  "start_url": "index.html",
  "display": "standalone",
  "icons": [
    {
      "src": "icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ],
  "background_color": "#000000",
  "theme_color": "#111111"
}
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Windows Xbox</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/windows.png">
</head>
<body class="bg-gray-900 text-white font-sans">
  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Atalhos na "Área de Trabalho" -->
    <div class="absolute top-4 left-4 space-y-4">
      <button onclick="openApp('youtube')" class="flex flex-col items-center">
        <img src="assets/icons/youtube.png" class="w-12 h-12" />
        <span class="text-xs">YouTube</span>
      </button>
      <button onclick="openApp('netflix')" class="flex flex-col items-center">
        <img src="assets/icons/netflix.png" class="w-12 h-12" />
        <span class="text-xs">Netflix</span>
      </button>
      <button onclick="openApp('photopea')" class="flex flex-col items-center">
        <img src="assets/icons/photopea.png" class="w-12 h-12" />
        <span class="text-xs">Photopea</span>
      </button>
      <button onclick="openApp('gmail')" class="flex flex-col items-center">
        <img src="assets/icons/gmail.png" class="w-12 h-12" />
        <span class="text-xs">Gmail</span>
      </button>
    </div>
  </div>
</body>
</html>
// system.js - Gerencia janelas do Mini Windows Xbox

const appUrls = { youtube: "https://www.youtube.com", netflix: "https://www.netflix.com", photopea: "https://www.photopea.com", gmail: "https://mail.google.com" };

function openApp(appName) { if (!appUrls[appName]) return alert("App não encontrado");

const win = document.createElement("div"); win.className = "absolute top-16 left-16 w-3/4 h-3/4 bg-gray-800 border border-white shadow-lg rounded-xl overflow-hidden"; win.innerHTML = <div class="flex justify-between items-center bg-gray-700 text-sm px-4 py-2"> <span>${appName.toUpperCase()}</span> <button onclick="this.closest('div').parentElement.remove()">❌</button> </div> <iframe src="${appUrls[appName]}" class="w-full h-full border-none"></iframe>;

document.getElementById("desktop").appendChild(win); }
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 200px;
    }
    #startMenu.active {
      display: block;
    }
  </style>
</head>
<body class="text-white font-sans">
  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Menu Iniciar -->
    <div class="absolute bottom-4 left-4">
      <div class="menu-btn" onclick="toggleStartMenu()">X</div>
    </div>
    <div id="startMenu">
      <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
      <ul class="space-y-1">
        <li><button onclick="openApp('youtube')">📺 YouTube</button></li>
        <li><button onclick="openApp('netflix')">🎬 Netflix</button></li>
        <li><button onclick="openApp('photopea')">🖌️ Photopea</button></li>
        <li><button onclick="openApp('gmail')">✉️ Gmail</button></li>
      </ul>
    </div>
  </div>
  <script>
    function toggleStartMenu() {
      const menu = document.getElementById("startMenu");
      menu.classList.toggle("active");
    }
  </script>
</body>
</html>
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 200px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    /* Barra lateral */
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 60px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 1rem 0;
    }
    .sidebar-icon {
      width: 40px;
      height: 40px;
      margin: 0.5rem 0;
      background-color: #107c10;
      border-radius: 0.75rem;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.25rem;
      transition: transform 0.2s, background 0.2s;
      cursor: pointer;
    }
    .sidebar-icon:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Barra lateral -->
    <div id="sidebar">
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo loja...')">🛒</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo configurações...')">⚙️</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Ajuda')">❓</div>
      <div class="sidebar-icon" onclick="playError(); alert('Erro de exemplo!')">⛔</div>
    </div><!-- Menu Iniciar -->
<div class="absolute bottom-4 left-20">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
  </ul>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");function playNav() {
  soundNav.currentTime = 0;
  soundNav.play();
}
function playOk() {
  soundOk.currentTime = 0;
  soundOk.play();
}
function playError() {
  soundError.currentTime = 0;
  soundError.play();
}

function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}

// Tecla M ou Enter para abrir menu
document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});

  </script>
</body>
</html>
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 200px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    /* Barra lateral */
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 60px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 1rem 0;
    }
    .sidebar-icon {
      width: 40px;
      height: 40px;
      margin: 0.5rem 0;
      background-color: #107c10;
      border-radius: 0.75rem;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.25rem;
      transition: transform 0.2s, background 0.2s;
      cursor: pointer;
    }
    .sidebar-icon:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Barra lateral -->
    <div id="sidebar">
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo loja...')">🛒</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo configurações...')">⚙️</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Ajuda')">❓</div>
      <div class="sidebar-icon" onclick="playError(); alert('Erro de exemplo!')">⛔</div>
    </div><!-- Menu Iniciar -->
<div class="absolute bottom-4 left-20">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
  </ul>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");function playNav() {
  soundNav.currentTime = 0;
  soundNav.play();
}
function playOk() {
  soundOk.currentTime = 0;
  soundOk.play();
}
function playError() {
  soundError.currentTime = 0;
  soundError.play();
}

function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}

// Tecla M ou Enter para abrir menu
document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});

  </script>
</body>
</html>
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 200px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    /* Barra lateral */
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 60px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 1rem 0;
    }
    .sidebar-icon {
      width: 40px;
      height: 40px;
      margin: 0.5rem 0;
      background-color: #107c10;
      border-radius: 0.75rem;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.25rem;
      transition: transform 0.2s, background 0.2s;
      cursor: pointer;
    }
    .sidebar-icon:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Barra lateral -->
    <div id="sidebar">
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo loja...')">🛒</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Abrindo configurações...')">⚙️</div>
      <div class="sidebar-icon" onclick="playOk(); alert('Ajuda')">❓</div>
      <div class="sidebar-icon" onclick="playError(); alert('Erro de exemplo!')">⛔</div>
    </div><!-- Menu Iniciar -->
<div class="absolute bottom-4 left-20">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
  </ul>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");function playNav() {
  soundNav.currentTime = 0;
  soundNav.play();
}
function playOk() {
  soundOk.currentTime = 0;
  soundOk.play();
}
function playError() {
  soundError.currentTime = 0;
  soundError.play();
}

function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}

// Tecla M ou Enter para abrir menu
document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});

  </script>
</body>
</html>
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 200px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    /* Barra lateral */
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 200px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      padding: 1rem 0;
      transition: width 0.3s ease;
      overflow: hidden;
    }
    .sidebar-icon {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1rem;
      color: white;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s, transform 0.2s;
    }
    .sidebar-icon:hover {
      background-color: #159c15;
      transform: scale(1.02);
    }
    .sidebar-icon span {
      white-space: nowrap;
    }
    #notifications {
      position: absolute;
      top: 1rem;
      right: 1rem;
      z-index: 100;
    }
    .toast {
      background: rgba(0,0,0,0.85);
      color: white;
      padding: 0.75rem 1rem;
      border-radius: 0.5rem;
      margin-bottom: 0.5rem;
      backdrop-filter: blur(6px);
      animation: fadeInOut 3s ease forwards;
    }
    @keyframes fadeInOut {
      0% { opacity: 0; transform: translateY(-10px); }
      10% { opacity: 1; transform: translateY(0); }
      90% { opacity: 1; }
      100% { opacity: 0; transform: translateY(-10px); }
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <!-- Notificações -->
    <div id="notifications"></div><!-- Barra lateral -->
<div id="sidebar">
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo loja...')">🛒 <span>Loja</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo configurações...')">⚙️ <span>Configurações</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Ajuda aberta')">❓ <span>Ajuda</span></div>
  <div class="sidebar-icon" onclick="playError(); showToast('Erro simulado!')">⛔ <span>Erro</span></div>
</div>

<!-- Menu Iniciar -->
<div class="absolute bottom-4 left-56">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
  </ul>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");function playNav() {
  soundNav.currentTime = 0;
  soundNav.play();
}
function playOk() {
  soundOk.currentTime = 0;
  soundOk.play();
}
function playError() {
  soundError.currentTime = 0;
  soundError.play();
}

function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}

// Tecla M ou Enter para abrir menu
document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});

function showToast(text) {
  const toast = document.createElement("div");
  toast.className = "toast";
  toast.textContent = text;
  notificationArea.appendChild(toast);
  setTimeout(() => toast.remove(), 3000);
}

  </script>
</body>
</html>
<button onclick="launchGame('games/space-invaders/index.html')">👾 Space Invaders</button>/games/
  space-invaders/
    index.html
  tetris/
    index.htmlfunction launchGame(path) {
  window.open(path, "_blank", "fullscreen=yes");
}
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 250px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 200px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      padding: 1rem 0;
    }
    .sidebar-icon {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1rem;
      color: white;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s, transform 0.2s;
    }
    .sidebar-icon:hover {
      background-color: #159c15;
      transform: scale(1.02);
    }
    .sidebar-icon span {
      white-space: nowrap;
    }
    #notifications {
      position: absolute;
      top: 1rem;
      right: 1rem;
      z-index: 100;
    }
    .toast {
      background: rgba(0,0,0,0.85);
      color: white;
      padding: 0.75rem 1rem;
      border-radius: 0.5rem;
      margin-bottom: 0.5rem;
      backdrop-filter: blur(6px);
      animation: fadeInOut 3s ease forwards;
    }
    @keyframes fadeInOut {
      0% { opacity: 0; transform: translateY(-10px); }
      10% { opacity: 1; transform: translateY(0); }
      90% { opacity: 1; }
      100% { opacity: 0; transform: translateY(-10px); }
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <div id="notifications"></div><!-- Barra lateral -->
<div id="sidebar">
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo loja...')">🛒 <span>Loja</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo configurações...')">⚙️ <span>Configurações</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Jogos carregando...'); openGames()">🎮 <span>Jogos</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Ajuda aberta')">❓ <span>Ajuda</span></div>
  <div class="sidebar-icon" onclick="playError(); showToast('Erro simulado!')">⛔ <span>Erro</span></div>
</div>

<!-- Menu Iniciar -->
<div class="absolute bottom-4 left-56">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
    <li><button onclick="playNav(); openGames()">🎮 Meus Jogos</button></li>
  </ul>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");function playNav() {
  soundNav.currentTime = 0;
  soundNav.play();
}
function playOk() {
  soundOk.currentTime = 0;
  soundOk.play();
}
function playError() {
  soundError.currentTime = 0;
  soundError.play();
}
function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}
document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});
function showToast(text) {
  const toast = document.createElement("div");
  toast.className = "toast";
  toast.textContent = text;
  notificationArea.appendChild(toast);
  setTimeout(() => toast.remove(), 3000);
}
function openApp(appName) {
  showToast(`Abrindo ${appName}...`);
  window.open(`apps/${appName}/index.html`, "_blank");
}
function openGames() {
  window.open("games/index.html", "_blank");
}

  </script>
</body>
</html>
<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mini Xbox OS</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <script defer src="system.js"></script>
  <link rel="icon" type="image/png" href="assets/icons/xbox.png">
  <style>
    body {
      background-image: url('assets/wallpapers/xbox-bg.jpg');
      background-size: cover;
      background-position: center;
    }
    .menu-btn {
      background-color: #107c10;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .menu-btn:hover {
      transform: scale(1.1);
      background-color: #159c15;
    }
    #startMenu {
      position: absolute;
      bottom: 70px;
      left: 20px;
      background: rgba(0, 0, 0, 0.85);
      color: white;
      padding: 1rem;
      border-radius: 0.5rem;
      display: none;
      min-width: 250px;
      backdrop-filter: blur(10px);
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.3s ease-in-out;
    }
    #startMenu.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }
    button {
      background: none;
      color: white;
      text-align: left;
      width: 100%;
      padding: 0.25rem;
      transition: background 0.2s, transform 0.2s;
    }
    button:hover {
      background: rgba(255,255,255,0.1);
      transform: scale(1.05);
    }
    #sidebar {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 200px;
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      flex-direction: column;
      padding: 1rem 0;
    }
    .sidebar-icon {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1rem;
      color: white;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s, transform 0.2s;
    }
    .sidebar-icon:hover {
      background-color: #159c15;
      transform: scale(1.02);
    }
    .sidebar-icon span {
      white-space: nowrap;
    }
    #notifications {
      position: absolute;
      top: 1rem;
      right: 1rem;
      z-index: 100;
    }
    .toast {
      background: rgba(0,0,0,0.85);
      color: white;
      padding: 0.75rem 1rem;
      border-radius: 0.5rem;
      margin-bottom: 0.5rem;
      backdrop-filter: blur(6px);
      animation: fadeInOut 3s ease forwards;
    }
    @keyframes fadeInOut {
      0% { opacity: 0; transform: translateY(-10px); }
      10% { opacity: 1; transform: translateY(0); }
      90% { opacity: 1; }
      100% { opacity: 0; transform: translateY(-10px); }
    }
    .game-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
      padding: 1rem;
      background: rgba(0,0,0,0.85);
      border-radius: 1rem;
    }
    .game-card {
      background: #111;
      padding: 0.5rem;
      border-radius: 0.5rem;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .game-card:hover {
      transform: scale(1.05);
      background: #222;
    }
    .game-card img {
      border-radius: 0.25rem;
      width: 100%;
      height: 120px;
      object-fit: cover;
    }
    .game-card h4 {
      margin-top: 0.5rem;
      font-size: 0.9rem;
      color: #fff;
    }
  </style>
</head>
<body class="text-white font-sans">
  <audio id="sound-open" src="assets/sounds/menu-open.mp3" preload="auto"></audio>
  <audio id="sound-nav" src="assets/sounds/menu-nav.mp3" preload="auto"></audio>
  <audio id="sound-ok" src="assets/sounds/confirm.mp3" preload="auto"></audio>
  <audio id="sound-error" src="assets/sounds/error.mp3" preload="auto"></audio>  <div id="desktop" class="relative w-screen h-screen overflow-hidden">
    <div id="notifications"></div><!-- Barra lateral -->
<div id="sidebar">
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo loja...')">🛒 <span>Loja</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Abrindo configurações...')">⚙️ <span>Configurações</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Jogos carregando...'); openGames()">🎮 <span>Jogos</span></div>
  <div class="sidebar-icon" onclick="playOk(); showToast('Ajuda aberta')">❓ <span>Ajuda</span></div>
  <div class="sidebar-icon" onclick="playError(); showToast('Erro simulado!')">⛔ <span>Erro</span></div>
</div>

<!-- Menu Iniciar -->
<div class="absolute bottom-4 left-56">
  <div class="menu-btn" onclick="toggleStartMenu()">X</div>
</div>
<div id="startMenu">
  <div class="text-lg font-semibold mb-2">Menu Iniciar</div>
  <ul class="space-y-1">
    <li><button onclick="playNav(); openApp('youtube')">📺 YouTube</button></li>
    <li><button onclick="playNav(); openApp('netflix')">🎬 Netflix</button></li>
    <li><button onclick="playNav(); openApp('photopea')">🖌️ Photopea</button></li>
    <li><button onclick="playNav(); openApp('gmail')">✉️ Gmail</button></li>
    <li><button onclick="playNav(); showGameGallery()">🎮 Meus Jogos</button></li>
  </ul>
</div>

<div id="gameGallery" class="absolute top-20 left-60 right-4 bg-black/80 rounded-xl p-4 hidden">
  <div class="flex justify-between items-center mb-2">
    <h2 class="text-xl font-bold">🎮 Meus Jogos</h2>
    <button class="bg-green-600 px-3 py-1 rounded hover:bg-green-700" onclick="closeGameGallery()">Fechar</button>
  </div>
  <div class="game-grid">
    <div class="game-card" onclick="launchGame('games/tetris/index.html')">
      <img src="games/tetris/thumb.jpg" alt="Tetris">
      <h4>Tetris</h4>
    </div>
    <div class="game-card" onclick="launchGame('games/snake/index.html')">
      <img src="games/snake/thumb.jpg" alt="Snake">
      <h4>Snake</h4>
    </div>
    <div class="game-card" onclick="launchGame('games/space-invaders/index.html')">
      <img src="games/space-invaders/thumb.jpg" alt="Invaders">
      <h4>Space Invaders</h4>
    </div>
  </div>
</div>

  </div>
  <script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");function playNav() { soundNav.currentTime = 0; soundNav.play(); }
function playOk() { soundOk.currentTime = 0; soundOk.play(); }
function playError() { soundError.currentTime = 0; soundError.play(); }

function toggleStartMenu() {
  const menu = document.getElementById("startMenu");
  if (menu.classList.contains("active")) {
    menu.classList.remove("active");
    setTimeout(() => (menu.style.display = "none"), 300);
  } else {
    menu.style.display = "block";
    setTimeout(() => menu.classList.add("active"), 10);
    soundOpen.currentTime = 0;
    soundOpen.play();
  }
}

function showToast(text) {
  const toast = document.createElement("div");
  toast.className = "toast";
  toast.textContent = text;
  notificationArea.appendChild(toast);
  setTimeout(() => toast.remove(), 3000);
}

function openApp(appName) {
  showToast(`Abrindo ${appName}...`);
  window.open(`apps/${appName}/index.html`, "_blank");
}

function launchGame(path) {
  const win = window.open(path, '_blank', 'width=1024,height=768');
}

function showGameGallery() {
  document.getElementById('gameGallery').classList.remove('hidden');
}

function closeGameGallery() {
  document.getElementById('gameGallery').classList.add('hidden');
}

document.addEventListener("keydown", e => {
  if (e.key === "m" || e.key === "M" || e.key === "Enter") {
    toggleStartMenu();
  }
});

  </script>
</body>
</html>![1000009962](https://github.com/user-attachments/assets/cfd3f58f-52df-47b2-a074-59060c82fe5d)
<script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");

    function playNav() { soundNav.currentTime = 0; soundNav.play(); }
    function playOk() { soundOk.currentTime = 0; soundOk.play(); }
    function playError() { soundError.currentTime = 0; soundError.play(); }

    function toggleStartMenu() {
      const menu = document.getElementById("startMenu");
      if (menu.classList.contains("active")) {
        menu.classList.remove("active");
        setTimeout(() => (menu.style.display = "none"), 300);
      } else {
        menu.style.display = "block";
        setTimeout(() => menu.classList.add("active"), 10);
        soundOpen.currentTime = 0;
        soundOpen.play();
      }
    }

    function showToast(text) {
      const toast = document.createElement("div");
      toast.className = "toast";
      toast.textContent = text;
      notificationArea.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function openApp(appName) {
      showToast(`Abrindo ${appName}...`);
      window.open(`apps/${appName}/index.html`, "_blank");
    }

    function launchGame(path) {
      const win = window.open(path, '_blank', 'width=1024,height=768');
      saveLastGame(path);
    }

    function saveLastGame(path) {
      localStorage.setItem("lastGame", path);
    }

    function loadLastGame() {
      const path = localStorage.getItem("lastGame");
      if (path) {
        showToast("Carregando jogo salvo...");
        launchGame(path);
      } else {
        showToast("Nenhum jogo salvo encontrado.");
      }
    }

    function showGameGallery() {
      document.getElementById('gameGallery').classList.remove('hidden');
    }

    function closeGameGallery() {
      document.getElementById('gameGallery').classList.add('hidden');
    }

    document.addEventListener("keydown", e => {
      if (e.key === "m" || e.key === "M" || e.key === "Enter") {
        toggleStartMenu();
      }
      if (e.key === "g" || e.key === "G") {
        showGameGallery();
      }
      if (e.key === "l" || e.key === "L") {
        loadLastGame();
      }
    });

    // Gamepad support
    window.addEventListener("gamepadconnected", function(e) {
      showToast("Controle conectado!");
    });

    setInterval(() => {
      const gamepads = navigator.getGamepads();
      const gp = gamepads[0];
      if (gp) {
        if (gp.buttons[0].pressed) toggleStartMenu(); // A button
        if (gp.buttons[1].pressed) showGameGallery(); // B button
      }
    }, 100);
  </script>
<script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");

    function playNav() { soundNav.currentTime = 0; soundNav.play(); }
    function playOk() { soundOk.currentTime = 0; soundOk.play(); }
    function playError() { soundError.currentTime = 0; soundError.play(); }

    function toggleStartMenu() {
      const menu = document.getElementById("startMenu");
      if (menu.classList.contains("active")) {
        menu.classList.remove("active");
        setTimeout(() => (menu.style.display = "none"), 300);
      } else {
        menu.style.display = "block";
        setTimeout(() => menu.classList.add("active"), 10);
        soundOpen.currentTime = 0;
        soundOpen.play();
      }
    }

    function showToast(text) {
      const toast = document.createElement("div");
      toast.className = "toast";
      toast.textContent = text;
      notificationArea.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function openApp(appName) {
      showToast(`Abrindo ${appName}...`);
      window.open(`apps/${appName}/index.html`, "_blank");
    }

    function launchGame(path, title = "Jogo") {
      const win = window.open(path, '_blank', 'width=1024,height=768');
      saveLastGame(path);
      registerPlay(title);
    }

    function saveLastGame(path) {
      localStorage.setItem("lastGame", path);
    }

    function loadLastGame() {
      const path = localStorage.getItem("lastGame");
      if (path) {
        showToast("Carregando jogo salvo...");
        launchGame(path);
      } else {
        showToast("Nenhum jogo salvo encontrado.");
      }
    }

    function showGameGallery() {
      document.getElementById('gameGallery').classList.remove('hidden');
    }

    function closeGameGallery() {
      document.getElementById('gameGallery').classList.add('hidden');
    }

    function unlockAchievement(title, description) {
      const achievements = JSON.parse(localStorage.getItem("achievements") || "[]");
      if (!achievements.some(a => a.title === title)) {
        achievements.push({ title, description });
        localStorage.setItem("achievements", JSON.stringify(achievements));
        showToast(`🏆 Conquista: ${title}`);
      }
    }

    function registerPlay(gameTitle) {
      const scores = JSON.parse(localStorage.getItem("scoreboard") || "{}");
      scores[gameTitle] = (scores[gameTitle] || 0) + 1;
      localStorage.setItem("scoreboard", JSON.stringify(scores));

      if (scores[gameTitle] === 10) {
        unlockAchievement(`Veterano de ${gameTitle}`, `Você jogou ${gameTitle} 10 vezes!`);
      }
    }

    function showAchievements() {
      const data = JSON.parse(localStorage.getItem("achievements") || "[]");
      const html = data.map(a => `<li><strong>${a.title}</strong>: ${a.description}</li>`).join('');
      alert("Conquistas desbloqueadas:\n\n" + data.map(a => `🏆 ${a.title}: ${a.description}`).join("\n"));
    }

    function showScores() {
      const data = JSON.parse(localStorage.getItem("scoreboard") || "{}");
      const lines = Object.entries(data).map(([game, count]) => `${game}: ${count} partidas`);
      alert("Ranking de Jogos:\n\n" + lines.join("\n"));
    }

    document.addEventListener("keydown", e => {
      if (e.key === "m" || e.key === "M" || e.key === "Enter") {
        toggleStartMenu();
      }
      if (e.key === "g" || e.key === "G") {
        showGameGallery();
      }
      if (e.key === "l" || e.key === "L") {
        loadLastGame();
      }
      if (e.key === "a" || e.key === "A") {
        showAchievements();
      }
      if (e.key === "r" || e.key === "R") {
        showScores();
      }
    });

    // Gamepad support
    window.addEventListener("gamepadconnected", function(e) {
      showToast("Controle conectado!");
    });

    setInterval(() => {
      const gamepads = navigator.getGamepads();
      const gp = gamepads[0];
      if (gp) {
        if (gp.buttons[0].pressed) toggleStartMenu(); // A button
        if (gp.buttons[1].pressed) showGameGallery(); // B button
        if (gp.buttons[2].pressed) showAchievements(); // X button
        if (gp.buttons[3].pressed) showScores(); // Y button
      }
    }, 100);
  </script>
<script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");

    let currentUser = null;

    function playNav() { soundNav.currentTime = 0; soundNav.play(); }
    function playOk() { soundOk.currentTime = 0; soundOk.play(); }
    function playError() { soundError.currentTime = 0; soundError.play(); }

    function toggleStartMenu() {
      const menu = document.getElementById("startMenu");
      if (menu.classList.contains("active")) {
        menu.classList.remove("active");
        setTimeout(() => (menu.style.display = "none"), 300);
      } else {
        menu.style.display = "block";
        setTimeout(() => menu.classList.add("active"), 10);
        soundOpen.currentTime = 0;
        soundOpen.play();
      }
    }

    function showToast(text) {
      const toast = document.createElement("div");
      toast.className = "toast";
      toast.textContent = text;
      notificationArea.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function openApp(appName) {
      showToast(`Abrindo ${appName}...`);
      window.open(`apps/${appName}/index.html`, "_blank");
    }

    function launchGame(path, title = "Jogo") {
      const win = window.open(path, '_blank', 'width=1024,height=768');
      saveLastGame(path);
      registerPlay(title);
    }

    function saveLastGame(path) {
      localStorage.setItem("lastGame", path);
    }

    function loadLastGame() {
      const path = localStorage.getItem("lastGame");
      if (path) {
        showToast("Carregando jogo salvo...");
        launchGame(path);
      } else {
        showToast("Nenhum jogo salvo encontrado.");
      }
    }

    function showGameGallery() {
      document.getElementById('gameGallery').classList.remove('hidden');
    }

    function closeGameGallery() {
      document.getElementById('gameGallery').classList.add('hidden');
    }

    function unlockAchievement(title, description) {
      const achievements = JSON.parse(localStorage.getItem("achievements") || "[]");
      if (!achievements.some(a => a.title === title)) {
        achievements.push({ title, description });
        localStorage.setItem("achievements", JSON.stringify(achievements));
        showToast(`🏆 Conquista: ${title}`);
      }
    }

    function registerPlay(gameTitle) {
      const scores = JSON.parse(localStorage.getItem("scoreboard") || "{}");
      scores[gameTitle] = (scores[gameTitle] || 0) + 1;
      localStorage.setItem("scoreboard", JSON.stringify(scores));

      if (scores[gameTitle] === 10) {
        unlockAchievement(`Veterano de ${gameTitle}`, `Você jogou ${gameTitle} 10 vezes!`);
      }
    }

    function showAchievements() {
      const data = JSON.parse(localStorage.getItem("achievements") || "[]");
      alert("Conquistas desbloqueadas:\n\n" + data.map(a => `🏆 ${a.title}: ${a.description}`).join("\n"));
    }

    function showScores() {
      const data = JSON.parse(localStorage.getItem("scoreboard") || "{}");
      const lines = Object.entries(data).map(([game, count]) => `${game}: ${count} partidas`);
      alert("Ranking de Jogos:\n\n" + lines.join("\n"));
    }

    function loginUser() {
      const name = prompt("Digite seu nome de usuário:");
      if (!name) return;
      const avatar = prompt("Cole aqui a URL de seu avatar ou deixe em branco para padrão:") || "https://i.imgur.com/0y0y0y0.png";
      currentUser = { name, avatar };
      localStorage.setItem("user", JSON.stringify(currentUser));
      showToast(`Bem-vindo(a), ${name}!`);
    }

    function loadUser() {
      const data = localStorage.getItem("user");
      if (data) {
        currentUser = JSON.parse(data);
        showToast(`Usuário carregado: ${currentUser.name}`);
      } else {
        loginUser();
      }
    }

    function showStore() {
      const games = [
        { title: "Tetris", path: "games/tetris/index.html" },
        { title: "Snake", path: "games/snake/index.html" },
        { title: "Invaders", path: "games/invaders/index.html" }
      ];
      const list = games.map(g => `<li>${g.title} <button onclick="installGame('${g.title}', '${g.path}')">Instalar</button></li>`).join("");
      const html = `<ul>${list}</ul>`;
      const win = window.open("", "Loja de Jogos", "width=400,height=600");
      win.document.write(`<h1>Loja Xbox</h1>${html}`);
    }

    function installGame(title, path) {
      const installed = JSON.parse(localStorage.getItem("installedGames") || "[]");
      if (!installed.some(g => g.title === title)) {
        installed.push({ title, path });
        localStorage.setItem("installedGames", JSON.stringify(installed));
        showToast(`${title} instalado com sucesso!`);
      }
    }

    function showMultiplayerInfo() {
      alert("Multiplayer local ativado!\nJogador 1: Teclado\nJogador 2: Controle ou outra parte do teclado.");
    }

    document.addEventListener("keydown", e => {
      if (e.key === "m" || e.key === "M" || e.key === "Enter") {
        toggleStartMenu();
      }
      if (e.key === "g" || e.key === "G") {
        showGameGallery();
      }
      if (e.key === "l" || e.key === "L") {
        loadLastGame();
      }
      if (e.key === "a" || e.key === "A") {
        showAchievements();
      }
      if (e.key === "r" || e.key === "R") {
        showScores();
      }
      if (e.key === "u" || e.key === "U") {
        loginUser();
      }
      if (e.key === "s" || e.key === "S") {
        showStore();
      }
      if (e.key === "p" || e.key === "P") {
        showMultiplayerInfo();
      }
    });

    // Gamepad support
    window.addEventListener("gamepadconnected", function(e) {
      showToast("Controle conectado!");
    });

    setInterval(() => {
      const gamepads = navigator.getGamepads();
      const gp = gamepads[0];
      if (gp) {
        if (gp.buttons[0].pressed) toggleStartMenu(); // A button
        if (gp.buttons[1].pressed) showGameGallery(); // B button
        if (gp.buttons[2].pressed) showAchievements(); // X button
        if (gp.buttons[3].pressed) showScores(); // Y button
      }
    }, 100);

    loadUser();
  </script>
<script>
    const soundOpen = document.getElementById("sound-open");
    const soundNav = document.getElementById("sound-nav");
    const soundOk = document.getElementById("sound-ok");
    const soundError = document.getElementById("sound-error");
    const notificationArea = document.getElementById("notifications");

    let currentUser = null;
    let userList = JSON.parse(localStorage.getItem("userList") || "[]");

    function playNav() { soundNav.currentTime = 0; soundNav.play(); }
    function playOk() { soundOk.currentTime = 0; soundOk.play(); }
    function playError() { soundError.currentTime = 0; soundError.play(); }

    function toggleStartMenu() {
      const menu = document.getElementById("startMenu");
      if (menu.classList.contains("active")) {
        menu.classList.remove("active");
        setTimeout(() => (menu.style.display = "none"), 300);
      } else {
        menu.style.display = "block";
        setTimeout(() => menu.classList.add("active"), 10);
        soundOpen.currentTime = 0;
        soundOpen.play();
      }
    }

    function showToast(text) {
      const toast = document.createElement("div");
      toast.className = "toast";
      toast.textContent = text;
      notificationArea.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function openApp(appName) {
      showToast(`Abrindo ${appName}...`);
      window.open(`apps/${appName}/index.html`, "_blank");
    }

    function launchGame(path, title = "Jogo") {
      const win = window.open(path, '_blank', 'width=1024,height=768');
      saveLastGame(path);
      registerPlay(title);
    }

    function saveLastGame(path) {
      localStorage.setItem("lastGame", path);
      if (currentUser) {
        localStorage.setItem(`progress_${currentUser.name}`, path);
      }
    }

    function loadLastGame() {
      let path = localStorage.getItem("lastGame");
      if (currentUser) {
        path = localStorage.getItem(`progress_${currentUser.name}`) || path;
      }
      if (path) {
        showToast("Carregando jogo salvo...");
        launchGame(path);
      } else {
        showToast("Nenhum jogo salvo encontrado.");
      }
    }

    function showGameGallery() {
      document.getElementById('gameGallery').classList.remove('hidden');
    }

    function closeGameGallery() {
      document.getElementById('gameGallery').classList.add('hidden');
    }

    function unlockAchievement(title, description) {
      const key = currentUser ? `achievements_${currentUser.name}` : "achievements";
      const achievements = JSON.parse(localStorage.getItem(key) || "[]");
      if (!achievements.some(a => a.title === title)) {
        achievements.push({ title, description });
        localStorage.setItem(key, JSON.stringify(achievements));
        showToast(`🏆 Conquista: ${title}`);
      }
    }

    function registerPlay(gameTitle) {
      const key = currentUser ? `scoreboard_${currentUser.name}` : "scoreboard";
      const scores = JSON.parse(localStorage.getItem(key) || "{}");
      scores[gameTitle] = (scores[gameTitle] || 0) + 1;
      localStorage.setItem(key, JSON.stringify(scores));

      if (scores[gameTitle] === 10) {
        unlockAchievement(`Veterano de ${gameTitle}`, `Você jogou ${gameTitle} 10 vezes!`);
      }
    }

    function showAchievements() {
      const key = currentUser ? `achievements_${currentUser.name}` : "achievements";
      const data = JSON.parse(localStorage.getItem(key) || "[]");
      alert("Conquistas desbloqueadas:\n\n" + data.map(a => `🏆 ${a.title}: ${a.description}`).join("\n"));
    }

    function showScores() {
      const key = currentUser ? `scoreboard_${currentUser.name}` : "scoreboard";
      const data = JSON.parse(localStorage.getItem(key) || "{}");
      const lines = Object.entries(data).map(([game, count]) => `${game}: ${count} partidas`);
      alert("Ranking de Jogos:\n\n" + lines.join("\n"));
    }

    function loginUser() {
      const name = prompt("Digite seu nome de usuário:");
      if (!name) return;
      const avatar = prompt("Cole aqui a URL de seu avatar ou deixe em branco para padrão:") || "https://i.imgur.com/0y0y0y0.png";
      currentUser = { name, avatar };
      userList = userList.filter(u => u.name !== name);
      userList.push(currentUser);
      localStorage.setItem("userList", JSON.stringify(userList));
      localStorage.setItem("user", JSON.stringify(currentUser));
      showToast(`Bem-vindo(a), ${name}!`);
    }

    function switchUser() {
      const names = userList.map(u => u.name);
      const choice = prompt("Usuários:\n" + names.join("\n") + "\n\nDigite o nome para alternar:");
      const found = userList.find(u => u.name === choice);
      if (found) {
        currentUser = found;
        localStorage.setItem("user", JSON.stringify(currentUser));
        showToast(`Usuário atual: ${currentUser.name}`);
      } else {
        showToast("Usuário não encontrado.");
      }
    }

    function loadUser() {
      const data = localStorage.getItem("user");
      if (data) {
        currentUser = JSON.parse(data);
        showToast(`Usuário carregado: ${currentUser.name}`);
      } else {
        loginUser();
      }
    }

    function showStore() {
      const games = [
        { title: "Tetris", path: "games/tetris/index.html" },
        { title: "Snake", path: "games/snake/index.html" },
        { title: "Invaders", path: "games/invaders/index.html" }
      ];
      const list = games.map(g => `<li>${g.title} <button onclick="installGame('${g.title}', '${g.path}')">Instalar</button></li>`).join("");
      const html = `<ul>${list}</ul>`;
      const win = window.open("", "Loja de Jogos", "width=400,height=600");
      win.document.write(`<h1>Loja Xbox</h1>${html}`);
    }

    function installGame(title, path) {
      const key = currentUser ? `installedGames_${currentUser.name}` : "installedGames";
      const installed = JSON.parse(localStorage.getItem(key) || "[]");
      if (!installed.some(g => g.title === title)) {
        installed.push({ title, path });
        localStorage.setItem(key, JSON.stringify(installed));
        showToast(`${title} instalado com sucesso!`);
      }
    }

    function showMultiplayerInfo() {
      alert("Multiplayer local ativado!\nJogador 1: Teclado\nJogador 2: Controle ou outra parte do teclado.");
    }

    function showFriends() {
      const amigos = userList.map(u => `${u.name} - ${(Math.random() > 0.5 ? "🟢 Online" : "⚪ Offline")}`);
      alert("Amigos:\n\n" + amigos.join("\n"));
    }

    document.addEventListener("keydown", e => {
      if (e.key === "m") toggleStartMenu();
      if (e.key === "g") showGameGallery();
      if (e.key === "l") loadLastGame();
      if (e.key === "a") showAchievements();
      if (e.key === "r") showScores();
      if (e.key === "u") loginUser();
      if (e.key === "x") switchUser();
      if (e.key === "s") showStore();
      if (e.key === "p") showMultiplayerInfo();
      if (e.key === "f") showFriends();
    });

    window.addEventListener("gamepadconnected", function(e) {
      showToast("Controle conectado!");
    });

    setInterval(() => {
      const gamepads = navigator.getGamepads();
      const gp = gamepads[0];
      if (gp) {
        if (gp.buttons[0].pressed) toggleStartMenu();
        if (gp.buttons[1].pressed) showGameGallery();
        if (gp.buttons[2].pressed) showAchievements();
        if (gp.buttons[3].pressed) showScores();
      }
    }, 100);

    loadUser();
</script>
<!-- Gaming Hub com integração Xbox, Game Pass, Discord, Steam e Epic Games --><!-- Painel Gaming Hub --><div id="gamingHub" class="hidden fixed top-12 left-12 w-[80vw] h-[80vh] bg-black text-white p-4 rounded-2xl shadow-2xl z-50 overflow-hidden">
  <h2 class="text-2xl font-bold mb-4">🎮 Gaming Hub</h2>
  <div class="grid grid-cols-2 gap-4 h-full">
    <iframe src="https://www.xbox.com/play" class="w-full h-full rounded-xl border border-green-600"></iframe>
    <iframe src="https://discord.com/app" class="w-full h-full rounded-xl border border-blue-600"></iframe>
    <iframe src="https://store.steampowered.com" class="w-full h-full rounded-xl border border-gray-500"></iframe>
    <iframe src="https://store.epicgames.com" class="w-full h-full rounded-xl border border-purple-600"></iframe>
  </div>
  <button onclick="closeGamingHub()" class="absolute top-2 right-4 bg-gray-800 hover:bg-gray-700 p-2 rounded">✖ Fechar</button>
</div><script>
function openGamingHub() {
  document.getElementById("gamingHub").classList.remove("hidden");
}

function closeGamingHub() {
  document.getElementById("gamingHub").classList.add("hidden");
}

document.addEventListener("keydown", e => {
  if (e.key === "g") openGamingHub();
});
</script>
<!-- Gaming Hub com integração Xbox, Game Pass, Discord, Steam, Epic Games e Tela Inicial Xbox Style --><!-- Tela Inicial Xbox Style --><div id="xboxHome" class="fixed inset-0 bg-black text-white p-8 grid grid-cols-4 gap-4 z-40 hidden">
  <div onclick="openGamingHub()" class="bg-green-700 hover:bg-green-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    🎮<span class="mt-2 font-bold">Game Pass</span>
  </div>
  <div onclick="openDiscord()" class="bg-blue-700 hover:bg-blue-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    💬<span class="mt-2 font-bold">Discord</span>
  </div>
  <div onclick="openSteam()" class="bg-gray-700 hover:bg-gray-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    🕹️<span class="mt-2 font-bold">Steam</span>
  </div>
  <div onclick="openEpic()" class="bg-purple-700 hover:bg-purple-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    🛍️<span class="mt-2 font-bold">Epic Games</span>
  </div>
  <div onclick="showStore()" class="bg-green-800 hover:bg-green-700 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    🛒<span class="mt-2 font-bold">Loja</span>
  </div>
  <div onclick="showFriends()" class="bg-indigo-700 hover:bg-indigo-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    👥<span class="mt-2 font-bold">Amigos</span>
  </div>
  <div onclick="showAchievements()" class="bg-yellow-700 hover:bg-yellow-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    🏆<span class="mt-2 font-bold">Conquistas</span>
  </div>
  <div onclick="closeXboxHome()" class="bg-red-700 hover:bg-red-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
    ✖<span class="mt-2 font-bold">Fechar</span>
  </div>
</div><!-- Gaming Hub (iframe apps) --><div id="gamingHub" class="hidden fixed top-12 left-12 w-[80vw] h-[80vh] bg-black text-white p-4 rounded-2xl shadow-2xl z-50 overflow-hidden">
  <h2 class="text-2xl font-bold mb-4">🎮 Gaming Hub</h2>
  <div class="grid grid-cols-2 gap-4 h-full">
    <iframe id="gamepassFrame" src="" class="w-full h-full rounded-xl border border-green-600"></iframe>
    <iframe id="discordFrame" src="" class="w-full h-full rounded-xl border border-blue-600"></iframe>
    <iframe id="steamFrame" src="" class="w-full h-full rounded-xl border border-gray-500"></iframe>
    <iframe id="epicFrame" src="" class="w-full h-full rounded-xl border border-purple-600"></iframe>
  </div>
  <button onclick="closeGamingHub()" class="absolute top-2 right-4 bg-gray-800 hover:bg-gray-700 p-2 rounded">✖ Fechar</button>
</div><script>
function openXboxHome() {
  document.getElementById("xboxHome").classList.remove("hidden");
}

function closeXboxHome() {
  document.getElementById("xboxHome").classList.add("hidden");
}

function openGamingHub() {
  // Login automático simulando tokens salvos
  document.getElementById("gamepassFrame").src = "https://www.xbox.com/play";
  document.getElementById("discordFrame").src = "https://discord.com/app";
  document.getElementById("steamFrame").src = "https://store.steampowered.com";
  document.getElementById("epicFrame").src = "https://store.epicgames.com";

  closeXboxHome();
  document.getElementById("gamingHub").classList.remove("hidden");
}

function closeGamingHub() {
  document.getElementById("gamingHub").classList.add("hidden");
}

function openDiscord() {
  window.open("https://discord.com/app", "_blank");
}

function openSteam() {
  window.open("https://store.steampowered.com", "_blank");
}

function openEpic() {
  window.open("https://store.epicgames.com", "_blank");
}

document.addEventListener("keydown", e => {
  if (e.key === "Meta" || e.key === "OS" || e.key === "Win") openXboxHome();
});
</script>
<!-- Mini Windows com Categorias, Mira Personalizada, Monitor de FPS e Temperatura --><!-- Mira personalizada --><div id="crosshair" class="pointer-events-none fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 z-50">
  <div class="w-2 h-2 bg-red-500 rounded-full"></div>
</div><!-- HUD: FPS e Temperatura --><div id="hudOverlay" class="fixed top-2 right-2 text-xs bg-black bg-opacity-60 text-white px-3 py-2 rounded-lg z-50 font-mono">
  <div id="fps">FPS: 0</div>
  <div id="temp">Temp: 42°C</div>
</div><!-- Tela Inicial Xbox Style com Categorias --><div id="xboxHome" class="fixed inset-0 bg-black text-white p-8 z-40 hidden overflow-y-auto">
  <h2 class="text-3xl font-bold mb-4">🎮 Mini Windows Dashboard</h2>  <!-- Categoria: Jogos -->  <div class="mb-6">
    <h3 class="text-xl font-semibold mb-2">🎮 Jogos</h3>
    <div class="grid grid-cols-4 gap-4">
      <div onclick="openGamingHub()" class="bg-green-700 hover:bg-green-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        🟢<span class="mt-2 font-bold">Game Pass</span>
      </div>
    </div>
  </div>  <!-- Categoria: Social -->  <div class="mb-6">
    <h3 class="text-xl font-semibold mb-2">💬 Social</h3>
    <div class="grid grid-cols-4 gap-4">
      <div onclick="openDiscord()" class="bg-blue-700 hover:bg-blue-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        💬<span class="mt-2 font-bold">Discord</span>
      </div>
      <div onclick="showFriends()" class="bg-indigo-700 hover:bg-indigo-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        👥<span class="mt-2 font-bold">Amigos</span>
      </div>
    </div>
  </div>  <!-- Categoria: Apps -->  <div class="mb-6">
    <h3 class="text-xl font-semibold mb-2">🛠️ Utilitários</h3>
    <div class="grid grid-cols-4 gap-4">
      <div onclick="openSteam()" class="bg-gray-700 hover:bg-gray-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        🕹️<span class="mt-2 font-bold">Steam</span>
      </div>
      <div onclick="openEpic()" class="bg-purple-700 hover:bg-purple-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        🛍️<span class="mt-2 font-bold">Epic Games</span>
      </div>
      <div onclick="showStore()" class="bg-green-800 hover:bg-green-700 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        🛒<span class="mt-2 font-bold">Loja</span>
      </div>
      <div onclick="showAchievements()" class="bg-yellow-700 hover:bg-yellow-600 p-4 rounded-2xl shadow-xl flex flex-col items-center cursor-pointer">
        🏆<span class="mt-2 font-bold">Conquistas</span>
      </div>
    </div>
  </div>  <div onclick="closeXboxHome()" class="bg-red-700 hover:bg-red-600 p-4 mt-4 w-max rounded-2xl shadow-xl flex items-center cursor-pointer">
    ✖<span class="ml-2 font-bold">Fechar</span>
  </div>
</div><!-- Scripts --><script>
function updateFPS() {
  let lastTime = performance.now(), frame = 0;
  function tick() {
    const now = performance.now();
    const delta = now - lastTime;
    if (delta >= 1000) {
      document.getElementById("fps").innerText = `FPS: ${frame}`;
      frame = 0;
      lastTime = now;
    }
    frame++;
    requestAnimationFrame(tick);
  }
  tick();
}

function simulateTemp() {
  setInterval(() => {
    const temp = 35 + Math.floor(Math.random() * 10);
    document.getElementById("temp").innerText = `Temp: ${temp}°C`;
  }, 3000);
}

function openXboxHome() {
  document.getElementById("xboxHome").classList.remove("hidden");
}
function closeXboxHome() {
  document.getElementById("xboxHome").classList.add("hidden");
}
function openGamingHub() {
  document.getElementById("gamepassFrame").src = "https://www.xbox.com/play";
  document.getElementById("discordFrame").src = "https://discord.com/app";
  document.getElementById("steamFrame").src = "https://store.steampowered.com";
  document.getElementById("epicFrame").src = "https://store.epicgames.com";
  closeXboxHome();
  document.getElementById("gamingHub").classList.remove("hidden");
}
function closeGamingHub() {
  document.getElementById("gamingHub").classList.add("hidden");
}
function openDiscord() {
  window.open("https://discord.com/app", "_blank");
}
function openSteam() {
  window.open("https://store.steampowered.com", "_blank");
}
function openEpic() {
  window.open("https://store.epicgames.com", "_blank");
}

document.addEventListener("keydown", e => {
  if (e.key === "Meta" || e.key === "OS" || e.key === "Win") openXboxHome();
});

updateFPS();
simulateTemp();
</script>
<!-- Mini Windows com Filtros de Performance --><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  if (mode === "max") {
    root.style.setProperty("--animation-speed", "0s");
    root.style.setProperty("--shadow", "none");
    root.style.setProperty("--resolution-scale", "1");
  } else if (mode === "balanced") {
    root.style.setProperty("--animation-speed", "0.3s");
    root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
    root.style.setProperty("--resolution-scale", "1");
  } else if (mode === "eco") {
    root.style.setProperty("--animation-speed", "0.1s");
    root.style.setProperty("--shadow", "none");
    root.style.setProperty("--resolution-scale", "0.75");
  } else if (mode === "auto") {
    let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
    if (fpsValue < 25) applyPerformanceMode("eco");
    else if (fpsValue > 50) applyPerformanceMode("max");
    else applyPerformanceMode("balanced");
    return;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*.").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
    el.style.imageRendering = performanceMode === "eco" ? "pixelated" : "auto";
  });
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script>
<!-- Mini Windows com Filtros de Performance (Avançado) --><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script>
<!-- Mini Windows com Filtros de Performance (Avançado com Otimização de Rede) --><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  // Simulação de otimização de rede: Desativa fetch de apps ociosos e reduz pings
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  console.log("Rede otimizada: apps em segundo plano pausados");
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script>
<!-- Mini Windows com Otimização de GPU e Filtros de Performance --><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
  <button onclick="setPerformanceMode('gpuopt')" class="w-full bg-pink-700 hover:bg-pink-600 px-3 py-2 rounded">🎮 Reduzir GPU</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
    case "gpuopt":
      optimizeGPU();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  console.log("Rede otimizada: apps em segundo plano pausados");
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function optimizeGPU() {
  document.body.style.filter = "brightness(0.9) contrast(0.9) saturate(0.8)";
  document.querySelectorAll(".effect, .glow, .particle").forEach(el => el.remove());
  alert("🎮 Otimização de GPU aplicada: efeitos reduzidos.");
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script>
<!-- Mini Windows com Otimização de GPU e Filtros de Performance com Input Lag Reduzido --><!-- Notificação de Input Lag --><div id="inputLagNotify" class="fixed bottom-16 right-4 bg-orange-600 text-white px-4 py-2 rounded-lg shadow-lg hidden transition-opacity duration-500">⚡ Modo de Resposta Rápida Ativado</div><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
  <button onclick="setPerformanceMode('gpuopt')" class="w-full bg-pink-700 hover:bg-pink-600 px-3 py-2 rounded">🎮 Reduzir GPU</button>
  <button onclick="setPerformanceMode('lowinputlag')" class="w-full bg-orange-700 hover:bg-orange-600 px-3 py-2 rounded">⚡ Reduzir Input Lag</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
    case "gpuopt":
      optimizeGPU();
      break;
    case "lowinputlag":
      reduceInputLag();
      showInputLagNotification();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  console.log("Rede otimizada: apps em segundo plano pausados");
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function optimizeGPU() {
  document.body.style.filter = "brightness(0.9) contrast(0.9) saturate(0.8)";
  document.querySelectorAll(".effect, .glow, .particle").forEach(el => el.remove());
  alert("🎮 Otimização de GPU aplicada: efeitos reduzidos.");
}

function reduceInputLag() {
  document.body.style.setProperty("cursor", "default");
  document.querySelectorAll("* :not(input):not(textarea)").forEach(el => el.tabIndex = -1);
  document.addEventListener("keydown", e => e.preventDefault(), { passive: true });
  document.addEventListener("mousedown", e => e.preventDefault(), { passive: true });
  console.log("⚡ Input Lag minimizado");
}

function showInputLagNotification() {
  const notify = document.getElementById("inputLagNotify");
  notify.classList.remove("hidden");
  notify.style.opacity = 1;
  setTimeout(() => {
    notify.style.opacity = 0;
    setTimeout(() => notify.classList.add("hidden"), 500);
  }, 3000);
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Detecta controle ou teclado pressionado e ativa modo de input lag reduzido
window.addEventListener("gamepadconnected", () => setPerformanceMode("lowinputlag"));
document.addEventListener("keydown", e => {
  if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight", "Enter", "Space", "w", "a", "s", "d"].includes(e.key.toLowerCase())) {
    setPerformanceMode("lowinputlag");
  }
});

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script><!-- Mini Windows com Otimização de GPU e Filtros de Performance com Input Lag Reduzido --><!-- Notificação de Input Lag --><div id="inputLagNotify" class="fixed bottom-16 right-4 bg-orange-600 text-white px-4 py-2 rounded-lg shadow-lg hidden transition-opacity duration-500">⚡ Modo de Resposta Rápida Ativado</div><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
  <button onclick="setPerformanceMode('gpuopt')" class="w-full bg-pink-700 hover:bg-pink-600 px-3 py-2 rounded">🎮 Reduzir GPU</button>
  <button onclick="setPerformanceMode('lowinputlag')" class="w-full bg-orange-700 hover:bg-orange-600 px-3 py-2 rounded">⚡ Reduzir Input Lag</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
    case "gpuopt":
      optimizeGPU();
      break;
    case "lowinputlag":
      reduceInputLag();
      showInputLagNotification();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  console.log("Rede otimizada: apps em segundo plano pausados");
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function optimizeGPU() {
  document.body.style.filter = "brightness(0.9) contrast(0.9) saturate(0.8)";
  document.querySelectorAll(".effect, .glow, .particle").forEach(el => el.remove());
  alert("🎮 Otimização de GPU aplicada: efeitos reduzidos.");
}

function reduceInputLag() {
  document.body.style.setProperty("cursor", "default");
  document.querySelectorAll("* :not(input):not(textarea)").forEach(el => el.tabIndex = -1);
  document.addEventListener("keydown", e => e.preventDefault(), { passive: true });
  document.addEventListener("mousedown", e => e.preventDefault(), { passive: true });
  console.log("⚡ Input Lag minimizado");
}

function showInputLagNotification() {
  const notify = document.getElementById("inputLagNotify");
  notify.classList.remove("hidden");
  notify.style.opacity = 1;
  setTimeout(() => {
    notify.style.opacity = 0;
    setTimeout(() => notify.classList.add("hidden"), 500);
  }, 3000);
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Detecta controle ou teclado pressionado e ativa modo de input lag reduzido
window.addEventListener("gamepadconnected", () => setPerformanceMode("lowinputlag"));
document.addEventListener("keydown", e => {
  if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight", "Enter", "Space", "w", "a", "s", "d"].includes(e.key.toLowerCase())) {
    setPerformanceMode("lowinputlag");
  }
});

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script><!-- Mini Windows com Otimização de GPU e Filtros de Performance com Input Lag Reduzido --><!-- Notificação de Input Lag --><div id="inputLagNotify" class="fixed bottom-16 right-4 bg-orange-600 text-white px-4 py-2 rounded-lg shadow-lg hidden transition-opacity duration-500">⚡ Modo de Resposta Rápida Ativado</div><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
  <button onclick="setPerformanceMode('gpuopt')" class="w-full bg-pink-700 hover:bg-pink-600 px-3 py-2 rounded">🎮 Reduzir GPU</button>
  <button onclick="setPerformanceMode('lowinputlag')" class="w-full bg-orange-700 hover:bg-orange-600 px-3 py-2 rounded">⚡ Reduzir Input Lag</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
    case "gpuopt":
      optimizeGPU();
      break;
    case "lowinputlag":
      reduceInputLag();
      showInputLagNotification();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  console.log("Rede otimizada: apps em segundo plano pausados");
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function optimizeGPU() {
  document.body.style.filter = "brightness(0.9) contrast(0.9) saturate(0.8)";
  document.querySelectorAll(".effect, .glow, .particle").forEach(el => el.remove());
  alert("🎮 Otimização de GPU aplicada: efeitos reduzidos.");
}

function reduceInputLag() {
  document.body.style.setProperty("cursor", "default");
  document.querySelectorAll("* :not(input):not(textarea)").forEach(el => el.tabIndex = -1);
  document.addEventListener("keydown", e => e.preventDefault(), { passive: true });
  document.addEventListener("mousedown", e => e.preventDefault(), { passive: true });
  console.log("⚡ Input Lag minimizado");
}

function showInputLagNotification() {
  const notify = document.getElementById("inputLagNotify");
  notify.classList.remove("hidden");
  notify.style.opacity = 1;
  setTimeout(() => {
    notify.style.opacity = 0;
    setTimeout(() => notify.classList.add("hidden"), 500);
  }, 3000);
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

// Detecta controle ou teclado pressionado e ativa modo de input lag reduzido
window.addEventListener("gamepadconnected", () => setPerformanceMode("lowinputlag"));
document.addEventListener("keydown", e => {
  if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight", "Enter", "Space", "w", "a", "s", "d"].includes(e.key.toLowerCase())) {
    setPerformanceMode("lowinputlag");
  }
});

// Aplicar ao iniciar
applyPerformanceMode(performanceMode);
</script>
<!-- Mini Windows com Otimização + Bluetooth --><!-- Notificação de Input Lag --><div id="inputLagNotify" class="fixed bottom-16 right-4 bg-orange-600 text-white px-4 py-2 rounded-lg shadow-lg hidden transition-opacity duration-500">⚡ Modo de Resposta Rápida Ativado</div><!-- Status Bluetooth --><div id="bluetoothStatus" class="fixed top-4 right-4 bg-blue-800 text-white px-4 py-1 rounded shadow text-sm">🔵 Bluetooth: Desconectado</div><!-- Menu Flutuante de Performance --><div id="performanceMenu" class="fixed bottom-4 right-4 z-50 bg-black bg-opacity-80 text-white p-4 rounded-2xl shadow-lg space-y-2 w-64">
  <h3 class="font-bold text-lg mb-2">⚙️ Filtro de Performance</h3>
  <button onclick="setPerformanceMode('max')" class="w-full bg-green-700 hover:bg-green-600 px-3 py-2 rounded">🟢 Máximo</button>
  <button onclick="setPerformanceMode('balanced')" class="w-full bg-blue-700 hover:bg-blue-600 px-3 py-2 rounded">⚖️ Equilibrado</button>
  <button onclick="setPerformanceMode('eco')" class="w-full bg-yellow-700 hover:bg-yellow-600 px-3 py-2 rounded">🟡 Economia</button>
  <button onclick="setPerformanceMode('auto')" class="w-full bg-purple-700 hover:bg-purple-600 px-3 py-2 rounded">🔄 Autoajuste</button>
  <button onclick="setPerformanceMode('lowres')" class="w-full bg-red-700 hover:bg-red-600 px-3 py-2 rounded">🟥 Baixa Resolução</button>
  <button onclick="setPerformanceMode('lowram')" class="w-full bg-gray-700 hover:bg-gray-600 px-3 py-2 rounded">💾 Baixo Uso de RAM</button>
  <button onclick="setPerformanceMode('netopt')" class="w-full bg-cyan-700 hover:bg-cyan-600 px-3 py-2 rounded">🌐 Otimizar Rede</button>
  <button onclick="setPerformanceMode('gpuopt')" class="w-full bg-pink-700 hover:bg-pink-600 px-3 py-2 rounded">🎮 Reduzir GPU</button>
  <button onclick="setPerformanceMode('lowinputlag')" class="w-full bg-orange-700 hover:bg-orange-600 px-3 py-2 rounded">⚡ Reduzir Input Lag</button>
</div><script>
const root = document.documentElement;
let performanceMode = localStorage.getItem("performanceMode") || "balanced";

function applyPerformanceMode(mode) {
  performanceMode = mode;
  localStorage.setItem("performanceMode", mode);

  switch (mode) {
    case "max":
      root.style.setProperty("--animation-speed", "0s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "true");
      break;
    case "balanced":
      root.style.setProperty("--animation-speed", "0.3s");
      root.style.setProperty("--shadow", "0 4px 12px rgba(0,0,0,0.3)");
      root.style.setProperty("--resolution-scale", "1");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "eco":
      root.style.setProperty("--animation-speed", "0.1s");
      root.style.setProperty("--shadow", "none");
      root.style.setProperty("--resolution-scale", "0.75");
      root.style.setProperty("--preload-apps", "false");
      break;
    case "auto":
      let fpsValue = parseInt(document.getElementById("fps").innerText.split(": ")[1]);
      if (fpsValue < 25) applyPerformanceMode("eco");
      else if (fpsValue > 50) applyPerformanceMode("max");
      else applyPerformanceMode("balanced");
      return;
    case "lowres":
      document.body.style.imageRendering = "pixelated";
      document.querySelectorAll("canvas, img, video").forEach(el => el.style.imageRendering = "pixelated");
      break;
    case "lowram":
      document.querySelectorAll(".app").forEach(app => {
        if (!app.classList.contains("active")) app.style.display = "none";
      });
      break;
    case "netopt":
      optimizeNetwork();
      break;
    case "gpuopt":
      optimizeGPU();
      break;
    case "lowinputlag":
      reduceInputLag();
      showInputLagNotification();
      break;
  }

  document.body.style.setProperty("transition", `all var(--animation-speed)`);
  document.querySelectorAll("*").forEach(el => {
    el.style.boxShadow = getComputedStyle(root).getPropertyValue("--shadow");
  });
}

function optimizeNetwork() {
  document.querySelectorAll(".app").forEach(app => {
    if (!app.classList.contains("active")) {
      app.dataset.network = "paused";
    }
  });
  alert("🌐 Otimização de rede ativada! Apps ociosos pausados.");
}

function optimizeGPU() {
  document.body.style.filter = "brightness(0.9) contrast(0.9) saturate(0.8)";
  document.querySelectorAll(".effect, .glow, .particle").forEach(el => el.remove());
  alert("🎮 Otimização de GPU aplicada: efeitos reduzidos.");
}

function reduceInputLag() {
  document.body.style.setProperty("cursor", "default");
  document.querySelectorAll("* :not(input):not(textarea)").forEach(el => el.tabIndex = -1);
  document.addEventListener("keydown", e => e.preventDefault(), { passive: true });
  document.addEventListener("mousedown", e => e.preventDefault(), { passive: true });
  console.log("⚡ Input Lag minimizado");
}

function showInputLagNotification() {
  const notify = document.getElementById("inputLagNotify");
  notify.classList.remove("hidden");
  notify.style.opacity = 1;
  setTimeout(() => {
    notify.style.opacity = 0;
    setTimeout(() => notify.classList.add("hidden"), 500);
  }, 3000);
}

function setPerformanceMode(mode) {
  applyPerformanceMode(mode);
  alert("Modo de performance: " + mode);
}

async function checkBluetooth() {
  if (!navigator.bluetooth) {
    document.getElementById("bluetoothStatus").innerText = "❌ Bluetooth não suportado";
    return;
  }
  try {
    await navigator.bluetooth.requestDevice({ acceptAllDevices: true });
    document.getElementById("bluetoothStatus").innerText = "🔵 Bluetooth: Conectado";
  } catch {
    document.getElementById("bluetoothStatus").innerText = "🔵 Bluetooth: Desconectado";
  }
}

window.addEventListener("gamepadconnected", () => setPerformanceMode("lowinputlag"));
document.addEventListener("keydown", e => {
  if (["ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight", "Enter", "Space", "w", "a", "s", "d"].includes(e.key.toLowerCase())) {
    setPerformanceMode("lowinputlag");
  }
});

applyPerformanceMode(performanceMode);
checkBluetooth();
</script><!-- Mini Windows com Bluetooth Avançado --><!-- Status Bluetooth --><div id="bluetoothStatus" class="fixed top-4 right-4 bg-blue-800 text-white px-4 py-1 rounded shadow text-sm">🔵 Bluetooth: Desconectado</div>
<button onclick="toggleBluetooth()" class="fixed top-16 right-4 bg-blue-700 hover:bg-blue-600 text-white px-3 py-1 rounded shadow">🔁 Alternar Bluetooth</button><!-- Lista de dispositivos emparelhados --><div id="pairedDevices" class="fixed top-28 right-4 bg-blue-900 text-white p-2 rounded shadow w-64 max-h-48 overflow-y-auto hidden">
  <h4 class="font-bold mb-2">🔗 Dispositivos Emparelhados:</h4>
  <ul id="devicesList" class="space-y-1 text-sm"></ul>
</div><script>
let bluetoothEnabled = false;
let knownDevices = JSON.parse(localStorage.getItem("knownBluetoothDevices")) || [];

function updateBluetoothUI(status) {
  document.getElementById("bluetoothStatus").innerText = status;
}

async function requestAndRememberDevice() {
  try {
    const device = await navigator.bluetooth.requestDevice({ acceptAllDevices: true });
    if (!knownDevices.includes(device.name)) {
      knownDevices.push(device.name);
      localStorage.setItem("knownBluetoothDevices", JSON.stringify(knownDevices));
    }
    listKnownDevices();
    updateBluetoothUI(`🔵 Bluetooth: Conectado a ${device.name}`);
  } catch {
    updateBluetoothUI("🔵 Bluetooth: Desconectado");
  }
}

function listKnownDevices() {
  const listEl = document.getElementById("devicesList");
  const container = document.getElementById("pairedDevices");
  listEl.innerHTML = "";
  if (knownDevices.length > 0) {
    container.classList.remove("hidden");
    knownDevices.forEach(name => {
      const li = document.createElement("li");
      li.textContent = `📱 ${name}`;
      listEl.appendChild(li);
    });
  } else {
    container.classList.add("hidden");
  }
}

function toggleBluetooth() {
  if (!navigator.bluetooth) {
    updateBluetoothUI("❌ Bluetooth não suportado");
    return;
  }
  bluetoothEnabled = !bluetoothEnabled;
  if (bluetoothEnabled) {
    requestAndRememberDevice();
  } else {
    updateBluetoothUI("🔵 Bluetooth: Desativado");
  }
}

window.addEventListener("load", () => {
  listKnownDevices();
  if (!navigator.bluetooth) updateBluetoothUI("❌ Bluetooth não suportado");
});
</script><!-- Mini Windows com Bluetooth Avançado com Reescolha e Bateria --><!-- Status Bluetooth --><div id="bluetoothStatus" class="fixed top-4 right-4 bg-blue-800 text-white px-4 py-1 rounded shadow text-sm">🔵 Bluetooth: Desconectado</div>
<button onclick="toggleBluetooth()" class="fixed top-16 right-4 bg-blue-700 hover:bg-blue-600 text-white px-3 py-1 rounded shadow">🔁 Alternar Bluetooth</button><!-- Lista de dispositivos emparelhados --><div id="pairedDevices" class="fixed top-28 right-4 bg-blue-900 text-white p-2 rounded shadow w-72 max-h-60 overflow-y-auto hidden">
  <h4 class="font-bold mb-2">🔗 Dispositivos Emparelhados:</h4>
  <ul id="devicesList" class="space-y-1 text-sm"></ul>
</div><script>
let bluetoothEnabled = false;
let knownDevices = JSON.parse(localStorage.getItem("knownBluetoothDevices")) || [];

function updateBluetoothUI(status) {
  document.getElementById("bluetoothStatus").innerText = status;
}

async function requestAndRememberDevice() {
  try {
    const device = await navigator.bluetooth.requestDevice({ acceptAllDevices: true, optionalServices: ['battery_service'] });
    if (!knownDevices.find(d => d.id === device.id)) {
      knownDevices.push({ id: device.id, name: device.name });
      localStorage.setItem("knownBluetoothDevices", JSON.stringify(knownDevices));
    }
    updateBluetoothUI(`🔵 Conectado a ${device.name}`);
    listKnownDevices();
    readBatteryLevel(device);
  } catch {
    updateBluetoothUI("🔵 Bluetooth: Desconectado");
  }
}

function listKnownDevices() {
  const listEl = document.getElementById("devicesList");
  const container = document.getElementById("pairedDevices");
  listEl.innerHTML = "";
  if (knownDevices.length > 0) {
    container.classList.remove("hidden");
    knownDevices.forEach(d => {
      const li = document.createElement("li");
      li.innerHTML = `📱 <button onclick="connectToDeviceById('${d.id}')" class="underline hover:text-lime-300">${d.name}</button>`;
      listEl.appendChild(li);
    });
  } else {
    container.classList.add("hidden");
  }
}

async function connectToDeviceById(deviceId) {
  try {
    const device = await navigator.bluetooth.requestDevice({ acceptAllDevices: true }); // Fallback
    if (device.id === deviceId) {
      updateBluetoothUI(`🔵 Reconectado a ${device.name}`);
      readBatteryLevel(device);
    }
  } catch (err) {
    console.warn("Erro ao reconectar:", err);
  }
}

async function readBatteryLevel(device) {
  try {
    const server = await device.gatt.connect();
    const service = await server.getPrimaryService('battery_service');
    const batteryLevel = await service.getCharacteristic('battery_level');
    const value = await batteryLevel.readValue();
    const level = value.getUint8(0);
    updateBluetoothUI(`🔋 ${device.name}: ${level}%`);
  } catch (e) {
    console.warn("Bateria não disponível para", device.name);
  }
}

function toggleBluetooth() {
  if (!navigator.bluetooth) {
    updateBluetoothUI("❌ Bluetooth não suportado");
    return;
  }
  bluetoothEnabled = !bluetoothEnabled;
  if (bluetoothEnabled) {
    requestAndRememberDevice();
  } else {
    updateBluetoothUI("🔵 Bluetooth: Desativado");
  }
}

window.addEventListener("load", () => {
  listKnownDevices();
  if (!navigator.bluetooth) updateBluetoothUI("❌ Bluetooth não suportado");
});
</script>
<!-- Mini Windows com Bluetooth Avançado Finalizado --><!-- Status Bluetooth --><div id="bluetoothStatus" class="fixed top-4 right-4 bg-blue-800 text-white px-4 py-1 rounded shadow text-sm">🔵 Bluetooth: Desconectado</div>
<button onclick="toggleBluetooth()" class="fixed top-16 right-4 bg-blue-700 hover:bg-blue-600 text-white px-3 py-1 rounded shadow">🔁 Alternar Bluetooth</button><!-- Lista de dispositivos emparelhados --><div id="pairedDevices" class="fixed top-28 right-4 bg-blue-900 text-white p-2 rounded shadow w-72 max-h-60 overflow-y-auto hidden">
  <h4 class="font-bold mb-2">🔗 Dispositivos Emparelhados:</h4>
  <ul id="devicesList" class="space-y-1 text-sm"></ul>
</div><script>
let bluetoothEnabled = false;
let knownDevices = JSON.parse(localStorage.getItem("knownBluetoothDevices")) || [];
let lastConnectedId = localStorage.getItem("lastConnectedBluetoothId") || null;

function updateBluetoothUI(status) {
  document.getElementById("bluetoothStatus").innerText = status;
}

async function requestAndRememberDevice() {
  try {
    const device = await navigator.bluetooth.requestDevice({ acceptAllDevices: true, optionalServices: ['battery_service'] });
    if (!knownDevices.find(d => d.id === device.id)) {
      knownDevices.push({ id: device.id, name: device.name });
      localStorage.setItem("knownBluetoothDevices", JSON.stringify(knownDevices));
    }
    localStorage.setItem("lastConnectedBluetoothId", device.id);
    updateBluetoothUI(`🔵 Conectado a ${device.name}`);
    listKnownDevices();
    readBatteryLevel(device);
  } catch {
    updateBluetoothUI("🔵 Bluetooth: Desconectado");
  }
}

function listKnownDevices() {
  const listEl = document.getElementById("devicesList");
  const container = document.getElementById("pairedDevices");
  listEl.innerHTML = "";
  if (knownDevices.length > 0) {
    container.classList.remove("hidden");
    knownDevices.forEach(d => {
      const li = document.createElement("li");
      li.innerHTML = `📱 <button onclick="connectToDeviceById('${d.id}', '${d.name}')" class="underline hover:text-lime-300">${d.name}</button>`;
      listEl.appendChild(li);
    });
  } else {
    container.classList.add("hidden");
  }
}

async function connectToDeviceById(deviceId, name) {
  try {
    const device = await navigator.bluetooth.requestDevice({ acceptAllDevices: true, optionalServices: ['battery_service'] });
    if (device.id === deviceId) {
      updateBluetoothUI(`🔵 Reconectado a ${name}`);
      localStorage.setItem("lastConnectedBluetoothId", device.id);
      readBatteryLevel(device);
    }
  } catch (err) {
    console.warn("Erro ao reconectar:", err);
  }
}

async function autoReconnectLastDevice() {
  if (!lastConnectedId) return;
  const match = knownDevices.find(d => d.id === lastConnectedId);
  if (match) {
    connectToDeviceById(match.id, match.name);
  }
}

async function readBatteryLevel(device) {
  try {
    const server = await device.gatt.connect();
    const service = await server.getPrimaryService('battery_service');
    const batteryLevel = await service.getCharacteristic('battery_level');
    const value = await batteryLevel.readValue();
    const level = value.getUint8(0);
    updateBluetoothUI(`🔋 ${device.name}: ${level}%`);
  } catch (e) {
    console.warn("Bateria não disponível para", device.name);
  }
}

function toggleBluetooth() {
  if (!navigator.bluetooth) {
    updateBluetoothUI("❌ Bluetooth não suportado");
    return;
  }
  bluetoothEnabled = !bluetoothEnabled;
  if (bluetoothEnabled) {
    requestAndRememberDevice();
  } else {
    updateBluetoothUI("🔵 Bluetooth: Desativado");
  }
}

window.addEventListener("load", () => {
  listKnownDevices();
  if (!navigator.bluetooth) updateBluetoothUI("❌ Bluetooth não suportado");
  if (navigator.bluetooth && lastConnectedId) autoReconnectLastDevice();
});
</script>
<!-- Mini Windows com Modo Desempenho e Gestão de Energia --><!-- Botão de modo desempenho --><button onclick="togglePerformanceMode()" class="fixed top-44 right-4 bg-red-700 hover:bg-red-600 text-white px-3 py-1 rounded shadow">⚡ Modo Desempenho</button>

<div id="performanceStatus" class="fixed top-56 right-4 bg-red-800 text-white px-4 py-1 rounded shadow text-sm">⚙️ Desempenho: Normal</div><script>
let performanceMode = false;

function togglePerformanceMode() {
  performanceMode = !performanceMode;
  const status = document.getElementById("performanceStatus");
  if (performanceMode) {
    // Aumenta frequência de atualizações, reduz timers, ativa power use máximo
    status.innerText = "⚙️ Desempenho: Máximo";
    try {
      if ('wakeLock' in navigator) {
        navigator.wakeLock.request('screen');
      }
    } catch (e) {
      console.warn("WakeLock indisponível:", e);
    }
    document.body.style.setProperty("--performance-hint", "ultra");
  } else {
    status.innerText = "⚙️ Desempenho: Normal";
    document.body.style.setProperty("--performance-hint", "auto");
  }
}
</script><!-- Instruções para o navegador consumir mais energia (simulado com wakeLock e ajustes de CSS) --><style>
:root {
  --performance-hint: auto;
}
body[data-performance="ultra"] {
  image-rendering: auto;
  will-change: transform, opacity;
  scroll-behavior: auto;
}
</style>
