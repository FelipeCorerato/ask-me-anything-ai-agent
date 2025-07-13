# NLW Agents

Este projeto foi desenvolvido durante o evento **NLW** promovido pela Rocketseat.

## Tecnologias e Bibliotecas Utilizadas

- **React 19** – Biblioteca principal para construção da interface.
- **Vite** – Ferramenta de build e desenvolvimento rápido.
- **TypeScript** – Tipagem estática para JavaScript.
- **React Router DOM** – Gerenciamento de rotas SPA.
- **@tanstack/react-query** – Gerenciamento de dados assíncronos e cache.
- **Tailwind CSS** – Utilitário para estilização rápida e responsiva.
- **@radix-ui/react-slot** – Composição avançada de componentes.
- **class-variance-authority, clsx, tailwind-merge** – Utilitários para composição e variação de classes CSS.
- **lucide-react** – Ícones em SVG para React.

## Padrões de Projeto e Arquitetura

- **Componentização**: Uso extensivo de componentes reutilizáveis.
- **Hooks**: Utilização de hooks do React e do React Query para gerenciamento de estado e efeitos colaterais.
- **Provider Pattern**: Contexto global de dados via `QueryClientProvider`.
- **Rotas**: Gerenciamento de páginas com React Router.
- **Alias de Imports**: Utilização de `@` como atalho para a pasta `src`.

## Setup e Configuração

1. **Clone o repositório:**
   ```bash
   git clone <url-do-repo>
   cd web
   ```

2. **Instale as dependências:**
   ```bash
   npm install
   ```

3. **Rode o projeto em modo desenvolvimento:**
   ```bash
   npm run dev
   ```

4. **Build para produção:**
   ```bash
   npm run build
   ```

5. **Pré-visualização do build:**
   ```bash
   npm run preview
   ```

## Observações

- O projeto utiliza **Tailwind CSS** e animações via `tw-animate-css`.
- O ponto de entrada da aplicação é o arquivo `src/main.tsx`.
- As rotas principais estão em `src/pages/`.
- O backend deve estar rodando em `http://localhost:3333` para o correto funcionamento das requisições. 