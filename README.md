# Docker Básico
Docker - Primeiros Passos

## Comandos Básicos

### Listar as imagens disponíveis no sistema
`docker images`

### Baixa uma imagem, podendo definir uma versão (tag) específica
`docker pull ubuntu`
`docker pull ubuntu:16.10`

### Procura por uma imagem específica
`docker search php`

### Executa um container a partir de uma imagem
`docker run ubuntu`

### Analisa os containers em execução no sistema
`docker ps`
`docker ps -a`

### A opção “q” retorna somente o código dos containers
`docker ps -qa`

### Executa um container permitindo a sua interação com o console do container (-it)
`docker run ubuntu -it bash`

### Para a execução de todos os containers
`docker stop $(docker ps)`

### Remove um container específico
`docker rm`

### Remove todos os containers no sistema
`docker rm $(docker ps -qa)`

### Remove uma lista de imagens no sistema
`docker rmi $(docker images -q)`

## Volumes

### Lista todos os volumes disponíveis no sistema.
`docker volume ls`

### Remove o ultimo volume criado.
`docker volume remove $(docker volume ls -q | head -n 1)`

### Mapeia o ultimo volume criado com um novo container.
`docker run --rm -it -v $(docker volume ls -q | head -n 1):/myvol treinaweb/volume ls /myvol`

### Cria um novo volume nomeado.
`docker volume create treinaweb`

### Cria um container anexando o volume nomeado treinaweb.
`docker run --rm -it -v treinaweb:/myvol treinaweb/volume ls /myvol`

### Lista as informações do volume nomeado treinaweb.
`docker volume inspect treinaweb`

## Gerenciamento de redes entre containers

### Lista os network disponíveis.
`docker network ls`

### Inspeciona informações do network bridge.
`docker network inspect bridge`

### Cria um novo network do tipo bridge chamado treinaweb.
`docker network create --driver bridge treinaweb`

### Executa um novo container, inserindo o network adapter chamado treinaweb.
`docker run --network=treinaweb -itd --name container3 busybox`

### Conecta um container já em execução a uma network, definindo um apelido dentro daquela rede.
`docker network connect --alias c1 treinaweb container1`
















