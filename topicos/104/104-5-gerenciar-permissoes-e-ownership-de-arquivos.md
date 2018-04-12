---
layout: page
title: 104.5 Gerenciar Permissões e Owership de Arquivos (Peso 3)
permalink: 104/104-5-gerenciar-permissoes-e-ownership-de-arquivos
---

Ter a capacidade de controlar acesso a arquivos e tambem e utilizar o controle de permissões ownerships de modo adequado.

* Gerenciar acesso a permissões em arquivos regulares e especiais como tambem em diretórios
* Utilizar modos de acesso como o `sgid` e o `sticky bit` para manter a segurança
* Saber como mudar a mascara de criação de arquivos
* Utilizar o campo de grupo para garantir acesso a arquvios menbros de grupos

## chmod

O comando `chmod` segundo o `man` é:

> chmod changes the file mode bits of each given file according to mode,
> which can be either a symbolic representation of changes to make, 
> or an octal number representing the bit pattern for the new
> mode bits.


Em resumo esse comando altera as pemissões de um arquivo ou diretório. Atraves de parametros utilizando `letras` que podemos chamar de simbolico e o octal.

### Modo Octal








### Modo Simbolico

Para visualizar as pemissões de um arquivo iremos executar o comando

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ls -l arquivo.txt</code>
-rwxrwxrwx 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

As permissões do arquivo `arquivo.txt` são representadas pelos caracteres `-rw-rw-r--` . 

* `r` permissão de leitura (**r**ead)
* `w` permissão de escrita (**w**rite)
* `x` permissão de execução (e**x**ecution)

Esses caracteres representam de forma simplificada 3 níveis de permissão:

* **rwx**rwxrwx permissões de usuário
* rwx**rwx**rwx permissões de grupo
* rwxrwx**rwx** permissões de outros


Primeiro vamos remover todas as permissões do arquivo

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>sudo chmod 000 arquivo.txt</code>
</pre>


Para atribuir ao dono do arquivo a permissão de leitura:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod u=r arquivo.txt</code> 
<code>ls -la arquivo.txt</code> 
-r-------- 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Para remover a permissão utilizamos o sinal de `-`

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod u-r arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---------- 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>


Podemos adicionar e remover varias permissões ao mesmo tempo

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod u+rwx arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
-rwx------ 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Ou ainda assim para o dono:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod u=rwx arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
-rwx------ 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Para o grupo:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod g=rwx arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
----rwx--- 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Para os outros:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod o=rwx arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
-------rwx 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>


## chown

## chgrp

## umask
