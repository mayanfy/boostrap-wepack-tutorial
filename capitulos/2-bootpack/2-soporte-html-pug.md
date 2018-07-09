# Soporte Html con Pug 

En esta sección se configurará el soporte de html con pug. Que es el framework que genera los archivos `.html`.

Para usar Pug instalamos los siguientes loaders que darán el soporte para su uso. Para esto nos redireccionamos desde la Consola a la raiz del proyecto y ejecutamos los siguientes comandos.

### 1. Instalar pug

Loader que interpreta los archivos `.pug`.

```bash
npm install --save-dev pug
```

### 2. Instalar pug html loader

Loader que interpreta etiquetas pug y las pasa a etiquetas html.

```bash
npm install --save-dev pug-html-loader
```

### 3. Instalar html loader

La tarea de este loader es buscar dentro los  `.html` las url de las imagenes y ponerla de forma correcta. 

Por ejemplo si en `index.html` encuentra una imagen `src/img/nombreimagen.jpg` pone la dirección `dist/img/nombreimagen.jpg` del directorio de salida.

```bash
npm install --save-dev html-loader
```

### 4. Instalar html webpack plugin

Loader para configurar y definir los templates pug-html y exportarlo a la carpeta `dist/`

```bash
npm install --save-dev html-webpack-plugin
```

Despues de la instalación de los loader's el archivo `package.json` añadio las siguientes lineas.

```json
{
  ...
  "devDependencies": {
    "html-loader": "^0.5.5",
    "html-webpack-plugin": "^3.2.0",
    "pug": "^2.0.3",
    "pug-html-loader": "^1.1.5",
    "webpack": "^4.12.0",
    "webpack-cli": "^3.0.3"
  }
}

```

# Configurar el archivo webpack.config.js

Añadir las siguientes lineas al archivo `webpack.config.js`, esto es para usar los loaders de pug en nuestro proyecto.

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');

const config = {
    ...
    module: {
        rules: [
            {
                test: /\.pug$/,
                use: [
                    {
                        loader: 'html-loader',
                        options: {
                            publicPath: "./images"
                        }
                    },
                    {
                        loader: 'pug-html-loader', 
                        options: { 
                            pretty: "    " 
                        }
                    }
                ]
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
            filename: 'index.html',
            template: 'src/index.pug'
        })
    ]
};

module.exports = config;
```

Quedando el archivo `webpack.config.js` de la siguiente forma:

```javascript
//  webpack.config.js 
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

const config = {
    entry: './src/app.js',

    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'js/bundle.js'
    },
    module: {
        rules: [
            {
                test: /\.pug$/,
                use: [
                    {
                        loader: 'html-loader',
                        options: {
                            publicPath: "./images"
                        }
                    },
                    {
                        loader: 'pug-html-loader', 
                        options: { 
                            pretty: "    " 
                        }
                    }
                ]
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
            filename: 'index.html',
            template: 'src/index.pug'
        })
    ]
};

module.exports = config;
```

En esta configuracion se observa dos bloques que son `module: {}` y `plugins: []`. 

**module:** Esta sección se define las tareas o reglas que webpack ejecutará, se configuran en `rules: {}`.

ejemplo: se busca los archivos `.pug` y esta regla convierte las etiquetas pug en etiquetas html.

**plugins:** Realizan tareas espeficicas, que no pueden ser definidas en `module: {}`.

Ejemplo: con el plugin `HtmlWebpackPlugin` se determina el archivo `index.pug` a ser renderizado en un archivo `index.html`. Con este plugin se genera "fisicamente" el archivo `dist/index.html`.

# Ejecutar pug

**1.** Configurar el archivo `src/index.pug` con el siguiente codigo.

```html
<!DOCTYPE html>
html(lang="en")
head
  meta(charset="UTF-8")
  title index
body
  h1 Hola mundo!
```

**2.** En la Consola desde la raiz del proyecto ejecutar:

```bash
npm run dev
```

La salida es `dist/index.html`.

```html
<!DOCTYPE html>
<html lang="en"></html>
<head>
    <meta charset="UTF-8"/>
    <title>index</title>
</head>
<body>
    <h1>Hola mundo!</h1>
    <script type="text/javascript" src="js/bundle.js"></script>
</body>
```

> ir a  [Configurar css con sass]() 

***

Cualquier consulta, critica o sugerencia es totalmente bienvenida. Desarrollado por [@chandzul](https://chandzul.com), [@sauware](https://sauware.com) con :heart: