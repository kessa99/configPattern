### 1. FastAPI Template (ta base – légèrement nettoyée et prête à l’emploi)

Repo name suggéré : `fastapi-clean-architecture-template`

```bash
src/
├── app/
│   ├── config/
│   │   ├── database_config.py      # get_db_url(), AsyncSession factory
│   │   ├── jwt_config.py           # JWT settings + generate_token, verify_token
│   │   ├── mail_config.py          # SMTP, Sendgrid, etc.
│   │   ├── app_config.py           # BaseSettings global
│   │   └── __init__.py
│   │
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user.entity.py
│   │   │   └── base.entity.py      # UUIDBase, TimestampMixin
│   │   ├── dtos/
│   │   │   └── user.dto.py
│   │   └── repositories_interface/
│   │       ├── user.repository.py  # ABC ou Protocol
│   │       └── base.repository.py
│   │
│   ├── application/
│   │   ├── controllers/
│   │   │   ├── user.controller.py
│   │   │   ├── auth.controller.py
│   │   │   └── health.controller.py
│   │   └── services/
│   │       ├── user/
│   │       │   ├── user.service.py
│   │       │   ├── create_user.use_case.py
│   │       │   └── dto/
│   │       │       ├── create_user.dto.py
│   │       │       └── update_user.dto.py
│   │       └── auth/
│   │           └── auth.service.py
│   │
│   ├── infrastructure/
│   │   ├── repositories/
│   │   │   ├── user.repository.impl.py
│   │   │   └── __init__.py
│   │   ├── mappers/
│   │   │   ├── user.mapper.py
│   │   │   └── __init__.py
│   │   ├── security/
│   │   │   ├── jwt.strategy.py
│   │   │   └── password_hasher.py
│   │   ├── middlewares/
│   │   └── mail.service.py
│   │
│   └── main.py                         # create_app() + lifespan
│
├── tests/ ...
├── alembic/
├── .env
├── pyproject.toml
└── README.md
```



#### 1. FastAPI – Template complet (copie-colle tout ça dans ton terminal)

```bash
mkdir -p fastapi-clean-template/src/app/{config/{database_config,jwt_config,mail_config,app_config},domain/{entities,dtos,repositories_interface},application/{controllers,services/{user/dto,auth}},infrastructure/{repositories,mappers,security,middlewares,utils/decorators},tests/{unit/{application/services,domain},integration,e2e},alembic}

touch fastapi-clean-template/src/app/__init__.py
touch fastapi-clean-template/src/app/main.py

# config
touch fastapi-clean-template/src/app/config/__init__.py
touch fastapi-clean-template/src/app/config/database_config.py
touch fastapi-clean-template/src/app/config/jwt_config.py
touch fastapi-clean-template/src/app/config/mail_config.py
touch fastapi-clean-template/src/app/config/app_config.py

# domain
touch fastapi-clean-template/src/app/domain/entities/base.entity.py
touch fastapi-clean-template/src/app/domain/entities/user.entity.py
touch fastapi-clean-template/src/app/domain/dtos/user.dto.py
touch fastapi-clean-template/src/app/domain/repositories_interface/base.repository.py
touch fastapi-clean-template/src/app/domain/repositories_interface/user.repository.py

# application
touch fastapi-clean-template/src/app/application/controllers/user.controller.py
touch fastapi-clean-template/src/app/application/controllers/auth.controller.py
touch fastapi-clean-template/src/app/application/controllers/health.controller.py
touch fastapi-clean-template/src/app/application/services/user/user.service.py
touch fastapi-clean-template/src/app/application/services/user/create_user.use_case.py
touch fastapi-clean-template/src/app/application/services/user/dto/create_user.dto.py
touch fastapi-clean-template/src/app/application/services/user/dto/update_user.dto.py
touch fastapi-clean-template/src/app/application/services/auth/auth.service.py

# infrastructure
touch fastapi-clean-template/src/app/infrastructure/repositories/__init__.py
touch fastapi-clean-template/src/app/infrastructure/repositories/user.repository.impl.py
touch fastapi-clean-template/src/app/infrastructure/mappers/__init__.py
touch fastapi-clean-template/src/app/infrastructure/mappers/user.mapper.py
touch fastapi-clean-template/src/app/infrastructure/security/jwt.strategy.py
touch fastapi-clean-template/src/app/infrastructure/security/password_hasher.py
touch fastapi-clean-template/src/app/infrastructure/mail.service.py

# tests
touch fastapi-clean-template/tests/__init__.py

# root files
touch fastapi-clean-template/{.env,.env.example,pyproject.toml,README.md,alembic.ini}

echo "FastAPI Clean Architecture Template créé !"
```
