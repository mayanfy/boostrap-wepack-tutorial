# Configuración básica

Para construcción de bootpack se requiere de los siguientes archivos y carpetas.

Partiendo en que lo que queremos es generar el archivo `main.css` apartir del los archivos `.scss` de bootstrap, al igual que el archivo inicial de nuestra app que es `index.html` usamos el generador de templates [Pug](https://pugjs.org/) quedando de la siguiente forma.

```text
.
└── bootpack
    ├── dist
    ├── src
    	├── img
        ├── scss
        	└── app.scss
        ├── app.js
        └── index.pug
    ├── .gitignore
    ├── LICENCE
    ├── package.json
    ├── README.md
    └── webpack.config.js
```

# Inicializar npm

Para generar el archivo desde donde `npm` ejecuta webpack se crea el siguiente archivo `package.json` y este puede ser generado de dos formas en la raiz de nuestro poryecto bootpack:

1. En la consola nos dirijimos a la raiz del proyecto y ejecutamos `npm init`.
	* Enter a todas las opciones que nos pide.
2. En la raiz del proyecto creamos el archivo `package.json`.
	* Copiar y pegar lo siguiente.

```json
{
  "name": "bootpack",
  "version": "1.0.0",
  "description": "desarrollar sitios html con bootstrap y webpack",
  "main": "webpack.config.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "bootstrap",
    "webpack",
    "css",
    "html"
  ],
  "author": "@nickname",
  "license": "MIT"
}

```

# Instalar webpack

Sin entrar en tanto detalle webpack es un empaquetador de módulos, que permite encapsular los modulos que necesites en tu aplicación en un solo archivo generalmente llamado `bundle.js`, pero webpack al ser muy versatil permite el uso de bundles o pequeños scripts que hacen tareas especificas que permiten trabajar con archivos `.scss` para compilar css, `.pug` para compilar html, etc. Esto permite que al estar desarrollando nuestra app con **webpack** sea de una forma mas ágil y organizada.

Para el uso de webpack se requiere dos paquetes que trabajan en conjunto para ejecutar las tareas que se configuren en el archivo `webpack.config.js` y estos son `webpack` y `webpack-cli`, los comandos que ejectuaremos en la raiz de nuestro proyecto son:

**1. Instalar webpack**

```bash
npm install --save-dev webpack@4.12.0
```

**2. Instalar webpack-cli**

```bash
npm install --save-dev webpack-cli@3.0.3
```
___

> Usamos `--save-dev` para que nuestros bundles de desarrollo se guarde en `"devDependencies": {}` de nuestro archivo `package.json`

# Configurar webpack

Para construir nuestra app requerimos decirle a webpack que es lo que necesita hacer y como debe hacerlo. Para esto webpack buscar el archivo `webpack.congif.js` que esta en la raiz de bootpack. Aqui es donde se configura las tareas que queremos que webpack ejecute.

Para la configuración basica se requiere de dos puntos iniciales:

1. entry: archivo o archivos desde donde webpack busca todo nuestro código.
2. output: donde estara ubicado nuestro archivo de salida con todo nuestro codigo compilado.

**NOTA:** Como podemos estar trabajando en diferentes entornos(Windows, Linux, Mac OS) usaremos una libreria que resuelva las url donde se buscara los archivos de entrada y donde se generara los archivos de salida, para esto usaremos `path` que ya viene instalado con node.

**Quedando de la siguiente forma:**

```javascript
//  webpack.config.js 
const path = require('path');

const config = {
    entry: './src/app.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'js/bundle.js'
    }
};

module.exports = config;
```

Configurar los comandos para ejecutar webpack. En el archivo `package.json` de la raiz de bootpack, añadir las siguientes lineas de codigo:

```json
{
  "name": "bootpack",
  ...
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack --mode development",
    "build": "webpack --mode production"
  },
  ...
}

```


> Ejecutamos el comando `npm run dev`


Al ejecutar el comando `npm run dev` se genera el archivo `js/bunble.js` dentro la carpeta `dist/`,  este es el archivo de salida de la app que definimos en `webpack.config.js`.

***

Cualquier consulta, critica o sugerencia es totalmente bienvenida. Desarrollado por [@chandzul](https://chandzul.com), [@sauware](https://sauware.com) con :heart: