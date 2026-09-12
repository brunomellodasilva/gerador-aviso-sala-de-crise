<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Guia de Causas — Rede FiBrasil</title>
<style>
  :root{
    --bg:#f4f6f5;
    --panel:#ffffff;
    --ink:#132022;
    --ink-soft:#54646a;
    --line:#dfe6e5;
    --accent:#0e7c66;
    --accent-soft:#e3f3ee;
    --warn:#b5541b;
    --warn-soft:#fbeee3;
    --radius:10px;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--bg);
    color:var(--ink);
    font-family:"Inter","Segoe UI",Roboto,system-ui,sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  header{
    background:var(--ink);
    color:#fff;
    padding:22px 20px 20px;
    position:sticky;
    top:0;
    z-index:20;
  }
  header .wrap{max-width:1080px;margin:0 auto;}
  header h1{
    margin:0 0 4px;
    font-size:1.35rem;
    font-weight:650;
    letter-spacing:-0.01em;
  }
  header p{margin:0 0 16px;color:#b9c4c2;font-size:0.92rem;}
  .search-row{display:flex;gap:10px;}
  #search{
    flex:1;
    padding:12px 14px;
    border-radius:var(--radius);
    border:none;
    font-size:1rem;
    background:#1e2f30;
    color:#fff;
  }
  #search::placeholder{color:#8ba09d;}
  #search:focus{outline:2px solid var(--accent);}
  .counter{
    align-self:center;
    font-size:0.82rem;
    color:#8ba09d;
    white-space:nowrap;
  }

  .tabs{
    display:flex;
    gap:8px;
    overflow-x:auto;
    padding:14px 20px 0;
    max-width:1080px;
    margin:0 auto;
    scrollbar-width:none;
  }
  .tabs::-webkit-scrollbar{display:none;}
  .tab{
    flex:0 0 auto;
    padding:8px 14px;
    border-radius:999px;
    border:1px solid var(--line);
    background:var(--panel);
    color:var(--ink-soft);
    font-size:0.85rem;
    cursor:pointer;
    white-space:nowrap;
  }
  .tab.active{
    background:var(--ink);
    color:#fff;
    border-color:var(--ink);
  }

  main{max-width:1080px;margin:0 auto;padding:18px 20px 60px;}

  .empty{
    text-align:center;
    color:var(--ink-soft);
    padding:60px 20px;
    font-size:0.95rem;
  }

  .grid{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax(210px,1fr));
    gap:12px;
  }
  .card{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:var(--radius);
    padding:14px;
    cursor:pointer;
    display:flex;
    flex-direction:column;
    gap:10px;
    transition:border-color .15s, transform .1s;
    text-align:left;
  }
  .card:hover{border-color:var(--accent);}
  .card:active{transform:scale(0.98);}
  .card .icon-wrap{
    width:44px;height:44px;
    border-radius:9px;
    background:var(--accent-soft);
    display:flex;align-items:center;justify-content:center;
    color:var(--accent);
  }
  .card .icon-wrap svg{width:24px;height:24px;}
  .card h3{
    margin:0;
    font-size:0.94rem;
    font-weight:600;
    line-height:1.25;
  }
  .card .cat-tag{
    font-size:0.72rem;
    color:var(--ink-soft);
  }

  /* Modal */
  .overlay{
    position:fixed;inset:0;
    background:rgba(10,15,15,0.55);
    display:none;
    align-items:flex-end;
    justify-content:center;
    z-index:50;
    padding:0;
  }
  .overlay.open{display:flex;}
  .modal{
    background:var(--panel);
    width:100%;
    max-width:560px;
    border-radius:16px 16px 0 0;
    padding:26px 24px 30px;
    max-height:85vh;
    overflow-y:auto;
    animation:slideUp .18s ease-out;
  }
  @media (min-width:640px){
    .overlay{align-items:center;padding:20px;}
    .modal{border-radius:16px;}
  }
  @keyframes slideUp{from{transform:translateY(24px);opacity:0;}to{transform:translateY(0);opacity:1;}}
  .modal-top{display:flex;justify-content:space-between;align-items:flex-start;gap:12px;}
  .modal-icon{
    width:64px;height:64px;
    border-radius:14px;
    background:var(--accent-soft);
    color:var(--accent);
    display:flex;align-items:center;justify-content:center;
    flex-shrink:0;
  }
  .modal-icon svg{width:34px;height:34px;}
  .close-btn{
    border:none;background:var(--bg);
    width:34px;height:34px;border-radius:50%;
    font-size:1.1rem;color:var(--ink-soft);
    cursor:pointer;flex-shrink:0;
  }
  .modal h2{margin:16px 0 4px;font-size:1.2rem;}
  .modal .cat-pill{
    display:inline-block;
    font-size:0.75rem;
    color:var(--accent);
    background:var(--accent-soft);
    padding:3px 10px;
    border-radius:999px;
    margin-bottom:14px;
  }
  .modal .desc{
    font-size:0.98rem;
    line-height:1.55;
    color:var(--ink);
  }
  .modal .note{
    margin-top:16px;
    background:var(--warn-soft);
    color:var(--warn);
    border-radius:8px;
    padding:10px 12px;
    font-size:0.85rem;
    line-height:1.4;
  }

  footer{
    text-align:center;
    color:var(--ink-soft);
    font-size:0.78rem;
    padding:10px 20px 40px;
  }
</style>
</head>
<body>

<header>
  <div class="wrap">
    <h1>Guia de Causas — Rede FiBrasil</h1>
    <p>Toque em uma causa para ver a definição completa</p>
    <div class="search-row">
      <input id="search" type="text" placeholder="Buscar causa (ex: cordão, poste, splitter)..." autocomplete="off">
      <span class="counter" id="counter"></span>
    </div>
  </div>
</header>

<div class="tabs" id="tabs"></div>

<main>
  <div class="grid" id="grid"></div>
  <div class="empty" id="empty" style="display:none;">Nenhuma causa encontrada.</div>
</main>

<footer>Guia interno de apoio à classificação de TTKs — consulte o time NOC em caso de dúvida.</footer>

<div class="overlay" id="overlay">
  <div class="modal">
    <div class="modal-top">
      <div class="modal-icon" id="modal-icon"></div>
      <button class="close-btn" id="close-btn" aria-label="Fechar">✕</button>
    </div>
    <h2 id="modal-title"></h2>
    <span class="cat-pill" id="modal-cat"></span>
    <p class="desc" id="modal-desc"></p>
    <div class="note" id="modal-note" style="display:none;"></div>
  </div>
</div>

<script>
/* ---------- ícones (line-icon style, stroke=currentColor) ---------- */
const ICONS = {
  crash: `<path d="M4 17h1l1.5-4.5A2 2 0 0 1 8.4 11h7.2a2 2 0 0 1 1.9 1.5L19 17h1M4 17v2a1 1 0 0 0 1 1h1a1 1 0 0 0 1-1v-2M17 17v2a1 1 0 0 0 1 1h1a1 1 0 0 0 1-1v-2M4 17H2M20 8l-3 3M9 4l2 3M13 4l-2 3" stroke-linecap="round" stroke-linejoin="round"/><circle cx="7" cy="17" r="1.4"/><circle cx="17" cy="17" r="1.4"/>`,
  rodent: `<path d="M3 15c0-3 2.5-6 6-6 1 0 2 .3 2.8.8M11.8 9.8C13 8.6 14.7 8 16.5 8 19 8 21 10 21 12.5c0 1.6-.9 3-2.2 3.7M11.8 9.8c1.6.4 2.7 1.9 2.7 3.6 0 2.1-1.7 3.8-3.8 3.8H6c-1.7 0-3-1.3-3-3" stroke-linecap="round" stroke-linejoin="round"/><circle cx="17" cy="11" r=".6" fill="currentColor" stroke="none"/><path d="M3 15l-2 1M18.5 16l2 2" stroke-linecap="round"/>`,
  truck: `<path d="M2 8h11v8H2zM13 11h4l3 3v2h-7zM6 20a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3zM17 20a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3z" stroke-linejoin="round"/><path d="M2 3h13M2 5.5h9" stroke-linecap="round"/>`,
  excavator: `<path d="M3 20h13M6 20v-4h4v4M14 8l6-3M14 8l3 4M14 8l-2 3M9 12l5-4M9 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4z" stroke-linecap="round" stroke-linejoin="round"/>`,
  lightning: `<path d="M13 2 4 14h6l-1 8 9-12h-6l1-8z" stroke-linejoin="round" fill="none"/>`,
  fire: `<path d="M12 2c1 3-2 4-2 7a3 3 0 0 0 6 0c0-1-.5-2-1-2 1 3-1 4-1 4a5 5 0 0 1-9 3c0-4 3-5 3-9 0-2-1-3-1-3 3 0 5 2 5 4z" stroke-linejoin="round"/>`,
  kite: `<path d="M12 3 20 8l-4 12-8-3-4 3 2-9z" stroke-linejoin="round"/><path d="M12 3v17M8 17l-6 4M8 8l8 4" stroke-linecap="round"/>`,
  treeprune: `<path d="M12 3 6 11h4l-3 6h4v4M12 3l6 8h-4l3 6" stroke-linecap="round" stroke-linejoin="round" fill="none"/><path d="M17 5l3-2M18 8l3 0" stroke-linecap="round"/>`,
  treefallen: `<path d="M2 18h10M8 18l6-10 2 2-6 8M14 8l3-4M17 7l2-1M16 10l3 1" stroke-linecap="round" stroke-linejoin="round"/><circle cx="8" cy="18" r="1.4"/>`,
  pole: `<path d="M12 2v20M8 6h8M8 6l-3-2M16 6l3-2M8 10h8M8 10l-3-2M16 10l3-2" stroke-linecap="round"/>`,
  vandal: `<path d="M4 20 15 9M15 9l2-2 2 2-2 2M15 9l-3-3M8 16l3 3M6 6l3 3M4 4l4 4M20 20l-4-4" stroke-linecap="round" stroke-linejoin="round"/>`,
  cablesag: `<path d="M2 6h2M20 6h2M4 6c4 0 4 12 8 12s4-12 8-12" stroke-linecap="round" fill="none"/><circle cx="4" cy="6" r="1.5"/><circle cx="20" cy="6" r="1.5"/>`,
  breaker: `<rect x="4" y="3" width="16" height="18" rx="2"/><path d="M8 8h3v3H8zM13 8h3v3h-3zM8 13h3v3H8zM13 13h3v3h-3z" stroke-linejoin="round"/>`,
  ac: `<rect x="2" y="6" width="20" height="8" rx="1.5"/><path d="M5 17v2M9 17v3M13 17v2M17 17v3M6 10h5M6 12h8" stroke-linecap="round"/>`,
  fibercut: `<path d="M2 12h6M16 12h6M8 12l1.5-2M9.5 10l1.5 2M11 12l1.5-2M12.5 10l1.5 2M14 12l1.5-2" stroke-linecap="round"/>`,
  patchcord: `<path d="M3 12c3 0 3-6 6-6h3M12 6c3 0 3 6 6 6" stroke-linecap="round" fill="none"/><rect x="15" y="9" width="6" height="6" rx="1"/>`,
  ctobox: `<rect x="4" y="4" width="16" height="16" rx="2"/><path d="M4 9h16M9 4v5M9 14h6M9 17h6" stroke-linecap="round"/>`,
  ceobox: `<rect x="3" y="7" width="18" height="10" rx="2"/><path d="M3 12h18M7 7v10M17 7v10" stroke-linecap="round"/>`,
  connector: `<rect x="3" y="9" width="7" height="6" rx="1"/><path d="M10 12h4M14 9v6M14 10.5h5M14 13.5h5" stroke-linecap="round"/>`,
  splicer: `<rect x="3" y="5" width="18" height="13" rx="2"/><path d="M7 5v13M7 11.5h10M17 5v13" stroke-linecap="round"/><circle cx="12" cy="8" r="1"/>`,
  dgorack: `<rect x="4" y="3" width="16" height="18" rx="1.5"/><path d="M4 8h16M4 13h16M4 18h16M7 8v5M11 8v5M15 8v5" stroke-linecap="round"/>`,
  pigtail: `<path d="M4 12h6" stroke-linecap="round"/><path d="M10 12c4 0 3-6 7-6" fill="none" stroke-linecap="round"/><circle cx="18" cy="6" r="1.4"/>`,
  clamp: `<path d="M6 4v16M18 4v16M6 12h12" stroke-linecap="round"/><path d="M6 8l-2-1M6 16l-2 1M18 8l2-1M18 16l2 1" stroke-linecap="round"/>`,
  splitter: `<path d="M3 12h5M16 4l5 0M16 12l5 0M16 20l5 0M8 12l8-8M8 12l8 0M8 12l8 8" stroke-linecap="round" fill="none"/>`,
  serverrack: `<rect x="5" y="3" width="14" height="18" rx="1.5"/><path d="M8 7h.01M8 11h.01M8 15h.01M11 7h5M11 11h5M11 15h5" stroke-linecap="round"/>`,
  lockedgate: `<rect x="6" y="11" width="12" height="9" rx="1.5"/><path d="M9 11V8a3 3 0 0 1 6 0v3" fill="none" stroke-linecap="round"/><circle cx="12" cy="15" r="1.2"/>`,
  warnsign: `<path d="M12 3 22 20H2z" stroke-linejoin="round"/><path d="M12 10v4" stroke-linecap="round"/><circle cx="12" cy="17" r=".6" fill="currentColor" stroke="none"/>`,
  gear: `<circle cx="12" cy="12" r="3"/><path d="M12 3v2M12 19v2M4.2 7l1.7 1M18.1 16l1.7 1M4.2 17l1.7-1M18.1 8l1.7-1M3 12h2M19 12h2" stroke-linecap="round"/>`,
  mappin: `<path d="M12 21s7-6.5 7-12a7 7 0 1 0-14 0c0 5.5 7 12 7 12z" fill="none"/><circle cx="12" cy="9" r="2.4"/>`,
  bug: `<rect x="8" y="8" width="8" height="10" rx="4"/><path d="M12 8V5M9 5h6M5 12H3M21 12h-2M5 17l-2 2M19 17l2 2M5 9l-2-1M19 9l2-1" stroke-linecap="round"/>`,
  clipboard: `<rect x="5" y="4" width="14" height="17" rx="2"/><rect x="9" y="2" width="6" height="4" rx="1"/><path d="M9 12h6M9 16h6" stroke-linecap="round"/><path d="M9 12l-1.5 1.5" stroke-linecap="round"/>`,
  calendar: `<rect x="3" y="5" width="18" height="16" rx="2"/><path d="M3 10h18M8 3v4M16 3v4" stroke-linecap="round"/>`,
  wrench: `<path d="M14.7 6.3a4 4 0 0 0-5.4 5.4L4 17l3 3 5.3-5.3a4 4 0 0 0 5.4-5.4l-2.3 2.3-2-2z" stroke-linejoin="round" fill="none"/>`,
  handshake: `<path d="M2 12l4-4h3l3 3-2 2-3-3M22 12l-4-4h-3l-3 3 2 2 3-3M9 11l4 4-2 2-4-4M13 15l-2 2 2 2 2-2" stroke-linecap="round" stroke-linejoin="round" fill="none"/>`,
  question: `<circle cx="12" cy="12" r="10"/><path d="M9.5 9a2.5 2.5 0 0 1 4.9.8c0 1.7-2.4 2-2.4 3.7" stroke-linecap="round" fill="none"/><circle cx="12" cy="17" r=".6" fill="currentColor" stroke="none"/>`,
  info: `<circle cx="12" cy="12" r="10"/><path d="M12 11v6" stroke-linecap="round"/><circle cx="12" cy="8" r=".6" fill="currentColor" stroke="none"/>`,
  xcircle: `<circle cx="12" cy="12" r="10"/><path d="M9 9l6 6M15 9l-6 6" stroke-linecap="round"/>`,
  docq: `<path d="M6 3h9l4 4v14H6z" stroke-linejoin="round" fill="none"/><path d="M15 3v4h4" stroke-linejoin="round"/><path d="M10 14a2 2 0 1 1 2.6 1.9c-.6.2-.9.6-.9 1.1" stroke-linecap="round"/><circle cx="11.7" cy="18.5" r=".5" fill="currentColor" stroke="none"/>`,
  check: `<circle cx="12" cy="12" r="10"/><path d="M8 12.5l2.5 2.5L16 9" stroke-linecap="round" stroke-linejoin="round" fill="none"/>`,
  copy: `<rect x="9" y="9" width="12" height="12" rx="2"/><path d="M5 15V5a2 2 0 0 1 2-2h10" fill="none" stroke-linecap="round"/>`,
  box: `<path d="M3 8l9-5 9 5-9 5-9-5zM3 8v9l9 5 9-5V8M12 13v9" stroke-linejoin="round" fill="none"/>`
};

function svgIcon(key){
  return `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6">${ICONS[key]||ICONS.info}</svg>`;
}

/* ---------- categorias ---------- */
const CATS = [
  {id:"rede",   nome:"Rede física"},
  {id:"equip",  nome:"Equipamentos"},
  {id:"config", nome:"Configuração"},
  {id:"energia",nome:"Energia"},
  {id:"externo",nome:"Fatores externos"},
  {id:"tercei", nome:"Terceiros / Tenant"},
  {id:"operac", nome:"Operacional"},
  {id:"cliente",nome:"Cliente / Acesso"},
  {id:"admin",  nome:"Administrativo"}
];
const CAT_NOME = Object.fromEntries(CATS.map(c=>[c.id,c.nome]));

/* ---------- causas ---------- */
const CAUSAS = [
  {n:"Abalroamento", cat:"externo", icon:"crash", d:"Falha causada pelo abalroamento do poste."},
  {n:"Acidente", cat:"externo", icon:"crash", d:"Falha na rede FiBrasil por algum acidente. Ex: batida de carro no poste, caminhão derrubou cabo, etc."},
  {n:"AGG", cat:"equip", icon:"serverrack", d:"Falha identificada é originada pelo AGG."},
  {n:"Alívio físico", cat:"rede", icon:"dgorack", d:"Caixa lotada; é necessário alívio físico na rede."},
  {n:"Ar condicionado - baixa eficiência", cat:"energia", icon:"ac", d:"Identificado no POP aumento de temperatura causado pelo ar condicionado."},
  {n:"Ar condicionado inoperante", cat:"energia", icon:"ac", d:"Identificado no POP falha no ar condicionado, sem funcionamento."},
  {n:"Área de risco", cat:"cliente", icon:"warnsign", d:"Técnico identifica que o local é uma área de risco, impossibilitando a tratativa."},
  {n:"Ataque de animais", cat:"externo", icon:"rodent", d:"Necessidade de reparo na rede por ataque de qualquer tipo de animal."},
  {n:"Ausência de configuração", cat:"config", icon:"gear", d:"Identificada ausência de configuração no serviço do cliente. Ex: VLAN, velocidade, etc."},
  {n:"Cabo baixo", cat:"rede", icon:"cablesag", d:"Cabo da FiBrasil fora da altura padrão do local, podendo causar rompimento."},
  {n:"Caixa sem conectividade", cat:"rede", icon:"dgorack", d:"A caixa está fisicamente em campo e não está cadastrada, ou está cadastrada e não é possível fazer a manobra."},
  {n:"Carga alta", cat:"externo", icon:"truck", d:"Rompimento de fibra por um veículo transitando em vias com altura fora do permitido."},
  {n:"Casa fechada / sem acesso", cat:"cliente", icon:"lockedgate", d:"Técnico não localiza o cliente na casa/local para dar manutenção na rede FiBrasil ou caixa de condomínio."},
  {n:"Causa não listada", cat:"admin", icon:"question", d:"Algum motivo/causa não foi encontrado no catálogo de causas."},
  {n:"CBLI danificado", cat:"rede", icon:"box", d:"CBLI se encontra danificado e existe a necessidade da troca."},
  {n:"CEO danificada", cat:"rede", icon:"ceobox", d:"Identificada falha na CEO e é necessária a troca."},
  {n:"Conectividade", cat:"admin", icon:"info", d:"Categoria genérica — avaliar em conjunto. Não deve ser usada como causa final isolada."},
  {n:"Conector assinante", cat:"rede", icon:"connector", d:"Identificado que a causa está no conector do assinante."},
  {n:"Conector CTO", cat:"rede", icon:"connector", d:"Técnico identifica necessidade da troca do conector da CTO."},
  {n:"Conector drop rede", cat:"rede", icon:"connector", d:"Identificada necessidade da troca do conector drop."},
  {n:"Construção", cat:"externo", icon:"excavator", d:"Falha identificada durante ou após uma construção."},
  {n:"Cordão atenuado", cat:"rede", icon:"patchcord", d:"Causa do problema na rede, POP, prédios etc. foi cordão atenuado/dobrado."},
  {n:"Cordão danificado", cat:"rede", icon:"patchcord", d:"Identificada necessidade de troca do cordão danificado."},
  {n:"Cordão óptico atenuado", cat:"rede", icon:"patchcord", d:"Causa do problema na rede, POP, prédios etc. foi cordão atenuado/dobrado."},
  {n:"CTO atenuada", cat:"rede", icon:"ctobox", d:"Técnico identifica, através de testes, atenuação na fibra/CTO."},
  {n:"CTO danificada", cat:"rede", icon:"ctobox", d:"Identificada a necessidade de troca da CTO por falha/dano."},
  {n:"Cunha quebrada", cat:"rede", icon:"clamp", d:"O problema foi causado pela quebra de uma cunha; necessária a troca da cunha e, se preciso, do cabo."},
  {n:"Defeito splitter", cat:"rede", icon:"splitter", d:"Identificado, através de testes, que o problema está relacionado ao splitter."},
  {n:"Descarga elétrica", cat:"externo", icon:"lightning", d:"Falhas ocasionadas por descarga elétrica."},
  {n:"Disjuntor desarmado", cat:"energia", icon:"breaker", d:"A falha na rede foi causada pelo desarme do disjuntor."},
  {n:"Divergência profile", cat:"config", icon:"gear", d:"O profile configurado na porta do cliente é diferente do contratado/ordem."},
  {n:"Duplicidade de ONT na gerência", cat:"equip", icon:"serverrack", d:"O serial (SN) está configurado em 2 portas da OLT."},
  {n:"Endereço incorreto", cat:"cliente", icon:"mappin", d:"Técnico identifica que o endereço da ordem é diferente do local localizado."},
  {n:"Endereço não coberto", cat:"cliente", icon:"mappin", d:"No momento da instalação é identificado que o endereço do cliente não é coberto pela rede FiBrasil."},
  {n:"Erro construção", cat:"externo", icon:"excavator", d:"Falha identificada durante ou após uma construção."},
  {n:"Erro na aplicação", cat:"config", icon:"bug", d:"Falha em alguma aplicação sistêmica da FiBrasil. Ex: SIG, Netwin, etc."},
  {n:"Erro operação", cat:"operac", icon:"clipboard", d:"A falha origina de uma atividade/tratativa da FiBrasil, impactando demais clientes."},
  {n:"Falha configuração", cat:"config", icon:"gear", d:"Aplica-se a qualquer falha lógica nos equipamentos FiBrasil."},
  {n:"Falha de gerência do elemento de rede (OLT, AGG e BNG)", cat:"equip", icon:"serverrack", d:"O equipamento fica inacessível, porém sem impacto para o cliente."},
  {n:"Falha do servidor de gerência (AMS-Nokia, NCE-Huawei)", cat:"equip", icon:"serverrack", d:"O servidor de gerência dos equipamentos apresenta falhas."},
  {n:"Falha energia", cat:"energia", icon:"breaker", d:"Identificado que a falha foi causada por falta de energia."},
  {n:"Falha hardware", cat:"equip", icon:"serverrack", d:"A falha na rede foi causada por algum equipamento/hardware. Ex: slot, SFP, placas, etc."},
  {n:"Falha operacional", cat:"operac", icon:"clipboard", d:"A falha origina de uma atividade/tratativa da FiBrasil, impactando demais clientes."},
  {n:"Falha operadora", cat:"tercei", icon:"handshake", d:"A falha origina de outra empresa que presta serviço para a FiBrasil, parceiras."},
  {n:"Falha software", cat:"equip", icon:"serverrack", d:"Identificada falha de software em algum equipamento FiBrasil (OLT, AGG, BNG, etc.)."},
  {n:"Falha tenant", cat:"tercei", icon:"handshake", d:"A falha origina de outra empresa que atende na rede FiBrasil."},
  {n:"Fibra quebrada", cat:"rede", icon:"fibercut", d:"Identificado, por testes, que a fibra está parada/sem sinal em algum ponto da rede."},
  {n:"Fusão atenuada", cat:"rede", icon:"splicer", d:"Técnico identifica, através de testes, atenuação da fibra. Necessário anexar evidências."},
  {n:"Improcedente", cat:"admin", icon:"xcircle", d:"TTK aberto para a FiBrasil sobre uma atividade que não faz parte da FiBrasil. Ex: falha em rede móvel, tubulação obstruída, etc."},
  {n:"Incêndio", cat:"externo", icon:"fire", d:"Identificado que a falha na rede foi ocasionada por incêndio."},
  {n:"Informação insuficiente", cat:"admin", icon:"docq", d:"TTK aberto sem descrição de máscara, carimbo ou informações de prévias que permitam identificar o motivo da abertura.", note:"Obrigatório detalhar no fechamento do TTK quais informações estavam faltando."},
  {n:"Limpeza de drop", cat:"rede", icon:"connector", d:"Identificada necessidade de limpeza do conector drop."},
  {n:"Linha de pipa", cat:"externo", icon:"kite", d:"A linha da pipa danifica a rede FiBrasil."},
  {n:"Link down", cat:"equip", icon:"serverrack", d:"Falha identificada por motivo de Link Down."},
  {n:"Manobra de CTO", cat:"rede", icon:"ctobox", d:"CTO lotada ou qualquer motivo que impeça a instalação na CTO designada; necessária a troca/manobra da CTO."},
  {n:"Manobra de porta", cat:"rede", icon:"wrench", d:"Após testes, é necessária a manobra da porta na CTO."},
  {n:"Necessária ação tenant", cat:"tercei", icon:"handshake", d:"Falha ocasionada por falha do tenant; válido para caso cliente, HL4, etc."},
  {n:"Normalizado pela concessionária", cat:"energia", icon:"check", d:"Existe uma falha de energia causada pela concessionária e é restabelecida pela mesma."},
  {n:"Normalizado sem intervenção", cat:"admin", icon:"check", d:"Existem evidências no TTK da falha informada e, ao chegar no local, o sinal já está normalizado."},
  {n:"Obra terceiros", cat:"externo", icon:"excavator", d:"Um terceiro efetua uma obra que impacta a rede FiBrasil."},
  {n:"Operação terceiros", cat:"tercei", icon:"handshake", d:"A falha origina de operação de terceiro que não está relacionada a vandalismo."},
  {n:"Passante danificado", cat:"rede", icon:"dgorack", d:"O passante do DGO se encontra danificado e existe a necessidade da troca."},
  {n:"Pig tail danificado", cat:"rede", icon:"pigtail", d:"Identificada necessidade de troca do pig tail com defeito."},
  {n:"Poda árvore", cat:"externo", icon:"treeprune", d:"Identificado que o motivo da falha de sinal foi causado pela poda de árvore."},
  {n:"Porta com defeito", cat:"rede", icon:"ctobox", d:"Identificada a porta da CTO do cliente/saída com defeito."},
  {n:"Queda árvore", cat:"externo", icon:"treefallen", d:"A falha é originada de uma queda de árvore impactando a rede FiBrasil."},
  {n:"Reutilizado o drop", cat:"rede", icon:"clamp", d:"Equipe usa reserva técnica, ou não há danos no cabo."},
  {n:"Sem falha rede FiBrasil", cat:"admin", icon:"check", d:"Técnico FiBrasil não identifica falhas na rede FiBrasil que ocasionaram o TTK."},
  {n:"Spliter invertido", cat:"rede", icon:"splitter", d:"Identificada, através de testes, a inversão entre splitters."},
  {n:"Trabalhos programados", cat:"operac", icon:"calendar", d:"A falha acontece durante ou após um trabalho já programado/agendado."},
  {n:"Troca de poste", cat:"externo", icon:"pole", d:"Houve troca de poste não acompanhada, sendo necessária adequação por parte da FiBrasil."},
  {n:"TTK duplicado", cat:"admin", icon:"copy", d:"Existe um TTK já aberto para o mesmo cliente tratando da mesma falha, ou TTK massivo que afeta o cliente."},
  {n:"Vandalismo", cat:"externo", icon:"vandal", d:"Identificado qualquer vandalismo que venha a causar danos na rede."}
];

/* ---------- render ---------- */
const tabsEl = document.getElementById("tabs");
const gridEl = document.getElementById("grid");
const emptyEl = document.getElementById("empty");
const counterEl = document.getElementById("counter");
const searchEl = document.getElementById("search");
let activeCat = "all";

function buildTabs(){
  const all = [{id:"all", nome:"Todas"}, ...CATS];
  tabsEl.innerHTML = all.map(c =>
    `<button class="tab${c.id===activeCat?' active':''}" data-cat="${c.id}">${c.nome}</button>`
  ).join("");
  tabsEl.querySelectorAll(".tab").forEach(btn=>{
    btn.addEventListener("click", ()=>{
      activeCat = btn.dataset.cat;
      buildTabs();
      render();
    });
  });
}

function render(){
  const term = searchEl.value.trim().toLowerCase();
  const list = CAUSAS.filter(c=>{
    const matchCat = activeCat==="all" || c.cat===activeCat;
    const matchTerm = !term || c.n.toLowerCase().includes(term) || c.d.toLowerCase().includes(term);
    return matchCat && matchTerm;
  });

  counterEl.textContent = `${list.length} causa${list.length===1?'':'s'}`;

  if(list.length===0){
    gridEl.style.display = "none";
    emptyEl.style.display = "block";
    return;
  }
  gridEl.style.display = "grid";
  emptyEl.style.display = "none";

  gridEl.innerHTML = list.map((c,i)=>`
    <button class="card" data-idx="${CAUSAS.indexOf(c)}">
      <div class="icon-wrap">${svgIcon(c.icon)}</div>
      <div>
        <h3>${c.n}</h3>
        <div class="cat-tag">${CAT_NOME[c.cat]}</div>
      </div>
    </button>
  `).join("");

  gridEl.querySelectorAll(".card").forEach(card=>{
    card.addEventListener("click", ()=> openModal(CAUSAS[card.dataset.idx]));
  });
}

/* ---------- modal ---------- */
const overlay = document.getElementById("overlay");
function openModal(c){
  document.getElementById("modal-icon").innerHTML = svgIcon(c.icon);
  document.getElementById("modal-title").textContent = c.n;
  document.getElementById("modal-cat").textContent = CAT_NOME[c.cat];
  document.getElementById("modal-desc").textContent = c.d;
  const noteEl = document.getElementById("modal-note");
  if(c.note){ noteEl.style.display = "block"; noteEl.textContent = "⚠ " + c.note; }
  else { noteEl.style.display = "none"; }
  overlay.classList.add("open");
}
document.getElementById("close-btn").addEventListener("click", ()=> overlay.classList.remove("open"));
overlay.addEventListener("click", (e)=>{ if(e.target===overlay) overlay.classList.remove("open"); });
document.addEventListener("keydown", (e)=>{ if(e.key==="Escape") overlay.classList.remove("open"); });

searchEl.addEventListener("input", render);

buildTabs();
render();
</script>
</body>
</html>
