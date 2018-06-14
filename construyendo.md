# Construyendo Bootpack

Lo que se hizo para integrar y generar el css de bootstrap, tipografias, efectos css y html todo con el framework webpack.

Bootpack nacio de la necesidad de querer hacer templates html de una forma rapida con el framework de bootstrap, al querer hacer esto se detecto que no habia una forma estandarizada para hacerlo, despues de buscar y leer unos cuantos tutoriales se percato que todos hacian o resolvian una parte de la necesidad como son por ejemplo usar bootsstrap 4 con webpack, el uso de iconos tipograficos, el uso de sass o incrustar caracteristicas especiales para hacer el maquetado.

?> Entonces nace **Bootpack** para solucionar esta necesidad.

# Índice

1. [Estructura](construyendo?id=estructura)
2. [Inicializar npm](construyendo?id=inicializar-npm)
3. [Instalar Webpack](construyendo?id=instalar-webpack)
4. [Configurar Webpack](construyendo?id=configurar-webpack)


# Estructura

Para construcción de bootpack se requiere de los siguientes archivos y carpetas.

Partiendo en que lo que queremos es generar el archivo `main.css` apartir del los archivos `.scss` de bootstrap, al igual que el archivo inicial de nuestra app que es `index.html` usamos el generador de templates [Pug](https://pugjs.org/) quedando de la siguiente forma.

```text
.
└── bootpack
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

Sin antrar en tanto detalle webpack es un empaquetador de módulos, que permite encapsular los modulos que necesites en tu aplicación en un solo archivo generalmente llamado `bundle.js`, pero webpack al ser muy versatil permite el uso de bundles o pequeños scripts que hacen tareas especificas que permiten trabajar con archivos `.scss` para compilar css, `.pug` para compilar html, etc. Esto permite que al estar desarrollando nuestra app con **webpack** sea de una forma mas ágil y organizada.

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

?> Usamos `--save-dev` para que nuestros bundles de desarrollo se guarde en `"devDependencies": {}` de nuestro archivo `package.json`

# Configurar webpack

