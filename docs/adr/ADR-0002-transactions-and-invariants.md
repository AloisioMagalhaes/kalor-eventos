# ADR-0002 — Transações e invariantes no servidor

- Status: accepted
- Data: 2026-09-06

Entrada, troca e fechamento alteram várias entidades. Operações independentes do frontend permitem dados parciais e falhas concorrentes.

A implementação deve usar TransactionPort e reforçar unicidade, estados e relacionamentos no armazenamento antes de construir telas completas.
