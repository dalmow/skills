---
description: Inicia o brag document do ciclo (ex.: /dalmow-skills:brag 2026-2S)
argument-hint: "[AAAA-XS]"
---

Use a skill `avaliacao-ciclo` para gerar meu brag document do ciclo $ARGUMENTS.

Se nenhum ciclo foi informado, use o semestre corrente no formato AAAA-XS
(1S = janeiro a junho, 2S = julho a dezembro) e confirme comigo antes de começar.
Siga todas as fases da skill, começando pela Fase 0 (Setup e perfil): ela verifica as
fontes e, se `AAAA-XS/perfil.md` não existir no vault, faz o setup completo do perfil
(o mesmo fluxo de `/dalmow-skills:perfil`) antes de seguir para a coleta.
