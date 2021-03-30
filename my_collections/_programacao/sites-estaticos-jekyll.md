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

Sua primeira aplicação em Jekyll estará rodando na porta [http://localhost:4000](http://localhost:4000/), basta abri-la em um navegador