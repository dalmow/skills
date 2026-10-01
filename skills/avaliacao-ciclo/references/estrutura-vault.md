# Estrutura do vault

O vault é o diretório onde o Claude Code está rodando. A skill cria (com confirmação) a pasta do ciclo nele:

```
<diretório atual>/
└── AAAA-XS/              ex.: 2026-2S (X = número do semestre)
    ├── perfil.md         cargo, trilha, GitHub, datas
    ├── Feedbacks/        feedbacks recebidos e pontos a melhorar
    │   └── anexos/       imagens (prints, fotos) referenciadas pelas notas
    ├── Negocio/          impactos de negócio, métricas, decisões, resultados
    ├── Anotacoes/        anotações gerais (estudos, IA, mentoria, incidentes, contexto)
    └── Brags/            brags parciais e o brag final
```

## Notas raw

Um arquivo por registro, nome `AAAA-MM-DD titulo-curto.md`. Frontmatter:

```yaml
---
tipo: feedback          # feedback | melhoria | negocio | anotacao
data: 2026-10-01
origem: "1:1 com a gestora"   # quem/onde, quando souber (feedback)
sentimento: elogio      # só feedback/melhoria: elogio | critica | melhoria
trilha: [colaboração]   # eixos da trilha, só se o usuário citar ou for óbvio
linear: ENG-123         # opcional
pr: https://github.com/org/repo/pull/456   # opcional
impacto: "redução de 40% no fechamento mensal"   # opcional, só com dado do usuário
compilado: false
---
```

Depois de compilada em um parcial, a nota recebe (e só isso muda nela):

```yaml
compilado: true
compilado_em: 2026-10-15
brag: "Brag Parcial 2026-10-15"
```

## Brags

- Parcial: `Brags/Brag Parcial AAAA-MM-DD.md`, frontmatter `tipo: brag-parcial`, `compilado: false`, `periodo_inicio`, `periodo_fim`.
- Final: `Brags/Brag Final AAAA-XS.md`, frontmatter `tipo: brag-final`.
- Quando um parcial é consumido pelo final, ele recebe `compilado: true`, `compilado_em` e `brag: "Brag Final AAAA-XS"`.
