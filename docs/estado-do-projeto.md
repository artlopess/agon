# AGON — Estado do projeto

> Documento central: onde o projeto está, o que foi decidido e onde está cada coisa. Atualizar ao fim de cada etapa.

**Última atualização:** 17/11/2026
**Etapa atual:** Fim de Semana 1 — Walking skeleton (em paralelo: descoberta com usuários)

---

## 1. Roadmap por etapas

| Etapa | Conteúdo | Status |
| --- | --- | --- |
| Planejamento | Elicitação (5 rodadas), requisitos, arquitetura, ADRs | ✅ Concluída (12–13/11/2026) |
| Etapa 0 — Protótipo | 9 telas testadas no celular; escopo da R1 congelado | ✅ Concluída (13/11/2026) |
| Marca | Símbolo "A de progressão" vetorizado; prancha com 3 assinaturas | 🟡 Falta escolher assinatura, testar ícone e buscar INPI |
| Repositório | README, estrutura, ADRs, marca em SVG, estado do projeto, pesquisa de mercado | 🟡 Falta exportar os 3 documentos principais para `docs/` |
| FS1 — Walking skeleton | Monorepo, PWA no Pages chamando `/v1/health` no Workers, projeto Supabase | ⏳ Próxima |
| FS2 — Banco e login | Migração inicial, RLS, login, 1º teste de isolamento | ⏳ |
| FS3 — Exercícios e ficha | Endpoints e telas; cadastrar a ficha real | ⏳ |
| FS4 — Registro na academia | Tela Hoje, sessão, registro de séries pré-preenchido | ⏳ |
| FS5 — Uso real (fim R1a) | Usar em todos os treinos; corrigir atritos | ⏳ |
| FS6 — Histórico e gráfico | Gráfico de carga, recorde pessoal | ⏳ |
| FS7 — Regras de progressão | RN-01/02/03/06 com testes unitários | ⏳ |
| FS8 — Peso, CI e backup (fim R1b) | Peso, testes no GitHub Actions, backup com restauração testada | ⏳ |
| Descoberta (paralela) | Teste do Hevy por 1–2 semanas; entrevistas com 5 pessoas que treinam | ⏳ |
| R2 — Alimentação | Definida após resultado da descoberta | Futuro |
| Validação | 10–20 usuários por 4 semanas (exige LGPD/RNF-07 antes) | Futuro |

## 2. Documentos e artefatos

| Item | Versão | Onde |
| --- | --- | --- |
| Especificação de Requisitos | v1.2 | [`requisitos.md`](./requisitos.md) · [online](https://claude.ai/artifact/9UE81Vmca1mwZRLbvX5Bhi) |
| Documento de Arquitetura | v1.1 | [`arquitetura.md`](./arquitetura.md) · [online](https://claude.ai/artifact/LXbpeH9uueWfBXfXLACRC6) |
| Identidade Visual | rascunho | [`identidade-visual.md`](./identidade-visual.md) · [online](https://claude.ai/artifact/Dvi9NvP2DDVwgfqwr7VhT4) |
| Pesquisa de mercado e estratégia | v1 | [`pesquisa-de-mercado.md`](./pesquisa-de-mercado.md) |
| Protótipo R1 (9 telas) | aprovado | [online](https://claude.ai/artifact/QY6JcbiHQJvuQyoHqwWRC7) |
| Prancha de marca | v1 | [online](https://claude.ai/artifact/WxhwVeDVndPYXE23yTmLug) · SVGs em [`../assets/marca`](../assets/marca) |

Os links "online" são privados do autor.

## 3. Números do escopo

- 48 requisitos funcionais (22 Must, 15 Should, 10 Could, 1 Won't), 14 regras de negócio, 13 requisitos não funcionais, 9 histórias de usuário.
- Release 1 = Treino. Meta-chave: registrar uma série em até 3 toques e 10 s (RNF-01) — atingida no teste do protótipo.

## 4. Decisões tomadas

| ID | Decisão | Data |
| --- | --- | --- |
| ADR-0001 | Stack híbrida: Supabase (banco + login) + API própria em TypeScript + PWA React | 12/11 |
| ADR-0002 | Hospedagem gratuita: Cloudflare Pages + Workers (Hono) + Supabase Free; Render descartado por hibernar | 12/11 |
| ADR-0003 | API acessa o banco com filtro por usuário em todo SQL; teste de isolamento obrigatório; RLS só bloqueia a API automática | 13/11 |
| V-01 a V-06 | Hospedagem; código em inglês; faixa de reps copiada na série; grupos musculares padrão; 1 ficha ativa; treino do dia flexível | 12/11 |
| QA-01 a QA-09 | Incremento 1,25 kg; estagnação = 3 sessões; IA 3 usos/dia; aceita custo de IA; foco ganho de massa; medidas definidas; aquecimento 80% da carga de trabalho; recorde sem 1RM | 12/11 |
| RF-TRE-19 | Anotação opcional por série (pedido no teste de usabilidade) | 13/11 |
| Marca | Direção "A de progressão" (barra diagonal subindo); elmo, folhas e duas linhas descartados | 16/11 |

## 5. Pendências abertas

- [ ] Escolher a assinatura da marca (A símbolo como letra · B separados por fio · C empilhada)
- [ ] Testar ícone no iPhone (60 px) e favicon (16/32 px); mostrar a 3–4 pessoas
- [ ] Busca de marcas parecidas no INPI antes de abrir para outros usuários
- [ ] Exportar requisitos, arquitetura e identidade visual em Markdown para `docs/`
- [ ] Teste do Hevy (1–2 semanas) e entrevistas com 5 pessoas
- [ ] CF-05: medir se o RIR é usado após 4 semanas de uso real

## 6. Backlog de ideias futuras

- BL-01 — Integração com relógios e plataformas de saúde (exige ADR; PWA não acessa HealthKit/Health Connect diretamente)
- BL-02 — Hábitos e rotina (reavaliar após R2)
- Registro de refeição por foto (hoje Won't; usuário prefere texto)
- Recursos sociais (Won't na v1)
- Modelo freemium e versão para personal trainers (só após validação)

---

Ver também: [Pesquisa de mercado e estratégia](./pesquisa-de-mercado.md).
