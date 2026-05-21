# config_project

Como Instalar Back End

Nesta seção, você encontrará informações sobre como instalar algumas das ferramentas de desenvolvimento mais populares, incluindo Git, Docker Compose e Magento Cloud. Siga as páginas abaixo para obter instruções detalhadas sobre como instalá-las.

Instalação do Git

instalação do docker

Instalação do Docker Compose

Instalação do Magento Cloud

Criação De hosts

Preparando seu ambiente BE

Siga as etapas abaixo para criar seu ambiente, o docker já esta disponível no repositório Magento .docker:

Certifique-se de ter o Docker e o Docker Compose instalados em seu sistema.

Acesse o diretório raiz do seu projeto Magento.

Na pasta app/etc/, copie o arquivo env_docker.php para env.php 

cp app/etc/env_docker.php app/etc/env.php

 

Na raiz do projeto copie o arquivo .env.integration para .env 

cp .env.local .env

Para limpar a base instalada, basta limpar o conteúdo da pasta:  

sudo rm -r .docker/mysql/data/*

Se o processo for de reinstalação do ambiente, rode o comando para matar os volumes antigos do docker 

docker-compose down -v

Execute o seguinte comando para criar os containers:

docker-compose up


O Docker Compose lerá o arquivo docker-compose.yml e iniciará o contêiner de acordo com as configurações definidas no arquivo.

Isso poderá levar algum tempo se o data da base (.docker/mysql/data) estiver limpo (no local 2min), nesse processo a base de dados será instalada automaticamente.

Acesse o container da instalação:

docker-compose run --rm deploy bash 


depois rode o comando abaixo;

composer install 


Depois do primeiro, acesso, sempre use o comando abaixo para acessar e utilizar o cli do bin/magento.:

bin/magento-docker bash


Use este mesmo comando para acessar posteriormente todas as funções do cli do bin/magento

Depois rode. 

 bin/magento  setup:upgrade


Depois aplique os patches.

 vendor/bin/ece-patches apply


 rode o di compile

bin/magento setup:di:compile


Rode o reindex para indexar os produtos: 

bin/magento ind:rei

saia do docker ( digite exit) e gere o front end.


Para buildar todos: ./front_deploy.sh all
Para buildar o Atrial: ./front_deploy.sh atrial
Para buildar o Elfa: ./front_deploy.sh elfa
Para buildar o Surya: ./front_deploy.sh surya
Para buildar o Descarpack: ./front_deploy.sh descarpack
Para buildar o Salesforce: ./front_deploy.sh salesforce

altere o hosts conforme exemplificado aqui.

o http://https://local.suryadental/ na barra de endereço.

Para subir as imagens, deve primeiramente ser limpada a pasta media: 

sudo rm -r pub/media/*

Depois deve ser baixado o arquivo:  (arquivo deve ser gerado sempre que descer a base de prod para os ambientes de baixo)

E extraído pelo tar: 

tar -xvf {PATH_ONDE_FOI_BAIXADO}/media_integration.tar.gz pub/media/



