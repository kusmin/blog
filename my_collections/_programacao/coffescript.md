---
layout: post
comments: true
title: CoffeScript
date: 2021-05-31 6:00 AM
description: Uma forma mais simplificada de escrever em javaScript
imagem: "/uploads/cofeescript.png"
categories: CoffeeScript
published: false

---
CoffeeScript é uma mistura de Python com Ruby, usado para compilar JavaScript.

Escrita parecida com as arrows-functions de javaScript, porem compilam funções normais para compilar uma arrow-function tem que utilizar a =>

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

A alguns comandos em JavaScript, entre eles break, continue e return que não podem ser convertidos dentro das expressões do CoffeeScript.

Algumas conversões boas interessantes dentro do CooffeeScript, ele compila o operador == em ===, assim como is também é compilado para ===, e o operador  !== em !==, assim como isnt também para !==

    if x is 5
       break  
    else if x isnt 10
       "Tamo ai"
    
    
    if x == 5
      break  
    else if x != 10
      "Tamo ai"

Compilam a mesma coisa em JavaScript

    if (x === 5) {
      break;
    } else if (x !== 10) {
      "Tamo ai";
    }

O not tem o mesmo valor que o !(negado).

Pode usar para lógica  and que é igual ao && e or para ||

    if x == 5 or x isnt 7
      break  
    else if x not 10 and y is 5
      "Tamo ai"

JavaScript

    if (x === 5 || x !== 7) {
      break;
    } else if (x(!10 && y === 5)) {
      "Tamo ai";
    }

Then pode ser usado para separar condições nas expressões, nas instruções while, if/else e switch/when. Then funciona "quase" como um ternário

    if name == "Renan" then sue else jill
    
    if (name === "Renan") {
      sue;
    } else {
      jill;
    }

Para boolenos além do true e do false, temos as opções on e yes para verdadeiro, e off e no para false.

    x = no
    y = off
    
    z= on
    m= yes
    
    var m, x, y, z;
    
    x = false;
    
    y = false;
    
    z = true;
    
    m = true;

Em arrays utilizamos o in e em objetos o of especialmente para iterar sobre eles.

    yearsOld = max: 10, ida: 9, tim: 11
    
    ages = for child, age of yearsOld
      "#{child} is #{age}"

Iterando sobre o objeto yearsOld

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

Sutil diferença utilizando o in, agora ele itera sobre o array

    yearsOld = max: 10, ida: 9, tim: 11
    
    ages = for child, age in yearsOld
      "#{child} is #{age}"
    
    var age, ages, child, yearsOld;
    
    yearsOld = {
      max: 10,
      ida: 9,
      tim: 11
    };
    
    ages = (function() {
      var i, len, results;
      results = [];
      for (age = i = 0, len = yearsOld.length; i < len; age = ++i) {
        child = yearsOld[age];
        results.push(`${child} is ${age}`);
      }
      return results;
    })();

Para expressões matemáticas temos o ** para exponenciação e // realiza divisão sem resto, para divisão normal utilizar /. O % resto da divisão funciona exatamente como em JavaScript e temos o %% que retorna o resto da divisão em modulo.

    -7 % 5 == -2 # The remainder of 7 / 5
    -7 %% 5 == 3 # n %% 5 is always between 0 and 4
    
    tabs.selectTabAtIndex((tabs.currentIndex - count) %% tabs.length)
    
    x = 8**8
    z = 64//8
    m = 64/8
    
    var m, x, z,
      modulo = function(a, b) { return (+a % (b = +b) + b) % b; };
    
    -7 % 5 === -2; // The remainder of 7 / 5
    
    modulo(-7, 5) === 3; // n %% 5 is always between 0 and 4
    
    tabs.selectTabAtIndex(modulo(tabs.currentIndex - count, tabs.length));
    
    x = 8 ** 8;
    
    z = Math.floor(64 / 8);
    
    m = 64 / 8;

Tabela resumo

| CoffeeScript | JavaScript |
| --- | --- |
| is | === |
| isnt | !== |
| not | ! |
| and | && |
| or | \|\| |
| true, yes,on | true |
| false, no,off | false |
| @, this | this |
| a in b | \[\].indexOf.call(b, a) >= 0 |
| a of b | a in b |
| for a from b | for (a of b) |
| a ** b | a ** b |
| a // b | Math.floor(a / b) |
| a %% b | (a % b + b) % b |

Alguns exemplos

    launch() if ignition is on
    
    volume = 10 if band isnt SpinalTap
    
    letTheWildRumpusBegin() unless answer is no
    
    if car.speed < limit then accelerate()
    
    winner = yes if pick in [47, 92, 13]
    
    print inspect "My name is #{@name}"
    
    var volume, winner;
    
    if (ignition === true) {
      launch();
    }
    
    if (band !== SpinalTap) {
      volume = 10;
    }
    
    if (answer !== false) {
      letTheWildRumpusBegin();
    }
    
    if (car.speed < limit) {
      accelerate();
    }
    
    if (pick === 47 || pick === 92 || pick === 13) {
      winner = true;
    }
    
    print(inspect(`My name is ${this.name}`));

Em CoffeeScript o operados ? retorna verdadeiro quando não é null, undefined ou não foi declarado, análogo ao nil? em Ruby.

    x = null
    x ?= caro
    
    var x;
    
    x = null;
    
    if (x == null) {
      x = caro;
    }

Verifica se a variável x é nula se for atribui o valor de caro.

    bom
    cafe = bom ? ruim
    
    bom;
    var cafe;
    
    cafe = typeof bom !== "undefined" && bom !== null ? bom : ruim;

O CoffeeScript é inteligente o suficiente para perceber se a variável esta no escopo ou não.

    major = 'Computer Science'
    
    if major?
      signUpForClass 'Introduction to Wines'
    
    var major;
    
    major = 'Computer Science';
    
    if (major != null) {
      signUpForClass('Introduction to Wines');
    }

Faz uma verificação completa se a variavel foi declarada ou não.

    unless window?
      environment = 'browser (probably)'

    var environment;
    
    if (typeof window === "undefined" || window === null) {
      environment = 'browser (probably)';
    }

Além disso o operador ? pode ser utilizado junto com o operador . semelhante ao que utilizado em Groovy para verificar referencias null ou undefined. Neste caso se todas as propriedades da cadeia que for verificada existirem vai ser obtido o resultado esperado caso contrario ele era retornar o undefined em vez do TypeError.

    zip = lottery.drawWinner?().address?.zipcode

    var ref, zip;
    
    zip = typeof lottery.drawWinner === "function" ? (ref = lottery.drawWinner().address) != null ? ref.zipcode : void 0 : void 0;

| Exemplo | Definição |
| --- | --- |
| a? | testes que aestão no escopo ea != null |
| a ? b | retorna ase aestá no escopo e a != null; por outro lado,b |
| a?.b ou a?\['b'\] | retorna a.bse aestá no escopo e a != null; por outro lado,undefined |
| a?(b, c) ou a? b, c | retorna o resultado da chamada a(com argumentos be c) se aestiver no escopo e puder ser chamado ; por outro lado,undefined |
| a ?= b | atribui o valor de bpara aif anão está no escopo ou if a == null; produz o novo valor dea |

Encadeamento de funções.

    $ 'body'
    .click (e) ->
      $ '.box'
      .fadeIn 'fast'
      .addClass 'show'
    .css 'background', 'white'

    $('body').click(function(e) {
      return $('.box').fadeIn('fast').addClass('show');
    }).css('background', 'white');
    

Assim como o JavaScript o CoffeeScript tem sintaxe de atribuição de desestruturação.  Quando atribui uma matriz ou literal de um objeto a um valor, ele se divide em dois, atribuindo os valores a direita, as variáveis a esquerda. Um caso simples é de atribuição paralela.

    theBait   = 1000
    theSwitch = 0
    
    [theBait, theSwitch] = [theSwitch, theBait]

    var theBait, theSwitch;
    
    theBait = 1000;
    
    theSwitch = 0;
    
    [theBait, theSwitch] = [theSwitch, theBait];

Nesse caso se printar o valor de TheBait obteríamos o valor de 0 e TheSwitch o valor de 1000.

Ou mesmo poderíamos fazer uma atribuição múltipla por função.

    weatherReport = (location) ->
      # Make an Ajax request to fetch the weather...
      [location, 72, "BH"]
    
    [city, temp, forecast] = weatherReport "Berkeley, CA"

    var city, forecast, temp, weatherReport;
    
    weatherReport = function(location) {
      // Make an Ajax request to fetch the weather...
      return [location, 72, "BH"];
    };
    
    [city, temp, forecast] = weatherReport("Berkeley, CA");

A desestruturação pode ser usada em qualquer profundidade de array ou aninhamento de objetos para ajudar a extrair propriedades.

    futurists =
      sculptor: "Umberto Boccioni"
      painter:  "Vladimir Burliuk"
      poet:
        name:   "F.T. Marinetti"
        address: [
          "Via Roma 42R"
          "Bellagio, Italy 22021"
        ]
    
    {sculptor} = futurists
    
    {poet: {name, address: [city, street]}} = futurists

    var city, futurists, name, sculptor, street;
    
    futurists = {
      sculptor: "Umberto Boccioni",
      painter: "Vladimir Burliuk",
      poet: {
        name: "F.T. Marinetti",
        address: ["Via Roma 42R", "Bellagio, Italy 22021"]
      }
    };
    
    ({sculptor} = futurists);
    
    ({
      poet: {
        name,
        address: [city, street]
      }
    } = futurists);

Desestruturação é útil na hora criar objetos por construtores, passando as propriedades de forma mais simples.

    class Person
      constructor: (options) ->
        {@name, @age, @height = 'average'} = options
    
    tim = new Person name: 'Tim', age: 4

    var Person, tim;
    
    Person = class Person {
      constructor(options) {
        ({name: this.name, age: this.age, height: this.height = 'average'} = options);
      }
    
    };
    
    tim = new Person({
      name: 'Tim',
      age: 4
    });

JavaScript tem o problema do escopo da função this a um tempo dentro da linguagem, com a função seta(=>), pode ser usada para vincular ao valor atual do this. Isto especialmente útil ao utilizar bibliotecas, baseadas em callback como JQuery.

    Account = (customer, cart) ->
      @customer = customer
      @cart = cart
    
      $('.shopping_cart').on 'click', (event) =>
        @customer.purchase @cart

    var Account;
    
    Account = function(customer, cart) {
      this.customer = customer;
      this.cart = cart;
      return $('.shopping_cart').on('click', (event) => {
        return this.customer.purchase(this.cart);
      });
    };

Se tivesse sido usado a -> na chamada acima @customer teria se referido a uma propriedade indefinida "customer" dentro do escopo e tentar chama-la pelo purchase geraria uma exceção. 

obs: Outra palavra reservada dentro do CoffeeScript é a palavra loop que simplesmente gera em JavaScript um while(true)

    loop
      x++

    while (true) {
      x++;
    }

Por padrão o CoffeeScript não tem uma função geradora function*(){}, bastando utilizar o yield que vira uma função geradora.

    perfectSquares = ->
      num = 0
      loop
        num += 1
        yield num * num
      return
    
    window.ps or= perfectSquares()

    var perfectSquares;
    
    perfectSquares = function*() {
      var num;
      num = 0;
      while (true) {
        num += 1;
        yield num * num;
      }
    };
    
    window.ps || (window.ps = perfectSquares());

    fibonacci = ->
      [previous, current] = [1, 1]
      loop
        [previous, current] = [current, previous + current]
        yield current
      return
    
    getFibonacciNumbers = (length) ->
      results = [1]
      for n from fibonacci()
        results.push n
        break if results.length is length
      results

    var fibonacci, getFibonacciNumbers;
    
    fibonacci = function*() {
      var current, previous;
      [previous, current] = [1, 1];
      while (true) {
        [previous, current] = [current, previous + current];
        yield current;
      }
    };
    
    getFibonacciNumbers = function(length) {
      var n, ref, results;
      results = [1];
      ref = fibonacci();
      for (n of ref) {
        results.push(n);
        if (results.length === length) {
          break;
        }
      }
      return results;
    };

Assim como acontece com o yield na uma função assíncrona especifica, uma função assíncrona é uma que simplesmente tem o await 

    # Your browser must support async/await and speech synthesis
    # to run this example.
    
    sleep = (ms) ->
      new Promise (resolve) ->
        window.setTimeout resolve, ms
    
    say = (text) ->
      window.speechSynthesis.cancel()
      window.speechSynthesis.speak new SpeechSynthesisUtterance text
    
    countdown = (seconds) ->
      for i in [seconds..1]
        say i
        await sleep 1000 # wait one second
      say "Brasil!"
    
    countdown 3

    // Your browser must support async/await and speech synthesis
    // to run this example.
    var countdown, say, sleep;
    
    sleep = function(ms) {
      return new Promise(function(resolve) {
        return window.setTimeout(resolve, ms);
      });
    };
    
    say = function(text) {
      window.speechSynthesis.cancel();
      return window.speechSynthesis.speak(new SpeechSynthesisUtterance(text));
    };
    
    countdown = async function(seconds) {
      var i, j, ref;
      for (i = j = ref = seconds; (ref <= 1 ? j <= 1 : j >= 1); i = ref <= 1 ? ++j : --j) {
        say(i);
        await sleep(1000); // wait one second
      }
      return say("Brasil!");
    };
    
    countdown(3);

Classes tem muita semelhança com as classes em Ruby

    class Pessoa
      constructor: (@name, @trabalho) ->
      
      trabalho: (acao) ->
        alert """#{@name} esta #{acao} como #{@trabalho}"""
        
    class Programador extends Pesssoa
      trabalho: (idade) ->
        super """digitando"""
        alert """tem #{idade} de idade"""
        
    renan = new Programador "Renan", "Programador Junior"
    renan.trabalho(45)

    var Pessoa, Programador, renan;
    
    Pessoa = class Pessoa {
      constructor(name, trabalho) {
        this.name = name;
        this.trabalho = trabalho;
      }
    
      trabalho(acao) {
        return alert(`${this.name} esta ${acao} como ${this.trabalho}`);
      }
    
    };
    
    Programador = class Programador extends Pesssoa {
      trabalho(idade) {
        super.trabalho(`digitando`);
        return alert(`tem ${idade} de idade`);
      }
    
    };
    
    renan = new Programador("Renan", "Programador Junior");
    
    renan.trabalho(45);

Para métodos estáticos incluir o @ frente do nome do metodo

    class Teenager
      @say: (speech) ->
        words = speech.split ' '
        fillers = ['uh', 'um', 'like', 'actually', 'so', 'maybe']
        output = []
        for word, index in words
          output.push word
          output.push fillers[Math.floor(Math.random() * fillers.length)] unless index is words.length - 1
        output.join '-'

Nesse método vai receber como parâmetro uma String, esta string vai ser armazenada palavra por palavra separada pelo espaço dentro da lista words. Depois essas variáveis do words  são unidas com uma variável escolhida aleatoriamente da lista fillers.

No switch não precisa colocar o break no final ele ja faz isso para você em cada condição vai utilizar o when ajudado por um then e no valor default vira com else no final.

    switch day
      when "Mon" then go work
      when "Tue" then go relax
      when "Thu" then go iceFishing
      when "Fri", "Sat"
        if day is bingoDay
          go bingo
          go dancing
      when "Sun" then go church
      else go work

    switch (dia) {
      case "segunda":
        bora(trabalhar);
        break;
      case "terça":
        bora(trabalharmais);
        break;
      case "quarta":
        bora(estudar);
        break;
      case "quinta":
      case "sexta":
        if (compeonato === true) {
          bora(assistir);
        } else {
          bora("):");
        }
        break;
      default:
        bora(descansar);
    }

Pode chamar o switch atribuindo a uma variável também, caso não passe um parâmetro para o switch, por padrão ele vem como falso.

    day = switch 
      when "segunda" then bora trabalhar
      when "terça" then bora trabalharmais
      when "quarta"then bora estudar
      when "quinta", "sexta"
        if compeonato is true
          bora assistir
        else
          bora "):"
      else bora descansar  

    var day;
    
    day = (function() {
      switch (false) {
        case !"segunda":
          return bora(trabalhar);
        case !"terça":
          return bora(trabalharmais);
        case !"quarta":
          return bora(estudar);
        case !"quinta":
        case !"sexta":
          if (compeonato === true) {
            return bora(assistir);
          } else {
            return bora("):");
          }
          break;
        default:
          return bora(descansar);
      }
    })();

E nesse caso ele nega os cases. Para não negar os cases basta colocar um parâmetro ou true mesmo

    day = switch true
      when "segunda" then bora trabalhar
      when "terça" then bora trabalharmais
      when "quarta"then bora estudar
      when "quinta", "sexta"
        if compeonato is true
          bora assistir
        else
          bora "):"
      else bora descansar  

    var day;
    
    day = (function() {
      switch (true) {
        case "segunda":
          return bora(trabalhar);
        case "terça":
          return bora(trabalharmais);
        case "quarta":
          return bora(estudar);
        case "quinta":
        case "sexta":
          if (compeonato === true) {
            return bora(assistir);
          } else {
            return bora("):");
          }
          break;
        default:
          return bora(descansar);
      }
    })();

No try/catch tem a mesma semântica do JavaScript podendo adicionalmente omitir o parâmetro de erro no catch

    try
      allHellBreaksLoose()
      catsAndDogsLivingTogether()
    catch 
      "deu ruim"
    finally
      cleanUp()

    try {
      allHellBreaksLoose();
      catsAndDogsLivingTogether();
    } catch (error) {
      "deu ruim";
    } finally {
      cleanUp();
    }

Utiliza as comparações encadeadas do Python

    idade = 35
    
    adulto = 60 > idade >  20
    
    alert adulto

    var adulto, idade;
    
    idade = 35;
    
    adulto = (60 > idade && idade > 20);
    
    alert(adulto);