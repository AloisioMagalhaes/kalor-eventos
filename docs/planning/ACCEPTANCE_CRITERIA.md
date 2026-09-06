# Critérios de aceitação

## AC-001 — Isolamento

Dado usuário sem vínculo com o escopo, quando tenta consultar, alterar ou fechar, então recebe forbidden e nada muda.

## AC-002 — Entrada consistente

Dado evento e garçom válidos, quando a entrada é confirmada, então participação, sequência, máquina ativa e auditoria persistem como uma operação lógica.

## AC-003 — Sequência concorrente

Dadas duas entradas simultâneas no evento, então cada uma recebe sequência diferente e não há registros parciais.

## AC-004 — Troca

Dada participação com máquina ativa, quando troca válida é confirmada, então a anterior encerra, a nova fica ativa, motivo e histórico são preservados.

## AC-005 — Conflito

Dada máquina já ativa conforme a regra, quando é usada em nova troca, então retorna conflict e a anterior continua ativa.

## AC-006 — Fechamento único

Dada participação, quando fechamento é confirmado duas vezes, então existe no máximo um fechamento e a repetição segue a política de idempotência definida.

## AC-007 — Checklist

Dado item obrigatório pendente, quando tenta concluir, então servidor rejeita e informa a pendência.

## AC-008 — Auditoria

Dada mudança crítica aprovada, então existe entrada append-only com ator, ação, entidade, horário e resultado.

## AC-009 — Exportação

Dado snapshot já exportado, quando a mesma exportação é solicitada, então não duplica linhas sem nova versão explícita.

## AC-010 — Retomada

Dado agente sem histórico, quando lê README.md, AGENTS.md, AI_HANDOFF.md e issue vinculada, então identifica escopo, decisão, riscos, critérios e próximo passo.
