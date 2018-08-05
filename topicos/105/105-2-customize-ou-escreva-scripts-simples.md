---
layout: page
title: 105.2 Customize ou Escreva Scripts Simples (Peso 4)
permalink: /105/105-2-customize-ou-escreva-scripts-simples
---

Canditados devem ser capazes de alterar scripts simples ou escrever novos scripts em bash


* Utilizar a sintaxe padrão de loops e testes
* Utilizar substituição de comando
* Testar valores de retorno, para verificar falha ou sucesso ou outras informações forncecidas por um comando
* Realizar envio de email condicional para o superusuário
* Escolher corretamento o interpretador do script com o uso do She-Bang
* Gerenciar a localização, dono e execução e permissões suid de scripts

### Termos e Utilitários

* if
* test
* for
* while
* read
* seq
* exec


Um script nada mais é do que uma conjunto de comandos salvos em um arquivo, sendo que esses comandos são executados em uma determinada ordem.

Um script bash é interpretado pelo bash e seu resultado é executado. 

### Estrututa básica de um arquivo de script bash

Veja abaixo o conteúdo do arquivo **imprimir.sh** que realiza a simples tarefa de imprimir a mensagem "Isso é um script bash." No terminal. Para isso utilizamos o comando **echo**

	
	echo "Isso é um script bash."

Para exucutar esse script devemos entrar no diretório **~/Scripts** e em seguida executar um dos comandos abaixo  no terminal.

Podemos apenas chamar o imterpretador do **bash** e em seguida o nome do arquivo:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>bash imprimir.sh</code>
</pre>

Ou com interpretador **sh**:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>sh imprimir.sh</code>
</pre>


Ou ainda o comando  **exec**. Logo apos o termindo do script sua sessão atual do bash sera encerrada, essa é a caracterisca do comando exec:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>exec imprimir.sh</code>
</pre>

Veja que até o momento nosso arquivo não possui permissão de execução:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>ls -l imprimir.sh</code>
-rw-rw-r-- 1 alphabraga alphabraga 30 Aug  5 18:28 imprimir.sh
</pre>


Podemos executar o script sem que seja necessario chamar um interpretador de forma explicita. Basta usarmos o `She-Bang`. Que nada mais que do que uma anotação que fica no cabeçalho do script que indica que interpretador deve ser chamado no momento que o arquivo for executado. Dessa forma não se faz nessário a utilização do comando **bash**. O script ficaria assim:

	#!/bin/bash
	echo "Isso é um bash script."


Mas para de fato o script funcionar precisamos ainda colcoar a permissão de execução nele.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>chmod +x imprimir.sh</code>
</pre>

Agora sim! Basta executar o comando abaixo para que o script seja executado com sucesso.


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost" >
<code>./imprimir.sh</code>
Isso é um bash script.
</pre>


