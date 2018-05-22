---
layout: page
title: 103.4 Utilizar Fluxos Pipes e Redirecionamentos
permalink: 103/103-4-utilizar-fluxos-pipes-e-redirecionamentos
---

Candidatos devem ter a capacidade de redirect streams and connect them in order to efficiently process textual data. Tasks include redirecting standard input, standard output and standard error, piping the output of one command to the input of another command, using the output of one command as arguments to another command and sending output to both stdout and a file.

Areas Chave de Conhecimento:

* Redirecting standard input, standard output and standard error
* Pipe the output of one command to the input of another command
* Use the output of one command as arguments to another command
* Send output to both stdout and a file

Todo programa/processo no linux possui o que chamamos de descritores de arquivo, para ser mais exato 3 descritores.


## stdin

Significa Standart Input, seu codigo é `0`. Que é o teclado.

## sdout

Significa Standart output, seu código é `1`. Que é a tela.

## stderr

Significa Standart Error, seu código é `2`. Por padrão elas vão pra tela.

O `2>&1`

	wget -q -O - http://yourwebsite.com/wp-cron.php?doing_wp_cron > /dev/null 2>&1


2 faz referencia ao segundo descritor de arquivos do processo, stderr.

> significa redirecionamento.

&1 sgnifica que o alvo do redirecionamento deve ser o mesmo do primeiro descritor de arquivo, stdout

Portanto esse comando primeiro redireciona o stdout para /dev/null  e em seguida redireciona o stderr para para o primereiro descritor. Isso acaba silenciando o comando com eficiencia.

O mesmo comando acima poderia ser escrito dessa forma

	wget -q -O - http://yourwebsite.com/wp-cron.php?doing_wp_cron &> /dev/null

Já que o `&` faz referencia aos dois descritores stdin e stdout.


However be careful here! Writing:

command >file 2>&1
Is not the same as writing:

$ command 2>&1 >file
The order of redirects matters in bash! This command redirects only the standard output to the file. The stderr will still print to the terminal. To understand why that happens, let's go through the steps again. So before running the command the file descriptor table looks like this:

![IMAGE ALT TEXT HERE](http://www.catonmat.net/images/bash-redirections/initial-fd-table.png)



Now bash processes redirections left to right. It first sees 2>&1 so it duplicates stderr to stdout. The file 
descriptor table becomes:

![IMAGE ALT TEXT HERE](http://www.catonmat.net/images/bash-redirections/duplicate-stderr-stdout.png)



Now bash sees the second redirect >file and it redirects stdout to file:

![IMAGE ALT TEXT HERE](http://www.catonmat.net/images/bash-redirections/duplicate-stderr-stdout-stdout-file.png)



Do you see what happens here? Stdout now points to file but the stderr still points to the terminal! Everything that gets written to stderr still gets printed out to the screen! So be very, very careful with the order of redirects!


Also note that in bash, writing this:

$ command &>file
Is exactly the same as:

$ command >&file
The first form is preferred however.


Redirect a bunch of text to the stdin of a command

$ command <<EOL
your
multi-line
text
goes
here
EOL
Here we use the here-document redirection operator <<MARKER. This operator instructs bash to read the input from stdin until a line containing only MARKER is found. At this point bash passes the all the input read so far to the stdin of the command.

Here is a common example. Suppose you've copied a bunch of URLs to the clipboard and you want to remove http:// part of them. A quick one-liner to do this would be:

$ sed 's|http://||' <<EOL
http://url1.com
http://url2.com
http://url3.com
EOL

Redirect a single line of text to the stdin of a command

$ command <<< "foo bar baz"
For example, let's say you quickly want to pass the text in your clipboard as the stdin to a command. Instead of doing something like:

$ echo "clipboard contents" | command
You can now just write:

$ command <<< "clipboard contents"
This trick changed my life when I learned it!



## xargs

Pega a saida padrão de um comando e joga cada linha dessa saida como argumento para um proximo comando veja o exemplo abaixo. o xargs é muito utilziado com o find.

Procuramos o arquvivo "ping.\*".

	find ./ -name "ping.*"
	./ping.google.log
	./ping.local.log

Como podemos ver acima dois resultados foram encontrados, ou seja duas linhas cserão passadas para o comando `ls` abaixo:
 	
	find ./ -name "ping.*" | xargs ls -lah
	-rw-rw-r-- 1 alphabraga alphabraga 1,8K May 22 10:19 ./ping.google.log
	-rw-rw-r-- 1 alphabraga alphabraga 1,2K May 22 10:19 ./ping.local.log


Execução de comandos dentro de strings

Podemos executar o comando uname e pegar sua saida e jogar na string dessa forma:

	$echo "Eu gosto de "`uname -s`
	Eu gosto de Linux

Ou assim:

	$echo "Eu gosto de "$(uname -s)
	Eu gosto de Linux

Termos e Utilitários:

* [tee]
* [xargs]