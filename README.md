# EMBAgame

Plan de estudios EMBA gamificado: etapas de toma de decisiones estratégicas en formato de juego.

## Estructura

- `index.html` — Mapa de ruta principal (menú de etapas, progreso del jugador).
- `juego.html` — Simulador corporativo continuo: diriges **Nimbus Dynamics**, de startup en un garaje a multinacional. Al primer arranque eliges el **sector industrial** (fintech, aeroespacial, biotech, logística automatizada o energías renovables) y toda la historia —producto, cliente, competidor, regulador, eventos— se narra desde esa industria. Botón 🔑 API IA (arriba a la derecha) para cambiar la clave de Mistral en cualquier momento. Los 100 temas EMBA se juegan como trimestres de la misma empresa con **módulos que se mezclan**: cada ciclo de 5 etapas rota Estrategia → Finanzas → Marketing → Operaciones, y la quinta es **combinada** (un tema de Capital Humano entrelazado con el tema ya visto de otro módulo ese ciclo — repetición espaciada deliberada; la decisión doble reúne ambos módulos y el briefing indica la etapa de origen del refuerzo), **KPIs heredados entre etapas** (arranque al 50%, evolución persistente en `emba_estado_juego`), 5 fases de crecimiento (garaje → scale-up → expansión → internacionalización → multinacional) y reglas de supervivencia: todos los KPIs > 35% y nunca 3 rondas seguidas < 40%. **Sin rebotes gratuitos**: cada fase aplica presión ambiental narrada (el garaje quema caja, la scale-up rompe procesos, la expansión te copian, la internacionalización erosiona la cohesión, la multinacional paga burocracia).
  - **Mecánicas**: dilemas de 3-4 opciones neutras (sin pistas de la solución), decisiones dobles que combinan dos módulos simultáneos, y slider de asignación de recursos con **impactos ocultos** orientado por informes de analistas contradictorios (gráfica SVG de ingresos esperados vs. tensión de caja, cotizaciones del CFO y de Estrategia que no coinciden).
  - **Didáctico**: briefing teórico previo por tema (con la "situación de la empresa" y su herencia de KPIs) e informe post-dilemas que conecta cada decisión con su marco académico.
  - **IA opcional**: clave API de Mistral (`emba_mistral_api_key`) genera cada trimestre con IA; sin ella, generador interno con bank de opciones y subdecisiones. La etapa se detecta automáticamente (`?etapa=N`, `emba_etapa_seleccionada` o mayor completada en `emba_progreso`).
- `etapa1.html` — Etapa 1 independiente (Ventaja Competitiva de Porter, Fintech de Microcréditos).

## Progreso

El progreso se guarda en `localStorage` bajo la clave `emba_progeso` (etapas completadas y puntuación global) y, si hay credenciales de GitHub configuradas (`emba_github_token`, `emba_github_sha`), se sincroniza con la nube al completar cada etapa.

## Añadir una nueva etapa

El motor `juego.html` contiene la base curricular completa `TEMAS_EMBA` (100 temas en 5 módulos: Estrategia, Finanzas, Marketing, Operaciones y Capital Humano) y genera los dilemas dinámicamente — con la clave API de Mistral guardada en `localStorage` (`emba_mistral_api_key`) los genera IA; sin ella, usa el generador interno. No hace falta un archivo por etapa. Para el archivo `etapa1.html` clásico, copia y modifica únicamente su bloque `CONFIG_ETAPA`.

El avance se registra en `emba_progreso` (incluye `kpis_empresa` y `fase_empresa` de la partida) (`etapas_completadas`, `puntuacion_global`, `ultima_etapa`, `fecha_actualizacion`) y puede descargarse como `emba_avance.json` desde la pantalla de desenlace.
