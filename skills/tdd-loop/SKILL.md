---
name: tdd-loop
description: Fluxo autônomo para executar issues do Linear do início até a PR aberta.
---

# Execução de issues: TDD → Review → Correção (loop) → PR

Fluxo autônomo para executar issues do Linear do início até a PR aberta.

## Princípio de autonomia

- **Não pergunte nada ao usuário** durante o fluxo, exceto quando for de **extrema importância** e envolver **dúvida de produto/negócio ou regra** que não possa ser inferida da issue, do código ou de convenções do projeto.
- Dúvidas técnicas (nomes, estrutura, abordagem, bibliotecas) são decididas por você, seguindo os padrões do repositório. Registre as decisões relevantes na descrição da PR.
- Correções apontadas pela revisão são aplicadas **sem pedir confirmação**.
- A PR é aberta **sem pedir confirmação**.

## Orquestração (agente principal)

Para **cada issue** solicitada pelo usuário:

1. Busque a issue no Linear (título, descrição, critérios de aceite, `gitBranchName`).
2. Crie uma **worktree separada** para a issue, a partir da branch principal atualizada, usando o nome de branch sugerido pelo Linear (ou `<ID-da-issue>-<slug-do-titulo>`).
3. Dispare **um sub-agente de implementação por issue**, dentro dessa worktree, passando: ID da issue, conteúdo completo da issue, caminho da worktree e estas instruções (seção "Sub-agente de implementação").
4. Issues diferentes podem rodar em paralelo, cada uma em sua worktree e seu sub-agente.
5. Ao final, reporte ao usuário, por issue: link da PR, número de ciclos de revisão e eventuais pontos não críticos remanescentes.

## Sub-agente de implementação (um por issue)

Trabalhe **somente dentro da worktree da issue**.

### 1. Implementação inicial

1. Mova a issue no Linear para **Em progresso** (In Progress).
2. Implemente usando a skill **`/mattpocock-skills:tdd`** (red → green → refactor), cobrindo os critérios de aceite da issue.
3. Rode toda a suíte de testes, lint e typecheck do projeto. Tudo deve passar.
4. Faça um **commit local** (mensagem clara referenciando o ID da issue, ex.: `feat(ABC-123): ...`).

### 2. Revisão

1. Mova a issue no Linear para **Em revisão** (In Review).
2. Dispare um **sub-agente de revisão** que use a skill **`/mattpocock-skills:code-review`** sobre o diff da branch em relação à branch base.
3. O revisor deve devolver um relatório com cada ponto classificado como **red** (crítico), **yellow** (importante) ou **green** (ok / sugestão / nit não crítico).

### 3. Loop de correção

Enquanto o relatório contiver qualquer ponto **red** ou **yellow**:

1. **Não** mova a issue de volta para Em progresso. Ela **permanece em Em revisão** no Linear.
2. Implemente **todas** as correções red e yellow, sem perguntar, usando novamente **`/mattpocock-skills:tdd`** (quando a correção envolver comportamento, escreva primeiro o teste que expõe o problema).
3. Rode testes, lint e typecheck. Tudo deve passar.
4. Faça um **commit local** das correções (ex.: `fix(ABC-123): ajustes da revisão #N`).
5. Dispare um **novo sub-agente de revisão** com `/mattpocock-skills:code-review` sobre o diff completo da branch.
6. Repita.

**Condição de saída:** sobram apenas pontos **green** ou pontos explicitamente não críticos (nits, sugestões opcionais, preferências de estilo).

**Proteção contra loop infinito:** se após **5 ciclos** ainda houver red/yellow, ou se o mesmo ponto reaparecer em 2 ciclos seguidos sem progresso, pare o loop, siga para a PR e liste os pontos pendentes na descrição da PR. Só pergunte ao usuário se o impasse for uma questão de produto/negócio.

### 4. Pull Request

1. Faça push da branch.
2. Abra a PR **sem perguntar**, com:
   - Título: `[ID-da-issue] Título da issue`
   - Descrição: resumo do que foi feito, link da issue no Linear, como testar, decisões técnicas tomadas, número de ciclos de revisão e pontos green/não críticos remanescentes (se houver).
3. **Não altere** o status da issue no Linear ao abrir a PR (ela continua em Em revisão).
4. Retorne ao agente principal: link da PR, ciclos executados e pendências não críticas.

## Resumo das transições no Linear

| Evento | Status no Linear |
|---|---|
| Implementação iniciada | Em progresso |
| Revisão iniciada | Em revisão |
| Revisão encontrou pontos / correções em andamento | Mantém Em revisão (nunca volta) |
| PR aberta | Nenhuma alteração |

## Regras de commit

- Sempre um commit local após **cada** rodada de implementação (inicial e cada correção).
- Nunca faça commit com testes, lint ou typecheck falhando.
- Push apenas no momento de abrir a PR.

## Observação sobre sub-agentes aninhados

Se o ambiente não permitir que o sub-agente de implementação dispare outro sub-agente, o agente principal assume essa função: o sub-agente de implementação devolve o controle após o commit, o agente principal dispara o sub-agente de revisão na mesma worktree e repassa o relatório para um novo sub-agente de implementação, mantendo o mesmo ciclo descrito acima.