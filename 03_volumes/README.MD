# _PT-BR_

# Volumes

### Os volumes são utilizados para compartilhar dados entre containers sem a necessidade de uso de paths absolutos ou relativo dos arquivos.
> OBS: Um volume pode ser compartilhado por um ou mais containers, e sempre quando for adicionado algum item no volume, será refletido em todos os containers que estão vinculados a ele.

## Comandos básicos

````bash
# Exibe todos os volumes disponíveis

docker volume ls
````

````bash
# Cria um volume com o nome especificado

docker volume inspect VOLUME_NAME
````

````bash
# Remove todos os volumes que não estão sendo utilizados por containers
docker volume prune
````

````bash
# Deleta o volume com nome especificado
docker volume rm VOLUME_NAME
````

## Mapeando um volume para o container

````bash
# Efetua o mapeamento do volume especificado para o container, para isso, utilizaremos os bind mounts

docker run -d -p 8080:80 --name nginx --mount type=volume,source=VOLUME_NAME,target=CAMINHO_DENTRO_DO_CONTAINER nginx

# ou

docker run -d -p 8080:80 --name nginx -v VOLUME_NAME:CAMINHO_DENTRO_DO_CONTAINER nginx

# EX:

docker run -d -p 8080:80 --name nginx --mount type=volume,source=myvolume,target=/app nginx

# ou

docker run -d -p 8080:80 --name nginx -v myvolume:/app nginx
````

# _EN_

# Volumes

### Volumes are used to share data between containers without the need to use absolute or relative file paths.
> NOTE: A volume can be shared by one or more containers, and any items added to the volume will be reflected in all containers linked to it.

## Basic Commands

````bash
# List all available volumes

docker volume ls
````

````bash
# Create a volume with the specified name

docker volume inspect VOLUME_NAME
````

````bash
# Remove all volumes not used by any containers
docker volume prune
````

````bash
# Delete the volume with the specified name
docker volume rm VOLUME_NAME
````

## Mapping a volume to a container

````bash
# Map the specified volume to the container using bind mounts

docker run -d -p 8080:80 --name nginx --mount type=volume,source=VOLUME_NAME,target=PATH_INSIDE_CONTAINER nginx

# or

docker run -d -p 8080:80 --name nginx -v VOLUME_NAME:PATH_INSIDE_CONTAINER nginx

# EX:

docker run -d -p 8080:80 --name nginx --mount type=volume,source=myvolume,target=/app nginx

# or

docker run -d -p 8080:80 --name nginx -v myvolume:/app nginx
````
