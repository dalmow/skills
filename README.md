# dalmow/skills

Marketplace de plugins/skills do Kelvi Dalmazo para o Claude Code.

## Instalar

```
/plugin marketplace add dalmow/skills
/plugin install dalmow-skills@dalmow
```

## O que vem no plugin `dalmow-skills`

- **Skill `avaliacao-ciclo`** — coleta, entrevista e geração do brag document (ativa
  sozinha quando você fala em brag document, autoavaliação, trilha de carreira etc.).
- **`/dalmow-skills:setup [AAAA-XS]`** — configuração do ciclo: valida GitHub, Obsidian,
  Linear e Drive, e cria/atualiza o perfil (cargo/nível, trilha, orgs, datas).
- **`/dalmow-skills:brag [AAAA-XS]`** — inicia o fluxo para um ciclo.
- **`/dalmow-skills:perfil [AAAA-XS]`** — mostra ou edita o perfil do ciclo
  (cargo, trilha, orgs do GitHub, datas).
- **`.mcp.json`** — servidores MCP do vault do Obsidian, GitHub e Linear.

## Pré-requisitos

Exporte as variáveis antes de abrir o Claude Code (ex.: no `~/.zshrc`):

```bash
export OBSIDIAN_VAULT_PATH="$HOME/caminho/do/vault"
export GITHUB_AUTH_TOKEN="ghp_..."   # escopos de leitura: repo, read:org
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
