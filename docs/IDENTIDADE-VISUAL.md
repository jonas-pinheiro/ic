# Diretrizes de Identidade Visual — Portal IC Junior
**Colégio Interativa · Uso interno**

---

## 1. Contexto e princípio geral

Este portal é uma ferramenta de trabalho, não uma vitrine institucional. A identidade visual deve transmitir **seriedade acadêmica com acolhimento** — o mesmo espírito do programa de IC do Interativa: rigoroso no método, humano na abordagem.

A referência direta é o site [interativalondrina.com.br](https://www.interativalondrina.com.br): tipografia limpa em negrito, fundo branco predominante, seções bem demarcadas, sem ornamentos desnecessários. O portal de IC herda esse DNA e adiciona cor funcional por série para facilitar a navegação.

**Regra de ouro:** se um elemento não ajuda o usuário a encontrar ou entender uma informação, ele não existe.

---

## 2. Paleta de cores

### Cores base

| Nome | Hex | Uso |
|---|---|---|
| `--navy` | `#0d2b4e` | Navbar, títulos principais, rodapé, fundo de destaques |
| `--navy-mid` | `#1a4070` | Gradientes, variações de fundo escuro |
| `--teal` | `#2a9d8f` | Acento principal, links, botões, bordas de card |
| `--teal-lt` | `#e6f7f5` | Fundo de caixas de destaque (tip boxes) |
| `--amber` | `#e9c46a` | Acento quente, destaques em fundo escuro, avisos |
| `--bg` | `#f4f6f9` | Fundo geral de página |
| `--white` | `#ffffff` | Fundo de cards e painéis |
| `--text` | `#1c2a3a` | Corpo de texto principal |
| `--muted` | `#5a6a7a` | Textos secundários, metadados, labels |
| `--border` | `#dce3ec` | Bordas de cards, divisores, linhas |

### Cores por série (funcionais, não decorativas)

Cada série tem uma cor própria usada em: cabeçalho da página, borda superior de card, tags e ícones de navegação lateral.

| Série | Nome | Hex | Significado intuitivo |
|---|---|---|---|
| 6º ano | `--c6` | `#2a9d8f` | Teal — início, descoberta |
| 7º ano | `--c7` | `#e76f51` | Laranja — energia, método |
| 8º ano | `--c8` | `#457b9d` | Azul-ardósia — análise, profundidade |
| 9º ano | `--c9` | `#6a4c93` | Roxo — maturidade, pesquisa plena |

---

## 3. Tipografia

**Família única:** `Inter` (Google Fonts)
`<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">`

Sem serifa, alta legibilidade em tela, disponível gratuitamente. Alinha com o visual do site institucional do Interativa.

### Escala tipográfica

| Elemento | Peso | Tamanho | Observação |
|---|---|---|---|
| Título de hero/página | 800 | `clamp(1.6rem, 3vw, 2.2rem)` | Letra-spacing: `-0.03em` |
| Título de seção (h2) | 700 | `1.1rem` | Com borda inferior colorida |
| Título de card (h3) | 700 | `0.95rem` | Cor: `--navy` |
| Título de subitem (h4) | 700 | `0.88rem` | Cor: `--navy` |
| Corpo de texto | 400 | `0.9rem` | Line-height: `1.7` |
| Texto secundário/muted | 400 | `0.82rem` | Cor: `--muted` |
| Labels/eyebrows | 700 | `0.68–0.72rem` | Uppercase, letter-spacing: `0.08em` |
| Navbar | 500–700 | `0.85–0.95rem` | — |

---

## 4. Componentes padrão

### Navbar
- Fundo: `--navy`
- Altura fixa: `60px`, `position: sticky; top: 0`
- Logo à esquerda: usar `logo_interativa_fundoescuro.webp` — logotipo oficial do Colégio Interativa em versão clara, **só funciona sobre fundo escuro**. Nunca usar em fundo branco ou claro.
  - Altura recomendada na navbar: `36px`, `width: auto`
  - Caminho: `logo_interativa_fundoescuro.webp` (raiz) ou `../logo_interativa_fundoescuro.webp` (subpastas)
  - Ao lado do logo, manter o texto "IC Junior" em branco para identificar o portal
- Links à direita em branco com opacidade reduzida, hover em `--teal-lt`
- Nas páginas internas: substituir links por breadcrumb `Início / Nome da Página`

### Cards de conteúdo
- Fundo branco, borda `1px solid --border`, border-radius `10px`
- Borda superior `3px solid` na cor do acento (teal por padrão, cor da série nas páginas de série)
- Hover: `box-shadow` suave + `translateY(-2px)`
- Estrutura: ícone emoji → título → descrição → seta de acesso

### Cards de série
- Cabeçalho colorido com gradiente na cor da série
- Badge de estágio no canto superior direito
- Rodapé com tags de conteúdo em `--bg`

### Caixas de destaque (infobox)
- **Regra/aviso** (`rule`): fundo `#fff8e1`, borda `#f0c040`, ícone ⚠️
- **Dica/orientação** (`tip`): fundo `--teal-lt`, borda `#a8dfd9`, ícone 💡
- Padding: `1rem 1.25rem`, border-radius `8px`

### Linha do tempo (cronograma)
- Círculos numerados na cor da série
- Linha vertical conectora em `--border`
- Texto com período em uppercase acima do título

### Barra lateral de navegação (páginas internas)
- `position: sticky; top: 76px`
- Cabeçalho da nav em `--navy`
- Item ativo: fundo `--teal-lt`, borda esquerda `3px solid --serie`, texto em `--serie`
- Seção "Outras Séries" abaixo, em tom mais discreto

### Tags/badges
- Border-radius: `4px` (retangular, não pílula)
- Fundo: `--bg`, texto: `--muted`
- Exceção: badges em fundo escuro usam `rgba(255,255,255,.2)`

---

## 5. Layout e espaçamento

- **Largura máxima do conteúdo:** `1100px`, centralizado com `margin: 0 auto`
- **Padding lateral de página:** `1.5rem` (mobile) → `2rem` (desktop)
- **Gap entre cards:** `1.25rem`
- **Espaçamento entre seções:** `2.5rem` margin-bottom
- **Grid de cards:** `repeat(auto-fill, minmax(240px, 1fr))` — responsivo sem media queries

### Estrutura de página interna
```
Navbar (sticky)
Page Header (fundo colorido da série)
Layout grid: [Sidebar 220px] [Conteúdo 1fr]
Footer
```

---

## 6. Tom e linguagem

Herdado do Interativa: **direto, humano, sem jargão desnecessário**.

- Títulos de seção começam com emoji funcional (não decorativo)
- Usar "você" e "seu projeto" — não "o aluno" ou "o orientando"
- Regras em destaque visual (infobox), nunca enterradas em parágrafos
- Itens marcados com `⚠️ a confirmar` onde o conteúdo ainda precisa de validação

---

## 7. Arquivo CSS central

Quando todos os HTMLs estiverem prontos, todo o CSS será extraído para um único `style.css` na raiz do projeto. Subpastas referenciam com `../style.css`.

```
ic-site/
├── style.css          ← fonte única de verdade
├── index.html
├── 6ano.html
├── 7ano.html
├── 8ano.html
├── 9ano.html
├── manual-jovem-pesquisador.html
├── manual-orientador.html
├── regras-gerais.html
├── etica-em-pesquisa.html
├── glossario.html
├── perguntas-frequentes.html
├── modelos/
│   ├── plano-de-pesquisa.html
│   ├── diario-de-campo.html
│   ├── relatorio-final.html
│   ├── ficha-avaliacao.html
│   ├── termo-autorizacao.html
│   ├── apresentacao-banner.html
│   ├── cronograma.html
│   └── ficha-inscricao-feira.html
└── recursos/
    ├── planos-de-aula.html
    ├── atividades.html
    ├── exemplos-projetos.html
    └── links-externos.html
```

---

## 8. O que NÃO fazer

- ❌ Não usar Google Fonts diferentes de Inter
- ❌ Não adicionar imagens de banco de fotos ou ícones SVG externos (sem CDN garantida)
- ❌ Não usar sombras pesadas ou gradientes em elementos de conteúdo
- ❌ Não criar variações de cor fora da paleta definida
- ❌ Não usar border-radius acima de `12px` em cards (mantém tom sóbrio)
- ❌ Não usar animações além do hover de cards (a elegância está na contenção)
- ❌ Não colocar texto em caixa alta em parágrafos — apenas em labels/eyebrows

---

*Documento de referência interno — Portal IC Junior · Colégio Interativa*
