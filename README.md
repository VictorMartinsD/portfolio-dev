# Portfolio Dev - Victor Martins Dias

## 🔗 Links do Projeto

<div align="center">
  
[![Acessar Deploy](https://img.shields.io/badge/Acessar%20Deploy-Github%20Pages-blue?style=for-the-badge)](https://victormartinsd.github.io/portfolio-dev/)
[![Figma Design](https://img.shields.io/badge/Figma%20Design-811?style=for-the-badge&logo=figma&logoColor=white&color=FC4A1A)](https://www.figma.com/design/RpjJrZokp9M3BvfRxBY3Bm/Portfolio-Dev--Community-?node-id=3-376&p=f&t=ip9T8ridJcvSxXJv-0)
[![📘 Notas de Estudo](https://img.shields.io/badge/%F0%9F%93%98%20Notas%20de%20Estudo-Documenta%C3%A7%C3%A3o-0ea5e9?style=for-the-badge)](./docs/notas-de-estudo.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

</div>

<div align="center">

## Sumário | Summary

| Português                                                                | English                                                                        |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| [Sobre o Projeto](#-sobre-o-projeto)                                     | [About the Project](#-about-the-project)                                       |
| [Funcionalidades](#-funcionalidades)                                     | [Features](#-features)                                                         |
| [Arquitetura e Decisões Técnicas](#-arquitetura-e-decisões-técnicas)     | [Architecture and Technical Decisions](#-architecture-and-technical-decisions) |
| [Tecnologias e Ferramentas](#-tecnologias-e-ferramentas-análise-técnica) | [Technologies and Tooling](#-technologies-and-tooling-technical-analysis)      |
| [Acessibilidade e Performance](#-acessibilidade-e-performance-checklist) | [Accessibility and Performance](#-accessibility-and-performance-checklist)     |
| [Estrutura de Pastas](#-estrutura-de-pastas-atual)                       | [Current Folder Structure](#-current-folder-structure)                         |
| [Como Rodar Localmente](#-como-rodar-o-projeto-localmente)               | [Run Locally](#-how-to-run-locally)                                            |
| [Aprendizados](#-aprendizados)                                           | [Learnings](#-learnings)                                                       |

</div>

## 🇵🇹 Português

### 📷 Preview do Projeto

<details>
  <summary><strong>Clique para expandir e ver as imagens</strong></summary>
  <div align="center">
    <img src="https://github.com/user-attachments/assets/2ef8d17d-aa39-444a-874e-f5984d0ee5e2" alt="Preview 1" width="100%">
    <img src="https://github.com/user-attachments/assets/70b31598-231b-4ec6-8f9f-84d3929d0631" alt="Preview 2" width="100%">
    <img src="https://github.com/user-attachments/assets/f7429b32-d28c-49ec-a865-77c1b834533c" alt="Preview 3" width="100%">
    <img src="https://github.com/user-attachments/assets/881651c0-b2ea-469c-b440-6d99b6f659d6" alt="Preview 4" width="100%">
  </div>
</details>

### 📌 Sobre o Projeto

Objetivo do projeto:
Converter um layout de portfólio em uma implementação front-end estática com HTML semântico e CSS modular.
Demonstrar consistência em acessibilidade, organização de estilos e performance sem dependência de JavaScript.
Evidenciar decisões técnicas de engenharia em um projeto simples, porém escalável para manutenção futura.

Este projeto implementa uma página única de portfólio com foco em estrutura semântica, componentes de interface reutilizáveis e arquitetura de CSS em camadas. O contexto técnico é a transformação de um design de referência em código navegável, mantendo legibilidade de markup, organização de estilos e previsibilidade de manutenção.

### ✨ Funcionalidades

- Seção de apresentação com animações visuais (typing, blink, fade e bounce).
- Lista de stack técnica com ícones em SVG sprite e feedback visual por hover.
- Grade de projetos com links externos seguros e imagens com carregamento otimizado.
- Seção de serviços e contatos com destaque visual e microinterações.
- Metadados SEO/Open Graph/Twitter para compartilhamento e indexação.

### 🏗️ Arquitetura e Decisões Técnicas

- Arquitetura de CSS por camadas em `src/css`: `tokens`, `base`, `components`, `animations`.
- Separação de responsabilidades: variáveis de design em `tokens`, regras globais em `base`, seções da página em `components`, keyframes em `animations`.
- HTML semântico com `main`, hierarquia de títulos (`h1/h2/h3`) e `aria-labelledby` nas seções principais.
- Decisão de não utilizar JavaScript: toda a interface e interações são controladas por HTML + CSS.
- Ícones centralizados em sprite SVG (`assets/img/icons.svg`) para reduzir repetição no HTML e facilitar manutenção.
- Uso de CSS Nesting nativo para reduzir repetição de seletores e manter escopo de estilo coeso.
- Sem camadas de componentes JavaScript, serviços, hooks, integração com APIs ou testes automatizados no estado atual.

### 🛠️ Tecnologias e Ferramentas (Análise Técnica)

#### Core

- HTML5: estrutura semântica da página, landmarks e conteúdo.

#### Styling

- CSS3: layout, tipografia, estados de interação e responsividade.
- CSS Nesting nativo: organização hierárquica de seletores sem pré-processador.

#### Animations

- CSS Keyframes: animações `bounce`, `typing`, `blink` e `fadeOut` em `src/css/animations/keyframes.css`.

#### Infrastructure / API

- GitHub Pages: entrega estática do projeto em ambiente de produção.
- Sem APIs externas e sem camada de serviços HTTP no código atual.

#### Tooling

- Prettier: padronização de formatação (`npm run format`).
- Husky: preparo de hooks Git (`npm run prepare`).
- lint-staged: execução de formatação em arquivos staged (`*.html`, `*.css`, `*.js`).

### ✅ Acessibilidade e Performance (Checklist)

- [x] Estrutura semântica com `main`, `section`, `header`, `nav`, `article` e `footer`.
- [x] Hierarquia de headings aplicada (`h1`, `h2`, `h3`).
- [x] `aria-labelledby` nas seções principais.
- [x] Textos alternativos (`alt`) em imagens de conteúdo.
- [x] `aria-hidden="true"` em ícones decorativos SVG.
- [x] Links externos com `target="_blank"` + `rel="noopener noreferrer"`.
- [x] `loading="lazy"` e `decoding="async"` nas imagens de projetos.
- [x] Sprite SVG para reduzir repetição de markup e simplificar manutenção.

### 🗂️ Estrutura de Pastas Atual

```text
portfolio-dev/
├── assets/
│   ├── background/
│   ├── img/
│   │   ├── icons.svg
│   │   ├── favicon.png
│   │   └── ...
│   └── thumbnail/
├── src/
│   └── css/
│       ├── animations/
│       │   └── keyframes.css
│       ├── base/
│       │   ├── base.css
│       │   └── reset.css
│       ├── components/
│       │   ├── contact.css
│       │   ├── intro.css
│       │   ├── projects.css
│       │   ├── services.css
│       │   └── utilities.css
│       ├── tokens/
│       │   └── tokens.css
│       └── index.css
├── index.html
├── package.json
└── README.md
```

### 🚀 Como Rodar o Projeto Localmente

Pré-requisito: Node.js instalado (para instalar dependências de tooling).

```bash
git clone https://github.com/VictorMartinsD/portfolio-dev.git
```

```bash
cd portfolio-dev
```

```bash
npm install
```

Como abrir o projeto:

- Projeto estático: abra `index.html` no navegador.

Comandos disponíveis via `package.json`:

```bash
npm run format
```

```bash
npm run prepare
```

Observações técnicas:

- Não há script `dev` no `package.json` atual.
- Não há script `lint` dedicado; o fluxo atual de qualidade usa Prettier + lint-staged.

### 📚 Aprendizados

- Evolução de uma estrutura CSS monolítica para arquitetura em camadas com responsabilidades claras.
- Consolidação de boas práticas de semântica e acessibilidade sem impacto visual.
- Padronização de segurança em links externos e otimização de carregamento de mídia.
- Melhoria de manutenção com sprite SVG e seletor CSS explícito no lugar de seletores frágeis.

> 📘 Para mais detalhes técnicos e análises, consulte [📖 notas-de-estudo.md](./docs/notas-de-estudo.md)

---

## 🇺🇸 English

### 📌 About the Project

Project goal:
Convert a portfolio layout into a static front-end implementation with semantic HTML and modular CSS.
Demonstrate consistent accessibility, style organization, and performance without JavaScript dependencies.
Show technical decision-making in a simple project that is still maintainable and scalable.

This project implements a single-page portfolio focused on semantic structure, reusable UI sections, and layered CSS architecture. The technical context is turning a reference design into production-ready markup with maintainable styling and clear engineering choices.

### ✨ Features

- Intro section with visual animations (typing, blink, fade, and bounce).
- Tech stack list using an SVG sprite and hover feedback.
- Project grid with secure external links and optimized image loading.
- Services and contact sections with visual emphasis and microinteractions.
- SEO/Open Graph/Twitter metadata for indexing and social sharing.

### 🏗️ Architecture and Technical Decisions

- Layered CSS architecture in `src/css`: `tokens`, `base`, `components`, `animations`.
- Responsibility split: design variables in `tokens`, global rules in `base`, page sections in `components`, keyframes in `animations`.
- Semantic HTML with `main`, heading hierarchy (`h1/h2/h3`), and `aria-labelledby` on main sections.
- Decision to avoid JavaScript: all interface behavior is implemented with HTML + CSS.
- Centralized SVG sprite (`assets/img/icons.svg`) to reduce repetitive markup and simplify maintenance.
- Native CSS Nesting to keep selectors scoped and easier to evolve.
- No JavaScript component layer, services, hooks, API integrations, or automated tests in the current state.

### 🛠️ Technologies and Tooling (Technical Analysis)

#### Core

- HTML5: semantic page structure, landmarks, and content.

#### Styling

- CSS3: layout, typography, interaction states, and responsiveness.
- Native CSS Nesting: hierarchical selector organization without a preprocessor.

#### Animations

- CSS Keyframes: `bounce`, `typing`, `blink`, and `fadeOut` in `src/css/animations/keyframes.css`.

#### Infrastructure / API

- GitHub Pages: static deployment target.
- No external APIs and no HTTP service layer in the current codebase.

#### Tooling

- Prettier: formatting standardization (`npm run format`).
- Husky: Git hooks setup (`npm run prepare`).
- lint-staged: staged-file formatting for `*.html`, `*.css`, and `*.js`.

### ✅ Accessibility and Performance Checklist

- [x] Semantic structure with `main`, `section`, `header`, `nav`, `article`, and `footer`.
- [x] Heading hierarchy implemented (`h1`, `h2`, `h3`).
- [x] `aria-labelledby` in key sections.
- [x] Alternative text (`alt`) in content images.
- [x] `aria-hidden="true"` in decorative SVG icons.
- [x] External links using `target="_blank"` + `rel="noopener noreferrer"`.
- [x] `loading="lazy"` and `decoding="async"` on project images.
- [x] SVG sprite to reduce repeated HTML and improve maintainability.

### 🗂️ Current Folder Structure

```text
portfolio-dev/
├── assets/
│   ├── background/
│   ├── img/
│   │   ├── icons.svg
│   │   ├── favicon.png
│   │   └── ...
│   └── thumbnail/
├── src/
│   └── css/
│       ├── animations/
│       │   └── keyframes.css
│       ├── base/
│       │   ├── base.css
│       │   └── reset.css
│       ├── components/
│       │   ├── contact.css
│       │   ├── intro.css
│       │   ├── projects.css
│       │   ├── services.css
│       │   └── utilities.css
│       ├── tokens/
│       │   └── tokens.css
│       └── index.css
├── index.html
├── package.json
└── README.md
```

### 🚀 How to Run Locally

Prerequisite: Node.js installed (for tooling dependencies).

```bash
git clone https://github.com/VictorMartinsD/portfolio-dev.git
```

```bash
cd portfolio-dev
```

```bash
npm install
```

How to open the project:

- Static project: open `index.html` in the browser.

Available commands from `package.json`:

```bash
npm run format
```

```bash
npm run prepare
```

Technical notes:

- There is no `dev` script in the current `package.json`.
- There is no dedicated `lint` script; the current quality flow uses Prettier + lint-staged.

### 📷 Preview

<details>
  <summary><strong>Click to expand and view images</strong></summary>
  <div align="center">
    <img src="https://github.com/user-attachments/assets/2ef8d17d-aa39-444a-874e-f5984d0ee5e2" alt="Preview 1" width="100%">
    <img src="https://github.com/user-attachments/assets/70b31598-231b-4ec6-8f9f-84d3929d0631" alt="Preview 2" width="100%">
    <img src="https://github.com/user-attachments/assets/f7429b32-d28c-49ec-a865-77c1b834533c" alt="Preview 3" width="100%">
    <img src="https://github.com/user-attachments/assets/881651c0-b2ea-469c-b440-6d99b6f659d6" alt="Preview 4" width="100%">
  </div>
</details>

### 📚 Learnings

- Refactoring from a monolithic stylesheet into a layered architecture with explicit responsibilities.
- Applying semantic and accessibility improvements without changing the visual output.
- Standardizing external-link security and media-loading optimization.
- Improving maintainability with an SVG sprite and explicit CSS selectors.

> 📘 For deeper technical insights and project analysis, see [📖 notas-de-estudo.md](./docs/notas-de-estudo.md)

---

Desenvolvido por [Victor Martins Dias](https://github.com/VictorMartinsD)  
Front-End Developer focado em aplicações web modernas e performance.
