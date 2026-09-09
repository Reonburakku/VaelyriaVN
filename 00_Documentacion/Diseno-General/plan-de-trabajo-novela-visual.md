# Plan de Trabajo — Novela Visual

Plan de tareas en orden sucesivo, agrupado por fases (según el documento de diseño). Cada fase tiene una entrega verificable al final, para que puedas confirmar que estás listo para pasar a la siguiente sin acumular deuda de alcance.

---

## FASE 0 — Preproducción

**Objetivo de la fase:** tener el mundo, los personajes y el pipeline técnico/artístico definidos antes de escribir una sola línea de guion final.

1. Escribir la "biblia" del mundo: reglas de la fantasía/sci-fi, geografía, facciones, tecnología o magia, tono general.
2. Escribir la ficha completa del protagonista (personalidad, motivación, arco, rol narrativo del jugador — ¿es mudo/POV o tiene personalidad propia?).
3. Escribir la ficha de cada una de las 3 heroínas (personalidad, arco, secreto o conflicto central, por qué sus 3 finales son distintos entre sí).
4. Definir el punto de quiebre donde el jugador elige ruta (qué pasa en el prólogo que motiva la elección).
5. Elegir el motor: instalar Unity + comprar/instalar Naninovel (o confirmar la alternativa Godot si cambias de decisión).
6. Hacer un proyecto vacío en el motor y correr el ejemplo/tutorial oficial de Naninovel hasta entender el flujo básico (texto, personaje, fondo, elección).
7. Elegir y probar la herramienta de arte con IA (Stable Diffusion + LoRA, Midjourney con character reference, NovelAI, etc.).
8. Prueba de consistencia de personaje: generar 10-15 imágenes de una sola heroína en distintas poses/expresiones y verificar que se reconoce como el mismo personaje. **Este paso es el que más se debe iterar — no avances de fase sin resolverlo.**
9. Elegir fuente de música/SFX (librería de stock o IA) y de voces (freelancer vs. síntesis) y hacer una prueba de una línea de diálogo con cada una.

**Entrega de la fase:** biblia + fichas de personajes escritas, motor instalado y probado, pipeline de arte con consistencia validada, prueba de audio hecha.

---

## FASE 1 — Vertical Slice (prólogo jugable de punta a punta)

**Objetivo de la fase:** demostrar que todo el pipeline (guion → arte → audio → motor → build) funciona junto, antes de escalar contenido.

10. Escribir el guion final del prólogo común (2-3 escenas, ~3,000-5,000 palabras) incluyendo el punto de elección de ruta.
11. Generar los fondos necesarios para el prólogo.
12. Generar los sprites del protagonista (si aplica) y de las 3 heroínas para las escenas del prólogo (expresiones básicas).
13. Conseguir/generar la música de fondo y los SFX del prólogo.
14. Grabar o sintetizar las voces de las líneas del prólogo (si decidiste doblar esta parte).
15. Implementar el prólogo completo en Unity/Naninovel: texto, personajes, fondos, elección de ruta, audio. 🔶 Primer paso antes de generar cualquier script: configurar el Source Locale en español (Naninovel → Configuration → Localization), para que el proyecto quede preparado para sumar idiomas más adelante sin reestructurar nada (ver documento de diseño, sección 6).
16. Implementar el sistema de guardado/carga (aunque sea básico) y probarlo dentro del prólogo.
17. Compilar un build de Android (y de iOS si tenés acceso a Mac/certificados) e instalarlo en un dispositivo real. 🔶 Opcional en esta fase: como Unity exporta a PC de forma nativa sin trabajo extra, podés probar también un build de Windows si te resulta cómodo, aunque no es obligatorio hasta la Fase 4.
18. Jugar el prólogo de principio a fin en el dispositivo real y corregir errores de texto, timing, audio o crasheos.

**Entrega de la fase:** prólogo 100% jugable en un dispositivo móvil real, de punta a punta, sin errores críticos.

---

## FASE 2 — Producción de rutas

**Objetivo de la fase:** completar el contenido de la ruta de Egis y de la ruta compartida Hazel/Vaelyr (con sus dos ramas finales), para poder detectar problemas de ritmo o alcance temprano en vez de al final.

🔶 **Nota de estructura**: a diferencia de una primera versión de este plan, esto ya **no son 3 rutas simétricas e independientes**. Son 2 bloques de producción:

- **Bloque A — Ruta Egis**: completamente independiente, con sus propios 3 finales.
- **Bloque B — Ruta compartida Hazel/Vaelyr**: un solo tramo principal (la investigación conjunta sobre la verdad de Vaelyria) que se escribe **una sola vez**, seguido de dos ramas finales cortas (Rama Hazel y Rama Vaelyr), cada una con sus propios 3 finales. Escribir el tramo compartido dos veces (una "para" Hazel y otra "para" Vaelyr) sería guion redundante — es la misma escena vista una sola vez, no dos historias paralelas.

Repetir los siguientes pasos **para cada bloque, de a uno por vez** (no en paralelo, salvo que tengas ayuda). Dentro del Bloque B, el tramo compartido se escribe primero y una sola vez; luego cada rama (Hazel, Vaelyr) se trabaja por separado solo para su tramo corto post-separación y sus 3 finales:

19. Escribir el guion del bloque:
    - Bloque A (Egis): guion completo hasta el punto donde se separan los 3 finales (~15,000-20,000 palabras).
    - Bloque B: guion del tramo compartido Hazel/Vaelyr hasta la separación (~15,000-20,000 palabras, una sola vez), luego el guion corto de cada rama post-separación (Hazel y Vaelyr, por separado).
      Marcar explícitamente los puntos de decisión y qué elección/afinidad lleva a qué final.
20. Escribir el guion de los 3 finales de cada heroína del bloque (~1,500-3,000 palabras cada uno).
21. Listar los "flags"/variables que el motor debe rastrear para ese bloque (qué elecciones y afinidades activan qué final), incluyendo las variables cross-ruta y la variable de progreso persistente entre partidas (`ruta_egis_completada`, ver documento de diseño sección 2).
22. Generar los fondos nuevos que necesite ese bloque (reutilizando los del prólogo y de otros bloques cuando sea posible).
23. Generar los sprites adicionales de las heroínas de ese bloque (expresiones nuevas, outfits si aplica).
24. Generar los CGs de los momentos clave del bloque y de sus finales.
25. Conseguir/generar música y SFX específicos del bloque (tema de cada heroína, tensión, etc.).
26. Grabar o sintetizar las voces definidas para ese bloque.
27. Implementar el bloque completo en el motor: guion, flags de decisión y afinidad, arte, audio.
28. Jugar el bloque completo de principio a fin (todos sus finales) y corregir errores.
29. Hacer que 1-2 testers externos jueguen el bloque y anotar su feedback (ritmo, claridad de las elecciones, bugs).

**Entrega de la fase (×2 bloques)**: Bloque Egis completo jugable con sus 3 finales, y Bloque Hazel/Vaelyr completo jugable con sus 6 finales (3+3), ambos probados por al menos un tester externo.

---

## FASE 3 — Finales, galería y pulido general

**Objetivo de la fase:** unificar las 3 rutas en un solo producto coherente y agregar las features que dan sensación de "juego terminado".

30. Implementar el sistema de galería de CGs desbloqueados.
31. Revisar consistencia de tono/calidad entre las 3 rutas (que ninguna se sienta claramente más corta o menos pulida que las otras).
32. Ajustar configuración de texto (velocidad, tamaño de fuente) y accesibilidad básica.
33. Diseñar y pulir el menú principal, pantalla de título, pantalla de créditos.
34. Revisión completa de guion (ortografía, coherencia de nombres/flags, continuidad entre elecciones).
35. Pase de pulido visual: transiciones entre escenas, animaciones de textbox, efectos de UI.
36. Optimizar tamaño final del build (compresión de imágenes/audio) para que el peso sea razonable en tiendas móviles y en Steam.

**Entrega de la fase:** juego completo, las 3 rutas y 9 finales integrados, galería funcional, build optimizado.

---

## FASE 4 — QA móvil

**Objetivo de la fase:** asegurar que el juego funciona de forma confiable en la variedad de dispositivos Android/iOS reales y en PC, no solo en tu dispositivo de prueba.

37. Armar una lista de dispositivos objetivo (gama alta, media y baja de Android, más algún iPhone y una PC de referencia para el build de Steam).
38. Probar instalación, guardado/carga y las 9 rutas de finales en cada dispositivo de la lista.
39. Medir rendimiento (tiempos de carga, uso de memoria) y ajustar si hay caídas de rendimiento en gama baja.
40. Revisar el juego en distintos tamaños/proporciones de pantalla (notch, tablets, etc.).
41. Corregir todos los bugs críticos y de prioridad alta detectados.
42. Hacer una ronda final de testers externos jugando el juego completo (no solo una ruta) para detectar problemas de conjunto.

**Entrega de la fase:** build estable validado en múltiples dispositivos reales, sin bugs críticos pendientes.

---

## FASE 5 — Lanzamiento

**Objetivo de la fase:** publicar el juego correctamente en las tiendas, con todo lo legal y de marketing en regla.

43. Completar el cuestionario de clasificación de contenido en Google Play, App Store y Steam (declarando el tono maduro sin contenido explícito).
44. Declarar el uso de arte generado por IA según las políticas vigentes de cada tienda al momento de publicar.
45. Escribir la política de privacidad y publicarla (requisito obligatorio de las tres tiendas).
46. Preparar los assets de tienda: ícono, capturas de pantalla, arte de portada, video/trailer si es posible, descripción del juego.
47. Definir el precio de venta (pago único, según lo decidido).
48. Configurar las cuentas de desarrollador (Google Play Console, Apple Developer y Steamworks) si no las tenés ya.
49. Subir el build a modo de prueba cerrada/interna en las tres tiendas y verificar que pasa la revisión técnica. 🔶 Steam tiene su propio calendario: hay una espera obligatoria de 30 días después de pagar el fee de Steam Direct ($100 USD, recuperable), más el requisito de tener la página "Coming Soon" publicada al menos dos semanas antes del lanzamiento — conviene arrancar este trámite con varias semanas de anticipación respecto a Google Play/App Store, que son más rápidos.
50. (Opcional) Hacer un soft launch en un mercado más pequeño antes del lanzamiento global, para detectar problemas con usuarios reales.
51. Lanzamiento global.
52. Monitorear reseñas y crashes la primera semana, y preparar un parche rápido de corrección si aparecen problemas críticos.

**Entrega de la fase:** juego publicado y disponible para compra en Android/iOS/PC (Steam).

---

## Nota sobre el orden

Las fases están pensadas para ejecutarse en este orden porque cada una **valida** un supuesto antes de invertir tiempo en escalarlo:

- Fase 0 valida que el pipeline de arte/audio/motor es viable.
- Fase 1 valida que todo el pipeline junto funciona en un dispositivo real.
- Fase 2 valida ritmo narrativo y calidad bloque por bloque (Egis, y luego Hazel/Vaelyr), antes de comprometerte a ambos completos.
- Fases 3-5 son de integración, calidad y lanzamiento, y solo tienen sentido una vez que el contenido central ya está probado.

Si en cualquier fase el tiempo real supera fuertemente la estimación (guion, arte o audio), es la señal para recortar alcance (ver sección 9 del documento de diseño) antes de seguir a la fase siguiente.
