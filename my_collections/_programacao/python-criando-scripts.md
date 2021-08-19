---
layout: post
comments: true
title: 'Python: criando scripts'
date: 2021-08-18 6:00 AM
description: Rodando os primeiros scripts em python
imagem: "/uploads/script-python.jpeg"
categories: python, scripts, automação

---
![](/uploads/script-python.jpeg)

Python é uma linguagem de script muito simples e divertida de se utilizar, amplamente utilizada por não-programadores por sua facilidade e curva de aprendizado menor. É amplamente utilizada em áreas que tem tido destaque atualmente como a inteligencia artificial.

Neste post veremos como instalar no Linux e um scrip bem simples para começar.

### Instalando

Na maioria das vezes o python já vem por padrão instalando, alguma versão, para verificar execute no terminal:

    which python

Caso tenha instalado deve retornar: 

    /usr/bin/python

Caso contrario deve retornar algo parecido como:

    which: no python in (/usr/local/sbin:/usr/local/bin:/usr/bin:/usr...)

Para instalar o Python 3, digite no terminal:

    sudo apt-get install python3

Depois instale também o gerenciador de pacote pip, ele vai ser necessário para instalar módulos do python:

    sudo apt-get install python3-pip

Segue abaixo um pequeno script para busca de oportunidades no linkedin:

    import time
    
    from selenium import webdriver
    from selenium.webdriver.common.keys import Keys
    
    browser = webdriver.Chrome(
        '/usr/bin/chromedriver')
    
    browser.get("https://www.linkedin.com/login")
    
    input_email = browser.find_element_by_id("username")
    input_email.send_keys("##Coloque seu email##")
    
    input_senha = browser.find_element_by_id("password")
    input_senha.send_keys("##coloque sua senha aqui##")
    
    btn_login = browser.find_element_by_xpath("//button[@type='submit']")
    btn_login.click()
    
    
    busca = browser.find_element_by_xpath("//input[@placeholder='Pesquisar']")
    busca.send_keys("Python")
    busca.send_keys(Keys.RETURN)
    
    time.sleep(2)
    
    filtro_vagas = browser.find_element_by_xpath("//button[@aria_label='Vagas']")
    filtro_vagas.click()
    
    input('')

A primeira coisa que vai ter que fazer para rodar sera baixar o pacote do selenium pelo pip.

    pip install selenium

E para executar o selenium também vamos precisar baixar e instalar  chromedriver, você pode baixar no [https://chromedriver.chromium.org/downloads](https://chromedriver.chromium.org/downloads "https://chromedriver.chromium.org/downloads"), de acordo com sua versão do Chrome, para verificar a versão do Chrome, vá nos três pontos ao no lado direito e depois clique em ajuda -> sobre o Google Chrome

![](/uploads/captura-de-tela-de-2021-08-18-21-14-17.png)

![](/uploads/captura-de-tela-de-2021-08-18-21-14-28.png)

Depois basta descompactar o arquivo, e move-lo para a pasta bin com:

    mv chromedriver /usr/bin

Não se esqueça de dar a permissão para executar o binario:

    chmod +x chromedriver

E lembre-se preencher com seu e-mail e senha, para executar o aplicativo basta, executar no terminal:

    python "nome-do-arquivo".py