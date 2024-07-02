# _PT-BR_

# Bind mount (_vincular volume_)

### O conceito de bind mount consiste em vincular um diretório específico do Docker Host à um diretório do container Docker.

> OBS: As alterações refletem em tempo real no container ao serem feitas no diretório presente no Docker Host.

### Hoje, existem duas maneiras de realizar um bind mount, as opções: -v (ou --volume) e --mount. 
> A diferença entre -v e --mount é trivial, onde quando -v é usado, se o diretório à ser vinculado não existir, ele criará. Se ocorrer o mesmo com --mount, ele retornará um erro. Isso traz mais integridade ao desenvolvimento.

## Realizando bind mount com a opção -v/--volume

````bash
# Executa o binds mount no container especificado

docker run -d --name nginx -p 8080:80 -v CAMINHO_DA_PASTA_A_SER_VINCULADA:CAMINHO_DA_PASTA_A_SER_VINCULADA_DENTRO_DO_CONTAINER

# Exemplo:

docker run -d --name nginx -p 8080:80 -v ~/src/projects/docker/bind_mounts/html:/usr/share/nginx/html
````

## Realizando bind mount com a opção --mount

````bash
# "--mount" -> especifica que o mount será realizado
# "type" -> especifica o tipo de mount que será realizado (bind, volume or tmpfs)
# "source" -> especifica o caminho na máquina da pasta que será vinculada ao container
# "target" -> especifica o caminho no container onde será vinculado o mount
# OBS: O helper "$(pwd)" pode ser usado para representar o caminho absoluto da pasta onde está sendo executado o comando

# Sintaxe

docker run -d --name nginx -p 8080:80 --mount type=TIPO_DO_MOUNT,source=CAMINHO_DA_PASTA_A_SER_VINCULADA,target=CAMINHO_DA_PASTA_A_SER_VINCULADA_DENTRO_DO_CONTAINER

# Exemplo:
docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html 
````

# _EN_

# Bind mount

### The concept of a bind mount involves linking a specific directory from the Docker Host to a directory within the Docker container

> NOTE: Changes made in the directory on the Docker Host will be reflected in real-time within the container.

### Today, there are two ways to perform a bind mount, using the options: -v (or --volume) and --mount.
> The difference between -v and --mount is subtle: when -v is used, if the directory to be linked does not exist, it will be created. If the same happens with --mount, an error will be returned. This brings more integrity to the development process.

## Performing a bind mount with the -v/--volume option

````bash
# Execute the bind mount in the specified container

docker run -d --name nginx -p 8080:80 -v HOST_DIRECTORY_PATH:CONTAINER_DIRECTORY_PATH

# Example:

docker run -d --name nginx -p 8080:80 -v ~/src/projects/docker/bind_mounts/html:/usr/share/nginx/html
````

## Performing a bind mount with the --mount option

````bash
# "--mount" -> specifies that a mount will be performed
# "type" -> specifies the type of mount to be performed (bind, volume, or tmpfs)
# "source" -> specifies the path on the host machine of the directory to be linked to the container
# "target" -> specifies the path in the container where the mount will be linked
# NOTE: The helper "$(pwd)" can be used to represent the absolute path of the directory where the command is being executed

# Syntax

docker run -d --name nginx -p 8080:80 --mount type=MOUNT_TYPE,source=HOST_DIRECTORY_PATH,target=CONTAINER_DIRECTORY_PATH

# Example:
docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html 
````
