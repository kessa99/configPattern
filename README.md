

### 1. Express.js + TypeScript Template – même structure, ultra lisible

Repo name suggéré : `express-clean-architecture-template`

```bash
src/
├── app/
│   ├── config/
│   │   ├── database.config.ts
│   │   ├── jwt.config.ts
│   │   ├── mail.config.ts
│   │   ├── app.config.ts
│   │   └── index.ts
│   │
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user.entity.ts
│   │   │   └── base.entity.ts
│   │   ├── dtos/
│   │   │   └── user.dto.ts
│   │   └── repositories-interface/
│   │       ├── user.repository.ts
│   │       └── base.repository.ts
│   │
│   ├── application/
│   │   ├── controllers/
│   │   │   ├── user.controller.ts      # express Router
│   │   │   ├── auth.controller.ts
│   │   │   └── health.controller.ts
│   │   └── services/
│   │       ├── user/
│   │       │   ├── user.service.ts
│   │       │   ├── create-user.use-case.ts
│   │       │   └── dto/
│   │       │       ├── create-user.dto.ts
│   │       │       └── update-user.dto.ts
│   │       └── auth/
│   │           └── auth.service.ts
│   │
│   ├── infrastructure/
│   │   ├── repositories/
│   │   │   ├── user.repository.impl.ts
│   │   │   └── index.ts
│   │   ├── mappers/
│   │   │   ├── user.mapper.ts
│   │   │   └── index.ts
│   │   ├── security/
│   │   │   ├── jwt.strategy.ts
│   │   │   └── password-hasher.ts
│   │   ├── middlewares/
│   │   └── mail.service.ts
│   │
│   └── server.ts                       # const app = express()
│
├── tests/ ...
├── prisma/ ou migrations/
├── .env
├── package.json
└── tsconfig.json
```

```bash
mkdir -p express-clean-template/src/app/{config/{database,jwt,mail,app},domain/{entities,dtos,repositories-interface},application/{controllers,services/{user/dto,auth}},infrastructure/{repositories,mappers,security,middlewares},tests/{unit/{application/services,domain},integration,e2e}}

# src/app
touch express-clean-template/src/app/server.ts

# config
touch express-clean-template/src/app/config/{database,jwt,mail,app}.config.ts

# domain
touch express-clean-template/src/app/domain/entities/{base,user}.entity.ts
touch express-clean-template/src/app/domain/dtos/user.dto.ts
touch express-clean-template/src/app/domain/repositories-interface/{base,user}.repository.ts

# application
touch express-clean-template/src/app/application/controllers/{user,auth,health}.controller.ts
touch express-clean-template/src/app/application/services/user/user.service.ts
touch express-clean-template/src/app/application/services/user/create-user.use-case.ts
touch express-clean-template/src/app/application/services/user/dto/{create-user,update-user}.dto.ts
touch express-clean-template/src/app/application/services/auth/auth.service.ts

# infrastructure
touch express-clean-template/src/app/infrastructure/repositories/user.repository.impl.ts
touch express-clean-template/src/app/infrastructure/mappers/user.mapper.ts
touch express-clean-template/src/app/infrastructure/security/{jwt.strategy,password-hasher}.ts
touch express-clean-template/src/app/infrastructure/mail.service.ts

# root
touch express-clean-template/{.env,.env.example,tsconfig.json,package.json,README.md}

echo "Express + TS Clean Architecture Template créé !"
```