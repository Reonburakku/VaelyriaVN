Prólogo — Guion final (Borrador 9)

> Tarea 10 del plan de trabajo — Fase 1 (Vertical Slice). Prólogo común a todas las partidas. Incluye el punto de elección de ruta. No incluye contenido explícito ni desnudos (política confirmada).
>
> **Cambio respecto al Borrador 8**: reescribí partes del guion para que quede escrito con mi forma de escribir. Hice cambios menores para que los diálogos de los personajes coincidan con la personalidad que imagino para ellos.
>
> **Revisión aplicada sobre este Borrador 9**: corrección ortográfica, dos restos de voseo pasados a tuteo ("tenés"→"tienes", "buscás"→"buscas"), una acotación de tono duplicada, y un "Valirya" tratado como typo de "Vaelyria" (según la regla ya acordada). El contenido narrativo no se tocó — ver el resto de la conversación para los puntos que sí requieren una decisión tuya antes de tocarlos.
>
> Notas técnicas para Naninovel (implementación en tarea 15) marcadas entre corchetes en cursiva. Su nombre real lo define el jugador vía variable — donde haga falta pronunciarlo en diálogo ajeno, se marca `{Nombre}`. El nombre de Egis usa el mismo mecanismo de variable (name binding) pero en sentido inverso — empieza oculto ("???") y se revela a mitad de la Escena 3; ver las notas técnicas puntuales en esa escena.

---

## ESCENA 1 — Primer día

Entro al aula de arqueología. Es media mañana de finales de verano, y el aula se va llenando de a poco con otros estudiantes de primer año. Noto la formalidad en la vestimenta de la mayoría, es evidente que quieren empezar con pie derecho.

Encuentro un lugar cerca de la ventana, con buena iluminación. Dejo la maleta en el piso y saco mi libreta, ya gastada en los bordes, reviso las notas que he tomado acerca de "la gran ciudad de Vaelyria" siempre me ha llamado la atención desde que supe de ella, una gran ciudad tecnológica, que ha sido mencionada en diversos textos, aunque no he encontrado literatura que hable específicamente de esta. A eso vine, deduje que esta es la ubicación, aunque ahora tiene otro nombre, espero encontrar más información que las cortas menciones que he conseguido.

Entra la profesora, una mujer tan elegante que usa su abrigo de pana a pesar del calor. Deja sus cosas en el escritorio sin apuro y mira al grupo con la calma de quien ha dado esta misma clase innumerables veces.

*[Nota de arte/dirección: sprite de Marr = "Idle" (expresión base) desde su entrada hasta el cambio a "Pensativa" más abajo.]*

**PROF. MARR**
Bienvenidos a Introducción a la Arqueología. Antes de repartir el programa, quiero que cada uno diga su nombre y, si ya lo tiene claro, qué período o región le interesa investigar. Si aún no lo saben, les recomiendo empezar a pensarlo, la historia no se descubre por casualidad.

Empieza la ronda de presentaciones. Menciones dispersas de Mesopotamia, la Ruta de la Seda, arqueología subacuática del Mediterráneo. Nada que se detenga demasiado. Me llega el turno.

*[Nota técnica para Naninovel: este es el primer uso de la variable `{Nombre}` en todo el guion — es el punto donde se le debe pedir al jugador que ingrese su nombre (o confirme el que venga por defecto, ver Protagonista.md), justo antes de mostrar esta línea. Sumarlo a la tarea 21 (listado de flags/variables) y a la tarea 15 (implementación del prólogo).]*

**PROTAGONISTA**
Me llamo {Nombre}. Vine  específicamente para investigar sobre Vaelyria.

.........
Silencio breve. No el silencio de quien reconoce el nombre y lo sopesa, sino el de quien lo escucha por primera vez y no sabe bien qué hacer con él. La profesora Marr frunce el ceño, genuinamente pensativa, no hostil.

*[Nota de arte/dirección: sprite de Marr = "Pensativa" en este momento.]*

**PROF. MARR**
¿Vaelyria... como asentamiento, dices? No me suena el nombre. ¿Es una variante regional de algo, o...?

**PROTAGONISTA**
Aparece mencionada en varias fuentes como una ciudad importante, próspera, con un crecimiento inusualmente rápido para su época. Nunca encontré un texto que la describiera directamente, solo referencias de paso, como cualquier ciudad que simplemente existe.

**ESTUDIANTES DE FONDO**

¿Vaelyria?

¿Te suena ese nombre?

Para nada

**PROF. MARR**
No conozco ese nombre. Puede que sea una mala traducción, o una confusión con otra ciudad. Tráigame las fuentes que tenga cuando quiera y le echamos un ojo con calma. Aunque es difícil que yo no haya escuchado de una ciudad tan importante como la que menciona.

**PROTAGONISTA**
Por supuesto.

Ella sigue con la ronda.

**PROTAGONISTA**
*(hablando para sí mismo)*
Alguien debería saber.

*[Nota de dirección: la reacción de Marr debe leerse como genuinamente profesional y curiosa, no despectiva — es importante que el primer rechazo no se sienta personal. El endurecimiento social viene después, en la Escena 2, cuando la pregunta se repite fuera de un contexto académico protegido.]*

*Corte.*

---

## ESCENA 2 — Preguntas sin respuesta

*Estructura de esta escena: después de la biblioteca (2.1), tres días de intentos fallidos con elección de destino a cargo del jugador, seguidos de un cuarto día que fuerza la decisión de quedarse en el aula (2.3) — que a su vez desemboca en el cruce con Agnes esa misma tarde (2.4).*

### 2.1 — Biblioteca central, tarde

Estoy frente al mostrador de referencia. La bibliotecaria, una mujer mayor con lentes colgando de una cadena, escucha mi pregunta con paciencia y termina negando con la cabeza.

*[Nota de arte/dirección: sprite de la Bibliotecaria = "Idle" (expresión base) desde que aparece hasta el cambio a "Lástima" más abajo.]*

**BIBLIOTECARIA**
Busqué en el catálogo general y en los índices de historia regional. No encuentro nada relacionado con Vaelyria, ni como tema principal ni como referencia. Si quieres, te dejo anotado el pedido y lo reviso con más calma esta semana.

**PROTAGONISTA**
Se lo agradezco. Voy a seguir buscando por mi cuenta también.

Me mira un segundo de más, con esa mezcla de simpatía y lástima que se les da a los estudiantes obsesionados con algo que probablemente no lleve a ningún lado.

*[Nota de arte/dirección: sprite de la Bibliotecaria = "Lástima" en este momento.]*

### Días 1 a 3 — Preguntando por el campus, horario de almuerzo

*[Nota técnica para Naninovel: bucle de 3 días. Cada día se ofrece una elección entre los destinos que todavía no se visitaron — el Día 1 ofrece los 3, el Día 2 ofrece los 2 restantes, y el Día 3 avanza directo al único que queda, sin necesidad de mostrar una elección real ese día. El contenido de cada destino no cambia según el día en que se visite; lo único que varía es el orden, que depende de lo que elige el jugador. Los tres destinos terminan visitándose siempre, sin excepción.]*

Durante el almuerzo, puedo aprovechar para obtener información.

**[Elección de destino]**

> **Ir al restaurante** (comedor universitario)
> **Ir al jardín**
> **Ir a la entrada de la universidad**

#### Destino: Restaurante

Me acerco a una mesa donde reconozco un par de caras de mi clase de arqueología. Apenas menciono "Vaelyria", uno de ellos suelta una risa corta, nada amable.

**ESTUDIANTE**
Ah, eres tú. El de la ciudad que no existe.

**PROTAGONISTA**
¿Entonces la conoces?

**ESTUDIANTE**
No, no puedo conocer algo que no existe.

Nadie en la mesa tiene nada más que ofrecer.

Pregunto a unos cuantos estudiantes, antes de comer.

#### Destino: Jardín

El jardín interior de la facultad está tranquilo a esta hora. Veo un par de estudiantes leyendo bajo la sombra de un árbol. Me acerco suavemente, tratando de sonar casual.

**ESTUDIANTE**
¿Vaelyria? Ni idea. ¿Es de una serie o algo?

**PROTAGONISTA**
No, es... da igual. Gracias de todas formas.

Vuelvo sobre mis pasos antes de que me pregunten por qué me interesa tanto algo que, para ellos, ni siquiera existe.

#### Destino: Entrada de la universidad

Pruebo en la entrada, con el personal de seguridad y algunos estudiantes que van llegando tarde. Uno de los guardias, más por cortesía que por interés real, me escucha hasta el final.

**GUARDIA**
Llevo doce años acá y nunca escuché ese nombre. Lo siento.

*[Nota de arte/dirección: sprite de guardia genérico = "Lástima" en este momento.]*

**PROTAGONISTA** *(pensamiento)*
Bueno, no podía esperar más.

*[Nota de guion: los tres destinos usan personajes anónimos de una sola aparición (Estudiante, Estudiante, Guardia) — usan los sprites genéricos "Extra Genérico Femenino/Masculino" (ver `Personajes-Secundarios.md`), elegidos al azar en cada uno ya que ninguno especifica género.]*

### Día 4

**[Única opción disponible]**

> **Quedarme en el aula**

*Corte a la Escena 2.3.*

### 2.3 — Aula vacía, hora de almuerzo

Me quedo en el aula de la electiva de arte, reviso mi vieja libreta con apuntes sobre Vaelyria. La mayoría sale corriendo a almorzar, pero no tengo ganas de cruzarme con gente que ya empieza a mirarme raro. No estoy solo: Hazel también se quedó, sentada en su lugar de siempre, ya terminó de comer y aprovecha el rato libre para estudiar antes de que vuelva el resto.

*[Nota de arte/dirección: sprite de Hazel = "Estudiando" desde su introducción hasta el cambio a "Sorprendida" más abajo.]*

No tengo nada qué perder.

**PROTAGONISTA**
¿Hazel, cierto? Compartimos la electiva de arte. Te quería preguntar algo rápido, si tienes un segundo.

**HAZEL**
*(sin levantar mucho la vista)*
Depende de la pregunta.

**PROTAGONISTA**
¿Alguna vez escuchaste el nombre "Vaelyria"? Como ciudad, como región, lo que sea.

*[Nota de arte/dirección: sprite de Hazel = "Sorprendida" en este instante — pero una sorpresa sutil, contenida, no exagerada (apenas un parpadeo, una ceja que se mueve, nada de boca abierta ni gesto grande). La narración NO lo describe ni lo menciona en la primera partida. Es una pista puramente visual, solo para el jugador que esté mirando la pantalla justo en ese momento. Ver variante de segunda partida en adelante más abajo.]*

**HAZEL**
*(recuperándose casi de inmediato, con un tono demasiado neutro para ser natural)*
No. No me suena de nada.

**PROTAGONISTA**
Ah. Bueno, gracias igual.

Me alejo sin darle más vueltas al asunto.

*[Nota de arte/dirección: sprite de Hazel = "Pensativa" en cuanto el protagonista se aleja — sostener un instante antes de cortar a la escena siguiente.]*

*[Nota de guion: esta reacción de Hazel es el gancho de su ruta (ver Heroina-C.md). En la primera partida no debe explicarse ni comentarse en el texto bajo ninguna circunstancia — toda la pista vive en el arte. Ver variante de segunda partida en adelante, abajo.]*

**Variante — desde la segunda partida (`ruta_egis_completada == true`)**

Mismo diálogo, con un solo agregado: entre la pregunta del protagonista y la respuesta de Hazel se inserta esta línea de narración —

Por una fracción de segundo algo le cambia la cara: la mano se le detiene a mitad de un trazo, un parpadeo que dura un poco más de lo normal.

### 2.4 — Explanada frente al edificio central, atardecer

Un grupo pequeño cruza la explanada entre risas, son bastante llamativos, deben ser el grupo de "populares", entre ellos, noto a una chica en particular: rubia, carismática, el centro obvio de gravedad del grupo sin esforzarse por serlo. No la conozco. La veo pasar, y por un segundo dejo de pensar en Vaelyria.

*[Nota de arte/dirección: sprite de Agnes = "Sonrisa confiada" durante este primer vistazo.]*

**PROTAGONISTA** *(pensamiento)*
Tengo que admitir que es muy linda.

**ESTUDIANTE 1 (VOZ ENTRE EL GRUPO)**
...te digo que Marr tiene un alumno nuevo preguntando por una ciudad que no existe, algo como Va, Vael...

**ESTUDIANTE 2 (VOZ ENTRE EL GRUPO)**
¡Vael-boy!

*[Nota de guion: Estudiante 1 y 2 usan el sprite "Extra Genérico Femenino" (ver `Personajes-Secundarios.md`) de forma fija, no al azar — el séquito de Agnes es 100% femenino.]*

Risas de todo el grupo — incluida ella.

*[Nota de arte/dirección: sprite de Agnes = "Riendo" en este momento.]*

Sigo caminando, y cada vez noto con más claridad las miradas y los comentarios a media voz que me siguen por el campus.

*[Nota de guion: este es el único vistazo a Agnes en el prólogo (aquí sin nombre, ya que el protagonista todavía no la conoce). No debe haber diálogo directo entre ella y él todavía más allá de este cruce a la distancia — sigue funcionando como ambientación, estableciéndola visualmente como la figura popular del campus antes de que aparezca con más peso en rutas posteriores.]*

**PROTAGONISTA** *(pensamiento)*
"Vael-boy." Ya tengo apodo. Genial.

*Corte a Escena 3.*

---

## ESCENA 3 — La advertencia de Egis

Estoy solo entre las estanterías de la sección de historia regional, en la biblioteca central. Ya está casi vacía a esta hora de la tarde. Reviso el lomo de libros que ya revisé antes, más por costumbre que por esperanza. Oigo pasos que se acercan. Suaves, controlados.

Veo venir al final del pasillo a una chica. Recordaría haberla visto anteriormente, su largo cabello blanco y su traje elegante no pasarían desapercibidos. Se queda a una distancia prudente, lo suficientemente cerca para hablar sin subir la voz, y lo suficientemente lejos para que no exista posibilidad de contacto, parece que sabe medir el espacio perfectamente.

*[Nota de arte/dirección: sprite de Egis = "Seria" desde su entrada hasta el cambio a "Tensa" más abajo.]*

*[Nota técnica para Naninovel: el jugador todavía no conoce el nombre de Egis en este punto — usar name binding (Display Name atado a una variable, ej. {NombreEgis}) en vez de un nombre fijo en la configuración del personaje. Al principio de esta escena, antes de su primera línea: `@set NombreEgis="???"`. El cambio a su nombre real va marcado más abajo, en el momento exacto donde se lo dice al protagonista — no antes.]*

**EGIS**
Eres el que anda preguntando por una ciudad que nadie conoce, ¿cierto?

**PROTAGONISTA**
Sí soy. Aunque ya perdí la cuenta de a cuántas personas les pregunté.

**EGIS**
A bastantes. Se corrió la voz.

.....

Se acerca un poco más, pero mantiene su postura firme y distante, se queda de pie, con los brazos cruzados de forma casi protectora.

**EGIS**
No vine a burlarme, si es lo que estás pensando. Vine a decirte algo que probablemente nadie más te va a decir con esta claridad: detente.

**PROTAGONISTA**
¿Disculpa?

**EGIS**
Deja de preguntar. No creo que esté mal tener curiosidad, de hecho, creo que es mejor que solo intentar aprobar las materias, como hacen la mayoría. Pero seguir insistiendo en algo que nadie reconoce, en voz alta, frente a cada vez más gente... no te va a dar la respuesta que buscas. Y puedes tener consecuencias.

*[Nota técnica para Naninovel: acá se abre un menú de dos opciones. Es una elección de sabor — ambas convergen en el mismo punto de la escena, no genera ninguna variable ni afecta ninguna ruta.]*

> **Opción 1**: "¿Consecuencias?"
> **Opción 2**: "¿Como un apodo?"

**Si el jugador elige "¿Consecuencias?":**

No responde de inmediato. Por un segundo algo se tensa en su postura, como si subiera la guardia.

*[Nota de arte/dirección: sprite de Egis = "Tensa" en este momento.]*

**EGIS**
Aprendí, hace tiempo, que hay preguntas que es mejor no hacer en voz alta. No todos tienen tanto interés.

**Si el jugador elige "¿Como un apodo?":**

**EGIS**
*(susurrando)*
Ojalá solo fuera un apodo.

*[Nota de arte/dirección: sprite de Egis = "Triste" en este momento.]*

**Sigue igual sea cual sea la opción elegida:**

**PROTAGONISTA**
¿Me dejarías de hablar si pasa eso?

**EGIS**
¿Eh?

**PROTAGONISTA**
Bueno, no quisiera que esta fuera la última charla.

**EGIS**
*(con algo parecido a media sonrisa, la primera grieta en su tono)*
Preferiría no ser la Vael-chica.

*[Nota de arte/dirección: sprite de Egis = "Sonrisa tímida" en este momento.]*

Me mira un momento más, evaluándome, con la curiosidad de alguien que reconoce algo familiar y no está segura de qué hacer con eso.

**EGIS**
Recién llegaste. No conoces a nadie todavía, y ya estás construyendo fama de raro antes de terminar el primer mes. Puedes seguir así si quieres. Pero si te importa hacer amigos acá, si te importa que la gente te trate como alguien normal, es mejor no llamar tanto la atención.

Silencio. La miro, y noto algo más allá de mis propias ganas de seguir investigando: ella no está actuando por fastidio ni por seguir una norma social cualquiera. Hay algo genuino ahí, algo que no termino de entender. No me está mintiendo. Y tampoco me está contando todo.

---

### [PUNTO DE ELECCIÓN — Nota técnica para Naninovel, tarea 21]

> - En la **primera partida**, solo está disponible la Opción A. La Opción B no se muestra (no existe la variable `ruta_egis_completada` todavía, o su valor es `false`).
> - Desde la **segunda partida en adelante** (`ruta_egis_completada == true`, guardado persistente entre partidas — ver documento de diseño, sección 2), se habilita también la Opción B.
> - Este nodo es el "punto de quiebre" mencionado en la tarea 4 del plan de trabajo.

**Elección presentada al jugador:**

> **A. Seguir el consejo de Egis.** *(Siempre disponible.)*
> **B. Volver a preguntarle a Hazel** *(Solo visible desde la 2ª partida.)*

---

#### Opción A — Hacerle caso a Egis *(cierre del prólogo, primera partida y siguientes)*

**PROTAGONISTA**
Está bien. Voy a dejarlo por un tiempo. Al menos en público.

Algo en su postura se afloja. Como si se quitara una carga que no le correspondía.

**EGIS**
Es lo más sensato que vas a hacer esta semana.

**PROTAGONISTA**
No prometo que se me vaya a pasar la curiosidad.

**EGIS**
No te pedí eso. Te pedí que no lo grites por los pasillos.

Se da media vuelta para irse.

**PROTAGONISTA**
¿Cómo te llamas?

**EGIS**
Egis.

*[Nota técnica para Naninovel: acá se revela el nombre — `@set NombreEgis="Egis"`, justo antes o junto con esta línea. De acá en adelante (resto del prólogo y toda su ruta) el Display Name ya muestra "Egis" en vez de "???" automáticamente.]*

*[Nota de arte/dirección: sprite de Egis = "Mirada hacia atrás" en este momento.]*

**PROTAGONISTA**
*(hablando para sí mismo)*
Vaelyria puede esperar. Por ahora.

**BIBLIOTECARIA**
¡Shhh!

*[Fin del prólogo — Opción A. Continúa en Bloque A: Ruta Egis (Fase 2, tarea 19). No se desarrolla más contenido de ruta en este documento.]*

---

#### Opción B — Preguntarle a Hazel en su lugar *(desbloqueada desde la 2ª partida)*

**PROTAGONISTA**
Aprecio el consejo. Pero no puedo simplemente soltarlo.

Egis no se sorprende — casi parece que lo esperaba.

**EGIS**
Me imaginaba que ibas a decir algo así. Bueno. Es tu decisión.

Se va sin más reproche, con la misma calma con la que llegó. Me quedo solo un momento entre las estanterías, y entonces recuerdo algo: la reacción de Hazel, cuando le pregunté lo mismo. Algo no me cuadra.

Hazel dijo que no sabía nada. Pero no parecía alguien que no sabe nada.

*Corte.*

*[Fin del prólogo — Opción B. Continúa en Bloque B: Ruta compartida Hazel/Vaelyr (Fase 2, tarea 19). No se desarrolla más contenido de ruta en este documento.]*

---

## Notas para el pase de consistencia (a revisar antes de aprobar esta tarea)

- [ ] **Pendiente de producción de arte**: todas las expresiones puntuales especificadas en el guion del prólogo ya están consolidadas en `Lista-Expresiones-Sprites.md` — hay que sumarlas a la tarea 8 (prueba de consistencia) y la tarea 12 (sprites del prólogo) para que no se pierdan al armar el set genérico de cada personaje.
- [ ] Decidir si el diálogo de Egis revela demasiado sobre su propio trauma ("aprendí que hay preguntas que es mejor no hacer en voz alta") — se dejó deliberadamente ambiguo, sin mencionar a su madre ni petrificación.
- [ ] Verificar longitud final una vez cerrado el pulido (objetivo: 3,000–5,000 palabras).
