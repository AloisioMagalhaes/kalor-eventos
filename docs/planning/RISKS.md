# Registro de riscos

| ID | Risco | Probabilidade | Impacto | Mitigação | Gatilho |
|---|---|---:|---:|---|---|
| R-001 | RLS permite acesso fora do escopo | média | crítico | matriz de autorização, políticas completas e testes negativos | recurso de outro escopo acessado |
| R-002 | Sequência duplicada sob concorrência | alta | alto | constraint única e alocação transacional | duas entradas simultâneas |
| R-003 | Máquina atribuída em dois lugares | média | alto | índice de ativa e lock na troca | trocas simultâneas |
| R-004 | Falha deixa dados parciais | alta | alto | TransactionPort e operação atômica | falha entre gravações |
| R-005 | OAuth expõe token | média | crítico | server-side, secrets manager e escopo mínimo | token em log/payload |
| R-006 | Domínio acoplado ao fornecedor | média | alto | portas, adaptadores e testes de contrato | regra importa SDK |
| R-007 | Agente inventa decisão OPEN | alta | alto | ADR e bloqueio de itens abertos | implementação contraditória |
| R-008 | Offline cria conflitos | média | alto | retirar do MVP ou definir outbox/conflitos | alteração divergente |
| R-009 | Auditoria é alterada | baixa | alto | append-only e políticas sem update/delete | histórico modificado |
| R-010 | Horário diverge entre ambientes | média | médio | TIMESTAMPTZ, ClockPort e testes | fechamento perto da meia-noite |
| R-011 | Exportação duplica dados | média | médio | snapshot versionado e idempotency key | exportação repetida |
| R-012 | Trabalho depende de contexto privado | média | alto | AI_HANDOFF, docs e issues | agente não retoma |

Novos riscos recebem ID, probabilidade, impacto, mitigação e gatilho.
