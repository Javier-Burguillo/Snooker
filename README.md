# Snooker

Marcador de snooker para iPhone. Lleva la puntuación de un frame bola a bola, aplica las faltas según el reglamento y muestra en todo momento el máximo que queda en la mesa y los snookers que necesita cada jugador.

Es una aplicación web sin servidor: un único `index.html` que funciona en el navegador, se instala en la pantalla de inicio con su propio icono y sigue funcionando sin conexión.

## Funciones

- **Anotación bola a bola.** Solo se activan las bolas legales en cada momento: roja y color mientras quedan rojas, cualquier color tras la última roja y después la secuencia amarilla → verde → marrón → azul → rosa → negra. Varias rojas en el mismo golpe se anotan tocando la roja otra vez antes del color.
- **Máximo en mesa.** Se recalcula tras cada jugada:
  - en roja: `rojas × 8 + 27`
  - en color tras una roja: `7 + rojas × 8 + 27`
  - en la secuencia final: la suma de los colores que quedan
- **Valor de las bolas en mesa**, rojas restantes, diferencia entre jugadores y break actual.
- **Faltas** de 4 a 7 puntos para el rival. En la secuencia final, el mínimo sube al valor de la bola en juego.
  - Rojas embolsadas en falta (no se reponen).
  - Elegir quién sigue: el rival, el infractor repite, o *falta y miss* con las bolas repuestas.
  - **Bola libre** cuando la falta deja al rival snookeado.
- **Snookers necesarios.** Indica cuántos snookers necesita el jugador que va detrás, cuánto vale cada uno y los puntos que le faltan para ganar.
- **Frame ganado.** Avisa cuando el rival ya no puede superar la puntuación sin faltas a su favor, o solo puede empatar.
- **Última negra y negra recolocada.** Con solo la negra en mesa, el primer tanto o falta decide el frame. Si hay empate, la negra se recoloca a muerte súbita.
- **Partida a varios frames** (al mejor de 1 a 35), frames ganados y mejor break de cada jugador.
- **Deshacer** ilimitado, historial del frame, conceder el frame y corrección manual de puntos y rojas.
- **Reiniciar mesa** y **resetear partida** desde la cabecera, con doble toque para confirmar.
- La partida se guarda en el propio dispositivo y la pantalla se mantiene encendida mientras se juega.

## Instalación en el iPhone

1. Abre la dirección de GitHub Pages en **Safari**: `https://TU-USUARIO.github.io/snooker/`
2. Toca **Compartir → Añadir a pantalla de inicio**.
3. Aparecerá el icono de la bola roja con el nombre **Snooker**. Ábrelo desde ahí para usarlo a pantalla completa.

Tras abrirla una vez con conexión, la app funciona también sin internet.

## Publicación en GitHub Pages

1. Sube todos los archivos de este repositorio a la rama `main`.
2. En **Settings → Pages**, elige la rama `main` y la carpeta `/ (root)`, y guarda.
3. La app queda disponible en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPOSITORIO/` en uno o dos minutos.

## Archivos

| Archivo | Para qué sirve |
| --- | --- |
| `index.html` | La aplicación completa: estructura, estilos y lógica del marcador. |
| `manifest.webmanifest` | Nombre, colores e iconos de la app instalada. |
| `sw.js` | Guarda la app en el dispositivo para usarla sin conexión. |
| `apple-touch-icon.png` | Icono de 180 × 180 que usa el iPhone en la pantalla de inicio. |
| `icon-192.png`, `icon-512.png` | Iconos para otros navegadores y dispositivos. |

## Actualizar la app

1. Edita `index.html` y súbelo al repositorio.
2. Si cambias la lista de archivos o quieres forzar la actualización, sube el número de versión en `sw.js` (`snooker-v1` → `snooker-v2`).
3. En el iPhone, cierra la app y vuelve a abrirla con conexión para recibir la nueva versión.

Las partidas guardadas no se pierden al actualizar.

## Reglas de referencia

| Bola | Puntos |
| --- | --- |
| Roja (15) | 1 |
| Amarilla | 2 |
| Verde | 3 |
| Marrón | 4 |
| Azul | 5 |
| Rosa | 6 |
| Negra | 7 |

- Break máximo posible: **147** (15 rojas con 15 negras y todos los colores).
- Falta: mínimo **4 puntos**, o el valor de la bola en juego, la bola tocada primero o la embolsada si es mayor, hasta un máximo de **7**.
- Los colores embolsados mientras quedan rojas se reponen; las rojas no.
- La bola libre vale como la bola en juego (1 si toca roja) y no se concede si se obliga al infractor a repetir.
