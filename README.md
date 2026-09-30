# dalmow/skills

Marketplace de plugins/skills do Kelvi Dalmazo para o Claude Code.

## Instalar

```
/plugin marketplace add dalmow/skills
/plugin install dalmow-skills@dalmow
```

## Atualizar

O plugin segue semver no `plugin.json`; cada release aumenta a versão. Para receber updates:

- Automático: no `/plugin`, aba de marketplaces, ative o auto-update do `dalmow`
  (vem desligado para marketplaces de terceiros).
- Manual: `/plugin marketplace update dalmow` e depois `/plugin update`, ou no shell:

```bash
claude plugin update dalmow-skills@dalmow
```

## O que vem no plugin `dalmow-skills`

- **Skill `avaliacao-ciclo`** — coleta, entrevista e geração do brag document (ativa
  sozinha quando você fala em brag document, autoavaliação, trilha de carreira etc.).
- **`/dalmow-skills:perfil [AAAA-XS]`** — setup do ciclo: verifica as fontes (Obsidian,
  Linear, GitHub, Drive) e cria ou edita o perfil (cargo/nível, trilha, orgs, datas).
- **`/dalmow-skills:brag [AAAA-XS]`** — gera o brag document. Começa pelo mesmo setup;
  se o perfil do ciclo não existir, cria antes de coletar.
- **`.mcp.json`** — servidores MCP do vault do Obsidian e do GitHub.

## Pré-requisitos

Exporte as variáveis antes de abrir o Claude Code (ex.: no `~/.zshrc`):

```bash
export OBSIDIAN_VAULT_PATH="$HOME/caminho/do/vault"
export GITHUB_AUTH_TOKEN="ghp_..."   # escopos de leitura: repo, read:org
```

Linear e Google Drive **não** vêm no plugin: a skill usa os MCPs que você já tem
configurados no Claude Code (conectores do claude.ai ou `claude mcp add`). Se algum faltar,
o setup avisa e pede a configuração; a fonte ausente fica de fora do documento. Para a
trilha, dá para usar um export em Markdown/PDF dentro do vault no lugar do Drive.

Se você já tem um MCP do GitHub configurado globalmente, remova a entrada duplicada
do `.mcp.json`.

## Estrutura esperada do vault

```
AAAA-XS/
├── perfil.md
├── Feedbacks/
├── Produto/
├── Estudos/
└── IA/
```
