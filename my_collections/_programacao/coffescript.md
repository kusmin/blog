---
layout: post
comments: true
title: CoffeScript
date: 2021-05-31 6:00 AM
description: Uma forma mais simplificada de escrever em javaScript
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

* Não precisa declarar as variáveis, ele já faz isso para a gente;
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

Um pouco mais útil é o exemplo abaixo

    foods = ['broccoli', 'spinach', 'chocolate']
    eat food for food in foods 

JavaScript

    var food, foods, i, len;
    
    foods = ['broccoli', 'spinach', 'chocolate'];
    
    for (i = 0, len = foods.length; i < len; i++) {
      food = foods[i];
      eat(food);
    }

Ele usa a palavra reservada when para ifs dentro do for, por exemplo:

    foods = ['broccoli', 'spinach', 'chocolate']
    eat food for food in foods when food != 'chocolate'

JavaScript

    for (l = 0, len2 = foods.length; l < len2; l++) {
      food = foods[l];
      if (food !== 'chocolate') {
        eat(food);
      }
    }

Caso não seja chocolate o food vai atribuir a eat o valor food

Outro exemplo, seria

     list = ["Lucas","Renan", "Pedro"]
    console.log name for name in list when name == "Renan"

Vai percorrer toda a lista e imprimir no console o nome Renan, caso o tenha.

    var i, len, list, name;
    
    list = ["Lucas", "Renan", "Pedro"];
    
    for (i = 0, len = list.length; i < len; i++) {
      name = list[i];
      if (name === "Renan") {
        console.log(name);
      }
    }

Criando uma lista de 1 a 10 com o for

    list = (num for num in [1..10])

JavaScript

    var list, num;
    
    list = (function() {
      var i, results;
      results = [];
      for (num = i = 1; i <= 10; num = ++i) {
        results.push(num);
      }
      return results;
    })();

Tirando o numero 5 da lista

    list = (num for num in [1..10] when num isnt 5)

JavaScript

    var list, num;
    
    list = (function() {
      var i, results;
      results = [];
      for (num = i = 1; i <= 10; num = ++i) {
        if (num !== 5) {
          results.push(num);
        }
      }
      return results;
    })();

Para controlar o incremento dentro do for, utilize o by, por exemplo iterar todos os números pares exceto o valor 4:

    countdown = (num for num in [0..10] by 2 when num isnt 4)  

Resulta em 0, 2, 6, 8, 10

JavaScript

    var countdown, num;
    
    countdown = (function() {
      var i, results;
      results = [];
      for (num = i = 0; i <= 10; num = i += 2) {
        if (num !== 4) {
          results.push(num);
        }
      }
      return results;
    })();

Iteração sobre objetos é bem fácil, basta usar o of, como no exemplo a seguir:

    yearsOld = max: 10, ida: 9, tim: 11
    
    ages = for child, age of yearsOld
      "#{child} is #{age}"

JavaScript

    var age, ages, child, yearsOld;
    
    yearsOld = {
      max: 10,
      ida: 9,
      tim: 11
    };
    
    ages = (function() {
      var results;
      results = [];
      for (child in yearsOld) {
        age = yearsOld[child];
        results.push(`${child} is ${age}`);
      }
      return results;
    })();

E outro loop que o CoffeeScript possui é o while e o until que é como um while negado

     console.log "5 é maior que 4"  while 5 > 4
     console.log "negando que 5 maior que 4, não entra neste loop" until 5 > 4

JavaScript

    while (5 > 4) {
      console.log("5 é maior que 4");
    }
    
    while (!(5 > 4)) {
      console.log("negando que 5 maior que 4, não entra neste loop");
    }

Opção interessante utilizando o until é a seguinte

    x = 10
    until x < 4
      if x 7
        x - 2
      else
        x--

Enquanto x não for menor que 4 ou seja enquanto x for maior que 4 vai ficar dentro do loop

JavaScript

    var x;
    
    x = 10;
    
    while (!(x < 4)) {
      if (x(7)) {
        x - 2;
      } else {
        x--;
      }
    }

Podemos usar os intervalo para extrair partes de matrizes, Com dois pontos(3..6) o intervalo é inclusivo com (3, 4, 5, 6) com três pontos (3...6), o intervalo exclui o ultimo numero.

    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    inclusivo   = numbers[3..5] # 4, 5, 6
    
    exclusivo = numbers[3...5] # 4,5 
    
    todosOsNumero = number[..]
    
    incioAoFimInclusivo  = numbers[..5] #1, 2, 3, 4, 5, 6
    
    incioAoFimExclusivo  = numbers[...5] #1, 2, 3, 4, 5
    
    cortadoApartir = numbers[5...] # 6, 7, 8, 9
    
    cortadoApartir = numbers[5..] #6,7,8, 9

JavaScript

    var cortadoApartir, exclusivo, incioAoFimExclusivo, incioAoFimInclusivo, inclusivo, numbers, todosOsNumero;
    
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    
    inclusivo = numbers.slice(3, 6);
    
    exclusivo = numbers.slice(3, 5);
    
    todosOsNumero = number.slice(0);
    
    incioAoFimInclusivo = numbers.slice(0, 6);
    
    incioAoFimExclusivo = numbers.slice(0, 5);
    
    cortadoApartir = numbers.slice(5);
    
    cortadoApartir = numbers.slice(5);

Outra opção é interessante é usar como replace para substituir parte do array

    numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    numbers[3..6] = [-3, -4, -5, -6]

JavaScript

    var numbers, ref,
      splice = [].splice;
    
    numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
    
    splice.apply(numbers, [3, 4].concat(ref = [-3, -4, -5, -6])), ref;

Tudo em CoffeeScript é uma expressão, linguagem é baseada em expressão. Algumas coisas que seriam instruções em JavaScript são convertidas em expressões em CoffeeScript.

    alert(
      try
        if x ==5
            
        else  
          "Tamo ai"
      catch error
        "And the error is ... #{error}"
    )

A alguns comandos em JavaScript, entre eles break, continue e return que não podem ser convertidos dentros das expressões do CoffeeScript