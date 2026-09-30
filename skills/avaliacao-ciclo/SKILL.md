---
name: avaliacao-ciclo
description: Gera o brag document do ciclo operacional (semestral) de um desenvolvedor. Coleta issues no Linear, PRs e code reviews no GitHub e anotações no vault do Obsidian (pastas AAAA-XS com Feedbacks, Produto, Estudos e IA), entrevista o usuário para preencher lacunas, compara tudo com a trilha de carreira do Google Drive para o cargo atual e produz um documento com entregas, pontos fortes, melhorias e alinhamentos/desalinhamentos com o esperado para a posição. Use sempre que o usuário mencionar brag document, autoavaliação, avaliação de desempenho, ciclo operacional, review semestral, trilha de carreira, promoção ou "o que eu entreguei", mesmo sem citar esta skill.
---

# Brag document do ciclo operacional

O objetivo é produzir um brag document que o usuário leve para a avaliação da empresa: honesto, baseado em evidências e lido contra a trilha de carreira do cargo dele. Avaliadores confiam em fatos verificáveis, então toda afirmação no documento deve apontar para uma fonte (issue do Linear, PR/review do GitHub, nota do Obsidian ou relato na entrevista). E o valor do documento está tanto nos acertos quanto nos desalinhamentos: saber o que falta para o nível esperado é o que torna a conversa de avaliação produtiva.

## Fontes

| Fonte | O que traz | Como acessar |
|---|---|---|
| Obsidian (vault) | Contexto, impacto, feedbacks, estudos, trabalho invisível | MCP do Obsidian ou do sistema de arquivos |
| Linear | Issues e projetos entregues | Conector do Linear |
| GitHub | PRs abertos/mergeados e code reviews feitos | MCP do GitHub |
| Google Drive | Trilha de carreira (expectativas por cargo) | Conector do Google Drive |

Se alguma fonte não estiver disponível, avise o usuário qual está faltando, siga com as demais e deixe explícito no documento final que aquela fonte não foi consultada. Não bloqueie o trabalho por uma fonte ausente.

## Fase 0 — Perfil e ciclo

O perfil fica salvo no vault para que o usuário só precise informá-lo uma vez. Procure o arquivo `perfil.md` na raiz da pasta do semestre (ex.: `2026-2S/perfil.md`); se não existir lá, procure o do semestre anterior como ponto de partida.

**Se o perfil não existir**, pergunte, uma coisa por vez:
1. Qual é o seu cargo atual? (ex.: Desenvolvedor Pleno II). É a pergunta mais importante, pois define contra qual nível da trilha o documento será avaliado.
2. Qual o arquivo da trilha de carreira no Drive? Antes de perguntar, tente encontrar sozinho buscando no Drive por termos como "trilha de carreira", "career path", "matriz de carreira", e peça só a confirmação.
3. Qual o seu usuário do GitHub e **quais organizações** devem ser consideradas? O usuário participa de mais de uma org, então pergunte explicitamente; se o MCP permitir, liste as orgs dele para que escolha. Só as orgs escolhidas entram no perfil.
4. Confirme as datas do ciclo. Proponha a partir do nome da pasta (1S = janeiro a junho, 2S = julho a dezembro) e pergunte se estão corretas.

Então salve `perfil.md` no formato de `references/perfil-template.md` e mostre ao usuário o que foi salvo.

**Se o perfil existir**, apenas confirme numa linha ("Vou avaliar como Desenvolvedor Pleno II, ciclo 2026-2S, de 01/07 a 31/12, olhando as orgs X e Y no GitHub — correto?"). Inclua as orgs do GitHub nessa confirmação. Se o cargo ou as orgs mudaram (promoção, troca de time), atualize o arquivo.

## Fase 1 — Trilha de carreira (Drive)

Leia o documento da trilha. Extraia as expectativas do **cargo atual** e do **próximo nível**, organizadas pelos eixos que a própria trilha usa (ex.: técnico, entrega, colaboração, liderança, produto). Preserve os critérios da trilha com a redação dela; eles serão a régua do documento. Se a trilha não tiver o cargo informado, mostre os níveis disponíveis e pergunte qual corresponde.

## Fase 2 — Coleta

**Obsidian** — leia a pasta do semestre (`AAAA-XS/`) e suas subpastas. Veja `references/estrutura-vault.md` para o papel de cada uma. Em resumo:
- `Feedbacks/` — elogios e críticas recebidos: alimentam pontos fortes e melhorias com a voz de terceiros.
- `Produto/` — entregas, contexto de negócio, métricas de impacto.
- `Estudos/` — cursos, leituras, certificações: evidência de desenvolvimento técnico.
- `IA/` — uso e iniciativas com IA (automações, ferramentas adotadas, ganhos de produtividade).

**Linear** — filtre pelo usuário autenticado ("me") e pelo período do ciclo:
- Issues atribuídas concluídas no período (`list_issues`), paginando até trazer tudo.
- Projetos e iniciativas em que participou ou liderou (`list_projects`, `list_initiatives`).
- Para issues grandes (estimativa alta, prioridade alta, ligadas a projetos), abra o detalhe e os comentários para capturar decisões e contexto.

**GitHub** — use o usuário, as orgs (`github_orgs`) e o período do perfil. Consulte **somente** as orgs listadas: trabalho em outras orgs não pertence a este ciclo de avaliação e não deve entrar no documento, nem mesmo nos números. Rode as buscas uma vez por org (ou combine com `org:A org:B`) e descarte qualquer resultado de repositório fora da lista.
- PRs de autoria dele mergeados no período (busca do tipo `is:pr author:<usuario> org:<org> merged:<inicio>..<fim>`).
- PRs revisados por ele (`is:pr reviewed-by:<usuario> -author:<usuario> org:<org> updated:<inicio>..<fim>`), com contagem e alguns exemplos de reviews substanciais (com comentários de design, bugs encontrados, sugestões aceitas).
- Relacione PRs com issues do Linear pelo identificador (ex.: `ENG-123` no título ou branch) para não duplicar.

Agrupe tudo em **entregas** (projeto, épico ou tema), não em itens soltos. Um avaliador lê "Migrei o módulo de cobrança para a nova API (23 issues, 18 PRs)", não 41 linhas.

## Fase 3 — Cruzar com a trilha

Monte internamente uma matriz critérios da trilha × evidências:
- **Alinhado**: critério do cargo atual com evidência forte.
- **Parcial**: evidência fraca, pontual ou sem resultado claro.
- **Desalinhado / sem evidência**: nenhum registro nas fontes.
- **Acima do nível**: evidência que atende critérios do próximo nível.

Mostre ao usuário um resumo curto (entregas principais + critérios sem evidência) antes da entrevista, para ele corrigir agrupamentos errados cedo.

## Fase 4 — Entrevista

A entrevista preenche lacunas, não repete o que já foi coletado.
- Faça **uma pergunta por vez** e espere a resposta.
- Comece pelas entregas de maior peso, depois pelos critérios da trilha sem evidência ("A trilha espera que um Pleno II conduza decisões técnicas do time. Teve alguma situação assim no semestre?").
- Peça números: antes/depois, tempo economizado, usuários afetados, incidentes evitados.
- Pergunte sobre trabalho que nenhuma fonte capta: mentoria, onboarding, entrevistas técnicas, apoio em incidentes.
- Se a resposta for vaga, aprofunde uma vez com algo concreto. Se o usuário não souber, registre sem inventar.
- Se um critério continuar sem evidência, ele vai para o documento como desalinhamento. Não force evidências fracas para "fechar" a matriz.
- Pare quando os critérios principais estiverem cobertos ou quando o usuário pedir para gerar.

## Fase 5 — Gerar o brag document

Siga `references/template-output.md`. Princípios:
- Primeira pessoa, tom profissional e direto, sem adjetivos inflados. Os fatos falam.
- Cada evidência com fonte: link do Linear/GitHub, nome da nota do Obsidian ou "(relato na entrevista)".
- Nunca invente métricas, datas ou impactos. Dado faltante vira `[a confirmar]` visível.
- Seja seletivo: 3 a 6 entregas bem contadas valem mais que 30 itens.
- Pontos fortes e melhorias devem vir sustentados por evidências e, quando houver, pelos feedbacks da pasta `Feedbacks/`.
- A seção de alinhamento com a trilha é o coração do documento: trate desalinhamentos com a mesma clareza que os acertos, sempre com uma sugestão de como gerar evidência no próximo ciclo.

Ao final, ofereça salvar o documento no vault como `AAAA-XS/Brag Document AAAA-XS.md`.
