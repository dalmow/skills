# Modo Registro

Salva o que o usuário pede, na hora, como nota raw em `AAAA-XS/<pasta>/`. Formato de nome e frontmatter em `estrutura-vault.md`.

## Roteamento

| O usuário diz algo como | Pasta | `tipo` | `sentimento` |
|---|---|---|---|
| "salva esse feedback", "recebi esse elogio/crítica" | `Feedbacks/` | `feedback` | `elogio` ou `critica` (deduza do conteúdo; na dúvida, pergunte em uma linha) |
| "anota esse ponto a melhorar", "preciso melhorar X" | `Feedbacks/` | `melhoria` | `melhoria` |
| "anota esse impacto", "isso gerou resultado X" | `Negocio/` | `negocio` | — |
| "faz uma anotação", "anota aí", estudo, IA, mentoria, incidente | `Anotacoes/` | `anotacao` | — |

Pedido ambíguo entre duas pastas: escolha a mais provável e diga qual em uma linha; o usuário corrige se quiser. Um mesmo pedido com dois propósitos (ex.: feedback que também revela impacto) pode gerar duas notas ligadas por `[[wikilink]]`.

## Como salvar

1. Descubra o ciclo corrente (ou o citado). Se `AAAA-XS/<pasta>/` não existir, crie (`mkdir -p`). Não precisa de setup completo para isso.
2. Escreva o conteúdo **fiel ao que o usuário trouxe**. Pode organizar (título, contexto, citação literal em bloco `>`), mas não parafraseie feedback de terceiros: a voz original vale como evidência. Não acrescente interpretação ou impacto que o usuário não deu.
3. Preencha o frontmatter com o que for conhecido; omita campos desconhecidos em vez de inventar. `compilado: false` sempre.
4. Responda em uma linha: `Salvo em AAAA-XS/Feedbacks/2026-10-01 elogio-api.md`.

## Imagens

- Caminho de arquivo informado: copie para `AAAA-XS/<pasta>/anexos/` (`cp`, nome `AAAA-MM-DD-slug.ext`) e referencie na nota com `![[nome.ext]]`.
- Imagem colada na conversa (sem arquivo no disco): você não consegue gravar os bytes. Transcreva o texto visível e descreva o essencial na nota, marque `[imagem original não anexada]` e avise o usuário que, se quiser o arquivo, deve salvá-lo em `anexos/` e dar o caminho.
- Transcrição de print (ex.: mensagem do Slack): inclua autor/papel, data e o texto literal.
