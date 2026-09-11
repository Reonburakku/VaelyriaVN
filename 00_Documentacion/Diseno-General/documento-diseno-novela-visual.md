# Documento de Diseño — Novela Visual (Fantasía/Sci-fi con romance)

## 1. Visión general

| Aspecto            | Definición                                                                                                         |
| ------------------ | ------------------------------------------------------------------------------------------------------------------- |
| Género            | Fantasía o sci-fi con romance                                                                                      |
| Protagonistas      | 1 protagonista masculino (POV del jugador) + 3 interesses románticos femeninos                                     |
| Finales            | 9 finales totales (3 por cada heroína)                                                                             |
| Duración objetivo | Media: 4–8 horas de lectura total                                                                                  |
| Clasificación     | Maduro (temas adultos) — sin desnudos; intimidad insinuada mediante elipsis/fundido a negro, sin mostrar el cuerpo |
| Plataforma         | Móvil (Android/iOS) + PC (Steam)                                                                                   |
| Monetización      | Pago único                                                                                                         |
| Audio              | Música + efectos + voces parciales                                                                                 |
| Equipo             | Desarrollador solo, 13 años de experiencia en C#, poca experiencia en desarrollo móvil                            |
| Arte               | Generado con IA como base; apoyo humano puntual a evaluar tras la prueba de consistencia (tarea 8)                  |

Esta combinación es completamente viable en solitario, pero el punto crítico va a ser la **gestión del alcance**: 9 finales con arte, voces y una historia de fantasía/sci-fi es un proyecto real, no un fin de semana. La clave de éxito no es la herramienta, es el control de alcance (ver sección 8).

---

## 2. Estructura narrativa

**Modelo recomendado: "Ruta de entrada obligatoria + bifurcación compartida con separación tardía"**

```
PRIMERA PARTIDA
PRÓLOGO COMÚN ──────► Ruta Egis (única disponible) ──┬── Final Egis 1
                                                       ├── Final Egis 2
                                                       └── Final Egis 3 (con afinidad Hazel)

SEGUNDA PARTIDA EN ADELANTE (tras completar la ruta de Egis al menos una vez)
                            ┌── (obedecer a Egis) ──► vuelve a Ruta Egis
PRÓLOGO COMÚN ──► Punto de quiebre ─┤
                            └── (preguntar a Hazel) ──► Ruta compartida Hazel/Vaelyr
                                                              │
                                                    (se separan cerca del final)
                                                              │
                                              ┌───────────────┴───────────────┐
                                        Rama Hazel                      Rama Vaelyr
                                    ┌── Final Hazel 1                ┌── Final Vaelyr 1
                                    ├── Final Hazel 2 (afin. Vaelyr)  ├── Final Vaelyr 2 (afin. Hazel)
                                    └── Final Hazel 3 (afin. Vaelyr   └── Final Vaelyr 3 (afin. Hazel
                                         y Egis)                          y Egis)
```

- **Egis es la ruta de entrada obligatoria.** En la primera partida, cuando el protagonista empieza a preguntar por Vaelyria a profesores y estudiantes, Egis es quien lo detiene: le aconseja, con amabilidad pero distancia, que deje de hacer esas preguntas porque está dañando su propia reputación y no podrá hacer amigos (algo que ella conoce de primera mano). El protagonista le hace caso y ahí arranca, sin alternativa, la ruta de Egis.
- **A partir de la segunda partida**, en ese mismo punto de quiebre aparece una opción nueva: obedecer a Egis otra vez (vuelve a entrar en su ruta) o preguntarle a alguien más que se muestra interesada — Hazel —, lo cual abre la ruta compartida de Hazel y Vaelyr.
- **La ruta Hazel/Vaelyr es una sola** durante la mayor parte de su extensión (la investigación conjunta sobre la verdad de Vaelyria), y solo se separa en dos ramas cerca del final, una vez que la verdad queda revelada: el protagonista elige acompañar a Hazel o a Vaelyr, lo que determina cuál de las dos se convierte en el interés romántico de esa rama.
- **Afinidad cross-ruta** (ver más abajo) determina cuál de los 3 finales de cada rama se desbloquea, igual que en el modelo original, pero ahora también condiciona contenido adicional dentro de la ruta compartida antes de la separación.
- Las 4 personajes (protagonista + 3 heroínas) son estudiantes de la misma universidad, lo que habilita que sus historias se crucen de forma natural: pueden compartir clases, espacios comunes, y tener entre ellas relaciones de amistad o enemistad preexistentes, independientes de su relación con el protagonista. Esto es lo que permite que Hazel, Vaelyr y Egis se crucen de forma orgánica dentro de la ruta de cualquiera de ellas.

🔶 **Nota técnica importante para el plan de trabajo (fases 2 y de implementación en Naninovel)**: esta estructura ya no es "3 flags de afinidad corriendo en paralelo dentro de una sola partida" — requiere una **variable de progreso persistente entre partidas** (ej. `ruta_egis_completada = true`, guardada en el save del juego, no reseteada al empezar una partida nueva) que modifique el diálogo de Egis en el punto de quiebre la próxima vez que el jugador llegue ahí. Es viable en Naninovel, pero es una decisión de arquitectura que conviene dejar escrita antes de programar el árbol de escenas — vale la pena anotarla explícitamente en la tarea 21 (listado de flags) junto con las tres variables de afinidad cross-ruta.

### Los 9 finales

**Ruta Egis** (rejugable en cualquier partida mientras el jugador elija "obedecer"):

- **Final 1 — Amistad**: el protagonista opta por no arriesgar el contacto físico. Terminan sus estudios como amigos, se ven de vez en cuando a comer, envejecen cada uno con su vida, solo como amigos.
- **Final 2 — Tragedia**: el protagonista elige la intimidad física con Egis pese al riesgo. Durante el clímax, el poder de petrificación se acelera drásticamente y el protagonista queda convertido en estatua — que Egis atesora para siempre.
- **Final 3 — Redención** (requiere suficiente afinidad con Hazel): Hazel, con su conocimiento, desarrolla un brebaje que logra despetrificar al protagonista tras los eventos del Final 2, y además libera a la madre de Egis, dando paso al final bueno.

**Rama Hazel** (requiere haber completado la ruta de Egis al menos una vez, y llegar a la separación final eligiendo acompañar a Hazel):

- **Final 1**: Hazel confronta a su familia y la abandona, continuando su vida en una nueva familia junto al protagonista.
- **Final 2** (requiere suficiente afinidad con Vaelyr): logran romper el sello de Vaelyr; con su ayuda, Hazel confronta y derroca a los Wren, y se establece como nueva ministra, prometiendo revelar la verdad y restaurar la posición y el orgullo de Vaelyr. Hazel vive como ministra junto al protagonista; Vaelyr se va a vivir su vida antigua, libre.
- **Final 3** (requiere suficiente afinidad con Vaelyr y con Egis): similar al Final 2, pero con Egis presente — a través de varias interacciones, ayuda a que Hazel y Vaelyr se reconcilien y se vuelvan amigas. Esta vez Vaelyr no se va: se queda gobernando la ciudad como mano derecha de Hazel. Si el jugador también logró el Final 3 de Egis, se muestra una escena adicional donde Egis y su madre (despetrificada) emprenden una aventura para encontrar a Vaelyr y volver a ser sus sacerdotisas.

**Rama Vaelyr** (mismos requisitos de acceso que la rama Hazel, eligiendo acompañar a Vaelyr en la separación final):

- **Final 1**: Vaelyr empieza a vivir con el protagonista mientras mantiene su "trabajo" de cuidar a Hazel, pero ahora lleva mejor la carga gracias a él (además, conserva sus tesoros y pueden vivir cómodamente).
- **Final 2** (requiere suficiente afinidad con Hazel): Hazel y Vaelyr enfrentan juntas a los Wren y rompen el sello. Vaelyr queda gobernando, instaura un nuevo sistema donde el ministerio pierde poder y la familia Wren es expulsada de la política. Hazel continúa sus estudios, libre del yugo familiar.
- **Final 3** (requiere suficiente afinidad con Hazel y con Egis): similar al Final 2, con Egis presente ayudando a reconciliar a Hazel y Vaelyr. Esta vez Hazel y el protagonista se quedan como cogobernantes, apoyando el nuevo gobierno de Vaelyr — Hazel como su mejor amiga, el protagonista como su amante. Si el jugador logró el Final 3 de Egis, ella y su madre también aparecen en estas escenas, sirviendo como sacerdotisas de Vaelyr.

**Recomendación de longitud de guion** (para llegar a 4-8h de lectura):

- Prólogo común: ~3,000–5,000 palabras
- Cada ruta (hasta el punto de ramificación de finales): ~15,000–20,000 palabras
- Cada final individual: ~1,500–3,000 palabras
- **Total estimado: ~70,000–90,000 palabras** (equivalente a una novela corta/mediana)

### Manejo de revelaciones y pistas (principio de guion, aplica desde ahora)

La ruta de Egis, al ser la única jugable en la primera partida, **no revela nada del lore mayor del mundo** (el sometimiento de Vaelyr, el robo de identidad de los Wren, la verdadera naturaleza de Agnes). Se centra exclusivamente en la historia entre el protagonista y Egis, mientras conoce de forma superficial al resto del elenco:

- **Agnes** aparece únicamente como la "diva" popular de la universidad (arquetipo *gal*, carismática, con su séquito) — su nombre real (Vaelyr) y su naturaleza de dragona sometida **no se revelan** en esta ruta bajo ninguna circunstancia.
- **Hazel** aparece como una compañera amistosa que podría ayudar al protagonista — su identidad como bruja y cualquier trasfondo de su familia **solo se revela si el jugador alcanza suficiente afinidad con ella** (necesaria para el Final 3 de Egis), y aun así de forma acotada al brebaje, sin destapar el lore completo.
- El resto del elenco (profesores, estudiantes) funciona como color de ambiente, sin plantar misterios que no se puedan resolver dentro de esta ruta.

**Sí conviene sembrar pistas sutiles** a lo largo del guion de Egis — comentarios ambiguos, reacciones fuera de lugar, detalles de ambientación — que no signifiquen nada en una primera lectura, pero que cobren sentido retrospectivamente para un jugador que ya completó la ruta Hazel/Vaelyr y entiende el trasfondo completo. El objetivo es que **releer (o rejugar) la ruta de Egis después de conocer todos los secretos se sienta como una experiencia distinta**, no una repetición.

🔶 Vale la pena mantener, junto al guion de Egis, una lista aparte de "pistas plantadas" (qué línea, en qué escena, y qué revela en retrospectiva) para no perder el hilo de qué se sembró y dónde, especialmente porque la ruta de Egis probablemente se escriba antes de tener completamente cerrado el guion de Hazel/Vaelyr.

#### Lista de pistas plantadas (ruta de Egis)

| # | Pista                                                                                                                                                                                                 | Qué revela en retrospectiva                                                                                                                                                                                                                                                                      |
| - | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | El semblante coqueto habitual de Agnes cambia visiblemente cada vez que se acerca Hazel — incluso puede responderle con sarcasmo — pero el guion deja pasar el cambio sin comentarlo ni explicarlo. | Agnes es en realidad Vaelyr, sometida por la familia de Hazel y obligada a vigilarla; su frialdad hacia ella es la única grieta visible de una hostilidad contenida por siglos de resentimiento.                                                                                                 |
| 2 | Para el brebaje del Final 3, Hazel le pide a Egis un poco de su sangre, pero nunca se menciona cuáles son los demás ingredientes.                                                                   | El otro ingrediente es sangre de la propia Vaelyr — algo que solo se revela en la ruta compartida Hazel/Vaelyr.                                                                                                                                                                                  |
| 3 | En el prólogo, cuando el protagonista le pregunta si dejará de hablarle si le pasan "consecuencias", Egis bromea: "Eso me convertiría en Vael-chica".                                              | La broma es un eco inconsciente de la propia tragedia de Egis: fue ella misma quien, de chica, repitió sin darle importancia el nombre "Vaelyr" en público — el mismo desliz que llevó al regaño y al accidente que petrificó a su madre. Sin saberlo, vuelve a jugar con ese mismo nombre. |

*(Esta tabla se va a ir ampliando a medida que surjan más pistas durante la escritura del guion.)*

---

## 3. Requerimientos de contenido (guion)

- [ ] Documento de "biblia" del mundo: reglas de la fantasía/sci-fi, geografía, facciones, tono
- [ ] Ficha de personaje para el protagonista y cada heroína (personalidad, arco, motivaciones, secretos)
- [ ] Guion del prólogo común
- [ ] Guion de las 3 rutas con sus puntos de decisión marcados explícitamente
- [ ] Guion de los 9 finales
- [ ] Lista de "flags"/variables que el motor debe rastrear (qué elección lleva a qué final)
- [ ] Revisión de coherencia de tono maduro sin cruzar a contenido explícito (importante para las políticas de las tiendas de apps, ver sección 7)

---

## 4. Requerimientos de arte (enfoque híbrido: IA como base, apoyo humano puntual si hace falta)

**Estrategia principal: generación 100% con IA**, dejando abierta la puerta a incorporar apoyo humano puntual si la producción lo requiere. El costo real de la vía IA no es económico, sino tiempo de iteración y curaduría (ver tarea 8 del plan de trabajo, "prueba de consistencia de personaje", marcada explícitamente como la más crítica de la Fase 0).

🔶 **Nota para revisar más adelante — posible incorporación de un artista humano**: si al completar la tarea 8 la IA elegida no logra consistencia de personaje aceptable tras iterar en serio, o si en cualquier punto de producción la calidad del arte generado no alcanza el nivel que el proyecto necesita, vale la pena reconsiderar contratar a un artista humano — no necesariamente para todo el pipeline (el presupuesto estimado para eso ronda los $4,800–$11,250 USD, ver estimación de la conversación de diseño), sino posiblemente acotado a las piezas donde más se nota la calidad (por ejemplo, solo los CGs de los finales, que son los momentos de mayor impacto visual del juego). Esta decisión debería tomarse **después** de ver el resultado real de la tarea 8, no antes — no tiene sentido presupuestar ayuda humana antes de confirmar si hace falta.

| Tipo de asset                            | Cantidad estimada                                                                                       | Notas                                                                                                                                                                                                                                                                    |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Fondos (backgrounds)                     | 15–25 escenarios únicos                                                                               | Reutilizables con variaciones de luz (día/noche/clima) para ahorrar cantidad                                                                                                                                                                                            |
| Sprites de personaje                     | 4 personajes × 4–6 expresiones × 1–2 outfits, + estados adicionales para el protagonista (ver nota) | El protagonista sí necesita sprite propio (tiene personalidad definida, no es POV muda) — además de sus expresiones normales, requiere estados especiales de petrificación progresiva (normal → petrificación parcial → estatua completa) para el Final 2 de Egis |
| CGs (ilustraciones especiales de escena) | 15–20 (momentos clave + finales)                                                                       | Los 9 finales casi seguro necesitan un CG único cada uno                                                                                                                                                                                                                |
| UI/Assets de interfaz                    | Logo, menú, botones, íconos de guardado, textbox                                                      | Estilo coherente con el arte generado                                                                                                                                                                                                                                    |
| Splash/portada                           | 1 arte principal para tienda                                                                            | Fundamental para conversión en Google Play/App Store                                                                                                                                                                                                                    |

**Consideración importante sobre arte con IA:**

- Necesitarás mantener **consistencia de personaje** entre cientos de imágenes (mismo rostro, mismo pelo, mismos ojos). Esto es el mayor riesgo técnico del pipeline de arte con IA. Herramientas como control de personaje por LoRA/character reference (Stable Diffusion + LoRA entrenado, o herramientas como NovelAI, Midjourney con character reference) ayudan, pero vas a necesitar iterar y curar mucho.
- Google Play y App Store están empezando a pedir **declaración de contenido generado por IA** en el listado — no es un impedimento, pero hay que declararlo (ver sección 7).

---

## 5. Requerimientos de audio

| Tipo                   | Cantidad estimada                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Fuente sugerida                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Música de fondo (BGM) | 8–12 pistas (tema por heroína, tensión, romance, finales)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Librerías de stock con licencia (Epidemic Sound, Envato) o IA de música (Suno, Udio)                                                                                                                                                                                                                                                                                                                                      |
| Efectos de sonido      | 20–40 (transiciones, UI, ambiente)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Librerías gratuitas/pagas (Freesound con licencia comercial, Zapsplat)                                                                                                                                                                                                                                                                                                                                                     |
| Voces parciales        | No se dobla el guion completo — se usa un set reutilizable de interjecciones/reacciones cortas por emoción y por personaje (ej. una risita para "alegre", un quejido breve para "triste", un resoplido para "enojada"), disparadas junto al texto en vez de leer la línea completa. Definir el set de emociones base (sugerido: neutral, alegre, triste, sorpresa, enojo, coqueta/sarcástica — esta última relevante para Vaelyr) por cada una de las 3 heroínas.**Estrategia de fuente (decidida en la tarea 9)**: packs de sonidos vocales pregrabados con licencia comercial como fuente principal por heroína (ej. WOW Sound "Anime Vocals", GfxSoundsStudios "Anime Kit"); las emociones que un pack no cubra se completan más adelante (después de tener el guion, cuando se sepa con precisión qué falta) generando con ElevenLabs una voz de su propia librería que suene parecida por oído — nunca clonando la voz de un pack comprado, ya que las licencias de estos proveedores (confirmado con WOW Sound y Sonniss) prohíben explícitamente usar su contenido para entrenar o clonar con IA. | Packs pregrabados: WOW Sound, Sonniss (pago único, sin recurrencia). ElevenLabs para relleno de emociones faltantes: planes desde $5 USD/mes. 🔶 El protagonista no lleva voz grabada — pese a tener personalidad propia definida (ver ficha), sus líneas se presentan solo en texto, siguiendo la convención habitual del género de no doblar al personaje jugable. Esto acota el trabajo de voces a las 3 heroínas. |

Como es solo, te conviene decidir **desde ya** cuánto de la voz será real vs. sintética — esto cambia mucho el presupuesto y el tiempo.

🔶 **Nota técnica para Naninovel**: el enfoque de "voice barks" (interjecciones cortas por emoción, no doblaje línea por línea) es compatible con Naninovel, pero requiere configurarlo como un sistema de disparo por etiqueta de emoción en vez de asociar un archivo de audio a cada línea de texto — vale la pena anotarlo en la tarea 21 (listado de flags) o en la documentación técnica de implementación cuando se llegue a esa etapa, ya que cambia cómo se estructura la integración de audio en el motor respecto a un doblaje línea por línea tradicional.

---

## 6. Requerimientos técnicos y motor recomendado

Dado tu perfil (13 años en C#, poca experiencia móvil, necesitas ramificación + guardado + voces + monetización paga en tiendas móviles y PC), esta es la comparación relevante:

### Opción recomendada: **Unity + Naninovel**

- Naninovel es un framework de novela visual construido sobre Unity en C#. Tiene: sistema de diálogo con ramificación, gestión de personajes/expresiones, CGs, guardado/carga, integración de voces, y exportación nativa a Android/iOS.
- **Por qué te conviene**: aprovechas directamente tus 13 años de C#, Unity tiene la documentación de publicación a Android/iOS más madura del mercado, y Naninovel te ahorra meses de programar desde cero un motor de diálogo/ramificación/guardado. Bonus relevante ahora que PC (Steam) también es plataforma objetivo: Unity exporta de forma nativa a Windows/Mac/Linux — no es un cambio de stack ni de motor, es una opción de build que ya tenés disponible sin trabajo adicional de arquitectura.
- Costo: Naninovel es un asset pago (rango de $100–150 USD, versión única), Unity es gratis hasta cierto nivel de ingresos.

### Alternativa gratuita: **Godot 4 + C# + Dialogic**

- Godot soporta C# nativamente y exporta a Android/iOS. Dialogic es un addon de diálogo/VN maduro (aunque su configuración por defecto es más GDScript-friendly).
- Ventaja: 100% gratis y de código abierto.
- Desventaja: tendrás que programar más "pegamento" a mano entre Dialogic y tu lógica en C#, y la documentación de publicación móvil es menos pulida que la de Unity.

### Opción del género (no recomendada para tu caso): **Ren'Py**

- Es el estándar de facto para VN y tiene el ecosystem más grande de tutoriales, pero está en Python — no aprovecha tu experiencia en C# y tendrías que aprender un lenguaje nuevo desde cero solo por el motor.

**Mi recomendación concreta: Unity + Naninovel.** Es la combinación que minimiza el tiempo que gastás en "reinventar el motor" y maximiza el tiempo que gastás en contenido (que es lo que realmente diferencia tu juego).

### Otros requerimientos técnicos

- [ ] Sistema de guardado/carga con múltiples slots (esperado en el género)
- [ ] Sistema de "galería" de CGs desbloqueados (estándar en VNs, aumenta el valor percibido)
- [ ] Optimización de tamaño de build (las imágenes generadas por IA en alta resolución pueden inflar el peso de la app — hay que definir compresión/resolución final desde el inicio)
- [ ] Testing en dispositivos de gama media/baja de Android (fragmentación de Android es el mayor riesgo técnico de QA)
- [ ] Sistema de configuración de texto (velocidad, tamaño de fuente) — importante en móvil
- [ ] **Multi-idioma**: lanzamiento en español, con el código preparado para sumar idiomas más adelante. Naninovel tiene soporte de localización nativo (scripts, texto de UI, nombres de personajes, audio, fondos con texto) — no requiere arquitectura custom. Único paso obligatorio desde el arranque de la tarea 15: configurar el **Source Locale en español** (Naninovel → Configuration → Localization) antes de generar los primeros scripts `.nani`, para que agregar un idioma nuevo más adelante sea correr la herramienta de localización, no reestructurar el proyecto. El guion en Markdown no necesita ningún cambio de formato por esto — la localización se genera a partir de los `.nani` ya escritos.

---

## 7. Consideraciones legales y de tiendas

- **Clasificación de contenido**: al no incluir desnudos (la intimidad se maneja con elipsis/fundido a negro), el juego vuelve a entrar cómodo en las categorías estándar de Google Play y App Store con clasificación "Maduro 17+" — evita el problema de distribución que sí generaba la versión con desnudos. Aun así, hay que completar el cuestionario de contenido de cada tienda con honestidad (temas maduros, romance, violencia si aplica) y verificar las políticas vigentes al momento de publicar, ya que cambian con frecuencia.
- **Declaración de arte generado por IA**: revisa las políticas vigentes de Google Play, App Store y Steam al momento de publicar — las tres plataformas han ido añadiendo requisitos de divulgación para contenido generado por IA.
- **Steam Direct (PC)**: fee único de $100 USD por juego al enviarlo a través de Steamworks, reembolsable una vez que el juego genera $1,000 de ingresos brutos en la tienda. Split estándar: 70% para vos, 30% para Valve (mejora en tramos de ingresos altos, irrelevante en tu escala inicial). El proceso completo —alta como partner, verificación de identidad, carga del build, revisión— toma un mínimo de 4 a 6 semanas: hay una espera obligatoria de 30 días después de pagar el fee, más el requisito de tener la página de tienda ("Coming Soon") publicada al menos dos semanas antes del lanzamiento. Conviene arrancar este trámite con bastante anticipación al lanzamiento planeado, no a último momento.
- **Política de privacidad**: obligatoria para publicar en las tres tiendas, incluso para un juego offline simple.
- **Licencias de música/SFX/voces**: asegúrate de que cualquier librería o herramienta de IA que uses para audio tenga licencia comercial explícita para juegos pagos.

---

## 8. Plan de producción sugerido (para 1 persona)

Dado que sos un equipo de una sola persona, la recomendación es producir en **fases verticales**, no horizontales (no "todo el guion, luego todo el arte, luego todo el audio"):

1. **Fase 0 — Preproducción (2-4 semanas)**: biblia del mundo, fichas de personajes, guion del prólogo, prueba de consistencia de personaje con tu pipeline de IA elegido.
2. **Fase 1 — Vertical slice (4-6 semanas)**: prólogo completo jugable en el motor, con arte, audio y guardado funcionando de principio a fin. Esto valida el pipeline completo antes de escalar.
3. **Fase 2 — Producción de rutas (la fase más larga)**: dos bloques, no tres rutas simétricas — primero el bloque de Egis completo (guion a arte a integración), y luego el bloque compartido Hazel/Vaelyr (tramo compartido escrito una sola vez + las dos ramas finales cortas), para poder soltar contenido probado incrementalmente.
4. **Fase 3 — Finales y pulido**: los 9 finales, galería, ajustes de UI/UX.
5. **Fase 4 — QA móvil y PC**: pruebas en múltiples dispositivos/tamaños de pantalla, optimización de rendimiento y peso.
6. **Fase 5 — Lanzamiento**: assets de tienda (capturas, trailer, descripción) para Google Play, App Store y Steam, configuración de precio, alta en Steamworks (fee, verificación, página "Coming Soon"), soft launch opcional en un mercado antes del lanzamiento global.

---

## 9. Cómo se ve el éxito

Un proyecto exitoso, dado tu perfil y alcance, se ve así:

- **Un vertical slice jugable** (prólogo completo) en las primeras 6-10 semanas — esto es la señal más importante de que el pipeline (guion → arte IA → Unity/Naninovel → build móvil) funciona de punta a punta.
- **Consistencia visual de personajes** lograda de forma repetible (no imagen por imagen a mano) antes de escalar a las 3 rutas completas.
- **Una ruta completa terminada y jugada por testers externos** antes de replicar el proceso en el otro bloque — valida ritmo narrativo, duración real de lectura y calidad de las decisiones. Con la estructura de 2 bloques (Egis; Hazel/Vaelyr), esto aplica primero al Bloque Egis antes de invertir en el Bloque Hazel/Vaelyr completo.
- **Build estable en al menos 3-4 dispositivos Android de gama distinta**, en iOS, y en PC (Windows como mínimo), sin errores de guardado/carga.
- **Listado de tienda completo y honesto** (clasificación, divulgación de IA, política de privacidad) sin fricción de aprobación.
- **Alcance controlado**: si en algún punto el guion, arte o audio empiezan a superar las estimaciones de la sección 2-5 en más de 30-40%, es señal de recortar (por ejemplo, reducir CGs por final, o compartir más fondos entre rutas) antes de que el proyecto se vuelva inmanejable para una sola persona.

El mayor riesgo para un desarrollador solo en este tipo de proyecto no es técnico — es de **alcance**. 9 finales completos con voces parciales y arte curado es ambicioso pero factible si seguís el modelo de producción vertical y sos disciplinado recortando cuando haga falta.
