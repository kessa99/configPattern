
### 2. NestJS Template (TypeScript) – 100 % identique en structure

Repo name suggéré : `nestjs-clean-architecture-template`

```bash
src/
├── app/
│   ├── config/
│   │   ├── database.config.ts
│   │   ├── jwt.config.ts
│   │   ├── mail.config.ts
│   │   ├── app.config.ts           # ConfigModule + ValidationSchema
│   │   └── index.ts
│   │
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user.entity.ts
│   │   │   └── base.entity.ts
│   │   ├── dtos/
│   │   │   └── user.dto.ts
│   │   └── repositories-interface/
│   │       ├── user.repository.ts      # pure interface
│   │       └── base.repository.ts
│   │
│   ├── application/
│   │   ├── controllers/
│   │   │   ├── user.controller.ts
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
│   │   │   ├── user.repository.impl.ts   # implements UserRepository
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
│   └── main.ts                         # bootstrap()
│
├── test/ ...
├── prisma/ ou typeorm/
├── .env
├── package.json
└── README.md
```

```bash
mkdir -p nestjs-clean-template/src/app/{config/{database,jwt,mail,app},domain/{entities,dtos,repositories-interface},application/{controllers,services/{user/dto,auth}},infrastructure/{repositories,mappers,security,middlewares},test/{unit/{application/services,domain},integration,e2e}}

# src/app
touch nestjs-clean-template/src/app/main.ts

# config
touch nestjs-clean-template/src/app/config/{database,jwt,mail,app}.config.ts

# domain
touch nestjs-clean-template/src/app/domain/entities/{base,user}.entity.ts
touch nestjs-clean-template/src/app/domain/dtos/user.dto.ts
touch nestjs-clean-template/src/app/domain/repositories-interface/{base,user}.repository.ts

# application
touch nestjs-clean-template/src/app/application/controllers/{user,auth,health}.controller.ts
touch nestjs-clean-template/src/app/application/services/user/user.service.ts
touch nestjs-clean-template/src/app/application/services/user/create-user.use-case.ts
touch nestjs-clean-template/src/app/application/services/user/dto/{create-user,update-user}.dto.ts
touch nestjs-clean-template/src/app/application/services/auth/auth.service.ts

# infrastructure
touch nestjs-clean-template/src/app/infrastructure/repositories/user.repository.impl.ts
touch nestjs-clean-template/src/app/infrastructure/mappers/user.mapper.ts
touch nestjs-clean-template/src/app/infrastructure/security/{jwt.strategy,password-hasher}.ts
touch nestjs-clean-template/src/app/infrastructure/mail.service.ts

# root
touch nestjs-clean-template/{.env,.env.example,tsconfig.json,package.json,nest-cli.json,README.md}

echo "NestJS Clean Architecture Template créé !"
```