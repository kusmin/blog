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

CoffeeScript

    criancas =
      menino:
        nome: "Pedro"
        anos:  11
      menina:
        nome: "Maria"
        age:  9

JavaScript

    criancas = {
      menino: {
        nome: "Pedro",
        anos: 11
      },
      menina: {
        nome: "Maria",
        age: 9
      }
    };

No caso as virgulas ficam sendo opcionais e as chaves {} são definidas pela endentação.

Comentários de uma só linha são definidos pelo #, caso seja comentário de bloco utilizar ###.

    ###
    Fortune Cookie Reader v1.0
    Released under the MIT License
    ###
    
    riqueza = (dinheiro) ->
      console.log dinheiro # estou rico!

Mais sobre as declarações de variáveis, como dito antes o CoffeeScript, declara automaticamente as variáveis com var, não sendo possível declaração explicita, não podendo utilizar os nomes let, const ou var explicitamente(todas as variáveis são declaradas como tipo var implicitamente). Assim toma o cuidado quando o escopo das variáveis, entre global e local. No exemplo a seguir o resultado da variável inner global vai ser igual a 10 diferente do seu valor local dentro da função: 

    outer = 1
    changeNumbers = ->
      inner = -1
      outer = 10
    inner = changeNumbers()

Resultado em JavaScript

    var changeNumbers, inner, outer;
    
    outer = 1;
    
    changeNumbers = function() {
      var inner;
      inner = -1;
      return outer = 10;
    };
    
    inner = changeNumbers();

 Assim como nas funções as instruções if e else e delimitações de bloco são feitas por endentação, sem precisar de parenteses ou chaves.

Não existe operador ternario explicito em Coffee, caso precise de um, utilize um if na mesma linha junto com um then e else.

    mood = greatlyImproved if singing
    
    if happy and knowsIt
      clapsHands()
      chaChaCha()
    else
      showIt()
    
    date = if friday then sue else jill

Resultado em JavaScript

    var date, mood;
    
    if (singing) {
      mood = greatlyImproved;
    }
    
    if (happy && knowsIt) {
      clapsHands();
      chaChaCha();
    } else {
      showIt();
    }
    
    date = friday ? sue : jill;

Uma opção interessante que a linguagem oferece é o unless(muito utilizado no ruby), onde diferente do if que valida enquanto for verdadeiro, o unless valida enquanto for falso ele entra no bloco.

    x = 5
    
    unless x == 5
      console.log y = 10
    else
      console.log y = 12 

Resultado em JavaScript

    var x, y;
    
    x = 5;
    
    if (x !== 5) {
      console.log(y = 10);
    } else {
      console.log(y = 12);
    }

Outro exemplo

    x = 5
    
    unless x == 5
      console.log "diferente de 5"
    else unless x != 6
      console.log "igual a 6"
    else
      console.log "outro"  
    

JavaScript

    var x;
    
    x = 5;
    
    if (x !== 5) {
      console.log("diferente de 5");
    } else if (x === 6) {
      console.log("igual a 6");
    } else {
      console.log("outro");
    }

O mode de propriedades de objetos é ainda mais simples que no JavaScript.

    user =
      name: 'Werner Heisenberg'
      occupation: 'theoretical physicist'
      age: 28
      ativo: true
    
    currentUser = { user..., status: 'incerto' }

JavaScript

    var currentUser, user;
    
    user = {
      name: 'Werner Heisenberg',
      occupation: 'theoretical physicist',
      age: 28,
      ativo: true
    };
    
    currentUser = {
      ...user,
      status: 'incerto'
    };

Splats em coffeeScript são parecidos com o de Java Script a diferença é que os 3 pontos (...) vão depois 

    gold = silver = rest = "unknown"
    
    awardMedals = (first, second, others...) ->
      gold   = first
      silver = second
      rest   = others
    
    contenders = [
      "Michael Phelps"
      "Liu Xiang"
      "Yao Ming"
      "Allyson Felix"
      "Shawn Johnson"
      "Roman Sebrle"
      "Guo Jingjing"
      "Tyson Gay"
      "Asafa Powell"
      "Usain Bolt"
    ]
    
    awardMedals contenders...
    
    alert """
    Gold: #{gold}
    Silver: #{silver}
    The Field: #{rest.join ', '}
    """

JavaScript

    var awardMedals, contenders, gold, rest, silver;
    
    gold = silver = rest = "unknown";
    
    awardMedals = function(first, second, ...others) {
      gold = first;
      silver = second;
      return rest = others;
    };
    
    contenders = ["Michael Phelps", "Liu Xiang", "Yao Ming", "Allyson Felix", "Shawn Johnson", "Roman Sebrle", "Guo Jingjing", "Tyson Gay", "Asafa Powell", "Usain Bolt"];
    
    awardMedals(...contenders);
    
    alert(`Gold: ${gold}
    Silver: ${silver}
    The Field: ${rest.join(', ')}`);

O loop for do CoffeeScript não é tão intuitivo em um primeiro momento, o próximo exemplo é bem simples.

    courses = ['greens', 'caviar', 'truffles', 'roast', 'cake']
    
    estudo for estudo, i in courses 

basicamente a cada loop dentro do array, ele muda o valor da variável estudo de acordo com o índice.

JavaScript

    var courses, estudo, i, j, len;
    
    courses = ['greens', 'caviar', 'truffles', 'roast', 'cake'];
    
    for (i = 0 ; i < courses.length; ++i) {
      estudo = courses[i];
      estudo;
    }