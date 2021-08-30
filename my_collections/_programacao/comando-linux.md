---
layout: post
comments: true
title: Comando Linux
date: 2021-08-28 6:00 AM
description: Comandos úteis para se usar no Linux
imagem: "/uploads/linux.jpeg"
categories: Linux

---
Para abir o gerenciador:

    sudo software-properties-gtk

Para atualizar  os programas:

    sudo apt-get update
    sudo apt-get upgrade

Caso não atualize pode forçar a atualização com:

    sudo apt-get dist-upgrade

Abrir imagem pelo terminal:

    display nome_da_imagem.jpg

Comando curl, opções do cURL:

* `-X` define o método HTTP a ser utilizado
* `-i` inclui informações detalhadas da resposta
* `-H` define um cabeçalho HTTP
* `-d` define uma representação do recurso a ser enviado ao serviço

    curl -X POST
      -i
      -H 'Content-Type: application/json'
      -d '{ "valor": 51.8, "nome": "JOÃO DA SILVA", "numero": "1111 2222 3333 4444", "expiracao": "2022-07", "codigo": "123", "formaDePagamentoId": 2, "pedidoId": 1 }'
      http://localhost:8081/pagamentos