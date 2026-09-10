# NovelaVisual — Contexto del proyecto

Novela visual de romance/misterio (Vaelyria/Vantia). Desarrollador solo. Este archivo es el punto de partida para cualquier sesión de Claude Code en esta carpeta — para detalle completo, siempre remitir a los documentos referenciados abajo antes de asumir nada.

## Estructura de carpetas

- `02_Proyecto-Unity/Vaelyria` — el proyecto de Unity + Naninovel. Todo el trabajo de código y scripts `.nani` pasa acá.
- `00_Documentacion/` — **solo de referencia**. Guion, fichas de personajes, listas de assets, presupuesto. No escribir ni modificar nada acá salvo que se pida explícitamente.

## Motor y stack técnico

- Unity 6000.3.23f1 LTS + Naninovel v1.21
- **Source Locale: español.** El proyecto lanza solo en español, pero debe quedar preparado para sumar idiomas después usando las herramientas de localización nativas de Naninovel (Naninovel → Tools → Localization) — no armar ninguna solución custom de traducción, y no hardcodear texto fuera de scripts/managed text de forma que rompa ese flujo.
- Guardado/carga con múltiples slots, con al menos una variable persistente **entre partidas** (no se resetea al empezar una nueva): `ruta_egis_completada`. Ver estructura narrativa en el documento de diseño, sección 2, antes de tocar el sistema de guardado. **En el código, esta variable lleva el prefijo `g_`** (`g_ruta_egis_completada`) — es el que exige Naninovel para que un valor persista entre partidas nuevas (variables sin ese prefijo se resetean como cualquier variable local de partida). Se inicializa de forma defensiva al principio de la Escena 1 (`@set g_ruta_egis_completada?=false`) para que exista siempre, incluso en la primerísima partida; se lee (todavía no se escribe en `true` en ningún lado) por primera vez en la Escena 2.3, en la variante de Hazel para 2ª partida en adelante.

## Ubicación de assets generados

Dentro de `02_Proyecto-Unity/Vaelyria/Assets/NaninovelData/Resources/Naninovel/` (convención por defecto de Naninovel — cualquier archivo puesto ahí queda disponible en los scripts sin necesidad de registrarlo a mano, la vía más simple para un desarrollador solo):

- `Backgrounds/MainBackground/` — fondos (nombres en `Lista-Fondos.md`). **Van dentro de la subcarpeta `MainBackground/`, no sueltos en `Backgrounds/`**: el actor de fondo único (`MainBackground`) resuelve sus recursos como `Backgrounds/<actorId>/<apariencia>`, igual que un personaje — dejarlos sueltos en `Backgrounds/` hace que Naninovel no encuentre ninguno (se ve un fondo rojo sólido, el placeholder de recurso faltante). En los scripts se siguen referenciando solo por nombre de apariencia (ej. `@back "Historia - Manana"`), sin mencionar `MainBackground/`.
- `Characters/` — sprites de personajes, una subcarpeta por personaje (nombres de expresión en `Lista-Expresiones-Sprites.md`). PNG con fondo transparente real (canal alfa) — el fondo blanco de generación se remueve con IOPaint antes de copiar el archivo acá, nunca se importa con fondo blanco sólido.
- `Audio/` — BGM y SFX (contenido en `Lista-Audio.md`); se pueden organizar en subcarpetas, ej. `Audio/BGM/`, `Audio/SFX/`
- `Voice/` — interjecciones de voz por heroína y emoción (`Lista-Voces.md`)
- `Text/` — documentos de managed text (se generan con la herramienta de Naninovel, Naninovel → Tools → Managed Text — no crear a mano)

Si un asset está en una subcarpeta, se referencia en los scripts con `/`: por ejemplo, un archivo en `Audio/BGM/TemaCampus.wav` se referencia como `BGM/TemaCampus`.

Los scripts `.nani` en sí pueden vivir en cualquier carpeta del proyecto (deben compartir una única raíz) ; sugerencia por defecto: `Assets/Scenario/`.

**Implementación de actores (Backgrounds/Characters)**: en `Configuration/BackgroundsConfiguration.asset` y `Configuration/CharactersConfiguration.asset`, el campo `Implementation` de `DefaultMetadata` (y de cualquier entrada por-actor en `Metadata`) debe ser `Naninovel.SpriteBackground` / `Naninovel.SpriteCharacter`. El proyecto arrancó con `Naninovel.PlaceholderBackground` / `Naninovel.PlaceholderCharacter` (la implementación de ejemplo que trae Naninovel por defecto, la misma que usan `Entry.nani`/`Title.nani`), que ignora cualquier sprite real y dibuja una figura/color genérico — si en algún momento se resetea esta configuración o se agrega un actor nuevo, hay que revisar que no vuelva a quedar en `Placeholder*`.

**Transición default entre escenas**: todo `@back` que abre una escena o cambia de ubicación (no los cambios de apariencia de personaje) usa la transición `LineReveal` con `time:1.5` — por ejemplo `@back "Universidad.LineReveal" time:1.5`. Usar este mismo valor por defecto en cualquier `@back` nuevo, salvo que se pida explícitamente otro efecto (ver lista completa de transiciones disponibles en `Naninovel.TransitionType`, `Packages/com.elringus.naninovel/Runtime/Transition/TransitionType.cs`).

**Tamaño y posición default de los sprites de personaje**: el arte generado viene en resolución mucho más alta que el `PixelsPerUnit` default de Naninovel (100), así que todo `@char` que muestra por primera vez a un personaje (primera aparición, no los cambios de apariencia posteriores del mismo personaje, que heredan el tamaño/posición ya seteado) lleva un `scale:`/`pos:` fijo según el personaje — **no hay un único valor global**, depende de a cuál de estos dos grupos pertenece:

- **Marr y Bibliotecaria**: `scale:0.6 pos:60,0` — ej. `@char Marr scale:0.6 pos:60,0`.
- **Resto de personajes** (Egis, Hazel, Vaelyr/Agnes, Extra Genérico Femenino/Masculino, y cualquier personaje con sprite que se agregue de acá en adelante): `scale:1 pos:60,-60` — ej. `@char Egis.Egis-seria scale:1 pos:60,-60`.

Personajes sin sprite (Protagonista, EstudiantesFondo, GrupoEstudiantes, GrupoPersonas — todos `NarratorCharacter`) no llevan `scale:`/`pos:`, no aplica. Cuando una escena necesita más de un personaje en pantalla a la vez (ej. Escena 2.4, Agnes + un Extra), se puede ajustar el eje X para separarlos manteniendo el mismo `scale:` y el mismo Y (`-60`) del grupo que corresponda — no es una excepción a la regla, es la misma composición con distinto encuadre horizontal.

**Protagonista como personaje sin sprite**: el protagonista no tiene carpeta en `Characters/` (no se muestra en pantalla, es POV). Sus líneas en los scripts (`Protagonista: texto`) igual necesitan una entrada en `CharactersConfiguration.asset` → `Metadata` con `Implementation: Naninovel.NarratorCharacter` (la implementación nativa de Naninovel para personajes sin presencia en escena, nunca intenta cargar sprite) y `DisplayName: '{Nombre}'` — Naninovel evalúa como expresión cualquier `DisplayName` envuelto en `{ }`, así que esto hace que el cuadro de diálogo muestre el nombre que haya elegido el jugador (variable `Nombre`, seteada vía `@input` en la Escena 1) en vez del literal "Protagonista". Se reevalúa en cada línea, así que también cubre pensamientos/asides del protagonista sin configuración aparte.

**Nombres ocultos hasta la revelación en escena (Egis, Hazel, Marr)**: estas tres heroínas/Marr muestran `"???"` como nombre de autor hasta que se presentan por su nombre dentro de la propia escena — mismo mecanismo de `DisplayName` atado a variable que Protagonista, pero con un valor inicial que cambia a mitad de escena en vez de fijo. `CharactersConfiguration.asset` → `Metadata` ya tiene las tres entradas (`Marr` → `'{NombreMarr}'`, `Egis` → `'{NombreEgis}'`, `Hazel` → `'{NombreHazel}'`). Patrón a seguir en los scripts (ya aplicado en Marr, Escena 1 — `Assets/Scenario/Prologo_Escena1.nani`):

- Justo antes de la primera aparición/línea del personaje: `@set NombreX="???"`.
- Justo después de la línea donde el personaje dice su propio nombre (esa línea todavía se muestra con "???" como hablante — recién la siguiente ya usa el nombre real): `@set NombreX="<Nombre revelado>"`.
- **Pendiente**: Egis (`@set NombreEgis="???"` al principio de la Escena 3 de `Prologo.md`, `@set NombreEgis="Egis"` en su línea "Egis.") y Hazel (`@set NombreHazel="???"` al principio de la Escena 2.3, `@set NombreHazel="Hazel"` cuando se presente) — ninguna de las dos escenas está escrita todavía como `.nani`; aplicar este patrón cuando se implementen.

**Paleta de color de la UI**: la interfaz por defecto de Naninovel (grises) se recoloreó a tonos azules. El color de acento/paneles elegido y confirmado por el usuario es el oficial del proyecto — usar este valor para cualquier panel o elemento de UI nuevo:

- **Hex exacto: `#0084FF`**
- RGBA (float, como lo serializa Unity): `{r: 0, g: 0.5176471, b: 1, a: 1}`
- Aplicado de forma consistente a todos los paneles que antes eran grises: `TextPanel` y `AuthorNamePanel` del cuadro de diálogo, y el resto de paneles equivalentes en `DefaultUI/*.prefab` y `ChoiceHandlers/*.prefab` (título, pausa, guardado, ajustes, tips, confirmación, etc.) — tanto en el paquete (`Packages/com.elringus.naninovel/Prefabs/`) como en la copia de proyecto de `Dialogue.prefab`.
- El override del cuadro de diálogo vive en `Assets/NaninovelData/Resources/Naninovel/TextPrinters/Dialogue.prefab` (GameObject `TextPanel`/`AuthorNamePanel` → componente `Image` → `Color`). Es la copia de proyecto que sobreescribe el `Dialogue.prefab` del paquete — los overrides de recursos de Naninovel van en `Resources/Naninovel/<PathPrefix>/`, no en `UI/` (esa carpeta es solo para menús: título, pausa, ajustes, etc., categoría separada de `TextPrinters/`).
- Nota de Unity: los cambios a este `.prefab` no se reflejan en una sesión de Play Mode ya iniciada — hay que parar y volver a darle Play después de editarlo.

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
