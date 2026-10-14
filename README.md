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
(`partidos-v1` > `partidos-v2`) para que los móviles recojan la actualización.

## Importante

Los partidos se guardan en el navegador de cada dispositivo (no se comparten entre móviles).
Si borras los datos del navegador, se pierden.
