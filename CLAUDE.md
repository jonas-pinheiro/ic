# CLAUDE.md — Portal IC Junior · Colégio Interativa

Este arquivo é lido automaticamente pelo Claude Code no início de cada sessão neste repositório. Ele existe para você não precisar reexplicar o projeto toda vez.

## O que é este repositório

Site estático (GitHub Pages) que centraliza a documentação do programa de Iniciação Científica do Colégio Interativa (Londrina-PR), Ensino Fundamental Anos Finais (6º–9º) + Ensino Médio. Substitui documentos Word/PDF avulsos.

## Leia antes de gerar qualquer página

Sempre, nesta ordem, antes de escrever ou editar HTML:

1. **`docs/PROMPT-PROJETO.md`** — regras de comportamento, estrutura de pastas do site, o que nunca fazer, como mapear conteúdo de documentos para componentes visuais.
2. **`docs/IDENTIDADE-VISUAL.md`** — paleta de cores (incluindo cor por série), tipografia, componentes padrão (cards, infoboxes, timeline, sidebar), regras de layout.
3. **`docs/fluxo-anual-ic-consolidado.md`** — o conteúdo pedagógico já validado com a coordenação: fluxo anual do programa, ênfase por série (6º–9º), rubrica de avaliação trimestral, regras de grupo/orientador por série, regras transversais (jaleco, continuidade, FITEC x Mostra de Monografias, 9º EFAF x Médio). **Esta é a fonte de conteúdo para as páginas 6ano.html–9ano.html.**

Esses três arquivos não são opcionais — eles substituem qualquer suposição sobre o programa. Se um dado necessário para uma página não estiver em nenhum dos três, marque `⚠️ a confirmar` em vez de inventar (regra já detalhada em `PROMPT-PROJETO.md`).

## Referências visuais já existentes no repo

- `index.html`, `regimento-ic.html`, `manual-jovem-pesquisador.html`, `manual-orientador.html` — já publicados, servem de gabarito de estrutura e tom.
- `6ano.html` a `9ano.html` — hoje são stubs "em construção"; são o que vamos preencher.
- `logo_interativa_fundoescuro.webp` — só usar sobre fundo escuro (`--navy`), nunca sobre fundo claro.

## Regra de ouro de execução

- Gerar **uma página por vez**, não o lote inteiro, a menos que seja pedido explicitamente.
- Nunca criar `style.css` central antes de todos os HTMLs estarem prontos e validados (fase ainda não chegou).
- Nunca criar arquivos fora da estrutura de pastas prevista em `PROMPT-PROJETO.md` sem confirmação explícita.
- Depois de gerar uma página, parar e aguardar validação antes de seguir para a próxima.

## Origem dos arquivos em `docs/`

| Arquivo | Origem |
|---|---|
| `PROMPT-PROJETO.md` | Já existia no projeto de conteúdo (Claude.ai) — copiado sem alteração |
| `IDENTIDADE-VISUAL.md` | Já existia no projeto de conteúdo (Claude.ai) — copiado sem alteração |
| `fluxo-anual-ic-consolidado.md` | Gerado nas conversas do projeto de conteúdo (Claude.ai), a partir do relato do coordenador/professor sobre o fluxo anual do programa — é o único documento novo deste pacote |
