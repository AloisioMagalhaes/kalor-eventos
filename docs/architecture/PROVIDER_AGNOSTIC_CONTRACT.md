# Contrato provider-agnostic

## Propósito

Qualquer implementação deve respeitar este contrato, seja usando Supabase, outro PostgreSQL, outro storage, outro provedor de planilha ou outro provedor de IA.

## Portas

- IdentityPort: identifica ator, organizações e papéis; falhas normalizadas.
- EventRepository: create, getById, list e updateStatus sem expor SQL ou SDK.
- GarconRepository: findByNormalizedName, create, getById e update.
- ParticipationRepository: allocateSequence, create, getById e markClosed; sequência segura sob concorrência.
- MachineAssignmentRepository: getActive, assign, close e listHistory.
- ClosingRepository: getByParticipation, saveChecklist e complete; no máximo um fechamento.
- AuditPort: append; registros imutáveis com ator, timestamp, ação, entidade e resultado.
- TransactionPort: executa caso de uso com atomicidade; nunca simular transação no cliente.
- ClockPort e IdGeneratorPort: tornam horário e IDs determinísticos nos testes.
- ObjectStoragePort: put, getTemporaryUrl e delete sem conhecer bucket ou SDK.
- ExportPort: exportClosingSnapshot com referência externa, status e erro normalizado.
- ObservabilityPort: recordEvent, recordError e recordMetric sem depender de fornecedor.

## Invariantes

- Cada evento pertence a um escopo autorizado.
- Sequência é única dentro do evento.
- Garçom não é duplicado na mesma participação, salvo decisão explícita.
- Participação tem no máximo uma máquina ativa.
- Máquina física não tem alocações conflitantes quando a regra exigir exclusividade global.
- Participação tem no máximo um fechamento.
- Fechamento completo exige checklist válido.
- Auditoria é imutável e vinculada ao ator.
- Persistência usa timezone; conversão local fica na entrega.

## Erros

Converter erros externos para: validation-error, unauthenticated, forbidden, not-found, conflict, invariant-violation, provider-unavailable, timeout e unknown. A UI não depende de mensagens específicas de SDK.

## Troca de provedor

Trocar provedor exige novo adaptador, composição atualizada, testes de contrato e configuração documentada. Se exigir mudar domínio ou caso de uso, existe acoplamento indevido.
