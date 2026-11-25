# Senai-Livraria-Vue

Livraria — Vue.js 3 (Vite + TypeScript)

## Descrição

Aplicação web de livraria desenvolvida com **Vue.js 3**, **TypeScript** e **Vite**, conforme proposto na **Aula 03 - Atividade 02** da disciplina Frameworks Front-end.

O projeto demonstra os principais conceitos de Vue estudados na aula: reatividade com `ref`, **Composition API** (`setup`), renderização de listas com `v-for`, renderização condicional com `v-if`, vinculação bidirecional de dados com `v-model` e propriedades computadas com `computed`.

## Tecnologias utilizadas

- **Vue.js 3** — framework progressivo JavaScript para interfaces de usuário
- **TypeScript** — tipagem estática para JavaScript
- **Vite** — ferramenta de build e servidor de desenvolvimento rápido
- **HTML5 / CSS3** — estrutura e estilização

## Estrutura do projeto

```
livraria-vue/
├── index.html
├── package.json
├── vite.config.ts
├── tsconfig.json
├── src/
│   ├── main.ts      — ponto de entrada do Vue (createApp)
│   ├── App.vue      — componente principal (template + script + estilo)
│   └── index.css    — estilos globais
```

## Como o protótipo funciona

O prototipo e uma livraria virtual. A pagina exibe um cabecalho, um campo de busca que filtra os livros em tempo real, e uma grade de cards de livros.

Cada livro e renderizado dinamicamente com **v-for**, e ao clicar em um livro ele e selecionado e exibido em uma secao de detalhes abaixo (**v-if** renderizacao condicional). O campo de busca usa **v-model** para vinculacao bidirecional de dados, e a lista filtrada e calculada com uma propriedade **computed** que reage automaticamente a mudancas no filtro.

## Conceitos aplicados (Aula 03 - Atividade 02)

- [x] Reatividade automática com `ref`
- [x] Composition API (`setup`, `<script setup>`)
- [x] Renderização de listas com `v-for`
- [x] Renderização condicional com `v-if`
- [x] Vinculação de dados com `v-model`
- [x] Propriedades computadas com `computed`
- [x] Componentização e props implícitas via eventos de clique

## Como executar

1. Instale as dependencias:
   ```bash
   npm install
   ```
2. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
3. Acesse a URL gerada pelo Vite (por default: `http://localhost:5173`)

Para build de producao:
```bash
npm run build
```

## Repositorio principal

[senai-framework-frontend](https://github.com/paulopoppes-hash/senai-framework-frontend)
