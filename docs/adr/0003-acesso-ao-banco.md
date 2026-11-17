# ADR-0003 — Acesso ao banco e autorização

- **Status:** Aceita
- **Data:** 13/11/2026

## Contexto

A API se conecta ao PostgreSQL com credencial de servidor. Essa conexão (como a chave `service_role`) ignora as políticas de RLS, então o RLS não protege as consultas da própria API.

## Opções

- **A)** Conexão direta com filtro explícito por usuário em todo SQL
- **B)** Executar cada consulta com o JWT do usuário, deixando o RLS decidir

## Decisão

**A** na Release 1. Todo método do repository recebe o `user_id` autenticado e filtra por ele. Operações em registros filhos (ex.: série) verificam a propriedade do registro pai (sessão).

O RLS continua ligado em todas as tabelas, sem políticas para clientes públicos, para bloquear o acesso pela API automática do Supabase.

## Garantia

Teste automático com dois usuários em toda rota que toca dados privados: o usuário A nunca lê nem altera dados do usuário B.

## Consequências

- (+) Repository simples em SQL; regras de acesso visíveis no código e testáveis.
- (−) Um filtro esquecido expõe dados; por isso os testes de isolamento são obrigatórios.

## Revisão

Reavaliar a opção B antes de abrir para usuários externos (Release 3).
