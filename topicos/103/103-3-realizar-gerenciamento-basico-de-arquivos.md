---
layout: page
title: 103.6 Alterar a Prioridade de Execução de Processos (Peso 2)
permalink: 103/103-3-realizar-gerenciamento-basico-de-arquivos
---

* Ter a capacidade de user comandos básicos do Linux para gerenciar arquivos e diretorios.
* Copiar, mover, remover arquivos e diretorios individualmente
* Copiar multiplos arquivos e diretorios recursivamente
* Mover arquivos e diretórios recursivamente
* Remover arquivos e diretórios recursivamente
* Usar `wilcard` simples e avançados nos comandos 
* Usar o `find` para localizar e integragir em arquivos baseados em seu tipo, tamnho ou tempo
* Utilizar o comando `tar`, `cpio` e `dd`

## cp

O comando cp realiza a copia de arquivos. Sua utilização mais comum é essa:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cp arquivo.txt novo-arquivo.txt</code>
</pre>

No comando acima o comando `cp` realiza uma copia do `arquivo.txt` o diretorio corrente com o nome de `novo-arquivo.txt`.

Tambem podemos realizar a copia desse arquivo para outro diretório. Basta colocar o `path` relativo ou absoluti para o novo arquivo.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cp arquivo.txt ~/Desktop/nova-copia.txt</code>
</pre>


Ou ainda podemos indicar os dois caminhos tanto na origem como no destino.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cp ~/arquivo.txt ~home/usuario/Downloads/nova-copia.txt</code>
</pre>


O comando `cp` possui algumas opções como:

### `-r` **r**ecursive

É utiliado para realizar a copia de arquivos de forma recursiva. NO exemplo abaixo foi realizada a cópia de todos os arquivos que começam com `arquivo-9` e terminam com qualquer caracter para o diretório files. Veja abaixo:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>usuario@maquina:~/copias$ cp -r arquivo-9* files/
	usuario@maquina:~/copias$ cd files/
	usuario@maquina:~/copias/files$ ls -l
	total 0
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-90.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-91.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-92.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-93.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-94.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-95.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-96.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-97.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-98.txt
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 15:31 arquivo-99.txt
</code>
</pre>


### `-p` **p**reserve 

A opção `-p` preserva as permissões, `ownership`, e `timestamp` . No exemplo abaixo foi criado um arquivo com o usuario `alphabraga` em seguida com o usuario root foi criada uma cópia desse arquivo e por fim foi criada uma cópia do primeiro arquivo mas com a opção `-p`.

	alphabraga@sharp:~/manter$ touch file-alplhabraga
	alphabraga@sharp:~/manter$ ls -l
	total 0
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 16:46 file-alplhabraga
	alphabraga@sharp:~/manter$ su - root
	Senha: 
	root@sharp:~# cd /home/alphabraga/manter/
	root@sharp:/home/alphabraga/manter# cp file-alplhabraga file-root
	root@sharp:/home/alphabraga/manter# ls -la
	total 8
	drwxrwxr-x  2 alphabraga alphabraga 4096 Mar 30 16:47 .
	drwxr-xr-x 36 alphabraga alphabraga 4096 Mar 30 15:41 ..
	-rw-rw-r--  1 alphabraga alphabraga    0 Mar 30 16:46 file-alplhabraga
	-rw-r--r--  1 root       root          0 Mar 30 16:47 file-root
	root@sharp:/home/alphabraga/manter# cp -p file-alplhabraga file-root-com-p
	root@sharp:/home/alphabraga/manter# ls -la
	total 8
	drwxrwxr-x  2 alphabraga alphabraga 4096 Mar 30 16:47 .
	drwxr-xr-x 36 alphabraga alphabraga 4096 Mar 30 15:41 ..
	-rw-rw-r--  1 alphabraga alphabraga    0 Mar 30 16:46 file-alplhabraga
	-rw-r--r--  1 root       root          0 Mar 30 16:47 file-root
	-rw-rw-r--  1 alphabraga alphabraga    0 Mar 30 16:46 file-root-com-p
	root@sharp:/home/alphabraga/manter# 


Observe que as permissões foram mantidas no `file-root-com-p`



### `-f` **f**orce 

Se um arquivo de destino não pode ser aberto, realiza a remoção e tenta novamente


### `-i` **i**nteractive

Pergunta se uma ação de sobreescrita realmente deve ser realizada. Isso é muito util para não realizar a sobreescrita de uma rquivo importante, pois dá a chance do usuário confirmar a operacão. No exemplo abaixo vamos mover o arquivo `meu-arquivo.txt` para pasta `~/arquivos` mas já existe o arquivo `meu-arquivo.txt` nesse diretorio com a opção `-i` o sistema pergunta se o usuario realmente deseja sobreescrever o arquivo


	alphabraga@sharp:~$ cd arquivos/
	alphabraga@sharp:~/arquivos$ touch meu-arquivo.txt
	alphabraga@sharp:~/arquivos$ cd ..
	alphabraga@sharp:~$ touch meu-arquivo.txt
	alphabraga@sharp:~$ mv -i meu-arquivo.txt arquivos/meu-arquivo.txt 
	mv: sobrescrever 'arquivos/meu-arquivo.txt'? 


### `-v` **v**erbose

Essa opção é muito comum em diversos comandos do linux e ela gera uma saida mais verbosa observe:

	alphabraga@sharp:~/arquivos$ ls -l
	total 4
	drwxrwxr-x 2 alphabraga alphabraga 4096 Mar 30 17:08 backup
	-rw-rw-r-- 1 alphabraga alphabraga    0 Mar 30 17:08 file-01.txt
	-rw-rw-r-- 1 alphabraga alphabraga    0 Mar 30 17:08 file-02.txt
	-rw-rw-r-- 1 alphabraga alphabraga    0 Mar 30 17:08 file-03.txt
	-rw-rw-r-- 1 alphabraga alphabraga    0 Mar 30 17:08 file-04.txt
	-rw-rw-r-- 1 alphabraga alphabraga    0 Mar 30 17:08 file-05.txt
	alphabraga@sharp:~/arquivos$ cp -r file-0* backup/
	alphabraga@sharp:~/arquivos$ cp -rv file-0* backup/
	'file-01.txt' -> 'backup/file-01.txt'
	'file-02.txt' -> 'backup/file-02.txt'
	'file-03.txt' -> 'backup/file-03.txt'
	'file-04.txt' -> 'backup/file-04.txt'
	'file-05.txt' -> 'backup/file-05.txt'
	alphabraga@sharp:~/arquivos$ 

Sem a opção `-v` nada é impresso na tela. Já com a opção `-v` é colocado na saída padrão quais os arquivos foram copiados.

## rm

Tem praticamente os mesmos parametros do `cp`.

### -f, --force

Ignora arquivos não existentes e arqgumentos, nunca pergunta

### -i 

Pergunta a cada vez que vai remover um arquivo

	alphabraga@sharp:~/testes$ rm -ir file-{5..9}.txt

	rm: remover ficheiro regular vazio 'file-5.txt'? y
	rm: remover ficheiro regular vazio 'file-6.txt'? y
	rm: remover ficheiro regular vazio 'file-7.txt'? y
	rm: remover ficheiro regular vazio 'file-8.txt'? y
	rm: remover ficheiro regular vazio 'file-9.txt'? y


### -I     

Prompt once before removing more than three files, or when removing recursively; less intrusive than -i,  while  still giving protection against most mistakes

--interactive[=WHEN]

Prompt according to WHEN: never, once (-I), or always (-i); without WHEN, prompt always

-r, -R, --recursive

Remove diretorios e o seu conteúdo recursivamente

-d, --dir

Remove diretorios vázios

### -v, --verbose

Gera uma saída mais verbosa


## find

Encontra arquivos no sistema.

Primeiro passamos o parametro do local onde queremos que ele busque. Se nada for passado ele busca todos os arquivos no local atual.

Exemplo sem parametros:

	alphabraga@sharp:~/testes$ find

	.
	./arquivo-1.txt
	./arquivo-4.txt
	./arquivo-2.txt
	./file-0.txt
	./file-{0-9}.txt
	./backup.tar
	./arquivo-3.txt
	./file[0-9].txt
	./rele[1-5].txt
	./alfredo-dir

Exemplo com parametro de local:


	alphabraga@sharp:~/testes$ find /home/alphabraga/comandos/

	/home/alphabraga/comandos/
	/home/alphabraga/comandos/comando3
	/home/alphabraga/comandos/comando2
	/home/alphabraga/comandos/comando1


### -maxdepth

O find vai descendo a arvore de diretórios apartir do ponto de busca. **-maxdepth 0** siginifica que a busca ira ocorrer apenas no nivel de busca e nenhum diretório abaixo.

### -name

Busca pelo nome do arquivo. Podendo ser utilizados caracteres coringas.

### -iname

Realiza a busca de forma `case insensitive` 

## mkdir

Cria diretório. Com  o `-p` ele vai criando a arveore de diretórios caso eles não existam

## mv

O comando `mv` serve para mover arquivos, equivalente a um recortar e colar, tambem sendo utilizado para mudar o nome de arquivos possui praticamente as mesmas opções que o comando `cp` 

## ls

## rmdir

Só remove diretórios **vázios**. Ele tambem possui o parametro `-p` onde a arvore de diretórios é apagada caso não contenha arquivos em nenhum nó.

## touch

O comando `touch` segundo o `man` tem a utilidade mudar o timestamp de um arquivo. Dessa forma:

	alphabraga@sharp:~$ ls -l meu-novo-arquivo.txt 
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 17:23 meu-novo-arquivo.txt
	alphabraga@sharp:~$ touch meu-novo-arquivo.txt 
	alphabraga@sharp:~$ ls -l meu-novo-arquivo.txt 
	-rw-rw-r-- 1 alphabraga alphabraga 0 Mar 30 17:24 meu-novo-arquivo.txt

Veja que o `timestamp` mudou apos a execução do `touch`.

** Esse comando cria o arquivo caso ele não exista** . Existem parametros importantes:


### m

Altera apenas a data de criação do arquivo



### c



## tar


## cpio


## dd


## file

## gzip

## gunzip

## bzip2

## xz

## file globbing