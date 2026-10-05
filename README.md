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
│   ├── config.toml           # tema claro e configurações do servidor
│   └── secrets.toml.example  # modelo opcional para envio por SMTP
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

## Celular (Android)

Em telas de até 768 px aparece uma barra de navegação fixa na parte inferior (rolável na horizontal), com alvos de toque de 44 px ou mais. E-mail e telefone abrem o app de e-mail e o discador com um toque, e o endereço abre no Google Maps. Para instalar como atalho, use no Chrome **⋮ → Adicionar à tela inicial**.

## Formulário de contato

A aba **Contato** tem um formulário (nome, e-mail, assunto e mensagem). As mensagens são enviadas para `contato@afonsotaveira.com.br`, e o botão "Responder" do e-mail já usa o endereço do visitante.

**Padrão: FormSubmit (sem senha, sem configuração)**
1. Publique o site e envie uma mensagem de teste pelo formulário.
2. O FormSubmit manda um e-mail de ativação para `contato@afonsotaveira.com.br` (veja também a caixa de Lixo Eletrônico). Clique em **Activate Form**.
3. Depois da ativação, as mensagens passam a chegar normalmente. Se a de teste não chegar, envie outra.

**Alternativa: SMTP (opcional)**
Se preferir enviar pelo seu próprio e-mail, copie `.streamlit/secrets.toml.example` para `.streamlit/secrets.toml` (local) ou cole o conteúdo em **Settings → Secrets** (Streamlit Cloud). No Railway, prefira o FormSubmit, pois lá o app não lê o arquivo de secrets. Com a seção `[smtp]` presente, o app usa SMTP automaticamente. Use uma **senha de aplicativo**, nunca a senha normal, e não envie o `secrets.toml` para o GitHub (já está no `.gitignore`).

**Proteções incluídas:** validação de e-mail, limite de tamanho, intervalo de 60 s entre envios e máximo de 3 mensagens por hora por visitante.

**Atenção:** se o repositório for público, o endereço `contato@afonsotaveira.com.br` ficará visível no código (`CONTACT_TO` em `app.py`). Use um repositório privado ou o alias aleatório que o FormSubmit oferece após a ativação (coloque-o em `formsubmit_target` nos secrets).

## Privacidade

Em `app.py`, altere `SHOW_PHONE` e `SHOW_ADDRESS` para `False` para ocultar telefone e endereço.
Lembre-se de que o arquivo `.docx` em `assets/` também contém esses dados.
