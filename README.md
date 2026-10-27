# hyperframes-cloud

Video hecho con [HyperFrames](https://hyperframes.heygen.com) que se **renderiza en la nube de GitHub**.
La computadora local solo se usa para editar archivos de texto: el render (Chromium + FFmpeg) corre en
un runner de GitHub Actions.

## Cómo funciona

1. Se edita el proyecto (`index.html`, `compositions/`, `assets/`).
2. Al hacer push a `main`, se dispara `.github/workflows/render.yml`.
3. El workflow corre `hyperframes check` (control de calidad), saca capturas de revisión y renderiza
   `out/video.mp4` en la máquina de GitHub.
4. El MP4 queda como **artifact** de la ejecución y, además, se publica en la release
   [`latest`](../../releases/tag/latest) — se descarga desde ahí sin instalar nada.

## Dónde ver el resultado

| Qué | Dónde |
| --- | --- |
| Video final | Pestaña **Releases** → `latest` → `video.mp4` |
| Última ejecución | Pestaña **Actions** → workflow `Render` |
| Frames de revisión | Dentro de la ejecución → *Artifacts* → `frames` |
| Reporte del check | *Artifacts* → `frames` → `check.json` |

## Correrlo a mano

**Actions** → `Render` → **Run workflow**:

- `quality`: `draft` (rápido, para iterar), `looks` (por defecto) o `delivery` (final).
- `frames`: los segundos donde sacar capturas, por ejemplo `1,3,5`.

## Trabajar localmente (opcional)

Requiere Node 22+ y FFmpeg.

```bash
npm run dev      # preview en el navegador
npm run check    # lint + runtime + layout + contraste
npm run render   # MP4 local
```

## Render gestionado opcional (HeyGen)

Si en algún momento querés el render oficial de HyperFrames en la nube de HeyGen
(`hyperframes cloud render`, más rápido y con 4K/alpha), hace falta una cuenta HeyGen y un
`HEYGEN_API_KEY` como secret del repo. El flujo de GitHub Actions actual no lo necesita.

## Estructura

```
index.html                 composición raíz (timeline principal)
compositions/              sub-composiciones y bloques del catálogo
assets/                    imágenes, audio, fuentes, video
hyperframes.json           configuración del proyecto
.github/workflows/         el render en la nube
```
