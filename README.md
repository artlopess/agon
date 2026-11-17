# AGON

> **Your life. Your pace. Your evolution.**

Plataforma pessoal de gestão de performance: treino, alimentação e evolução física em um só lugar, com inteligência artificial integrada aos dados do próprio usuário.

**Status:** 🟡 Em desenvolvimento — Release 1 (Treino), Fim de Semana 1 de 8. Situação detalhada em [`docs/estado-do-projeto.md`](./docs/estado-do-projeto.md).

---

## O problema

Quem treina sem registrar cargas tende a estagnar: esquece o que fez na última sessão e não sabe quando nem quanto progredir. A alimentação, sem controle, vira aleatória. O AGON nasceu para resolver isso começando pela dor principal — **registrar treinos de forma rápida e mostrar a progressão de forma clara**.

## Escopo da Release 1 (congelado em 13/11/2026)

### R1a — Ciclo básico
- Cadastro e login (Supabase Auth)
- Cadastro de exercícios e grupos musculares
- Fichas com treinos por dia da semana, faixas de repetições e exercícios alternativos
- Versionamento de fichas (uma ativa por vez; anteriores preservadas)
- Tela **Hoje** com o treino do dia e opção de trocar
- Registro de séries (aquecimento ou válida) com valores da última sessão pré-preenchidos
- Anotação opcional por série
- Meta de usabilidade: **registrar uma série em até 3 toques e 10 segundos**

### R1b — Análise
- Gráfico de evolução de carga por exercício
- Recorde pessoal
- Sugestão de progressão por **dupla progressão** (incremento padrão de 1,25 kg)
- Identificação de estagnação (3 sessões sem aumento de carga)
- Registro de peso corporal

### Fora da Release 1
Alimentação (R2), IA e contexto (R3), assistente e relatórios (R4). Integração com relógios, hábitos e recursos sociais estão no backlog de ideias futuras.

## Mercado e estratégia

O AGON entra num mercado com concorrentes maduros (Hevy, Strong, JEFIT, Fitbod, MyFitnessPal e apps de academia como o da Smart Fit). Registrar treino e sugerir progressão **não são diferenciais**. As hipóteses de diferencial — transparência das regras de progressão, contexto brasileiro e integração para quem usa várias ferramentas — serão validadas com usuários antes da R2. Detalhes em [`docs/pesquisa-de-mercado.md`](./docs/pesquisa-de-mercado.md).

## Stack

| Camada | Tecnologia | Hospedagem |
| --- | --- | --- |
| Front | React + TypeScript + Vite + Tailwind (PWA) | Cloudflare Pages |
| API | Hono + TypeScript | Cloudflare Workers |
| Banco e autenticação | PostgreSQL + Supabase Auth | Supabase |
| Validação | Zod (compartilhado entre front e API) | — |
| CI e backup | GitHub Actions | — |

## Estrutura do repositório

```
agon/
├── apps/
│   ├── web/          # PWA (React)
│   └── api/          # API (Hono no Workers), organizada por domínio
├── packages/
│   └── shared/       # Tipos e schemas Zod compartilhados
├── db/
│   └── migrations/   # Migrações SQL versionadas
├── docs/             # Requisitos, arquitetura, ADRs
└── .github/
    └── workflows/    # Testes e backup
```

Dentro de cada módulo da API: `routes → service → rules / repository`. Regras de negócio (`rules`) são funções puras, sem acesso a banco, e o `repository` é a única camada que executa SQL.

## Decisões de arquitetura

| ADR | Decisão |
| --- | --- |
| [ADR-0001](./docs/adr/0001-stack-hibrida.md) | Stack híbrida: Supabase para banco e login; API própria concentra as regras de negócio |
| [ADR-0002](./docs/adr/0002-hospedagem.md) | Hospedagem gratuita: Cloudflare Pages + Workers + Supabase Free |
| [ADR-0003](./docs/adr/0003-acesso-ao-banco.md) | Acesso ao banco apenas pela API, com filtro por usuário em todo SQL e testes de isolamento entre contas |

## Como rodar localmente

> Disponível a partir do Fim de Semana 1.

```bash
npm install
npm run dev -w apps/api   # API em http://localhost:8787
npm run dev -w apps/web   # App em http://localhost:5173
```

## Documentação

Índice completo em [`docs/README.md`](./docs/README.md):

- [Estado do projeto](./docs/estado-do-projeto.md) — etapa atual, decisões e pendências
- [Especificação de Requisitos de Software](./docs/requisitos.md) (v1.2)
- [Documento de Arquitetura](./docs/arquitetura.md) (v1.1)
- [Identidade Visual](./docs/identidade-visual.md) (rascunho) — símbolo em [`assets/marca`](./assets/marca)
- [Pesquisa de mercado e estratégia](./docs/pesquisa-de-mercado.md)

## Convenções

- **Commits:** [Conventional Commits](https://www.conventionalcommits.org/pt-br/) — `feat:`, `fix:`, `docs:`, `chore:`, `test:`, `refactor:`
- **Código e banco** em inglês; **telas e documentação** em português
- Segredos nunca vão para o repositório

## Roadmap

- [x] Etapa 0 — Requisitos, arquitetura e protótipo aprovados
- [ ] Etapa 1 — Walking skeleton ← atual
- [ ] Descoberta em paralelo — teste do Hevy e entrevistas com 5 pessoas
- [ ] Etapa 2 — Banco e autenticação
- [ ] Etapa 3 — Exercícios e fichas
- [ ] Etapa 4 — Registro na academia
- [ ] Etapa 5 — Uso real e ajustes (fim da R1a)
- [ ] Etapa 6 — Histórico e gráfico
- [ ] Etapa 7 — Regras de progressão
- [ ] Etapa 8 — Peso, testes automáticos e backup (fim da R1b)

---

Projeto pessoal de Arthur — estudante de Engenharia de Software (PUC Campinas).
