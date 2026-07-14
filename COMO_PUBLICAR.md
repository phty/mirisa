# Cómo publicar el Simulador MIR (Lovable, hosting y móvil)

Tienes dos entregables:
- **`simulador_mir_2026.html`** — la app completa en un solo archivo (funciona sin internet).
- **`preguntas_mir_2026.json`** — las 500 preguntas (el activo valioso y reutilizable).

---

## ⚠️ ¿Puedo (Claude) publicar en Lovable por ti?
**No directamente.** No tengo integración con Lovable, así que no puedo crear el proyecto ni desplegarlo en tu cuenta. Lo que sí he hecho:
- Optimizar la app para móvil (abajo).
- Dejarte un **prompt listo para pegar** en Lovable y los pasos exactos.
- Puedo, si quieres, **desplegar el HTML tal cual en una URL pública** (Cloudflare Pages) — solo dímelo.

---

## Recomendación rápida
| Objetivo | Mejor opción |
|---|---|
| Tenerlo online y verse bien en móvil **ya**, gratis | **Hosting estático** (Cloudflare Pages / Netlify / GitHub Pages) con el HTML actual |
| Seguir iterando el diseño, añadir **cuentas de usuario, guardar progreso en la nube, ranking, monetizar** | **Lovable** (React + Supabase) usando el JSON como fuente de datos |

Mi consejo: publica **hoy** el HTML en un hosting estático (5 minutos) y, en paralelo, monta la versión "producto" en Lovable con el prompt de abajo. El JSON de 500 preguntas te sirve para ambas.

---

## Opción A — Publicar el HTML tal cual (lo más rápido)
El archivo es autónomo; cualquier hosting estático vale.

**Netlify Drop (sin cuenta técnica):**
1. Entra en https://app.netlify.com/drop
2. Arrastra `simulador_mir_2026.html` (renómbralo antes a `index.html`).
3. Te da una URL pública al instante. Ábrela en el móvil.

**GitHub Pages / Cloudflare Pages / Vercel:** sube el archivo como `index.html` a un repo y activa Pages. Mismo resultado.

> Ventaja: es una PWA offline de facto, carga instantánea, cero backend. Limitación: el progreso se guarda solo en ese dispositivo (localStorage).

---

## Opción B — Llevarlo a Lovable (versión "producto")
Lovable construye React + Tailwind + shadcn (móvil-first por defecto) sobre Supabase. La estrategia correcta **no es subir el HTML**, sino darle el **JSON de preguntas** + un prompt claro y dejar que Lovable genere la UI.

### Pasos
1. Entra en https://lovable.dev y crea un proyecto nuevo.
2. Pega el **prompt** de `lovable_prompt.txt` (en esta carpeta) en el chat inicial.
3. Cuando tenga el esqueleto, conéctalo a **GitHub** (botón *GitHub → Connect*). Esto crea un repositorio.
4. En ese repositorio, sube el archivo **`preguntas_mir_2026.json`** dentro de la carpeta `public/` con el nombre `preguntas.json` (arrástralo en la web de GitHub → *Add file → Upload files*).
5. Vuelve a Lovable y escribe: *"Carga las preguntas desde `/preguntas.json` (fetch en el arranque) en lugar de los datos de ejemplo. Son 500 objetos con los campos: especialidad, tema, dificultad, enunciado, opciones (array de 4), correcta (índice 0-3), explicacion, perla."*
6. Itera el diseño con frases cortas ("hazlo móvil-first", "añade modo oscuro", "guarda el progreso con Supabase").

### (Opcional, recomendado para "producto") Supabase
Para cuentas de usuario y guardar progreso/estadísticas entre dispositivos:
- Activa la integración **Supabase** en Lovable.
- Pídele: *"Crea una tabla `preguntas` e impórtalas desde el JSON; crea `intentos` (user_id, pregunta_id, respuesta, acierto, fecha) y guarda cada respuesta; añade login por email."*

---

## Móvil
El `simulador_mir_2026.html` ya está optimizado para móvil: viewport correcto, botones grandes en rejilla 2×2 al alcance del pulgar, cabecera y tablas adaptadas, sin scroll horizontal, y toques sin retardo. Pruébalo en tu teléfono con cualquiera de las opciones de hosting de arriba (en `file://` local algunos navegadores móviles limitan funciones; mejor con una URL http).
