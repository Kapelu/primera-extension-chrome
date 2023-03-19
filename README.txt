


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