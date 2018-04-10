---
layout: page
title: 103.6 Alterar a Prioridade de Execução de Processos (Peso 2)
permalink: /103/103-6-alterar-a-prioridade-de-execucao-de-processos
---

Candidatos devem ter a capacidade de gerenciar a prioridade de processos.


* Saber a prioridade padrão de um `job` que foi criado
* Executar um programa com maioor ou menor prioridade que a padrão
* Mudar a prioridade de um processo em execução

Termos e Utilitários:

## ps

O `ps` é um `Snapshot` de Processos em execução. Com o `ps` é possível visualizar a prioridade dos processos. Para isso utilizamos a opção `-l`.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>ps -l</code>
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 S  1000  9850  7589  0  80   0 -  5683 wait   pts/18   00:00:00 bash
4 R  1000  9860  9850  0  80   0 -  7240 -      pts/18   00:00:00 ps
</pre>

A prioridade é exibida na coluna NI, o processo bash e ps possuem a mesma prioridade `0`.


## top

O comando top também exibir a prioridade de um processo.


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>top</code>
top - 22:44:54 up  3:19,  1 user,  load average: 0,63, 0,95, 1,00
Tarefas: 225 total,   1 executando, 224 dormindo,   0 parado,   0 zumbi
%Cpu(s):  0,8 us,  0,1 sy,  0,0 ni, 99,2 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  3932988 total,   254544 free,  1607880 used,  2070564 buff/cache
KiB Swap:  4086780 total,  4086780 free,        0 used.  1548744 avail Mem 

  PID USUÁRIO  PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                             
 1066 root      20   0  652212 187600 158832 S   2,7  4,8   2:53.38 Xorg                                                                
 2029 alphabr+  20   0 1542272 194640  66968 S   1,7  4,9   2:46.47 compiz                                                              
 7589 alphabr+  20   0  663300  37796  29096 S   1,7  1,0   0:03.77 gnome-terminal-                                                     
  196 root      -2   0       0      0      0 S   0,3  0,0   0:02.17 i915/signal:0                                                       
 1899 alphabr+  20   0  664508  47656  31296 S   0,3  1,2   0:06.60 hud-service                                                         
 2108 alphabr+  20   0  886748  36848  30252 S   0,3  0,9   0:06.60 nm-applet                                                           
 2615 alphabr+  20   0 1297152 259912 131092 S   0,3  6,6   4:54.04 chrome                                                              
 9215 root      20   0       0      0      0 S   0,3  0,0   0:00.22 kworker/1:1                                                         
    1 root      20   0  185304   5964   4032 S   0,0  0,2   0:01.64 systemd                                                             
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                            
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                 
</pre>


Da mesma forma que o ps é a coluna `NI` que exibe as informações sobre a prioridade dos processos. 


## Níveis de prioridades


Esses são os niveis de prioridade de processos:


	[-20 .. 0 .. +19]


* Quanto menor o número acima, maior a prioridade.
* Ao executar normalmente um processo (sem chamar o nice) por padrão o processo tem prioridade `0`.
* Ao executar um processo chamando o nice (Ex: `nice firefox`) ele vai começar com prioridade `10`.
* Um usuário comum pode apenas diminuir a prioridade de seus processos.
* O root pode aumentar e diminuir a prioridade de um processo.
* Apenas o root pode atribuir valores negativos de `nice` a processos.


## nice

Com o `nice` você pode executar um programa com uma prioridade diferente da padrão. Ou seja maior ou menor.

O comando abaixo ira executar o firefox com prioridade `15`. Ou seja um prioridade baixa.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>nice -n 15 firefox</code>
</pre>

O comando abaixo é igual ao anterior. Apenas o `-n` foi omitido.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>nice -15 firefox</code>
</pre>


Com o comando top podemos visualizar o nice desse programa:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>top</code>
top - 22:59:04 up  3:33,  1 user,  load average: 0,85, 1,06, 1,04
Tarefas: 231 total,   1 executando, 230 dormindo,   0 parado,   0 zumbi
%Cpu(s):  0,4 us,  1,0 sy,  3,0 ni, 95,4 id,  0,0 wa,  0,0 hi,  0,2 si,  0,0 st
KiB Mem :  3932988 total,   146528 free,  1849584 used,  1936876 buff/cache
KiB Swap:  4086780 total,  4086780 free,        0 used.  1245840 avail Mem 

  PID USUÁRIO  PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                             
11174 alphabr+  35  15 2232580 270100 140000 S   7,0  6,9   0:09.03 firefox                                                             
11289 alphabr+  35  15 1751416 152908  98200 S   7,0  3,9   0:04.59 Web Content                                                         
 1064 root      20   0  893972  27884   9124 S   0,7  0,7   0:03.09 core                                                                
 2029 alphabr+  20   0 1542412 194784  67048 S   0,3  5,0   3:34.21 compiz                                                              
 2085 alphabr+  20   0  772292  25452  15516 S   0,3  0,6   0:11.54 core                                                                
 2111 alphabr+  20   0 1333584 109268  84432 S   0,3  2,8   0:18.05 nautilus      

</pre>

Para colocar prioridades negativas (alta prioridade) temos que fazer isso como usuário root.

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>nice -n -15 firefox</code>
</pre>

Podemos tambem claro omitir o `-n`

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>nice --15 firefox</code>
</pre>


## renice

Alterar a prioridade de processos em execução

O comando abaixo ira alterar o nice do processo `20159`.

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice -n 15 20159</code>
</pre>

Podemos omitir o `-n`. Observe que no `renice` removemos por completo, não fica o `-` como no `nice`.

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice 15 20159</code>
</pre>


Para atriuir um valor negativo omitindo o `-n`

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice 15 20159</code>
</pre>

Um valor negativo fica assim:

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice -15 20159</code>
</pre>


Podemos alterar a prioridade de processos baseados no usuario, assim:

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice -u alphabraga -n 15</code>
</pre>


Ou do grupo

<pre class="command-line language-bash" data-user="root" data-host="localhost">
<code>renice -g developers -n 15</code>
</pre>

