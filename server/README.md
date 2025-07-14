# NLW Agents

Projeto desenvolvido durante o evento **NLW** da Rocketseat.

## Descrição

API inteligente para gerenciamento de salas (rooms) com funcionalidades de IA. Permite transcrição automática de áudio, geração de respostas contextuais e busca semântica usando Gemini AI, PostgreSQL com pgvector, Fastify e Drizzle ORM.

---

## Tecnologias e Bibliotecas

- **Node.js** (TypeScript)
- **Fastify**: Framework web para Node.js
- **Zod**: Validação de esquemas e variáveis de ambiente
- **Drizzle ORM**: ORM para banco de dados relacional
- **PostgreSQL**: Banco de dados relacional
- **pgvector**: Extensão para busca vetorial e semântica
- **Biome**: Linter e formatter unificado (substitui ESLint + Prettier)
- **Gemini AI**: API para transcrição de áudio e geração de respostas
- **drizzle-kit**: Migrations e geração de schema
- **docker-compose**: Facilita o setup do banco de dados em ambiente local

---

## Padrões de Projeto e Arquitetura

- **Validação de ambiente**: Utiliza Zod para garantir variáveis obrigatórias.
- **Separação de responsabilidades**: Rotas, conexões e schemas organizados em pastas distintas.
- **Migrations versionadas**: Gerenciadas pelo Drizzle ORM.
- **Type-safe**: Uso de TypeScript e tipagem nas rotas e banco.
- **Qualidade de código**: Biome garante formatação consistente e identifica problemas de qualidade.
- **Inteligência Artificial**: Integração com Gemini AI para transcrição de áudio e geração de respostas contextuais.
- **Busca Semântica**: Uso de embeddings vetoriais com pgvector para busca inteligente de conteúdo.
- **Banco Vetorial**: PostgreSQL com pgvector para operações de similaridade e busca por proximidade.

---

## Setup e Configuração

### 1. Clone o repositório

```bash
git clone https://github.com/felipecorerato/ask-me-anything-ai-agent.git
cd ask-me-anything-ai-agent/server
```

### 2. Configure a versão do Node.js

Este projeto usa Node.js v22.13.0. Se você usa o **nvm**, pode usar:

```bash
nvm use
```

### 3. Instale as dependências

```bash
npm install
```

### 4. Configure as variáveis de ambiente

Copie o arquivo `.env.example` para `.env`:

```bash
cp .env.example .env
```

Edite o arquivo `.env` conforme necessário para seu ambiente.

> **Importante**: A chave do Gemini AI é **obrigatória** para o funcionamento da aplicação. Obtenha sua chave em [Google AI Studio](https://ai.google.dev/).

> **Dica**: Para mais detalhes sobre o Gemini AI, consulte a seção [Gemini AI - Inteligência Artificial](#gemini-ai---inteligência-artificial).

### 5. Suba o banco de dados com Docker

```bash
docker-compose up -d
```

> **Nota**: O banco utiliza PostgreSQL com pgvector para busca semântica. Veja mais detalhes na seção [PostgreSQL com pgvector - Banco de Dados](#postgresql-com-pgvector---banco-de-dados).

### 6. Configure o banco de dados

Execute os comandos do Drizzle ORM na ordem:

**6.1. Gere as migrations:**
```bash
npm run db:generate
```

**6.2. Execute as migrations:**
```bash
npm run db:migrate
```

**6.3. Popule o banco com dados de exemplo (opcional):**
```bash
npm run db:seed
```

> **Dica**: Para mais detalhes sobre os comandos do Drizzle, consulte a seção [Drizzle ORM](#drizzle-orm).

> **Visualizar dados**: Use `npm run db:studio` para abrir o Drizzle Studio e visualizar os dados do banco.

### 7. Inicie o servidor

```bash
npm run dev
```

> **Formatação**: O código é formatado automaticamente com Biome. Veja mais detalhes na seção [Biome - Linter e Formatter](#biome---linter-e-formatter).

---

## Drizzle ORM

Este projeto utiliza o **Drizzle ORM** como ORM principal para interação com o banco de dados PostgreSQL.

### Estrutura do Banco

O schema do banco está organizado em:
- **Rooms**: Salas onde são feitas as perguntas
- **Questions**: Perguntas feitas nas salas com suas respectivas respostas
- **Audio Chunks**: Transcrições de áudio com embeddings vetoriais (pgvector) para busca semântica

> **Nota**: A tabela `audio_chunks` utiliza o tipo `vector(768)` da pgvector para armazenar embeddings. Veja mais detalhes na seção [PostgreSQL com pgvector](#postgresql-com-pgvector---banco-de-dados).

### Comandos Úteis

**Gerar migrations:**
```bash
npm run db:generate
```
> Analisa o schema e gera os arquivos de migration necessários.

**Executar migrations:**
```bash
npm run db:migrate
```
> Aplica as migrations pendentes no banco de dados.

**Visualizar o banco (Drizzle Studio):**
```bash
npm run db:studio
```
> Abre o Drizzle Studio em `http://localhost:4983` ou `https://local.drizzle.studio/` para visualizar e editar dados.

**Popular com dados de exemplo:**
```bash
npm run db:seed
```
> Reseta e popula o banco com dados de exemplo para desenvolvimento.

### Drizzle Studio

O Drizzle Studio é uma interface web para visualizar e editar dados do banco de dados. Para usar:

1. Execute `npm run db:studio`
2. Acesse `http://localhost:4983` ou `https://local.drizzle.studio/` no seu navegador
3. Visualize tabelas, dados e execute queries diretamente na interface

> **Dica**: Ideal para desenvolvimento e debugging, permitindo visualizar os dados de forma intuitiva.

---

## Biome - Linter e Formatter

O projeto utiliza **Biome** como linter e formatter unificado, substituindo ESLint e Prettier. Biome oferece alta performance e configuração simplificada.

### Configuração

O Biome está configurado para usar o preset **Ultracite** que inclui regras recomendadas para TypeScript e JavaScript moderno.

Configuração no `biome.jsonc`:
```json
{
  "$schema": "https://biomejs.dev/schemas/2.0.6/schema.json",
  "extends": ["ultracite"],
  "javascript": {
    "formatter": {
      "semicolons": "asNeeded"
    }
  }
}
```

### Integração com VSCode

O projeto está configurado para usar o Biome automaticamente no VSCode:

- **Formatação automática**: Salvar (`Ctrl+S`) formata o código
- **Correções automáticas**: Aplica correções de lint automaticamente
- **Organização de imports**: Ordena imports ao salvar

> **Dica**: Para melhor experiência, instale a extensão **Biome** no VSCode.

---

## Gemini AI - Inteligência Artificial

O projeto utiliza o **Gemini AI** da Google para funcionalidades de inteligência artificial, incluindo transcrição de áudio, geração de embeddings e respostas inteligentes.

### Funcionalidades Implementadas

O Gemini AI é usado em três principais funcionalidades:

#### 1. **Transcrição de Áudio**
- **Modelo**: `gemini-2.5-flash`
- **Função**: Converte arquivos de áudio em texto em português do Brasil
- **Uso**: Transcrição automática de áudios enviados para as salas

```typescript
// Exemplo de uso
const transcription = await transcribeAudio(audioAsBase64, mimeType)
```

#### 2. **Geração de Embeddings**
- **Modelo**: `text-embedding-004`
- **Função**: Gera vetores de 768 dimensões para busca semântica
- **Uso**: Permite encontrar conteúdos similares através de busca vetorial

```typescript
// Exemplo de uso
const embeddings = await generateEmbeddings(text)
```

#### 3. **Geração de Respostas Inteligentes**
- **Modelo**: `gemini-2.5-flash`
- **Função**: Gera respostas baseadas no contexto das transcrições
- **Uso**: Responde perguntas usando o conteúdo transcrito como contexto

```typescript
// Exemplo de uso
const answer = await generateAnswer(question, transcriptions)
```

### Fluxo de Trabalho

1. **Upload de Áudio**: Áudio é enviado para `/rooms/:roomId/audio`
2. **Transcrição**: Gemini converte o áudio em texto
3. **Embeddings**: Texto é convertido em vetores para busca semântica
4. **Armazenamento**: Transcrição e embeddings são salvos no banco
5. **Pergunta**: Usuário faz uma pergunta via `/rooms/:roomId/questions`
6. **Busca Semântica**: Sistema busca conteúdos similares usando embeddings
7. **Resposta**: Gemini gera resposta baseada no contexto encontrado

### Configuração

Para usar o Gemini AI, você precisa:

1. **Obter uma chave de API**:
   - Acesse [Google AI Studio](https://ai.google.dev/)
   - Crie uma nova chave de API
   - Configure no arquivo `.env`:

```env
GEMINI_API_KEY=sua-chave-aqui
```

2. **Modelos utilizados**:
   - `gemini-2.5-flash`: Transcrição e geração de texto
   - `text-embedding-004`: Geração de embeddings (768 dimensões)

### Características Importantes

- **Idioma**: Otimizado para português do Brasil
- **Contexto**: Respostas baseadas apenas no conteúdo transcrito
- **Busca**: Usa similaridade coseno com threshold de 0.7
- **Limite**: Considera até 10 chunks mais relevantes por pergunta
- **Fallback**: Responde "não possui informações suficientes" quando não há contexto

### Exemplo de Prompt

O sistema usa prompts estruturados para garantir respostas de qualidade:

```text
Com base no texto fornecido abaixo como contexto, responda a pergunta 
de forma clara e precisa em português do Brasil.

INSTRUÇÕES:
- Use apenas informações contidas no contexto enviado
- Se a resposta não for encontrada, diga que não possui informações suficientes
- Seja objetivo e mantenha tom educativo
- Cite trechos relevantes usando "conteúdo da aula"
```

> **Importante**: O Gemini AI é essencial para o funcionamento da aplicação. Sem a chave de API configurada, as funcionalidades de transcrição e geração de respostas não funcionarão.

---

## PostgreSQL com pgvector - Banco de Dados

O projeto utiliza **PostgreSQL** como banco de dados principal, com a extensão **pgvector** para suporte a busca vetorial e semântica.

### Imagem Docker

**Imagem utilizada**: `pgvector/pgvector:pg17`

Esta imagem especializada contém:
- **PostgreSQL 17**: Versão mais recente do banco de dados
- **Extensão pgvector**: Suporte nativo para operações com vetores
- **Otimizações**: Configurada para trabalhar com embeddings e busca semântica

### Configuração do Container

```yaml
services:
  nlw-agents-pg:
    image: pgvector/pgvector:pg17
    environment:
      POSTGRES_PASSWORD: docker
      POSTGRES_USER: docker
      POSTGRES_DB: agents
    ports:
      - "5433:5432"
    volumes:
      - ./docker/setup.sql:/docker-entrypoint-initdb.d/setup.sql
```

### Extensão pgvector

A extensão **pgvector** é habilitada automaticamente durante a inicialização:

```sql
CREATE EXTENSION IF NOT EXISTS vector;
```

#### Funcionalidades da pgvector:
- **Tipos de dados**: Suporte ao tipo `vector(n)` para armazenar embeddings
- **Operadores**: Similaridade coseno (`<=>`) e distância L2 (`<->`)
- **Índices**: Índices especializados para busca vetorial eficiente
- **Dimensões**: Suporte a até 16,000 dimensões por vetor

### Estrutura do Banco de Dados

O banco está organizado em três tabelas principais:

#### 1. **Rooms (Salas)**
```sql
CREATE TABLE rooms (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name TEXT NOT NULL,
    description TEXT,
    created_at TIMESTAMP DEFAULT now()
);
```

#### 2. **Questions (Perguntas)**
```sql
CREATE TABLE questions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    room_id UUID REFERENCES rooms(id),
    question TEXT NOT NULL,
    answer TEXT,
    created_at TIMESTAMP DEFAULT now()
);
```

#### 3. **Audio Chunks (Fragmentos de Áudio)**
```sql
CREATE TABLE audio_chunks (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    room_id UUID REFERENCES rooms(id),
    transcription TEXT NOT NULL,
    embeddings vector(768) NOT NULL,  -- Vetores de 768 dimensões
    created_at TIMESTAMP DEFAULT now()
);
```

### Busca Semântica

O projeto utiliza a pgvector para implementar busca semântica:

#### 1. **Armazenamento de Embeddings**
- Transcrições de áudio são convertidas em vetores de 768 dimensões
- Embeddings são gerados pelo Gemini AI (`text-embedding-004`)
- Vetores são armazenados na coluna `embeddings` do tipo `vector(768)`

#### 2. **Busca por Similaridade**
```sql
SELECT 
    transcription,
    1 - (embeddings <=> $1::vector) AS similarity
FROM audio_chunks 
WHERE 1 - (embeddings <=> $1::vector) > 0.7
ORDER BY embeddings <=> $1::vector
LIMIT 10;
```

#### 3. **Operadores Utilizados**
- `<=>`: Distância coseno (usado para similaridade)
- `<->`: Distância L2 (euclidiana)
- `<#>`: Produto interno negativo

### Características Técnicas

- **Porta**: 5433 (mapeada do 5432 interno)
- **Volumes**: Script de inicialização em `/docker-entrypoint-initdb.d/`
- **Encoding**: UTF-8 (suporte completo ao português)
- **Timezone**: UTC (configurável via environment)

### Vantagens da pgvector

1. **Performance**: Busca vetorial otimizada diretamente no banco
2. **Escalabilidade**: Suporte a milhões de vetores com índices especializados
3. **Integração**: Funciona nativamente com PostgreSQL
4. **Flexibilidade**: Suporte a diferentes tipos de distância e similaridade
5. **Consistência**: Transações ACID para operações com vetores

> **Importante**: A pgvector é essencial para a funcionalidade de busca semântica. Sem ela, as consultas baseadas em similaridade não funcionarão.

---

## Exemplos de uso

- **Health check:**  
  `GET http://localhost:3333/health`

- **Listar salas:**  
  `GET http://localhost:3333/rooms`

## Portas utilizadas

- **PostgreSQL**: 5433 (mapeado do 5432 dentro do Docker)
- **Servidor backend**: 3333 (padrão, customizável via variável `PORT`)
- **Frontend**: 5173 (padrão do Vite, configurado no CORS do backend)
- **Drizzle Studio**: 4983 (padrão do Drizzle Kit)

> **Importante**: O CORS está configurado para aceitar apenas conexões do `http://localhost:5173`

---

## Licença

Projeto desenvolvido para fins educacionais durante o evento NLW da Rocketseat. 