
# Lista de Audio — Música y SFX Necesarios

> Documento vivo, mismo espíritu que `Lista-Fondos.md` y `Lista-Expresiones-Sprites.md`: se actualiza a medida que el guion define qué necesita cada escena. Cubre música de fondo (BGM) y efectos de sonido (SFX) — las voces/interjecciones de personaje van en la tarea 14, no acá.
>
> Fuente según lo decidido en el documento de diseño (sección 5): BGM desde librerías con licencia (Epidemic Sound, Envato) o IA de música (Suno, Udio); SFX desde librerías con licencia (Freesound, Zapsplat).
>
> El documento de diseño estima 8-12 pistas de BGM para todo el juego — el prólogo usa 4, dejando margen para los temas de ruta, romance y finales de fases posteriores.

## Prólogo — Música (BGM)

| Tema                                             | Dónde se usa                  | Mood / prompt sugerido para IA de música (Suno/Udio)                                                                                                                               | Pista elegida                   |
| ------------------------------------------------ | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| **Tema de campus** (cotidiano)             | Escena 1, Escena 2 (Días 1-3) | Instrumental, guitarra acústica suave y piano, cálido y liviano, tempo medio, banda sonora anime de vida cotidiana, atmósfera de universidad de día, cuerdas sutiles, loopeable | **Glass Garden Morning**  |
| **Tema de curiosidad** (misterio suave)    | Escena 2.3 (Hazel)             | Instrumental, piano suave con cuerdas ligeras, delicado y contemplativo, tempo lento-medio, un toque de melancolía, banda sonora de novela visual, introspectivo, loopeable        | **Snowflake Dance**       |
| **Tema social** (animado)                  | Escena 2.4 (Agnes)             | Instrumental, pop instrumental optimista, synth y percusión liviana, brillante y enérgico, banda sonora anime de vida cotidiana, divertido y ligero, loopeable                    | **Footsteps in the Snow** |
| **Tema de tensión suave** (introspectivo) | Escena 3 (Egis)                | Instrumental, piano en tono menor, tempo lento, tenso pero contenido, swell de cuerdas sutil, banda sonora de novela visual, presagio silencioso, con peso emocional, loopeable     | **Memories of Winter**    |

Las tres pistas son de Crescendo, un recurso gratuito de 3 temas de piano loopeables — ver créditos requeridos en `Creditos.md`. 🔶 Asumí que "tema suave" se refería al "Tema de tensión suave" (es el único de los cuatro que tiene "suave" en el nombre) — confirmame si en realidad iba para otro.

🔶 El tema de tensión de la Escena 3 es buen candidato a convertirse, más adelante, en el motivo musical de Egis para su ruta completa (Bloque A) — vale la pena tenerlo en mente al componerlo/generarlo, en vez de tratarlo como descartable después del prólogo.

✅ Las 4 pistas de BGM del prólogo ya están elegidas.

## Prólogo — Efectos de sonido (SFX)

| SFX                                   | Dónde se usa                                                     | Notas                                                              |
| ------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------ |
| Murmullo de aula llena                | Escena 1                                                          | Ambiente de fondo, loop                                            |
| Pasos (entrada de Marr)               | Escena 1                                                          |                                                                    |
| Risas contenidas de grupo             | Escena 1                                                          | Al mencionar Vaelyria                                              |
| Sonido de escribir en libreta         | Escena 1, 2.3                                                     | Reutilizable en ambas escenas                                      |
| Ambiente de comedor universitario     | Escena 2, destino Restaurante                                     | Platos, murmullo, bullicio — loop                                 |
| Ambiente exterior de jardín          | Escena 2, destino Jardín                                         | Viento suave, pájaros — loop                                     |
| Ambiente exterior de entrada          | Escena 2, destino Entrada                                         | Viento, sonido urbano lejano — loop                               |
| Ambiente de aula vacía               | Escena 2.3                                                        | Silencio con eco leve — loop                                      |
| Ambiente exterior atardecer           | Escena 2.4                                                        | Viento suave — loop                                               |
| Risas de grupo (séquito de Agnes)    | Escena 2.4                                                        | Distinto del de Escena 1 — más animado                           |
| Ambiente de biblioteca                | Escena 3                                                          | Muy silencioso, eco sutil — loop                                  |
| Pasos controlados (Egis acercándose) | Escena 3                                                          |                                                                    |
| Sonido de libros/estanterías         | Escena 3                                                          |                                                                    |
| "¡Shhh!" de la Bibliotecaria         | Final de Opción A                                                | 🔶 Definir si es SFX o se resuelve con voz en la tarea 14          |
| Aparición de menú de elección      | Puntos de elección (ruta, "¿Consecuencias?"/"¿Como un apodo?") | SFX de UI, reutilizable en todos los puntos de elección del juego |
| Confirmación de selección           | Puntos de elección                                               | SFX de UI, reutilizable                                            |
| Transición entre escenas             | Todos los cortes de escena                                        | SFX de UI, reutilizable en todo el juego, no solo el prólogo      |

## Bloques de ruta (Fase 2)

*(Todavía no hay guion escrito para los Bloques A y B — esta sección se completa a medida que avance la tarea 19.)*
