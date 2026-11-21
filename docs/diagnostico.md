# Diagnóstico del repo de ejemplos (2026-11-20)

Hecho sobre `upstream/main` = `afc9845` (último cambio en CodelyTV: abr-2023), Windows 11, Node 22.14, npm 10.9, instalación limpia con `npm ci` y `CYPRESS_INSTALL_BINARY=0`.

| Ejemplo | `npm ci` | `npm run lint` | Jest | `npm run build` |
|---|---|---|---|---|
| `functional-basic` | ok (≈40 s) | 0 errores, 3 avisos | 5/5 | ok (28 s, con avisos) |
| `functional-currying` | ok | 0 errores, 2 avisos | 4/4 | no medido |
| `object-oriented` | ok | 2 errores (`import/no-unresolved`) | 0 tests: 2 suites no arrancan | no medido |

`npm audit`: ≈103 avisos por ejemplo (7 críticos, 50 altos), casi todos de `react-scripts` 5 (Create React App, sin mantenimiento) y sus dependencias de desarrollo.

## Hallazgos y decisión

| # | Hallazgo | Decisión |
|---|---|---|
| H1 | Los workflows están en `<ejemplo>/.github/workflows`; GitHub solo lee la raíz, así que nunca se ejecutaron (0 ejecuciones en Actions) aunque el README dice que sí. | **PR** `ci/root-workflow` |
| H2 | No hay tests de los casos de uso (`createCourse`, `getAllCourses`, `getCourse`), solo de componentes. | **PR** `test/use-cases-unit-tests` (ejemplos funcionales) |
| H3 | `object-oriented`: imports rotos en los tests y `CourseTitle.isValid` invertido. | **No se propone:** el PR #1 abierto (feb-2026, de otra persona) ya lo arregla. Duplicarlo sería ruido. Por eso tampoco se añaden tests de casos de uso a `object-oriented` ni entra en la matriz de CI hasta que se integre. |
| H4 | `useCourseForm` en los ejemplos funcionales: el `catch` vuelve a lanzar dentro de una promesa, así que el estado `Error` nunca se alcanza. | **No se propone:** también lo cubre el PR #1. |
| H5 | Vulnerabilidades de `react-scripts` 5. | **No se propone:** la solución es migrar de herramienta (Vite u otra), un cambio de enfoque que el mantenedor difícilmente aceptaría en un repo de curso. |
| H6 | `npm test` en `object-oriented` usa `--watch` y se queda esperando en una terminal sin git. | **No se propone:** decisión didáctica de la plantilla; poco valor. |
| H7 | En Windows con `core.autocrlf=true`, Prettier marca todas las líneas (CRLF). | Solo afecta al entorno local; se resolvió con `core.autocrlf=false` en el clon. Un `.gitattributes` con `eol=lf` lo evitaría, pero es un cambio de configuración global del repo: queda como idea, no como PR. |
