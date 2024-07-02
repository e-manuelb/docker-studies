# _PT-BR_

# Network

## Tipos de Network

- Bridge (Padrão)

- Host -> Quando um container tem esse tipo de network ele se integra a network da máquina host, ou seja, não necessário
  fazer a exposição das portas do container

- Overlay -> Serve como um intermediador para comunicação entre Cluster Docker de máquinas diferentes

- Maclan -> para mais informações, acesse: https://docs.docker.com/network/drivers/macvlan/

- None -> O container roda de forma isolada

## Comandos básicos

```bash
# Exibe todas as networks existentes

docker network ls
```

```bash
# Exibe informações da network especificada

docker network inspect NETWORK_NAME

# Exemplo:

docker network inspect bridge
```

```bash
# Cria uma Network com as informações especificadas

docker network create --drive NETWORK_TYPE NETWORK_NAME

# Exemplo:

docker network create --driver bridge minharede
```

## Executando container no escopo da rede customizada

```bash
# Executa o container no escopo da rede especificada

docker run -dit -name ubuntu1 --network NETWORK_NAME bash

# Exemplo:

docker run -dit -name ubuntu1 --network minharede bash
```

## Conectando container já em execução a uma Network

```bash
# Conecta o container a rede especificada

docker network connect NETWORK_NAME CONTAINER_NAME

# Exemplo:

docker network connect minharede ubuntu3
```

## Container acessando a máquina

```bash
# Dentro do container o "http://host.docker.internal" referencia a minha máquina

curl http://host.docker.internal:8000
```

# _EN_

# Network

## Network types

- Bridge (Default)

- Host -> When a container has this type of network, it integrates with the host machine's network, meaning it is not necessary to expose the container's ports

- Overlay -> Serves as an intermediary for communication between Docker clusters on different machines

- Macvlan -> for more information, see: https://docs.docker.com/network/drivers/macvlan/

- None -> The container runs in isolation

## Comandos básicos

```bash
# List all existing networks

docker network ls
```

```bash
# Display information about the specified network

docker network inspect NETWORK_NAME

# Example:

docker network inspect bridge
```

```bash
# Create a network with the specified information

docker network create --driver NETWORK_TYPE NETWORK_NAME

# Example:

docker network create --driver bridge mynetwork
```

## Running a container within the scope of the custom network

```bash
# Run the container within the specified network

docker run -dit --name ubuntu1 --network NETWORK_NAME bash

# Example:

docker run -dit --name ubuntu1 --network mynetwork bash
```

## Connecting an already running container to a Network

```bash
# Connect the container to the specified network

docker network connect NETWORK_NAME CONTAINER_NAME

# Example:

docker network connect mynetwork ubuntu3
```

## Container accessing the host machine

```bash
# Connect the container to the specified network

docker network connect NETWORK_NAME CONTAINER_NAME

# Example:

docker network connect mynetwork ubuntu3
```
