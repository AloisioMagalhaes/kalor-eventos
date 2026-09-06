# Requisitos explícitos

Baseline derivado da arquitetura funcional fornecida. Itens OPEN exigem decisão antes da implementação correspondente.

## Funcionais

- REQ-001: usuário autenticado acessa somente o escopo autorizado.
- REQ-002: usuário autorizado cria e acompanha eventos.
- REQ-003: usuário autorizado cadastra ou localiza garçom.
- REQ-004: entrada registra participação, sequência e máquina inicial.
- REQ-005: trocas de máquina preservam histórico.
- REQ-006: fechamento inválido ou incompleto é rejeitado.
- REQ-007: mudanças críticas deixam auditoria.
- REQ-008: usuário autorizado exporta snapshot de fechamentos.
- REQ-009: operações críticas permanecem consistentes sob concorrência.

## Não funcionais

- NFR-001: regras de negócio não dependem de fornecedor.
- NFR-002: autorização é reforçada no armazenamento.
- NFR-003: timestamps persistidos têm timezone.
- NFR-004: erros externos são normalizados.
- NFR-005: há logs estruturados e rastreabilidade.
- NFR-006: mudanças usam PR e Conventional Commits.
- NFR-007: outro agente retoma lendo docs e issues.

## Decisões abertas

- OPEN-001: single-tenant ou multi-tenant?
- OPEN-002: um garçom pode aparecer mais de uma vez no mesmo evento?
- OPEN-003: exclusividade da máquina é por evento ou global?
- OPEN-004: quais papéis e ações existem?
- OPEN-005: offline completo está no MVP?
- OPEN-006: qual provedor inicial será usado em cada porta?
- OPEN-007: qual retenção de auditoria?
- OPEN-008: qual fuso operacional padrão?
- OPEN-009: exportação cria aba ou atualiza aba existente?

## Fora do escopo inicial

Pagamentos, folha, marketplace, billing, autoatendimento público, app mobile nativo, analytics avançado e múltiplos provedores de exportação antes do primeiro contrato estabilizar.
