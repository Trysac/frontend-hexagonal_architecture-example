# PR preparado · `ci/root-workflow`

- **Estado:** needs-miguel (aprobar antes de abrir el PR hacia CodelyTV)
- **Base:** `CodelyTV/frontend-hexagonal_architecture-example:main` · **Head:** `Trysac:ci/root-workflow` (commits `1a050d5`, `e7d61ce`, `999ea05`, `68174fa`, `db06077`; diff neto: solo `.github/workflows/ci.yml`)
- **Nota:** `object-oriented` queda fuera de la matriz hasta que se integre el PR #1 del original (de otra persona), que arregla sus tests.
- **Comando para abrirlo** (solo con el OK de Miguel):

```bash
gh pr create -R CodelyTV/frontend-hexagonal_architecture-example --base main --head Trysac:ci/root-workflow \
  --title "ci: run lint and unit tests for every example from the repository root" --body-file docs/prs/02-ci-root-workflow.body.md
```

## Título
`ci: run lint and unit tests for every example from the repository root`

## Cuerpo
Ver [`02-ci-root-workflow.body.md`](02-ci-root-workflow.body.md) (se pega tal cual).
