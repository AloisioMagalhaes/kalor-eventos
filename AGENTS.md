# Instruções para agentes

## Antes de alterar

1. Leia README.md, AGENTS.md, docs/AI_HANDOFF.md e a documentação da área.
2. Consulte requisitos, riscos e critérios relacionados.
3. Não invente decisões marcadas como OPEN.
4. Não acople o domínio a um fornecedor específico.
5. Se mudar uma decisão arquitetural, crie ou atualize um ADR.

## Durante

- Faça mudanças pequenas e rastreáveis.
- Preserve contratos ou documente quebras.
- Valide autorização no caso de uso e no armazenamento.
- Use transações para operações que alteram mais de uma entidade.
- Normalize erros externos.
- Não adicione credenciais, dados pessoais reais ou arquivos de ambiente.

## Antes de concluir

- Execute as verificações disponíveis.
- Atualize documentação, riscos e critérios quando necessário.
- Informe arquivos alterados, verificações e pendências.
- Não declare pronto sem evidência de aceite.

Um agente sem histórico deve conseguir continuar lendo a documentação acima e a issue vinculada ao Project.
