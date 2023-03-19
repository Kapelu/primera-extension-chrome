<h2 align='center'> 😊 &nbsp;Crea una extensión para navegadores basados en Chromiun, paso a paso</h2>
<br>

En este tutorial les voy a mostrar como podemos crear su primera extensión navegadores basados en Chromiun. Los guiaré desde lo más básico, como es crear el archivo de manifiesto (JSON), una página emergente o tambien llamada Popup, ademas de añadir codigo de Javascript para que el usuario pueda interactuar con la extension, y como hacer para activar la extensión en nuestro navegador.

Al existir otros navegadores basados en Chromiun, como Brave, Opera, Microsoft Edge y el mismo Chromiun, esta extension puede funcionar exactamente igual para esos proyectos.

> ## Requerimientos

HTML, CSS, y Javascript. Este tutorial es adecuado para desarrolladores web frontend que tienen conocimientos básicos de HTML, CSS y JavaScript. No se requiere experiencia previa en la creación de extensiones para Chrome, pero se recomienda estar familiarizado con los conceptos básicos de crear sitios web sencillos.

¡Empecemos!
<br>

> ## Creación del Proyecto

Primero, abre tu editor de código preferido y crea una carpeta para nuestra extensión, en mi caso la voy a llamar primera-extension-chrome.

Puedes crearlo esta carpeta, dando click derecho, "crear carpeta", pero Si eres un amante de la consola tambien puedes crearlo usando los comandos:


```bash
mkdir primera-extension-chrome
cd primera-extension-chrome
```
<br>

## Abrelo con tu Editor

Una vez creado abre tu proyecto con tu editor favorito, en mi caso usare Visual Studio Code. tambien puedes abrir este desde la consola usando.

```bash
code .
```

> Creación del Manifest

Luego dentro de esta carpeta, crea un archivo llamado manifest.json. Este archivo es esencial para crear una extensión de Chrome, ya que describe la información de la extensión, incluyendo su nombre, descripción, icono y permisos.

Tambien debemos saber que hay varias versiones de Manifest, en donde la ultima version es el Manifest V3 (Version 3)

El contenido del archivo `manifest.json` debe ser similar al siguiente:

```json
{
  "manifest_version": 3,
  "name": "Mi Primera Extension de Chrome",
  "version": "1.0",
  "description": "Esta es la descripción de mi extensión",
  "icons": {
    "128": "logo.png"
  },
  "action": {
    "default_popup": "popup.html"
  }
}
```
Este código define los metadatos básicos de la extensión, incluyendo su nombre, versión, descripción e icono. También especifica que la extensión tendrá una página emergente (popup) que se abrirá cuando el usuario haga clic en el icono de la extensión.

Crear la página emergente o Popup
Crea un archivo llamado `popup.html` en la raíz de tu proyecto y escribe el siguiente código:

```html
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
```
Este código define una página emergente simple que muestra un mensaje de bienvenida al usuario. También se define un estilo básico para centrar el contenido en la ventana emergente.

> ## Sube la Imagen

Como notas en el código anterior, es necesario cargar un logotipo, asi que dentro de la raiz de tu proyecto añade un imagen cualquiera, pero que tenga el mismo nombre `logo.png`. De lo contrario si no lo añades no podras cargar tu extension.

> ## Cargar la extensión en Chrome

Una vez creada la extensión, ya podemos cargarla desde nuestro navegador de Google Chrome, así que puedes seguir estos pasos:

* Abre Google Chrome y escribe "chrome://extensions" en la barra de direcciones.

* Activa el "Modo de desarrollador" haciendo clic en el interruptor o Switch en la parte superior derecha de la página.

* Haz clic en "Cargar extension sin empaquetar" en la parte superior izquierda de la página.

* Selecciona la carpeta que contiene tu archivo manifest.json y haz clic en "Seleccionar carpeta".

> ¡Listo! Tu extensión se ha cargado en Chrome. Ahora puedes hacer clic en el icono de la extensión para abrir la página emergente y ver el mensaje de bienvenida.

<br>

> ## Interacción con el usuario

Para agregar interacción con el usuario, puedes utilizar JavaScript en la página emergente. Por ejemplo, puedes agregar un botón que cambie el mensaje de bienvenida al hacer clic en él.

Para ello nesecitaras crear un archivo de javascript. Aqui voy a dar un simple ejemplo de como  agregando un boton se cambia el mensaje de tu extensión. 

Deberás crear un archivo, por ejemplo `my-script.js` de la siguiente forma:

```js
  const mensaje = document.querySelector('div')
  const boton = document.getElementById('cambiar-mensaje')
  
  boton.addEventListener('click', () => {
    mensaje.textContent = 'Nuevo mensaje'
  })
```
En el archivo `popup.html`, agrega el siguiente código dentro del cuerpo:

```html
<button id="cambiar-mensaje">Cambiar mensaje</button>
```
Este código agrega un botón a la página emergente y utiliza JavaScript para cambiar el mensaje de bienvenida cuando el usuario hace clic en el botón.

Quedando el código final, de esta forma:


```html
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
```

Y el código de Javascript quedaría así.

```js
const mensaje = document.querySelector("div")
const boton = document.getElementById("cambiar-mensaje")

boton.addEventListener("click", () => {
  mensaje.textContent = "Nuevo mensaje"
})
```

A partir de aqui puedes seguir añadiendo interactividad, como por ejemplo ejecutar una alerta

aunue tambien hacer peticiones HTTP, leer archivos o modificar la página, pero estos requieren distintos permisos que se deben añadir en el manifest y deben ser investigados en la documentación de [Extensiones de Google Chrome](https://developer.chrome.com/docs/extensions/)

> ### ¡Listo! Ahora tu extensión tiene interacción, basada en código de Javascript.

<br>

Más Recursos
[Tutorial Oficial de Google Chrome](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/)