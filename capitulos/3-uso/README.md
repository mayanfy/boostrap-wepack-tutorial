# Uso

Aqui de como descargar e instalar la herramienta configurada para su uso.

# Instalación

Ver las sección de [Requisitos](https://github.com/mayanfy/bootstrap-webpack-tutorial/blob/master/capitulos/1-primeros-pasos/1-requisitos.md) para mas informacion de las herramientas basicas.

> **A considerar:** Bootpack trae integrado las fuentes de [Font Awesome v4.7](https://fontawesome.com/v4.7.0/) y [Material Design Icons](https://materialdesignicons.com/), el uso de [SASS](https://sass-lang.com/) y [PUG](https://pugjs.org/api/getting-started.html).

## Descargar Bootpack

Desde la consola ejecutar

```bash
λ git clone https://github.com/mayanfy/bootpack.git /mi/directorio/aplicaciones/bootpack
```

## Instalar paquetes npm

Descargado el repositorio procedemos a instalar las dependecias de Bootpack. 

```bash
λ cd /mi/directorio/aplicaciones/bootpack
λ npm install
```

## Ejecutar Bootpack

Instaladas las dependencias se ejecuta uno de los siguientes comandos para tener los archivos de bootstrap en desarrollo o produccion. En ambos casos se generaran los archivos `main.css` y `app.js` dentro la carpeta definida para el proyecto.

```bash
# Comando para generar archivos de desarrollo
λ npm run dev

# Comando para generar archivos para producción
λ npm run prod
```

> Al ejecutar elguno de estos comandos se ejecuta `webpack-dev-server` el cual creara un localhost para ver los archivos en tiempo real, generalmente sera `http://localhost:3000`.

***

Cualquier consulta, critica o sugerencia es totalmente bienvenida. Desarrollado por [@chandzul](https://chandzul.com), [@sauware](https://sauware.com) con :heart: