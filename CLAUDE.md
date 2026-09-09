
# NovelaVisual — Contexto del proyecto

Novela visual de romance/misterio (Vaelyria/Vantia). Desarrollador solo. Este archivo es el punto de partida para cualquier sesión de Claude Code en esta carpeta — para detalle completo, siempre remitir a los documentos referenciados abajo antes de asumir nada.

## Estructura de carpetas

- `02_Proyecto-Unity/` — el proyecto de Unity + Naninovel. Todo el trabajo de código y scripts `.nani` pasa acá.
- `00_Documentacion/` — **solo de referencia**. Guion, fichas de personajes, listas de assets, presupuesto. No escribir ni modificar nada acá salvo que se pida explícitamente.

## Motor y stack técnico

- Unity 6000.3.23f1 LTS + Naninovel v1.21
- **Source Locale: español.** El proyecto lanza solo en español, pero debe quedar preparado para sumar idiomas después usando las herramientas de localización nativas de Naninovel (Naninovel → Tools → Localization) — no armar ninguna solución custom de traducción, y no hardcodear texto fuera de scripts/managed text de forma que rompa ese flujo.
- Guardado/carga con múltiples slots, con al menos una variable persistente **entre partidas** (no se resetea al empezar una nueva): `ruta_egis_completada`. Ver estructura narrativa en el documento de diseño, sección 2, antes de tocar el sistema de guardado.

## Ubicación de assets generados

Dentro de `02_Proyecto-Unity/Assets/Resources/Naninovel/` (convención por defecto de Naninovel — cualquier archivo puesto ahí queda disponible en los scripts sin necesidad de registrarlo a mano, la vía más simple para un desarrollador solo):

- `Backgrounds/` — fondos (nombres en `Lista-Fondos.md`)
- `Characters/` — sprites de personajes, una subcarpeta por personaje (nombres de expresión en `Lista-Expresiones-Sprites.md`)
- `Audio/` — BGM y SFX (contenido en `Lista-Audio.md`); se pueden organizar en subcarpetas, ej. `Audio/BGM/`, `Audio/SFX/`
- `Voice/` — interjecciones de voz por heroína y emoción (`Lista-Voces.md`)
- `Text/` — documentos de managed text (se generan con la herramienta de Naninovel, Naninovel → Tools → Managed Text — no crear a mano)

Si un asset está en una subcarpeta, se referencia en los scripts con `/`: por ejemplo, un archivo en `Audio/BGM/TemaCampus.wav` se referencia como `BGM/TemaCampus`.

🔶 Los scripts `.nani` en sí pueden vivir en cualquier carpeta del proyecto (deben compartir una única raíz) — falta decidir dónde exactamente; sugerencia por defecto: `Assets/Scenario/`.

## Documentos de referencia (dentro de `00_Documentacion/`)

Completar las rutas relativas exactas:

| Documento                                                                   | Contenido                                                                                                                                                  |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `00_Documentacion/Guion/Biblia-del-Mundo.md`                              | Reglas del mundo, geografía (la ciudad es una isla, alcance de la trama limitado a ella), facciones, tono                                                 |
| `00_Documentacion/Diseno-General/documento-diseno-novela-visual.md`       | Diseño completo: estructura narrativa de rutas/finales, requerimientos de arte/audio/técnicos, plataformas (Android/iOS + PC/Steam), plan de producción |
| `00_Documentacion/Diseno-General/plan-de-trabajo-novela-visual.md`        | Lista de tareas por fase — el prólogo (Fase 1) corresponde a la tarea 15 en adelante                                                                     |
| `00_Documentacion/Guion/Fichas-Personajes/Protagonista.md`                | Ficha del protagonista (nombre por defecto:**Leo**, personalizable vía variable)                                                                    |
| `00_Documentacion/Guion/Fichas-Personajes/Heroina-A.md`                   | Ficha de Egis (arquetipo Kuudere)                                                                                                                          |
| `00_Documentacion/Guion/Fichas-Personajes/Heroina-B.md`                   | Ficha de Agnes/Vaelyr (arquetipo dandere en su forma real)                                                                                                 |
| `00_Documentacion/Guion/Fichas-Personajes/Heroina-C.md`                   | Ficha de Hazel (arquetipo Dandere)                                                                                                                         |
| `01_Assets/Arte/Apariencia-Fisica-Personajes.md`                          | Tabla de referencia física de las 4 fichas de arriba                                                                                                      |
| `00_Documentacion/Guion/Personajes-Secundarios/Personajes-Secundarios.md` | Personajes menores (Prof. Marr, Bibliotecaria, extras genéricos)                                                                                          |
| `00_Documentacion/Guion/Prologo.md`                                       | Guion final del prólogo (fuente de texto para los scripts`.nani`)                                                                                       |
| `01_Assets/Arte/Fondos/Lista-Fondos.md`                                   | Fondos necesarios, con prompts de generación usados                                                                                                       |
| `01_Assets/Arte/Sprites/Lista-Expresiones-Sprites.md`                     | Sprites/expresiones necesarios por personaje, con prompts de generación usados                                                                            |
| `01_Assets/Audio/Lista-Audio.md`                                          | BGM y SFX del prólogo                                                                                                                                     |
| `01_Assets/Audio/Voces/Lista-Voces.md`                                    | Mapeo de interjecciones de voz por heroína y emoción                                                                                                     |
| `05_Legal/Creditos.md`                                                    | Atribuciones obligatorias/voluntarias de recursos de terceros — revisar antes de tocar la pantalla de créditos                                           |
| `00_Documentacion/Gestion/PresupuestoInvertido.xlsx`                      | Registro de gastos reales del proyecto                                                                                                                     |

## Convenciones del guion (cómo leer `Prologo.md`)

- `**PERSONAJE**` seguido de una línea es diálogo hablado — el nombre en negrita es el tag de personaje para Naninovel, no se muestra al jugador.
- Texto corrido sin tag de personaje es narración en primera persona del protagonista.
- *(texto entre paréntesis en cursiva)* antes de una línea es una acotación de tono/actuación — informa qué sprite/animación usar, generalmente no se muestra como texto de juego salvo decisión de UI en contrario.
- *[Nota de arte/dirección: ...]* y *[Nota técnica para Naninovel: ...]* entre corchetes **no son texto de juego** — son instrucciones de implementación (qué sprite usar, cómo armar un choice, qué variable setear). Traducir a comandos reales, no mostrar al jugador.
- Los bloques `> **Elección**` marcan puntos de decisión del jugador — algunos son de ruta (afectan flags persistentes) y otros son "de sabor" (no generan ninguna variable, solo dan textura al personaje) — cada uno lo aclara en su propia nota técnica.
- Notas de versión ("Borrador N", checklist de consistencia) son andamiaje de escritura, no tienen equivalente en el juego — se descartan al implementar.

## Política de contenido

- Clasificación madura, **sin desnudos ni contenido explícito** — intimidad mediante elipsis/fundido a negro. Tenerlo en cuenta en cualquier CG o escena que se implemente.

## Nombres de assets

No inventar nombres de archivo de sprites/fondos/audio — usar exactamente los que figuran en `Lista-Fondos.md`, `Lista-Expresiones-Sprites.md` y `Lista-Audio.md`. Si un asset que el guion necesita no aparece en esas listas, avisar en vez de asumir un nombre.
