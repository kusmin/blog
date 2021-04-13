---
layout: post
comments: true
title: 'Grails: consultas e pesquisas no GORM'
date: 2021-04-13 12:00 PM
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

Nosso sistema é bem simples composto de três classes de domínio, pessoa, tipo de pessoa e trabalho, elas podem ser encontradas dentro da pasta grails-app/domain. Vamos começar colocando alguns dados no banco de dados, você pode colocar direto pela aplicação ou pelo próprio console, aqui vamos ver como colocar pelo console...

> import exemplo.buscar.*
>
> def pessoa = new Pessoa(nome: "Pedro", identidade: "948924892")

<br>

Com duas simples você inseriu seu primeiro registro no banco de dados. O 'import' é para importamos a aplicação para o console, a partir de agora, não voltarei a repita-la nos exemplos. Vamos utilizar um método de busca para encontra-lo:

<br>

> def pessoa = Pessoa.get(1)

<br>

Você deve ver na sua tela, algo igual a imagem a seguir![](/uploads/captura-de-tela-de-2021-04-12-21-57-53.png)

Mostrando o nome que inserimos na posição um do banco de dados, podemos modificar o registro pelo método get também. Acrescentando o seguinte comando ao código...

> pessoa.nome = "Renan"

<br>

O registro que antes era "Pedro", foi alterado para "Renan", iremos utilizar agora outro método de pesquisa para visualizar essa alteração.

> def pessoa =  Pessoa.read(1)

<br>

![](/uploads/captura-de-tela-de-2021-04-12-22-04-30.png)![](/uploads/captura-de-tela-de-2021-04-12-22-05-17.png)

Vóila ! Agora podemos visualizar o registro com o nome "Renan", através do método read. Vamos troca-lo novamente ...

> def pessoa = Pessoa.read(1)
>
> pessoa.nome = "Lucas"

<br>

![](/uploads/captura-de-tela-de-2021-04-12-22-07-51.png)![](/uploads/captura-de-tela-de-2021-04-12-22-08-46.png)

Vamos pesquisar novamente o registro...

> def pessoa = Pessoa.read(1)

E vejam só...

![](/uploads/captura-de-tela-de-2021-04-12-22-13-00.png)

O nome não foi alterado, vamos entender melhor o que aconteceu. O GORM usa por trás dos panos o Hibernate, e este por sua vez se utiliza de algumas convenções e comportamentos padrão, o primeiro deles, é sobre a sessão. Ao terminar uma sessão o Hibernate, persiste todos os objetos que estiverem em memoria, ele se utiliza da _detecção de sujeira_ para verificar quais dados foram alterados e assim que termina a sessão, estes dados alterados são persistidos no banco de dados. É uma convenção que visa a economizar dados computacionais, uma vez que é a persistência  um processo caro, junta o máximo possível de dados para serem salvos juntos. 

Nos exemplos que vimos o método get tem por padrão a detecção de sujeito ativa e o read não, podemos visualizar este comportamento utilizando o método **isDirty()**, que nós mostra se a detecção esta ativa ou não, vamos aos exemplos.

![](/uploads/captura-de-tela-de-2021-04-13-07-37-42.png)

Como pode ver pelo este exemplo, quando chamamos o método isDirty() no primeiro caso, sem nenhuma modificação foi retornado como falso, pois ainda nada havia sido alterado, entretanto quando o nome foi alterado o Hibernate detectou esta alteração e nos retornou como verdadeiro.