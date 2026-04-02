# Docker - guía rápida

## Contenedores

Crear un contenedor sin iniciarlo:
```bash
docker create --name mi_nginx -p 8080:80 nginx:latest
```

Crear e iniciar un contenedor:
```bash
docker run <opciones> <imagen>
```

Listar contenedores en ejecución:
```bash
docker ps
```

Listar todos los contenedores (incluye detenidos):
```bash
docker ps -a
```

Detener un contenedor:
```bash
docker stop <contenedor>
```

Iniciar un contenedor detenido:
```bash
docker start <contenedor>
```

Reiniciar un contenedor:
```bash
docker restart <contenedor>
```

Eliminar un contenedor:
```bash
docker rm <contenedor>
```

Ejecutar un comando dentro de un contenedor en ejecución:
```bash
docker exec -it <contenedor> bash
```

Ver logs de un contenedor:
```bash
docker logs <contenedor>
```

Listar solo nombres de contenedores en ejecución:
```bash
docker ps --format "{{.Names}}"
```

## Imágenes

Listar imágenes locales:
```bash
docker images
```

Descargar una imagen:
```bash
docker pull <imagen>
```

Descargar imagen para arquitectura específica:
```bash
docker pull --platform linux/arm64 ubuntu:latest
```

Construir una imagen desde Dockerfile (directorio actual):
```bash
docker build -t mi_app_python .
```

Construir usando un Dockerfile específico:
```bash
docker build -f ruta/al/Dockerfile -t mi_app .
```

Subir imagen a un registry:
```bash
docker push <imagen>
```

## Docker Compose

Crear e iniciar servicios:
```bash
docker compose up
```

Crear e iniciar en segundo plano, recreando contenedores:
```bash
docker compose up -d --force-recreate
```

Detener y eliminar contenedores y redes del compose:
```bash
docker compose down
```

## Volúmenes

Listar volúmenes:
```bash
docker volume ls
```

Ver detalle de un volumen:
```bash
docker volume inspect <volumen>
```

Listar volúmenes no utilizados:
```bash
docker volume ls -qf dangling=true
```

Eliminar volúmenes no utilizados:
```bash
docker volume prune
```

Eliminar todos los volúmenes:
```bash
docker volume rm $(docker volume ls -q)
```

## Publicar imagen en Docker Hub

Login (si tienes 2FA, usar Access Token como contraseña):
```bash
docker login -u richardcollao
```

Construir imagen:
```bash
docker build -t richardcollao/sonar-app:1.0.0 /home/richard/Docker/SonarProject
```

Subir imagen:
```bash
docker push richardcollao/sonar-app:1.0.0
```

Verificar en Docker Hub que la imagen existe.

























