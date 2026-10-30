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
(`partidos-v10` > `partidos-v11`) para que los móviles recojan la actualización.

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

## Móvil, tableta y ordenador

- **Ordenador:** calendario a la izquierda y detalle del día a la derecha.
- **Móvil y tableta:** el calendario ocupa toda la pantalla y, al tocar un día, el detalle sube como una hoja
  desde abajo (con la lista de partidos y las horas). Se cierra con la ✕, tocando fuera o con Esc.
- En el móvil los botones principales (Importar, Trayectos, Nuevo partido) están en una barra fija abajo.

## Partidos del Club Vòlei Sant Celoni (iSquad)

- El botón **iSquad** añade al calendario los partidos de las 10 categorías del club, con la categoría, el entrenador
  (cuando figura en iSquad), el lugar con sus coordenadas, y si es local o visitante.
- Los datos van **dentro de la página** (bloque `isq-data` al final de `index.html`), leídos de iSquad el 15/10/2026.
  La web de iSquad no permite que otra página lea sus datos desde el navegador, por eso la app no se actualiza sola:
  para refrescar, se vuelve a generar el bloque `isq-data` y se sube una versión nueva.
- Al importar, cada partido entra como **horario sin confirmar** (borde discontinuo y «?»). En el detalle del día
  hay «Confirmar horario» (uno a uno) y «Confirmar los horarios del día».
- Los partidos que iSquad todavía no tiene con hora salen como **«Hora por confirmar»**: no cuentan para superposiciones
  ni trayectos hasta que les pongas hora («Poner hora»).
- Si se vuelve a importar y iSquad cambia una fecha u hora, el partido vuelve a «sin confirmar» y muestra el horario anterior.
- En «Trayectos > Ajustes» hay una opción para avisar de superposiciones solo cuando coincide el entrenador.

## Filtro por club

Sobre el calendario hay tres botones: **Todos**, **Sant Celoni** y **Arenys de Mar**. El filtro cambia el calendario, los contadores, el detalle del día y los avisos. La elección se recuerda.
Las superposiciones y trayectos se avisan solo cuando coincide el entrenador (se puede cambiar en Trayectos > Ajustes).

## Editar en el ordenador, ver en el móvil

- En **ordenador** se edita todo (los datos se guardan en ese navegador).
- En **móvil y tableta** la app es **solo lectura**.
- Para enviar el calendario al móvil: en el ordenador pulsa **Compartir**, copia el enlace y envíatelo (WhatsApp, correo…).
  Al abrirlo en el móvil, la app guarda esos datos y los muestra. Cuando cambies algo, envía un enlace nuevo.
  Alternativa: «Descargar como archivo» y, en el móvil, «Cargar archivo». No hace falta GitHub.
- Para editar desde un móvil excepcionalmente, añade `?editar=1` a la dirección.
- Las superposiciones y trayectos solo se avisan si los dos partidos tienen el mismo entrenador.

## Calendarios escolares

El botón **iSquad** también incluye los equipos escolares (Consell Esportiu del Vallès Oriental): Infantil mixt y Aleví mixt, leídos de los PDF del Consell. Entran igual que los de la federación: sin confirmar y con «Hora por confirmar» donde el PDF dice «sense hora». Los datos están en el bloque `isq-data` del final de `index.html`.

También está el **Cadet-Juvenil masculí** de los Jocs Esportius Escolars del Maresme (CV Sant Celoni «A»), leído del PDF del Consell Esportiu del Maresme.

## Actualizar horarios

Los datos de iSquad y de los PDF escolares van dentro de la app, así que no se actualizan solos. Cuando haya horarios nuevos, se prepara un **archivo de actualización** (`actualizacion.json`). En la app: botón **iSquad > Cargar actualización**, y luego **Añadir al calendario**. Los partidos cuyo horario ha cambiado vuelven a «sin confirmar» y muestran el horario anterior. No hace falta volver a subir la app.

## Actualizar desde iSquad (botón)

En **iSquad > Actualizar desde iSquad** la app puede volver a leer las páginas de la federación y aplicar los cambios. Necesita el **lector** (un Cloudflare Worker, carpeta `lector-isquad`, que NO va en este zip): pega su dirección en el diálogo. Sin lector, sigue funcionando «Cargar actualización» con un archivo.

## Actualización de datos (26/10/2026)

Esta versión trae datos de iSquad releídos el 26/10/2026 para 6 categorías. Al abrir la app en el ordenador, **se aplican solos** los cambios (resultados, horas y fechas nuevas) a los partidos que ya tengas importados; los que cambian de fecha u hora vuelven a «sin confirmar» y muestran el horario anterior. En el diálogo de iSquad cada categoría indica la fecha de su última lectura.

## Actualización automática

Si hay un lector configurado (carpeta `lector-isquad`, instrucciones en `LEEME.md`), la app en el ordenador se actualiza sola al abrirla, como máximo una vez cada 20 horas. Sin lector, se usa la carga manual.

## Mismo entrenador con nombres distintos

Las superposiciones y trayectos se avisan cuando es el mismo entrenador aunque el nombre esté escrito distinto: «Santi» = «Santiago Sancer Navarro», «Juanma» = «Juan Manuel Arguelles», o el mismo nombre con y sin segundo apellido. Si un apodo puede ser de dos personas, no se une. Para el resto, en **Trayectos > Ajustes** hay una caja «Entrenadores con varios nombres» (una línea por persona: `Nombre1 = Nombre2`).

## Horarios escolares (PDF)

En **iSquad > Horarios escolares (PDF)** se puede elegir el PDF del calendario del Consell Esportiu (Vallès Oriental o Maresme; se pueden elegir varios a la vez). La app coge solo los partidos de Sant Celoni y los fusiona con los que ya hay: no duplica, y si una fecha u hora cambia el partido vuelve a «sin confirmar» y muestra el anterior. Si el PDF trae una fecha claramente errónea (por ejemplo un año equivocado), la corrige y lo avisa en una nota del partido. Para categorías nuevas basta con cargar su PDF.

## CEVO automático

Si el lector está actualizado (nuevo `worker.js`), la actualización automática también trae los calendarios escolares del CEVO (Infantil y Aleví mixt) desde su PDF de exportación. El Maresme sigue siendo manual (PDF).

## Móvil: actualizar datos

El móvil sigue siendo de solo lectura (no se editan partidos), pero ahora puede **traer datos nuevos**: se actualiza solo al abrirla (como máximo una vez al día, si hay lector) y tiene el botón **Actualizar datos** en la franja gris de arriba, con la opción de cargar un PDF escolar. Los cambios se guardan en la copia del móvil. Un enlace nuevo de **Compartir** desde el ordenador sustituye esa copia. Un móvil sin datos puede cargarlo todo desde el lector, pero sin las confirmaciones hechas en el ordenador.

## Enlaces de Compartir más cortos

El enlace ya no incluye los trayectos que no hacen falta ni los campos vacíos (antes podía pasar de 20.000 caracteres si había muchos trayectos guardados). Además hay una casilla **«Enlace más corto: sin los partidos ya jugados»**. Si una aplicación de mensajes corta el enlace, usa esa casilla o «Descargar como archivo» (en el móvil: «Cargar archivo»).

## Enlace corto

Si el lector tiene el KV `SHARE` (ver `lector-isquad/LEEME.md`), **Compartir** da un enlace de unos 45 caracteres. Si no, la app da el enlace largo como hasta ahora.
