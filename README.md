# Gestión Financiera

Libro de cuentas personal: ingresos, gastos, crédito hipotecario, ahorro, fondos de inversión, presupuesto por categoría y metas de ahorro. Es una sola página web (`index.html`) que funciona en cualquier navegador, sin servidor y sin cuentas de terceros.

## Qué hace

- **Movimientos:** ingresos a un lado, salidas al otro y el balance del mes al final. Buscador y filtros por origen y categoría.
- **Fijos y cuotas:** gastos que se anotan solos cada mes y compras en cuotas.
- **Gráficos, presupuesto, metas y resumen anual.**
- **Gmail (opcional):** lee tus comprobantes de Servipag y tus recibos de Google Play y los anota como gastos.
- **Respaldo:** exporta e importa todos tus datos en un archivo.

## Dónde quedan los datos

En el navegador de cada computador (almacenamiento local). No se envían a ningún servidor y este repositorio no contiene datos de nadie. Para pasar el libro a otro equipo o no perderlo, usa **Respaldo → Exportar** y luego **Importar**.

## Publicar con GitHub Pages

1. En el repositorio: **Settings → Pages**.
2. En *Build and deployment*, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)` y guarda.
3. En uno o dos minutos la aplicación queda en `https://ealamosalas.github.io/Gestion-Financiera/`.

El sitio de GitHub Pages es público para quien tenga el enlace, aunque el repositorio sea privado. No expone datos: solo la aplicación vacía.

## Conectar Gmail (una sola vez, gratis)

La lectura de Gmail necesita un identificador de cliente de Google asociado a tu cuenta.

1. Entra a <https://console.cloud.google.com/> y crea un proyecto (por ejemplo, "Gestion Financiera").
2. **APIs y servicios → Biblioteca**: busca **Gmail API** y actívala.
3. **APIs y servicios → Pantalla de consentimiento de OAuth**: tipo de usuario **Externo**, completa el nombre de la aplicación y tu correo, y deja el estado en **Prueba**.
4. En esa misma pantalla, en **Usuarios de prueba**, agrega tu cuenta de Gmail y la de cada persona a la que quieras dar acceso (hasta 100).
5. **APIs y servicios → Credenciales → Crear credenciales → ID de cliente de OAuth**: tipo **Aplicación web**. En **Orígenes de JavaScript autorizados** agrega `https://ealamosalas.github.io`.
6. Copia el ID de cliente (termina en `.apps.googleusercontent.com`) y pégalo en `config.js`, en `googleClientId`.

Al abrir la aplicación aparecerá el botón **Conectar Gmail**. Google mostrará el aviso "Google no ha verificado esta aplicación": es normal en modo de prueba; elige *Continuar*. El permiso es de solo lectura y dura una hora, así que cada día hay que pulsar el botón de nuevo.

Solo se importan correos desde el 1 de septiembre de 2026.

## Quién tiene acceso

- **A leer su Gmail desde la aplicación:** las cuentas de la lista de usuarios de prueba (paso 4).
- **Al código:** los colaboradores del repositorio (**Settings → Collaborators**).
