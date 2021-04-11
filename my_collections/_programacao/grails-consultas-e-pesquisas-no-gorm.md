---
layout: post
comments: true
title: 'Grails: consultas e pesquisas no GORM'
date: 2021-04-10 6:00 AM
description: introdução a como são feitos pesquisas dentro do Grails
imagem: "/uploads/gorm.jpeg"
categories: grails, gorm
published: false

---
Uma das funções mais interessantes dentro do framework do Grails são os tipos de pesquisas que podem ser realizadas utilizando o GORM e o Hibernate. Iremos entender como funciona cada uma desses tipos de pesquisa, que alias são quatro, sendo elas: find, criteria, where  e HQL.

<br>

### Find

<br>

Caso queiram acompanhar os mesmos exemplos aqui descritos, segue o link do repositório [https://github.com/kusmin/exemploPesquisaGrails](https://github.com/kusmin/exemploPesquisaGrails "https://github.com/kusmin/exemploPesquisaGrails")