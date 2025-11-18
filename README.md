
```
express-js-clean-project/
├── src/
│   └── app/
│       ├── config/
│       │   ├── database.config.js
│       │   ├── jwt.config.js
│       │   ├── mail.config.js
│       │   ├── app.config.js
│       │   └── index.js               # (optionnel) export tout
│       │
│       ├── domain/
│       │   ├── entities/
│       │   │   ├── base.entity.js
│       │   │   ├── user.entity.js
│       │   │   └── product.entity.js      # exemples
│       │   │
│       │   ├── dtos/
│       │   │   └── user.dto.js
│       │   │
│       │   └── repositories-interface/
│       │       ├── base.repository.js
│       │       ├── user.repository.js
│       │       └── product.repository.js
│       │
│       ├── application/
│       │   ├── controllers/
│       │   │   ├── user.controller.js
│       │   │   ├── auth.controller.js
│       │   │   ├── health.controller.js
│       │   │   └── index.js               # export tous les routers
│       │   │
│       │   └── services/
│       │       ├── user/
│       │       │   ├── user.service.js
│       │       │   ├── create-user.use-case.js
│       │       │   ├── update-user.use-case.js
│       │       │   └── dto/
│       │       │       ├── create-user.dto.js
│       │       │       └── update-user.dto.js
│       │       │
│       │       └── auth/
│       │           └── auth.service.js
│       │
│       ├── infrastructure/
│       │   ├── repositories/
│       │   │   ├── user.repository.impl.js
│       │   │   └── product.repository.impl.js
│       │   │
│       │   ├── mappers/
│       │   │   └── user.mapper.js
│       │   │
│       │   ├── security/
│       │   │   ├── jwt.strategy.js
│       │   │   └── password-hasher.js
│       │   │
│       │   ├── middlewares/
│       │   │   ├── error-handler.js
│       │   │   └── auth.middleware.js
│       │   │
│       │   └── external/
│       │       └── mail.service.js
│       │
│       └── server.js                      # const app = express() + bootstrap
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── .env
├── .env.example
├── package.json
├── README.md
└── .gitignore
```

```bash
# Création du projet Express.js (JavaScript) - Clean Architecture
mkdir -p /src/app/{config/{database,jwt,mail,app},domain/{entities,dtos,repositories-interface},application/{controllers,services/{user/dto,auth}},infrastructure/{repositories,mappers,security,middlewares},tests/{unit/{application/services,domain},integration,e2e}}

# Fichiers principaux
touch /src/app/server.js

# config/
touch /src/app/config/database.config.js
touch /src/app/config/jwt.config.js
touch /src/app/config/mail.config.js
touch /src/app/config/app.config.js
touch /src/app/config/index.js

# domain/
touch /src/app/domain/entities/base.entity.js
touch /src/app/domain/entities/user.entity.js
touch /src/app/domain/dtos/user.dto.js
touch /src/app/domain/repositories-interface/base.repository.js
touch /src/app/domain/repositories-interface/user.repository.js

# application/controllers/
touch /src/app/application/controllers/user.controller.js
touch /src/app/application/controllers/auth.controller.js
touch /src/app/application/controllers/health.controller.js

# application/services/
touch /src/app/application/services/user/user.service.js
touch /src/app/application/services/user/create-user.use-case.js
touch /src/app/application/services/user/dto/create-user.dto.js
touch /src/app/application/services/user/dto/update-user.dto.js
touch /src/app/application/services/auth/auth.service.js

# infrastructure/
touch /src/app/infrastructure/repositories/user.repository.impl.js
touch /src/app/infrastructure/mappers/user.mapper.js
touch /src/app/infrastructure/security/jwt.strategy.js
touch /src/app/infrastructure/security/password-hasher.js
touch /src/app/infrastructure/mail.service.js
```