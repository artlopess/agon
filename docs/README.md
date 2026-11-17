# Documentação do AGON

Comece pelo [**Estado do projeto**](./estado-do-projeto.md): ele mostra a etapa atual, as decisões tomadas e as pendências.

| Documento | Arquivo | Versão |
| --- | --- | --- |
| Estado do projeto (painel central) | [`estado-do-projeto.md`](./estado-do-projeto.md) | 17/11/2026 |
| Especificação de Requisitos de Software | [`requisitos.md`](./requisitos.md) | 1.2 |
| Documento de Arquitetura | [`arquitetura.md`](./arquitetura.md) | 1.1 |
| Identidade Visual | [`identidade-visual.md`](./identidade-visual.md) | rascunho |
| Pesquisa de mercado e estratégia | [`pesquisa-de-mercado.md`](./pesquisa-de-mercado.md) | v1 |
| Decisões de arquitetura (ADRs) | [`adr/`](./adr) | 3 aceitas |

Os arquivos SVG da marca ficam em [`../assets/marca`](../assets/marca).

## Como manter

- Ao fim de cada etapa, atualizar o **Estado do projeto** (status, decisões novas, pendências).
- Toda mudança de escopo passa primeiro pela Especificação de Requisitos (novo ID, origem e prioridade). Ideias novas vão para o backlog, não para o código.
- Toda decisão técnica relevante vira uma ADR nova; ADRs aceitas não são editadas, são substituídas por outra.
- Resultados de testes com usuários e entrevistas entram na **Pesquisa de mercado e estratégia**.
- Commits de documentação usam o prefixo `docs:`.
