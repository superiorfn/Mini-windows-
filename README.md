mini-windows/
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
atualizarRelogio();
