# Instalación

Instalar **npm**, este viene con la instalación de [Node JS](https://nodejs.org/es/) para el ejecutar bootpack se instalo la versión Actual(v10.4.0).

?> **A considerar:** Bootpack trae integrado las fuentes de [Font Awesome v4.7](https://fontawesome.com/v4.7.0/) y [Material Design Icons](https://materialdesignicons.com/)

## Descargar Bootpack

Para esto usamos la consola de windows o en su caso usar [cmder](http://cmder.net/).

```bash
λ mkdir directorio/aplicaciones/bootpack
λ cd directorio/aplicaciones/bootpack
λ git init
λ git remote add origin https://github.com/mayanfy/bootpack.git
λ git fetch origin master
λ git pull origin master
```

## Instalar paquetes npm

Una vez que tenemos instalado npm y descargado el repositorio procedemos a instalar los paquetes del cual depende Bootpack. 

``` bash
λ npm install
```

## Ejecutar Bootpack

Una vez instaladas las dependencias pasamos a ejecutar uno de los siguientes comandos para tener los archivos de bootstrap dependiendo si es cuando estamos desarrollando o en su caso ya es para producción. En ambos casos se generaran los archivos `main.css` y `app.js` dentro la carpeta definida para el proyecto.

```bash
# Comando para generar archivos de desarrollo
λ npm run dev

# Comando para generar archivos para producción
λ npm run prod
```

?> Al ejecutar elguno de estos comandos no olvidemos que se ejecutara `webpack-dev-server` mismo que nos creara un localhost para ver nuestro archivo en ejecución, generalmente sera `http://localhost:3000` a menos que le indiquemos lo contrario.

***

Desarrollado por [@chandzul](https://chandzul.com), [@sauware](https://sauware.com) con :heart: