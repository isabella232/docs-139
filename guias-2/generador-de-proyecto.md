---
description: 'Atomico ofrece un generador de proyectos mediante el siguiente script:'
---

# Generador de proyecto

```bash
npm init @atomico
```

 **Paso 1** Ingresamos un nomre para crear o recuperaar el directorio de nuestro proyecto

```bash
Welcome to Atomico, let's create your project

? Project destination folder? » hi-atomico # nombre de ejemplo   
```

**Paso 2** Para comenzar recomendamos la configuracion \`Started - ....\`, Esta nos permitira montar un servidor de desarrollo preconfigurado para Atomico.

```text
? Select the type of project » - Use arrow-keys. Return to submit.
>   Started - Hassle-free starter template, perfect for starting with Atomico
    Getting started with Atomico + Snowpack
```

El paso 2 finaliza copiando el contenido dentro del directorio asingado en el paso 1 y nos eseñara una lista de intrucciones para finalizar la instalacion. 

```bash
Your project has been created successfully, next steps:
1. cd hi-atomico
2. npm install
3. npm start
4. Enjoy Atomico!
```

El Comando **npm start**  nos enseñara el serivdor local para desarrollar con Atomico.

```bash
D:\hi-atomico>npm start

> atomico-base@0.0.0 start D:\hi-atomico
> estack dev src/**/*.{html,md}

Server running on http://localhost:8000

Build    Status    Duration  Time
ESbuild  Resolved  0.4s      17:51:33
Rollup   Resolved  0.3s      17:51:33
```



