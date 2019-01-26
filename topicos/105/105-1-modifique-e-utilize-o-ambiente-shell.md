---
layout: page
title: 105.1 Modifique e utilize o ambiente shell
permalink: /105/105-1-modifique-e-utilize-o-ambiente-shell
---

Candidatos deve ser capazes de modificar ambientes do shell para atender as necessidades dos usuários. É também é necessário que saibam modificar ambientes globais e perfils de usuários.

* Definir variáveis de ambientes (como o PATH), no momento do login ou quando um novo shell é iniciado.
* Escrever funções em Bash para comandos frequentemente utilizados.
* Manter `skeleton directories` para novas contas de usuários.

## source

O comando `source` serve para executar arquivos de script. **Mas qual a diferença entre ele e o `sh` ou `bash` ?** O comando `source` não abre uma nova sessão de shell dessa forma variáveis definidas localmente são lidas pelo script. Vejamos o exemplo abaixo:

Definimos a variável `SISTEMA` e exibimos o seu valor com um echo:

<pre class="command-line language-bash">
	<code>SISTEMA=linux</code>
	<code>echo $SISTEMA</code>
	linux
</pre>

O script `meusistema.sh` exibe na tela o valor da variável local previamente definida. Veja abaixo o conteúdo do script: 

	echo $SISTEMA

Agora vamos executar o script utilizando o comando `bash`:

<pre class="command-line language-bash">
<code>bash meusistema.sh</code>

</pre>

Perceba que o valor da variável SISTEMA não foi exibido na tela.
Agora em vez do `bash` vamos usar o `source`:


<pre class="command-line language-bash">
<code>source meusistema.sh</code>
linux
</pre>

Podemos executar nossos scripts trocando a palavra `source` por um  `.` . Dessa forma:

<pre class="command-line language-bash">
<code>. meusistema.sh</code>
linux
</pre>

O source exibe o conteúdo da variável local porque não abre uma nova sessão.

## /etc/profile

Esse arquivo é invocado sempre que um novo login é realizado. Nele são contidas variaveis e funções.


## /etc/bash.bashrc

Esse arquivo é utilizado para definir funções e variáveis de ambiente. **Ele é invocado sempre que um novo bash é aberto.** Isso seginifca que sempre que um novo terminal for aberto no ambinete grafico ou em linha de comando digitando `bash` o arquivo `/etc/bash.bashrc` é chamado.
Esse arquivo executa atravez de um `source` o arquivo `/etc/bash.bashrc`.


## env

Esse comando lista **as variáveis de ambiente**

## set

Esse comando lista todas as **variáveis locais** e **variáveis de ambiente** além de **funções**. 

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

É importante ressaltar que um shell script que utiliza variáveis não declaradas dentro dele, só consegue ler as mesmas se elas estiverem expotadas. Isso porque quando executamos um script um novo `shell` é aberto. Para executar um script levando em consideraão as variáveis locais utilizamos o comando `source` 

## unset

Remove uma variável até mesmo se ela estiver exportada do ambiente. Para utilizar o comando basta executar:

<pre class="command-line language-bash">
<code>unset nomedavariavel</code>
</pre>


## ~/.bash_profile

Arquivo que contêm variáveis, funções e `alias` de um usuário expecifico

## ~/.bash_login

Arquivo que contêm variáveis, funções e `alias` de um usuário expecifico

## ~/.profile

Arquivo que contem variaveis, funcoes e alias de um usuário expecifico. **Esse arquivo é executado sempre que uma nova sessão para um determinado usuário é iniciada, por exemplo sempre que for aberto dentro do ambeinte grafico uma janela do terminal esse arquivo sera executado**.

## ~/.bashrc

Arquivo que contem variaveis, funcoes e alias de um usuário expecifico


### Ordem de execução

O sistema inicialmente procura por `~/.bash_profile` se ele não encontrar vai procurar o `~/.bash_login` e por sua vez se o mesmo não for encontrado o sistema vai procurar o `~/.profile`

## ~/.bash_logout

Esse arquivo é envocado sempre que realizamos o logout do sistema e ele executa tudo que estiver dentro dele anntes de realizar o logout

## function

Vamos aprender como definir funções dentro do linux. Utilizandomos a palavra reservada `function` em seguida um nome para a função, abrimos e fechamos parenteses:

	function primeira(){

	        echo "Essa é a primeira função. Usamos a palavra function e abrimos e fechamos parenteses depois do nome da função."
	}


Podemos dispensar os parenteses, **mas veja que existe um espaço entre o nome da função e o sinal de `{`**:

	function segunda {

	        echo "Assim escrevemos a segunda. Sem os parenteses, mas preste atenção pois existe um espaço entre o nome da função e as chaves"
	}

E por fim podemos omitir a palavra `function`:

	terceira(){

	        echo "Agora temos a terceira função. Escrevemos sem a palavra function, mas com os parenteses"
	}


## alias

O `alias` tem a função de definir apelidos para comandos. Imagine que você utiliza o comando `nmap -Pn 127.0.01` diversas vezes em seu terminal linux. E ter que digitar todo esse comando varias vezes pode ser entediante além de improdutivo. Mas você pode resolver esse problema, basta criar um `alias`. Basta definir no arquivo `~/.bash_bashrc` a linha:


	alias scanlocal="nmap -Pn 127.0.0.1"

Em seguida basta ler o arquivo `~/.bash_bashrc` com o comando `source`


	source ~/.bash_bashrc

Agora sim! O seu apelido esta disponível em seu ambiente shell

<pre class="command-line language-bash">
<code>scanlocal</code>
</pre>
		

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


Para remover um valor dentro da lista utilizamos o comando usent da seguinte forma:

<pre class="command-line language-bash">
	<code>ARRAY1 = (um dois tres)</code>
	<code>unset ARRAY1[2]</code>
	<code>echo ${ARRAY1[*]}</code>
</pre> 

Podemos observar que a sintaxe para remover o valor da lista não utiliza o `$`. 

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