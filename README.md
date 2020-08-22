![UML](img/LogotipoSlashicorp.png)

# Treinamento DevOps - Part II

VirtualBox:
```
Download: https://www.virtualbox.org/wiki/Downloads
Documentacão: https://www.virtualbox.org/wiki/Documentation
```

# Docker Wordpress

Ambiente Docker para desenvolvimento de Temas e Plugins Wordpress. Utilizando PHP-7.2, Mysql e PHPMyAdmin.

## Visão Geral

1. [Instalar Pré Requisitos](#pre-requisitos)

    Antes de executar o projeto, tenha certeza que os pré requisitos são atendidos.

2. [Clonar Projeto](#clonar-projeto)

    Baixe o código deste repositório no GitHub. 

3. [Rodar Projeto](#rodar-projeto)

    Com todos requisitos atendidos, aqui iniciamos o projeto.

___

## Pré Requisitos

Este projeto foi criado e testado no sistema operacional `MacOS Mojave 10.14`. Entretando pode funcionar normalmente no Windows e Linux.

Os requisitos abaixo devem estar disponíveis em seu sistema operacional:

* [Git](https://git-scm.com/downloads)
* [Docker](https://docs.docker.com/engine/installation/)
* [Docker Compose](https://docs.docker.com/compose/install/)

Confira se o `docker-compose` está instalado usando o comando abaixo: 

```sh
which docker-compose
```

Confira a compatibilidade do Docker Compose:

* [Referência do Docker Compose versão 3](https://docs.docker.com/compose/compose-file/)

### Imagens Usadas

* [Wordpress](https://hub.docker.com/_/wordpress/)
* [MySQL](https://hub.docker.com/_/mysql/)
* [PHPMyAdmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin/)

Este projeto funciona nas seguintes portas:

| Servidor   | Porta |
|------------|-------|
| MySQL      | 3306  |
| Wordpress  | 8000  |
| PHPMyAdmin | 8080  |



## Clonar Projeto

Com o [Git](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git) instalado, clone o projeto com o comando abaixo:

```sh
git clone https://github.com/hubslashicorp/treinamento-devops-part2.git
```

Acesse o diretório do projeto:

```sh
cd treinamento-devops-part2
```

### Estrutura do Projeto

```sh
.
├── data
│   └── mysql
├── etc
│   ├── mysql
│   │   └── Dockerfile
│   ├── phpmyadmin
│   │   └── Dockerfile
│   └── wordpress
│       └── Dockerfile
├── src
│   ├── plugins
│   ├── themes
│   └── uploads
├── .gitignore
├── docker-compose.yml
└── README.md
```

___

## Rodar Projeto

1. Iniciar aplicação:

    ```sh
    sudo docker-compose up -d # Roda a aplicação em background
    ```

    **Aguarde, pode demorar vários minutos.**

    ```sh
    sudo docker-compose logs -f # Imprime os logs da aplicação no terminal
    ```

2. Acesse no seu navegador:

    * [http://localhost](http://localhost/)
    * [http://localhost:8080](http://localhost:8080/) PHPMyAdmin (servidor: mysql, usuário: wordpress, senha: wordpress)

4. Parar e limpar serviços:

    ```sh
    sudo docker-compose down -v
    ```


## Step by Step:

| Item  | Descrição                                |
|-------|------------------------------------------|
|  1.0  |   [lab] Instalando Docker-machine        |
|  2.0  |   [lab] Instalando Docker-compose        |
|  3.0  |   Inspecionando Dockerfile               |
|  4.0  |   [lab] Provis. VM com Docker-machine    |
|  5.0  |   [lab] Principais comandos Docker-mach  |
|  5.1  |   Entendendo Dockerfile                  |
|  6.0  |   [lab] Construindo primeira imagem      |
|  6.1  |   [lab] Commitando imagem no docker hub  |


Mais uma vez, sinta-se à vontade para esclarecer duvidas com relação a instalação e tudo o mais
com seu instrutor.

att;

![UML](img/SlashiCorpSig.png)
