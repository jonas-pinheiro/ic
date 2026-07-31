# Prompt do Projeto — Portal IC Junior

## Contexto

Estou construindo um portal de documentação interna chamado **IC Junior** para o Colégio Interativa (Londrina-PR). O objetivo é centralizar toda a documentação do programa de Iniciação Científica do Ensino Fundamental Anos Finais (6º ao 9º ano) em arquivos HTML estáticos, organizados em pastas, para deploy no GitHub Pages.

O portal substitui documentos Word e PDFs dispersos que se perdem na troca de coordenadores. Não é uma vitrine — é uma ferramenta de trabalho para orientadores e alunos.

---

## Arquivos de referência deste projeto

- `IDENTIDADE-VISUAL.md` — especificação completa de cores, tipografia, componentes e layout. **Toda geração de HTML deve seguir este arquivo à risca.**
- `index.html` — página principal já criada, serve como referência de estrutura e padrão visual
- `6ano.html` — página de série já criada, serve como referência de layout de página interna (sidebar + conteúdo + header colorido)
- `logo_interativa_fundoescuro.webp` — logotipo oficial do Colégio Interativa em versão clara (texto branco/cinza + símbolo colorido). **Usar exclusivamente na navbar e em outros elementos sobre fundo escuro (`--navy`).** Nunca colocar sobre fundo branco ou claro — o logo desaparece. Caminho relativo: `logo_interativa_fundoescuro.webp` para arquivos na raiz, `../logo_interativa_fundoescuro.webp` para arquivos em subpastas (`modelos/`, `recursos/`).

---

## Regras que nunca mudam

### 1. Fidelidade ao conteúdo oficial
Quando o usuário fornecer documentos oficiais do colégio (manuais, regulamentos, cronogramas, fichas), o conteúdo deve ser transposto **sem alteração de significado**. Não resumir, não reinterpretar, não complementar com informações externas. Se um trecho for ambíguo ou parecer incompleto, marcá-lo com:
```html
<span class="placeholder-tag">⚠️ a confirmar</span>
```
e seguir em frente — nunca inventar conteúdo institucional.

### 2. Identidade visual
Seguir `IDENTIDADE-VISUAL.md` em todos os detalhes:
- Fonte única: `Inter` via Google Fonts
- Paleta de variáveis CSS conforme especificado (sem novas cores)
- Componentes padrão: cards, infoboxes, timeline, sidebar, tags
- Sem imagens externas, sem SVG de CDNs não garantidas, sem animações além de hover

### 3. CSS inline por enquanto
Durante a fase de construção, cada HTML carrega seu próprio `<style>` completo. Isso permite abrir qualquer arquivo isoladamente no browser sem depender de outros arquivos. **A centralização para `style.css` acontece apenas quando todos os HTMLs estiverem prontos**, em uma etapa final de refatoração.

### 4. Links relativos corretos
- Arquivos na raiz: `href="6ano.html"`, `href="index.html"`
- Arquivos em subpastas: `href="../index.html"`, `href="../style.css"` (quando centralizar)
- Nunca usar caminhos absolutos ou `./`

### 5. Estrutura de pastas
```
ic-site/
├── style.css              ← só existe na etapa final de centralização
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
Arquivos novos não previstos aqui só são criados se o usuário confirmar explicitamente.

---

## Como processar documentos recebidos

Quando o usuário enviar um documento (PDF, Word, texto, foto):

1. **Identificar** a qual página do site o conteúdo pertence
2. **Mapear** cada seção do documento para os componentes visuais corretos:
   - Regras e obrigações → `infobox rule` (⚠️)
   - Dicas e orientações → `infobox tip` (💡)
   - Sequências temporais → componente `timeline`
   - Listas de itens independentes → `obj-list` com checkmarks
   - Conceitos com definição → `concept-grid`
   - Documentos para baixar → `res-list`
3. **Preservar** títulos, nomes próprios, numerações e terminologia exatamente como estão no original
4. **Marcar** com `⚠️ a confirmar` qualquer trecho que:
   - Contenha data ou valor numérico que possa estar desatualizado
   - Faça referência a outro documento não fornecido
   - Seja ambíguo sem o contexto completo
5. **Gerar** o arquivo HTML completo, pronto para salvar na pasta correta

---

## Estrutura padrão de uma página interna

Toda página de conteúdo (série, manual, modelo, recurso) segue este esqueleto:

```
Navbar (sticky, --navy, breadcrumb à direita)
Page Header (fundo colorido: --navy para páginas gerais, cor da série para 6º-9º)
  ├── eyebrow label (categoria)
  ├── h1 (título da página)
  ├── subtitle (descrição curta)
  └── header-tags (contexto rápido)
Layout grid: sidebar 220px | conteúdo 1fr
  Sidebar:
    ├── nav interna (âncoras para seções)
    └── nav outras séries (se for página de série)
  Conteúdo:
    └── sections com id para âncora
Footer
```

---

## Comportamento esperado em cada tipo de solicitação

| Solicitação | Ação |
|---|---|
| "Gera o 7ano.html" sem conteúdo | Gerar com estrutura completa e placeholders `⚠️ a confirmar` em todo o conteúdo |
| Documento oficial anexado | Extrair conteúdo, mapear para componentes, gerar HTML fiel |
| "Atualiza a seção X do arquivo Y" | Editar apenas a seção indicada, preservar o resto |
| "Centraliza o CSS" | Extrair todo CSS em `style.css`, substituir `<style>` por `<link>` em todos os HTMLs, ajustar caminhos relativos por subpasta |
| "Gera o .zip para deploy" | Organizar todos os arquivos na estrutura de pastas correta e zipar |
| Conteúdo ambíguo ou ausente | Marcar `⚠️ a confirmar`, nunca inventar |

---

## Tom e linguagem

- Segunda pessoa: "você", "seu projeto", "sua pesquisa"
- Evitar: "o aluno", "o orientando", "o discente"
- Emojis apenas funcionais no início de títulos de seção (não decorativos no corpo)
- Português brasileiro, sem jargão acadêmico desnecessário
- Frases curtas e diretas — o usuário está consultando em meio a uma tarefa, não lendo por prazer

---

## O que nunca fazer

- ❌ Inventar conteúdo institucional (datas, regras, nomes, critérios)
- ❌ Resumir ou reinterpretar documentos oficiais sem autorização explícita
- ❌ Criar arquivos fora da estrutura de pastas acordada sem confirmação
- ❌ Usar cores, fontes ou componentes fora do especificado em `IDENTIDADE-VISUAL.md`
- ❌ Adicionar dependências externas (bibliotecas JS, ícones de CDN, imagens de stock)
- ❌ Criar um `style.css` central antes de todos os HTMLs estarem prontos e validados

---

*Prompt de projeto — Portal IC Junior · Colégio Interativa · uso interno*
