# Atlas Virtual da Teoria e Crítica Literárias — Standalone

Página única, estática, sem dependências, com o panorama comparativo das correntes de teoria literária do século XX–XXI usado na disciplina **IELit — Introdução aos Estudos Literários** (UNIVISA/Letras, 2026.2). Cobre 17 períodos, 204 correntes teóricas, 47 termos de glossário e uma tabela de síntese transversal final.

## Como abrir

Dê duplo clique em **`Atlas Virtual de Literatura - Standalone.html`**. Abre em qualquer navegador, sem internet, sem servidor, sem instalação. A pasta `assets/` precisa continuar ao lado do `.html` — é de lá que vêm as imagens de cada período e a logo da UNIVISA.

Para compartilhar com alunos: copie **o `.html` + a pasta `assets/`** juntos (ex.: zipando os dois). Sem a pasta `assets/`, o texto continua íntegro, mas as imagens de período e a logo aparecem quebradas.

## O que tem na página

- **Busca** (topo direito) — filtra por nome da corrente, autor ou década, e pula direto para o cartão.
- **Sumário lateral** (ícone ☰) — salto rápido para qualquer um dos 17 períodos ou para a síntese.
- **204 cartões de correntes teóricas**, agrupados nos 17 períodos, cada um expansível com: concepção de literatura, tríade autor–obra–leitor, método de análise em prosa, método de análise em verso, observações e termos de glossário clicáveis.
- **Glossário em modal** — 47 termos, cada um com definição, exemplo e "por que importa".
- **Síntese transversal** — tabela comparativa dos grandes paradigmas ao final.
- Leitura por rolagem com revelação suave por seção, aba de período que acompanha o scroll, botão de voltar ao topo.

## Arquivos da pasta

| Arquivo/pasta | O que é |
| --- | --- |
| `Atlas Virtual de Literatura - Standalone.html` | **O produto final.** HTML+CSS+JS puro, ~925 KB, sem framework nem runtime externo. |
| `assets/` | Imagens que o standalone consome: `assets/periods/I.png`…`XVII.png` (uma por período) + `univisa-logo.png` + `hero-emblem.png`. |
| `Atlas Virtual de Literatura.zip` | Export do canvas de origem no Claude Design (`Atlas.dc.html` + `atlas-data.js` + `glossary.js` + o design system "Organic" em `_ds/`). É a **fonte editável** — qualquer atualização de conteúdo ou visual nasce aqui e depois é regerada para o standalone (ver abaixo). |
| `Atlas Virtual de Literatura - Standalone (export Claude Design, bundler).html` | Export antigo, gerado direto pelo botão "download standalone" do Claude Design. **Evite usar** — ver aviso abaixo. Mantido só como histórico. |
| `1.png`…`17.png`, `ChatGPT Image…png` | Material de referência/rascunho usado na produção das imagens de período; não são consumidos pela página. |
| `Asimov Academy Design System.html` | Referência visual externa (site real da Asimov Academy) usada como inspiração pontual para os toques "premium" (glow no botão, sombras em camada, revelação por scroll) — não é parte do produto. |

## ⚠️ Por que existem dois arquivos "Standalone"

O botão de export "standalone" do Claude Design gera uma página do tipo *bundler*: ela guarda todo o conteúdo (inclusive as imagens, em base64) dentro de um `<script>` gigante que só vira página de verdade depois de um passo de descompactação em JavaScript, na hora de abrir. Esse formato é frágil no Windows — pode abrir em branco por bloqueio de script local, sem avisar o motivo, mesmo com o conteúdo intacto por dentro. Foi o que aconteceu com o arquivo marcado `(export Claude Design, bundler)`.

O `Atlas Virtual de Literatura - Standalone.html` atual foi **reconstruído do zero como HTML/CSS/JS estático de verdade** — sem manifesto, sem descompactação, sem `import()` — direto a partir dos dados reais (`atlas-data.js`/`glossary.js`) dentro do `.zip`, com as imagens como arquivos normais em `assets/`. É o que deve ser usado e distribuído.

## Como atualizar o conteúdo (para quem for mexer depois)

1. Editar o conteúdo/dados **dentro do canvas do Claude Design** (reabra `Atlas Virtual de Literatura.zip` lá, ou trabalhe direto na sessão publicada) — é onde vivem `atlas-data.js` (períodos e correntes), `glossary.js` (termos) e o visual em `_ds/organic-<hash>/styles.css`.
2. Exportar o `.zip` atualizado para esta pasta.
3. Regenerar o `Standalone.html` a partir dele — não usar o botão "download standalone" do próprio Claude Design pelo motivo acima; peça para reconstruir via script (extrai `atlas-data.js`/`glossary.js`/`styles.css` do zip e regera o HTML/CSS/JS puro, copiando as imagens para `assets/`).

## Créditos

Desenvolvido por Prof. Marcos de Andrade Filho — UNIVISA / Letras.
