<h1 align='center'> 😊 &nbsp;Crea una extensión de Google Chrome paso a paso</h1>
<br>
<div style="text-align:justify;">

En este tutorial les voy a enseñar a crear su primera extensión de Google Chrome!. los guiaré desde lo más basico como es crear el archivo de manifiesto (JSON), una página emergente o tambien llamada Popup, ademas de añadir codigo de Javascript para que el usuario pueda interactuar con la extension, y como hacer para activar la extensión en nuestro navegador.

Y aunque el titulo dice para Google Chrome, al existir otros navegadores basados en Chromiun, como Brave, Opera, Microsoft Edge y el mismo Chromiun, esta extension puede funcionar exactamente igual para esos proyectos tambien.
</div>

> Requerimientos

<div style="text-align:justify;">
HTML, CSS, y Javascript. Este tutorial es adecuado para desarrolladores web frontend que tienen conocimientos básicos de HTML, CSS y JavaScript. No se requiere experiencia previa en la creación de extensiones para Chrome, pero se recomienda estar familiarizado con los conceptos básicos de crear sitios web sencillos.

¡Empecemos!
</div>


> Creación del Proyecto

<div style="text-align:justify;">
<p>Primero, abre tu editor de código preferido y crea una carpeta para nuestra extensión, en mi caso la voy a llamar primera-extension-chrome.
</p>
<p>
Puedes crearlo esta carpeta, dando click derecho, "crear carpeta", pero Si eres un amante de la consola tambien puedes crearlo usando los comandos:
</p>

```bash
mkdir primera-extension-chrome
cd primera-extension-chrome
```
Abrelo con tu Editor

Una vez creado abre tu proyecto con tu editor favorito, en mi caso usare Visual Studio Code. tambien puedes abrir este desde la consola usando.

code .
Creación del Manifest
Luego dentro de esta carpeta, crea un archivo llamado manifest.json. Este archivo es esencial para crear una extensión de Chrome, ya que describe la información de la extensión, incluyendo su nombre, descripción, icono y permisos.

Tambien debemos saber que hay varias versiones de Manifest, en donde la ultima version es el Manifest V3 (Version 3)

El contenido del archivo manifest.json debe ser similar al siguiente:
</div>