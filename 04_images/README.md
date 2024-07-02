# _PT-BR_

# Comandos básicos

````bash
# Exite todas as imagens baixadas na máquina

docker images
````

````bash
# Baixa a imagem na versão especificada

docker pull IMAGE_NAME:IMAGE_TAG
````

````bash
# Deleta a imagem na versão especificada

docker rmi IMAGE_NAME:IMAGE_TAG
````

# Comandos Dockerfile

````bash
# Especifica a imagem que será utilizada

FROM nginx:latest

# Acessa o path especificado dentro do container (caso não exista, ele cria)

WORKDIR /app

# Executa o comando especificado dentro do container, nesse caso, são usadas "\" para que possa haver a quebra de linha

RUN apt-get update && \
    apt-get install -y

# Copia uma pasta específica da máquina para dentro do container

# OBS: O path é definido a partir de onde está o Dockerfile

# COPY PATH_DA_PASTA_NA_MAQUINA PATH_DENTRO_DO_CONTAINER

COPY html /usr/share/nginx/html
````

# _EN_

# Basic Commands

````bash
# List all images downloaded on the machine

docker images
````

````bash
# Download the image with the specified version

docker pull IMAGE_NAME:IMAGE_TAG
````

````bash
# Remove the image with the specified version

docker rmi IMAGE_NAME:IMAGE_TAG
````

# Comandos Dockerfile

````bash
# Specify the image to be used

FROM nginx:latest

# Access the specified path inside the container (if it doesn't exist, it will be created)

WORKDIR /app

# Execute the specified command inside the container, in this case, "\" is used to allow line breaks

RUN apt-get update && \
    apt-get install -y

# Copy a specific directory from the machine into the container

# NOTE: The path is defined from where the Dockerfile is located

# COPY PATH_ON_MACHINE PATH_INSIDE_CONTAINER

COPY html /usr/share/nginx/html
````
