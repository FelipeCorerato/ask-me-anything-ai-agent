# Ask Me Anything AI Agent

![Node.js](https://img.shields.io/badge/Node.js-22.13.0-green.svg)
![React](https://img.shields.io/badge/React-19-blue.svg)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8-blue.svg)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-blue.svg)
![Gemini AI](https://img.shields.io/badge/Gemini_AI-2.5_Flash-orange.svg)

Projeto desenvolvido durante o evento **NLW Agents** da Rocketseat. Um sistema inteligente de salas de perguntas e respostas que utiliza inteligência artificial para transcrever áudios e gerar respostas contextuais baseadas no conteúdo transcrito.

https://github.com/user-attachments/assets/b9d9b71d-e61e-446b-85cc-7ad007052ce8  

## 🎯 Propósito do Projeto

O **Ask Me Anything AI Agent** é uma aplicação full-stack que permite:

- **Criar salas temáticas** onde usuários podem fazer perguntas
- **Gravar e enviar áudios** que são automaticamente transcritos 
- **Fazer perguntas** e receber respostas inteligentes baseadas no conteúdo dos áudios
- **Busca semântica** através de embeddings vetoriais para encontrar informações relevantes
- **Interface moderna e responsiva** para uma experiência fluida

### Como Funciona

1. **Usuário cria uma sala** com nome e descrição
2. **Envia áudios** que são transcritos automaticamente pela IA
3. **Faz perguntas** relacionadas ao conteúdo dos áudios
4. **Sistema busca** semanticamente nos conteúdos transcritos
5. **IA gera resposta** contextual baseada nas informações encontradas

## 🏗️ Arquitetura do Sistema

O projeto está dividido em duas partes principais:

### 🔙 Backend (Server)
- **Node.js + TypeScript** com framework Fastify
- **PostgreSQL + pgvector** para armazenamento e busca vetorial
- **Gemini AI** para transcrição de áudio e geração de respostas
- **Drizzle ORM** para gerenciamento do banco de dados
- **Busca semântica** com embeddings de 768 dimensões

### 🔝 Frontend (Web)
- **React 19** com TypeScript
- **Vite** para build e desenvolvimento
- **shadcn/ui** para sistema de componentes
- **React Query** para gerenciamento de estado e cache
- **React Hook Form + Zod** para formulários e validação

## 🚀 Tecnologias Principais

### Backend
- **Fastify** - Framework web rápido e eficiente
- **Gemini AI** - Transcrição de áudio e geração de respostas
- **PostgreSQL + pgvector** - Banco de dados com suporte a vetores
- **Drizzle ORM** - ORM type-safe para TypeScript
- **Zod** - Validação de esquemas e variáveis de ambiente

### Frontend
- **React 19** - Biblioteca para interfaces de usuário
- **shadcn/ui** - Sistema de componentes baseado em Radix UI
- **Tailwind CSS** - Framework CSS utilitário
- **React Router DOM** - Gerenciamento de rotas
- **React Query** - Sincronização de dados servidor-cliente

### Ferramentas de Desenvolvimento
- **Biome** - Linter e formatador de código
- **Docker** - Containerização do banco de dados
- **TypeScript** - Tipagem estática
- **Vite** - Ferramenta de build moderna

## 📁 Estrutura do Projeto

```
ask-me-anything-ai-agent/
├── 📁 server/              # Backend (Node.js + Fastify)
│   ├── src/
│   │   ├── db/            # Configuração do banco e schemas
│   │   ├── http/          # Rotas da API
│   │   └── services/      # Integração com Gemini AI
│   ├── docker/            # Configuração do PostgreSQL
│   └── README.md          # 📖 Documentação do backend
├── 📁 web/                # Frontend (React + Vite)
│   ├── src/
│   │   ├── components/    # Componentes React
│   │   ├── pages/         # Páginas da aplicação
│   │   └── http/          # Hooks para requisições HTTP
│   └── README.md          # 📖 Documentação do frontend
└── README.md              # 📖 Este arquivo
```

## 🛠️ Setup Rápido

### Pré-requisitos
- **Node.js** 22.13.0 ou superior
- **Docker** e **Docker Compose**
- **Chave do Gemini AI** ([Google AI Studio](https://ai.google.dev/))

### 1. Clone o repositório
```bash
git clone https://github.com/felipecorerato/ask-me-anything-ai-agent.git
cd ask-me-anything-ai-agent
```

### 2. Configure o Backend
```bash
cd server
npm install
cp .env.example .env
# Configure sua chave do Gemini AI no arquivo .env
docker-compose up -d
npm run db:generate
npm run db:migrate
npm run dev
```

### 3. Configure o Frontend
```bash
cd ../web
npm install
npm run dev
```

### 4. Acesse a aplicação
- **Frontend**: http://localhost:5173
- **Backend**: http://localhost:3333
- **Banco de dados**: localhost:5433

## 📚 Documentação Detalhada

Para informações específicas sobre cada parte do projeto, consulte:

- **[📖 Documentação do Backend](./server/README.md)**
  - Configuração do banco de dados PostgreSQL + pgvector
  - Integração com Gemini AI
  - Rotas da API e endpoints
  - Migrations e schemas do banco
  - Busca semântica com embeddings

- **[📖 Documentação do Frontend](./web/README.md)**
  - Sistema de componentes shadcn/ui
  - Hooks para requisições HTTP
  - Configuração do React Query
  - Gravação de áudio
  - Interface responsiva

## 🎯 Funcionalidades Principais

### ✨ Gestão de Salas
- Criação de salas com nome e descrição
- Listagem de salas recentes
- Navegação entre salas

### 🎤 Transcrição de Áudio
- Gravação de áudio diretamente no navegador
- Upload automático para o backend
- Transcrição em tempo real usando Gemini AI
- Suporte a múltiplos formatos de áudio

### ❓ Sistema de Perguntas
- Interface intuitiva para fazer perguntas
- Geração de respostas baseadas no conteúdo transcrito
- Histórico de perguntas e respostas por sala
- Busca semântica para encontrar informações relevantes

### 🔍 Inteligência Artificial
- Transcrição automática de áudios em português
- Geração de embeddings vetoriais para busca semântica
- Respostas contextuais baseadas no conteúdo disponível
- Similaridade coseno para encontrar informações relevantes

## 🌟 Características Técnicas

- **Type-safe**: Projeto totalmente tipado com TypeScript
- **Responsivo**: Interface otimizada para desktop e mobile
- **Acessível**: Componentes seguem padrões de acessibilidade
- **Performático**: Busca vetorial otimizada no banco de dados
- **Moderno**: Uso das tecnologias mais recentes do ecossistema JavaScript

## 🔧 Desenvolvimento

O projeto utiliza **Biome** como ferramenta de linting e formatação em ambas as partes (server e web), garantindo consistência e qualidade de código.

### Comandos Úteis
```bash
# Backend
cd server
npm run db:studio    # Visualizar dados do banco
npm run db:seed      # Popular banco com dados de exemplo

# Frontend  
cd web
npm run build        # Build de produção
npm run preview      # Preview do build
```

## 📝 Licença

Projeto desenvolvido para fins educacionais durante o evento **NLW Agents** da Rocketseat.

---

⭐ **Dica**: Para uma experiência completa, certifique-se de ter configurado corretamente a chave do Gemini AI no backend, pois ela é essencial para as funcionalidades de transcrição e geração de respostas.
