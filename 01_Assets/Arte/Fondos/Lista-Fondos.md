# Lista de Fondos — Backgrounds Necesarios

> Documento vivo, en el mismo espíritu que `Lista-Expresiones-Sprites.md`: se actualiza cada vez que un guion nuevo menciona una locación que necesita fondo propio. Sirve para armar el pedido de arte de las tareas 11 (fondos del prólogo) y 22 (fondos de cada bloque de ruta) sin tener que releer guiones enteros.
>
> El documento de diseño (sección 4) estima 15-25 fondos únicos para todo el juego, reutilizables con variaciones de luz (día/noche/clima). Donde dos escenas comparten locación, lo marco como reutilización en vez de fondo nuevo.

## Prólogo

| Fondo                                                              | Dónde se usa                                                      | Notas                                                                                                                                                                                                                                                                                                                                                                                                      |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Aula de Historia y Arqueología (llena, de día)                   | Escena 1                                                           | Interior de un edificio con fachada de castillo medieval, pero luce impecable/nuevo por dentro (ver Biblia del Mundo, sección 4).                                                                                                                                                                                                                                                                         |
| Aula de la electiva de arte (vacía, hora de almuerzo)             | Escena 2.3                                                         | 🔶 Ya no es el mismo fondo que el de Escena 1 — Hazel estudia Medicina, no Arqueología, así que esta aula es una locación distinta (la de la electiva de arte que comparte con el protagonista). Puede reutilizar el mismo estilo general de aula que la Escena 1 (mismo tipo de edificio, mismo criterio de "impecable pese a la antigüedad"), pero como locación es un fondo aparte.               |
| Universidad Pública de Vantia — fachada exterior (vista general) | Aún no vinculada a una escena específica                         | Diseño y prompt ya definidos (ver conversación). Útil como plano de establecimiento antes de cortar a un interior — por ejemplo, al abrir la Escena 1. Incluye el estanque con puente frente a la entrada; ver también la entrada de la universidad, más abajo. La terraza de la torre este es, confirmado, la misma terraza donde Agnes descansa durante las electivas de Hazel (ver Heroina-B.md). |
| Biblioteca central — estanterías                                 | Escena 2.1 (tarde) y Escena 3 (última hora de la tarde, luz baja) | Un solo fondo de estanterías, con dos variantes de iluminación según el momento del día — decisión confirmada. Ya no hace falta un fondo aparte para el "mostrador de referencia" de 2.1.                                                                                                                                                                                                            |
| Restaurante / comedor universitario                                | Escena 2, Día 1-3 (destino)                                       |                                                                                                                                                                                                                                                                                                                                                                                                            |
| Jardín interior de la facultad                                    | Escena 2, Día 1-3 (destino)                                       | Confirmado: es el mismo jardín central que rodea la fachada general de la universidad.                                                                                                                                                                                                                                                                                                                    |
| Entrada de la universidad                                          | Escena 2, Día 1-3 (destino)                                       | Incluye ahora el puente de concreto sobre el estanque que rodea el edificio, frente a la entrada principal.                                                                                                                                                                                                                                                                                                |
| Explanada frente al edificio central (atardecer)                   | Escena 2.4                                                         |                                                                                                                                                                                                                                                                                                                                                                                                            |

## Prólogo — Prompts de generación (NovelAI Diffusion V4.5, formato Danbooru)

> **Nota de pipeline**: si un elemento del prompt tiende a desaparecer entre generaciones (como pasó con las sillas), NovelAI soporta énfasis con llaves — `{elemento}` aumenta su peso, `{{elemento}}` lo aumenta más. Vale la pena anotar acá qué elementos necesitaron este refuerzo, para no tener que redescubrirlo la próxima vez que se regenere un fondo parecido.
>
> **Orientación confirmada: horizontal (landscape)**, no vertical. Esto es una configuración de generación (ancho × alto en NovelAI), no un tag de prompt — sugerido **16:9** (por ejemplo 1920×1088, ajustado a un múltiplo válido para el modelo) para todos los fondos de acá en adelante. Ya incluí "wide angle"/"wide shot" en todos los prompts, que ayuda a la composición, pero la relación de aspecto real hay que fijarla en la configuración de generación, no en el texto del prompt.
>
> **Regla de vidrio confirmada**: la universidad usa vidrio espejado/reflectante de una sola vía — desde afuera se ve azulado y opaco (no se distingue el interior), desde adentro se ve transparente y normal. Esto significa que **solo los prompts de exterior** llevan el detalle de vidrio azul/reflectante; los interiores (aulas, biblioteca, comedor) llevan vidrio común, sin tinte.
>
> Negativo sugerido para todos: `humans, people, text, watermark, signature, blurry, low quality, modern architecture, ruins, damaged`

**Aula de Arqueología (Escena 1) — interior**

```
masterpiece, best quality, scenery, no humans, indoors, university lecture hall, second floor classroom, {large blackboard}, {teacher's desk at front of classroom}, {large arched windows}, clear glass, window showing only sky outside, clouds visible, elevated view, morning sunlight, cream colored stone walls, flat ceiling, archaeology posters, old maps on wall, pristine clean interior, warm lighting, anime background art, wide angle, empty foreground for characters
```

**Aula de la electiva de arte (Escena 2.3, vacía) — interior**

```
masterpiece, best quality, scenery, no humans, indoors, empty classroom, art classroom, second floor classroom, {large blackboard}, {teacher's desk at front of classroom}, easels, art supplies, paintings on wall, {large windows}, clear glass windows, window showing only sky outside, clouds visible, elevated view, natural afternoon light, cream colored stone walls, flat ceiling, quiet atmosphere, pristine clean interior, anime background art, wide angle
```

**Universidad Pública de Vantia — fachada exterior**

```
masterpiece, best quality, scenery, no humans, wide shot, european academy building, symmetrical architecture, cream colored stone walls, terracotta tiled roof, twin towers, asymmetrical towers, tall west tower, observatory dome, large telescope pointing at sky, shorter east tower, open terrace with railing, mirrored blue windows, reflective one-way glass, windows reflecting the sky, opaque glass, rows of arched windows, central triangular pediment, grand entrance doors, stone pathway, moat, reflecting water, stone bridge, manicured green lawn, clear blue sky, daytime, pristine condition, clean architecture, ultra detailed background, anime background art, scenery focus, no text, no watermark
```

**Biblioteca central — estanterías (variante Escena 2.1, tarde) — interior**

```
masterpiece, best quality, scenery, no humans, indoors, library, tall bookshelves, wooden shelving, old books, reading area, wooden floor, warm interior, high ceiling, arched windows, clear glass, afternoon light, bright natural lighting, warm sunlight through windows, quiet atmosphere, pristine clean interior, anime background art, wide angle
```

**Biblioteca central — estanterías (variante Escena 3, última hora de la tarde) — interior**

```
masterpiece, best quality, scenery, no humans, indoors, library, tall bookshelves, wooden shelving, old books, reading area, wooden floor, warm interior, high ceiling, arched windows, clear glass, evening light, low warm lighting, golden hour, dim lamps turned on, long shadows, empty quiet library, soft warm glow, pristine clean interior, anime background art, wide angle
```

**Restaurante / comedor universitario — interior**

```
masterpiece, best quality, scenery, no humans, indoors, university cafeteria, dining hall, long tables and benches, food counter, large windows, clear glass, natural daylight, cream colored stone walls, high ceiling, pristine clean interior, anime background art, wide angle
```

**Jardín interior de la facultad — exterior (ve las aulas desde afuera)**

```
masterpiece, best quality, scenery, no humans, outdoors, university courtyard garden, central garden, green lawn, trees, flower beds, stone walking paths, benches, surrounded by building wings, mirrored blue windows visible in background, reflective one-way glass, midday sunlight, peaceful atmosphere, clear sky, anime background art, wide angle
```

**Entrada de la universidad — exterior**

```
masterpiece, best quality, scenery, no humans, outdoors, university main entrance, grand stone doors, stone bridge, moat, reflecting water, pathway, cream colored stone walls, mirrored blue windows, reflective one-way glass, manicured lawn, daytime, clear sky, welcoming atmosphere, anime background art, wide angle
```

**Explanada frente al edificio central (Escena 2.4, atardecer) — exterior**

```
masterpiece, best quality, scenery, no humans, outdoors, university plaza, open courtyard, stone pavement, wide open space, building facade in background, mirrored blue windows, reflective one-way glass, sunset lighting, warm orange sky, golden hour, long shadows, anime background art, wide angle
```

## Bloques de ruta (Fase 2)

*(Todavía no hay guion escrito para los Bloques A y B — esta sección se completa a medida que avance la tarea 19.)*
