# dalmow/skills

Marketplace (`dalmow`) e plugin (`dalmow-skills`) de skills e comandos para o Claude Code.

## Estrutura

- `.claude-plugin/marketplace.json` — manifesto do marketplace; o plugin usa `source: "./"`.
- `.claude-plugin/plugin.json` — manifesto do plugin; **única** fonte da versão.
- `commands/` — slash commands (`/dalmow-skills:<nome>`).
- `skills/` — skills do plugin, cada uma com `SKILL.md` e `references/`.
- `.mcp.json` — MCP do vault do Obsidian (`OBSIDIAN_VAULT_PATH`) e MCP do GitHub (HTTP,
  `https://api.githubcopilot.com/mcp/`, header `Authorization: Bearer ${GITHUB_AUTH_TOKEN}`).
  Linear e Drive usam os MCPs que o usuário já configurou no Claude Code; não adicione
  servidores próprios para eles.

## Versionamento (obrigatório)

O Claude Code só entrega update aos clientes quando `version` em `.claude-plugin/plugin.json`
muda. Push sem mudar a versão deixa os clientes com o conteúdo antigo em cache.

- Toda alteração que vai para o repositório (commit + push na `main`) **precisa** incluir o
  aumento de `version` em `.claude-plugin/plugin.json`, seguindo semver:
  - **major** — mudança incompatível: command ou skill removido/renomeado, MCP removido,
    formato do `perfil.md` alterado.
  - **minor** — funcionalidade nova compatível.
  - **patch** — correção ou ajuste de texto/prompt sem mudança de comportamento esperado.
- Se as mudanças a enviar não incluírem o aumento de versão, **pergunte ao usuário** qual
  bump aplicar (sugerindo um com base nas regras acima) antes de commitar ou fazer push.
  Não faça push sem versão nova.
- Não defina `version` no `marketplace.json`; ela fica apenas no `plugin.json`.
- Mencione a versão nova na mensagem de commit (ex.: `Release 1.2.0: ...`).

## Convenções

- Conteúdo das skills, commands e README em português.
- Mantenha os commands finos: a lógica fica na skill e o command só aponta para a fase certa.
