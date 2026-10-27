# Notas de trabajo

Estado y decisiones de este video, para no volver a descubrirlas.

## Qué se está haciendo

Video vertical de 15 s del **exprimidor de limones USA MILER 20205M**, para redes.
Fondo blanco, cinco fotos del producto con zoom lento y corte seco, con música.

## Decisiones tomadas (y por qué)

- **El fondo blanco es marco, no fondo del producto.** La referencia tiene la máquina
  recortada sobre blanco puro. Se probó el recorte automático
  (`hyperframes remove-background`) sobre `assets/img/01.jpg` y **destruyó la foto**:
  el acero cromado y el acrílico naranja transparente confunden al modelo, que deja
  solo un manchón. Descartado. Para el look real hacen falta fotos sobre mesa blanca
  o fondo liso, sin galpón atrás.
- **Tarjeta de 700 × 1400** centrada en 1080 × 1920, radio 26, sombra suave. Es el
  encuadre que menos recorta la foto (0,97× de escala) y saca la marca de agua de
  WhatsApp de la parte de abajo.
- **Cinco tomas de 3 s** (`0, 3, 6, 9, 12`), 15 s totales. Orden actual:
  perfil con la marca → detalle de la canasta → placa de especificaciones →
  dos máquinas → frente (cierre).
- **Firma fija abajo**: `USA MILER` / `EXPRIMIDOR 20205M`, con una línea fina.
  Entra animada una vez al principio.
- **Música**: "Wallpaper" de Kevin MacLeod (incompetech.com), CC BY 4.0, recortada
  del segundo 4,225 (pulso fuerte) a 15 s, con fundido de entrada y salida.
  **Requiere crédito** (`Música: Kevin MacLeod — incompetech.com (CC BY 4.0)`).
  Se reemplaza por `assets/audio/bed.mp3`, manteniendo 15 s.

## Pendiente

- Decidir si se saca la toma de la placa (6–9 s): es la más débil, tiene una mano
  y una grieta en la pared. Si se saca, las otras cuatro quedan en 3,75 s.

## Cómo se trabaja

1. Editar `index.html` (y `assets/`) y hacer push a `main`.
2. `.github/workflows/render.yml` corre en GitHub: `check` → capturas → render.
3. El MP4 queda en la release [`latest`](../../releases/tag/latest) y como artifact.
4. Las capturas y el `check.json` quedan en el artifact `frames` de cada ejecución:
   se miran desde ahí, **sin abrir Chromium en la máquina local**.

El render es gratis e ilimitado en un repo público. El modelo que edita no es
ilimitado: cada turno consume saldo, y el contexto largo cuesta más.
