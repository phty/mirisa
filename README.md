# Simulador MIR 2026

Simulador de examen tipo test para la preparación del **MIR** (examen de médico residente en España), con **500 preguntas** de alto rendimiento repartidas por 28 especialidades siguiendo el peso real del examen. Casos clínicos estilo MIR, corrección con la fórmula oficial (aciertos − fallos/3), estadísticas por especialidad y explicación razonada de cada respuesta.

## 🌐 Web (GitHub Pages)
Una vez activadas las Pages del repo, la app está disponible en:
`https://phty.github.io/mirisa/`

Es una app autónoma (un solo `index.html`): funciona sin conexión y guarda el progreso en el navegador.

## Contenido del repo
- `index.html` — la aplicación completa del simulador (lista para GitHub Pages).
- `preguntas_mir_2026.json` — el banco de 500 preguntas (reutilizable). Estructura de cada pregunta:
  `especialidad, tema, dificultad, enunciado, opciones[4], correcta (0-3), explicacion, perla`.
- `lovable_prompt.txt` — prompt listo para reconstruir la app en Lovable (React + Supabase).
- `COMO_PUBLICAR.md` — guía de publicación (hosting estático y Lovable).

## Modos de examen
Simulacro oficial (200 con cronómetro), examen completo (500), por especialidad y personalizado, con modo estudio (corrección inmediata), revisión con filtros y búsqueda, modo claro/oscuro y diseño móvil-first.

## Aviso
Herramienta de estudio generada con IA. Material de práctica que puede contener errores o simplificaciones; no sustituye a los temarios oficiales ni a las guías clínicas y no constituye consejo médico. Verifica siempre en fuentes oficiales.
