# Atlas da Teoria Literária

Site estático de página única com o panorama comparativo das correntes de teoria literária do século XX–XXI, usado na disciplina **IELit — Introdução aos Estudos Literários** (UNIVISA/Letras, 2026.2). Cobre 17 períodos, 204 correntes teóricas, 47 termos de glossário e uma tabela de síntese transversal final.

**Live:** _(adicionar aqui a URL depois do primeiro deploy no Vercel)_

## Stack

Nenhuma. É HTML + CSS + JS puro, sem framework, sem build step, sem dependências — `index.html` é a página inteira. Isso é proposital: qualquer navegador abre o arquivo direto do disco, e qualquer host estático (Vercel incluso) o serve sem nenhuma configuração de build.

## Estrutura do repositório

```
.
├── index.html          # a página inteira — busca, sumário, 204 cartões, glossário, síntese
├── assets/
│   ├── periods/I.png … XVII.png   # uma imagem por período
│   ├── univisa-logo.png
│   └── hero-emblem.png
├── vercel.json          # cache longo para /assets, URLs limpas, headers básicos de segurança
└── README.md
```

## O que tem na página

- **Busca** (topo direito) — filtra por nome da corrente, autor ou década, e pula direto para o cartão.
- **Sumário lateral** (ícone ☰) — salto rápido para qualquer um dos 17 períodos ou para a síntese.
- **204 cartões de correntes teóricas**, agrupados nos 17 períodos, cada um expansível com: concepção de literatura, tríade autor–obra–leitor, método de análise em prosa, método de análise em verso, observações e termos de glossário clicáveis.
- **Glossário em modal** — 47 termos, cada um com definição, exemplo e "por que importa".
- **Síntese transversal** — tabela comparativa dos grandes paradigmas ao final.
- Leitura por rolagem com revelação suave por seção, aba de período que acompanha o scroll, botão de voltar ao topo.

## Rodar localmente

Não precisa de servidor: dê duplo clique em `index.html`. Se preferir servir via HTTP (recomendado só para testar comportamento igual ao de produção, ex. cache headers), qualquer servidor estático funciona:

```bash
npx serve .
```

## Deploy no Vercel

O repo já está pronto para importar direto, sem nenhuma configuração adicional — Vercel detecta como projeto estático (sem framework) e serve `index.html` na raiz.

1. [vercel.com/new](https://vercel.com/new) → **Import Git Repository** → selecione `marcosdeandradefilho/atlas-da-teoria-literaria`.
2. Framework Preset: **Other** (ou deixe "No Framework Detected"). Build Command e Output Directory: deixe em branco — não há build.
3. **Deploy.**

Qualquer push em `main` gera um deploy novo automaticamente. `vercel.json` já define cache de 1 ano (imutável) para tudo em `/assets/*` — os PNGs de período nunca mudam de conteúdo sob o mesmo nome, então isso é seguro.

## Como atualizar o conteúdo

Este repositório é só o **produto final** (HTML/CSS/JS estático + imagens). O conteúdo (as 204 correntes, os 17 períodos, o glossário) vem de um canvas Claude Design mantido à parte, com os dados em `atlas-data.js`/`glossary.js` e o design system em `_ds/organic-<hash>/styles.css`. Para atualizar:

1. Editar o conteúdo/visual no canvas Claude Design de origem.
2. Exportar o `.zip` do canvas.
3. Regenerar este `index.html` a partir dele — **não use o botão "download standalone" do próprio Claude Design**: esse export empacota tudo (inclusive as imagens) como base64 dentro de um `<script>` de manifesto que precisa ser descompactado em runtime, e isso falha silenciosamente em vários navegadores/SOs (abre em branco mesmo com o conteúdo intacto por dentro). Regenere via script que lê `atlas-data.js`/`glossary.js`/`styles.css` direto do zip e produz HTML/CSS/JS puro, com as imagens como arquivos normais em `assets/` — é assim que este `index.html` foi construído.
4. Commitar e dar push em `main` — o Vercel republica sozinho.

## Créditos

Desenvolvido por Prof. Marcos de Andrade Filho — UNIVISA / Letras.
