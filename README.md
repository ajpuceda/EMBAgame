# EMBAgame

Plan de estudios EMBA gamificado: etapas de toma de decisiones estratégicas en formato de juego.

## Estructura

- `index.html` — Mapa de ruta principal (menú de etapas, progreso del jugador).
- `etapa1.html` — Etapa 1: Ventaja Competitiva de Porter y Diferenciación (Fintech de Microcréditos).

## Progreso

El progreso se guarda en `localStorage` bajo la clave `emba_progeso` (etapas completadas y puntuación global) y, si hay credenciales de GitHub configuradas (`emba_github_token`, `emba_github_sha`), se sincroniza con la nube al completar cada etapa.

## Añadir una nueva etapa

Copia `etapa1.html` y modifica únicamente el bloque `CONFIG_ETAPA` del `<script>`: número de etapa, tema académico, sector, contexto macroeconómico, evento detonante, dilemas y lecciones de victoria.
