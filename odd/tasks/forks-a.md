# FORKS-A · Improve the example fork and prepare upstream PRs

Objective: small, easy-to-accept improvements to CodelyTV/frontend-hexagonal_architecture-example, ready as PRs from this fork.
Branch: `main` (docs) · `test/use-cases-unit-tests`, `ci/root-workflow` (PR branches)
Delivery: PR branches pushed to Trysac; PRs to CodelyTV opened only with Miguel's OK
Runner: `bash scripts/validate.sh`

## Specs
- S1 Sync the fork with the original before changing anything
- S2 Diagnose and choose 2–4 improvements the maintainer would accept
- S3 One branch and one PR per improvement, Spanish PR text, max 2 open PRs per repo
- S4 README section "Cambios en este fork", repo description and topics
- S5 Local validation with evidence and devlog (protocol §3–§4, ADR 0001)

## Tasks
| ID | Task | Specs | Route | Status | Commit |
|---|---|---|---|---|---|
| T1 | Sync fork main with upstream main (afc9845) | S1 | inline | done (already in sync) | afc9845 |
| T2 | Diagnosis: install, lint, tests, build, audit, upstream PRs | S2 | inline | done (docs/diagnostico.md) | |
| T3 | Use-case unit tests in functional-basic and functional-currying | S2, S3 | inline | done (+18 tests, 27 total) | 3cecbbc, a817def |
| T4 | Root CI workflow (functional examples; object-oriented after upstream PR #1) | S2, S3 | inline | done (local matrix run green) | 1a050d5..db06077 |
| T5 | Local validation script and evidence | S5 | inline | done (36 tests) | |
| T6 | PR texts in docs/prs | S3 | inline | done | |
| T7 | Open PR test/use-cases-unit-tests to CodelyTV | S3 | user | done (https://github.com/CodelyTV/frontend-hexagonal_architecture-example/pull/2) | a817def |
| T8 | Open PR ci/root-workflow to CodelyTV | S3 | user | done (https://github.com/CodelyTV/frontend-hexagonal_architecture-example/pull/3, from the single-commit branch ci/run-examples-from-root) | 2a30258 |
| T9 | README section, description and 8 topics | S4 | inline | done | |
| T10 | Independent reviews (code, security, architecture+spec) | S5 | delegated | done (docs/reviews/) | |
| T11 | Run Cypress e2e of object-oriented | S5 | user | needs-miguel (allow Cypress binary + browser, about 1.5 GB RAM; not required by the PRs) | |
