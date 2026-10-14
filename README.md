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
(`partidos-v3` > `partidos-v4`) para que los móviles recojan la actualización.

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
- Un partido sale en **rojo** si se superpone con cualquier otro del día y en **ámbar** si no
  da tiempo a llegar de un campo al otro. Se comprueba entre todos los partidos, sea cual sea el entrenador.
