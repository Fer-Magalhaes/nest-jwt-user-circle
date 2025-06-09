<p align="center">
  <a href="https://nestjs.com/" target="_blank">
    <img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" />
  </a>
</p>

<h1 align="center">NestJS JWT Authentication Example</h1>

[![NPM Version](https://img.shields.io/npm/v/@nestjs/core.svg)](https://www.npmjs.com/package/@nestjs/core)  
[![Package License](https://img.shields.io/npm/l/@nestjs/core.svg)](https://github.com/nest-jwt-user-circle/LICENSE)  
[![NestJS CI](https://img.shields.io/circleci/build/github/your-repo.svg)](https://circleci.com/gh/nest-jwt-user-circle)  

---

## 📖 Descrição

Este é um starter project em **NestJS** demonstrando um fluxo completo de autenticação e autorização com:

- **Registro de usuário** (signup)
- **Login** (signin) com geração de **Access Token** e **Refresh Token**
- **Refresh** do Access Token usando Refresh Token
- Proteção de rotas via **Guards** (`jwt-auth.guard.ts`, `jwt-refresh.guard.ts`, `roles.guard.ts`)
- Exemplo de **Roles** (decorator `@Roles(...)`) para autorização
- Estrutura modular (`AuthModule`, `AppModule`)

---

## 🚀 Recursos

- `POST /auth/register` — Cria um novo usuário  
- `POST /auth/login` — Autentica usuário e retorna `{ accessToken, refreshToken }`  
- `POST /auth/refresh` — Gera um novo `accessToken` (envia `{ refreshToken }` no body)  
- Rotas de exemplo em `AppController` protegidas por `JwtAuthGuard` ou `@Roles(...)`

---

## ⚙️ Pré-requisitos

- **Node.js** v16+  
- **npm** ou **yarn**  
- (Opcional) **Docker** se você preferir rodar banco via container

---

## 🛠️ Instalação

1. Clone este repositório:
   ```bash
   git clone https://github.com/Fer-Magalhaes/nest-jwt-user-circle.git
   cd nest-jwt-user-circle
   ```

2. Instale dependências:
   ```bash
   npm install
   # ou
   yarn install
   ```

3. Crie um arquivo `.env` na raiz com as seguintes variáveis:

   ```env
   # Configuração do JWT
   JWT_ACCESS_SECRET=umaChaveSuperSecretaParaAccess
   JWT_REFRESH_SECRET=umaChaveSuperSecretaParaRefresh
   

   # Banco de dados (exemplo SQLite / MySQL / Postgres)
   DB_HOST=localhost
   DB_PORT=5432
   DB_USERNAME=seuUsuario
   DB_PASSWORD=suaSenha
   DB_NAME=seuBanco

   # (Opcional) Porta do Nest
   PORT=3000
   ```

---

## 🏃‍♂️ Rodando a Aplicação

### Modo Desenvolvimento

```bash
npm run start:dev
```
- Hot reload no diretório `src/`

### Modo Produção

```bash
npm run build
npm run start:prod
```

---

## 🗂️ Estrutura de Pastas

```
src/
├─ auth/
│  ├─ controllers/
│  │   └ auth.controller.ts
│  ├─ dto/
│  │   ├ access-token.dto.ts
│  │   ├ login.dto.ts
│  │   ├ refresh.dto.ts
│  │   ├ register.dto.ts
│  │   └ token.dto.ts
│  ├─ decorators/
│  │   └ roles.decorator.ts
│  ├─ entities/
│  │   └ user.entity.ts
│  ├─ guards/
│  │   ├ jwt-auth.guard.ts
│  │   ├ jwt-refresh.guard.ts
│  │   └ roles.guard.ts
│  ├─ strategies/
│  │   ├ jwt.strategy.ts
│  │   └ jwt-refresh.strategy.ts
│  ├─ auth.module.ts
│  └─ auth.service.ts
├─ app.controller.ts
├─ app.service.ts
├─ app.module.ts
└─ main.ts
```

---

## 📝 Exemplos de Requisições

### 1. Registro

```bash
curl -X POST http://localhost:3000/auth/register   -H "Content-Type: application/json"   -d '{"username":"joao","password":"senha123","role":"user"}'
```

### 2. Login

```bash
curl -X POST http://localhost:3000/auth/login   -H "Content-Type: application/json"   -d '{"username":"joao","password":"senha123"}'
```

Resposta:

```json
{
  "accessToken": "eyJhbGci... (JWT)",
  "refreshToken": "dGhpcyBpcyBhIHJlZnJlc2g="
}
```

### 3. Refresh Token

```bash
curl -X POST http://localhost:3000/auth/refresh   -H "Content-Type: application/json"   -d '{"refreshToken":"dGhpcyBpcyBhIHJlZnJlc2g="}'
```

Resposta:

```json
{
  "accessToken": "novo.jwt.token.aqui"
}
```

---

## 🤝 Contribuições

1. Fork este projeto  
2. Crie uma branch com sua feature (`git checkout -b feature/fooBar`)  
3. Commit suas mudanças (`git commit -m 'feat: algo incrível'`)  
4. Push para a branch (`git push origin feature/fooBar`)  
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 📬 Contato

- **Autor:** Seu Nome  
- **Website:** https://seusite.com  
- **Twitter:** [@seu_twitter](https://twitter.com/seu_twitter)  
