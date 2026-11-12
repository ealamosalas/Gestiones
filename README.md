# Gestión Financiera

Libro de cuentas personal: ingresos, gastos, crédito hipotecario, ahorro, fondos de inversión, presupuesto por categoría y metas de ahorro. Es una sola página web (`index.html`) que funciona en cualquier navegador, sin servidor y sin cuentas de terceros.

## Qué hace

- **Movimientos:** ingresos a un lado, salidas al otro y el balance del mes al final. Buscador y filtros por origen y categoría.
- **Fijos y cuotas:** gastos que se anotan solos cada mes y compras en cuotas.
- **Gráficos, presupuesto, metas y resumen anual.**
- **Gmail (opcional):** lee tus comprobantes de Servipag y tus recibos de Google Play y los anota como gastos.
- **Respaldo:** exporta e importa todos tus datos en un archivo.

## Acceso con usuario y contraseña

Al abrir la aplicación se pide un usuario y una contraseña. La primera vez se crea el usuario; después se entra con él.

- **No hay servidor ni base de datos de usuarios.** Cada usuario existe solo en el navegador donde se creó.
- **El libro se guarda cifrado** con una clave derivada de la contraseña (PBKDF2 con 600.000 iteraciones y AES-GCM de 256 bits). Sin la contraseña, lo guardado en el navegador no se puede leer.
- **Una contraseña olvidada no se puede recuperar.** Por eso conviene exportar respaldos.
- En un mismo navegador pueden convivir varios usuarios, cada uno con su libro.
- La sesión dura mientras la pestaña esté abierta. El botón **Salir** la cierra.

La contraseña protege los datos, no la página: cualquiera puede abrir la dirección del sitio y crear su propio usuario con un libro vacío.

## Dónde quedan los datos

- **En el navegador de cada computador**, cifrados con tu contraseña.
- **En tu Google Drive (opcional):** al pulsar **Conectar Google**, el mismo libro cifrado se guarda en la carpeta privada que Drive reserva para esta aplicación. No aparece entre tus archivos y ninguna otra aplicación puede leerlo. Con eso, el libro se sincroniza entre los equipos donde conectes la misma cuenta de Google.

Ni Google ni este repositorio pueden leer el contenido: sale cifrado del navegador. En un equipo nuevo, crea tu usuario, conecta Google y escribe la contraseña con la que creaste el libro para unirlo.

Si editas el mismo libro en dos equipos, se conserva la versión más reciente de cada movimiento y lo borrado en uno se borra en el otro.

Además puedes usar **Respaldo → Exportar** e **Importar**. El archivo de respaldo no va cifrado: guárdalo en un lugar seguro.

## Publicar con GitHub Pages

1. En el repositorio: **Settings → Pages**.
2. En *Build and deployment → Source*, elige **Deploy from a branch**.
3. En *Branch*, elige la rama que contiene `index.html` y la carpeta `/ (root)`, y pulsa **Save**.
4. En uno o dos minutos la aplicación queda en `https://ealamosalas.github.io/Gestiones/`.

Con una cuenta gratuita de GitHub, Pages solo está disponible si el repositorio es público; con GitHub Pro también funciona en repositorios privados. En ambos casos el sitio publicado es visible para quien tenga el enlace. No expone datos: solo la aplicación vacía.

## Conectar Google: Drive y Gmail (una sola vez, gratis)

El guardado en Drive y la lectura de Gmail necesitan un identificador de cliente de Google asociado a tu cuenta.

1. Entra a <https://console.cloud.google.com/> y crea un proyecto (por ejemplo, "Gestion Financiera").
2. **APIs y servicios → Biblioteca**: busca **Gmail API** y actívala; luego busca **Google Drive API** y actívala también.
3. **APIs y servicios → Pantalla de consentimiento de OAuth**: tipo de usuario **Externo**, completa el nombre de la aplicación y tu correo, y deja el estado en **Prueba**.
4. En esa misma pantalla, en **Usuarios de prueba**, agrega tu cuenta de Gmail y la de cada persona a la que quieras dar acceso (hasta 100).
5. **APIs y servicios → Credenciales → Crear credenciales → ID de cliente de OAuth**: tipo **Aplicación web**. En **Orígenes de JavaScript autorizados** agrega `https://ealamosalas.github.io` (solo el dominio, sin la ruta del repositorio ni barra final).
6. Copia el ID de cliente (termina en `.apps.googleusercontent.com`) y pégalo en `config.js`, en `googleClientId`.

En la hoja Movimientos aparecerá el botón **Conectar Google**. Pide dos permisos: leer tu correo (solo lectura) y guardar datos propios de la aplicación en tu Drive (no da acceso a tus demás archivos). Google mostrará el aviso "Google no ha verificado esta aplicación": es normal en modo de prueba; elige *Continuar*. El permiso dura una hora, así que en cada sesión hay que pulsar el botón de nuevo. Mientras no esté conectado, los cambios quedan en el navegador y se suben en la siguiente conexión.

Solo se importan correos desde el 1 de septiembre de 2026.

## Quién tiene acceso

- **A conectar su Google (Drive y Gmail) desde la aplicación:** las cuentas de la lista de usuarios de prueba (paso 4).
- **Al código:** los colaboradores del repositorio (**Settings → Collaborators**).
