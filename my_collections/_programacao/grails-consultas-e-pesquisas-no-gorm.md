---
layout: post
comments: true
title: 'Grails: consultas e pesquisas no GORM'
date: 2021-04-10 6:00 AM
description: introdução a como são feitas pesquisas dentro do Grails
imagem: "/uploads/gorm.jpeg"
categories: grails, gorm
published: false

---
Uma das funções mais interessantes dentro do framework do Grails são os tipos de pesquisas que podem ser realizadas utilizando o GORM e o Hibernate. Iremos entender como funciona cada uma desses tipos de pesquisa, que alias são quatro, sendo elas: find, criteria, where  e HQL.

<br>

### Antes de começar ...

<br>

Caso queiram acompanhar os mesmos exemplos aqui descritos, segue o link do repositório [https://github.com/kusmin/exemploPesquisaGrails](https://github.com/kusmin/exemploPesquisaGrails "https://github.com/kusmin/exemploPesquisaGrails"),depois de clonar a aplicação, coloque para rodar o banco de dados que esta na pasta docker:

<br>

    cd docker/

    docker-compose down && docker-compose build & docker-compose up

<br>

O primeiro comando é para entrar na pasta docker, caso já esteja na pasta da aplicação, o segundo sobe a imagem mysql que esta dentro do docker, caso ainda não conheça esta ferramenta maravilhosa que é o docker recomendo que visitem o site [https://docs.docker.com/](https://docs.docker.com/ "https://docs.docker.com/").

<br>

Depois de rodar o docker vamos colocar para rodar a aplicação, dentro da pasta raiz do projeto execute o comando:

<br>

    ./grailsw

<br>

Este comando é um binário que vai baixar  as dependências do grails . Observação: é necessário ter o java 7 ou mais recente instalado, recomendo que utilizem o [SDKman](https://sdkman.io/ "https://sdkman.io/") para este controle de versões do java, e de outras ferramentas do mundo JVM como o próprio grails.

<br>

Depois de baixar as dependências você vai estar dentro da aplicação, para roda-la basta executar:

<br>

    run-app

<br>

Que a aplicação vai estar rodando na porta 8080, no nosso caso vamos reproduzir os exemplo diretamente pelo console do Groovy, que foi esta presente dentro do grails.

    console

<br>

![](/uploads/captura-de-tela-de-2021-04-11-10-51-20.png)

<br>

Abrindo a janela do console particular do grails, agora sim vamos começar a brincar com as nossas buscar.

### Find

<br>

No sistema é bem simples composto de três classes de domínio, pessoa, tipo de pessoa e trabalho, elas podem ser encontradas dentro da pasta grails-app/domain.