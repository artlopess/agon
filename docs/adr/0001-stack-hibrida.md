# ADR-0001 — Stack híbrida

- **Status:** Aceita
- **Data:** 12/11/2026

## Contexto

Desenvolvedor único com cerca de 5 h/semana, custo de infraestrutura R$ 0, dados relacionais (ficha → treino → sessão → série), chamadas de IA apenas pelo backend e objetivo de aprender engenharia de software na prática.

## Opções

- **A)** Supabase completo (banco, login e API gerados automaticamente)
- **B)** Node + PostgreSQL com autenticação própria
- **C)** Híbrido

## Decisão

**C.** O Supabase fornece PostgreSQL e autenticação. A API própria, em TypeScript, concentra as regras de negócio e as chamadas de IA. O front é React + TypeScript + Vite + Tailwind, como PWA.

## Consequências

- (+) Autenticação pronta e segura; modelagem SQL, API REST e regras de negócio ficam com o desenvolvedor; regras testáveis em um só lugar.
- (−) Dependência do Supabase para login; duas camadas de backend para entender.
