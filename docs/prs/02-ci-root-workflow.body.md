## Qué cambia

Añade `.github/workflows/ci.yml` en la raíz con una matriz sobre los ejemplos `functional-basic` y `functional-currying`. Para cada uno: `npm ci`, `npm run lint` y los tests unitarios de Jest, en Node 22, con el token en solo lectura (`permissions: contents: read`).

## Por qué

GitHub solo ejecuta los workflows de `.github/workflows` en la raíz. Los de cada ejemplo nunca se han ejecutado en este repositorio, aunque el README dice que los tests y el lint corren en cada push.

Los workflows de cada carpeta se dejan como están: sirven si alguien copia un ejemplo como proyecto independiente.

`object-oriented` se queda fuera de la matriz (con un comentario) porque hoy sus tests no arrancan en `main`: el import de `CoursesContext` está roto y la validación de `CourseTitle` está invertida. Lo arregla el PR #1, de otra persona. Cuando se integre, basta con añadir una línea a la matriz.

## Cómo se ha probado

- Los pasos de la matriz se han ejecutado en local con instalación limpia (`npm ci`) y Node 22: los dos ejemplos pasan lint y tests (5 y 4 tests).
- El YAML se ha validado con `yaml-lint`.
