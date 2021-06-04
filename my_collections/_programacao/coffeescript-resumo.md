---
layout: post
comments: true
title: CoffeeScript resumo
date: 2021-06-03 6:00 AM
description: Resumo sobre as principais funcionalidades do CoffeeScript
imagem: "/uploads/cofeescript.png"
categories: CofeeScript
published: false

---
CoffeeScript é uma mistura bem gostosa de Ruby e Python. Nele lhe permite escrever códigos de uma forma quase discursiva. Por exemplo:

    if x is yes
      console.log x

Ou seja, lendo o código ao pé da letra seria "se x é sim, imprima o valor de x". Um código bem mais simplificado do que ficaria em JavaScript:

    if (x === true) {
      console.log(x);
    }

Alias o CoffeeScript, é compilado para JavaScript, logo o código acima de CoffeScript quando compilado gera o código abaixo de JavaScript.

Mais um detalhe que você ter notado é que em CoffeeScript não é comum se utilizar de chaves, parentese ou ponto-e-virgula são opcionais. Ele utiliza a endentação e os espaços assim como o Python, por exemplo caso no exemplo acima caso estivesse esquecido de colocar o espaço, ele iria retorna um erro por não ter nada executado dentro do if, um exemplo de como esquecer a endentação pode dar problema é o exemplo a seguir:

    if x is yes 
      console.log x
    else
    console.log x+1

Você esperaria que o console.log x+1 estaria executando dentro do else, mas o que ocorre é que ele executado fora da condição if/else, compilando o JavaScript a seguir:

    if (x === true) {
      console.log(x);
    } else {
    
    }
    
    console.log(x + 1);