---
layout: post
title: 'Sites estáticos: Introdução ao Jekyll'
date: 2021-03-29 6:00 AM
description: 'Neste post vamos ter um primeiro contato com o Jekyll, uma excelente
  ferramenta para a criação de sites estáticos. '
imagem: "/uploads/jekyll.png"
categories: Jekyll
published: false

---
O Jekyll é um gerador de sites estáticos desenvolvido em cima da linguagem ruby, se você tiver um conhecimento sobre o funcionamento da linguagem esse tutorial vai ser bem simples, caso não tenha, não se preocupe vai ser igualmente simples. Ele tem uma integração natural com o github pages o que lhe torna uma ótima  opção para a criação do seu primeiro site.

<br>

Este post foi baseado na documentação fornecida pelo próprio Jekyll recomendo a leitura do mesmo para a criação do seu site: [https://jekyllrb.com/](https://jekyllrb.com/ "https://jekyllrb.com/").

<br>

### Instalação

<br>

Antes de instalar o Jekyll é necessário que tenham instalados na sua  maquina a versão 2.4 do Ruby ou superior, para instalar no linux basca seguir o comando a seguir:

    sudo apt-get install ruby-full build-essential zlib1g-dev

**Dica**:  caso utilize outras versões do Ruby ou deseja um controle maior sobre as versões instaladas é recomendável alguma ferramenta de controle de versão, no meu caso utilizo o RVM, que é uma ferramenta bem simples e que ajuda bastante quando tem vários projetos Ruby em versões diferentes, para maiores informações acessem o [https://rvm.io/](https://rvm.io/ "https://rvm.io/").

<br>

Depois de instalados os pre-requisitos, vamos instalar o Jekyll propriamente dito:

    gem install jekyll bundler

Instalado, vamos criar e rodar a aplicação básica, vá para uma pasta de sua preferencia e rode: 

    Jekyll new nome-da-sua-aplicação
    cd nome-da-sua-aplicacao
    bundle exec jekyll serve

Sua primeira aplicação em Jekyll estará rodando na porta [http://localhost:4000](http://localhost:4000/), basta abri-la em um navegador, e você vera a tela inicial do jekyll bem parecida com esta:

![](/uploads/captura-de-tela-de-2021-03-30-17-44-34.png)

Pronto, sua primeira aplicação em Jekyll esta rodando, este é um pequeno passo rumo a criação do seu blog.

### Alerta

<br>

As versões mais novas do Ruby(depois da versão 3.0.0) não tem a dependência do 'webrick' instalando por padrão, isto pode resultar no erro da imagem a seguir ao executar sua aplicação.

![](/uploads/captura-de-tela-de-2021-03-30-17-40-30.png)

<br>

felizmente é um erro fácil de corrigir, bastando adicionar essa dependência manualmente dentro da aplicação

    bundle add webrick

Depois de instalada a dependência pode correr normalmente que o erro não mais acontecera, isto acontece devido que desde a versão 3.0.0 do Ruby esta dependência não veem por padrão dentro do Jekyll. Para maiores informações, consulte o link [https://github.com/jekyll/jekyll/issues/8523](https://github.com/jekyll/jekyll/issues/8523 "https://github.com/jekyll/jekyll/issues/8523").

### Bibliografia

1. 