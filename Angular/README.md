#Pasos para Ejecutar en Angular

## Dockerfile
1. Crear un archivo llamado Dockerfile y pegarlo a primer nivel del src
 . En la ultima linea reemplazamos "prueba-frontend-tsc"  por el nombre de tu proyecto

```bash
  #Primera Etapa
  
  FROM node:14-alpine as build-step

  RUN mkdir -p /app

  WORKDIR /app

  COPY package.json /app

  RUN npm install

  COPY . /app

  RUN npm run build --prod

  #Segunda Etapa
  FROM nginx:1.17.1-alpine

  #Si estas utilizando otra aplicacion cambia PokeApp por el nombre de tu app
  COPY --from=build-step /app/dist/prueba-frontend-tsc /usr/share/nginx/html

```

2. Pasos para ejecutar el dockerfile

```bash
  docker build -t prueba-frontend-tsc .
  docker run -d -it -p 4200:80 prueba-frontend-tsc
```

3. Dockerhub

```bash
  docker login
  docker tag prueba-frontend-tscr giank/prueba-frontend-tsc:v1
  docker push giank/prueba-frontend-tsc:v1
```