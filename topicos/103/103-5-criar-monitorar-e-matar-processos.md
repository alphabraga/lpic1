---
layout: page
title: 103.5 Criar Monitorar e Matar Processos
permalink: 103/103.5-criar-monitorar-e-matar-processos
---


Ter a capacidade de realizar gerenciamento de báciso de processos.

Executar processos em `foreground` e `background`.
Fazer com que um progtrama continue sua execução mesmo apos o logoff do usuário que executou o mesmo
Monitorar processos ativos
Selecionae e ordenar procesos para a visualização
Enviar sinais para processos

## &

Ao executar um comando podemos colocar um `&` no final do comando para colocar o mesmo em execução em `background`. Abaixo podemos observar que o comando `ping` esta sendo executado em `background`, porem o output do comando continua saindo para p terminal. O que de certa forma pode prejudicar a execução de outros comandos, já que a intenção é mandar um determinado comando para ser execudo em background e ficar com o `bash` para a execução de outros comandos. 

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ping 127.0.0.1  & </code>
[1] 4364
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.053 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.054 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.067 ms
</pre>

Para contornar essa situação podemos colocar todos as saídas para o `/dev/null` e assim o terminal fica livre.


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ping 127.0.0.1 &> /dev/null &</code>
[1] 4364
</pre>

## jobs

Comando `jobs` exibe todos os comando em execução em background 

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>jobs</code>
[1]-  Executando              ping 8.8.8.8 &> /dev/null &
[2]+  Executando              ping 127.0.0.1 &> /dev/null &
</pre>

Com a opção `-l` são exibidos os PIDS dos processos.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>jobs -l</code>
[1]-  6005 Executando              ping 127.0.0.1 &> /dev/null &
[2]+  6007 Executando              ping 8.8.8.8 &> /dev/null &
</pre>




## bg

O comando bg joga um comando para background. Ao executar o comando `gnome-calculator` o mesmo fica ocupando a sessão do terminal impedindo a execução de outros comandos. Mas podemos fazer a uma pausa em sua execução utilizando as teclas `CTRL+Z`, dessa forma o comando sera `STOPED` como podemos ver abaixo:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>gnome-calulator</code>
^Z
[3]+  Parado                  gnome-calculator
</pre>

Podemos observar que o mesmo esta parado

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>jobs -l</code>
[1]   6005 Executando              ping 127.0.0.1 &> /dev/null &
[2]-  6007 Executando              ping 8.8.8.8 &> /dev/null &
[3]+  6855 Parado                  gnome-calculator
</pre>


Executando o comando `bg` o mesmo é jogado em background e sua execução é continuada. 

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>bg</code>
</pre>

Nesse caso podemos utilizar o `bg +` ou ate mesmo o `bg 3`, como no fg.

## fg

O comando `fg` pega um comando que esta em background e joga o mesmo para o foreground.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>jobs</code>
[1]-  Executando              ping 8.8.8.8 &> /dev/null &
[2]+  Executando              ping 127.0.0.1 &> /dev/null &
<code>fg %1</code>
ping 8.8.8.8 &> /dev/null
</pre>

O sinal de `%` pode ser omitido docomando bg.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>jobs</code>
[1]-  Executando              ping 8.8.8.8 &> /dev/null &
[2]+  Executando              ping 127.0.0.1 &> /dev/null &
<code>fg 1</code>
ping 8.8.8.8 &> /dev/null
</pre>

Podemos também chamar um determinado comando usando o sinal de `+` ou `-`. Dessa forma com o `+`:



<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>fg +</code>
ping 127.0.0.1 &> /dev/null
</pre>

Com o `-`:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>fg -</code>
ping 8.8.8.8 &> /dev/null
</pre>

## kill


## nohup

 O comando `nohup` ignora o sinal de `HUP` (hang up), fazendo com que seja possivel executar comandos em background ate mesmo se o terminal acabar, no caso um logoff.

O comando abaixo vai continuar em execução mesmo que o terminal seja fechado ou o usuário faça logoff.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>nohup ping 127.0.0.1 &> /dev/null &</code>
[1] 4364
</pre>

## ps

Exibe informações sobre processos em execução.

## top

Exibe informações sobre processos em execução.

## free

Exibe informações sobre a memória volátil do sistema.

## uptime

O comando `uptime` informa quanto tempo a máquina esta ligada.


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>uptime --help</code>
Usage:
 uptime [options]

Options:
 -p, --pretty   show uptime in pretty format
 -h, --help     display this help and exit
 -s, --since    system up since
 -V, --version  output version information and exit

For more details see uptime(1).
</pre>

Sem argumentos:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>uptime</code>
11:06:53 up 1 day,  2:41,  1 user,  load average: 0,07, 0,11, 0,09
</pre>

COm o output mais bonito.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>uptime -p</code>
up 1 day, 2 hours, 42 minutes
</pre>

Ligado desde:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>uptime -s</code>
2018-04-09 08:25:03
</pre>

Para ver a versão do comando:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>uptime -V</code>
uptime from procps-ng 3.3.10
</pre>



## pgrep

<div class="label-error">Falta conteudo aqui</div>

## pkill


## killall


## screen

