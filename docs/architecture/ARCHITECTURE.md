# Arquitetura

## Objetivo

Controlar planejamento, entrada de garçons, alocação e troca de máquinas, fechamento individual, auditoria e exportação.

## Camadas

1. Domain: entidades, invariantes, value objects e eventos de domínio; sem framework ou fornecedor.
2. Application: casos de uso, autorização e orquestração transacional por portas.
3. Ports: interfaces para persistência, identidade, relógio, IDs, storage, exportação e observabilidade.
4. Adapters: implementações concretas de banco, auth, storage, planilha e telemetria.
5. Delivery: UI, HTTP, jobs e comandos; traduz entrada externa para comandos e DTOs.
6. Infrastructure: composição, configuração, migrations, deploy e telemetria.

## Dependências permitidas

- Domain não depende de Application, Delivery ou Adapters.
- Application depende de Domain e Ports.
- Adapters implementam Ports e podem usar SDKs.
- Delivery chama Application, nunca tabelas diretamente.
- Provedores são escolhidos somente na composição.

## Casos críticos

Entrada: autorização -> localizar/criar garçom -> alocar sequência -> criar participação -> máquina ativa -> auditoria -> estado final.

Troca: autorização -> bloquear participação e alocação atual -> validar nova máquina -> encerrar anterior -> criar nova -> auditoria -> histórico.

Fechamento: autorização -> validar checklist no servidor -> criar/atualizar fechamento único -> marcar participação -> auditoria.

Os três fluxos devem ser operações transacionais, não uma sequência de chamadas independentes no frontend.

## Modelo conceitual

Event, Responsible, Garcon, EventParticipation, MachineAssignment, Closing e AuditEntry.

## Segurança

O escopo recomendado é organization -> members -> resources. Autorização é verificada no caso de uso e reforçada pelo armazenamento. A auditoria é append-only. Fotos são privadas por padrão. Tokens externos nunca ficam no cliente.

## Consistência

O armazenamento reforça unicidade, estados e relacionamentos; casos de uso reforçam autorização e transições. Ver o contrato em PROVIDER_AGNOSTIC_CONTRACT.md.
