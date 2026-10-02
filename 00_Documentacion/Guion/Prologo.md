# Prólogo — Guion final (sincronizado con la implementación en Naninovel)

> Tarea 10 del plan de trabajo — Fase 1 (Vertical Slice). Sin contenido explícito ni desnudos (política confirmada).
>
> **Reemplaza el Borrador 9.** Este documento ya no es un borrador previo a la implementación: está reescrito a partir de los 7 archivos `.nani` que vos y Claude Code terminaron escribiendo en Unity (`Prologo_Escena0` a `Prologo_Escena3`), que se alejaron bastante del Borrador 9 durante el trabajo de implementación (diálogos reescritos, líneas nuevas, una escena entera — la 0 — que no existía acá). De acá en adelante este documento refleja lo que el jugador ve en pantalla, no al revés.
>
> Ortografía, puntuación y los dos hallazgos técnicos (nombre "Celador"→"Guardia", rama duplicada del `@random` en el destino Entrada) ya están corregidos tanto acá como en los `.nani` de Unity — ver el detalle en "Correcciones aplicadas", al final.

**Convenciones de formato** (repetir en los guiones de los bloques siguientes, para que no se desalineen de la implementación como pasó acá):

- Diálogo y narración se escriben línea por línea, tal como se van a mostrar en pantalla — no en párrafos largos. Una oración se puede fragmentar en varias líneas cortas para controlar el ritmo de lectura, incluso si eso convierte una coma en un corte de línea.
- Formato de diálogo: `Personaje: línea`, sin encabezados en negrita — permite escribir varias líneas seguidas del mismo personaje sin repetir su nombre como título cada vez.
- Pensamientos internos del protagonista van en *cursiva*, como una línea más de su propio diálogo (no como acotación aparte tipo "(pensamiento)").
- Puntos suspensivos: siempre exactamente 3 puntos (`...`), sea como línea propia (pausa) o dentro de una oración — nunca más, nunca menos.
- Personajes cuyo nombre el jugador todavía no conoce (Marr, Egis) se presentan con el nombre oculto ("???") hasta el momento exacto en que se presentan a sí mismos en el diálogo — recién ahí se revela su nombre real. Se marca en el guion con una nota en el punto donde ocurre el cambio.
- Las notas técnicas/de arte se mantienen entre corchetes en cursiva, pero acotadas a lo que afecta consistencia de personaje o arte (expresión de sprite, cambios de BGM, hitos de variables) — el detalle de implementación pura (posiciones, escalas, nombres de archivo) vive solo en el `.nani`.

---

## ESCENA 0 — Apertura

*[BGM: "Universidad - Mañana" de fondo, sin tema musical propio todavía.]*

- La Universidad Pública de Vantia.

Una prestigiosa universidad ubicada en la próspera ciudad de Vantia.
Ha sido reconocida por la calidad de sus egresados.
Estoy seguro de que todo padre quiere que sus hijos estudien acá.

Quise venir a esta universidad, en parte por su prestigio, pero también para obtener información de cierta ciudad que, según mis cálculos, debería estar justo acá.

Desde que recuerdo, he estado interesado en la historia del mundo.
Grandes ciudades e imperios han nacido, prosperado y caído a través del tiempo.
El ciclo siempre se repite: se unen unos cuantos habitantes, se construye una ciudad, se desarrolla una cultura, y luego todo se derrumba.
Quienes conocen la historia ven venir la caída de una civilización antes de que ocurra.
Pero normalmente, no tienen el poder para evitarlo.

Aún así, es imperdonable dejar que la historia se pierda, aunque solo sea una ciudad remota.
No he encontrado mucha información sobre esta ciudad, pero yo mismo me encargaré de mantener viva su historia.

*Corte a la Escena 1.*

---

## ESCENA 1 — Primer día (Aula de Arqueología)

*[BGM: "Glass Garden Morning" (Tema de campus) — arranca acá y sigue sonando hasta que otra escena la corte explícitamente.]*

Entro al aula de arqueología.
Es media mañana de finales de verano, y el aula se va llenando de a poco con otros estudiantes de primer año.
Noto la formalidad en la vestimenta de la mayoría, es evidente que quieren empezar con pie derecho.

Encuentro un lugar cerca de la ventana, con buena iluminación.
Dejo la maleta en el piso y saco mi libreta, ya gastada en los bordes.
Reviso las notas que he tomado acerca de "la gran ciudad de Vaelyria".
Siempre me ha llamado la atención desde que supe de ella, una gran ciudad tecnológica, que ha sido mencionada en diversos textos, aunque no he encontrado literatura que hable específicamente de esta.
A eso vine, deduje que esta es la ubicación, aunque ahora tiene otro nombre, espero encontrar más información que las cortas menciones que he conseguido.

*[Nombre de Marr oculto ("???") hasta que se presenta. Sprite = "Idle" (única apariencia) durante toda la escena.]*

Entra al aula una mujer tan elegante que usa su abrigo de pana a pesar del calor.
Parece ser la profesora.
Deja sus cosas en el escritorio sin apuro y mira al grupo con la calma de quien ha dado esta misma clase innumerables veces.

Marr: Bienvenidos a Introducción a la Arqueología.
Marr: Soy la profesora Isolde Marr.

*[Se presentó por su nombre — a partir de acá su nombre en pantalla deja de mostrar "???" y pasa a "Isolde".]*

Marr: Antes de repartir el programa, quiero que cada uno diga su nombre y, si ya lo tiene claro, qué período o región le interesa investigar.
Marr: Si aún no lo saben, les recomiendo empezar a pensarlo, los secretos no se descubren por casualidad.

Empieza la ronda de presentaciones.
Menciones dispersas de Mesopotamia, la Ruta de la Seda, arqueología subacuática del Mediterráneo.
Temas muy interesantes. Llega mi turno.

*[Acá se le pide su nombre al jugador — variable {Nombre}, valor por defecto "Leo".]*

Protagonista: Me llamo {Nombre}.
Protagonista: Vine específicamente para investigar sobre Vaelyria.

...

La profesora hace un silencio breve.
No el silencio de quien reconoce el nombre y lo sopesa, sino el de quien lo escucha por primera vez y no sabe bien qué hacer con él.
Frunce el ceño, genuinamente pensativa, no hostil.

Marr: ¿Vaelyria... como asentamiento?
Marr: No me suena el nombre.
Marr: ¿Es una variante regional de algo, o...?

Protagonista: Aparece mencionada en varias fuentes como una ciudad importante, próspera, con un crecimiento inusualmente rápido para su época.
Protagonista: Nunca encontré un texto que la describiera directamente, solo referencias de paso, como cualquier ciudad que simplemente existe.

*(Marr sale de escena un momento; se oyen risas contenidas del resto del curso.)*

EstudiantesFondo: ¿Vaelyria?
EstudiantesFondo: ¿Te suena ese nombre?
EstudiantesFondo: Para nada.

Marr: No conozco ese nombre.
Marr: Puede que sea una mala traducción, o una confusión con otra ciudad.
Marr: Tráigame las fuentes que tenga cuando quiera y le echamos un ojo con calma.
Marr: Aunque es difícil que yo no haya escuchado de una ciudad tan importante como la que menciona.

Protagonista: Por supuesto.

Ella sigue con la ronda de presentaciones.

Protagonista: *Alguien debería saber.*

*[Nota de dirección: la reacción de Marr debe leerse como genuinamente profesional y curiosa, no despectiva — el endurecimiento social real llega en la Escena 2, fuera de un contexto académico protegido.]*

*Fin Escena 1 — continúa en Escena 2.1 (Biblioteca central).*

---

## ESCENA 2.1 — Biblioteca central, tarde

*[BGM: sigue "Glass Garden Morning" — esta escena no tiene tema propio, se usa el de campus por defecto.]*

Después de clases, voy a la biblioteca.
Espero encontrar algo de información.
Luego de buscar un poco en las estanterías, sin éxito, me acerco a la recepción.

*[Sprite de la Bibliotecaria: "Idle" (única apariencia) durante toda la escena.]*

La bibliotecaria, una mujer mayor con lentes colgando de una cadena, escucha mi pregunta con paciencia y termina negando con la cabeza.

Bibliotecaria: Busqué en el catálogo general y en los índices de historia regional.
Bibliotecaria: No encuentro nada relacionado con Vaelyria, ni como tema principal ni como referencia.
Bibliotecaria: Si quieres, te dejo anotado el pedido y lo reviso con más calma esta semana.

Protagonista: Se lo agradezco. Voy a seguir buscando por mi cuenta también.

Me mira un segundo de más, con esa mezcla de simpatía y lástima que se les da a los estudiantes obsesionados con algo que probablemente no lleve a ningún lado.

Termino un día más.

*Fin Escena 2.1 — continúa en "Días 1 a 3" (elección de destino).*

---

## ESCENA 2 — Días 1 a 3: Preguntando por el campus, horario de almuerzo

*[Bucle de 3 días: cada día se ofrecen los destinos todavía no visitados — Día 1 ofrece los 3, Día 2 los 2 restantes, Día 3 avanza directo al único que queda, sin mostrar elección real. El contenido de cada destino no cambia según el día en que se visite, solo el orden. Los tres se visitan siempre, sin excepción. El fondo de la mañana alterna entre "Historia" y "Arte" según cuántos destinos ya se visitaron, solo para variar la imagen — sin significado narrativo.]*

Otra mañana productiva.

Durante el almuerzo, puedo aprovechar para obtener información.
¿En dónde puedo preguntar hoy?

> **Ir al restaurante**
> **Ir al jardín**
> **Ir a la entrada de la universidad**

### Destino: Restaurante

Me acerco a una mesa donde reconozco un par de caras de mi clase de arqueología.
Apenas menciono "Vaelyria", uno de ellos suelta una risa corta, nada amable.

*[Estudiante anónimo — sprite elegido al azar entre Extra Genérico Femenino/Masculino, ver `Personajes-Secundarios.md`.]*

Estudiante: Ah, eres tú. El de la ciudad que no existe.

Protagonista: ¿Entonces la conoces?

Estudiante: No, no puedo conocer algo que no existe.

Nadie en la mesa tiene nada más que ofrecer.
Pregunto a unos cuantos estudiantes, antes de comer.

Termino un día más.

### Destino: Jardín

El jardín interior de la facultad está tranquilo a esta hora.
Veo un par de estudiantes leyendo bajo la sombra de un árbol.
Me acerco suavemente, tratando de sonar casual.

*[Mismo criterio: estudiante anónimo, sprite al azar.]*

Estudiante: ¿Vaelyria? Ni idea. ¿Es de una serie o algo?

Protagonista: No, es... da igual. Gracias de todas formas.

Vuelvo sobre mis pasos antes de que me pregunten por qué me interesa tanto algo que, para ellos, ni siquiera existe.

Termino un día más.

### Destino: Entrada de la universidad

Pruebo en la entrada, con el personal de seguridad y algunos estudiantes que van llegando tarde.
Uno de los guardias, más por cortesía que por interés real, me escucha hasta el final.

Guardia: Llevo doce años acá y nunca escuché ese nombre. Lo siento.

Protagonista: *Bueno, no podía esperar más.*

Termino un día más.

### Día 4

Única opción disponible:

> **Quedarme en el aula**

*Fin "Días 1 a 3" — continúa en Escena 2.3 (Aula vacía, hora de almuerzo).*

---

## ESCENA 2.3 — Aula vacía, hora de almuerzo (Hazel)

*[BGM: "Snowflake Dance" (Tema de curiosidad).]*

Me quedo en el aula de la electiva de arte, reviso mi vieja libreta con apuntes sobre Vaelyria.
La mayoría sale corriendo a almorzar, pero no tengo ganas de cruzarme con gente que ya empieza a mirarme raro.
No estoy solo: Hazel también se quedó, sentada en su lugar de siempre, ya terminó de comer y aprovecha el rato libre para estudiar antes de que vuelva el resto.

*[A diferencia de Marr/Egis, el nombre de Hazel se revela de inmediato — la narración y el protagonista ya la llaman por su nombre desde el arranque de la escena, sin pasar por "???". Sprite de Hazel: "Estudiando" desde su entrada hasta el cambio a "Sorprendida" más abajo.]*

No tengo nada que perder.

Protagonista: ¿Hazel, cierto? Compartimos la electiva de arte.
Protagonista: Te quería preguntar algo rápido, si tienes un segundo.

Hazel: Depende de la pregunta.

Protagonista: ¿Alguna vez escuchaste el nombre "Vaelyria"?
Protagonista: Como ciudad, como región, lo que sea.

*[Sprite de Hazel: "Sorprendida" — sutil, contenida, no exagerada (apenas un parpadeo, una ceja que se mueve). La narración no lo describe en la primera partida; es una pista puramente visual.]*

*[Variante desde la 2ª partida (`g_ruta_egis_completada == true`): se inserta acá esta línea antes de la respuesta de Hazel — "Por una fracción de segundo algo le cambia la cara: la mano se le detiene a mitad de un trazo, un parpadeo que dura un poco más de lo normal."]*

Hazel: No.
Hazel: No me suena de nada.

Protagonista: Ah. Bueno, gracias igual.

Me alejo sin darle más vueltas al asunto.

*[Sprite de Hazel: "Pensativa" en cuanto el protagonista se aleja — se sostiene un instante antes de cortar.]*

*[Esta reacción es el gancho de la ruta de Hazel (ver `Heroina-C.md`). En la primera partida no se explica ni se comenta en el texto bajo ninguna circunstancia — toda la pista vive en el arte.]*

*Fin Escena 2.3 — continúa en Escena 2.4 (Explanada, atardecer).*

---

## ESCENA 2.4 — Explanada frente al edificio central, atardecer (Agnes)

*[BGM: "Footsteps in the Snow" (Tema social).]*

Cuando salgo de la universidad llama mi atención un grupo pequeño que va saliendo también.
Son bastante llamativos, debe ser el grupo de "populares".

*[Sprite de Agnes/Vaelyr: "Sonrisa confiada" durante este primer vistazo. Único vistazo a Agnes en el prólogo — el protagonista todavía no la conoce, no hay diálogo directo entre ambos más allá de este cruce a la distancia.]*

Entre ellos, noto a una chica en particular: rubia, carismática, el centro obvio de gravedad del grupo sin esforzarse por serlo.
La veo pasar, y por un segundo dejo de pensar en Vaelyria.

*[Estudiante 1 y 2 — sprite "Extra Genérico Femenino" de forma fija, no al azar (el séquito de Agnes es 100% femenino).]*

Estudiante: ...te digo que Marr tiene un alumno nuevo preguntando por una ciudad que no existe, algo como Va, Vael...

Estudiante: ¡Vael-boy!

*[Sprite de Agnes/Vaelyr: "Riendo" en este momento.]*

GrupoEstudiantes: JAJAJAJAJA

Sigo caminando, y cada vez noto con más claridad las miradas y los comentarios a media voz que me siguen por el campus.

Protagonista: *"Vael-boy." Ya tengo apodo. Genial.*

Termino un día más.

*Fin Escena 2.4 — corta a Escena 3 (La advertencia de Egis).*

---

## ESCENA 3 — La advertencia de Egis (Sábado)

*[Con esta escena arranca un nuevo día dentro del sistema de calendario del Bloque A — actualizar el indicador de día en UI a "Sábado" (Día 6) antes de que arranque. Ver `Bloque-A-Egis-Esquema.md`.]*

*[BGM: "Memories of Winter" (Tema de tensión suave).]*

Estoy solo entre las estanterías de la sección de historia regional, en la biblioteca central.
Ya está casi vacía a esta hora de la tarde.
Reviso el lomo de libros que ya revisé antes, más por costumbre que por esperanza.
Oigo pasos que se acercan. Suaves, controlados.

*[Nombre de Egis oculto ("???") desde acá hasta que se presenta a sí misma, más abajo. Sprite: "Seria" desde su entrada hasta el cambio a "Tensa".]*

Veo venir al final del pasillo a una chica.
Recordaría haberla visto anteriormente, su largo cabello blanco y su traje elegante no pasarían desapercibidos.
Se queda a una distancia prudente.
Lo suficientemente cerca para hablar sin subir la voz.
Y lo suficientemente lejos para que no exista posibilidad de contacto.
Parece que sabe medir el espacio perfectamente.

Egis: Eres el que anda preguntando por una ciudad que nadie conoce, ¿cierto?

Protagonista: Sí soy. Aunque ya perdí la cuenta de a cuántas personas les pregunté.

Egis: A bastantes. Se corrió la voz.

...

Se acerca un poco más, pero mantiene su postura firme y distante, se queda de pie, con los brazos cruzados de forma casi protectora.

Egis: No vine a burlarme, si es lo que estás pensando.
Egis: Vine a decirte algo que probablemente nadie más te va a decir con esta claridad:
Egis: Detente.

Protagonista: ¿Disculpa?

Egis: Deja de preguntar.
Egis: No creo que esté mal tener curiosidad.
Egis: De hecho, creo que es mejor que solo intentar aprobar las materias, como hacen la mayoría.
Egis: Pero seguir insistiendo en algo que nadie reconoce.
Egis: En voz alta.
Egis: Frente a cada vez más gente.
Egis: ...
Egis: No te va a dar la respuesta que buscas.
Egis: Y puedes tener consecuencias.

*[Elección de sabor — ambas opciones convergen en el mismo punto, sin afectar ninguna variable ni ruta.]*

> **"¿Consecuencias?"**
> **"¿Como un apodo?"**

**Si el jugador elige "¿Consecuencias?":**

*[Sprite de Egis: "Tensa".]*

No responde de inmediato.
Por un segundo algo se tensa en su postura, como si subiera la guardia.

Egis: Aprendí.
Egis: Hace tiempo.
Egis: Que hay preguntas que es mejor no hacer en voz alta.
Egis: No todos tienen tanto interés.

**Si el jugador elige "¿Como un apodo?":**

*[Sprite de Egis: "Triste".]*

Egis: Ojalá solo fuera un apodo.

**Sigue igual sea cual sea la opción elegida:**

Protagonista: ¿Me dejarías de hablar si pasa eso?

*[Sprite de Egis: "Sorprendida".]*

Egis: ¿Eh?

Protagonista: Bueno, no quisiera que esta fuera la última charla.

*[Sprite de Egis: "Sonrisa tímida" — pendiente de producción de arte.]*

Egis: Preferiría no ser la Vael-chica.

Protagonista: Tú también...

*[Sprite de Egis: vuelve a "Seria".]*

Me mira un momento más, evaluándome, con la curiosidad de alguien que reconoce algo familiar y no está segura de qué hacer con eso.

Egis: Recién llegaste.
Egis: No conoces a nadie todavía,
Egis: y ya estás construyendo fama de raro antes de terminar el primer mes.
Egis: Puedes seguir así si quieres.
Egis: Pero si te importa hacer amigos acá,
Egis: si te importa que la gente te trate como alguien normal,
Egis: es mejor no llamar tanto la atención.

...

La miro, y noto algo más allá de mis propias ganas de seguir investigando:
Ella no está actuando por fastidio.
Ni por seguir una norma social cualquiera.
Hay algo genuino ahí, algo que no termino de entender.
No me está mintiendo.
Pero tampoco me está contando todo.

---

### Punto de elección

*[Primera partida: solo la Opción A está disponible (no existe `g_ruta_egis_completada` todavía, o es `false`). Desde la 2ª partida en adelante (`g_ruta_egis_completada == true`), también se habilita la Opción B.]*

> **A. Seguir su consejo.** *(Siempre disponible.)*
> **B. Volver a preguntarle a Hazel.** *(Solo desde la 2ª partida.)*

---

#### Opción A — Hacerle caso a Egis *(cierre del prólogo, primera partida y siguientes)*

Protagonista: Está bien.
Protagonista: Voy a dejarlo por un tiempo.
Protagonista: Al menos en público.

Algo en su postura se afloja.
Como si se quitara una carga que no le correspondía.

Egis: Es lo más sensato que vas a hacer esta semana.

Protagonista: No prometo que se me vaya a pasar la curiosidad.

Egis: No te pedí eso.
Egis: Te pedí que no lo grites por los pasillos.

Se da media vuelta para irse.

Protagonista: ¿Cómo te llamas?

*[Sprite de Egis: "Mirada hacia atrás".]*

Egis: Egis.

*[Se presentó por su nombre — a partir de acá su nombre en pantalla deja de mostrar "???" y pasa a "Egis".]*

Protagonista: *Vaelyria puede esperar por ahora.*

Bibliotecaria: ¡Shhh!

*Fin del prólogo — Opción A. Continúa en Bloque A: Ruta Egis.*

---

#### Opción B — Preguntarle a Hazel en su lugar *(desbloqueada desde la 2ª partida)*

*[Egis nunca dice su nombre en esta rama — su nombre en pantalla se queda en "???" por el resto del prólogo.]*

Protagonista: Aprecio el consejo.
Protagonista: Pero no puedo simplemente soltarlo.

Egis no se sorprende.
Casi parece que lo esperaba.

Egis: Me imaginaba que ibas a decir algo así. Bueno. Es tu decisión.

Se va sin más reproche, con la misma calma con la que llegó.
Me quedo solo un momento entre las estanterías, y entonces recuerdo algo:
La reacción de Hazel, cuando le pregunté lo mismo.
Algo no me cuadra.

Hazel dijo que no sabía nada. Pero no parecía alguien que no sabe nada.

*Fin del prólogo — Opción B. Continúa en Bloque B: Ruta compartida Hazel/Vaelyr.*

---

## Correcciones aplicadas (ortografía y puntuación)

> ✅ Ya están hechas tanto en este documento como en los `.nani` de Unity.

| Escena | Error en el `.nani` | Corrección |
|---|---|---|
| Escena 0 | "a travez del tiempo" | "a través del tiempo" |
| Escena 0 | "que la hitoria se pierda" | "que la historia se pierda" |
| Escena 0 | "No he encontrade mucha informasobre esta ciudad" | "No he encontrado mucha información sobre esta ciudad" |
| Escena 0 | "me encargaré de manter viva su historia" | "me encargaré de mantener viva su historia" |
| Escena 1 | "........." (9 puntos, tras "Vine específicamente para investigar sobre Vaelyria.") | "..." (3 puntos) |
| Escena 2.1 | "voy a la bibliotecta" | "voy a la biblioteca" |
| Escena 2.3 | "No tengo nada qué perder." | "No tengo nada que perder." (sin tilde: no es una pregunta) |
| Escena 3 | "No conoces a nadie todavía. y ya estás construyendo fama..." | "No conoces a nadie todavía, y ya estás construyendo fama..." (coma, no punto — es una sola oración cortada en dos líneas; la "y" en minúscula ya estaba bien) |
| Escena 3 | "Pero si te importa hacer amigos acá, Si te importa que la gente..." | "...acá, si te importa que la gente..." (minúscula — sigue siendo la misma oración) |

## Otros hallazgos

- ✅ **Nombre unificado**: el personaje de la entrada se llama "Guardia" tanto acá como en `Personajes-Secundarios.md` y en el `.nani` — se descartó "Celador" por ser una palabra regional (en España, por ejemplo, significa otra cosa).
- ✅ **Rama duplicada del `@random`**: resuelta en el `.nani`.
- **Nota de contenido** (no es un error, queda solo para que lo tengas presente): la línea de pensamiento "Tengo que admitir que es muy linda" que tenía el Borrador 9 en la Escena 2.4 ya no está en el `.nani` — se asume como recorte intencional durante la implementación, no reincorporado acá.