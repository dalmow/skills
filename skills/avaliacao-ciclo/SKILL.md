---
name: avaliacao-ciclo
description: Braço direito do ciclo de avaliação (semestral) de um desenvolvedor. Durante o dia registra no vault (a pasta onde o Claude Code está rodando) feedbacks, pontos a melhorar, impactos de negócio e anotações gerais; sob demanda entrevista o usuário e compila os registros em um brag parcial; no fim do ciclo consolida os parciais (e, se útil, Linear e GitHub) em um brag final alinhado à trilha de carreira do Google Drive e ao cargo atual. Use quando o usuário disser "salva esse feedback", "anota esse impacto", "anota esse ponto a melhorar", "faz uma anotação", "gera um compilado/brag parcial", "gera o brag final", ou mencionar brag document, autoavaliação, ciclo, trilha de carreira ou promoção.
---

# Braço direito do ciclo

Três modos, escolhidos pelo que o usuário pede. Em todos, o vault é o **diretório de trabalho atual** da sessão (raiz do vault = `pwd`), nunca um caminho fixo. Leia e escreva arquivos com as ferramentas normais (Read, Write, Edit, Bash), sem MCP de vault.

| Pedido do usuário | Modo | Detalhes |
|---|---|---|
| "salva esse feedback", "anota esse impacto", "anota esse ponto a melhorar", "faz uma anotação" | **Registro** | `references/registro.md` |
| "gera um compilado", "brag parcial" | **Compilação parcial** | `references/compilacao.md` |
| "gera o brag final", "fechou o ciclo" | **Brag final** | `references/compilacao.md` + `references/template-output.md` |
| setup, trocar cargo/orgs/trilha | **Setup** (Fase 0 abaixo) | `/dalmow-skills:perfil` |

Estrutura do vault e frontmatter: `references/estrutura-vault.md`.

## Princípios

- **Registro é rápido.** Quando o usuário pede para salvar algo, salve na hora e confirme em uma linha (caminho do arquivo). Não faça entrevista nem peça confirmação, a não ser que falte algo sem o qual a nota perde o sentido (ex.: "anota esse feedback" sem conteúdo nenhum).
- **Nunca invente.** Métricas, datas, autores e impactos vêm do usuário ou das fontes. Dado faltante vira `[a confirmar]`.
- **O raw é intocável.** Compilar nunca apaga nem reescreve o conteúdo das notas brutas; só muda os campos de flag no frontmatter.
- **Toda afirmação aponta para fonte**: nota do vault, issue do Linear, PR/review do GitHub ou relato do usuário.
- **Ciclo corrente** = semestre da data de hoje (`AAAA-1S` jan–jun, `AAAA-2S` jul–dez), salvo se o usuário citar outro.

## Fontes

| Fonte | Uso | Acesso |
|---|---|---|
| Vault (cwd) | Registros raw, brags parciais, perfil | Arquivos locais |
| Google Drive | Trilha de carreira | MCP/conector do Drive já configurado no Claude Code |
| Linear | Issues e projetos entregues | MCP global do Linear já configurado no Claude Code |
| GitHub | PRs e code reviews | MCP `github` do plugin (env `GITHUB_AUTH_TOKEN`) |

Linear e Drive: identifique pelas ferramentas disponíveis na sessão (nomes com `linear` ou `drive`/`google`), sem assumir nome de servidor. Não adicione servidores próprios para eles.

Linear, GitHub e Drive são usados **só nas compilações** e **só quando agregam**: no parcial, quando as notas mencionam issues/PRs que valem confirmar ou o usuário pede; no final, sempre que disponíveis. Fonte indisponível não bloqueia: avise, siga sem ela e registre no documento que não foi consultada. O registro diário nunca depende de MCP.

## Fase 0 — Setup e perfil

Roda automaticamente na primeira interação do ciclo (quando `AAAA-XS/perfil.md` não existe) e sob demanda via `/dalmow-skills:perfil`.

### 0.1 Vault

O vault é o `pwd`. Se `AAAA-XS/` não existir nele, diga o diretório que será usado e crie a estrutura de `references/estrutura-vault.md` (confirme uma vez antes de criar, pois o usuário pode ter aberto o Claude na pasta errada).

### 0.2 Fontes (só quando for compilar)

Para o registro diário pule esta etapa. Antes de uma compilação, verifique uma fonte por vez e resuma em uma linha o que está disponível:
1. **GitHub** — env `GITHUB_AUTH_TOKEN` definida e MCP `github` respondendo. Se faltar, peça o token (escopos `repo`, `read:org`). O erro `Authorization header is badly formatted` indica env vazia no processo, não token inválido. No app desktop aberto pelo Dock/Finder, a env não vem do `~/.zshrc`: declare no bloco `env` do `~/.claude/settings.json` ou abra por `open -a Claude`.
2. **Linear** e **Drive** — procure o MCP na sessão e faça uma leitura simples. Se não houver ou falhar, peça ao usuário para configurar (claude.ai Settings → Connectors, ou `claude mcp add`, autorização via `/mcp`). Para o Drive, aceite também a trilha exportada em Markdown/PDF dentro do vault, apontada em `trilha_drive`.

### 0.3 Perfil do ciclo

Arquivo `AAAA-XS/perfil.md` (formato em `references/perfil-template.md`). Se não existir, use o do semestre anterior como proposta; se nenhum existir, pergunte uma coisa por vez:
1. Cargo atual (ex.: Desenvolvedor Pleno II, L8) e próximo nível. Define contra qual nível da trilha tudo é avaliado.
2. Arquivo da trilha no Drive. Tente achar sozinho buscando "trilha de carreira", "career path", "matriz de carreira" e peça só confirmação.
3. Usuário do GitHub e **quais organizações** considerar (liste as orgs se o MCP permitir). Só as escolhidas entram.
4. Datas do ciclo, propostas a partir do nome da pasta (1S = jan–jun, 2S = jul–dez).

Salve e mostre o que foi salvo. Se o perfil já existe, confirme em uma linha (cargo, ciclo, datas, orgs); se algo mudou (promoção, troca de time), atualize e ajuste `atualizado_em`.

No modo Registro, perfil ausente **não bloqueia**: salve a nota primeiro e ofereça o setup depois, ao final da resposta, em uma frase.

## Trilha de carreira (régua)

Nas compilações, leia a trilha do Drive e extraia as expectativas do **cargo atual** e do **próximo nível**, organizadas pelos eixos da própria trilha (técnico, entrega, colaboração, liderança, produto etc.), preservando a redação dela. Se a trilha não tiver o cargo informado, mostre os níveis disponíveis e pergunte. O cruzamento com a trilha é descrito em `references/compilacao.md`.
