---
description: Configura o ciclo (GitHub, Obsidian, Linear, Drive e perfil/nível atual)
argument-hint: "[AAAA-XS]"
---

Faça o setup do ciclo $ARGUMENTS (se omitido, use o semestre corrente no formato AAAA-XS).
Rode as verificações abaixo, uma por vez, e só avance para a próxima quando a atual
estiver resolvida.

1. **GitHub** — confirme que a env `GITHUB_AUTH_TOKEN` está definida. Se não estiver,
   pare e instrua o usuário a exportá-la (escopos de leitura `repo` e `read:org`) antes
   de continuar, já que o MCP do GitHub depende dela.
2. **Obsidian** — confirme que a env `OBSIDIAN_VAULT_PATH` está definida e aponta para um
   diretório existente. Se faltar, peça o caminho do vault e instrua a exportá-la.
3. **Linear** — tente uma chamada simples ao conector do Linear. Se falhar por
   autenticação, instrua o usuário a rodar `/mcp` e autorizar o Linear.
4. **Google Drive** (trilha de carreira) — não vem com MCP dedicado no plugin. Pergunte
   se o usuário já tem um MCP de Drive configurado; se não, peça o arquivo da trilha
   exportado como Markdown/PDF dentro do vault.
5. **Perfil do ciclo** — execute a Fase 0 da skill `avaliacao-ciclo` para preencher ou
   atualizar `perfil.md` (cargo/nível atual, ex.: L8, L9 etc., próximo nível, trilha do
   Drive, usuário e orgs do GitHub, datas do ciclo), seguindo
   `skills/avaliacao-ciclo/references/perfil-template.md`.

Ao final, resuma o que ficou configurado e o que ainda falta (ex.: fonte sem MCP
disponível), sem bloquear o uso das demais.
