# Template do perfil (salvo em AAAA-XS/perfil.md)

```markdown
---
tipo: perfil-ciclo
ciclo: 2026-2S
inicio: 2026-07-01
fim: 2026-12-31
cargo: Desenvolvedor Pleno II
proximo_nivel: Desenvolvedor Sênior I
trilha_drive: <link ou nome do arquivo da trilha no Google Drive>
github_usuario: <usuario>
github_orgs:          # SOMENTE estas orgs serão consultadas (obrigatório, ao menos uma)
  - <org-1>
  - <org-2>
atualizado_em: 2026-09-30
---

# Perfil do ciclo

Arquivo mantido pela skill de brag document. Edite à vontade; a skill lê estes campos
no início de cada execução e só pergunta o que estiver faltando.

Sobre `github_orgs`: a busca no GitHub fica restrita às organizações listadas. PRs e
reviews em qualquer outra org (ou em repositórios pessoais) são ignorados. Para incluir
repositórios pessoais, adicione o próprio usuário do GitHub à lista.
```
