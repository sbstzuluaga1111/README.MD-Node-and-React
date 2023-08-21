
# Sección 2: Introduction to Node js and NPM

Este repositorio contiene mi aprendizaje en el curso de la seccion 2 de Node.ja. Aqui dare a conocer los aspectos mas relevantes del video como tal y mi aprendizaje a lo largo del video explicativo.

## ¿Qué es Node.js y por qué usarlo?

Node.js es un entorno de tiempo de ejecución de JavaScript que permite ejecutar código JavaScript en el servidor. A diferencia de JavaScript en el navegador, que está orientado principalmente a la interacción con el usuario, Node.js se enfoca en el manejo de operaciones de entrada/salida y la construcción de aplicaciones escalables y en tiempo real.

## Características clave

- **No bloqueante y asíncrono**: Node.js utiliza un enfoque no bloqueante, lo que significa que puede manejar múltiples solicitudes y eventos al mismo tiempo sin bloquear el hilo principal. Esto es esencial para aplicaciones que requieren alta concurrencia.

- **V8 Engine**: Node.js se basa en el motor V8 de Google, que compila el código JavaScript en código de máquina altamente eficiente, lo que resulta en un rendimiento rápido.

- **NPM (Node Package Manager)**: NPM es un administrador de paquetes que permite a los desarrolladores compartir y reutilizar código. Ofrece acceso a miles de bibliotecas y módulos de código abierto.

- **Lenguaje único en ambos lados**: Node.js utiliza JavaScript tanto en el lado del cliente como en el del servidor. Esto permite a los desarrolladores utilizar las mismas habilidades y bibliotecas en ambos lados.

- **Amplia comunidad y soporte**: Node.js tiene una comunidad activa de desarrolladores que contribuyen con bibliotecas, tutoriales y soporte en línea.

## Ejemplos

En este repositorio, encontrarás ejemplos básicos para empezar con Node.js:

- **Ejecución de código**: Aprenderás cómo ejecutar código JavaScript usando Node.js en tu terminal.

- **Creación de un servidor web**: Verás cómo crear un servidor web simple utilizando Node.js y cómo responder a solicitudes HTTP.

- **Uso de módulos**: Aprenderás cómo dividir tu código en módulos reutilizables y cómo usar módulos preconstruidos.

## Requisitos previos

Asegúrate de tener instalado Node.js en tu sistema. Podemos descargarlo desde [nodejs.org](https://nodejs.org/).


## Ejecutar Javascript fuera del navegador

**Escribir tu código JavaScript:**

Crea un archivo con extensión .js en el que escribirás tu código JavaScript. Por ejemplo, crea un archivo llamado app.js con el siguiente contenido:

```
console.log("¡Hola, Node.js!");
```

**Ejecutar el código:**

Abre tu terminal y navega hasta el directorio donde guardaste el archivo app.js. Luego, ejecuta el siguiente comando:

 ```
 node app.js
 ```

Esto ejecutará el archivo app.js utilizando Node.js y deberías ver el mensaje "¡Hola, Node.js!" impreso en la consola.

**Usar módulos y paquetes:**

Node.js también te permite utilizar módulos y paquetes externos en tu código. Podemos instalar paquetes utilizando el administrador de paquetes NPM (Node Package Manager).Para instalar y usar estos paquetes es de la siguiente manera:
```
npm install ('paquete')

const paquete = require("paquete");

```

Estos son los pasos básicos para ejecutar JavaScript fuera del navegador utilizando Node.js. A partir de aquí, podemos explorar y aprender más sobre cómo Node.js puede utilizarse para crear aplicaciones en el lado del servidor, manejar operaciones de E/S, crear servidores web, acceder a bases de datos y mucho más.

## Usando módulos:

En Node.js, los módulos son una parte fundamental que te permite dividir y organizar tu código en piezas reutilizables.

**cómo podemos utilizar módulos en Node.js:**

Supongamos que tienes dos archivos en el mismo directorio que son **main.js** y **utilidades.js**

   ```
utilidades.js:

const sumar = (a, b) => a + b;
const restar = (a, b) => a - b;

// Exportamos las funciones para que estén disponibles fuera del módulo
module.exports = {
  sumar,
  restar
};
   ```
```
main.js:

// Importamos el módulo de utilidades
const utilidades = require('./utilidades');

// Utilizamos las funciones exportadas del módulo
console.log(utilidades.sumar(5, 3)); // Salida: 8
console.log(utilidades.restar(10, 4)); // Salida: 6
```
En este ejemplo, hemos definido dos funciones en el módulo utilidades.js, y luego las hemos exportado utilizando module.exports. Luego, en el archivo main.js, hemos importado el módulo utilizando require y hemos accedido a las funciones exportadas para realizar operaciones.

**Ten en cuenta lo siguiente:**

- El módulo require en Node.js busca en el directorio actual o en rutas relativas especificadas.

- Podemos exportar objetos, funciones, clases y más desde un módulo.

- Podemos exportar más de una cosa de un solo módulo.

- Podemos utilizar rutas absolutas o relativas al importar módulos.

Este es solo un ejemplo básico. los módulos te permiten organizar tu código de manera modular y eficiente, lo que facilita el mantenimiento y la escalabilidad de las aplicaciones.

## Leer y escribir archivos

En Node.js, podemos leer y escribir archivos de manera sencilla utilizando el módulo fs (File System).

**Leer un archivo:**
```
const fs = require('fs');

// Lee un archivo de texto de forma asíncrona
fs.readFile('archivo.txt', 'utf8', (error, data) => {
  if (error) {
    console.error('Error al leer el archivo:', error);
    return;
  }
  console.log('Contenido del archivo:', data);
});
```
**Escribir un archivo:**

```
const fs = require('fs');

const contenido = 'Este es el contenido que se escribirá en el archivo.';

// Escribe un archivo de texto de forma asíncrona
fs.writeFile('nuevo-archivo.txt', contenido, 'utf8', error => {
  if (error) {
    console.error('Error al escribir el archivo:', error);
    return;
  }
  console.log('Archivo creado exitosamente.');
});

```

## Creación de un servidor web sencillo

Crear un servidor web en Node.js es una excelente manera de comprender cómo funciona la plataforma y cómo manejar las solicitudes HTTP.

**cómo podemos crear un servidor web usando el módulo http de Node.js:**
```
const http = require('http');

// Crear un servidor
const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('¡Hola desde el servidor web de Node.js!');
});

// Escuchar en un puerto específico
const puerto = 3000;
server.listen(puerto, () => {
  console.log(`Servidor escuchando en http://localhost:${puerto}`);
});
```
- Importamos el módulo http de Node.js, que nos permite crear y manejar servidores web.

- Usamos http.createServer para crear un servidor. Dentro de la función de manejo, establecemos la respuesta que se enviará al cliente cuando realice una solicitud.

- Usamos res.writeHead para configurar la cabecera de la respuesta HTTP con un código de estado 200 y el tipo de contenido.

- Usamos res.end para enviar el contenido de la respuesta.

- Finalmente, usamos server.listen para hacer que el servidor escuche en un puerto específico (en este caso, el puerto 3000). Cuando el servidor comienza a escuchar, se ejecuta una función de devolución de llamada que muestra un mensaje en la consola.


Para probar el servidor, guarda el código en un archivo llamado server.js y ejecuta el siguiente comando en tu terminal:

   ```
node server.js

   ```

Luego, abre tu navegador y visita http://localhost:3000. Deberías ver el mensaje "¡Hola desde el servidor web de Node.js!" en la página.

## Enrutamiento

El enrutamiento en Node.js es la forma en que gestionas diferentes rutas y solicitudes HTTP en tu servidor. Podemos utilizar diversos módulos y técnicas para implementar un sistema de enrutamiento eficiente. Uno de los enfoques más comunes es utilizar el módulo express, que simplifica la creación de rutas y la gestión de solicitudes y respuestas.


- Primero, hay que tener express instalado en tu proyecto. Podemos hacerlo ejecutando npm install express en tu terminal.

- Luego, en el archivo server.js (o cualquier nombre que hayas elegido para tu archivo principal), podemos implementar el enrutamiento de la siguiente manera:
```
const express = require('express');
const app = express();
const puerto = 3000;

// Ruta raíz
app.get('/', (req, res) => {
  res.send('¡Bienvenido a mi servidor!');
});

// Ruta para la página "acerca-de"
app.get('/acerca-de', (req, res) => {
  res.send('Esta es la página "Acerca de nosotros".');
});

// Ruta para una página de error
app.get('*', (req, res) => {
  res.send('Página no encontrada.');
});

// Iniciar el servidor
app.listen(puerto, () => {
  console.log(`Servidor escuchando en http://localhost:${puerto}`);
});


```

- Usamos express para crear una instancia de la aplicación.

- Utilizamos app.get para definir rutas y manejar solicitudes HTTP de tipo GET.

- El asterisco (*) en la tercera ruta actúa como una ruta de comodín y captura cualquier ruta que no coincida con las rutas anteriores.

- res.send se utiliza para enviar respuestas al cliente con contenido específico.

Ejecuta el archivo con node server.js y luego podemos acceder a las rutas definidas en tu navegador, como http://localhost:3000/, http://localhost:3000/acerca-de y cualquier otra ruta que no coincida.

## Construyendo una API (muy) simple

- Asegúrate de tener express instalado en tu proyecto. Podemos hacerlo ejecutando npm install express en tu terminal.

- Luego, en tu archivo server.js, implementa la API de la siguiente manera:

```
const express = require('express');
const app = express();
const puerto = 3000;

// Middleware para analizar JSON en las solicitudes
app.use(express.json());

// Lista de tareas
let tareas = [];

// Obtener todas las tareas
app.get('/tareas', (req, res) => {
  res.json(tareas);
});

// Agregar una nueva tarea
app.post('/tareas', (req, res) => {
  const nuevaTarea = req.body;
  tareas.push(nuevaTarea);
  res.json({ mensaje: 'Tarea agregada correctamente' });
});

// Iniciar el servidor
app.listen(puerto, () => {
  console.log(`API escuchando en http://localhost:${puerto}`);
});

```

- Utilizamos express para crear una instancia de la aplicación.

- Usamos express.json() como middleware para analizar el cuerpo JSON en las solicitudes POST.

- Creamos una lista de tareas (en memoria) para almacenar las tareas.

- Utilizamos dos rutas:

    GET /tareas: Devuelve la lista de tareas.

    POST /tareas: Agrega una nueva tarea a la lista.

- res.json() se utiliza para enviar respuestas en formato JSON.

Se puede probar la API utilizando herramientas como Postman o cURL. Por ejemplo, para agregar una nueva tarea, envía una solicitud POST a http://localhost:3000/tareas con un cuerpo JSON:

```
{
  "nombre": "Completar proyecto",
  "prioridad": "alta"
}
```

## Plantillas HTML: creación de plantillas

En Node.js, podemos usar módulos de plantillas para generar contenido HTML dinámico y enviarlo al cliente. Uno de los módulos de plantillas populares es ejs (Embedded JavaScript), que te permite incrustar JavaScript en tus plantillas HTML.

- Hay que instala el paquete ejs en tu proyecto. Podemos hacerlo ejecutando npm install ejs en tu terminal.

- Crear un directorio llamado views en la raíz de tu proyecto. Dentro de este directorio, crea un archivo plantilla.ejs con el siguiente contenido:
```
<!DOCTYPE html>
<html>
<head>
  <title><%= titulo %></title>
</head>
<body>
  <h1><%= mensaje %></h1>
</body>
</html>
```
En el archivo principal (server.js o similar), configura express para usar el módulo ejs como motor de plantillas:

```
const express = require('express');
const app = express();
const puerto = 3000;

// Configurar el motor de plantillas ejs
app.set('view engine', 'ejs');

// Ruta para renderizar la plantilla
app.get('/', (req, res) => {
  res.render('plantilla', { titulo: 'Mi Página', mensaje: '¡Hola desde Node.js!' });
});

// Iniciar el servidor
app.listen(puerto, () => {
  console.log(`Servidor escuchando en http://localhost:${puerto}`);
});

```
- Configuramos express para usar ejs como el motor de plantillas.

- Utilizamos res.render para renderizar la plantilla plantilla.ejs y pasamos variables (titulo y mensaje) que se utilizarán en la plantilla.

Cuando accedas a http://localhost:3000/, verás que el contenido HTML se genera dinámicamente según las variables proporcionadas en la respuesta.

## Análisis de variables de URL

En Node.js, para analizar las variables de la URL en una solicitud HTTP, puedes usar el módulo url o el módulo express, dependiendo de cómo se este construyendo el servidor.

En este caso utilizaremos express. el análisis de las variables de la URL se maneja de manera más sencilla gracias a los parámetros de ruta.

```
const express = require('express');
const app = express();
const puerto = 3000;

// Ruta con parámetros de URL
app.get('/usuario/:id', (req, res) => {
  const usuarioId = req.params.id;
  res.send(`¡Hola, usuario ${usuarioId}!`);
});

// Iniciar el servidor
app.listen(puerto, () => {
  console.log(`Servidor escuchando en http://localhost:${puerto}`);
});

```
Usaremos una ruta /usuario/:id que captura el valor id de la URL usando req.params.id.

Usar express simplifica significativamente la manipulación de parámetros de URL y permite construir rutas dinámicas de manera más intuitiva.

## Uso de los Módulos

Los módulos en Node.js son componentes que te permiten organizar y reutilizar tu código de manera efectiva. Los módulos te ayudan a dividir tu aplicación en piezas más pequeñas y coherentes, lo que facilita el mantenimiento y la escalabilidad. Puedes crear tus propios módulos o utilizar módulos externos proporcionados por la comunidad de Node.js a través de NPM (Node Package Manager).

**Crear tus propios módulos:**

Creamos un archivo llamado calculadora.js que contiene funciones para realizar operaciones matemáticas:

   ```
// calculadora.js
function sumar(a, b) {
  return a + b;
}

function restar(a, b) {
  return a - b;
}

module.exports = {
  sumar,
  restar
};

   ```

En otro archivo, puedes utilizar el módulo calculadora.js de la siguiente manera:

```
const calculadora = require('./calculadora');

console.log(calculadora.sumar(5, 3)); // Salida: 8
console.log(calculadora.restar(10, 4)); // Salida: 6

```

**Utilizar módulos externos (NPM):**

NPM es el administrador de paquetes de Node.js que te permite instalar y usar módulos externos. Por ejemplo, si deseas utilizar el paquete lodash para manipulación de datos:

- Instalamos lodash para el proyecto: npm install lodash.

- En el archivo, se puede utilizar lodash de la siguiente manera:

```
const _ = require('lodash');

const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = _.map(numbers, n => n * n);

console.log(squaredNumbers); // Salida: [1, 4, 9, 16, 25]

```

**Módulos en el núcleo de Node.js:**

Node.js también proporciona módulos en su núcleo, lo que significa que están disponibles de forma predeterminada sin necesidad de instalación adicional. Puedes usar módulos como http, fs, path, util, entre otros, para realizar tareas comunes.

Por ejemplo, para crear un servidor HTTP:

```
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('¡Hola, mundo!');
});

server.listen(3000, () => {
  console.log('Servidor escuchando en http://localhost:3000');
});

```

En resumen, los módulos son una parte esencial de Node.js que te permiten organizar, reutilizar y mantener tu código de manera efectiva. Ya sea que estés creando tus propios módulos o utilizando módulos externos, te ayudarán a construir aplicaciones más eficientes y escalables.

## NPM y el archivo package.json

NPM (Node Package Manager) es una herramienta integral que se utiliza para administrar y distribuir paquetes de software de Node.js. Te permite instalar, actualizar y gestionar las dependencias de tus proyectos de Node.js de manera eficiente. Además, NPM también es un registro público en el que los desarrolladores pueden publicar y compartir sus paquetes para que otros puedan utilizarlos en sus propios proyectos.

El archivo package.json es un archivo de configuración esencial en un proyecto de Node.js. Contiene metadatos sobre el proyecto, como su nombre, versión, descripción, dependencias y scripts personalizados.

## Tipos de paquetes e instalaciones

En Node.js, hay varios tipos de paquetes que puedes instalar y utilizar en tus proyectos. Estos paquetes se instalan y gestionan mediante NPM (Node Package Manager). Aquí hay algunos tipos comunes de paquetes y cómo instalarlos:

- **Dependencias de Producción (dependencies)**
Las dependencias de producción son paquetes que tu aplicación necesita para funcionar en producción. Estos paquetes incluyen bibliotecas y herramientas esenciales que son necesarias para ejecutar tu aplicación. Puedes instalar dependencias de producción usando el comando npm install <paquete>.

- **Dependencias de Desarrollo (devDependencies)**
Las dependencias de desarrollo son paquetes que son necesarios durante el proceso de desarrollo, pero no son necesarios para que la aplicación funcione en producción. Esto puede incluir herramientas de construcción, pruebas, linters, etc. Puedes instalar dependencias de desarrollo usando el comando npm install <paquete> --save-dev.

- **Paquetes Globales**
Los paquetes globales son paquetes que se instalan en el sistema a nivel global, lo que significa que están disponibles para todos los proyectos. Aunque es menos común, algunos paquetes (como herramientas de línea de comandos) se pueden instalar globalmente para ser utilizados en varios proyectos. usando el comando npm install.

En resumen, hay varios tipos de paquetes que puedes instalar en Node.js, incluidas las dependencias de producción, las dependencias de desarrollo y los paquetes globales. Cada tipo tiene su uso y propósito específico en diferentes etapas de desarrollo y producción de tu proyecto.

## Versionado y actualización de paquetes

El versionado y la actualización de paquetes son aspectos esenciales en el desarrollo de aplicaciones en Node.js. Gestionar adecuadamente las versiones de los paquetes que utilizas es crucial para mantener la estabilidad de tu proyecto y garantizar que las actualizaciones no introduzcan problemas inesperados. Para lograrlo, Node.js utiliza el sistema de versionado semántico (SemVer).

- **Actualización de Paquetes**
```
npm update <paquete>

```


# Cómo usar este repositorio

- Clona este repositorio en tu máquina local:

   ```sh
   git clone https://github.com/sbstzuluaga1111/README.MD-Node-and-React.git


