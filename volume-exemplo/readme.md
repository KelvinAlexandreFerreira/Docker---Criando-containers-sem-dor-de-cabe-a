Aprendemos neste capítulo:

Comandos básicos do Docker para podermos baixar imagens e interagir com o container.
Imagens do Docker possuem um sistema de arquivos em camadas (Layered File System) e os benefícios dessa abordagem principalmente para o download de novas imagens.
Imagens são Read-Only sempre (apenas para leitura)
Containers representam uma instância de uma imagem
Como imagens são Read-Only os containers criam nova camada (layer) para guardar as alterações
O comando Docker run e as possibilidades de execução de um container
Segue também uma breve lista dos comandos utilizados:

docker ps - exibe todos os containers em execução no momento.
docker ps -a - exibe todos os containers, independentemente de estarem em execução ou não.
docker run -it NOME_DA_IMAGEM - conecta o terminal que estamos utilizando com o do container.
docker start ID_CONTAINER - inicia o container com id em questão.
docker stop ID_CONTAINER - interrompe o container com id em questão.
docker start -a -i ID_CONTAINER - inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos.
docker rm ID_CONTAINER - remove o container com id em questão.
docker container prune - remove todos os containers que estão parados.
docker rmi NOME_DA_IMAGEM - remove a imagem passada como parâmetro.
docker run -d -P --name NOME dockersamples/static-site - ao executar, dá um nome ao container.
docker run -d -p 12345:80 dockersamples/static-site - define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.
docker run -d -P -e AUTHOR="Fulano" dockersamples/static-site - define uma variável de ambiente AUTHOR com o valor Fulano no container criado.


Para startar o docker com uma imagem do node e rodar o fonte:

docker run -d -p 8080:3000 -v "/home/kelvin/Fontes/Git/Alura/Docker/Docker - Criando containers sem dor de cabeça/volume-exemplo:/var/www" -w "/var/www" node npm start

ou

docker run -d -p 8080:3000 -v "$(pwd):/var/www" -w "/var/www" node npm start

Nessas aulas avançamos bastante e aprendemos:

Que Container são voláteis, isso é, ao remover um, removemos os dados juntos
Para deixar os dados persistente devemos usar Volumes
Que volumes salvos não ficam no container e sim no Docker Host
Como criar um ambiente de execução node.js
Segue também uma breve lista dos comandos utilizados:

docker run -v "[CAMINHO_VOLUME_LOCAL:]CAMINHO_VOLUME_CONTAINER" NOME_DA_IMAGEM - cria um volume no respectivo caminho do container, caso seja especificado um caminho local monta o volume local no volume do container.
docker inspect ID_CONTAINER - retorna diversas informações sobre o container.

Criando um Dockerfile
Para rodar o dockerfile:
docker build -f Dockerfile -t kelvin/node .

Subindo a imagem do Docker Hub
Comando:
docker login
*Adiciona o usuário e senha do dockerhub
Comando:
docker push kelvin/node
