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

Skill `avaliacao-ciclo`: braço direito durante o ciclo de avaliação. O **vault é a pasta
onde você abre o Claude Code**; a skill cria `AAAA-XS/` nela.

Durante o dia, fale naturalmente:

- "salva esse feedback: ..." (texto ou imagem) → `Feedbacks/`
- "anota esse ponto a melhorar: ..." → `Feedbacks/`
- "anota esse impacto: ..." → `Negocio/`
- "faz uma anotação: ..." → `Anotacoes/`

Sob demanda, "gera um compilado" junta as notas ainda não compiladas em um brag parcial
(`Brags/`) e marca cada nota com `compilado: true`. No fim do ciclo, "gera o brag final"
consolida os parciais, Linear e GitHub quando agregam, e cruza tudo com a trilha de
carreira do Drive e seu cargo atual.

Comandos:

- **`/dalmow-skills:perfil [AAAA-XS]`** — setup: fontes, cargo/nível, trilha, orgs, datas.
- **`/dalmow-skills:brag-parcial [AAAA-XS]`** — compila os registros pendentes.
- **`/dalmow-skills:brag-final [AAAA-XS]`** — gera o brag final do ciclo.
- **`.mcp.json`** — MCP do GitHub.

## Pré-requisitos

Só o GitHub precisa de env (usado nas compilações):

```bash
export GITHUB_AUTH_TOKEN="ghp_..."   # escopos de leitura: repo, read:org
```

No app desktop (aberto pelo Dock/Finder), as variáveis do `~/.zshrc` não chegam ao Claude
Code e o GitHub falha com `Authorization header is badly formatted`. Declare a env no bloco
`env` do `~/.claude/settings.json` ou abra o app pelo terminal (`open -a Claude`).

Linear e Google Drive **não** vêm no plugin: a skill usa os MCPs que você já tem
configurados no Claude Code (conectores do claude.ai ou `claude mcp add`). Fonte ausente
fica de fora do documento. Para a trilha, dá para usar um export em Markdown/PDF dentro do
vault no lugar do Drive.

Se você já tem um MCP do GitHub configurado globalmente, remova a entrada duplicada
do `.mcp.json`.

## Estrutura do vault (criada na pasta atual)

```
AAAA-XS/
├── perfil.md
├── Feedbacks/   (+ anexos/)
├── Negocio/
├── Anotacoes/
└── Brags/
```
