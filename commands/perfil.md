---
description: Configura o ciclo e mostra/edita o perfil (cargo, trilha, orgs do GitHub, datas)
argument-hint: "[AAAA-XS]"
---

Use a skill `avaliacao-ciclo` e execute **somente a Fase 0 (Setup e perfil)** para o ciclo
$ARGUMENTS (se omitido, use o semestre corrente no formato AAAA-XS: 1S = janeiro a junho,
2S = julho a dezembro). O vault é o diretório atual.

Verifique as fontes (passo 0.2) e, se `perfil.md` já existir, não se limite à confirmação em
uma linha: mostre os campos atuais e pergunte, um por vez, se desejo alterar algum (cargo,
próximo nível, trilha no Drive, usuário do GitHub, orgs e datas). Salve as alterações e
atualize `atualizado_em`.

Ao final, resuma o que ficou configurado e o que falta. Não siga para compilações.
