# Inicio rápido

Instalar **npm**, este viene con la instalación de [Node JS](https://nodejs.org/es/) para el ejecutar bootpack se trabajo con la versión Actual(v10.4.0).

?> **A considerar:** Bootpack trae integrado los las fuentes de [Font Awesome v4.7](https://fontawesome.com/v4.7.0/) y [Material Design Icons](https://materialdesignicons.com/)

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

Ya que los paquetes se han instalado ejecutamos podemos ejecutar uno de los siguientes comandos para tener los archivos de bootstrap. En este caso sera el archivo **CSS** y **JS**.

```bash
# Comando para generar archivos de desarrollo
λ npm run dev

# Comando para generar archivos para producción
λ npm run prod
```