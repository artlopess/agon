# ADR-0002 — Hospedagem

- **Status:** Aceita
- **Data:** 12/11/2026

## Contexto

Custo R$ 0 e meta de salvar uma série em até 1 s (RNF-05), com uso às 19h30 depois de horas sem acesso.

## Opções para a API

- Render (servidor Node gratuito)
- Cloudflare Workers

## Decisão

Front no **Cloudflare Pages**, API no **Cloudflare Workers** com Hono, banco e login no **Supabase** (plano Free).

O Render foi descartado porque o serviço gratuito hiberna após 15 min sem tráfego e leva cerca de 1 min para acordar: a primeira série de cada treino estouraria o RNF-05.

## Consequências

- (+) Custo zero; resposta rápida; provedor já conhecido.
- (−) Workers não é Node.js puro: algumas bibliotecas não funcionam.
- (−) Supabase Free pausa o projeto após 7 dias sem uso e não inclui backups: exige rotina própria de backup com teste de restauração.

Limites consultados em 12/11/2026. Revisar antes de abrir para outros usuários.
