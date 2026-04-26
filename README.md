[README.md](https://github.com/user-attachments/files/27107229/README.md)
# PhotoPro — Fase 1: Base do Projeto

## Estrutura do projeto

```
photopro/
├── backend/          → API Django (Python)
└── frontend/         → Interface React (Vite)
```

---

## Como rodar o projeto

### 1. Backend (Django)

```bash
# Entre na pasta do backend
cd backend

# Crie e ative o ambiente virtual
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows

# Instale as dependências
pip install -r requirements.txt

# Configure o ambiente
cp .env.example .env
# Edite o .env com seus dados se necessário

# Rode as migrations
python manage.py migrate

# Crie o superusuário admin
python manage.py createsuperuser
# (escolha username, email e senha)

# Inicie o servidor
python manage.py runserver
```

A API estará disponível em: http://localhost:8000

Painel admin Django: http://localhost:8000/admin

---

### 2. Frontend (React)

```bash
# Em outro terminal, entre na pasta do frontend
cd frontend

# Configure o ambiente
cp .env.example .env

# Instale as dependências
npm install

# Inicie o servidor de desenvolvimento
npm run dev
```

A interface estará disponível em: http://localhost:5173

---

## Rotas disponíveis

### Frontend
| Rota | Descrição |
|---|---|
| `/login` | Login de noivos e admin |
| `/register` | Cadastro de novos usuários |
| `/dashboard` | Painel dos noivos |
| `/gallery/:slug` | Galeria do evento |
| `/evento/:slug` | Fluxo do convidado (via link/QR) |

### API
| Método | Rota | Descrição |
|---|---|---|
| POST | `/api/auth/login/` | Login — retorna JWT |
| POST | `/api/auth/refresh/` | Renovar token |
| POST | `/api/accounts/register/` | Cadastro |
| GET | `/api/accounts/me/` | Dados do usuário logado |
| GET/POST | `/api/events/` | Listar/criar eventos |
| GET | `/api/events/:slug/public/` | Info pública do evento |
| POST | `/api/events/:slug/register/` | Convidado se cadastra |
| GET/POST | `/api/events/:slug/photos/` | Listar fotos |
| POST | `/api/events/:slug/photos/upload/:id/` | Upload de fotos |
| PATCH | `/api/events/:slug/photos/:id/favorite/` | Favoritar foto |

---

## Criando o primeiro evento (via admin Django)

1. Acesse http://localhost:8000/admin
2. Faça login com o superusuário criado
3. Vá em **Events → Adicionar evento**
4. Preencha: nome do casal, data, slug (ex: `ana-e-rafael`)
5. Vincule o usuário dos noivos ao evento
6. Salve

O link do convidado será: `http://localhost:5173/evento/ana-e-rafael`

---

## O que foi entregue na Fase 1

- Autenticação JWT completa (login, refresh, logout)
- Sistema de roles: admin, couple, guest
- Models: Event, GuestRegistration, Photo
- API REST com todas as rotas
- Frontend com todas as telas do convidado (3 etapas)
- Galeria dos noivos com favoritos
- Dashboard dos noivos
- CSS global com identidade visual do PhotoPro

## Próximas fases

- **Fase 2** — Melhorias no upload (preview, progresso por arquivo)
- **Fase 3** — Download em lote (ZIP), filtros avançados na galeria
- **Fase 4** — Painel admin completo com criação de eventos e geração de QR Code
