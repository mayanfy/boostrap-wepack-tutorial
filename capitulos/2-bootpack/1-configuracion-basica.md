# Configuración básica

Crear la siguiente estructura de directorios para el proyecto, separando el código "fuente" `/src` del código "de distribución" `/dist`.

Para la construccion de bootpack se requiere el siguiente arbol de archivos.

```text
.
└── bootpack
    ├── dist/
    ├── src/
    	├── img/
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

> **Nota:** Se usara el framework de _Pug_ para generar los archivos `.html`

# Inicializar npm

Para instalar los bundles se crea `package.json`. Para esto tenemos dos opciones: 

1. Desde la Consola, redirecciónar a la raiz del proyecto y ejecutar `npm init`.
	 * Enter a todas las opciones que nos pide.
   * Se genera el archivo `package.json`.
2. En la raiz del proyecto crear el archivo `package.json`.
	* Copiar y pegar lo siguiente.

```json
{
  "name": "bootpack",
  "version": "1.0.0",
  "description": "desarrollar páginas web html con bootstrap y webpack",
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

La instalación de webpack requiere los bundles de `webpack` y `webpack-cli` que son instalados con *npm*.

**1. Instalar el bundle webpack**

```bash
npm install --save-dev webpack@4.12.0
```

**2. Instalar el bundle webpack-cli**

```bash
npm install --save-dev webpack-cli@3.0.3
```

> **Nota:** `--save-dev` se usa para que los bundles de desarrollo se guarde en `"devDependencies": {}` en el archivo `package.json`.

Depues de la instalación de los bundles, en el archivo `package.json` se añadieron las siguientes lineas automaticamente.

```json
{
  ...
  "devDependencies": {
    "webpack": "^4.12.0",
    "webpack-cli": "^3.0.3"
  }
}
```

# Configurar webpack

Para la configuración se requiere de dos conceptos iniciales:

1. entry: archivo o archivos donde se encuentra el codigo de entrada.
2. output: donde estará ubicado el archivo de salida.

**NOTA:** Dependiendo del entorno de trabajo(Windows, Linux, Mac OS) se usara la libreria `path` que resuelva los directorios donde estan los archivos de entrada y donde se generará los archivos de salida.

**Paso 1.** Abrir el archivo `webpack.config.js`, copiar y pegar el siguiente código:

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

**Paso 2.** Configurar los comandos para ejecutar webpack. En el archivo `package.json`, añadir las siguientes lineas de codigo:

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

**Paso 3.** Desde la Consola en la raiz del proyecto ejecutar el comando:

```bash
npm run dev
```


Al ejecutar el comando `npm run dev` se genera el archivo `js/bunble.js` dentro la carpeta `dist/`,  este es el archivo de salida del proyecto definido en `webpack.config.js`.  

***

Cualquier consulta, critica o sugerencia es totalmente bienvenida. Desarrollado por [@chandzul](https://chandzul.com), [@sauware](https://sauware.com) con :heart: