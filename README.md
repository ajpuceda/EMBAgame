# EMBAgame

Plan de estudios EMBA gamificado: etapas de toma de decisiones estratégicas en formato de juego.

## Estructura

- `index.html` — Mapa de ruta principal (menú de etapas, progreso del jugador).
- `juego.html` — Motor unificado de 100 niveles con experiencia completa: ventana de bienvenida explicando la herramienta, clave API de Mistral opcional (genera teoría, dilemas y escenarios con IA; con fallback al generador interno), pantalla de briefing teórico antes de cada etapa, dilemas con dos mecánicas (decisión ejecutiva y asignación de recursos con slider y proyección de KPIs en vivo), informe didáctico post-dilemas que conecta cada decisión con su marco teórico, y registro de avance exportable como `emba_avance.json`. Detecta la etapa automáticamente (`emba_etapa_seleccionada` o mayor etapa completada en `emba_progreso`).
- `etapa1.html` — Etapa 1 independiente (Ventaja Competitiva de Porter, Fintech de Microcréditos).

## Progreso

El progreso se guarda en `localStorage` bajo la clave `emba_progeso` (etapas completadas y puntuación global) y, si hay credenciales de GitHub configuradas (`emba_github_token`, `emba_github_sha`), se sincroniza con la nube al completar cada etapa.

## Añadir una nueva etapa

El motor `juego.html` contiene la base curricular completa `TEMAS_EMBA` (100 temas en 5 módulos: Estrategia, Finanzas, Marketing, Operaciones y Capital Humano) y genera los dilemas dinámicamente — con la clave API de Mistral guardada en `localStorage` (`emba_mistral_api_key`) los genera IA; sin ella, usa el generador interno. No hace falta un archivo por etapa. Para el archivo `etapa1.html` clásico, copia y modifica únicamente su bloque `CONFIG_ETAPA`.

El avance se registra en `emba_progreso` (`etapas_completadas`, `puntuacion_global`, `ultima_etapa`, `fecha_actualizacion`) y puede descargarse como `emba_avance.json` desde la pantalla de desenlace.
