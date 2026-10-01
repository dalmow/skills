# Compilações

## Brag parcial (sob demanda)

Transforma notas raw ainda não compiladas em um brag parcial.

1. **Selecionar**: leia `Feedbacks/`, `Negocio/` e `Anotacoes/` do ciclo e pegue só as notas com `compilado: false` (ou sem o campo). Se não houver nenhuma, diga e pare.
2. **Complementar (opcional, quando agregar)**: se as notas citam issues, PRs ou projetos, confirme/enriqueça no Linear e no GitHub (só as orgs do perfil, só o período dos registros). Não faça varredura completa do ciclo aqui; isso é papel do final.
3. **Entrevista parcial**: antes de escrever, mostre um resumo curto do que as notas cobrem e pergunte, **uma pergunta por vez**, o que falta para o parcial ficar útil. Foque no período coberto:
   - contexto, resultado e números das notas de impacto vagas ("antes/depois", tempo economizado, usuários afetados);
   - o que o usuário fez com feedbacks e pontos a melhorar;
   - trabalho que nenhuma nota registrou (mentoria, onboarding, apoio em incidente, decisões técnicas);
   - se a trilha já foi lida, critérios do cargo sem evidência até agora.
   Seja mais curto que no final: 3 a 5 perguntas, aprofunde uma vez se a resposta for vaga, e pare quando o usuário disser para gerar. Não force: se não souber, registre `[a confirmar]`.
   As respostas entram no parcial marcadas "(relato na entrevista)". Ofereça também salvar cada resposta relevante como nota raw (já com `compilado: true`, apontando para o parcial), para o relato não depender só do parcial.
4. **Escrever** `Brags/Brag Parcial AAAA-MM-DD.md` com o frontmatter de `estrutura-vault.md` e estas seções (omita as vazias):
   - **Período e resumo** (2 a 4 frases)
   - **Entregas e impacto** — agrupadas por tema/projeto, não por nota; resultado com números só se vierem das notas
   - **Feedbacks recebidos** — elogios e críticas, com origem e citação curta
   - **Pontos a melhorar** — e o que foi feito a respeito, se registrado
   - **Anotações relevantes** — estudos, IA, mentoria etc.
   - **Fontes** — lista de `[[wikilinks]]` das notas usadas
   - **Relatos da entrevista** — respostas que não viraram nota, com marcação
   - **Lacunas** — o que ficou sem dado (`[a confirmar]`)
   Se a trilha já foi lida, marque ao lado dos itens o eixo/critério que sustentam.
5. **Flagear**: em cada nota usada, edite só o frontmatter (`compilado: true`, `compilado_em`, `brag`). Não mexa no corpo.
6. Mostre o caminho do parcial e um resumo de 3 linhas. Notas que você julgou irrelevantes continuam `compilado: false`; avise quantas ficaram de fora e por quê.

## Brag final (fim do ciclo)

Consolida o ciclo inteiro.

1. **Setup**: execute 0.2 (fontes) e 0.3 (perfil) da SKILL.md. O perfil é obrigatório aqui.
2. **Régua**: leia a trilha do Drive (cargo atual e próximo nível).
3. **Fechar pendências**: se ainda há notas raw com `compilado: false`, gere antes um parcial com elas (passos acima), para que nada fique fora.
4. **Ler todos os parciais** de `Brags/` (`tipo: brag-parcial`) e, quando um detalhe importar, a nota raw de origem pelos wikilinks. Os parciais são a base; não recompile do zero o que já está consolidado.
5. **Coleta complementar** (sempre que a fonte estiver disponível), para verificar e completar, sem duplicar o que os parciais já contam:
   - **Linear**: issues concluídas no período atribuídas ao usuário (`list_issues`, paginando), projetos e iniciativas em que participou. Detalhe e comentários das issues grandes.
   - **GitHub**: **somente** as orgs do perfil. PRs mergeados (`is:pr author:<usuario> org:<org> merged:<inicio>..<fim>`), PRs revisados (`is:pr reviewed-by:<usuario> -author:<usuario> org:<org> updated:<inicio>..<fim>`) com exemplos de reviews substanciais. Descarte qualquer repositório fora da lista, mesmo nos números. Relacione PRs e issues pelo identificador.
   - Agrupe em **entregas** (projeto, épico, tema), não itens soltos.
6. **Cruzar com a trilha**: matriz critérios × evidências com status **Alinhado** (evidência forte), **Parcial** (fraca/pontual), **Sem evidência** e **Acima do nível** (atende critério do próximo nível). Mostre ao usuário um resumo curto (entregas principais + critérios sem evidência) para corrigir agrupamentos cedo.
7. **Lacunas**: pergunte, **uma pergunta por vez**, só o que os registros não cobrem, começando pelas entregas de maior peso e depois pelos critérios sem evidência. Peça números (antes/depois, tempo, usuários, incidentes). Se a resposta for vaga, aprofunde uma vez; se o usuário não souber, registre sem inventar. Pare quando os critérios principais estiverem cobertos ou o usuário pedir para gerar.
8. **Gerar** `Brags/Brag Final AAAA-XS.md` seguindo `template-output.md`. Seja seletivo (3 a 6 entregas bem contadas), primeira pessoa, tom direto, cada evidência com fonte, desalinhamentos tratados com a mesma clareza dos acertos, sempre com sugestão de como gerar evidência no próximo ciclo. Inclua tudo que agrega à avaliação: feedbacks, melhorias (e o que mudou), impacto, produto, estudos, IA, mentoria.
9. **Flagear** os parciais consumidos (`compilado: true`, `compilado_em`, `brag: "Brag Final AAAA-XS"`) e liste no final do documento as fontes não consultadas, se houver.
