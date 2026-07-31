# Préstamos de equipos  Aplicación para Ingeniería de Software II

**Estudiante:** Rocío Cristel Quise Chura
**Ficha:** 23 — Confirmación de devolución

Miniaplicación estática para la actividad individual de aseguramiento de calidad de software. No usa base de datos ni servidor, guarda los registros en el navegador mediante `localStorage`.

## Mejora implementada (Ficha 23)

**Mejora asignada:** Solicitar confirmación antes de cambiar el estado de un préstamo a *Devuelto*.

**Criterios de aceptación:**
- Al confirmar, el préstamo cambia a estado **Devuelto**.
- Al cancelar, el préstamo conserva el estado **Activo**.

**Descripción técnica:** al hacer clic en "Registrar devolución", la aplicación muestra un cuadro de confirmación (`window.confirm`) con el equipo y el solicitante involucrados. Si el usuario acepta, el estado del préstamo cambia a `Devuelto` y se guarda en `localStorage`. Si el usuario cancela, no se modifica ningún dato y el préstamo permanece `Activo`. El cambio se implementó únicamente en `app.js`, dentro del listener de clic de la tabla de préstamos (`loanList`).

## Diseño visual

Se rediseñó `style.css` con una identidad propia inspirada en una **consola de inventario de laboratorio**: paleta verde bosque / naranja rótulo, tipografías Space Grotesk (títulos) + IBM Plex Sans (texto) + IBM Plex Mono (códigos), y una etiqueta de equipo con borde punteado que imita un rótulo físico de activo (`EQ-01`, `EQ-02`, etc.). No se modificó ningún `id` usado por `app.js`, por lo que la funcionalidad original y la mejora de la Ficha 23 siguen intactas.

## Funcionalidad inicial

- Registra un préstamo de un equipo disponible.
- Evita registrar datos incompletos, una fecha de devolución anterior a la fecha de préstamo y el préstamo simultáneo del mismo equipo.
- Muestra los préstamos y permite registrar la devolución.
- Conserva los datos del navegador mientras no se restablezcan desde la aplicación.

## Inicio rápido

1. Copie esta carpeta a su repositorio individual o use el repositorio base como plantilla.
2. Abra `index.html` en el navegador para probarla localmente.
3. Implemente únicamente la mejora asignada en su ficha.
4. Registre dos casos de prueba en la sección final de este README.
5. Publique la aplicación en GitHub Pages y proporcione los enlaces solicitados.

## Archivos principales

- `index.html`: estructura y controles de la aplicación.
- `style.css`: diseño visual.
- `app.js`: catálogo, registros, validaciones y almacenamiento local.

## Casos de prueba de mi mejora

| Caso | Datos de entrada / acción | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|
| CP-01: válido (confirmar) | Préstamo activo: Laptop Lenovo (EQ-01) — Ana Quispe, préstamo 27/07/2026, devolución prevista 30/07/2026. Acción: clic en "Registrar devolución" y luego clic en "Aceptar" en el cuadro de confirmación. | El estado del préstamo debe cambiar de Activo a Devuelto y reflejarse en la tabla. | Al aceptar el cuadro de confirmación ("¿Confirma que 'Laptop Lenovo' prestado a Ana Quispe fue devuelto?"), el estado en la tabla cambió de "Activo" a "Devuelto" y el equipo volvió a estar disponible en el selector. | Aprobado |
| CP-02: cancelación | Mismo préstamo activo: Laptop Lenovo (EQ-01) — Ana Quispe. Acción: clic en "Registrar devolución" y luego clic en "Cancelar" en el cuadro de confirmación. | El estado del préstamo debe conservarse como Activo, sin ningún cambio en la tabla ni en los datos guardados. | Al cancelar el cuadro de confirmación, el préstamo permaneció con estado "Activo" en la tabla y el equipo siguió marcado como no disponible; no se alteró ningún dato en `localStorage`. | Aprobado |

Ambos casos fueron verificados: (1) manualmente en el navegador siguiendo la interacción real de la interfaz, y (2) mediante una simulación automatizada del flujo con `jsdom` que confirma que `confirm()` en `true` deja el estado en `Devuelto` y en `false` lo conserva en `Activo`.

## Entrega

- URL del repositorio individual.
- URL pública de GitHub Pages.
- README actualizado con los dos casos de prueba.
