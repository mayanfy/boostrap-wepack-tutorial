# Soporte Html con Pug 

En esta seccion lo que haremos es instalar el soporte de html con Pug ya que aqui es donde vamos poder ver la magia que sucede cuando se va programndo los estilos de css que seran generados con sass, claro, con el soporte de bootstrap 4.


# Instalando 

Para poder usar el Pug intalamos las siguientes dependencias o loaders que nos daran el soporte para poder usarlos.

### 1. Instalar html loader

Este loader lo que hace es que si dentro el archivo html usamos imagenes nos ponga de forma correcta la direcciones donde se encuentra en nuestro directorio `dist`.

```bash
npm install --save-dev html-loader
```

### 2. Instalar pug

Esto loader nos da el soporte para poder interpretar los archivos pug.

```bash
npm install --save-dev pug
```

### 3. Instalar pug html loader

Este loader lo que hace es leer un archivo con etiquetas pug y pasarlas a etiquetas html tradicionales.

```bash
npm install --save-dev pug-html-loader
```

### 4. Instalar html webpack plugin

Este loader nos ayuda a definir nuestro templates html y exportarlo a nuestra carpeta `dist`

```bash
npm install --save-dev html-webpack-plugin
```

# configurando el archivo webpack.config.js

Añadimos las siguientes lineas al archivo dejando las que se habian puesto en el paso anterior, esto es para poder usar la dependecia de pug a nuestro proyecto de bootpack.

```javascript
//  webpack.config.js 
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

const config = {
    entry: './src/app.js',

    output: {
        path: path.resolve(__dirname, 'public'),
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

Como pueden observar aqui estamos añadiendo varias lineas de codigo, que al principio no tiene mucho sentido, para fines ilustrativos efoquemonos en  `module: {}` y `plugins: []`. 

**modules:** En esta seccion vamos a definr las tareas o reglas que queremos que webpack ejecute, estas las definimos dentro la etiqueta `rules: {}` un ejemplo seria tomar los templates o archivos de pug que creemos y con estas reglas le decimos que todo el codigo pug se genere las etiquetas html tracionales.

**plugins:** Estas hacen tareas espeficicas, como por ejemplo en este caso que estamos usando pug, con `HtmlWebpackPlugin` le decimos que tome el template de `index.pug`, y lo renderize en un archivo `index.html`. y ustedes diran pero ya en las reglas le dije que haga esa tarea, si asi es pero esas reglas nos genera el archivo `.html` entonces con este plugin es con el que generamos "fisicamente" nuestros archivos html.