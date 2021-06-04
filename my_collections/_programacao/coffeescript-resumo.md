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

Mais um detalhe que você ter notado é que em CoffeeScript não é comum se utilizar de chaves, parentese ou ponto-e-virgula são opcionais. Ele utiliza a endentação e os espaços assim como o Python, por exemplo caso no exemplo acima caso estivesse esquecido de colocar o espaço 