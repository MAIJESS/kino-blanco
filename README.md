# Kino TV · Liquid Glass

Plugin de **temas de la app** (`apiVersion 18`) para Kino TV con el acabado de **cristal líquido**: superficies translúcidas, bordes de luz, esquinas continuas y una aurora azul de fondo, en el celular y en el TV.

| Tema | `id` | Look |
|---|---|---|
| **Kino TV · Liquid Glass** | `liquid-glass` | Noche azul profunda con aurora, acento azul cielo `#6FAEFF` y foco casi blanco. |
| **Kino TV · Liquid Glass Claro** | `liquid-glass-claro` | Cristal esmerilado sobre fondo claro con reflejos lila y celeste, acento azul `#0A63E6`. |

Cada tema cambia colores, fondo en degradado, esquinas, bordes, sombras, movimiento, controles del reproductor y **el logo de Kino** (menú lateral, cabecera del celular y riel del TV) por un logo vectorial propio: un icono de cristal con brillo superior y botón de play, junto a la palabra **KINO TV**.

> Proyecto de fans, sin relación con Apple. Es solo un tema inspirado en el estilo de cristal; no incluye imágenes, fuentes ni arte con derechos de autor. Es gratis y no cobra kinos.

## Requisitos

- **Kino 0.9.81 o posterior** (`"apiVersion": 18`). Los Kino anteriores muestran «Este plugin necesita una versión más nueva de Kino».
- Los bordes (`*Border`, `colors.border`) necesitan **Kino 0.9.82**; en 0.9.81 se ignoran y el tema se ve igual, sin bordes.
- Sin red ni datos: `"hosts": []` y ninguna capacidad.

## Instalación

1. Publica esta carpeta en un repositorio de GitHub (por ejemplo `tu-usuario/kino-theme-liquid-glass`).
2. En Kino: **Ajustes ▸ Plugins ▸ Agregar** y escribe `tu-usuario/kino-theme-liquid-glass`.
3. Ve a **Ajustes ▸ Apariencia**, elige *Liquid Glass* o *Liquid Glass Claro* y toca **Usar este tema**. Kino preguntará si quieres la experiencia completa (recomendada: bordes y sombras).

Para volver al aspecto original: **Apariencia ▸ Tema de Kino**.

## Archivos

```
kino-plugin.json   Manifiesto con los dos appThemes (colores, logo, ajustes...)
plugin.js          Punto de entrada; el tema es solo datos y no ejecuta nada
README.md          Este archivo
icon.png           Ícono del plugin (propuesta visual, 256×256)
icon.svg           Fuente editable del ícono (opcional, Kino lo ignora)
```

## Qué puede ajustar la persona

En **Apariencia ▸ Personalizar** (solo lo marcado como `adjustable`):

- **Color de acento**: azul, violeta, turquesa y rosa en el tema oscuro; azul, violeta y verde azulado en el claro.
- **Color del borde**: tres muestras por tema.
- **Redondeo de las tarjetas**: de 8 a 32.
- **Escala del texto**: de 1,0 a 1,2.
- **Fondo**.

## Paleta

| | Liquid Glass | Liquid Glass Claro |
|---|---|---|
| Acento | `#6FAEFF` | `#0A63E6` |
| Texto sobre acento | `#04121F` | `#FFFFFF` |
| Fondo (degradado) | `#05080F → #0B1430 → #141B4A` | `#EDF2FA → #F6F1FF → #E9F7FF` |
| Superficie | `#131A31` | `#F8FBFF` |
| Texto | `#F4F8FF` | `#0A1020` |
| Foco (TV) | `#D7E7FF` | `#0A63E6` |
| Borde | `#7D93C4` | `#C9D9EF` |

## Forma y movimiento

- Esquinas grandes y continuas: tarjetas y canales 24, botones 26, diálogos 30, entradas 18 (en TV, 20 / 20 / 24).
- Borde de 1 px en tarjetas, paneles, diálogos, menús y cabecera: el «borde de luz» del cristal.
- Zoom de foco 1,07 (1,06 en TV), fundido de 280 ms y deriva suave de la imagen principal.
- Reproductor con botones circulares, botón de play al 116 % y barra de progreso al 110 %.

## Logo propio

- `wordmark` (111×30): el icono de cristal más la palabra **KINO TV**.
- `mark` (30×30): solo el icono (riel cerrado del TV).
- Solo vectores, con `fill` ligado al tema (`accent`, `onAccent`, `textPrimary`) o blanco fijo para el brillo, así el logo cambia con el acento que elija la persona. Kino mantiene su propio logo en la pantalla de inicio y en las pantallas que piden una decisión.

## Probar en local

Con el kit del repositorio [kinotvapp/kino-plugins](https://github.com/kinotvapp/kino-plugins):

```
node sdk/validate.mjs .      # formato, rangos y protecciones de legibilidad (celular y TV)
```

El kit no dibuja colores: revisa el resultado en Kino (**Ajustes ▸ Apariencia ▸ vista previa**) en un celular y en un TV.

## Notas para quien edite el tema

- **Nunca cambies los `id` de los temas** tras publicar: de ellos cuelgan la elección y los ajustes de cada persona.
- Un valor fuera de rango no rompe nada: Kino lo descarta con una advertencia. Un error de formato (token desconocido, tipo equivocado) rechaza todo el manifiesto.
- El manifiesto tiene un tope de 16 KB; si añades logos o temas, vigila el tamaño.
- Si cambias el manifiesto, súbelo con una versión nueva (`version`) para que Kino vuelva a resolver los temas.

Documentación oficial: <https://kinotvapp.github.io/kino-plugins/themes/>

## Licencia

Código y manifiesto bajo MIT.
