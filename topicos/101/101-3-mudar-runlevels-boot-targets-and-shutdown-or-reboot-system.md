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


## shutdown

Esse comando realiza o desligamento e até mesmo a reiniclização da máquina. Vale lembrar que usando o `init 0` para desligar, e o `init 6` para desligar.

Podemos ainda usar o `telinit` para isso, mas esses comandos não realizam operações assessorias como enviar mensagens para os outros usuários que o sistema sera desligado.

O comando pode ser utilizado sem argumentos. Ele desliga a máquina em 1 minuto.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown</code>	
Shutdown scheduled for Thu 2018-05-10 09:45:47 -03, use 'shutdown -c' to cancel.
</pre>

O comando abaixo desliga a máquina imediatamente.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown now</code>	
</pre>

O comando abaixo reinicia a máquina imediatamente.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown now -r</code>	
</pre>


O comando abaixo desliga a máquina às 13:20

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown 13:20</code>	
</pre>

O comando abaixo desliga a máquina em 60 minutos

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown +60</code>	
</pre>

### Poweroff

Poweroff envia um sinal ACPI com instruções para desligar o sistema. Vejamos alguns exemplos:


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>poweroff   	       #poweroff</code>	
</pre>


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>poweroff --halt      #executa um halt</code>	
</pre>

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>poweroff --reboot    #reinicia a máquina</code>	
</pre>


Executa o halt

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>shutdown -H</code>	
</pre>


## -H, --halt

Esse comando desliga o linux mas não a máquina.

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

## halt

O halt instrui o hardware a parar todas as funções de CPU, mais sem desligar. Você pode usá-lo para deixar o sistema em um estado onde você pode executar manutenção de baixo nível.


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>	halt                  # para a máquina</code>	
</pre>

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>halt -p              # executa um poweroff</code>	
</pre>


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>halt --reboot    # reinicia a máquina</code>	
</pre>

## wall

Esse comando realiza o envio de mensagem para todos os usuários logados no sistema. Segundo o man:

> wall - escreve mensagens para todos os usuários

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>wall</code>	
Oi, eu sou o Goku
\< CTRL+D\>
</pre>

Essa mensagem é enviada para todos os usuarios logados na máquina

## /etc/inittab

Esse arquivo contem informações sobre o runlevel padrão do sistema

## runlevel

"Runlevels" são uma forma obsoleta de iniciar e parar grupos de serviços utilizados n SysV init. Systemd disponibiliza uma camada de compatibilidade que mapeia os runlevels para os targets.

Mapeamento entre runlevels e  targets do systemd

Runlevel  Target            

0        poweroff.target   

1        rescue.target     

2, 3, 4  multi-user.target

5        graphical.target 

6        reboot.target    



O comando runlevel exibe o runlevel anterior e o atual. Os dois caracteres são separados por um espaço. Se um desses runlevel não pode ser determinado  letra N é exibida, se os dois não podem ser determinados a palavra "unknown" é exibida.

Na execução do comando abaixo, o runlevel anterior não foi determinado e por isso o N foi exibido. Mas sabemos que o runlevel atual é o 5.

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

Systemd é um gerenciador de sistema e de serviços para o Linux, compativel com o SysV. Systemmd utiliza sockets e D-BUS para inicialização de serviços, oferece a iniciação por demanda de `daemons`, rastreia processos utilizando o controle de grupos do Linux, suporta `snaphotting` e o `restoring` de um determinado estado do sistema.

## systemctl


## /etc/systemd


## /usr/lib/systemd

