# Calendario de partidos

App web instalable (PWA) para organizar partidos locales y visitantes y ver las superposiciones.
Funciona sin conexión y guarda los datos en el propio móvil.

## Subir a GitHub y usarla en el móvil

1. En GitHub, crea un repositorio nuevo (por ejemplo `calendario-partidos`), público.
2. Sube **todos** los archivos de esta carpeta a la raíz del repositorio
   (Add file > Upload files, arrastra los archivos y pulsa "Commit changes").
3. Ve a **Settings > Pages**. En "Build and deployment" elige
   **Deploy from a branch**, rama **main** y carpeta **/ (root)**. Guarda.
4. Espera uno o dos minutos. La app quedará en:
   `https://TU-USUARIO.github.io/calendario-partidos/`
5. Abre ese enlace en el móvil:
   - **iPhone (Safari):** Compartir > Añadir a pantalla de inicio.
   - **Android (Chrome):** menú ⋮ > Instalar aplicación (o Añadir a pantalla de inicio).

## Actualizar la app

Cuando cambies `index.html`, sube también `sw.js` con el número de versión subido
(`partidos-v6` > `partidos-v7`) para que los móviles recojan la actualización.

## Importante

Los partidos se guardan en el navegador de cada dispositivo (no se comparten entre móviles).
Si borras los datos del navegador, se pierden.

## Trayectos entre lugares (cálculo automático)

- En cada partido escribe el **Lugar** (nombre o dirección, mejor con el pueblo) y el **Entrenador**.
- La app calcula sola el tiempo en coche entre los lugares de los partidos de un mismo día,
  con datos de OpenStreetMap (buscador Nominatim y rutas OSRM). No usa Google Maps ni Waze porque
  necesitan clave de pago; en el botón "Ver en Google Maps" puedes comprobar la ruta.
- En el botón **Trayectos** puedes poner un **origen y un destino** y calcular el tiempo,
  guardar el resultado, calcular todos los que faltan o escribir los minutos a mano.
- Se suma un **margen extra** (10 min por defecto) al tiempo de la ruta. Se puede cambiar.
- Si no encuentra un lugar, escribe la dirección completa, añade el pueblo o pega unas
  coordenadas (por ejemplo `41.6,2.5`).
- Hace falta conexión para calcular. Los trayectos ya calculados se guardan en el móvil.
- Un partido lleva un **anillo amarillo** si se superpone con cualquier otro del día y un **anillo azul verdoso** si no
  da tiempo a llegar de un campo al otro. Se comprueba entre todos los partidos, sea cual sea el club o el entrenador.

## Importar partidos desde archivos (PDF, CSV, XLSX)

- Botón **Importar** (o arrastra el archivo a la página).
- Escribe el nombre de **tu club** para que la app detecte sola si juegas en casa o fuera.
- La app reconoce las columnas por su nombre (Fecha/Data, Hora, Local, Visitante, Rival, Lugar/Campo/Pabellón,
  Entrenador, Categoría/Equipo, Duración) y, si no hay cabecera, por el contenido. Puedes corregir las
  columnas en el desplegable "Columnas detectadas".
- En PDF se lee el texto (tablas o líneas sueltas). Los PDF escaneados como imagen no se pueden leer.
- Antes de añadir nada hay una vista previa donde puedes editar fecha, hora, condición, rival, lugar,
  entrenador y equipo, y desmarcar los que no quieras. Los que ya existen salen desmarcados.
- Los lectores de PDF y Excel están en la carpeta `lib/` (funcionan sin conexión). Sube también esa carpeta.

## Colores por club

- **Sant Celoni:** local rojo oscuro, visitante rojo claro.
- **Arenys de Mar:** local verde oscuro, visitante verde claro.
- Los partidos que no tienen club asignado salen en gris (puedes asignarles club al editarlos).
- Al importar, elige "Todos son de…" o deja "Detectar por el nombre del equipo". Los nombres con los que
  aparece cada club en los archivos se pueden cambiar en "Cómo se reconocen los clubes en los archivos".
