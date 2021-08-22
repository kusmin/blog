---
layout: post
comments: true
title: SSH
date: 2021-08-22 6:00 AM
description: ''
imagem: ''
categories: ''
published: false

---

Padrão de permissão para execução das chaves SSH:

    chmod 400 "endereço-da-chave".pem

Acesso pelo terminal 

    ssh -i "endereço-da-chave".pem "user"@"endereço-dns-servidor"