# Estrutura do vault

```
AAAA-XS/              ex.: 2026-2S (X = número do semestre)
├── perfil.md         cargo, trilha, GitHub, datas (mantido pela skill)
├── Feedbacks/        feedbacks recebidos (1:1, Slack, avaliação de pares, clientes internos)
├── Produto/          entregas, contexto de negócio, decisões, métricas de impacto
├── Estudos/          cursos, livros, artigos, certificações, experimentos técnicos
└── IA/               uso de IA no trabalho: automações, ferramentas, prompts, ganhos medidos
```

## Como interpretar cada pasta

**Feedbacks** — Fonte principal para pontos fortes e melhorias, porque traz a percepção de outras pessoas. Registre quem deu (ou o papel), quando e o contexto. Feedbacks críticos também contam: mostrar o que fez com eles é evidência de maturidade.

**Produto** — Liga o trabalho técnico ao resultado. Procure o problema, a decisão tomada e o impacto (antes/depois). Cruze com Linear e GitHub pelo nome do projeto ou identificador de issue.

**Estudos** — Evidência de desenvolvimento técnico. Tem mais peso quando o estudo virou aplicação prática (ex.: curso de observabilidade → dashboards criados em Produto).

**IA** — Iniciativas com IA costumam mapear para critérios de inovação, produtividade ou influência técnica na trilha. Destaque o que foi adotado por outras pessoas ou gerou ganho mensurável.

## Frontmatter opcional nas notas

A skill funciona com notas livres, mas estes campos melhoram o cruzamento:

```yaml
---
data: 2026-08-14
linear: ENG-123
pr: https://github.com/org/repo/pull/456
impacto: "redução de 40% no tempo de fechamento mensal"
trilha: [técnico, colaboração]
---
```
