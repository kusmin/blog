---
layout: post
comments: true
title: SCP
date: 2021-05-18 6:00 AM
description: Como utilizar o comando SCP para transferir arquivos dentro do Linux
imagem: "/uploads/scp.jpeg"
categories: Arquivos, SCP

---
Para quem não sabe, SCP é um protocolo que permite copiar arquivos entre um servidor SSH e uma máquina local. Para funcionar o comando **scp** é necessário que já tenha configurado uma conexão SSH com um servidor remoto. O comando deve ter esse padrão:

    scp {opções} {usernameDoArquivoDeOrigim@IP} :/ {diretorioNomeArquivo} {UsernameDestinoDoArquivo@IP}:/ {DiretorioDeDestino}

###### Legenda:

* usernameDoArquivoDeOrigim@IP: nome do usuario e do IP da maquina onde esta o arquivo que desejo.


* :/ : Informa ao comando SCP que vou digitar o diretorio fonte.


* DiretorioNomeArquivo: Onde o arquivo esta localizado e o nome dele.


* UsernameDestinoDoArquivo@IP: é o nome do usuário e do IP da máquina de destino.


* DiretorioDeDestino: diretorio onde irei salvar o arquivo.

#### Opções úteis

* –**P** possibilita especificar uma entrada diferente para o servidor (a porta padrão para a porta TCP para o comando é a 22).
* –**c** dá a possibilidade de especificar a encriptação do algoritmo que o cliente vai usar. Alguns dos valores que você pode usar são ‘aes256-ctr’, ‘aes256-cbc’, ‘blowfish-cbc’, ‘arcfour’, ‘arcfour128’, ‘arcfour256’, ‘cast128-cbc’, aes128-ctr’, ‘aes128-cbc’, ‘aes192-ctr’, ‘aes192-cbc’ e 3des-cbc’. A opção padrão na configuração do shell é ‘AnyStdCipher’
* –**q** vai executar a operação em modo silencioso, o que significa que apenas os erros críticos é que serão mostrados.
* –**r** é para cópia recursiva, que vai incluir todos os subdiretórios.
* –**4 or -6** pode ser usado se você quiser escolher a versão do protocolo empregada, sendo IPv4 ou IPv6. Você também pode configurar os requerimentos da configuração de IP mais exaustivamente com a palavra-chave da família de endereço.
* –**p** vai preservar os tempos iniciais de modificação e atributos do arquivo. .
* –**u** vai apagar a fonte do arquivo logo depois que a transferência for completada.
* –**c** vai habilitar a compressão de dados enquanto a operação de transferência está sendo executada.

#### Detalhe importante

O SCP usa encriptação SSH logo terá que usar uma senha para a transferência do arquivo. A partir do seguinte comando você consigue gerar um par de senhas SSH:

    ssh-keygen -t rsa

E utilizando o seguinte comando copia para o sistema remoto:

    ssh-copy-id user@remote_machine

#### Alguns exemplos

Copiando um arquivo remoto para máquina local:

    scp user@domain:/pasta-remota/arquivo-remoto.txt /pasta-local/arquivo-local.txt

  
Enviando um arquivo local para um servidor remoto:

    scp /pasta-local/arquivo-local.txt user@domain:/pasta-remota/arquivo-remoto.txt

  
Copiando pastas e subpastas do servidor remoto para máquina local:

    scp -r user@domain:/pasta-remota/ /pasta-local/

  
Enviando pastas e subpastas da máquina local para o servidor remoto:

    scp -r /pasta-local/ user@domain:/pasta-remota/

#### **Bibliografia:**

* [https://www.hostinger.com.br/tutoriais/usar-comando-scp-linux-para-transferir-arquivos](https://www.hostinger.com.br/tutoriais/usar-comando-scp-linux-para-transferir-arquivos "https://www.hostinger.com.br/tutoriais/usar-comando-scp-linux-para-transferir-arquivos")
* [https://www.hospedagemsegura.com.br/transferir-copiar-arquivos-via-scp/](https://www.hospedagemsegura.com.br/transferir-copiar-arquivos-via-scp/ "https://www.hospedagemsegura.com.br/transferir-copiar-arquivos-via-scp/")