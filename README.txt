
```json
{
  "manifest_version": 3,
  "name": "Mi Primera Extension de Chrome",
  "version": "1.0",
  "description": "Esta es la descripción de mi extensión",
  "icons": {
    "128": "icon128.png"
  },
  "action": {
    "default_popup": "popup.html"
  }
}
```
Este código define los metadatos básicos de la extensión, incluyendo su nombre, versión, descripción e icono. También especifica que la extensión tendrá una página emergente (popup) que se abrirá cuando el usuario haga clic en el icono de la extensión.

Crear la página emergente o Popup
Crea un archivo llamado popup.html en la raíz de tu proyecto y escribe el siguiente código:

<!DOCTYPE html>
<html>
  <head>
    <title>Mi extensión</title>
    <meta charset="UTF-8">
    <style>
      body {
        width: 300px;
        height: 200px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
      }
    </style>
  </head>
  <body>
    <div>Hola desde mi extensión</div>
  </body>
</html>
Este código define una página emergente simple que muestra un mensaje de bienvenida al usuario. También se define un estilo básico para centrar el contenido en la ventana emergente.

Sube la Imagen
Como notas en el código anterior, es necesario cargar un logotipo, asi que dentro de la raiz de tu proyecto añade un imagen cualquiera, pero que tenga el mismo nombre icon128.png. De lo contrario si no lo añades no podras cargar tu extension.

Cargar la extensión en Chrome
Una vez creada la extensión, ya podemos cargarla desde nuestro navegador de Google Chrome, así que puedes seguir estos pasos:

Abre Google Chrome y escribe "chrome://extensions" en la barra de direcciones.
Activa el "Modo de desarrollador" haciendo clic en el interruptor o Switch en la parte superior derecha de la página.
Haz clic en "Cargar extension sin empaquetar" en la parte superior izquierda de la página.
Selecciona la carpeta que contiene tu archivo manifest.json y haz clic en "Seleccionar carpeta".
¡Listo! Tu extensión se ha cargado en Chrome. Ahora puedes hacer clic en el icono de la extensión para abrir la página emergente y ver el mensaje de bienvenida.

Interacción con el usuario
Para agregar interacción con el usuario, puedes utilizar JavaScript en la página emergente. Por ejemplo, puedes agregar un botón que cambie el mensaje de bienvenida al hacer clic en él.

En el archivo popup.html, agrega el siguiente código dentro del cuerpo:

<button id="cambiar-mensaje">Cambiar mensaje</button>

<script>
  const mensaje = document.querySelector('div');
  const boton = document.getElementById('cambiar-mensaje');
  
  boton.addEventListener('click', () => {
    mensaje.textContent = 'Nuevo mensaje';
  });
</script>
Este código agrega un botón a la página emergente y utiliza JavaScript para cambiar el mensaje de bienvenida cuando el usuario hace clic en el botón.

Quedando el código final, de esta forma:

<!DOCTYPE html>
<html>
  <head>
    <title>Mi extensión</title>
    <meta charset="UTF-8" />
    <style>
      body {
        width: 300px;
        height: 200px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
      }
    </style>
  </head>
  <body>
    <div>Hola desde mi extensión</div>

    <button id="cambiar-mensaje">Cambiar mensaje</button>

    <script>
      const mensaje = document.querySelector("div");
      const boton = document.getElementById("cambiar-mensaje");

      boton.addEventListener("click", () => {
        mensaje.textContent = "Nuevo mensaje";
      });
    </script>
  </body>
</html>
Ahora si lo ejecutas notaras que este no cambia el texto, de hecho si vas a la seccion de extensiones en chrome, en "chrome://extensions" veras que hay un boton nuevo rojo, para tu extension que dice "Errores", esto es porque el navegador nos pide que separemos los archivos. asi que lo que podemos hacer es separar el código, en dond el código de HTML quedaría asi:

<!DOCTYPE html>
<html>
  <head>
    <title>Mi extensión</title>
    <meta charset="UTF-8" />
    <style>
      body {
        width: 300px;
        height: 200px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 24px;
      }
    </style>
  </head>
  <body>
    <div>Hola desde mi extensión</div>

    <button id="cambiar-mensaje">Cambiar mensaje</button>

    <script src="my_script.js"></script>
  </body>
</html>
Y el código de Javascript quedaría así.

const mensaje = document.querySelector("div");
const boton = document.getElementById("cambiar-mensaje");

boton.addEventListener("click", () => {
  mensaje.textContent = "Nuevo mensaje";
});
Y a partir de aqui puedes seguir añadiendo interactividad, como por ejemplo ejecutar una alerta

aunue tambien hacer peticiones HTTP, leer archivos o modificar la pagina, pero estos requieren distintos permisos que se deben añadir en el manifest y deben ser investigados en la documentación de Extensiones de Google Chrome

¡Listo! Ahora tu extensión tiene interacción, basada en código de Javascript.

Más Recursos
Tutorial Oficial de Google Chrome