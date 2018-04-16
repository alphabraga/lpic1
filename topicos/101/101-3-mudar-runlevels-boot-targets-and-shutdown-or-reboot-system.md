---
layout: page
title: Mudar runlevels boot targets e desligar ou reiniciar o sistema (Peso 3)
permalink: /101/101-3-mudar-runlevels-boot-targets-and-shutdown-or-reboot-system
---

* Definir o `runlevel` padrão ou o `target` do `boot`
* Mudar entre `runlevels` e `boot targets` incluindo o `single user mode`
* Desligar e reiniciar a maquina pela linha de comando
* Alertar usuários antes de mudar de `runlevels` ou `boot target` ou ate mesmo em outros eventos considerados importantes.
* Finalizar processos de modo correto


## wall

Esse comando realiza o envio de mensagem para todos os usuários logados no sistema. Segundo o man:

> wall - escreve mensagens para todos os usuários

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>wall</code>	
Oi, eu sou o Goku
\< CTRL+D\>
</pre>

Essa mensagem é enviada para todos os usuarios logados na máquina

## shutdown

Esse comando realiza o desligamento e ate mesmo a reiniclização da máquina.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown now</code>	
</pre>

O comando acima desliga a máquina imediatamente

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown now -r</code>	
</pre>


## -H, --halt
Da um Halt na maquina.

## -P, --poweroff
Power-off the machine (the default).

## -r, --reboot
Reboot the machine.

## -h
Equivalent to --poweroff, unless --halt is specified.

## -k
Do not halt, power-off, reboot, just write wall message.

## --no-wall
Do not send wall message before halt, power-off, reboot.

## -c
Cancela um shutdown pendente. Esse comando evita que que um comando de desligamento seja executado caso claro ele não seja invocado com os agrumantos "now" ou "+0"

<pre class="language-bash command-line">
<code>shutdown +2</code>
Shutdown scheduled for Mon 2018-04-16 16:13:27 -03, use 'shutdown -c' to cancel.
<code>shutdown -c</code>
</pre>

## /etc/inittab

Esse arquivo contem informações sobre o runlevel padrão do sistema

## runlevel

Para ver seu runlevel atual basta digitar

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>runlevel</code>
N 5
</pre>

## init

Esse comando realiza a alteração de run level

## telinit

Esse comando realiza a alteração de run level

## /etc/init.d/

## systemd


## systemctl


## /etc/systemd


## /usr/lib/systemd