# NLW Agents

Projeto desenvolvido durante o evento **NLW** da Rocketseat.

## Descrição

API para gerenciamento de salas (rooms), utilizando Fastify, Drizzle ORM e PostgreSQL.

---

## Tecnologias e Bibliotecas

- **Node.js** (TypeScript)
- **Fastify**: Framework web para Node.js
- **Zod**: Validação de esquemas e variáveis de ambiente
- **Drizzle ORM**: ORM para banco de dados relacional
- **PostgreSQL**: Banco de dados relacional
- **drizzle-kit**: Migrations e geração de schema
- **docker-compose**: Facilita o setup do banco de dados em ambiente local
- **@biomejs/biome**: Linter e formatter

---

## Padrões de Projeto e Arquitetura

- **Validação de ambiente**: Utiliza Zod para garantir variáveis obrigatórias.
- **Separação de responsabilidades**: Rotas, conexões e schemas organizados em pastas distintas.
- **Migrations versionadas**: Gerenciadas pelo Drizzle ORM.
- **Type-safe**: Uso de TypeScript e tipagem nas rotas e banco.

---

## Setup e Configuração

### 1. Clone o repositório

```bash
git clone <repo-url>
cd nlw-agents/server
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz com:

```
DATABASE_URL=postgresql://docker:docker@localhost:5433/agents
PORT=3333
```

### 4. Suba o banco de dados com Docker

```bash
docker-compose up -d
```

### 5. Rode as migrations e popule o banco (opcional)

```bash
npm run db:seed
```

### 6. Inicie o servidor

```bash
npm run dev
```

---

## Exemplos de uso

- **Health check:**  
  `GET http://localhost:3333/health`

- **Listar salas:**  
  `GET http://localhost:3333/rooms`

---

## Licença

Projeto desenvolvido para fins educacionais durante o evento NLW da Rocketseat. 