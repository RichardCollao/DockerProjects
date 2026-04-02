Crea un contenedor a partir de una imagen, pero no lo inicia automáticamente
```html
docker create --name mi_nginx -p 8080:80 nginx:latest
```
Crea y/o ejecuta un contenedor a partir de una imagen.
```html
docker run <opciones> <nombre_imagen>
```
Lista los contenedores en ejecución.
```html
docker ps
```
Lista todos los contenedores aunque no esten en ejecución.
```html
docker ps -a
```
Detiene un contenedor en ejecución.
```html
docker stop <nombre_contenedor>
```
Inicia un contenedor detenido.
```html
docker start <nombre_contenedor>
```
Reinicia un contenedor.
```html
docker restart <nombre_contenedor>
```
Elimina un contenedor.
```html
docker rm <nombre_contenedor>
```
Lista las imágenes de Docker disponibles localmente.
```html
docker images
```
Descarga una imagen desde un registro (como Docker Hub).
```html
docker pull <nombre_imagen>
```
Para una arquitectura específica
Descarga una imagen desde un registro (como Docker Hub). docker pull <nombre_imagen>
```html
docker pull --platform linux/arm64 ubuntu:latest
```
Construye una imagen a partir de un Dockerfile.  docker build <opciones> <ruta_dockerfile>
```html
docker build -t mi_app_python
```
```html
docker build -f ruta/al/miDockerfile -t mi_app .
```
Sube una imagen a un registro.
```html
docker push <nombre_imagen>
```
Lista los nombres de todos los contenedores activos en Docker
```html
docker ps --format "{{.Names}}"
```
Ejecuta un comando dentro de un contenedor en ejecución. docker exec <opciones> <nombre_contenedor> <comando>
```html
docker exec -it sonarqube bash
```
Muestra los registros (logs) de un contenedor.
```html
docker logs <nombre_contenedor>
```
Crea e inicia los servicios definidos en un archivo docker-compose.yml.
```html
docker compose up
```
```html
docker compose up -d --force-recreate
```
Detiene y elimina los contenedores, redes y volúmenes definidos en un archivo docker-compose.yml.
```html
docker compose down
```

Mostrará una lista de todos los volúmenes, estén o no en uso.
```html
docker volume ls
```
Ver los detalles de un volumen específico
```html
docker volume inspect NOMBRE_DEL_VOLUMEN
```
Listar solo los volúmenes que NO están en uso
```html
docker volume ls -qf dangling=true
```
Eliminar los volúmenes que no están en uso
```html
docker volume prune
```
Elimina todos los volúmenes
```html
docker volume rm $(docker volume ls -q) 
```

DOCKER COMPOSER
CREAR CONTENEDOR CON DISCO COMPARTIDO
crear archivo docker-compose.yml
```html
version: '3.8'

services:
  sonarqube:
    image: sonarqube
    container_name: sonarqube
    ports:
      - "9000:9000"
    volumes:
      - D:/:/disco-d
    environment:
      - SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
```


PUBLICAR IMAGEN
Perfecto. Guía desde docker login -u richardcollao:

Login en Docker Hub

docker login -u richardcollao
Si tienes 2FA, usa un Access Token como contraseña.
Construir imagen

docker build -t richardcollao/sonar-app:1.0.0 /home/richard/Docker/SonarProject
Subir imagen

docker push richardcollao/sonar-app:1.0.0
Verificar que existe en Docker Hub

























