---
description: Configura o ciclo e mostra/edita o perfil (fontes, cargo, trilha, orgs do GitHub, datas)
argument-hint: "[AAAA-XS]"
---

Use a skill `avaliacao-ciclo` e execute **somente a Fase 0 (Setup e perfil)** para o ciclo
$ARGUMENTS (se omitido, use o semestre corrente no formato AAAA-XS: 1S = janeiro a junho,
2S = julho a dezembro).

Rode a verificação das fontes normalmente. Na parte do perfil, se `perfil.md` já existir,
não se limite à confirmação em uma linha: mostre os campos atuais e pergunte, um por vez,
se desejo alterar algum (cargo, próximo nível, trilha no Drive, usuário do GitHub, orgs do
GitHub e datas do ciclo). Salve as alterações e atualize `atualizado_em`.

Ao final, resuma o que ficou configurado e o que ainda falta. Não siga para as fases
seguintes da skill.
