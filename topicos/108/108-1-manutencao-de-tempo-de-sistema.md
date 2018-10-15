---
layout: page
title: 108.1 Manutenção de Tempo do Sistema (Peso 3)
permalink: /108/108-1-manutencao-de-tempo-de-sistema
---

Habilidade para manter o sistema de tempo e sincronizar o relógio pelo NTP.


* Setar a data e tempo no sistema
* Setar o relogio do hardware para o tempo correto em `UTC`
* Configurar o timezone correto
* Configuração básica de NTP
* Conhecimento em utilizar o serviço  depool.ntp.org
* Conhecimento em utilizar o comando ntpq


### Introdução

No linux existem dois tipo de relógios. O relógio de hardware, também conhecido como relógio da bios. Após o boot do linux o software clock assume. Existem comandos para exibir esses dois horários.

### Comando `date`

O comando mais commum é o `date` que exibe a data e horário de software, esse comando pode ser executado por qualquer usuário, abaixo a execução do comando sem nenhum argumento:

<pre class="language-bash command-line" >
<code>date</code>
Mon Oct 15 14:48:47 -03 2018
</pre>

Podemos passar também o parametro `-u`, que é o horário coordenado universal (UTC), com GMT 0:

<pre class="language-bash command-line" >
<code>date -u</code>
Mon Oct 15 18:10:20 UTC 2018
</pre>

É possivel formatar o output com parametros, abaixo vamos exibir apenas o ano corrente:

<pre class="language-bash command-line" >
<code>date +%Y</code>
2018
</pre>

Agora com a data completa:

<pre class="language-bash command-line" >
<code>date +%d/%m/%Y</code>
15/10/2018
</pre>

Agora apenas o horário:

<pre class="language-bash command-line" >
<code>date +%H:%M:%S</code>
15:19:30
</pre>

O comando `date` além de exibir a data e horário **também pode alterar esses dados**.

Para alterar a data usamos o comando da seguinte forma:

<pre class="language-bash command-line" >
<code>sudo date MMDDHHMMYYYY</code>
</pre>

Substituindo as letras pelos dados correspondentes, dessa forma podemos mudar a data para o dia 13/12/2018 12:00. Ficaria assim:

<pre class="language-bash command-line" >
<code>sudo date 121312002018</code>
</pre>

### Comando `hwclock`

Já o comando `hwclock` exibe dados de horário do hardware e só pode ser executado pelo `root`. Abaixo o comando sendo executado por um usuário comum:

<pre class="language-bash command-line">
<code>hwclock</code>
hwclock: Sorry, only the superuser can use the Hardware Clock.
</pre>

Agora o comando executado pelo `root`:

<pre class="language-bash command-line" data-user="root">
<code>hwclock</code>
Seg 15 Out 2018 14:54:36 -03  .076655 seconds
</pre>


Para setar uma outra data para o horário de máquina, usamos o comanod abaixo:

<pre class="language-bash command-line" data-user="root">
<code>hwclock --set --date "MM/DD/YYYY HH:MM"</code>
</pre>

Supondo que queremos alterar a data para 31/12/2018 01:00 o comando ficaria assim:

<pre class="language-bash command-line" data-user="root">
<code>hwclock --set --date "12/31/2018 01:00"</code>
</pre>


É aceitável que exista uma diferença de tempo entre esses dois comandos;

Mas caso o administardor deseja sincronizar esses horários podemos realizar isso de duas formas. Igualar o horário do hardware com o software, ou pegar os dados do software e atualizar o hardware.

### Sincronizar, copiando do software para o hardware

<pre class="language-bash command-line" data-user="root">
<code>hwclock -w</code>
</pre>

Ou usando o comando extendido:

<pre class="language-bash command-line" data-user="root">
<code>hwclock --systohc</code>
</pre>

### Sincronizar, copiando do hardware para o software

<pre class="language-bash command-line" data-user="root">
<code>hwclock -s</code>
</pre>

Ou usando o comando extendido:

<pre class="language-bash command-line" data-user="root">
<code>hwclock --hctosys</code>
</pre>


* /usr/share/zoneinfo/
* /etc/timezone
* /etc/localtime
* /etc/ntp.conf
* date
* hwclock
* ntpd
* ntpdate
* pool.ntp.org