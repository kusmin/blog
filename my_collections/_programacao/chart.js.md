---
layout: post
comments: true
title: Chart.js
date: 2021-04-16 6:00 AM
description: introdução a uma biblioteca javascript para criar seus graficos de uma
  forma facil e elegante
imagem: "/uploads/chartsjs.png"
categories: javascript

---
Recentemente precisei fazer um trabalho que envolvia a manipulação de gráficos, o que envolvia também adicionar estes gráficos renderizados em pdf.  A opção escolhida foi a do [Chart.js](https://www.chartjs.org/ "https://www.chartjs.org/"), uma biblioteca em javascipt muito simples, elegante e com uma curva de aprendizado bem tranquila, recomendo como sempre que leiam a documentação [https://www.chartjs.org/docs/latest/](https://www.chartjs.org/docs/latest/ "https://www.chartjs.org/docs/latest/"), que por sinal é muito bem feita.

### Começando

Para instalar é bem tranquilo, caso esteja usando o node.js, basta rodar o comando

    npm install chart.js

Outra opção seria utilizar via CDN, o link com as passos para o CDN [https://cdnjs.com/libraries/Chart.js](https://cdnjs.com/libraries/Chart.js "https://cdnjs.com/libraries/Chart.js"). Com pouco código conseguimos criar um grafico, segue abaixo um exemplo:

>  <div class="graficos">
>
> <canvas id="line" width="370" height="370"></canvas>
>
> </div>
>
>   
> <div class="graficos">
>
>  <canvas id="doughnut" width="370" height="370"></canvas></div>  
>   
> <script>
>
> // Grafico de linha
>
>   
>   
> const labels = \[ 'January', 'February', 'March', 'April', 'May', 'June',\];
>
> const data = { labels: labels, datasets: \[{ label: 'valor 1', backgroundColor: 'rgb(255, 99, 132)', borderColor: 'rgb(255, 99, 132)', data: \[0, 10, 5, 2, 20, 5\], }, { label: 'valor 2', backgroundColor: 'rgb(0, 32, 98)', borderColor: 'rgb(0, 32, 98)', data: \[20, 10, 6, 2, 17, 0\], }, { label: 'valor 3', backgroundColor: 'rgb(255, 0, 0)', borderColor: 'rgb(255, 0, 0)', data: \[7, 10, 5, 8, 25, 16\], }, { label: 'valor 4', backgroundColor: 'rgb(124, 32, 25)', borderColor: 'rgb(124, 32, 25)', data: \[23, 18, 5, 9, 20, 30\], },  
>   
> \]};  
>   
> const config = { type: 'line', data: data};  
> // Grafico de rosca  
>   
> const dataDoughnut = { labels: \['opção 1', 'opção 2', 'opção 3', 'opção 4', 'opção 5' \], datasets: \[{ label: 'Grafico', data: \[70, 40, 50, 20, 90\], backgroundColor: \[ 'rgb(255, 99, 132)', 'rgb(124, 32, 25)', 'rgb(255, 99, 132)', 'rgb(54, 162, 235)', 'rgb(255, 205, 86)' \] } \]};  
> const configDoughnut = { type: 'doughnut', data: dataDoughnut, options: {}};  
>   
>   
>  var myChart = new Chart( document.getElementById('line'), config);  
> var doughnut = new Chart( document.getElementById('doughnut'), configDoughnut);  
>   
>   
>   
>   
>  var myChart = new Chart( document.getElementById('line'), config);
>
>   
> var doughnut = new Chart( document.getElementById('doughnut'), configDoughnut);
>
>  var myChart = new Chart( document.getElementById('line'), config );
>
>   
>  myChart.resize(300, 300);
>
>   
>  var doughnut = new Chart( document.getElementById('doughnut'), configDoughnut );
>
>   
>  doughnut.resize(300, 300);
>
> </script>

Neste exemplo temos a construção de dois tipos de gráfico um de linha e outro de rosca. Como pode ver a utilização dele se baseia na tag do canvas HTML, a partir do id no canvas declaramos uma new Chart, passando os dados e as configurações a serem adotadas, e ele também muitas configurações que permitem um alto grau de estilização.