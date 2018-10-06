---
layout: page
title: 108-3 Mail Transfer Agent Básico
permalink: /108/108-3-mail-transfer-agent-basico
---

Cadidados devem ter conhecimento sobre os MTA's disponiveis e ser capazes de realizar redirecionamentos básicos e configuração de `alias` em um cliente. Outros arquivos de configuração não seram cobrados


Criar email `alias`

Configurar email `forwarding`
Conhecimento de programas de MTA disponiveis (postfix, sendmail, qmail, exim) não sera cobrada a configuração desses MTA's

## MTA

MTA é a sigla para Mail Transfer Agent. Que é o programa responsável pelo envio e recebimento de emails. É o que chamamos tambem de **servidor de emails** ou **servidor smtp**.

### Principais MTA's

* PostFix : Hoje em dia é o mais utilizado
* SendMail: Por muito tempo foi considerado o padrão. Ainda muito utilizado
* Qmail   : Bem antigo. Não é mais mantido há uns 15 anos.
* Exim    : Uma outra opção.. nada mais...
	

##SMTP

O SMTP ou Send Mail Transfer Protocol é o protocolo utilizado para o envio e recebimento emails. Por padrão o `smtp` utiliza a porta `25`.

## ~/.forward

## sendmail emulation layer commands

## newaliases

## mail

O comando `mail` é utilizado para enviar e ler emails. Para realizar o envio podemos utiliza-lo de 3 formas:

Podemos utilizar o comando com o modo interativo. Onde apos digitar o destinátario digitamos `ENTER`. Informa-mos os emails de cópia, essa informação é opcional. Por fim digatamos `ENTER` para começar a digitar o corpo da mensagem. E para realizar o envio da mensagem digitamos `Ctrl+D`.  

<pre class="command-line language-bash">
	<code>mail -s "aqui é o titulo da mensagem" nome@dominio.com.br [ENTER] </code>
	<code>Cc:[ENTER]</code>
	<code>Digitamos a mensagem por aqui[Ctrl+D]</code>
</pre>


Ou mandando a mensagem com um pipe:

<pre class="command-line language-bash">
	<code>echo "O corpo da mensagem" | mail -s "aqui é o titulo da mensagem" nome@dominio.com.br </code>
</pre>

Ou ainda fazendo um redirecionador:

<pre class="command-line language-bash">
	<code>mail -s "aqui é o titulo da mensagem" nome@dominio.com.br < nome-de-um-arqvivo.txt </code>
</pre>

O comando `mail` digitado sem agumentos lista as menagens de email do usuário do usuário atual

* A caixa de entrada fica em `var/mail/<usuario>`.
* A mensagens lidas ficam em `home/<usuario>/mbox` . 


Outro diretório importante é o `/var/spool/mail`. Em algumas distribuições o diretório  `/var/mail` é um link para o `/var/spool/mail` . O padrão do Linux é o `/var/spool/mail`.

Nele ficam arquivos texto com os nomes dos usuários. O conteúdo desses arquivos são os emails dos usuários.


## /etc/aliases

Arquivo que contem atalhos/apelidos


