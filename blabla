"""
Currículo digital – Afonso Camargo Taveira
Desenvolvido com Python + Streamlit.

Todo o conteúdo vem do currículo original (assets/curriculo_afonso_taveira.docx).
Para atualizar o site, edite apenas os dados nas seções "DADOS" logo abaixo.
"""

from __future__ import annotations

import base64
from datetime import date
from html import escape
from pathlib import Path
from urllib.parse import quote_plus

import streamlit as st
import streamlit.components.v1 as components

# ──────────────────────────────────────────────────────────────────────────────
# CONFIGURAÇÕES GERAIS
# ──────────────────────────────────────────────────────────────────────────────
BASE_DIR = Path(__file__).parent
ASSETS_DIR = BASE_DIR / "assets"
PHOTO_PATH = ASSETS_DIR / "foto.jpg"
CV_PATH = ASSETS_DIR / "curriculo_afonso_taveira.docx"
CV_FILENAME = "curriculo_afonso_taveira.docx"
CV_MIME = "application/vnd.openxmlformats-officedocument.wordprocessingml.document"

# Privacidade: coloque False para ocultar estes dados no site público.
SHOW_PHONE = True
SHOW_ADDRESS = True

st.set_page_config(
    page_title="Afonso Camargo Taveira | Currículo",
    page_icon="🏛️",
    layout="wide",
    initial_sidebar_state="auto",
)

# ──────────────────────────────────────────────────────────────────────────────
# DADOS (extraídos do currículo – não inclua nada que não conste no original)
# ──────────────────────────────────────────────────────────────────────────────
PROFILE = {
    "nome": "Afonso Camargo Taveira",
    "cargo": "Analista Legislativo",
    "orgao": "Câmara dos Deputados",
    "local": "Brasília, DF",
    "email": "afonso.taveira@camara.leg.br",
    "telefone_exibicao": "(61) 99603-2625",
    "telefone_link": "61996032625",
    "endereco": "Quadra 6, Bloco F, Edifício Mônaco, Apt. 212, Cruzeiro Novo – CEP 70655-616 – Brasília, DF",
}

ABOUT = [
    "Analista Legislativo da Câmara dos Deputados, com atuação em pesquisa sobre legislação "
    "nacional e estrangeira, na Assessoria Internacional da Presidência da Câmara dos Deputados "
    "e na elaboração e execução de projetos de treinamento e formação.",
    "Antes do serviço legislativo, atuou como Gestor Público na Agência Goiana de Esporte e Lazer "
    "(2001–2005), onde elaborou minutas de anteprojetos de lei e coordenou eventos esportivos, e "
    "como Professor de Inglês em instituições de Goiânia entre 1993 e 2000.",
    "Graduado em Ciências Econômicas (UCG, 1994), com especialização em Políticas Públicas "
    "(UFG, 2004) e mestrado em Poder Legislativo em andamento no CEFOR. Fluente em inglês, "
    "espanhol e francês, com certificações de proficiência (Cambridge C2, DELE C2 e DALF C1), "
    "e certificação CAPM® do PMI (2022).",
]

# Ordem: da mais recente para a mais antiga, conforme o currículo original.
EXPERIENCES = [
    {
        "periodo": "Janeiro 2014 –",
        "cargo": "Analista Legislativo",
        "orgao": "Câmara dos Deputados",
        "unidade": "Corpi/Cedi",
        "local": "",
        "atividades": [
            "Elaboração de pesquisas na área de legislação nacional e estrangeira, "
            "tanto para o público interno como para o público externo.",
        ],
    },
    {
        "periodo": "Novembro 2013 a Abril 2014",
        "cargo": "Analista Legislativo",
        "orgao": "Câmara dos Deputados",
        "unidade": "Assessoria Internacional da Presidência",
        "local": "",
        "atividades": [
            "Organização de missões oficiais de parlamentares.",
            "Recepção de delegações estrangeiras.",
            "Redação de correspondência oficial da Presidência da Câmara dos Deputados.",
        ],
    },
    {
        "periodo": "Janeiro 2011 – 2013",
        "cargo": "Analista Legislativo",
        "orgao": "Câmara dos Deputados",
        "unidade": "Corpi/Cedi",
        "local": "",
        "atividades": [
            "Elaboração de pesquisas na área de legislação nacional e estrangeira, "
            "tanto para o público interno como para o público externo.",
        ],
    },
    {
        "periodo": "Janeiro 2005 – 2011",
        "cargo": "Analista Legislativo",
        "orgao": "Câmara dos Deputados",
        "unidade": "CEFOR",
        "local": "",
        "atividades": [
            "Elaboração e execução de projetos de treinamento e formação.",
            "Coordenação do Programa Estágio-visita de curta duração.",
        ],
    },
    {
        "periodo": "2001 – 2005",
        "cargo": "Gestor Público",
        "orgao": "Agência Goiana de Esporte e Lazer",
        "unidade": "",
        "local": "",
        "atividades": [
            "Elaboração da minuta de anteprojetos de lei (Lei Proesporte e Lei Bolsa Esporte).",
            "Coordenação e planejamento de eventos esportivos "
            "(Campeonato Mundial de Basquete Escolar e Jogos da Juventude).",
        ],
    },
    {
        "periodo": "1995 – 2000",
        "cargo": "Professor de Inglês",
        "orgao": "Centro Cultural Brasil Estados Unidos",
        "unidade": "",
        "local": "Goiânia",
        "atividades": [],
    },
    {
        "periodo": "1993 – 1995",
        "cargo": "Professor de Inglês",
        "orgao": "Centro de Cultura Anglo Americana (CCAA)",
        "unidade": "",
        "local": "Goiânia",
        "atividades": [],
    },
    {
        "periodo": "1993 – 1994",
        "cargo": "Professor de Inglês",
        "orgao": "International House",
        "unidade": "",
        "local": "Goiânia",
        "atividades": [],
    },
]

EDUCATION = [
    {
        "titulo": "Mestrado em Poder Legislativo",
        "instituicao": "CEFOR",
        "periodo": "",
        "status": "Em andamento",
    },
    {
        "titulo": "Especialização em Políticas Públicas",
        "instituicao": "UFG",
        "periodo": "2004",
        "status": "",
    },
    {
        "titulo": "Ciências Econômicas",
        "instituicao": "Universidade Católica de Goiás (UCG)",
        "periodo": "1994",
        "status": "",
    },
]

CERTIFICATIONS = [
    {
        "titulo": "Certified Associate in Project Management (CAPM)®",
        "instituicao": "Project Management Institute (PMI)",
        "periodo": "2022",
    },
    {
        "titulo": "Processo legislativo fundamental",
        "instituicao": "CEFOR",
        "periodo": "2016",
    },
    {
        "titulo": "WebMaster Training Certificate",
        "instituicao": "Universidade da Califórnia – Santa Barbara",
        "periodo": "Março 2000",
    },
    {
        "titulo": "Advanced English for Teachers",
        "instituicao": "International House – Hastings (Reino Unido)",
        "periodo": "1994",
    },
    {
        "titulo": "ITTI – International Teacher Training Institute Certificate",
        "instituicao": "Goiânia, Brasil",
        "periodo": "",
    },
    {
        "titulo": "COTE – Certificate for Overseas Teachers of English",
        "instituicao": "Universidade de Cambridge",
        "periodo": "",
    },
]

LANGUAGES = [
    {"idioma": "Inglês", "nivel": "Fluente", "certificado": "Cambridge Proficiency Certificate – nível C2"},
    {"idioma": "Espanhol", "nivel": "Fluente", "certificado": "Certificado DELE – nível C2"},
    {"idioma": "Francês", "nivel": "Fluente", "certificado": "Certificado DALF C1 – Aliança Francesa – nível C1"},
    {"idioma": "Alemão", "nivel": "Básico", "certificado": ""},
    {"idioma": "Mandarim", "nivel": "Básico", "certificado": "Certificado HSK nível A2"},
]

SKILLS_IT = ["Excel", "Word", "Office", "BRoffice", "Internet", "HTML", "Sileg", "Legin", "Qlik"]

# Áreas extraídas diretamente das atividades descritas na experiência profissional.
SKILLS_AREAS = [
    "Pesquisa em legislação nacional e estrangeira",
    "Assessoria internacional",
    "Organização de missões oficiais",
    "Recepção de delegações estrangeiras",
    "Redação de correspondência oficial",
    "Projetos de treinamento e formação",
    "Elaboração de anteprojetos de lei",
    "Planejamento de eventos esportivos",
    "Ensino de língua inglesa",
]

# ──────────────────────────────────────────────────────────────────────────────
# ÍCONES (SVG inline – não dependem de CDN)
# ──────────────────────────────────────────────────────────────────────────────
ICONS = {
    "user": '<path d="M19 21v-2a4 4 0 0 0-4-4H9a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/>',
    "briefcase": '<rect width="20" height="14" x="2" y="7" rx="2" ry="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/>',
    "cap": '<path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/>',
    "award": '<circle cx="12" cy="8" r="6"/><path d="M15.477 12.89 17 22l-5-3-5 3 1.523-9.11"/>',
    "layers": '<path d="m12 2 10 5-10 5L2 7z"/><path d="m2 17 10 5 10-5"/><path d="m2 12 10 5 10-5"/>',
    "globe": '<circle cx="12" cy="12" r="10"/><path d="M2 12h20"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>',
    "mail": '<rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>',
    "phone": '<path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/>',
    "pin": '<path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/>',
    "home": '<path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/>',
    "calendar": '<rect width="18" height="18" x="3" y="4" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/>',
}


def icon(name: str, size: int = 18) -> str:
    return (
        f'<svg class="ico" width="{size}" height="{size}" viewBox="0 0 24 24" fill="none" '
        f'stroke="currentColor" stroke-width="1.8" stroke-linecap="round" '
        f'stroke-linejoin="round" aria-hidden="true">{ICONS[name]}</svg>'
    )


# ──────────────────────────────────────────────────────────────────────────────
# ESTILO (CSS personalizado)
# ──────────────────────────────────────────────────────────────────────────────
CSS = """
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:wght@600;700&display=swap');

:root{
  --navy:#14213d; --navy-2:#1f3560; --gold:#b08d57; --gold-soft:#f1e8d8;
  --ink:#1c2538; --muted:#5d6678; --bg:#f6f4ef; --card:#ffffff; --line:#e4e0d6;
}

html, body, [data-testid="stAppViewContainer"], .stApp{ background:var(--bg); }
html, body, [class*="st-"], .stMarkdown, button{ font-family:'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif; }

[data-testid="stHeader"]{ background:transparent; }
#MainMenu, footer{ visibility:hidden; }
.block-container{ max-width:1020px; padding:2.2rem 2rem 3rem; }

/* ─── Barra lateral ─────────────────────────────────────────────── */
section[data-testid="stSidebar"]{ background:linear-gradient(180deg, var(--navy) 0%, #0d1730 100%); border-right:0; }
section[data-testid="stSidebar"] [data-testid="stSidebarContent"]{ padding-top:.5rem; }
section[data-testid="stSidebar"] button[kind="header"],
section[data-testid="stSidebar"] [data-testid="stSidebarCollapseButton"] button{ color:#fff; }
.sb-profile{ text-align:center; padding:.6rem 0 1rem; }
.sb-photo{ width:104px; height:104px; border-radius:50%; object-fit:cover; object-position:50% 25%;
  border:3px solid var(--gold); box-shadow:0 6px 18px rgba(0,0,0,.35); }
.sb-initials{ display:flex; align-items:center; justify-content:center; margin:0 auto; background:var(--navy-2);
  color:#fff; font:700 1.8rem 'Playfair Display', serif; }
.sb-name{ color:#fff; font:600 1.15rem 'Playfair Display', serif; margin-top:.8rem; line-height:1.25; }
.sb-role{ color:#c9d3e6; font-size:.82rem; margin-top:.25rem; }
.sb-foot{ color:#8d9ab5; font-size:.72rem; text-align:center; margin-top:1.2rem; }

section[data-testid="stSidebar"] div[role="radiogroup"]{ gap:.2rem; }
section[data-testid="stSidebar"] div[role="radiogroup"] label{ width:100%; padding:.55rem .9rem; border-radius:10px;
  cursor:pointer; transition:background .15s ease; }
section[data-testid="stSidebar"] div[role="radiogroup"] label > div:first-child{ display:none; }
section[data-testid="stSidebar"] div[role="radiogroup"] label:hover{ background:rgba(255,255,255,.08); }
section[data-testid="stSidebar"] div[role="radiogroup"] label:has(input:checked){
  background:rgba(176,141,87,.22); box-shadow:inset 3px 0 0 var(--gold); }
section[data-testid="stSidebar"] div[role="radiogroup"] label p{ color:#e8ecf4; font-size:.95rem; font-weight:500; }

/* ─── Botão de download ─────────────────────────────────────────── */
[data-testid="stDownloadButton"] button{ background:var(--gold); color:#fff; border:0; border-radius:10px;
  font-weight:600; padding:.55rem 1rem; transition:transform .15s ease, box-shadow .15s ease, background .15s ease; }
[data-testid="stDownloadButton"] button:hover{ background:#9c7b49; color:#fff; transform:translateY(-1px);
  box-shadow:0 6px 16px rgba(176,141,87,.35); }
[data-testid="stDownloadButton"] button p{ color:#fff; }

/* ─── Elementos comuns ──────────────────────────────────────────── */
.ico{ flex:none; vertical-align:-3px; }
.sec-head{ display:flex; align-items:center; gap:.9rem; margin:.2rem 0 1.4rem; }
.sec-icon{ width:46px; height:46px; border-radius:12px; background:var(--navy); color:#fff;
  display:flex; align-items:center; justify-content:center; }
.sec-title{ font:700 1.9rem/1.15 'Playfair Display', serif; color:var(--navy); }
.sec-sub{ color:var(--muted); font-size:.92rem; margin-top:.15rem; }

.card{ background:var(--card); border:1px solid var(--line); border-radius:16px; padding:1.25rem 1.4rem;
  box-shadow:0 1px 2px rgba(20,33,61,.04); transition:transform .18s ease, box-shadow .18s ease; }
.card:hover{ transform:translateY(-2px); box-shadow:0 10px 26px rgba(20,33,61,.09); }
.card-featured{ border-left:4px solid var(--gold); margin-top:1.2rem; }
.eyebrow{ text-transform:uppercase; letter-spacing:.09em; font-size:.7rem; font-weight:600; color:var(--gold); margin-bottom:.35rem; }
.card-title{ font-weight:600; color:var(--navy); font-size:1.05rem; line-height:1.35; }
.card-sub{ color:var(--muted); font-size:.9rem; margin-top:.2rem; }
.card-text{ color:var(--ink); font-size:.94rem; line-height:1.6; margin-top:.6rem; }
.grid{ display:grid; grid-template-columns:repeat(auto-fit, minmax(270px, 1fr)); gap:1rem; }
.badge{ display:inline-block; font-size:.72rem; font-weight:600; padding:.22rem .6rem; border-radius:999px;
  background:var(--gold-soft); color:#7a5d2e; margin-top:.7rem; margin-right:.35rem; }
.badge-navy{ background:#e6ebf5; color:var(--navy-2); }
.chip{ display:inline-block; font-size:.86rem; padding:.4rem .85rem; margin:0 .4rem .5rem 0; border-radius:999px;
  background:#fff; border:1px solid var(--line); color:var(--ink); }
.chip-gold{ background:var(--gold-soft); border-color:#e5d6b9; color:#6b5127; }
.sub-title{ font-weight:600; color:var(--navy); margin:1.6rem 0 .8rem; font-size:1.05rem; }
.card-icon{ width:38px; height:38px; border-radius:10px; background:#e6ebf5; color:var(--navy-2);
  display:flex; align-items:center; justify-content:center; margin-bottom:.8rem; }

/* ─── Hero ──────────────────────────────────────────────────────── */
.hero{ display:grid; grid-template-columns:auto 1fr; gap:2rem; align-items:center; padding:2.2rem 2.4rem;
  border-radius:22px; color:#fff; background:linear-gradient(135deg, var(--navy) 0%, var(--navy-2) 100%);
  box-shadow:0 18px 40px rgba(20,33,61,.25); position:relative; overflow:hidden; }
.hero::after{ content:""; position:absolute; right:-80px; top:-80px; width:260px; height:260px; border-radius:50%;
  background:radial-gradient(circle, rgba(176,141,87,.35), transparent 70%); }
.hero-photo{ width:158px; height:158px; border-radius:50%; object-fit:cover; object-position:50% 25%;
  border:4px solid var(--gold); box-shadow:0 10px 26px rgba(0,0,0,.35); position:relative; z-index:1; }
.hero-initials{ display:flex; align-items:center; justify-content:center; background:var(--navy-2); color:#fff;
  font:700 3rem 'Playfair Display', serif; }
.hero-body{ position:relative; z-index:1; }
.hero-eyebrow{ text-transform:uppercase; letter-spacing:.14em; font-size:.74rem; color:#e3c895; font-weight:600; }
.hero-name{ font:700 2.5rem/1.1 'Playfair Display', serif; color:#fff; margin:.4rem 0 .5rem; }
.hero-role{ font-size:1.08rem; color:#dbe3f2; }
.hero-chips{ display:flex; flex-wrap:wrap; gap:.55rem; margin-top:1.3rem; }
div[data-testid="stMarkdownContainer"] a.hero-chip, .hero-chip{ display:inline-flex; align-items:center; gap:.45rem;
  padding:.45rem .9rem; border-radius:999px; background:rgba(255,255,255,.12); color:#fff !important;
  text-decoration:none !important; font-size:.86rem; border:1px solid rgba(255,255,255,.18); transition:background .15s ease; }
div[data-testid="stMarkdownContainer"] a.hero-chip:hover{ background:rgba(255,255,255,.22); }

.stats{ display:grid; grid-template-columns:repeat(4, 1fr); gap:1rem; margin-top:1.2rem; }
.stat{ background:var(--card); border:1px solid var(--line); border-radius:16px; padding:1rem 1.1rem; text-align:center; }
.stat-num{ font:700 1.7rem 'Playfair Display', serif; color:var(--navy); }
.stat-lbl{ font-size:.8rem; color:var(--muted); margin-top:.2rem; line-height:1.35; }

/* ─── Sobre ─────────────────────────────────────────────────────── */
.about p, .about-p{ color:var(--ink); font-size:1.02rem; line-height:1.75; margin:0 0 1rem; }

/* ─── Timeline ──────────────────────────────────────────────────── */
.timeline{ position:relative; padding-left:30px; }
.timeline::before{ content:""; position:absolute; left:8px; top:8px; bottom:8px; width:2px;
  background:linear-gradient(180deg, var(--gold), var(--line)); }
.tl-item{ position:relative; margin-bottom:1.1rem; }
.tl-dot{ position:absolute; left:-28px; top:22px; width:14px; height:14px; border-radius:50%;
  background:var(--card); border:3px solid var(--gold); box-shadow:0 0 0 4px var(--bg); }
.tl-period{ display:inline-flex; align-items:center; gap:.4rem; font-size:.78rem; font-weight:600; color:#7a5d2e;
  background:var(--gold-soft); padding:.25rem .7rem; border-radius:999px; }
.tl-title{ font-weight:600; font-size:1.1rem; color:var(--navy); margin-top:.7rem; }
.tl-org{ color:var(--muted); font-size:.92rem; margin-top:.15rem; }
.tl-list{ margin:.8rem 0 0; padding-left:1.15rem; color:var(--ink); font-size:.94rem; line-height:1.6; }
.tl-list li{ margin-bottom:.3rem; }
.tl-list li::marker{ color:var(--gold); }

/* ─── Contato ───────────────────────────────────────────────────── */
div[data-testid="stMarkdownContainer"] a.contact-link{ color:var(--navy) !important; text-decoration:none !important;
  font-weight:500; word-break:break-word; }
div[data-testid="stMarkdownContainer"] a.contact-link:hover{ color:var(--gold) !important; }

.footer{ text-align:center; color:var(--muted); font-size:.78rem; margin-top:2.6rem; padding-top:1.2rem;
  border-top:1px solid var(--line); }

/* ─── Contato tocável ───────────────────────────────────────────── */
div[data-testid="stMarkdownContainer"] a.tap{ display:block; text-decoration:none !important; color:var(--navy) !important; }
.contact-val{ font-weight:500; color:var(--navy); word-break:break-word; font-size:1rem; }
div[data-testid="stMarkdownContainer"] a.map-btn{ display:inline-flex; align-items:center; gap:.4rem; margin-top:.8rem;
  padding:.55rem 1rem; border-radius:10px; background:#e6ebf5; color:var(--navy-2) !important; text-decoration:none !important;
  font-size:.88rem; font-weight:600; min-height:44px; }

/* ─── Navegação inferior (somente celular/tablet) ───────────────── */
.st-key-mobile_nav{ display:none; }
* { -webkit-tap-highlight-color:transparent; }
.st-key-scroll_helper{ position:absolute; height:0; width:0; overflow:hidden; }
@media (hover:none){ .card:hover{ transform:none; box-shadow:0 1px 2px rgba(20,33,61,.04); } }

/* ─── Responsivo ────────────────────────────────────────────────── */
@media (max-width: 768px){
  .st-key-mobile_nav{ display:block; position:fixed; left:0; right:0; bottom:0; z-index:999990;
    background:rgba(13,23,48,.97); padding:.5rem .6rem calc(.5rem + env(safe-area-inset-bottom, 0px));
    box-shadow:0 -6px 20px rgba(0,0,0,.28); }
  .st-key-mobile_nav div[role="radiogroup"]{ flex-wrap:nowrap; overflow-x:auto; gap:.4rem; scrollbar-width:none;
    -webkit-overflow-scrolling:touch; }
  .st-key-mobile_nav div[role="radiogroup"]::-webkit-scrollbar{ display:none; }
  .st-key-mobile_nav div[role="radiogroup"] label{ flex:none; min-height:44px; padding:.55rem 1.05rem; margin:0;
    border-radius:999px; background:rgba(255,255,255,.09); align-items:center; }
  .st-key-mobile_nav div[role="radiogroup"] label > div:first-child{ display:none; }
  .st-key-mobile_nav div[role="radiogroup"] label p{ color:#e8ecf4; white-space:nowrap; font-size:.92rem; font-weight:500; }
  .st-key-mobile_nav div[role="radiogroup"] label:has(input:checked){ background:var(--gold); }
  .st-key-mobile_nav div[role="radiogroup"] label:has(input:checked) p{ color:#fff; font-weight:600; }
  .block-container{ padding-bottom:6.5rem !important; }
}
@media (max-width: 900px){
  .stats{ grid-template-columns:repeat(2, 1fr); }
}
@media (max-width: 640px){
  .block-container{ padding:1rem 1rem 2.5rem; }
  .hero{ grid-template-columns:1fr; text-align:center; padding:1.6rem 1.2rem; gap:1.2rem; justify-items:center; }
  .hero-name{ font-size:1.9rem; }
  .hero-chips{ flex-direction:column; width:100%; gap:.5rem; }
  div[data-testid="stMarkdownContainer"] a.hero-chip, .hero-chip{ justify-content:center; min-height:46px;
    font-size:.95rem; word-break:break-word; }
  .hero-photo{ width:120px; height:120px; }
  .stat-num{ font-size:1.45rem; }
  .card{ padding:1.05rem 1.1rem; }
  .card-text, .tl-list, .about-p{ font-size:1rem; }
  .chip{ font-size:.92rem; padding:.5rem .95rem; }
  [data-testid="stDownloadButton"] button{ min-height:50px; font-size:1rem; }
  .sec-title{ font-size:1.55rem; }
  .sec-icon{ width:40px; height:40px; }
  .timeline{ padding-left:26px; }
  .tl-dot{ left:-24px; }
  .grid{ grid-template-columns:1fr; }
}
"""


def render(markup: str) -> None:
    """Renderiza HTML sem que o Markdown interprete indentação como bloco de código."""
    compact = "".join(line.strip() for line in markup.splitlines())
    st.markdown(compact, unsafe_allow_html=True)


def esc(text: str) -> str:
    return escape(text, quote=True)


# ──────────────────────────────────────────────────────────────────────────────
# RECURSOS (foto e arquivo do currículo)
# ──────────────────────────────────────────────────────────────────────────────
@st.cache_data(show_spinner=False)
def photo_data_uri() -> str | None:
    if not PHOTO_PATH.exists():
        return None
    encoded = base64.b64encode(PHOTO_PATH.read_bytes()).decode()
    return f"data:image/jpeg;base64,{encoded}"


@st.cache_data(show_spinner=False)
def cv_bytes() -> bytes | None:
    return CV_PATH.read_bytes() if CV_PATH.exists() else None


def initials() -> str:
    parts = [p for p in PROFILE["nome"].split() if p[0].isupper()]
    return (parts[0][0] + parts[-1][0]).upper() if parts else "?"


def download_button(key: str) -> None:
    data = cv_bytes()
    if data is None:
        return
    st.download_button(
        label="Baixar currículo (.docx)",
        data=data,
        file_name=CV_FILENAME,
        mime=CV_MIME,
        key=key,
        use_container_width=True,
        icon=":material/download:",
    )


# ──────────────────────────────────────────────────────────────────────────────
# COMPONENTES DE INTERFACE
# ──────────────────────────────────────────────────────────────────────────────
def section_header(icon_name: str, title: str, subtitle: str = "") -> None:
    sub = f'<div class="sec-sub">{esc(subtitle)}</div>' if subtitle else ""
    render(
        f'<div class="sec-head"><div class="sec-icon">{icon(icon_name, 22)}</div>'
        f'<div><div class="sec-title">{esc(title)}</div>{sub}</div></div>'
    )


def footer() -> None:
    render(
        f'<div class="footer">© {date.today().year} {esc(PROFILE["nome"])} · '
        f"Currículo digital desenvolvido com Python e Streamlit</div>"
    )


def contact_chips() -> str:
    chips = [f'<span class="hero-chip">{icon("pin", 16)}{esc(PROFILE["local"])}</span>']
    chips.append(
        f'<a class="hero-chip" href="mailto:{esc(PROFILE["email"])}">{icon("mail", 16)}{esc(PROFILE["email"])}</a>'
    )
    if SHOW_PHONE:
        chips.append(
            f'<a class="hero-chip" href="tel:{esc(PROFILE["telefone_link"])}">'
            f'{icon("phone", 16)}{esc(PROFILE["telefone_exibicao"])}</a>'
        )
    return "".join(chips)


# ──────────────────────────────────────────────────────────────────────────────
# PÁGINAS
# ──────────────────────────────────────────────────────────────────────────────
def page_inicio() -> None:
    uri = photo_data_uri()
    if uri:
        photo = f'<img class="hero-photo" src="{uri}" alt="Foto de {esc(PROFILE["nome"])}">'
    else:
        photo = f'<div class="hero-photo hero-initials">{initials()}</div>'

    render(
        f"""
        <div class="hero">
            {photo}
            <div class="hero-body">
                <div class="hero-eyebrow">Currículo profissional</div>
                <div class="hero-name">{esc(PROFILE["nome"])}</div>
                <div class="hero-role">{esc(PROFILE["cargo"])} · {esc(PROFILE["orgao"])}</div>
                <div class="hero-chips">{contact_chips()}</div>
            </div>
        </div>
        """
    )

    fluent = sum(1 for lang in LANGUAGES if lang["nivel"].lower() == "fluente")
    stats = [
        ("1993", "Início da trajetória profissional registrada"),
        (str(len(EXPERIENCES)), "Experiências profissionais"),
        (str(fluent), "Idiomas com nível fluente"),
        ("CAPM®", "Certificação PMI, 2022"),
    ]
    render(
        '<div class="stats">'
        + "".join(
            f'<div class="stat"><div class="stat-num">{esc(num)}</div><div class="stat-lbl">{esc(lbl)}</div></div>'
            for num, lbl in stats
        )
        + "</div>"
    )

    latest = EXPERIENCES[0]
    org = f'{latest["orgao"]} · {latest["unidade"]}' if latest["unidade"] else latest["orgao"]
    render(
        f'<div class="card card-featured"><div class="eyebrow">Atuação mais recente listada</div>'
        f'<div class="card-title">{esc(latest["cargo"])}</div>'
        f'<div class="card-sub">{esc(org)} · {esc(latest["periodo"])}</div>'
        f'<div class="card-text">{esc(" ".join(latest["atividades"]))}</div></div>'
    )

    st.write("")
    download_button("download_inicio")
    footer()


def page_sobre() -> None:
    section_header("user", "Sobre mim", "Resumo da trajetória profissional e acadêmica")
    render('<div class="card about">' + "".join(f'<p class="about-p">{esc(p)}</p>' for p in ABOUT) + "</div>")
    footer()


def page_experiencia() -> None:
    section_header("briefcase", "Experiência profissional", "Linha do tempo, da posição mais recente para a mais antiga")
    items = []
    for exp in EXPERIENCES:
        org = exp["orgao"]
        if exp["unidade"]:
            org += f' · {exp["unidade"]}'
        if exp["local"]:
            org += f' — {exp["local"]}'
        bullets = ""
        if exp["atividades"]:
            bullets = '<ul class="tl-list">' + "".join(f"<li>{esc(a)}</li>" for a in exp["atividades"]) + "</ul>"
        items.append(
            f'<div class="tl-item"><span class="tl-dot"></span><div class="card">'
            f'<span class="tl-period">{icon("calendar", 14)}{esc(exp["periodo"])}</span>'
            f'<div class="tl-title">{esc(exp["cargo"])}</div>'
            f'<div class="tl-org">{esc(org)}</div>{bullets}</div></div>'
        )
    render('<div class="timeline">' + "".join(items) + "</div>")
    footer()


def page_formacao() -> None:
    section_header("cap", "Formação acadêmica", "Graduação, especialização e pós-graduação")
    cards = []
    for ed in EDUCATION:
        badges = ""
        if ed["periodo"]:
            badges += f'<span class="badge">{esc(ed["periodo"])}</span>'
        if ed["status"]:
            badges += f'<span class="badge badge-navy">{esc(ed["status"])}</span>'
        cards.append(
            f'<div class="card"><div class="card-icon">{icon("cap", 20)}</div>'
            f'<div class="card-title">{esc(ed["titulo"])}</div>'
            f'<div class="card-sub">{esc(ed["instituicao"])}</div>{badges}</div>'
        )
    render('<div class="grid">' + "".join(cards) + "</div>")
    footer()


def page_certificacoes() -> None:
    section_header("award", "Cursos e certificações", "Capacitações e certificados profissionais")
    cards = []
    for cert in CERTIFICATIONS:
        badge = f'<span class="badge">{esc(cert["periodo"])}</span>' if cert["periodo"] else ""
        cards.append(
            f'<div class="card"><div class="card-icon">{icon("award", 20)}</div>'
            f'<div class="card-title">{esc(cert["titulo"])}</div>'
            f'<div class="card-sub">{esc(cert["instituicao"])}</div>{badge}</div>'
        )
    render('<div class="grid">' + "".join(cards) + "</div>")
    footer()


def page_competencias() -> None:
    section_header("layers", "Competências", "Informática e áreas de atuação descritas na experiência")
    render('<div class="sub-title">Informática</div>' + "".join(f'<span class="chip">{esc(s)}</span>' for s in SKILLS_IT))
    render(
        '<div class="sub-title">Áreas de atuação</div>'
        + "".join(f'<span class="chip chip-gold">{esc(s)}</span>' for s in SKILLS_AREAS)
    )
    footer()


def page_idiomas() -> None:
    section_header("globe", "Idiomas", "Níveis e certificados de proficiência")
    cards = []
    for lang in LANGUAGES:
        cert = f'<div class="card-sub">{esc(lang["certificado"])}</div>' if lang["certificado"] else ""
        badge_class = "badge" if lang["nivel"].lower() == "fluente" else "badge badge-navy"
        cards.append(
            f'<div class="card"><div class="card-icon">{icon("globe", 20)}</div>'
            f'<div class="card-title">{esc(lang["idioma"])}</div>{cert}'
            f'<span class="{badge_class}">{esc(lang["nivel"])}</span></div>'
        )
    render('<div class="grid">' + "".join(cards) + "</div>")
    footer()


def page_contato() -> None:
    section_header("mail", "Contato", "Toque para enviar e-mail, ligar ou abrir o endereço no mapa")
    cards = [
        f'<a class="card tap" href="mailto:{esc(PROFILE["email"])}"><div class="card-icon">{icon("mail", 20)}</div>'
        f'<div class="eyebrow">E-mail</div><div class="contact-val">{esc(PROFILE["email"])}</div></a>'
    ]
    if SHOW_PHONE:
        cards.append(
            f'<a class="card tap" href="tel:{esc(PROFILE["telefone_link"])}"><div class="card-icon">{icon("phone", 20)}</div>'
            f'<div class="eyebrow">Telefone</div><div class="contact-val">{esc(PROFILE["telefone_exibicao"])}</div></a>'
        )
    if SHOW_ADDRESS:
        maps_url = "https://www.google.com/maps/search/?api=1&query=" + quote_plus(PROFILE["endereco"])
        cards.append(
            f'<div class="card"><div class="card-icon">{icon("home", 20)}</div><div class="eyebrow">Endereço</div>'
            f'<div class="contact-val">{esc(PROFILE["endereco"])}</div>'
            f'<a class="map-btn" href="{esc(maps_url)}" target="_blank" rel="noopener">{icon("pin", 16)}Abrir no mapa</a></div>'
        )
    render('<div class="grid">' + "".join(cards) + "</div>")
    st.write("")
    download_button("download_contato")
    footer()


# ──────────────────────────────────────────────────────────────────────────────
# NAVEGAÇÃO
# ──────────────────────────────────────────────────────────────────────────────
PAGES = {
    "Início": ("inicio", page_inicio),
    "Sobre mim": ("sobre", page_sobre),
    "Experiência profissional": ("experiencia", page_experiencia),
    "Formação acadêmica": ("formacao", page_formacao),
    "Cursos e certificações": ("certificacoes", page_certificacoes),
    "Competências": ("competencias", page_competencias),
    "Idiomas": ("idiomas", page_idiomas),
    "Contato": ("contato", page_contato),
}


SHORT_LABELS = {
    "Início": "Início",
    "Sobre mim": "Sobre",
    "Experiência profissional": "Experiência",
    "Formação acadêmica": "Formação",
    "Cursos e certificações": "Cursos",
    "Competências": "Competências",
    "Idiomas": "Idiomas",
    "Contato": "Contato",
}


def init_state() -> None:
    """Define a seção inicial (aceita ?secao=experiencia) e mantém os dois menus sincronizados."""
    if "secao" not in st.session_state:
        wanted = st.query_params.get("secao")
        first = next((label for label, (slug, _) in PAGES.items() if slug == wanted), "Início")
        st.session_state["secao"] = first
        st.session_state["secao_m"] = first


def _from_sidebar() -> None:
    st.session_state["secao_m"] = st.session_state["secao"]


def _from_mobile() -> None:
    st.session_state["secao"] = st.session_state["secao_m"]


def sidebar() -> None:
    uri = photo_data_uri()
    if uri:
        avatar = f'<img class="sb-photo" src="{uri}" alt="Foto de {esc(PROFILE["nome"])}">'
    else:
        avatar = f'<div class="sb-photo sb-initials">{initials()}</div>'

    with st.sidebar:
        render(
            f'<div class="sb-profile">{avatar}<div class="sb-name">{esc(PROFILE["nome"])}</div>'
            f'<div class="sb-role">{esc(PROFILE["cargo"])}<br>{esc(PROFILE["orgao"])}</div></div>'
        )
        st.radio(
            "Navegação",
            list(PAGES.keys()),
            key="secao",
            label_visibility="collapsed",
            on_change=_from_sidebar,
        )
        st.write("")
        download_button("download_sidebar")
        render(f'<div class="sb-foot">© {date.today().year} · {esc(PROFILE["nome"])}</div>')


def mobile_nav() -> None:
    """Barra de navegação fixa na parte inferior (visível só em telas pequenas), ao alcance do polegar."""
    with st.container(key="mobile_nav"):
        st.radio(
            "Navegação rápida",
            list(PAGES.keys()),
            key="secao_m",
            horizontal=True,
            label_visibility="collapsed",
            format_func=lambda label: SHORT_LABELS[label],
            on_change=_from_mobile,
        )


def scroll_helper() -> None:
    """Ao trocar de seção: volta ao topo e centraliza o item ativo na barra inferior."""
    if st.session_state.get("_ultima_secao") == st.session_state["secao"]:
        return
    st.session_state["_ultima_secao"] = st.session_state["secao"]
    script = """
        <script>
        try {
          const d = window.parent.document;
          const main = d.querySelector('[data-testid="stMain"]') || d.querySelector('section.main');
          if (main) main.scrollTo({top: 0});
          setTimeout(() => {
            const active = d.querySelector('.st-key-mobile_nav label:has(input:checked)');
            if (active) active.scrollIntoView({inline: 'center', block: 'nearest'});
          }, 150);
        } catch (e) {}
        </script>
        """
    with st.container(key="scroll_helper"):
        if hasattr(st, "iframe"):  # Streamlit recente
            st.iframe(script, height=1)
        else:  # versões mais antigas
            components.html(script, height=0)


def main() -> None:
    render("<style>" + CSS + "</style>")
    init_state()
    sidebar()
    mobile_nav()
    slug, page = PAGES[st.session_state["secao"]]
    st.query_params["secao"] = slug
    scroll_helper()
    page()


main()
