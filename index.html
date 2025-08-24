<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<title>Editor Completo — Ace + Console (JS / Python / HTML) + .ino</title>
<meta name="viewport" content="width=device-width,initial-scale=1" />
<style>
  :root{
    --bg:#1e1e1e; --panel:#333; --side:#252526; --muted:#9aa0a6; --accent:#0a84ff; --text:#fff;
    --node-hover:#2b2b2b; --node-active:#0a84ff; --node-active-text:#000;
    --console-bg:#0f0f0f; --console-border:#222;
    --log:#d1d1d1; --info:#8ab4f8; --warn:#fbbc05; --error:#ff6b6b; --match:#ffd866;
  }
  body.light{
    --bg:#f5f6f8; --panel:#e9eaee; --side:#f0f1f4; --muted:#5f6368; --accent:#0b57d0; --text:#111;
    --node-hover:#e1e3e8; --node-active:#bcd1ff; --node-active-text:#0b2a6b;
    --console-bg:#ffffff; --console-border:#dcdfe3;
    --log:#303134; --info:#174ea6; --warn:#a66300; --error:#b31412; --match:#e37400;
  }
  html,body{height:100%; margin:0; font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;}
  body{background:var(--bg); color:var(--text); display:flex; flex-direction:column;}
  #topbar{display:flex; gap:8px; align-items:center; padding:8px; background:var(--panel); border-bottom:1px solid rgba(0,0,0,.2)}
  button, select, input{background:#2f2f2f; color:#fff; border:0; padding:8px 10px; border-radius:6px; cursor:pointer;}
  body.light button, body.light select, body.light input{background:#ffffff; color:#111; border:1px solid #d0d3d8;}
  button:hover, select:hover, input:hover{filter:brightness(1.06)}
  .small{padding:6px 8px; font-size:13px}

  #main{flex:1; display:flex; min-height:0;}
  #left{width:300px; background:var(--side); display:flex; flex-direction:column; gap:8px; padding:10px; box-sizing:border-box;}
  #filetree{flex:1; overflow:auto; border-radius:6px; padding:6px; background:rgba(0,0,0,.15)}
  .node{padding:6px; border-radius:4px; cursor:pointer; user-select:none;}
  .node:hover{background:var(--node-hover)}
  .node.active{background:var(--node-active); color:var(--node-active-text)}
  .node.match{ font-weight:600; color:var(--match); }
  #left.drop{ outline:2px dashed var(--accent); outline-offset:-6px; }

  #editor-wrap{flex:1; display:flex; flex-direction:column; min-width:0;}
  #tabbar{display:flex; gap:6px; padding:6px; border-bottom:1px solid rgba(0,0,0,.2); background:rgba(0,0,0,.12); overflow:auto; scrollbar-width:thin;}
  body.light #tabbar{background:#f7f8fb;}
  .tab{display:flex; align-items:center; gap:6px; padding:6px 10px; border-radius:8px; background:#2f2f2f; color:#fff; cursor:grab; user-select:none}
  body.light .tab{background:#ffffff; color:#111; border:1px solid #d0d3d8;}
  .tab.active{background:var(--accent); color:#fff; cursor:default}
  .tab .close{font-weight:700; opacity:.8; cursor:pointer}
  .tab .close:hover{opacity:1}
  .tab[draggable="true"]{cursor:grabbing;}
  #editor{height:100%; flex:1;}

  #console-wrap{display:flex; flex-direction:column; height:240px; border-top:1px solid var(--console-border);}
  #console-tools{display:flex; gap:8px; align-items:center; padding:6px 8px; background:rgba(0,0,0,.15)}
  body.light #console-tools{background:#eef0f4;}
  #console{flex:1; background:var(--console-bg); font-family:ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace; padding:8px; overflow:auto;}
  #console .line{white-space:pre-wrap; margin:2px 0; padding:2px 6px; border-radius:4px;}
  #console .log{color:var(--log)}
  #console .info{color:var(--info)}
  #console .warn{color:var(--warn); background:rgba(255,186,0,.08)}
  #console .error{color:var(--error); background:rgba(255,0,0,.08)}
  #console mark.hl{ background:rgba(255, 216, 102, .35); padding:0 2px; border-radius:3px; }

  .status{margin-left:auto; color:var(--muted); font-size:13px;}
  label{color:var(--muted); font-size:13px;}
  #search{width:100%; padding:8px; border-radius:6px; border:0; background:#2b2b2b; color:#fff;}
  body.light #search{background:#fff; color:#111; border:1px solid #d0d3d8;}

  #preview{display:none; height:50vh; border-top:1px solid var(--console-border);}
  footer{padding:6px 10px; color:var(--muted); font-size:13px; background:#161616}
  body.light footer{background:#f1f3f7}
</style>
</head>
<body>

<div id="topbar">
  <div id="toolbar-actions">
    <button onclick="novoArquivo()" title="Novo arquivo" aria-label="Criar novo arquivo">Novo</button>
    <button onclick="abrirArquivosPC()" title="Abrir arquivos do seu PC (.py .js .html .css .json .ino)" aria-label="Abrir arquivos">Abrir</button>
    <button onclick="salvarArquivo()" title="Salvar arquivo atual" aria-label="Salvar">Salvar</button>
    <button onclick="downloadAll()" title="Download projeto .zip" aria-label="Baixar ZIP">Download ZIP</button>
    <select id="extensao" onchange="mudarModo()" class="small" title="Selecionar linguagem" aria-label="Selecionar linguagem">
      <option value="python">Python (.py)</option>
      <option value="javascript">JavaScript (.js)</option>
      <option value="html">HTML (.html)</option>
      <option value="css">CSS (.css)</option>
      <option value="json">JSON (.json)</option>
      <option value="c_cpp">Arduino (.ino)</option>
    </select>
    <button onclick="executarJS()" title="Executar como JavaScript">Run JS</button>
    <button id="btn-runpy" onclick="executarPy()" title="Executar como Python (Pyodide)" disabled>Run Py</button>
    <button onclick="preverHTML()" title="Pré-visualizar HTML">Preview HTML</button>
    <button id="btn-clear" onclick="consoleClear()" class="small" title="Limpar Console">Limpar Console</button>
    <button id="btn-theme" onclick="toggleTheme()" class="small" title="Alternar tema">Tema: Escuro</button>
  </div>
  <div class="status" id="py-status">Pyodide: carregando...</div>
</div>

<div id="main">
  <div id="left" aria-label="Lateral - arquivos (arraste arquivos aqui)">
    <div style="display:flex; gap:8px;">
      <input id="search" placeholder="Buscar (nome/conteúdo)..." oninput="searchTree()" aria-label="Buscar no projeto" />
      <button onclick="newFolder()" title="Nova pasta" class="small">+Pasta</button>
    </div>
    <div id="filetree" aria-label="Árvore de arquivos"></div>
    <!-- drag and drop dica -->
    <div style="font-size:12px; color:var(--muted); padding:6px 2px;">Dica: arraste arquivos/pastas do seu PC pra cá.</div>
  </div>

  <div id="editor-wrap">
    <div id="tabbar" aria-label="Abas de arquivos"></div>
    <div id="editor"></div>

    <div id="preview">
      <div style="display:flex; align-items:center; gap:8px; background:rgba(0,0,0,.15); padding:6px 8px;">
        <span style="color:var(--muted); font-size:13px;">Preview</span>
        <button class="small" onclick="fecharPreview()">Fechar</button>
      </div>
      <iframe id="preview-frame" style="width:100%; height:calc(100% - 34px); border:none;"></iframe>
    </div>

    <div id="console-wrap">
      <div id="console-tools">
        <label for="console-search">Buscar na saída:</label>
        <input id="console-search" placeholder="Digite e Enter para buscar…" onkeydown="consoleSearchKey(event)" class="small" style="flex:1" />
        <button class="small" onclick="consoleFindPrev()" title="Ocorrência anterior">◀</button>
        <button class="small" onclick="consoleFindNext()" title="Próxima ocorrência">▶</button>
        <span id="console-find-status" class="status"></span>
      </div>
      <div id="console" aria-live="polite"></div>
    </div>
  </div>
</div>

<footer>
  Editor offline — .py .js .html .css .json .ino —
  Atalhos: F5=Run JS • Ctrl+P=Preview • Ctrl+S=Salvar • Ctrl+F/ Ctrl+H = Buscar/Substituir • Ctrl+Tab/Shift+Ctrl+Tab = mudar aba • Ctrl+W = fechar aba
</footer>

<!-- Ace Editor -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/ace/1.4.14/ace.js" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/ace/1.4.14/ext-language_tools.js"></script>

<!-- Pyodide -->
<script src="https://cdn.jsdelivr.net/pyodide/v0.24.1/full/pyodide.js"></script>

<!-- JSZip & FileSaver for ZIP download -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>

<script>
/* ------------------ Editor (Ace) ------------------ */
const editor = ace.edit("editor", {useWorker:false});
const THEMES = { dark:"ace/theme/monokai", light:"ace/theme/chrome" };
let isLight = false;

editor.setTheme(THEMES.dark);
editor.session.setMode("ace/mode/python");
editor.setOptions({
  enableBasicAutocompletion: true,
  enableLiveAutocompletion: true,
  enableSnippets: true,
  fontSize: "13px",
  tabSize: 2,
  wrap: true
});
editor.renderer.setScrollMargin(8,8,8,8);

/* snippets Arduino (setup + loop + helpers) */
const snippetManager = ace.require("ace/snippets").snippetManager;
const arduinoSnip = `
snippet setup
\tvoid setup() {
\t\t// inicialização
\t}

snippet loop
\tvoid loop() {
\t\t// loop principal
\t}

snippet pinMode
\tpinMode(\${1:pin}, \${2:OUTPUT});

snippet pinmode
\tpinMode(\${1:pin}, \${2:OUTPUT});

snippet digitalWrite
\tdigitalWrite(\${1:pin}, \${2:HIGH});

snippet analogRead
\tanalogRead(\${1:pin});
`;
snippetManager.register(snippetManager.parseSnippetFile(arduinoSnip), "c_cpp");

/* ------------------ Projeto virtual + Abas ------------------ */
let root = {type:'folder', name:'root', children:[]};
let currentFile = null;
let openTabs = []; // array de nós de arquivo

function renderTree(){
  const el = document.getElementById('filetree');
  el.innerHTML = '';
  function nodeEl(node, depth=0){
    const d = document.createElement('div');
    d.className = 'node' + (node===currentFile ? ' active' : '');
    d.style.paddingLeft = (depth*12)+'px';
    d.textContent = node.name + (node.type==='folder' ? '/' : '');
    d.onclick = (e)=>{
      e.stopPropagation();
      if(node.type==='file'){ saveCurrent(); openInTab(node); }
    };
    d.oncontextmenu = (ev)=>{ ev.preventDefault(); contextActions(node); };
    return d;
  }
  function walk(parent, depth=0){
    parent.children.forEach(ch=>{
      el.appendChild(nodeEl(ch, depth));
      if(ch.children) walk(ch, depth+1);
    });
  }
  walk(root,0);
}

function contextActions(node){
  const action = prompt("ação (renomear / deletar / cancelar):", "renomear");
  if(!action) return;
  const cmd = action.trim().toLowerCase();
  if(cmd === 'renomear'){
    const novo = prompt("novo nome:", node.name);
    if(novo && !existsSiblingWithName(node, novo)) { node.name = novo; updateMode(node.name); persist(); renderTree(); renderTabs(); if(node===currentFile){ loadCurrent(); } }
    else if(novo){ alert('Já existe item com esse nome neste nível.'); }
  } else if(cmd === 'deletar'){
    if(!confirm("deletar '"+node.name+"' ?")) return;
    removeNode(root, node);
    const idx = openTabs.indexOf(node);
    if(idx>=0){ openTabs.splice(idx,1); }
    if(node===currentFile) { currentFile = openTabs[0] || null; loadCurrent(); }
    persist(); renderTree(); renderTabs();
  }
}
function existsSiblingWithName(node, newName){
  function parentOf(target, parent){
    if(!parent) parent = root;
    for(const ch of parent.children){
      if(ch === target) return parent;
      if(ch.children){ const res = parentOf(target, ch); if(res) return res; }
    }
    return null;
  }
  const p = parentOf(node);
  return p && p.children.some(ch=>ch!==node && ch.name===newName);
}
function removeNode(parent, target){
  for(let i=0;i<parent.children.length;i++){
    const ch = parent.children[i];
    if(ch===target){ parent.children.splice(i,1); return true; }
    if(ch.children) if(removeNode(ch, target)) return true;
  }
  return false;
}

/* Tabs */
function renderTabs(){
  const bar = document.getElementById('tabbar');
  bar.innerHTML = '';
  openTabs.forEach((file, i)=>{
    const t = document.createElement('div');
    t.className = 'tab' + (file===currentFile ? ' active' : '');
    t.draggable = true;
    t.dataset.idx = i;
    t.title = file.name;

    const span = document.createElement('span');
    span.textContent = file.name;
    const close = document.createElement('span');
    close.textContent = '×';
    close.className = 'close';
    close.onclick = (ev)=>{ ev.stopPropagation(); closeTab(file); };

    t.appendChild(span); t.appendChild(close);
    t.onclick = ()=>{ saveCurrent(); setCurrent(file); };
    // drag reorder
    t.addEventListener('dragstart', (e)=>{ e.dataTransfer.setData('text/plain', i); });
    t.addEventListener('dragover', (e)=>{ e.preventDefault(); });
    t.addEventListener('drop', (e)=>{
      e.preventDefault();
      const from = parseInt(e.dataTransfer.getData('text/plain'),10);
      const to = i;
      if(from===to) return;
      const [m] = openTabs.splice(from,1);
      openTabs.splice(to,0,m);
      renderTabs(); persist();
    });

    bar.appendChild(t);
  });
}
function openInTab(file){
  if(!openTabs.includes(file)) openTabs.push(file);
  setCurrent(file);
}
function setCurrent(file){
  currentFile = file;
  loadCurrent();
  renderTabs();
  renderTree();
}
function closeTab(file){
  const idx = openTabs.indexOf(file);
  if(idx>=0) openTabs.splice(idx,1);
  if(currentFile===file){
    currentFile = openTabs[idx] || openTabs[idx-1] || null;
    loadCurrent();
  }
  renderTabs(); persist();
}

/* Criar arquivos/pastas */
function novoArquivoDefaultName(ext='ino'){
  const base = 'novo_' + Math.random().toString(36).slice(2,7);
  return base + '.' + ext;
}
function defaultContentForExt(name){
  const n = name.toLowerCase();
  if(n.endsWith('.py')) return '# Python\n';
  if(n.endsWith('.js')) return '// JavaScript\n';
  if(n.endsWith('.html')) return '<!doctype html>\n<html>\n<head><meta charset="utf-8"><title>Preview</title></head>\n<body>\n\n</body>\n</html>';
  if(n.endsWith('.css')) return '/* CSS */\n';
  if(n.endsWith('.json')) return '{}';
  if(n.endsWith('.ino')) return 'void setup() {\n  // setup\n}\n\nvoid loop() {\n  // loop\n}\n';
  return '';
}
function novoArquivo(){
  const extMap = {'python':'py','javascript':'js','html':'html','css':'css','json':'json','c_cpp':'ino'};
  const sel = document.getElementById('extensao').value;
  const ext = extMap[sel] || 'txt';
  const name = prompt("Nome do arquivo:", novoArquivoDefaultName(ext));
  if(!name) return;
  const file = {type:'file', name:name, content: defaultContentForExt(name)};
  root.children.push(file);
  openInTab(file);
  persist(); renderTree();
}
function newFolder(){
  const name = prompt("Nome da pasta:", "nova_pasta");
  if(!name) return;
  root.children.push({type:'folder', name:name, children:[]});
  persist(); renderTree();
}

/* Abrir do PC — múltiplos + drag-and-drop + (opcional) pasta */
function abrirArquivosPC(){
  const inp = document.createElement('input');
  inp.type = 'file';
  inp.multiple = true;
  inp.accept = '.py,.js,.html,.css,.json,.ino,.c,.cpp,.h,.txt';
  // opcional: com ALT pressionado, seleciona pasta
  // (webkitdirectory só funciona via propriedade direta)
  if(window.event && window.event.altKey){ inp.setAttribute('webkitdirectory',''); }
  inp.onchange = (e)=>{ importFileList(e.target.files); };
  inp.click();
}
function importFileList(fileList){
  [...fileList].forEach(f=>{
    const r = new FileReader();
    r.onload = (ev)=>{
      const node = ensurePathAndCreateFile(f.webkitRelativePath || f.name, ev.target.result);
      openInTab(node);
      persist(); renderTree();
    };
    r.readAsText(f);
  });
}
/* drag-and-drop */
const leftEl = document.getElementById('left');
leftEl.addEventListener('dragover', (e)=>{ e.preventDefault(); leftEl.classList.add('drop'); });
leftEl.addEventListener('dragleave', ()=> leftEl.classList.remove('drop'));
leftEl.addEventListener('drop', (e)=>{
  e.preventDefault(); leftEl.classList.remove('drop');
  const files = e.dataTransfer.files;
  if(files && files.length) importFileList(files);
});
/* cria pastas a partir de path "folder/sub/name.ext" */
function ensurePathAndCreateFile(path, content){
  const parts = path.split('/').filter(Boolean);
  let parent = root;
  for(let i=0;i<parts.length-1;i++){
    const folderName = parts[i];
    let f = parent.children.find(c=>c.type==='folder' && c.name===folderName);
    if(!f){ f = {type:'folder', name:folderName, children:[]}; parent.children.push(f); }
    parent = f;
  }
  const fname = parts[parts.length-1];
  let file = parent.children.find(c=>c.type==='file' && c.name===fname);
  if(!file){ file = {type:'file', name:fname, content:content||''}; parent.children.push(file); }
  else{ file.content = content||file.content; }
  return file;
}

/* salvar arquivo atual (download com MIME correto) */
function salvarArquivo(){
  saveCurrent();
  if(!currentFile){ alert('Nenhum arquivo selecionado.'); return; }
  const mime = mimeForName(currentFile.name);
  const blob = new Blob([currentFile.content || ''], {type:mime});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = currentFile.name;
  a.click();
  URL.revokeObjectURL(a.href);
}
function mimeForName(name=''){
  const n = name.toLowerCase();
  if(n.endsWith('.html')||n.endsWith('.htm')) return 'text/html;charset=utf-8';
  if(n.endsWith('.css')) return 'text/css;charset=utf-8';
  if(n.endsWith('.js')) return 'application/javascript;charset=utf-8';
  if(n.endsWith('.json')) return 'application/json;charset=utf-8';
  if(n.endsWith('.py')||n.endsWith('.ino')||n.endsWith('.c')||n.endsWith('.cpp')||n.endsWith('.h')||n.endsWith('.txt')) return 'text/plain;charset=utf-8';
  return 'application/octet-stream';
}

/* download projeto como ZIP (recursivo) */
function downloadAll(){
  saveCurrent();
  const zip = new JSZip();
  function add(n, path=''){
    if(n.type==='file') zip.file(path + n.name, n.content || '');
    else if(n.type==='folder') n.children.forEach(ch=>add(ch, path + n.name + '/'));
  }
  root.children.forEach(ch=>add(ch,'')); // root children
  zip.generateAsync({type:'blob'}).then(content=>saveAs(content, 'projeto.zip'));
}

/* salvar atual no objeto */
function saveCurrent(){
  if(currentFile && currentFile.type==='file'){
    currentFile.content = editor.getValue();
  }
  persist();
}

/* carregar atual do objeto para editor + modo pela extensão */
function loadCurrent(){
  if(!currentFile){ editor.setValue('', -1); return; }
  editor.setValue(currentFile.content || '', -1);
  updateMode(currentFile.name);
  editor.focus();
}

/* detecta modo pela extensão automaticamente */
function updateMode(filename){
  const name = (filename||'').toLowerCase();
  if(name.endsWith('.py')) editor.session.setMode('ace/mode/python');
  else if(name.endsWith('.js')) editor.session.setMode('ace/mode/javascript');
  else if(name.endsWith('.html')||name.endsWith('.htm')) editor.session.setMode('ace/mode/html');
  else if(name.endsWith('.css')) editor.session.setMode('ace/mode/css');
  else if(name.endsWith('.json')) editor.session.setMode('ace/mode/json');
  else if(name.endsWith('.ino')||name.endsWith('.c')||name.endsWith('.cpp')||name.endsWith('.h')) editor.session.setMode('ace/mode/c_cpp');
  else editor.session.setMode('ace/mode/text');

  // reflete seleção manual também
  const sel = document.getElementById('extensao');
  if(name.endsWith('.py')) sel.value = 'python';
  else if(name.endsWith('.js')) sel.value = 'javascript';
  else if(name.endsWith('.html')||name.endsWith('.htm')) sel.value = 'html';
  else if(name.endsWith('.css')) sel.value = 'css';
  else if(name.endsWith('.json')) sel.value = 'json';
  else if(name.endsWith('.ino')||name.endsWith('.c')||name.endsWith('.cpp')||name.endsWith('.h')) sel.value = 'c_cpp';
}
function mudarModo(){
  const sel = document.getElementById('extensao').value;
  const map = {'python':'python','javascript':'javascript','html':'html','css':'css','json':'json','c_cpp':'c_cpp'};
  editor.session.setMode('ace/mode/' + (map[sel]||'text'));
}

/* buscar na árvore (segura contra XSS) */
function searchTree(){
  const term = document.getElementById('search').value.trim().toLowerCase();
  const el = document.getElementById('filetree');
  el.innerHTML = '';
  function walk(node, depth=0){
    node.children.forEach(ch=>{
      const d = document.createElement('div');
      d.style.paddingLeft = (depth*12)+'px';
      d.className = 'node' + (ch===currentFile ? ' active' : '');
      const matches = (term && (ch.name.toLowerCase().includes(term) || (ch.content && (ch.content+'').toLowerCase().includes(term))));
      d.textContent = ch.name + (ch.type==='folder' ? '/' : '');
      if(matches) d.classList.add('match');
      d.onclick = (e)=>{ e.stopPropagation(); if(ch.type==='file'){ saveCurrent(); openInTab(ch); } };
      d.oncontextmenu = (ev)=>{ ev.preventDefault(); contextActions(ch); }
      el.appendChild(d);
      if(ch.children) walk(ch, depth+1);
    });
  }
  walk(root,0);
}

/* ------------------ Console / Execução ------------------ */
const consoleEl = document.getElementById('console');
const consoleFindInput = document.getElementById('console-search');
const consoleFindStatus = document.getElementById('console-find-status');
let consoleMatches = [];
let consoleMatchIndex = -1;

function consoleLogLine(type, text){
  const div = document.createElement('div');
  div.className = 'line ' + (type||'log');
  // segura: nunca injeta HTML cru
  div.textContent = text;
  consoleEl.appendChild(div);
  consoleEl.scrollTop = consoleEl.scrollHeight;
}
function toText(val){
  if(typeof val === 'string') return val;
  try{ return JSON.stringify(val, null, 2); }catch{ return String(val); }
}
function consoleLog(...args){ args.forEach(a=>consoleLogLine('log', toText(a))); }
function consoleInfo(...args){ args.forEach(a=>consoleLogLine('info', toText(a))); }
function consoleWarn(...args){ args.forEach(a=>consoleLogLine('warn', toText(a))); }
function consoleError(...args){ args.forEach(a=>consoleLogLine('error', toText(a))); }

function consoleClear(){ consoleEl.innerHTML = ''; clearConsoleSearch(); }

/* Executar JS com captura customizada */
function executarJS(){
  saveCurrent();
  if(!currentFile){ alert('Selecione um arquivo ou crie um.'); return; }
  const code = currentFile.content || editor.getValue();
  consoleClear();
  const oLog = console.log, oWarn = console.warn, oErr = console.error, oInfo = console.info;
  console.log = (...a)=>{ consoleLog(...a); oLog.apply(console,a); };
  console.warn = (...a)=>{ consoleWarn(...a); oWarn.apply(console,a); };
  console.error = (...a)=>{ consoleError(...a); oErr.apply(console,a); };
  console.info = (...a)=>{ consoleInfo(...a); oInfo.apply(console,a); };
  try{
    const result = eval(code);
    if(result !== undefined) consoleInfo('> ' + toText(result));
  } catch(e){
    consoleError('Exception: ' + (e && e.toString ? e.toString() : e));
  } finally {
    console.log = oLog; console.warn = oWarn; console.error = oErr; console.info = oInfo;
  }
}

/* Preview HTML (em painel próprio) */
function preverHTML(){
  saveCurrent();
  if(!currentFile){ alert('Selecione um arquivo .html'); return; }
  const name = currentFile.name.toLowerCase();
  if(!name.endsWith('.html') && !name.endsWith('.htm')){
    if(!confirm('Arquivo atual não é HTML. Pré-visualizar conteúdo atual como HTML?')) return;
  }
  const src = currentFile.content || editor.getValue();
  consoleClear();
  const pv = document.getElementById('preview');
  const frame = document.getElementById('preview-frame');
  pv.style.display = 'block';
  frame.srcdoc = src;
}
function fecharPreview(){
  const pv = document.getElementById('preview');
  const frame = document.getElementById('preview-frame');
  pv.style.display = 'none';
  frame.srcdoc = '';
}

/* ------------------ Pyodide (Python) ------------------ */
let pyodide = null;
const pyStatusEl = document.getElementById('py-status');
const btnRunPy = document.getElementById('btn-runpy');

async function loadPyodideAndInit(){
  pyStatusEl.textContent = 'Pyodide: carregando... (pode demorar)';
  try{
    pyodide = await loadPyodide({indexURL:"https://cdn.jsdelivr.net/pyodide/v0.24.1/full/"});
    await pyodide.runPythonAsync(`
import sys, io
sys.stdout = io.StringIO()
sys.stderr = sys.stdout
`);
    pyStatusEl.textContent = 'Pyodide: pronto';
    btnRunPy.disabled = false;
  }catch(err){
    pyStatusEl.textContent = 'Pyodide: erro ao carregar';
    consoleError('Pyodide load error: ' + (err && err.toString ? err.toString() : err));
    btnRunPy.disabled = true;
  }
}
loadPyodideAndInit();

/* Executar Python com captura de stdout/stderr */
async function executarPy(){
  saveCurrent();
  if(!pyodide){ alert('Pyodide ainda não carregou.'); return; }
  const code = currentFile ? (currentFile.content || '') : editor.getValue();
  consoleClear();
  try{
    await pyodide.runPythonAsync(`import sys, io\nsys.stdout = io.StringIO()\nsys.stderr = sys.stdout`);
    await pyodide.runPythonAsync(code);
    const out = await pyodide.runPythonAsync('sys.stdout.getvalue()');
    if(out) out.split(/\n/).forEach(line=>consoleLogLine('info', line));
  } catch(e){
    consoleError('Python exec error: ' + (e.toString ? e.toString() : e));
  }
}

/* ------------------ Console: busca com destaque + navegação ------------------ */
function escapeHtml(s){ return s.replace(/[&<>"']/g, c=>({ '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;' }[c])); }
function highlightInElement(el, term){
  const text = el.textContent;
  if(!term) return el.textContent = text; // limpa
  const re = new RegExp(term.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'), 'gi');
  const parts = text.split(re);
  const matches = text.match(re);
  if(!matches) return;
  let html = '';
  for(let i=0;i<parts.length;i++){
    html += escapeHtml(parts[i]);
    if(i < parts.length-1) html += '<mark class="hl match-token">'+escapeHtml(matches[i])+'</mark>';
  }
  el.innerHTML = html;
}
function rebuildConsoleMatches(){
  consoleMatches = Array.from(consoleEl.querySelectorAll('mark.hl'));
  consoleMatchIndex = consoleMatches.length ? 0 : -1;
  updateConsoleFindStatus();
  if(consoleMatchIndex>=0) scrollMatchIntoView(consoleMatchIndex);
}
function clearConsoleSearch(){
  // remove marcações
  Array.from(consoleEl.querySelectorAll('mark.hl')).forEach(m=>{
    const t = document.createTextNode(m.textContent);
    m.replaceWith(t);
  });
  consoleMatches = []; consoleMatchIndex = -1;
  updateConsoleFindStatus();
}
function consoleSearchKey(e){
  if(e.key === 'Enter'){
    const term = e.target.value.trim();
    // limpa e destaca novamente
    clearConsoleSearch();
    if(!term) return;
    Array.from(consoleEl.querySelectorAll('.line')).forEach(line=>highlightInElement(line, term));
    rebuildConsoleMatches();
  }
}
function scrollMatchIntoView(i){
  const m = consoleMatches[i];
  if(!m) return;
  m.scrollIntoView({behavior:'smooth', block:'center'});
  consoleMatches.forEach(x=>x.style.outline='none');
  m.style.outline = '2px solid var(--accent)';
}
function updateConsoleFindStatus(){
  if(consoleMatches.length===0){ consoleFindStatus.textContent = ''; return; }
  consoleFindStatus.textContent = (consoleMatchIndex+1) + ' / ' + consoleMatches.length;
}
function consoleFindNext(){
  if(consoleMatches.length===0) return;
  consoleMatchIndex = (consoleMatchIndex + 1) % consoleMatches.length;
  updateConsoleFindStatus(); scrollMatchIntoView(consoleMatchIndex);
}
function consoleFindPrev(){
  if(consoleMatches.length===0) return;
  consoleMatchIndex = (consoleMatchIndex - 1 + consoleMatches.length) % consoleMatches.length;
  updateConsoleFindStatus(); scrollMatchIntoView(consoleMatchIndex);
}

/* ------------------ Tema claro/escuro ------------------ */
function toggleTheme(){
  isLight = !isLight;
  document.body.classList.toggle('light', isLight);
  editor.setTheme(isLight ? THEMES.light : THEMES.dark);
  document.getElementById('btn-theme').textContent = 'Tema: ' + (isLight ? 'Claro' : 'Escuro');
}

/* ------------------ Persistência local ------------------ */
const STORAGE_KEY = 'editor_projeto_v2';

function persist(){
  try{
    const snapshot = JSON.stringify({root, openTabsIdxs: openTabs.map(f=>pathOf(root,f)), current:pathOf(root,currentFile)});
    localStorage.setItem(STORAGE_KEY, snapshot);
  }catch(e){}
}
function loadPersisted(){
  try{
    const data = localStorage.getItem(STORAGE_KEY);
    if(!data) return false;
    const parsed = JSON.parse(data);
    root = parsed.root;
    // reconstruir tabs por caminho
    openTabs = (parsed.openTabsIdxs||[]).map(p=>getNodeByPath(p)).filter(Boolean);
    currentFile = getNodeByPath(parsed.current) || openTabs[0] || null;
    return true;
  }catch(e){ return false; }
}
function pathOf(rootNode, target){
  const path=[];
  function walk(n,p){
    if(n===target){ path.push(...p); return true; }
    if(n.children){
      for(const ch of n.children){
        if(walk(ch, p.concat(ch.name))) return true;
      }
    }
    return false;
  }
  walk(rootNode, []);
  return path.join('/');
}
function getNodeByPath(path){
  if(!path) return null;
  const parts = path.split('/').filter(Boolean);
  let node = root;
  for(const name of parts){
    if(!node.children) return null;
    node = node.children.find(c=>c.name===name);
    if(!node) return null;
  }
  return node;
}

/* ------------------ Atalhos de teclado ------------------ */
document.addEventListener('keydown', (e)=>{
  // dentro do editor, prioriza atalhos do app
  const isCtrl = e.ctrlKey || e.metaKey;

  if(e.key === 'F5'){
    e.preventDefault(); executarJS(); return;
  }
  if(isCtrl && e.key.toLowerCase() === 's'){
    e.preventDefault(); salvarArquivo(); return;
  }
  if(isCtrl && e.key.toLowerCase() === 'p'){
    e.preventDefault(); preverHTML(); return;
  }
  if(isCtrl && e.key.toLowerCase() === 'w'){
    if(currentFile){ e.preventDefault(); closeTab(currentFile); }
    return;
  }
  // mudar aba: Ctrl+Tab / Ctrl+Shift+Tab
  if(isCtrl && e.key === 'Tab'){
    e.preventDefault();
    if(openTabs.length<=1) return;
    const idx = openTabs.indexOf(currentFile);
    const next = (idx + (e.shiftKey?-1:1) + openTabs.length) % openTabs.length;
    setCurrent(openTabs[next]);
    return;
  }
  // Ace find/replace
  if(isCtrl && e.key.toLowerCase()==='f'){
    e.preventDefault(); editor.execCommand('find'); return;
  }
  if(isCtrl && e.key.toLowerCase()==='h'){
    e.preventDefault(); editor.execCommand('replace'); return;
  }
});

/* ------------------ Boot ------------------ */
(function init(){
  if(!loadPersisted()){
    // sem persistência prévia -> carrega demo
    const f1 = {type:'file', name:'main.ino', content:'void setup() {\n  Serial.begin(9600);\n}\n\nvoid loop() {\n  // exemplo Arduino\n  delay(1000);\n}'};
    const f2 = {type:'file', name:'app.py', content:'# exemplo Python\nprint(\"Olá do Pyodide\")'};
    const f3 = {type:'file', name:'index.html', content:'<!doctype html>\n<html><body><h1>Preview</h1></body></html>'};
    root.children.push(f1, f2, f3);
    openTabs = [f1,f2,f3];
    currentFile = f1;
  }
  renderTree();
  renderTabs();
  loadCurrent();
})();
</script>
</body>
</html>
