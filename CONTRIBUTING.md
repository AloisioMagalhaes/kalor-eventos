# Contribuindo

## Gitflow

- main: produção e releases estáveis.
- develop: integração do próximo incremento.
- feature/<id>-<slug>: funcionalidade ou requisito.
- fix/<id>-<slug>: correção não urgente.
- hotfix/<id>-<slug>: correção urgente derivada de main.
- release/<versão>: preparação de release.
- chore/<id>-<slug>: manutenção, documentação ou infraestrutura.

Branches de trabalho partem de develop. Features, fixes e chores entram em develop. Releases entram em main e retornam para develop. Hotfixes entram em main e são propagados para develop.

## Conventional Commits

Formato: type(scope): descrição imperativa curta

Tipos: feat, fix, docs, refactor, test, build, ci, chore, perf, revert.

Exemplos:

    feat(events): define contrato de criação de evento
    docs(architecture): registra limite entre domínio e adaptadores
    test(entry): cobre alocação concorrente de sequência

Breaking changes usam ! no tipo ou uma seção BREAKING CHANGE.

## Pull requests

Toda PR deve apontar para uma issue ou requisito, explicar o comportamento alterado, listar riscos e decisões, incluir testes ou justificativa, atualizar documentação quando necessário e passar pelas verificações. Use squash merge; o título da PR segue Conventional Commits.

## Pronto

Uma mudança está pronta quando o critério de aceitação foi demonstrado, riscos foram tratados e outro agente consegue retomar o trabalho.
