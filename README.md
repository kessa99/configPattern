**TOUS les setups officiels 2025**

- NestJS + PostgreSQL / MongoDB / Vector DB  
- FastAPI + PostgreSQL / MongoDB / Vector DB  
- Django + PostgreSQL / MongoDB / Vector DB  
- Express (le tien actuel – déjà inclus pour comparaison)


```markdown
# SETUP BACKEND 2025 – CHOIX MULTIPLES (NestJS / FastAPI / Django / Express)

> Togo – Novembre 2025 – Projet Edufia Hub  
> Objectif : avoir les meilleures configurations officielles pour chaque stack + PostgreSQL / MongoDB / Vector DB (Qdrant/PGVector)

## 1. NESTJS (TypeScript) – RECOMMANDÉ POUR EDUFIA

### Création du projet (officiel 2025)
```bash
npm i -g @nestjs/cli
nest new edufia-hub-nest --package-manager npm
cd edufia-hub-nest

# Ajouter Prisma + PostgreSQL
npm install prisma @prisma/client
npm install -D prisma
npx prisma init --datasource-provider postgresql

# OU MongoDB (Mongoose)
npm install @nestjs/mongoose mongoose

# OU Vector DB : PGVector (PostgreSQL) ou Qdrant
npm install pgvector @pgvector/sql
# ou
npm install @qdrant/js-client-core
```

### Prisma + PostgreSQL (recommandé)
```env
# .env
DATABASE_URL="postgresql://user:password@localhost:5432/edufia_hub?schema=public"
```

### Prisma + MongoDB
```env
DATABASE_URL="mongodb+srv://user:password@cluster0.mongodb.net/edufia_hub?retryWrites=true&w=majority"
```

### Prisma + PGVector (recommandé pour RAG IA)
```prisma
// schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model Document {
  id        String   @id @default(cuid())
  content   String
  embedding Unsupported("vector(1536)")? // OpenAI = 1536, Cohere = 1024
}
```

### Docker Compose complet (NestJS + PostgreSQL + PGVector + Qdrant + Redis)
```yaml
# docker-compose.yml
version: '3.9'
services:
  postgres:
    image: pgvector/pgvector:pg16
    environment:
      POSTGRES_DB: edufia_hub
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    ports: ["5432:5432"]
    volumes: ["pgdata:/var/lib/postgresql/data"]

  qdrant:
    image: qdrant/qdrant:latest
    ports: ["6333:6333"]

  redis:
    image: redis:7-alpine
    ports: ["6379:6379"]

volumes:
  pgdata:
```

**Liens officiels NestJS 2025**  
- https://docs.nestjs.com  
- https://www.prisma.io/docs  
- https://docs.nestjs.com/techniques/mongodb  
- https://github.com/pgvector/pgvector  

---

## 2. FASTAPI (Python) – Ultra-rapide & moderne

### Création du projet
```bash
pip install fastapi uvicorn python-dotenv sqlalchemy asyncpg psycopg2-binary
# ou MongoDB
pip install motor pymongo
# ou Qdrant
pip install qdrant-client
```

### PostgreSQL + SQLAlchemy + async
```env
DATABASE_URL=postgresql+asyncpg://user:password@localhost:5432/edufia_hub
```

### MongoDB + Motor
```env
DATABASE_URL=mongodb+srv://user:password@cluster0.mongodb.net/edufia_hub
```

### Vector DB – Qdrant (le plus simple avec FastAPI)
```python
from qdrant_client import QdrantClient
client = QdrantClient(url="http://localhost:6333")
```

**Liens officiels FastAPI 2025**  
- https://fastapi.tiangolo.com  
- https://fastapi.tiangolo.com/tutorial/sql-databases/  
- https://github.com/tiangolo/full-stack-fastapi-template (template complet)  

---

## 3. DJANGO (Python) – Admin intégré, très solide

### Création du projet
```bash
pip install django djangorestframework psycopg2-binary
django-admin startproject edufia_hub
cd edufia_hub
python manage.py startapp api
```

### PostgreSQL (settings.py)
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'edufia_hub',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### MongoDB (avec Djongo ou MongoEngine)
```bash
pip install djongo
# puis ENGINE: 'djongo'
```

### Vector DB – PGVector dans Django
```bash
pip install django-postgres-extensions
# puis dans models.py : from postgres_extensions import VectorField
```

**Liens officiels Django 2025**  
- https://docs.djangoproject.com/en/5.1/  
- https://www.django-rest-framework.org  
- https://github.com/abeltavares/django-pgvector  

---

## 4. EXPRESS (Node.js + TypeScript) – Ton choix actuel

Tu as déjà la commande complète plus haut.  
Voici juste le résumé :

```bash
npm init -y
npm install express prisma @prisma/client socket.io argon2 jsonwebtoken helmet cors express-rate-limit
npm install -D typescript ts-node-dev jest supertest @types/express
npx prisma init --datasource-provider postgresql
```

**Liens officiels Express + Clean Architecture**  
- https://github.com/jasongaylord/node-express-clean-architecture  
- https://github.com/ThomasAubert/express-prisma-starter  



```markdown
## 5. EXPRESS PUR (JavaScript – sans TypeScript) – Pour les équipes 100 % JavaScript ou débutants

Parfois tu veux juste du JS simple, rapide, sans compilation.  
Voici la config **pro 2025** (même sécurité, même scaling, même Prisma).

### Création du projet (tout en JavaScript)
```bash
mkdir edufia-hub-express-js && cd edufia-hub-express-js
npm init -y

# Dépendances principales (tout en JS)
npm install express cors helmet dotenv jsonwebtoken bcryptjs argon2 socket.io prisma @prisma/client express-rate-limit redis @socket.io/redis-adapter

# Dépendances dev
npm install -D jest supertest nodemon prisma swagger-ui-express swagger-jsdoc

# Initialise Prisma (PostgreSQL)
npx prisma init --datasource-provider postgresql
```

### Structure de dossiers (même Clean Architecture, mais en .js)
```bash
mkdir -p src/{config,core/{entities,use-cases,repositories},infrastructure/{database/repositories,websocket/events},interfaces/{http/controllers,http/routes,websocket},middlewares,utils}
```

### Fichiers essentiels (tout en JavaScript)

#### `src/config/env.js`
```js
require('dotenv').config();

module.exports = {
  PORT: process.env.PORT || 5000,
  DATABASE_URL: process.env.DATABASE_URL,
  JWT_SECRET: process.env.JWT_SECRET || 'edufia_secret_2025_change_me',
  NODE_ENV: process.env.NODE_ENV || 'development',
  REDIS_URL: process.env.REDIS_URL
};
```

#### `src/config/database.js`
```js
const { PrismaClient } = require('@prisma/client');

const globalForPrisma = global;
const prisma = globalForPrisma.prisma || new PrismaClient();

if (process.env.NODE_ENV !== 'production') globalForPrisma.prisma = prisma;

module.exports = { prisma };
```

#### `src/app.js`
```js
const express = require('express');
const cors = require('cors');
const helmet = require('helmet');
const { applySecurity } = require('./middlewares/security');

const app = express();
applySecurity(app);

app.use(express.json({ limit: '500kb' }));
app.use(express.urlencoded({ extended: true }));

app.get('/', (req, res) => {
  res.json({ message: 'Edufia Hub API – JavaScript Edition 2025' });
});

module.exports = app;
```

#### `src/server.js`
```js
const app = require('./app');
const http = require('http');
const { initSocketIO } = require('./config/socket.io');
const { PORT } = require('./config/env');

const server = http.createServer(app);
initSocketIO(server);

server.listen(PORT, () => {
  console.log(`Edufia JS Backend lancé → http://localhost:${PORT}`);
  console.log(`WebSocket prêt`);
});
```

#### `package.json` – scripts JS
```json
"scripts": {
  "dev": "nodemon src/server.js",
  "start": "node src/server.js",
  "prisma:dev": "prisma migrate dev",
  "prisma:generate": "prisma generate",
  "test": "jest",
  "test:watch": "jest --watch"
}
```

#### `.env` (identique)
```env
PORT=5000
DATABASE_URL="postgresql://user:password@localhost:5432/edufia_hub?schema=public"
JWT_SECRET=edufia_super_secret_js_2025
NODE_ENV=development
REDIS_URL="redis://default:password@localhost:6379"
```

### Lancement
```bash
npx prisma generate
npm run dev
```

**Liens officiels Express JS (sans TS) 2025**  
- https://expressjs.com  
- https://github.com/expressjs/express  
- https://github.com/prisma/prisma-examples/tree/latest/javascript  
- https://github.com/goldbergyoni/javascript-testing-best-practices  
