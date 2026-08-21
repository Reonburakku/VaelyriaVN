# Prompt de identidad — Vaelyr (forma humana / Agnes)

> Generado y validado en NovelAI Diffusion (V4.5) durante la tarea 8 de la Fase 0 (prueba de consistencia de personaje). Consistencia confirmada en: color/largo/forma de pelo, color y forma de ojos, forma de cara, ropa, color de piel, forma corporal. Sampler usado: Euler Ancestral. Seed fija entre generaciones (guardar la seed específica junto a las imágenes finales cuando se generen para producción).

## Prompt de identidad (fijo — no modificar entre generaciones)

```
1girl, solo, long wavy hair, hair between eyes, hair over shoulder, blonde hair, green eyes, tan skin, gyaru, white t-shirt, crop top, short sleeves, fitted, blue denim shorts, high-waisted shorts, frayed denim shorts, gold necklace, thin chain necklace, delicate necklace, pendant shaped like a dragon fang, hoop earrings, bracelet on left wrist, gold bracelet, bangle bracelet, wide bracelet, medium breasts, university student, laughing, open mouth, closed eyes, teeth, looking the viewer, simple background, white background, upper body, masterpiece, best quality, amazing quality
```

🔶 Pendiente: definir si el colgante es diente/colmillo (`fang pendant, tooth pendant`, usado en la prueba) o escama (`pendant shaped like a golden dragon scale`) — ver conversación de diseño. También pendiente: especificar que la pulsera va en una sola muñeca (agregar `single bracelet` o especificar la muñeca) para evitar que la IA la duplique en ambas manos.

## Tags de calidad/composición (fijos, no afectan identidad)

```
masterpiece, best quality, amazing quality, simple background, white background
```

## Capa variable (cambiar según la imagen: expresión, pose, encuadre)

Ejemplos ya probados:
- `confident smile` / `smirk` (sarcasmo, muy propio de su personalidad hacia Hazel)
- `surprised, hand over mouth`
- `hand on hip`
- `angry, scowl` (enojo contenido, más fiel a su personalidad que `furious`)
- `laughing, open mouth, closed eyes, teeth` (carcajada — fuera de personaje en escenas con Hazel presente, ver ficha)

Encuadre/ángulo: `upper body`, `looking at viewer`, `looking away`, `three-quarter view`, `cowboy shot`, `close-up`

## Configuración técnica

- Sampler: Euler Ancestral (default de NovelAI) — considerar cambiar a un sampler no-ancestral (Euler simple, DPM++ 2M) si se necesita mayor repetibilidad exacta.
- Reference Strength (si se usa Vibe Transfer, requiere plan pago): probar desde 0.6–0.7.
- Information Extracted: dejar en default salvo problema específico de composición/fondo no deseado.

## Prompt negativo (UC) sugerido

```
multiple girls, extra limbs, bad anatomy, different hair color, different eye color, frayedshorts, tornshorts, ripped shorts, bracelet on right wrist
```