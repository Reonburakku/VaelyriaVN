
# Lista de Expresiones — Sprites Necesarios

> ✅ **Tarea 12 (sprites del prólogo) completa.**
>
> Documento vivo: se actualiza cada vez que un guion especifica una expresión concreta en una nota de arte/dirección. Sirve como lista de referencia rápida para saber qué expresiones generar en las tareas 8, 12 y 23 (arte del prólogo y de cada bloque de ruta) — la idea es no tener que releer guiones enteros para armar el pedido de arte.
>
> Solo entran acá expresiones con **nombre explícito** asignado en el guion (ej. "sprite de Hazel = Sorprendida"). Momentos con carga emocional pero sin etiqueta formal (una media sonrisa descripta en prosa, por ejemplo) quedan aparte, en la sección de pendientes, hasta que se les ponga nombre.

## Prólogo

| Personaje         | Expresión          |
| ----------------- | ------------------- |
| Hazel             | Estudiando          |
| Hazel             | Sorprendida         |
| Hazel             | Pensativa           |
| Agnes             | Sonrisa confiada    |
| Agnes             | Riendo              |
| Prof. Isolde Marr | Idle                |
| Bibliotecaria     | Idle                |
| Egis              | Seria               |
| Egis              | Tensa               |
| Egis              | Triste              |
| Egis              | Sonrisa tímida     |
| Egis              | Mirada hacia atrás |

## Extras genéricos reutilizables

*(Ver `Personajes-Secundarios.md` para el criterio de uso — siluetas sin personalidad definida, no ligadas a una escena en particular. El Borrador 9 del prólogo le asignó expresión "Lástima" al Guardia genérico, así que ya no alcanza con una sola expresión "Neutral" por sprite — puede hacer falta ampliar el set mínimo de estos extras a medida que se usen en más escenas.)*

| Personaje                 | Expresión                                                  |
| ------------------------- | ----------------------------------------------------------- |
| Extra Genérico Femenino  | Neutral                                                     |
| Extra Genérico Masculino | Neutral                                                     |
| Extra Genérico Masculino | Lástima*(usada en el Guardia de la entrada, Borrador 9)* |

## Pendientes de etiquetar (momentos con carga emocional sin expresión formal asignada todavía)

*(Ninguno por ahora — todos los personajes con diálogo del prólogo ya tienen sus expresiones puntuales etiquetadas.)*

---

## Prólogo — Prompts de generación (NovelAI Diffusion V4.5, formato Danbooru)

> **Sobre el protagonista**: el guion del prólogo está narrado en primera persona y nunca lo muestra en pantalla (no hay espejo ni CG en esta parte), así que no armé prompt para él acá — su apariencia ya quedó definida en `Protagonista.md` para cuando haga falta (CGs de rutas posteriores, pantalla de nombre, etc.). Avisame si igual lo querés generar ahora.
>
> **Paso obligatorio de post-procesamiento**: todos los prompts de acá generan sobre fondo blanco liso a propósito — es la forma más limpia de recortar después, los modelos de difusión no manejan bien pedir transparencia directamente. Pero el fondo blanco final **no** es el que va a Unity: antes de importar cualquier sprite, hay que quitarlo con el plugin "Remove Background" de IOPaint (variante "Anime Segmentation", entrenada para este estilo de arte en vez de fotos reales) para dejarlo en PNG con transparencia real. Sin este paso, cada sprite se ve con un rectángulo blanco detrás al superponerse sobre los fondos de escena.
>
> **Cómo usar esto**: cada personaje tiene un prompt de **identidad base** (lo que se repite en todas sus expresiones, para mantener consistencia — probalo primero solo, varias veces, hasta lograr una cara que reconozcas siempre) y después un tag corto por expresión que se **agrega** al final del prompt base. Para consistencia real entre expresiones del mismo personaje, conviene generar todas usando la misma seed o, si NovelAI V4.5 lo permite en tu plan, la función de referencia de personaje (img2img/vibe transfer) sobre la primera imagen que te convenza.
>
> Negativo sugerido para todos: `multiple views, split view, turnaround, character turnaround, front and side view, reference sheet, bad anatomy, extra limbs, bad hands, extra fingers, fused fingers, missing fingers, malformed hands, mutated hands, poorly drawn hands, blurry, low quality, watermark, signature, text, cropped`
>
> Nota de eficiencia: la "Sonrisa confiada" de Agnes y la expresión "Seria" de Egis ya están incluidas en sus descripciones de apariencia base (sonrisa amplia y segura / ojos que lucen tristes por defecto) — en la práctica, el prompt de identidad base de cada una **es** esa expresión. No hace falta generarlas por separado.

### Hazel

**Identidad base:**

```
masterpiece, best quality, 1girl, solo, brown hair, auburn hair, long hair, wavy hair, ahoge, side-swept bangs, ponytail, amber eyes, almond shaped eyes, thin eyebrows, large breasts, fair skin, witch robe, dark purple robe, bell sleeves, gold cuffs, high collar, zipper with flap closure, wide black belt, fitted bodice, flared skirt below waist, dark stockings, navy mary jane shoes, standing, simple pose, white background, full body, official art, single view
```

- **Estudiando** → agregar: `reading, holding book, looking down, focused expression`
- **Sorprendida** → agregar: `subtle surprised expression, slightly widened eyes, barely parted lips` *(sutil, no exagerada — ver nota en el guion, Escena 2.3)*
- **Pensativa** → agregar: `thoughtful expression, distant gaze, hand near chin`

### Agnes / Vaelyr

**Identidad base (ya incluye la expresión "Sonrisa confiada"):**

```
masterpiece, best quality, 1girl, solo, blonde hair, wavy hair, long hair, center part, curly hair, green eyes, almond shaped eyes, thin eyebrows, medium breasts, toned body, tanned skin, white crop top, denim shorts, frayed denim shorts, gold hoop earrings, gold necklace, fang pendant, blue scrunchie, confident smile, slight blush, standing, simple pose, white background, full body, official art, single view
```

- **Riendo** → agregar: `laughing, open mouth smile, eyes closed, joyful expression`

### Egis

**Identidad base (ya incluye la expresión "Seria"):**

```
masterpiece, best quality, 1girl, solo, white hair, silver hair, straight hair, long hair, ahoge, dark blue eyes, almond shaped eyes, sad looking eyes, thin eyebrows, {mature face}, young adult, not childlike, small breasts, slender build, pale skin, {short blazer}, {closed jacket}, buttoned up, cropped jacket, plain white blouse, no decoration, simple collar, navy mini skirt, black sheer tights, low heels, black choker, neutral serious expression, standing, simple pose, white background, full body, official art, single view
```

- **Tensa** → agregar: `tense expression, guarded, crossed arms, closed off posture`
- **Triste** → agregar: `sad expression, downcast eyes, subdued`
- **Sonrisa tímida** → agregar: `shy smile, faint smile, soft expression, slight blush`
- **Mirada hacia atrás** → agregar: `looking back over shoulder, turned pose, glancing back`

### Prof. Isolde Marr

**Identidad base (ya incluye la expresión "Idle"):**

```
masterpiece, best quality, 1woman, solo, dark brown hair, greying hair, hair bun, thin frame glasses, brown corduroy blazer, simple shirt underneath, dress pants, middle aged woman, calm neutral expression, standing, simple pose, white background, full body, official art, single view
```

Solo se genera "Idle" — decisión confirmada de no producir "Pensativa" para este personaje.

### Bibliotecaria

**Identidad base (ya incluye la expresión "Idle"):**

```
masterpiece, best quality, 1woman, solo, elderly woman, grey hair, short hair, reading glasses on chain, cardigan, neutral colors, small frame, gentle neutral expression, standing, simple pose, white background, full body, official art, single view
```

Solo se genera "Idle" — decisión confirmada de no producir "Lástima" para este personaje.

### Extras genéricos

**Extra Genérico Femenino (identidad base = expresión "Neutral"):**

```
masterpiece, best quality, 1girl, solo, generic university student, college student, young adult, mature build, adult proportions, not childlike, plain features, unremarkable hairstyle, {eyes covered by hair}, {shadow over eyes}, hair over eyes, neutral casual clothing, simple design, neutral expression, standing, simple pose, white background, full body, official art, single view
```

**Extra Genérico Masculino (identidad base = expresión "Neutral"):**

```
masterpiece, best quality, 1boy, solo, generic university student, college student, young adult, mature build, adult proportions, not childlike, plain features, unremarkable hairstyle, {eyes covered by hair}, {shadow over eyes}, hair over eyes, neutral casual clothing, simple design, neutral expression, standing, simple pose, white background, full body, official art, single view
```

- **Lástima** *(usada en el Guardia)* → agregar: `pitying expression, sympathetic look, soft frown`

---

## Bloques de ruta (Fase 2)

*(Todavía no hay guion escrito para los Bloques A y B — esta sección se completa a medida que avance la tarea 19.)*
