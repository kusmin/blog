---
layout: post
comments: true
title: SSH
date: 
description: ''
imagem: ''
categories: ''

---

Padrão de permissão para execução das chaves SSH:

    chmod 400 "endereço-da-chave".pem

Acesso pelo terminal 

    ssh -i "endereço-da-chave".pem "user"@"endereço-dns-servidor"