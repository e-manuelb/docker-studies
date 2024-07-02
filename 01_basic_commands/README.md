# _PT-BR_

# COMANDOS BÁSICOS

## Listando containers

````bash
# Exibe todos os containers em execução na máquina

docker ps

# Siglas
# "-a/--all" -> mostra todos os containers ativos e inativos que existem na máquina
# "-f/--filter" -> filtra a listagem de container baseado nas condições dadas (table, json ou para mais informações, acesse: https://docs.docker.com/go/formatting)
# "--format" -> 

docker ps -a
````

## Executando containers

````bash
# Executa o container com a imagem informada.
# Para mais informações sobre imagens disponívels, consulte: https://hub.docker.com/
docker run image_version

# Executa o container informado, com a imagem e versão informada.
docker run image_name:image_version
````

## Interações com o container
````bash
# "-i" -> Interactive Mode - mantém o STDIN ativo e mantém o processo do container em execução
# "-t" -> TTY (Teletype) - permite que sejam enviados comandos pelo STDIN dentro do contexto do container Docker
# "--rm" -> Remove (talvez?) - deleta o container após o fim da execução
# "--name" -> Name - dá um nome ao container

# O que vier após a especificação da imagem à ser utilizada, será executado no contexto do container, por exemplo:
docker run -it ubuntu:latest bash
docker run -i -t ubuntu:latest bash

# Outros exemplos com options:
docker run -it --rm ubuntu:latest bash
docker run -it --rm --name ubuntu-container ubuntu:latest bash
````

## Exposição de portas

> Algumas imagens de container Docker possuem portas previamente abertas para o processo do container. Para expôr elas, é preciso realizar o redirecionamento para uma porta do Docker Host.

````bash
# "-p/--publish" -> efetua o redirecionamento da porta do container (inacessível) para uma porta disponível na máquina (Docker Host).
# Por exemplo:

docker run -p PORTA_NO_DOCKER_HOST:PORTA_NO_CONTAINER nginx

# Por padrão, o NGINX utiliza a porta 80 como exposta.

docker run -p 8080:80 nginx

# Neste exemplo, a porta 8080 da máquina (Docker Host), redirecionará para a porta 80 do container NGINX quando acessada
````

## Desassociando o processo do container do terminal

````bash
# "-d/--detach" -> executa o container em segundo plano e retorna o ID do container executado

docker run -d -p 8080:80 nginx
````

## Parar o container em execução

````bash
# O comando a seguir para o container em execução
docker stop CONTAINER_ID
````

## Deletar o container

````bash
docker rm CONTAINER_ID
# ou
docker rm CONTAINER_NAME
````

## Acessando o container em execução

````bash
# Acessa o container em execução com o nome especificado e executa o comando informado
docker exec CONTAINER_NAME COMMAND
# Exemplo:
docker exec ubuntu:latest bash
````
````bash
# Acessa o container em execução e permite input de dados, com o modo interativo, apresentado em tópicos anteriores.
docker exec -it ubuntu:latest bash 
````

# _EN_

## BASIC COMMANDS

## Listing commands

````bash
# Displays all running containers on the machine

docker ps

# Flags
# "-a/--all" -> shows all active and inactive containers that exist on the machine
# "-f/--filter" -> filters the container listing based on the given conditions (table, json, or for more information, access: https://docs.docker.com/go/formatting)
# "--format" -> 

docker ps -a
````

## Running Containers

````bash
# Runs the container with the specified image.
# For more information on available images, see: https://hub.docker.com/
docker run image_version

# Runs the specified container, with the image and version specified.
docker run image_name:image_version
````

## Container Interactions

````bash
# "-i" -> Interactive Mode - keeps STDIN active and keeps the container process running
# "-t" -> TTY (Teletype) - allows commands to be sent through STDIN within the Docker container context
# "--rm" -> Remove (maybe?) - deletes the container after execution
# "--name" -> Name - gives a name to the container

# What comes after the specification of the image to be used will be executed in the context of the container, for example:
docker run -it ubuntu:latest bash
docker run -i -t ubuntu:latest bash

# Other examples with options:
docker run -it --rm ubuntu:latest bash
docker run -it --rm --name ubuntu-container ubuntu:latest bash
````

## Port Exposure
> Some Docker container images have ports pre-opened for the container process. To expose them, you need to redirect them to a Docker Host port.

````bash
# "-p/--publish" -> forwards the container port (inaccessible) to a port available on the machine (Docker Host).
# For example:

docker run -p HOST_PORT:CONTAINER_PORT nginx

# By default, NGINX uses port 80 as exposed.

docker run -p 8080:80 nginx

# In this example, port 8080 of the machine (Docker Host) will redirect to port 80 of the NGINX container when accessed
````

## Detaching the Container Process from the Terminal

````bash
# "-d/--detach" -> runs the container in the background and returns the ID of the executed container

docker run -d -p 8080:80 nginx
````

## Stopping the Running Container
````bash
# The following command for the running container
docker stop CONTAINER_ID
````

## Deleting the Container
````bash
docker rm CONTAINER_ID
# or
docker rm CONTAINER_NAME
````

## Accessing the Running Container
````bash
# Access the running container with the specified name and execute the specified command
docker exec CONTAINER_NAME COMMAND
# Example:
docker exec ubuntu:latest bash
````
````bash
# Access the running container and allow data input, with the interactive mode, presented in previous topics.
docker exec -it ubuntu:latest bash 
````
