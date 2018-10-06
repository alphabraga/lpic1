---
layout: page
title: 105.1 Modifique e utilize o ambiemte shell
permalink: /105/105-1-modifique-e-utilize-o-ambiente-shell
---

105.1 Modifique e utilize o ambiente do Shell Peso 4


Candidatos deve ser capazes de modificar ambientes do shell para atender as necessidades dos usuários. E também é necessário que saibam modificar ambientes globais e perfils de usuários


* Definir variáveis de ambeintes (como o PATH), no momento do login ou quando um novo shell é iniciado
* Escrver funcções em Bash para comandos frequentemente utilizados 
* Manter `skeleton directories` para novas contas de usuários

## source

O comando source serve para executar arquivos de script. 

**Mas qual a diferença entre ele e o `sh` ou `bash` ?**. O comando `source` não abre uma nova sessão de shell dessa forma variáveis definidas localmente são lidas pelo script. Vejamos o exemplo abaixo:

Definimos a variável `SISTEMA`

<pre class="command-line language-bash">
	<code>SISTEMA=linux</code>
	<code>echo $SISTEMA</code>
	linux
</pre>

O script `meusistema.sh` exibe na tela o valor da variável local previamente definida. Primeiro vamos executar o script apenas utilizando o comanod `bash`

	echo $SISTEMA

<pre class="command-line language-bash">
<code>bash meusistema.sh</code>

</pre>

Agora com o source:

<pre class="command-line language-bash">
<code>source meusistema.sh</code>
linux
</pre>

Podemos rodar nossos scripts usando o source trocando a palavra "source" por um "." . Ficando dessa forma:

<pre class="command-line language-bash">
<code>. meusistema.sh</code>
linux
</pre>


O source exibe o conteudo da variável local porque não abre uma nova sessão.


## /etc/bash.bashrc

Esse arquivo é utilizado para definir funções e variáveis de ambiente.

## /etc/profile

Esse arquivo é utilizado para definir funções e variáveis de ambiente.

## env

Esse comando lista **as variáveis de ambiente**

## set

Esse comando lista todos as **variáveis locais** e **variáveis de ambiente** além das **funções**. 

Veja o exemplo abaixo onde definimos uma variável local e em seguida procuramos essa variável com o comando `env`. E não encontramos o valor pois o comando `env` só encontra variáveis exportadas.


<pre class="command-line language-bash">
	<code>SISTEMA=linux</code>
	<code>echo $SISTEMA</code>
	linux
	<code>env | grep SISTEMA </code>
</pre>

Para encontrar variáveis locais utilizamos o comando `set`:

<pre class="command-line language-bash">
<code>SISTEMA=linux</code>
<code>echo $SISTEMA</code>
linux
<code>set | grep SISTEMA </code>
SISTEMA=linux
</pre>


## export

O comando export realiza o exportação de uma variável para o ambiente do `shell`. 

É importante ressaltar que um shell script que utiliza variáveis só consegue ler as mesmas se elas estiverem expotadas. Isso porque quando executamos um script um novo `shell` é aberto. Para executar um script levando em consideraão as variáveis locais utilizamos o comando `source` 

## unset

Remove uma variável do ambiente.

## ~/.bash_profile


Arquivo que contêm variáveis, funções e `alias` de um usuário expecifico

## ~/.bash_login

Arquivo que contêm variáveis, funções e `alias` de um usuário expecifico


## ~/.profile


Arquivo que contem variaveis, funcoes e alias de um usuário expecifico

## ~/.bashrc

Arquivo que contem variaveis, funcoes e alias de um usuário expecifico

## ~/.bash_logout

Esse arquivo é envocado sempre que realizamos o logout do sistema e ele executa tudo que estiver dentro dele anntes de realizar o logout

## function

Vamos aprender como definir uma função no linux

	function meunome {

		echo "Alfredo"
	}

Ou então:


	sobrenome(){

		echo "Braga"
	}


## alias

O `alias` tem a funçõe de definir apelidos para comandos. Imagine que você utiliza o comando :


	nmap -Pn 127.0.01


Diversas vezes em seu terminal linux. E ter que digitar todo esse comando varias vezes pode ser entediante além de improdutivo
Mas você pode resolver esse problema você pode fazer um do `alias`. Basta definir no arquivo `~/.bash_bashrc` a linha:


	alias scanlocal="nmap -Pn 127.0.0.1"

Em seguida basta ler o arquivo `~/.bash_bashrc` com o comando `source`


	source ~/.bash_bashrc

Agora sim! O seu apelido esta disponivel em seu ambiente shell


	scanlocal	

## lists

Variáveis do tipo array podem ser criadas utilizando a sintaxe abaixo:

	ARRAY=(valor1 valor2 ... valorN)


Podemos inserir os valores seguindo a sintaxe nomedalista[indicenumerico]=string. Número de indice é opcional, caso o indice não seja informado é utilizado o indice de maior valor mais um. O indice por padrão começa do zero.

Podemos adicionar mais itens ao array da seguinte forma:

	NOMEDOARRAY[INDICE]=VALOR

<pre class="command-line language-bash">
<code>ARRAY=(one two three)</code>
<code>echo ${ARRAY[*]}</code>
one two three
<code>echo $ARRAY[*]</code>
one[*]
<code>echo ${ARRAY[2]}</code>
three

[bob in ~] ARRAY[3]=four

[bob in ~] echo ${ARRAY[*]}
one two three four	
</pre>


Referring to the content of a member variable of an array without providing an index number is the same as referring to the content of the first element, the one referenced with index number zero.

10.2.3. Deleting array variables
The unset built-in is used to destroy arrays or member variables of an array:

	[bob in ~] unset ARRAY[1]

	[bob in ~] echo ${ARRAY[*]}
	one three four

	[bob in ~] unset ARRAY

	[bob in ~] echo ${ARRAY[*]}
	<--no output-->

10.2.4. Examples of arrays
Practical examples of the usage of arrays are hard to find. You will find plenty of scripts that don't really do anything on your system but that do use arrays to calculate mathematical series, for instance. And that would be one of the more interesting examples...most scripts just show what you can do with an array in an oversimplified and theoretical way.

The reason for this dullness is that arrays are rather complex structures. You will find that most practical examples for which arrays could be used are already implemented on your system using arrays, however on a lower level, in the C programming language in which most UNIX commands are written. A good example is the Bash history built-in command. Those readers who are interested might check the built-ins directory in the Bash source tree and take a look at fc.def, which is processed when compiling the built-ins.

Another reason good examples are hard to find is that not all shells support arrays, so they break compatibility.

After long days of searching, I finally found this example operating at an Internet provider. It distributes Apache web server configuration files onto hosts in a web farm:

	#!/bin/bash

	if [ $(whoami) != 'root' ]; then
	        echo "Must be root to run $0"
	        exit 1;
	fi
	if [ -z $1 ]; then
	        echo "Usage: $0 </path/to/httpd.conf>"
	        exit 1
	fi

	httpd_conf_new=$1
	httpd_conf_path="/usr/local/apache/conf"
	login=htuser

	farm_hosts=(web03 web04 web05 web06 web07)

	for i in ${farm_hosts[@]}; do
	        su $login -c "scp $httpd_conf_new ${i}:${httpd_conf_path}"
	        su $login -c "ssh $i sudo /usr/local/apache/bin/apachectl graceful"

	done
	exit 0

## Prioridade de busca de Comandos

Quando executamos um comando o `bash` o mesmo procura o comando na seguinte sequencia: 

* 1 - Aliases            : Apelidos definidos
* 2 - Funções            : Funções definidas
* 3 - Comandos Builtin   : comandos do proprio bash como (`ls`, `cd`, `echo`)
* 4 - Searching the PATH : nos diretórios definidos no PATH