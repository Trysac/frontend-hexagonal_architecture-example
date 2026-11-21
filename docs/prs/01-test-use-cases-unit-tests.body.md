## Qué cambia

Añade tests unitarios de la capa de aplicación en `functional-basic` y `functional-currying`:

- `createCourse`: guarda un curso válido y no llama al repositorio cuando el id, el título o la URL de la imagen no son válidos.
- `getAllCourses` y `getCourse`: devuelven lo que entrega el repositorio, incluido `null` cuando el curso no existe.

Usan el `CourseMother` que ya existía y un mock del `CourseRepository` (`tests/modules/courses/domain/CourseRepositoryMock.ts`). No se toca código de `src/`.

## Por qué

Hasta ahora solo había tests de los componentes. Estos muestran una de las ventajas de la arquitectura hexagonal que explica el README: los casos de uso se prueban sin React ni infraestructura, cambiando solo el adaptador del repositorio.

## Cómo se ha probado

- `npx jest --config=jest.config.js --ci`: 14 tests en `functional-basic` y 13 en `functional-currying`, todos en verde. `npm run lint` sin errores nuevos.
- Donde el resultado depende de que el título sea válido se usa un título fijo, porque `faker.lorem.sentence()` puede pasar de 100 caracteres (aprox. 1 de cada 4.600 veces).
- Comprobación inversa: al comentar `ensureCourseIsValid(course)` en `createCourse`, fallan los 4 tests de validación.
