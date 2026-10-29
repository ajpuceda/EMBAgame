# EMBAgame

Plan de estudios EMBA gamificado: etapas de toma de decisiones estratégicas en formato de juego.

## Estructura

- `index.html` — Mapa de ruta principal (menú de etapas, progreso del jugador).
- `juego.html` — Motor unificado de 100 niveles: detecta la etapa automáticamente (`emba_etapa_seleccionada` o mayor etapa completada en `emba_progreso`), genera el escenario aleatoriamente (sector, contexto macro, evento detonante) a partir del tema EMBA de la base `TEMAS_EMBA`, y permite reintentar el mismo tema con un escenario nuevo tras una derrota.
- `etapa1.html` — Etapa 1 independiente (Ventaja Competitiva de Porter, Fintech de Microcréditos).

## Progreso

El progreso se guarda en `localStorage` bajo la clave `emba_progeso` (etapas completadas y puntuación global) y, si hay credenciales de GitHub configuradas (`emba_github_token`, `emba_github_sha`), se sincroniza con la nube al completar cada etapa.

## Añadir una nueva etapa

El motor `juego.html` contiene la base curricular completa `TEMAS_EMBA` (100 temas en 5 módulos: Estrategia, Finanzas, Marketing, Operaciones y Capital Humano) y genera los dilemas dinámicamente; no hace falta un archivo por etapa. Para el archivo `etapa1.html` clásico, copia y modifica únicamente su bloque `CONFIG_ETAPA`.
