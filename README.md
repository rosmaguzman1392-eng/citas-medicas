# citas-medicas

Taller de pruebas de software · Spring Boot 4.0.0 · Java 25 · Maven · H2

## Reglas de negocio
- Un profesional no puede tener dos citas en el mismo horario (restricción UNIQUE profesional/fecha_hora).
- Máximo 20 citas diarias por profesional.
- POST /api/citas → 201 creada · 409 conflicto de horario/cupo · 400 datos inválidos.

## Requisitos
JDK 25 · IntelliJ IDEA 2025.2+ · Google Chrome (pruebas UI) · Git/GitHub (CI).

## Ejecución
.\mvnw.cmd spring-boot:run → http://localhost:8080/citas.html

## Pruebas
- .\mvnw.cmd test → 13 pruebas (el grupo `ui` se excluye por configuración de Surefire).
- .\mvnw.cmd verify → pruebas + reporte JaCoCo (umbral 70 % de líneas) en target/site/jacoco/index.html.
- ReservaUITest (etiqueta `ui`): se ejecuta individualmente desde IntelliJ; Chrome headless.

## CI
.github/workflows/ci.yml ejecuta `mvn -B verify` en push/pull_request y publica el artefacto `reporte-jacoco`.
