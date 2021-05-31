---
layout: post
comments: true
title: CoffeScript
date: 2021-05-31 6:00 AM
description: Uma forma mais simples de escrever javaScript
imagem: "/uploads/cofeescript.png"
categories: CofeeScript
published: false

---

Parecido com as arrows-functions de javaScript.

Nas funções por padrão retorna como valor o ultimo comando.

Por exemplo, o comando em coffeeScript abaixo:

    fill = (container, liquid = "coffee", x) ->
      "Filling the #{container} with #{liquid}..."
      x

Tem a mesma função que o comando em JavaScript a seguir:

    var fill;
    
    fill = function(container, liquid = "coffee", x) {
      `Filling the ${container} with ${liquid}...`;
      return x;
    };

Se quisesse retornar a string teria que alterar a função para: 

    fill = (container, liquid = "coffee", x) ->
      valorCafe = x * x
      "Filling the #{container} with #{liquid}..."
      

Equivalente a função:

    var fill;
    
    fill = function(container, liquid = "coffee", x) {
      var valorCafe;
      valorCafe = x * x;
      return `Filling the ${container} with ${liquid}...`;
    };

Detalhe **importante,** cuidado com a endentação, ele não tem ponto e virgula e usa uma sintaxe parecida com a do python, por exemplo, se tirarmos a endentação da ultima linha ali:

    fill = (container, liquid = "coffee", x) ->
      valorCafe = x * x
     "Filling the #{container} with #{liquid}..."

O resultado seria esse:

    var fill;
    
    fill = function(container, liquid = "coffee", x) {
      var valorCafe;
      return valorCafe = x * x;
    };
    
    `Filling the ${container} with ${liquid}...`;

Mais alguns detalhes:

*  Não precisa declarar as variáveis, ele já faz isso para a gente;
* Ao passar variáveis(interpolação de strings) para a String usar a sintaxe #{};
* Chamar a função é bem simples:

    fill "cafe",35

No caso das Strings, quando são multi-linhas, ele ignora endentação, a não ser no caso que coloque uma barra invertida, nesse caso ele emenda o final de uma linha com o inicio da outra, segue os exemplos.

String multilinha normal:

    mobyDick = "Call me Ishmael. Some years ago --
      never mind how long precisely -- having little
      or no money in my purse, and nothing particular
      to interest me on shore, I thought I would sail
      about a little and see the watery part of the
      world..."

Resultado em javaScript:

    var mobyDick;
    
    mobyDick = "Call me Ishmael. Some years ago -- never mind how long precisely -- having little or no money in my purse, and nothing particular to interest me on shore, I thought I would sail about a little and see the watery part of the world...";
    

String multilinha com a barra invertida no final:

    mobyDick = "Call me Ishmael. Some years ago --\
      never mind how long precisely -- having little\
      or no money in my purse, and nothing particular\
      to interest me on shore, I thought I would sail\
      about a little and see the watery part of the\
      world..."

Resultado em javaScript:

    var mobyDick;
    
    mobyDick = "Call me Ishmael. Some years ago --never mind how long precisely -- having littleor no money in my purse, and nothing particularto interest me on shore, I thought I would sailabout a little and see the watery part of theworld...";

Caso queria uma String que contenha texto formatado ou que tenha sensibilidade a endentação, use """ ou '''. 

CoffeeScript

    html = """
           <strong>
             bora estudar
           </strong>
           """

JavaScript

    var html;
    
    html = `<strong>
      bora estudar
    </strong>`;

Listas e arrays são bem simples com o CoffeeScript, mas uma vez detalhe na endentação, que é similar com o YAML, como pode ser visto no exemplo: