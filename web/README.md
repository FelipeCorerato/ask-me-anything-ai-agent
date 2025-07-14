# NLW Agents

Este projeto foi desenvolvido durante o evento **NLW** promovido pela Rocketseat.

## Funcionalidades

- 🏠 **Página inicial** com listagem de salas recentes
- 🆕 **Criação de salas** com nome e descrição personalizados
- ❓ **Sistema de perguntas** com respostas geradas por IA
- 🎤 **Gravação de áudio** com upload automático para o backend
- 📱 **Interface responsiva** otimizada para desktop e mobile
- ⚡ **Atualizações em tempo real** via React Query
- 🔍 **Histórico de perguntas** organizadas por sala
- 🎨 **UI moderna** com sistema de componentes shadcn/ui (Radix UI + Tailwind CSS)

## Tecnologias e Bibliotecas Utilizadas

### Core
- **React 19** – Biblioteca principal para construção da interface
- **Vite** – Ferramenta de build e desenvolvimento rápido
- **TypeScript 5.8** – Tipagem estática para JavaScript

### Roteamento e Estado
- **React Router DOM v7** – Gerenciamento de rotas SPA
- **@tanstack/react-query** – Gerenciamento de dados assíncronos e cache

### Formulários e Validação
- **React Hook Form** – Gerenciamento de formulários performático
- **Zod** – Validação de esquemas TypeScript-first
- **@hookform/resolvers** – Integração entre React Hook Form e Zod

### Estilização e UI
- **shadcn/ui** – Sistema de componentes baseado em Radix UI + Tailwind CSS
- **Tailwind CSS v4** – Framework CSS utilitário moderno
- **@tailwindcss/vite** – Plugin do Vite para Tailwind CSS
- **Radix UI** – Componentes acessíveis e sem estilo (base do shadcn/ui)
- **class-variance-authority, clsx, tailwind-merge** – Utilitários para composição de classes
- **lucide-react** – Ícones em SVG para React

### Desenvolvimento e Qualidade
- **Biome** – Linter e formatador de código ultrarrápido
- **Ultracite** – Regras de linting especializadas

## Biome - Linter e Formatador

O projeto utiliza **Biome** como ferramenta principal para linting e formatação de código. Biome é uma ferramenta ultrarrápida que substitui ESLint e Prettier, oferecendo uma experiência de desenvolvimento mais consistente e performática.

### Características do Biome

- **🚀 Performance**: Escrito em Rust, oferece velocidade excepcional
- **🔧 Configuração Zero**: Funciona imediatamente sem configuração complexa
- **📦 Tudo em Um**: Linter, formatador e importador de dependências em uma única ferramenta
- **🎯 Compatibilidade**: Suporta JavaScript, TypeScript, JSX, TSX e JSON
- **🔄 Migração Fácil**: Configuração compatível com ESLint e Prettier

### Configuração Atual

O Biome está configurado através do arquivo `biome.jsonc`:

```jsonc
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

### Características da Configuração

- **Ultracite**: Extensão que fornece regras de linting especializadas para acessibilidade e melhores práticas
- **Semicolons**: Configurado como "asNeeded" para inserir semicolons apenas quando necessário
- **Schema**: Utiliza o schema oficial do Biome para validação e autocomplete

### Comandos Disponíveis

Embora não estejam configurados como scripts no `package.json`, você pode usar os seguintes comandos:

```bash
# Verificar código (linting)
npx biome check .

# Verificar e corrigir automaticamente
npx biome check --apply .

# Formatar código
npx biome format .

# Formatar e sobrescrever arquivos
npx biome format --write .

# Verificar apenas arquivos específicos
npx biome check src/

# Verificar com informações detalhadas
npx biome check --verbose .
```

### Integração com IDEs

Para uma melhor experiência de desenvolvimento, instale a extensão do Biome no seu editor:

- **VS Code**: Instale a extensão "Biome"
- **WebStorm**: Suporte nativo via plugin
- **Vim/Neovim**: Suporte via LSP

### Regras do Ultracite

O projeto usa a configuração **Ultracite**, que inclui:

- **Regras de acessibilidade**: Garantia de que componentes sejam acessíveis
- **Melhores práticas React**: Regras específicas para desenvolvimento React
- **Otimizações de performance**: Detecção de padrões que podem impactar a performance
- **Convenções de código**: Padrões consistentes de nomenclatura e estrutura

### Benefícios no Projeto

- **Velocidade**: Análise e formatação ultrarrápida de todo o código
- **Consistência**: Formatação e regras uniformes em todo o projeto
- **Qualidade**: Detecção precoce de problemas e code smells
- **Produtividade**: Correção automática de muitos problemas
- **Acessibilidade**: Regras que garantem código acessível por padrão

### Configuração Recomendada para Scripts

Para facilitar o uso, você pode adicionar estes scripts ao `package.json`:

```json
{
  "scripts": {
    "lint": "biome check .",
    "lint:fix": "biome check --apply .",
    "format": "biome format --write .",
    "check": "biome check --verbose ."
  }
}
```

## Padrões de Projeto e Arquitetura

- **Componentização**: Uso extensivo de componentes reutilizáveis.
- **Hooks**: Utilização de hooks do React e do React Query para gerenciamento de estado e efeitos colaterais.
- **Provider Pattern**: Contexto global de dados via `QueryClientProvider`.
- **Rotas**: Gerenciamento de páginas com React Router.
- **Alias de Imports**: Utilização de `@` como atalho para a pasta `src`.

## Setup e Configuração

### Pré-requisitos

- **Node.js** versão 22.13.0 ou superior (recomendado usar a versão específica em `.nvmrc`)
- **npm** ou **yarn** para gerenciamento de pacotes

### Configuração do Ambiente

1. **Verifique a versão do Node.js:**
   ```bash
   node --version
   ```

2. **Para usar a versão recomendada (se você tem o nvm instalado):**
   ```bash
   nvm use
   ```

### Instalação e Configuração

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/felipecorerato/ask-me-anything-ai-agent.git
   cd ask-me-anything-ai-agent/web
   ```

2. **Instale as dependências:**
   ```bash
   npm install
   ```

3. **Certifique-se de que o backend está rodando:**
   - O backend deve estar executando em `http://localhost:3333`
   - Para iniciar o backend, vá para o diretório `server` e siga as instruções do README do servidor

### Scripts Disponíveis

- **Desenvolvimento:**
  ```bash
  npm run dev
  ```
  Inicia o servidor de desenvolvimento com hot-reload em `http://localhost:5173`

- **Build de produção:**
  ```bash
  npm run build
  ```
  Gera os arquivos otimizados para produção na pasta `dist`

- **Pré-visualização do build:**
  ```bash
  npm run preview
  ```
  Serve os arquivos de produção localmente para teste

### Estrutura do Projeto

```
web/
├── src/
│   ├── components/          # Componentes React reutilizáveis
│   ├── pages/              # Páginas da aplicação
│   ├── http/               # Hooks e types para requisições HTTP
│   ├── lib/                # Utilitários e configurações
│   └── main.tsx            # Ponto de entrada da aplicação
├── public/                 # Arquivos estáticos
├── .nvmrc                  # Versão do Node.js recomendada
├── vite.config.ts         # Configuração do Vite
└── package.json           # Dependências e scripts
```

### Troubleshooting

- **Erro de conexão com API**: Verifique se o backend está rodando em `http://localhost:3333`
- **Erro de versão do Node.js**: Use a versão especificada no arquivo `.nvmrc`
- **Problemas com dependências**: Tente deletar `node_modules` e `package-lock.json`, depois execute `npm install` novamente

## Sistema de Componentes UI - shadcn/ui

O projeto utiliza **shadcn/ui**, um sistema de componentes moderno que combina **Radix UI** (funcionalidade e acessibilidade) com **Tailwind CSS** (estilização) para criar uma interface consistente e acessível.

### Características do shadcn/ui

- **Não é uma biblioteca tradicional**: Os componentes são copiados diretamente para o projeto
- **Controle total**: Código fonte acessível e modificável
- **Acessibilidade**: Baseado em Radix UI com suporte completo a ARIA
- **Customização**: Sistema de design baseado em CSS variables
- **Performance**: Apenas os componentes utilizados são incluídos

### Configuração

O shadcn/ui está configurado através do arquivo `components.json`:

```json
{
  "style": "new-york",
  "rsc": false,
  "tsx": true,
  "tailwind": {
    "css": "src/index.css",
    "baseColor": "zinc",
    "cssVariables": true
  },
  "aliases": {
    "components": "@/components",
    "ui": "@/components/ui"
  },
  "iconLibrary": "lucide"
}
```

### Componentes Implementados

```
src/components/ui/
├── badge.tsx        # Badges/etiquetas
├── button.tsx       # Botões com variantes
├── card.tsx         # Cards/cartões
├── form.tsx         # Formulários integrados
├── input.tsx        # Campos de entrada
├── label.tsx        # Labels de formulário
└── textarea.tsx     # Campos de texto grandes
```

### Sistema de Temas

O projeto usa CSS variables para um sistema de temas robusto:

- **Tema claro e escuro** configurados automaticamente
- **Cores semânticas**: primary, secondary, accent, destructive, etc.
- **Variáveis personalizáveis** em `src/index.css`

### Exemplo de Uso

```tsx
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card'

<Card>
  <CardHeader>
    <CardTitle>Título do Card</CardTitle>
  </CardHeader>
  <CardContent>
    <Button variant="outline" size="sm">
      Clique aqui
    </Button>
  </CardContent>
</Card>
```

### Adicionando Novos Componentes

Para adicionar novos componentes do shadcn/ui:

```bash
# Instalar a CLI (se necessário)
npm install -g shadcn-ui

# Adicionar componentes específicos
npx shadcn-ui@latest add dialog
npx shadcn-ui@latest add dropdown-menu
npx shadcn-ui@latest add avatar
```

### Utility Function

O projeto inclui a função `cn()` para combinar classes CSS:

```typescript
import { clsx } from 'clsx'
import { twMerge } from 'tailwind-merge'

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs))
}
```

Esta função resolve conflitos entre classes do Tailwind e permite condicionais de classe elegantes.

## Observações

- O projeto utiliza **shadcn/ui** com **Tailwind CSS v4** para um sistema de componentes moderno e acessível
- Utiliza **React 19** com os recursos mais recentes da biblioteca
- O sistema de roteamento é baseado em **React Router DOM v7**
- **React Query (TanStack Query)** para gerenciamento de estado de servidor e cache
- **React Hook Form** com validação **Zod** para formulários robustos
- **Biome** para linting e formatação de código
- O projeto suporta gravação de áudio com upload automático para o backend
- Todas as requisições HTTP são realizadas via hooks customizados em `src/http/`
- O backend deve estar rodando em `http://localhost:3333` para o correto funcionamento
- Interface otimizada para dispositivos móveis e desktop 