# brag-document

Plugin do Claude Code que gera o brag document do ciclo operacional semestral.

## O que vem no plugin

- **Skill `avaliacao-ciclo`** — coleta, entrevista e geração do documento (ativa sozinha
  quando você fala em brag document, autoavaliação, trilha de carreira etc.).
- **`/brag-document:brag [AAAA-XS]`** — inicia o fluxo para um ciclo.
- **`/brag-document:perfil [AAAA-XS]`** — mostra ou edita o perfil do ciclo
  (cargo, trilha, orgs do GitHub, datas).
- **`.mcp.json`** — servidores MCP do vault do Obsidian, GitHub e Linear.

## Pré-requisitos

Exporte as variáveis antes de abrir o Claude Code (ex.: no `~/.zshrc`):

```bash
export OBSIDIAN_VAULT_PATH="$HOME/caminho/do/vault"
export GITHUB_PERSONAL_ACCESS_TOKEN="ghp_..."   # escopos de leitura: repo, read:org
```

- **Linear**: autentique via OAuth no primeiro uso (`/mcp` dentro do Claude Code).
- **Google Drive** (trilha de carreira): não vem no `.mcp.json`. Use um servidor MCP do
  Google Drive de sua preferência, ou exporte a trilha para Markdown/PDF dentro do vault
  e aponte `trilha_drive` no `perfil.md` para esse arquivo.
- Se você já tem algum desses servidores configurado globalmente, remova a entrada
  duplicada do `.mcp.json`.

## Estrutura esperada do vault

```
AAAA-XS/
├── perfil.md
├── Feedbacks/
├── Produto/
├── Estudos/
└── IA/
```
