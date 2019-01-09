---
layout: page
title: 107.3 Localização e internacionalização (Peso 3)
permalink: /107/107-3-localizacao-e-internacionalizacao
---


Ter a capacidade de localizar o sistema em uma lingua diferente do Inglês. Como também, conhecer o porque LANG=C é útil quando estamos escrevendo scripts.
Configurar locais e variáveis de ambiente
Configurar `timezones` e variáveis de ambiente

O Linux internamente trabalha com UTC. Por exemplo quando ele salva um arquivo ele grava as informações de data em UTC, mas apenas para visualização do usuário final ele exibe de outra forma.

## /etc/timezone

Algumas distribuições utilizam esse arquivo para configurar o seu timezone. Então para mudar o seu timezone basta mudar o conteúdo desse arquivo de texto.

<pre class="command-line language-bash">
<code>cat /etc/timezone</code>
America/Belem
</pre>


## /etc/localtime

Esse é o principal arquivo de configuração de timezone. Na verdade ele é um link simbólico que aponta para algum **arquivo binário** dentro do diretório `/usr/share/zoneinfo`.


Podemos mudar o timezone removendo o arquivo:

<pre class="command-line language-bash">
<code>rm /etc/localtime</code>
</pre>

E criamos novamente o arquivo apontando para um novo timezone:

<pre class="command-line language-bash">
<code>ln -s /usr/share/zoneinfo/America/Belem /etc/localtime</code>
</pre>


Veja abaixo como o arquivo é apenas um link que aponta para `/usr/share/zoneinfo/America/Belem`

<pre class="command-line language-bash">
<code>ls -l /etc/localtime</code>
lrwxrwxrwx 1 root root 33 Jun 29 23:20 /etc/localtime -> /usr/share/zoneinfo/America/Belem
</pre>

## /usr/share/zoneinfo/

O diretório `/usr/share/zoneinfo` é uma estrutura de diretório com configurações de diferentes timezones. Sendo que muitas delas são apenas links para outras configurações.

## LC_TIME

Variável de localização é utilizada para definir a formatação de data e hora?


## LC_*


## LC_ALL


## LANG


## TZ

O `TZ` é uma variável de ambiente que armazena o timezone da sessão atual. Por padrão ela não vem setada:

<pre class="command-line language-bash">
	<code>echo $TZ</code>
</pre>

Vamos dar um date e verificar a data atual:

<pre class="command-line language-bash">
	<code>date</code>
	Sun Aug 12 21:01:20 -03 2018
</pre>

Perceba que nos estamos utilizando o timezone que esta configurado no arquivo /etc/timezone. Mas podemos mudar isso mudando a variável `TZ`.

<pre class="command-line language-bash">
	<code>export TZ=America/Port_of_Spain</code>
</pre>

Vamos novamente exibir a data atual com o comando `date`:

<pre class="command-line language-bash">
	<code>date</code>
	Sun Aug 12 20:03:26 AST 2018
</pre>

**Evidentemente se realizarmos um unset na variável TZ nossa data volta a configurada no /etc/timezone**

É possivel ainda definir o valor de TZ apontado para o diretorio dentro de /usr/share/zoneinfo. Abaixo configuração realizada utilizando a localização do arquivo:

<pre class="command-line language-bash">
	<code>export TZ=/usr/share/zoneinfo/Mexico/BajaSur</code>
</pre>


## /usr/bin/locale

Esse comando exibe as informações que localização do sistema.

<pre class="command-line language-bash">
	<code>locale</code>
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE=en_US.UTF-8
LC_NUMERIC=pt_BR.UTF-8
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=pt_BR.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=pt_BR.UTF-8
LC_NAME=pt_BR.UTF-8
LC_ADDRESS=pt_BR.UTF-8
LC_TELEPHONE=pt_BR.UTF-8
LC_MEASUREMENT=pt_BR.UTF-8
LC_IDENTIFICATION=pt_BR.UTF-8
LC_ALL=
</pre>

>>A variável **LC_ALL** sobreescrve todas as demais.

Essas informações são na verdade variáveis de ambiente. Podemos ver essas mesmas informações com o comando abaixo:

<pre class="command-line language-bash">
	<code>env | grep "^LC"</code>
LC_TELEPHONE=pt_BR.UTF-8
LC_NAME=pt_BR.UTF-8
LC_NUMERIC=pt_BR.UTF-8
LC_IDENTIFICATION=pt_BR.UTF-8
LC_PAPER=pt_BR.UTF-8
LC_MONETARY=pt_BR.UTF-8
LC_MEASUREMENT=pt_BR.UTF-8
LC_ADDRESS=pt_BR.UTF-8
LC_CTYPE=en_US.UTF-8
</pre>


### LANG=C

Quando escrevemos um script e não queremos que as configurações de localização afetem o comportamento do nosso script. Para resolver isso basta deixar a variável LANG com o valor `C`.  

## tzselect

É um comando que nos ajuda a encontrar o timezone que desejamos definir no sistema. **Ele não altera a configuração do sistema apenas exibe o timezone escolhido**. Veja abaixo a utilização do comando: 


<pre class="command-line language-bash">
	<code>tzselect </code>
Please identify a location so that time zone rules can be set correctly.
Please select a continent, ocean, "coord", or "TZ".
 1) Africa
 2) Americas
 3) Antarctica
 4) Asia
 5) Atlantic Ocean
 6) Australia
 7) Europe
 8) Indian Ocean
 9) Pacific Ocean
10) coord - I want to use geographical coordinates.
11) TZ - I want to specify the time zone using the Posix TZ format.
#? 2
Please select a country whose clocks agree with yours.
 1) Anguilla		  19) Dominican Republic    37) Peru
 2) Antigua & Barbuda	  20) Ecuador		    38) Puerto Rico
 3) Argentina		  21) El Salvador	    39) St Barthelemy
 4) Aruba		  22) French Guiana	    40) St Kitts & Nevis
 5) Bahamas		  23) Greenland		    41) St Lucia
 6) Barbados		  24) Grenada		    42) St Maarten (Dutch)
 7) Belize		  25) Guadeloupe	    43) St Martin (French)
 8) Bolivia		  26) Guatemala		    44) St Pierre & Miquelon
 9) Brazil		  27) Guyana		    45) St Vincent
10) Canada		  28) Haiti		    46) Suriname
11) Caribbean NL	  29) Honduras		    47) Trinidad & Tobago
12) Cayman Islands	  30) Jamaica		    48) Turks & Caicos Is
13) Chile		  31) Martinique	    49) United States
14) Colombia		  32) Mexico		    50) Uruguay
15) Costa Rica		  33) Montserrat	    51) Venezuela
16) Cuba		  34) Nicaragua		    52) Virgin Islands (UK)
17) Curaçao		  35) Panama		    53) Virgin Islands (US)
18) Dominica		  36) Paraguay
#? 1

The following information has been given:

	Anguilla

Therefore TZ='America/Port_of_Spain' will be used.
Local time is now:	Sun Aug 12 19:57:41 AST 2018.
Universal Time is now:	Sun Aug 12 23:57:41 UTC 2018.
Is the above information OK?
1) Yes
2) No
#? yes
Please enter a number in range.
#? 1

You can make this change permanent for yourself by appending the line
	TZ='America/Port_of_Spain'; export TZ
to the file '.profile' in your home directory; then log out and log in again.

Here is that TZ value again, this time on standard output so that you
can use the /usr/bin/tzselect command in shell scripts:
America/Port_of_Spain
</pre>

## timedatectl

Esse comando é utilizado para exibir da data atual em diferente formatos:

<pre class="command-line language-bash">
	<code>timedatectl</code>
   Local time: Sun 2018-08-12 20:36:33 -03
  Universal time: Sun 2018-08-12 23:36:33 UTC
        RTC time: Sun 2018-08-12 23:36:33
       Time zone: America/Belem (-03, -0300)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

</pre>



## date


## iconv


## UTF-8


## ISO-8859


## ASCII


## Unicode