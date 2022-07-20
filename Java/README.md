#Pasos para Ejecutar en java

## Dockerfile
1. Crear un archivo llamado Dockerfile y pegarlo a primer nivel del pom
. <artifactId>prueba-back-TSC</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	
```bash
  FROM openjdk:8-jdk-alpine
  VOLUME /tmp
  EXPOSE 8080
  ADD ./target/prueba-back-TSC-0.0.1-SNAPSHOT.jar prueba-back-TSC.jar
  ENTRYPOINT ["java","-jar","/prueba-back-TSC.jar"]

```

2. Pasos para ejecutar el dockerfile

```bash
  mvn package
  docker build --tag "prueba-back-tsc:v1" .
  docker images
  docker run prueba-back-tsc:v1 
  docker run -p 8080:8080 --name prueba-back-tsc prueba-back-tsc:v1
  docker ps
  
```

3. Dockerhub

```bash
  docker login
  docker tag prueba-back-tsc:v1 giank/prueba-back-tsc:v1
  docker push giank/prueba-back-tsc:v1
```