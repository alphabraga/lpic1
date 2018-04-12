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

Dar permissão de execução para o dono, o grupo e os outros:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>chmod +x arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---x--x--x 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

### -R, --recursive

Realiza as alterações de forma recursiva

## chown

O comando `chown` (Change Owner) realiza a alteração do dono e do grupo do arquivo

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro outrogrupo 0 Abr 10 23:02 arquivo.txt
<code>chown alphabraga arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---x--x--x 1 alphabraga outrogrupo 0 Abr 10 23:02 arquivo.txt
</pre>

Agora para mudar o grupo podemos fazer assim:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro outrogrupo 0 Abr 10 23:02 arquivo.txt
<code>chown alphabraga:alphabraga arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---x--x--x 1 alphabraga alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Para mudar só o grupo

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro outrogrupo 0 Abr 10 23:02 arquivo.txt
<code>chown :alphabraga arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

Podemos usar o separador `.` para separar o usuario do grupo

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro outrogrupo 0 Abr 10 23:02 arquivo.txt
<code>chown .alphabraga arquivo.txt</code> 
<code>ls -l arquivo.txt</code> 
---x--x--x 1 outro alphabraga 0 Abr 10 23:02 arquivo.txt
</pre>

### -R, --recursive

Com o  `-R` podemos aplicar as alterações de forma recursiva, para toda uma pasta por exemplo.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>sudo chown -R root:root dir-perms </code> 
<code>ls -l dir-perms/*</code> 
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-0.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-10.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-11.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-12.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-13.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-14.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-15.txt
-rw-rw-r-- 1 root root 0 Apr 12 14:09 dir-perms/exemplo-16.txt
</pre>

## chgrp

Esse comando muda apenas o grupo do arquivo.

## umask

Sempre que o usuário realiza a criação de um arquivo ou diretorio no sistema operacional o mesmo os cria utilizando dois parametros. O primeiro é permissão padrão do elemento criado. Para arquivos a permissão padão é a `666`, já para diretorios é a `777`.

> A permissão padrão para criar arquivos é 666 e para diretórios é 777

O segundo parametro utilizado para a criação de arquivos e diretórios é a mascara padrão do sistema. A mascara padrão do sistema é um valor octal que sera subtraido do valor da permissão padrão. O comando `umask` retorna o valor da máscara.

Sendo assim a permissão de um arquivo em um sistema linux é igual a 666 - `umask`. E a permissão de um diretório é 777 - o `umask`.

Para saber o `umask` padrão do sistema iremos utilizar o comando umask.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>umask</code> 
002
</pre>

Admitindo que o umask é igual a `002`. A permissão final do arquivo será igual a `664`, ou seja, `rw-rw-r--`. 

		666
	-	002
		____
		664

Podemos comprovar isso dando criando e listando o arquivo recem criado.



	

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>touch minhas-perms.txt</code> 
<code>ls -l minhas-perms.txt</code> 
-rw-rw-r-- 1 alphabraga alphabraga 0 Apr 12 13:59 minhas-perms.txt
<code>stat minhas-perms.txt</code> 
  File: 'minhas-perms.txt'
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 801h/2049d	Inode: 37506501    Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/alphabraga)   Gid: ( 1000/alphabraga)
Access: 2018-04-12 13:59:02.778333875 -0300
Modify: 2018-04-12 13:59:02.778333875 -0300
Change: 2018-04-12 13:59:02.778333875 -0300
</pre>

Da mesma forma que ao criar um diretorio a permissão final do diretório será `775` ou ainda `rwxrwxr-x`

		777
	-	002
		____
		775

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>mkdir dir-perms</code> 
<code>ls -l | grep dir-perms</code>
drwxrwxr-x  2 alphabraga alphabraga       4096 Apr 12 14:01 dir-perms
<code>stat dir-perms</code>
  File: 'dir-perms'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 45350989    Links: 2
Access: (0775/drwxrwxr-x)  Uid: ( 1000/alphabraga)   Gid: ( 1000/alphabraga)
Access: 2018-04-12 14:01:22.751563302 -0300
Modify: 2018-04-12 14:01:19.599535514 -0300
Change: 2018-04-12 14:01:19.599535514 -0300
 Birth: -
</pre>