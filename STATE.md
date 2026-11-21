# FORKS-A (frontend-hexagonal_architecture-example) — state

Last update: 2026-11-20 (two PR branches validated and ready; waiting for Miguel's OK to open them)
Phase: F1 — Improvements prepared as upstream PRs

## Waiting on Miguel
- Approve opening the PR `test/use-cases-unit-tests` to CodelyTV (since 2026-11-20; ref odd/tasks/forks-a.md T7)
- Approve opening the PR `ci/root-workflow` to CodelyTV (since 2026-11-20; ref odd/tasks/forks-a.md T8)
- Optional: allow running Cypress e2e locally (since 2026-11-20; ref odd/tasks/forks-a.md T11)

## Blocked
none

## Next step
- Miguel reviews docs/prs/ and, if OK, runs the `gh pr create` commands there
- After a PR is merged or closed: delete its branch and update "Cambios en este fork"

## Blocks
| Block | Content | Status | Verify |
|---|---|---|---|
| B1 | Sync, diagnosis, 2 PR branches, docs and validation | done | `bash scripts/validate.sh` |
| B2 | Open the 2 PRs to CodelyTV | done (#2 and #3 opened 2026-11-21 with Miguel's OK; waiting for the maintainer) | `gh pr list -R CodelyTV/frontend-hexagonal_architecture-example --author Trysac` |
