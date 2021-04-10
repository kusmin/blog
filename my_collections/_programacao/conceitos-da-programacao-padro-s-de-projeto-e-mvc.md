---
layout: post
comments: true
title: 'Conceitos da programação: Padroẽs de projeto e MVC'
date: 2021-04-03 6:00 AM
description: Uma introdução aos padrões de projeto com foco no padrão MVC
imagem: "/uploads/padroes-de-projeto.jpeg"
categories: MVC, padrões de projeto

---
Padrões de projeto é um conceito muito utilizado na comunidade de programação, que as vezes pode confundir o programador iniciante, caso não tome conhecimento deste conceito.

<br>

### Introdução

<br>

Os padrões de projeto são soluções para problemas bem conhecidos dentro da programação, reaproveitando as soluções bem sucedidas em futuros projetos, assim maximizando a produtividade do programador e evitando uma serie de erros que já foram solucionados pelo padrão escolhido.

<br>

O termo padrões de projeto ganhou notoriedade com o livro “Padrões de Projeto – Soluções reutilizáveis de software orientado a objetos. ” Em que são catalogados 23 tipos de padrões cada um deles responsável por solucionar um problema conhecido, dentro do seu contexto, e as vantagens e desvantagens da utilização deste padrão, dividindo-os em 3 categorias: padrões de criação, estruturais, e de comportamento.

<br>

### Vantagens e desvantagens

<br>

A utilização de um padrão de projeto traz diversas vantagens para aqueles que adotam, entre eles podemos citar:

1. Soluções já comprovadas para problemas conhecidos.
2. Facilita a comunicação entre aqueles que fazem a parte do projeto e a manutenção do projeto, uma vez que todos falam a mesma 'língua' ou mesmo padrão.
3. Cria códigos mais legíveis e com boas praticas.
4. Possibilita a reutilização do código em toda a aplicação (conceito DRY - em português "Não se repita"), evitando assim erros por códigos replicados, o famoso Ctrl + c, Ctrl + v.
5. Facilita a criação de códigos de teste, que é uma boa pratica, teste seus códigos !

<br>

Essas são algumas das vantagens de se adotar um padrão de projeto, mas como tudo na vida, nem tudo são flores e aqui vai algumas das desvantagens:

1. Uma curva de aprendizado maior até que você consiga aprender sobre a utilização correta do padrão, mas uma vez aprendida a uma economia no tempo de trabalho.
2. Muita complexidade para atingir um objetivo simples, muitas vezes não a necessidade de se usar todo um padrão de projeto para problemas simples. As vezes você esta usando todo um framework com varias funcionalidades para simplesmente imprimir algo na tela, é como utilizar uma bomba atômica para explodir um formigueiro.
3. Se não utilizado da maneira correta, traz mais problemas que solução, principalmente na manutenção.

<br>

### Sobre o padrão MVC

<br>

![](/uploads/mvc.jpeg)

<br>

Como pode ser visto pela foto acima o padrão MVC, separa sua aplicação em três camadas. A camada de interação do usuário (view), a camada de manipulação de dados (model) e a camada de controle (controller).

<br>

Na camada do Model,que é a camada mais preciosa do projeto, onde fica as nossas classes de domínio, a ligação com o banco de dados e toda a logica de serviços da aplicação.

<br>

Depois temos a camada mais externa a View, que é nada mais que é tudo aquilo que aparece na tela do usuário, a parte visual da aplicação.

<br>

Por ultimo temos a parte dos Controllers, aqui é onde é feito a ligação entre a parte da View e do Model. _Um detalhe importante_ é que o Model não conhece a  View, muito menos a View conhece a Model, o que traz algumas vantagens interessantes, como por exemplo maior segurança dos dados e a possibilidade de ter diferentes Views para uma mesma aplicação (APIs por exemplo). 

<br>

O Controller basicamente funciona como um carteiro levando, por exemplo _request_ da View e devolvendo _response_ da camada Model. Responsável por toda essa comunicação entre as diferentes partes da aplicação, é o único que tem conhecimento das três partes do MVC.

<br>

### Conclusão

<br>

Neste post foi dado uma introdução sobre os padrões de projeto e um pontapé inicial sobre um padrão de exemplo no caso o MVC. Antes de utilizar qualquer padrão é necessário estudar a real utilidade daquele padrão naquele contexto, pesando suas vantagens e desvantagens.

<br>

### **Bibliografia**

<br>

1. `Padrões de Projeto Soluções Reutilizáveis de Software orientado a objetos.
   Erick Gamma, Richard Helm, John Vlissides e Ralph Johnson.`
2. Playlist no youtube: Padrões de Projeto (Design Patterns - GoF) - Otávio Miranda

   [https://www.youtube.com/watch?v=MqddY6Ochkc&list=PLbIBj8vQhvm0VY5YrMrafWaQY2EnJ3j8H](https://www.youtube.com/watch?v=MqddY6Ochkc&list=PLbIBj8vQhvm0VY5YrMrafWaQY2EnJ3j8H "https://www.youtube.com/watch?v=MqddY6Ochkc&list=PLbIBj8vQhvm0VY5YrMrafWaQY2EnJ3j8H")