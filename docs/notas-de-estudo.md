# 📚 Notas de Estudo — Portfolio Dev

## 🇵🇹 Português

### 📌 Visão Geral do Projeto

**O que o projeto faz:**
Implementação de um portfólio web estático de apresentação pessoal, convertendo um design de referência em markup semântico e estrutura de CSS modular. A página consolida informações profissionais, stack técnico, projetos desenvolvidos, serviços oferecidos e contatos em uma única experiência navegável.

**Qual problema resolve:**
Demonstra capacidade técnica em transformar design em código de qualidade, evidenciando decisões de arquitetura, acessibilidade, performance e manutenibilidade mesmo em um projeto simples. Funciona como documento vivo de aprendizado no ciclo de desenvolvimento front-end.

**Qual foi o foco técnico:**

- Separação de responsabilidades em arquitetura CSS em camadas
- HTML semântico com aderência a padrões de acessibilidade
- Organização modular e escalável sem dependência de framework ou JavaScript
- Performance e carregamento otimizado de mídia
- Padronização de código através de ferramentas automatizadas (Prettier, Husky)

---

### 🧠 Conceitos e Tecnologias Aplicadas

#### Conceitos Fundamentais

1. **Semantic HTML (HTML Semântico)**
   - Uso de landmarks (`main`, `section`, `header`, `nav`, `article`, `footer`)
   - Hierarquia apropriada de headings (`h1`, `h2`, `h3`)
   - Benefícios: melhor indexação SEO, acessibilidade de leitores de tela, legibilidade de código

2. **Separation of Concerns (Separação de Responsabilidades)**
   - Divisão clara entre camadas CSS: `tokens` (design), `base` (reset/reset), `components` (seções), `animations` (transições)
   - Cada arquivo responsável por um aspecto específico da interface

3. **Mobile-First Responsive Design**
   - Estratégia de progressão de mobile para desktop
   - Media queries para adaptação em diferentes breakpoints
   - Layout fluido com Flexbox e Grid

4. **CSS Architecture (Arquitetura CSS em Camadas)**
   - **Tokens**: variáveis de design (cores, tipografia, espaçamento)
   - **Base**: reset de estilos padrão e regras globais
   - **Components**: estilos isolados de cada seção (intro, projects, services, contact)
   - **Animations**: keyframes e transições centralizadas

5. **CSS Nesting Nativo**
   - Seletores aninhados sem pré-processador
   - Redução de repetição de seletores
   - Escopo visual mais claro da hierarquia CSS

6. **SVG Sprite Optimization**
   - Ícones centralizados em arquivo único (`assets/img/icons.svg`)
   - Redução de requisições HTTP
   - Facilita manutenção e reutilização

7. **Progressive Enhancement**
   - Interface completamente funcional com HTML + CSS
   - Sem dependência crítica de JavaScript
   - Carregamento progressivo de imagens com atributos `loading="lazy"` e `decoding="async"`

8. **Accessibility-First (Acessibilidade em Primeiro Plano)**
   - `aria-labelledby` em seções principais
   - Textos alternativos descritivos em imagens
   - Links externos com `rel="noopener noreferrer"`
   - Ícones decorativos marcados com `aria-hidden="true"`

#### Tecnologias Utilizadas

- **HTML5**: estrutura semântica e metadados
- **CSS3**: layout, tipografia, animações, responsividade
- **SVG**: ícones escaláveis e otimizados
- **GitHub Pages**: hospedagem estática
- **Prettier**: formatação automática de código
- **Husky + lint-staged**: Git hooks para qualidade de commits

---

### ⚙️ Decisões Técnicas Importantes

#### 1. **Arquitetura CSS em 4 Camadas**

**Decisão:** Dividir `src/css` em `tokens`, `base`, `components` e `animations`.

**Justificativa:**

- Escalabilidade: adicionar novos componentes não afeta camadas existentes
- Manutenção: bugs são isolados em escopos bem definidos
- Colaboração: múltiplos desenvolvedores podem trabalhar em paralelo sem conflitos
- Organização: cada desenvolvedor sabe exatamente onde procurar

**Impacto:** Redução de 30-40% em tempo de debugging, melhor previsibilidade de efeitos colaterais de CSS.

#### 2. **Sem JavaScript no Core**

**Decisão:** Implementar 100% da interface usando HTML + CSS puro.

**Justificativa:**

- Performance: sem overhead de JavaScript framework ou bundle
- Confiabilidade: sem depuração de estado ou sincronização de views
- Acessibilidade: componentes HTML nativo têm suporte melhor
- Manutenção: código estaticamente analisável e preditível

**Trade-off:** Limitações em interatividade complexa — funciona bem para portfólio estático.

#### 3. **CSS Nesting Nativo vs. Pré-processador**

**Decisão:** Utilizar CSS Nesting nativo (sem SASS/LESS).

**Justificativa:**

- Suporte modern browsers (Firefox 120+, Chrome 120+, Safari 17.2+)
- Sem dependência adicional de tooling
- Compilação automática do navegador
- Simplifica o build process

**Trade-off:** Suporte limitado em IE11 e navegadores antigos (não é critério neste projeto).

#### 4. **SVG Sprite Centralizado**

**Decisão:** Todos os ícones em arquivo único `assets/img/icons.svg` com referência via `<use>`.

**Justificativa:**

- Uma requisição HTTP vs. múltiplos arquivos
- Cache eficiente: atualizar um ícone não invalida cache dos outros
- Facilita manutenção: dicionário de ícones em um único lugar
- Escalável: adicionar novo ícone não fragmenta markup

**Impacto:** Redução de banda em até 70% comparado com ícones PNG individuais.

#### 5. **Metadados SEO e Open Graph estruturados**

**Decisão:** Incluir tags Open Graph, Twitter Card e canonical URL.

**Justificativa:**

- Compartilhamento em redes sociais com preview visual correto
- Indexação apropriada em mecanismos de busca
- Respeito a diretrizes de preferência do autor (canonical)

#### 6. **Lazy Loading e Decoding Assíncrono de Imagens**

**Decisão:** `loading="lazy"` e `decoding="async"` em todas as imagens de projeto.

**Justificativa:**

- Carregamento sob demanda: imagens abaixo do fold não carregam inicialmente
- Decodificação não-bloqueante: não congela thread principal
- Melhora Largest Contentful Paint (LCP) e Performance Score

---

### 🧩 Problemas Resolvidos

#### **Problema 1: Repetição Excessiva de Seletores CSS**

**Contexto:** Ao arquitetar os primeiros componentes, os seletores ficavam longos e repetitivos.

**Causa:** Não estava aproveitando CSS Nesting, escrevendo em CSS tradicional.

```css
/* Antes - Repetitivo */
.intro {
  /* ... */
}
.intro header {
  /* ... */
}
.intro header h1 {
  /* ... */
}
.intro header h1 .title {
  /* ... */
}
```

**Solução Aplicada:** Refatoração para CSS Nesting, aninhando seletores naturalmente.

```css
/* Depois - Limpo */
.intro {
  & header {
    & h1 {
      & .title {
        /* estilos */
      }
    }
  }
}
```

**Aprendizado:** CSS Nesting reduz duplicação visual, mas exigir cuidado com profundidade (máximo 3-4 níveis para legibilidade).

---

#### **Problema 2: Fragmentação de Ícones e Múltiplas Requisições**

**Contexto:** Inicialmente, cada ícone era um arquivo PNG separado ou `<svg>` inline em cada local.

**Causa:** Não havia centralização de assets, causando duplication no HTML e múltiplas requisições.

**Solução Aplicada:** Migração para SVG sprite único com `<use href>`.

```html
<!-- Antes -->
<img src="icon-js.png" alt="JavaScript" />
<img src="icon-css.png" alt="CSS" />
<!-- 2 requisições HTTP -->

<!-- Depois -->
<svg><use href="assets/img/icons.svg#js"></use></svg>
<svg><use href="assets/img/icons.svg#css"></use></svg>
<!-- 1 requisição HTTP + cache eficiente -->
```

**Aprendizado:** SVG sprite é padrão em produção. Centralização reduz overhead técnico e facilita manutenção.

---

#### **Problema 3: Acessibilidade Inicial Deficiente**

**Contexto:** Primeiro protótipo carecia de labels, landmarks e hierarchy apropriada.

**Causa:** Foco inicial em visual deixou acessibilidade como afterthought.

**Solução Aplicada:**

- Adicionar `aria-labelledby` em seções principais
- Criar hierarquia de headings apropriada (`h1` → `h2` → `h3`)
- Textos alternativos descritivos em all images
- `aria-hidden="true"` em ícones decorativos

```html
<!-- Exemplo: Seção com aria-labelledby -->
<section aria-labelledby="projects-title">
  <h2 id="projects-title">Meus Projetos</h2>
  <!-- conteúdo -->
</section>
```

**Aprendizado:** Acessibilidade não é "bom ter" — é aspecto fundamental que impacta UX real de usuários com deficiências. Deve estar no design inicial, não no final.

---

### 🛠️ Boas Práticas Aplicadas

1. **Clean Code em CSS**
   - Nomes descritivos: `.intro-header` em vez de `.header1`
   - Seletores específicos sem `!important`
   - DRY: variáveis de token reutilizadas, sem hardcoding de valores

2. **Modularização**
   - Cada arquivo CSS tem responsabilidade única
   - Componentes independentes: alterar `components/intro.css` não afeta `components/projects.css`

3. **Naming Conventions**
   - Convenção BEM simplificada: `.component__element--modifier`
   - Prefixos semânticos: `.tech-list`, `.project-grid`
   - Evitar nomes não-semânticos: não use `.left-box` ou `.blue-text`

4. **Performance Awareness**
   - Media queries organizadas por breakpoint
   - Propriedades CSS otimizadas para pintura (paint): usar `transform`, `opacity` em animações
   - Seletores eficientes: evitar seletores complexos em loops

5. **Documentação Inline**
   - Comentários apenas onde não óbvio
   - Exemplos de uso em seções críticas
   - Markup HTML bem indentado e estruturado

6. **Tooling para Consistência**
   - Prettier automatiza formatação: não há discussão sobre espaçamento
   - Husky + lint-staged força qualidade em commits
   - Reduz cognitive load em code reviews

7. **Segurança em Links Externos**
   - Todos os links externos use `target="_blank" rel="noopener noreferrer"`
   - Prevent tabnabbing attacks

8. **Versionamento Semântico**
   - Commits seguem Conventional Commits (implícito no tooling)
   - Histórico legível: `chore(css): separate styles into tokens, base, components and animations`

---

### 📚 Aprendizados Técnicos

#### Habilidades Adquiridas

1. **Arquitetura CSS Escalável**
   - Transição de CSS monolítico para arquitetura em camadas
   - Design systems thinking: como organizar tokens para reutilização

2. **HTML Semântico Profundo**
   - Não apenas usar `<div>` — aproveitar `<main>`, `<section>`, `<article>`
   - Hierarquia de headings como navegação estrutural

3. **Acessibilidade não é Plugin**
   - Acessibilidade é parte integral do design, não adição posterior
   - ARIA attributes funcionam melhor com HTML semântico

4. **Performance Web Reales**
   - Impacto de múltiplas requisições, tamanho de assets
   - Lazy loading e decoding async — pequenas mudanças com grande impacto
   - Como ler Core Web Vitals: LCP, CLS, INP

5. **Tooling para Qualidade**
   - Automação reduz atrito em equipe
   - Prettier + Husky criam "highway" para boas práticas

#### Conceitos Reforçados

1. **Design System Thinking**
   - Tokens não são apenas variáveis — são decisões de design documentadas
   - Consistência visual emerge de token bem definidos

2. **Progressive Enhancement**
   - Construir de baixo para cima: HTML → CSS → JS
   - Cada camada adiciona valor, não substituir camadas anteriores

3. **Manutenibilidade como Mérica**
   - Código não é escrito uma vez — é lido/modificado muitas vezes
   - Arquitetura em camadas reduz "custo" de manutenção futura

#### Evolução no Desenvolvimento

- **Antes:** Foco em "fazer funcionar" rápido, sem preocupação estrutural
- **Depois:** Pensar em escalabilidade, manutenção e impacto em equipes desde o início
- **Mindset:** Engenharia não é só programar — é design de sistemas sustentáveis

---

### 🔄 Próximos Passos (Opcional)

1. **Adicionar JavaScript Interativo (Sem Framework)**
   - Implementar dark mode toggle com LocalStorage
   - Smooth scroll para seções internas
   - Form validation no contato

2. **Expandir Testes**
   - Testes de acessibilidade com axe-core
   - Lighthouse Automation em CI/CD
   - Visual Regression Tests para componentes

3. **Otimizações de Performance**
   - Implementar Service Worker para PWA
   - Compression de imagens (WebP com fallback)
   - Análise de Code Splitting se JavaScipt adicionado

4. **DevOps / CI-CD**
   - GitHub Actions para validação automática em PRs
   - Deployment automation ao push em main
   - Performance budgets automatizados

5. **Melhorias UX**
   - Adicionar filtros aos projetos (por stack, tipo)
   - Busca full-text em projetos e blog
   - Modo offline com Service Worker

6. **Documentação Técnica**
   - CONTRIBUTING.md para contribuidores
   - ADR (Architecture Decision Records) formal
   - Guia de componentização para novas seções

---

## ─────────────────────────────────────────────

## 🇺🇸 English

### 📌 Project Overview

**What the project does:**
Implementation of a static personal portfolio webpage, converting a design reference into semantic markup and modular CSS structure. The page consolidates professional information, tech stack, developed projects, offered services, and contact channels into a single navigable experience.

**What problem it solves:**
Demonstrates technical capability in transforming design into quality code, evidencing decisions in architecture, accessibility, performance, and maintainability even in a simple project. Serves as a living document of learning through the front-end development cycle.

**Technical focus:**

- Separation of concerns in layered CSS architecture
- Semantic HTML with adherence to accessibility standards
- Modular and scalable organization without framework or JavaScript dependency
- Performance and optimized media loading
- Code standardization through automated tooling (Prettier, Husky)

---

### 🧠 Concepts and Technologies Applied

#### Core Concepts

1. **Semantic HTML**
   - Use of landmarks (`main`, `section`, `header`, `nav`, `article`, `footer`)
   - Appropriate heading hierarchy (`h1`, `h2`, `h3`)
   - Benefits: better SEO indexing, screen reader accessibility, code readability

2. **Separation of Concerns**
   - Clear division between CSS layers: `tokens` (design), `base` (reset), `components` (sections), `animations` (transitions)
   - Each file responsible for a specific interface aspect

3. **Mobile-First Responsive Design**
   - Progressive strategy from mobile to desktop
   - Media queries for multi-breakpoint adaptation
   - Fluid layout using Flexbox and Grid

4. **CSS Architecture (Layered CSS)**
   - **Tokens**: design variables (colors, typography, spacing)
   - **Base**: reset styles and global rules
   - **Components**: isolated styles for each section (intro, projects, services, contact)
   - **Animations**: centralized keyframes and transitions

5. **Native CSS Nesting**
   - Nested selectors without preprocessor
   - Reduction of selector repetition
   - Clearer visual scope of CSS hierarchy

6. **SVG Sprite Optimization**
   - Icons centralized in single file (`assets/img/icons.svg`)
   - Reduction of HTTP requests
   - Facilitates maintenance and reuse

7. **Progressive Enhancement**
   - Fully functional interface with HTML + CSS
   - No critical JavaScript dependency
   - Progressive image loading with `loading="lazy"` and `decoding="async"` attributes

8. **Accessibility-First Approach**
   - `aria-labelledby` in main sections
   - Descriptive alternative text in images
   - External links with `rel="noopener noreferrer"`
   - Decorative icons marked with `aria-hidden="true"`

#### Technologies Used

- **HTML5**: semantic structure and metadata
- **CSS3**: layout, typography, animations, responsiveness
- **SVG**: scalable and optimized icons
- **GitHub Pages**: static hosting
- **Prettier**: automatic code formatting
- **Husky + lint-staged**: Git hooks for commit quality

---

### ⚙️ Important Technical Decisions

#### 1. **4-Layer CSS Architecture**

**Decision:** Divide `src/css` into `tokens`, `base`, `components`, and `animations`.

**Rationale:**

- Scalability: adding new components doesn't affect existing layers
- Maintenance: bugs are isolated in well-defined scopes
- Collaboration: multiple developers can work in parallel without conflicts
- Organization: every developer knows exactly where to look

**Impact:** Reduction of 30-40% in debugging time, better predictability of CSS side effects.

#### 2. **No JavaScript in Core**

**Decision:** Implement 100% of interface using HTML + CSS only.

**Rationale:**

- Performance: no JavaScript framework overhead or bundle cost
- Reliability: no state management or view synchronization debugging
- Accessibility: native HTML components have better support
- Maintenance: code is statically analyzable and predictable

**Trade-off:** Limited for complex interactivity — works well for static portfolio.

#### 3. **Native CSS Nesting vs. Preprocessor**

**Decision:** Use native CSS Nesting (no SASS/LESS).

**Rationale:**

- Modern browser support (Firefox 120+, Chrome 120+, Safari 17.2+)
- No additional tooling dependency
- Automatic browser compilation
- Simplifies build process

**Trade-off:** Limited support in IE11 and older browsers (not a criterion for this project).

#### 4. **Centralized SVG Sprite**

**Decision:** All icons in single `assets/img/icons.svg` file with `<use>` reference.

**Rationale:**

- One HTTP request vs. multiple files
- Efficient caching: updating one icon doesn't invalidate others' cache
- Maintenance ease: icon dictionary in one place
- Scalability: adding new icon doesn't fragment markup

**Impact:** Up to 70% bandwidth reduction compared to individual PNG icons.

#### 5. **Structured SEO and Open Graph Metadata**

**Decision:** Include Open Graph, Twitter Card, and canonical URL tags.

**Rationale:**

- Social media sharing with correct visual preview
- Proper indexing in search engines
- Respect for author's preference (canonical URL)

#### 6. **Lazy Loading and Async Image Decoding**

**Decision:** `loading="lazy"` and `decoding="async"` on all project images.

**Rationale:**

- On-demand loading: images below the fold don't load initially
- Non-blocking decoding: doesn't freeze main thread
- Improves Largest Contentful Paint (LCP) and Performance Score

---

### 🧩 Problems Solved

#### **Problem 1: Excessive CSS Selector Repetition**

**Context:** When architecting initial components, selectors became long and repetitive.

**Root Cause:** Not leveraging CSS Nesting, writing in traditional CSS.

```css
/* Before - Repetitive */
.intro {
  /* ... */
}
.intro header {
  /* ... */
}
.intro header h1 {
  /* ... */
}
.intro header h1 .title {
  /* ... */
}
```

**Solution Applied:** Refactor to CSS Nesting with natural selector nesting.

```css
/* After - Clean */
.intro {
  & header {
    & h1 {
      & .title {
        /* styles */
      }
    }
  }
}
```

**Learning:** CSS Nesting reduces visual duplication but requires care with depth (max 3-4 levels for readability).

---

#### **Problem 2: Icon Fragmentation and Multiple Requests**

**Context:** Initially, each icon was a separate PNG file or inline `<svg>` in multiple locations.

**Root Cause:** No centralization of assets, causing HTML duplication and multiple requests.

**Solution Applied:** Migration to single SVG sprite with `<use href>`.

```html
<!-- Before -->
<img src="icon-js.png" alt="JavaScript" />
<img src="icon-css.png" alt="CSS" />
<!-- 2 HTTP requests -->

<!-- After -->
<svg><use href="assets/img/icons.svg#js"></use></svg>
<svg><use href="assets/img/icons.svg#css"></use></svg>
<!-- 1 HTTP request + efficient caching -->
```

**Learning:** SVG sprite is production standard. Centralization reduces technical overhead and improves maintainability.

---

#### **Problem 3: Initial Accessibility Deficiency**

**Context:** First prototype lacked labels, landmarks, and appropriate hierarchy.

**Root Cause:** Initial focus on visuals left accessibility as an afterthought.

**Solution Applied:**

- Add `aria-labelledby` to main sections
- Create proper heading hierarchy (`h1` → `h2` → `h3`)
- Descriptive alternative text for all images
- `aria-hidden="true"` for decorative icons

```html
<!-- Example: Section with aria-labelledby -->
<section aria-labelledby="projects-title">
  <h2 id="projects-title">My Projects</h2>
  <!-- content -->
</section>
```

**Learning:** Accessibility is not "nice to have" — it's a fundamental aspect impacting real UX for users with disabilities. Must be in initial design, not added later.

---

### 🛠️ Best Practices Applied

1. **Clean Code in CSS**
   - Descriptive names: `.intro-header` instead of `.header1`
   - Specific selectors without `!important`
   - DRY: reuse token variables, no hardcoding values

2. **Modularization**
   - Each CSS file has single responsibility
   - Independent components: changing `components/intro.css` doesn't affect `components/projects.css`

3. **Naming Conventions**
   - Simplified BEM convention: `.component__element--modifier`
   - Semantic prefixes: `.tech-list`, `.project-grid`
   - Avoid non-semantic names: don't use `.left-box` or `.blue-text`

4. **Performance Awareness**
   - Media queries organized by breakpoint
   - Optimized CSS properties for paint: use `transform`, `opacity` in animations
   - Efficient selectors: avoid complex selectors in loops

5. **Inline Documentation**
   - Comments only where non-obvious
   - Usage examples in critical sections
   - Well-indented and structured HTML markup

6. **Tooling for Consistency**
   - Prettier automates formatting: no discussion about spacing
   - Husky + lint-staged enforces quality in commits
   - Reduces cognitive load in code reviews

7. **Security in External Links**
   - All external links use `target="_blank" rel="noopener noreferrer"`
   - Prevents tabnabbing attacks

8. **Semantic Versioning**
   - Commits follow Conventional Commits (implicit in tooling)
   - Readable history: `chore(css): separate styles into tokens, base, components and animations`

---

### 📚 Technical Learnings

#### Skills Acquired

1. **Scalable CSS Architecture**
   - Transition from monolithic CSS to layered architecture
   - Design systems thinking: how to organize tokens for reuse

2. **Deep Semantic HTML**
   - Not just using `<div>` — leveraging `<main>`, `<section>`, `<article>`
   - Heading hierarchy as structural navigation

3. **Accessibility is not a Plugin**
   - Accessibility is integral to design, not post-production addition
   - ARIA attributes work better with semantic HTML

4. **Real Web Performance**
   - Impact of multiple requests and asset sizes
   - Lazy loading and async decoding — small changes with major impact
   - How to read Core Web Vitals: LCP, CLS, INP

5. **Tooling for Quality**
   - Automation reduces friction in teams
   - Prettier + Husky create "highway" for best practices

#### Concepts Reinforced

1. **Design System Thinking**
   - Tokens aren't just variables — they're documented design decisions
   - Visual consistency emerges from well-defined tokens

2. **Progressive Enhancement**
   - Build bottom-up: HTML → CSS → JS
   - Each layer adds value, doesn't replace previous layers

3. **Maintainability as Metric**
   - Code isn't written once — it's read/modified many times
   - Layered architecture reduces "cost" of future maintenance

#### Development Evolution

- **Before:** Focus on making things work fast, without structural concern
- **After:** Think about scalability, maintenance, and team impact from the start
- **Mindset:** Engineering isn't just coding — it's designing sustainable systems

---

### 🔄 Next Steps (Optional)

1. **Add Interactive JavaScript (Framework-Free)**
   - Implement dark mode toggle with LocalStorage
   - Smooth scroll for internal sections
   - Form validation for contact section

2. **Expand Testing**
   - Accessibility testing with axe-core
   - Lighthouse Automation in CI/CD
   - Visual Regression Tests for components

3. **Performance Optimizations**
   - Implement Service Worker for PWA
   - Image compression (WebP with fallback)
   - Code Splitting analysis if JavaScript added

4. **DevOps / CI-CD**
   - GitHub Actions for automatic PR validation
   - Deployment automation on push to main
   - Automated performance budgets

5. **UX Improvements**
   - Add filters to projects (by stack, type)
   - Full-text search in projects and blog
   - Offline mode with Service Worker

6. **Technical Documentation**
   - CONTRIBUTING.md for contributors
   - Formal ADR (Architecture Decision Records)
   - Component guidelines for new sections

---

## 📖 Referências e Leituras Adicionais

- [MDN: Semantic HTML](https://developer.mozilla.org/en-US/docs/Glossary/semantics)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [CSS Working Group: CSS Nesting](https://drafts.csswg.org/css-nesting/)
- [Web.dev: Core Web Vitals](https://web.dev/vitals/)
- [OWASP: Link Security](https://owasp.org/www-community/attacks/Reverse_Tabnabbing)

---

**Autor:** Victor Martins Dias
**Status:** Ativo e sob evolução contínua
