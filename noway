# Currículo digital – Afonso Camargo Taveira

Site de currículo/portfólio em Python + Streamlit.

## Estrutura

```
curriculo-afonso-taveira/
├── app.py
├── requirements.txt
├── Procfile                  # usado pelo Railway
├── README.md
├── .gitignore
├── .streamlit/
│   └── config.toml           # tema claro e configurações do servidor
└── assets/
    ├── foto.jpg              # foto de perfil (recorte da foto do currículo)
    └── curriculo_afonso_taveira.docx   # arquivo do botão de download
```

## Executar localmente

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

Abra http://localhost:8501.

## Deploy no Streamlit Community Cloud

1. Crie um repositório no GitHub e envie todos os arquivos (inclusive `assets/` e `.streamlit/`).
2. Acesse https://share.streamlit.io e entre com o GitHub.
3. Clique em **Create app** → **Deploy a public app from GitHub**.
4. Escolha o repositório, a branch `main` e o arquivo principal `app.py`.
5. Clique em **Deploy**.

## Deploy no Railway

1. Envie o projeto para um repositório no GitHub.
2. Em https://railway.com, crie um **New Project → Deploy from GitHub repo**.
3. O `Procfile` já define o comando de inicialização:
   `streamlit run app.py --server.port=$PORT --server.address=0.0.0.0`
4. Em **Settings → Networking**, clique em **Generate Domain**.

## Privacidade

Em `app.py`, altere `SHOW_PHONE` e `SHOW_ADDRESS` para `False` para ocultar telefone e endereço.
Lembre-se de que o arquivo `.docx` em `assets/` também contém esses dados.
