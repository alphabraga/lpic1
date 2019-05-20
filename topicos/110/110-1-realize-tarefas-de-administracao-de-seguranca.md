---
layout: page
title: 110.1 Realize Tarefas de Administração de Segurança
permalink: /110/110-1-realize-tarefas-de-administracao-de-seguranca
---

* Candidatos devem ter capacidade de rever configurações para garantir segurança do host em concordância com políticas de segurança locais.
* Auditar um sistema para encontrar arquivos com o suid ou sgid setado.
* Setar ou mudar senhas de usuários. 
* Definir ou alterar senhas de usuários e informações sobre o envelhecimento da senha.
* Ser capaz de utilizar o 'nmap' e o `netstat` para descobrir portas abertas em um sistema.
* Configurar limites em logins de usuários, processos e utilização de memória
* Determinar que usuários realizaram login em um sistema ou os que estão logados atualmente
* Utilização e configuração básica do sudo

## find

Podemos utilizar o comando `find` para buscar arquivos com permissões que podem identificar falhas de segurança como arquivos que não deveriam ter determinadas permissões.

## passwd

Utilizado para mudar a senha de usuário. Para mais informações sobre esse comando ver a sessão 107.1

## fuser


## lsof

Serve pra exibir detalhes sobre determinado processos que estão utilizando determinada porta.

No comando abaixo estamos exibindo dados do processo que esta utilizando a porta `3306`.

<pre class="language-bash command-line">
<code>lsof -i :3306</code>
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mysqld  1157 mysql   23u  IPv4  26650      0t0  TCP xxxx.server.com:mysql (LISTEN)
</pre>


## nmap

O `nmap` realiza um scan nas porta de um determinado host. No exemplo abaixo vamos exibir as portas que estão abertas no localhost:


<pre class="language-bash command-line">
<code>nmap localhost</code>
Starting Nmap 7.01 ( https://nmap.org ) at 2018-08-09 23:42 -03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000040s latency).
rDNS record for 127.0.0.1: grafana.lig16.com
Not shown: 997 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
3306/tcp open  mysql
4000/tcp open  remoteanything

</pre>


## chage


## netstat


## sudo


## /etc/sudoers

É um arquivo onde são encontradas as configurações de segurança do utilitário sudo. O mais indicado é a edição desse arquivo com o programa `visudo`.

## su

O comando `su` possibilita realizar o login ou troca de um usuário no sistema. No exemplo abaixo vamos realizar o login do usuario `joao`.


<pre class="language-bash command-line" data-user="carlos" >
<code>su joao</code>
senha: [informar a senha]
</pre>

É importante resaltar, que dessa forma, os arquivos configuração de ambiente como `/etc/profile`, `~/bash_profile` não são executados e por consequência as configurações e variáveis de ambiente não são criadas nesse ambiente. Para que isso seja realziado com o uso do `su` devemos utilizar com o `-`, desse forma:

<pre class="language-bash command-line" data-user="carlos" >
<code>su - joao</code>
senha: [informar a senha]
</pre>

Assim as variáveis de ambiente de demais configurações ficam disponíveis nesse shell.

## usermod


## ulimit


## who 

Mosta informações dos usuários logados:

	# who
	alphabraga tty7         2019-01-26 16:23 (:0)
	blue ~ # who -a
	           system boot  2019-01-26 16:22
	           run-level 5  2019-01-26 16:22
	LOGIN      tty1         2019-01-26 16:22              1451 id=tty1
	alphabraga + tty7         2019-01-26 16:23  old         1695 (:0)

Com os parametros `-a` são exibidas mais informações e com o `-H` é exibido um header. 

	# who -aH
	NAME       LINE         TIME             IDLE          PID COMMENT  EXIT
	           system boot  2019-01-26 16:22
	           run-level 5  2019-01-26 16:22
	LOGIN      tty1         2019-01-26 16:22              1451 id=tty1
	alphabraga + tty7         2019-01-26 16:23  old         1695 (:0)

## w 

Tem a mesma funcionalidade o `who`, mas ele exibe mais informações como o que o usuário esta fazendo, ou melhor, que comando ele esta executando.

	# w
	 17:12:12 up 49 min,  1 user,  load average: 0,48, 0,73, 0,92
	USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
	alphabra tty7     :0               16:23   49:22   3:20   6.29s cinnamon-session --session cinnamon


## last

Lista o últimos logins realizados com sucesso. O `last` realiza a busca dessas informações no arquivo `/var/log/wtmp` (ou você pode definir o arquivo que deseja realizar a busca com a opção `-f`) e exibe uma lista com todos os usuários logados e que sairam desde sua criação.


	# last
	alphabra tty7         :0               Sat Jan 26 16:23    gone - no logout
	reboot   system boot  4.10.0-38-generi Sat Jan 26 16:22   still running
	alphabra tty7         :0               Fri Jan 25 23:15 - crash  (17:06)
	reboot   system boot  4.10.0-38-generi Fri Jan 25 23:15   still running
	alphabra tty7         :0               Wed Jan 23 23:54 - crash (1+23:21)
	reboot   system boot  4.10.0-38-generi Wed Jan 23 23:54   still running
	alphabra tty7         :0               Wed Jan 23 17:17 - down   (06:09)
	reboot   system boot  4.10.0-38-generi Wed Jan 23 17:17 - 23:26  (06:09)
	alphabra tty7         :0               Wed Jan 23 15:39 - crash  (01:37)
	reboot   system boot  4.10.0-38-generi Wed Jan 23 15:38 - 23:26  (07:47)
	alphabra tty7         :0               Tue Jan 22 23:01 - crash  (16:37)
	reboot   system boot  4.10.0-38-generi Tue Jan 22 23:00 - 23:26 (1+00:26)
	alphabra tty7         :0               Tue Jan 22 09:12 - down   (02:44)
	reboot   system boot  4.10.0-38-generi Tue Jan 22 09:12 - 11:57  (02:44)
	alphabra tty7         :0               Mon Jan 21 23:31 - crash  (09:40)
	reboot   system boot  4.10.0-38-generi Mon Jan 21 23:31 - 11:57  (12:25)
	alphabra tty7         :0               Mon Jan 21 21:30 - crash  (02:01)
	reboot   system boot  4.10.0-38-generi Mon Jan 21 21:29 - 11:57  (14:27)
	alphabra tty7         :0               Sun Jan 20 23:23 - crash  (22:06)
	reboot   system boot  4.10.0-38-generi Sun Jan 20 23:23 - 11:57 (1+12:33)
	alphabra tty7         :0               Sun Jan 20 23:02 - crash  (00:20)
	reboot   system boot  4.10.0-38-generi Sun Jan 20 23:02 - 11:57 (1+12:54)
	alphabra tty7         :0               Sun Jan 20 12:28 - 12:48  (00:19)
	reboot   system boot  4.10.0-38-generi Sun Jan 20 12:28 - 12:48  (00:19)
	alphabra tty7         :0               Sun Jan 20 00:20 - crash  (12:08)
	reboot   system boot  4.10.0-38-generi Sun Jan 20 00:20 - 12:48  (12:28)




O `last` realiza a busca dessas informações no arquivo `/var/log/wtmp` (ou você pode definir o arquivo que deseja realizar a busca com a opção `-f`) e exibe uma lista com todos os usuários logados e que sairam desde sua criação.

Veja o exemplo de utilização abaixo:

<pre class="language-bash command-line">
<code>last</code>
alphabra tty7         :0               Thu Aug  9 21:34    gone - no logout
reboot   system boot  4.10.0-38-generi Thu Aug  9 21:30   still running
alphabra tty7         :0               Thu Aug  9 18:06 - down   (01:01)
reboot   system boot  4.10.0-38-generi Thu Aug  9 18:06 - 19:08  (01:01)
alphabra tty7         :0               Wed Aug  8 22:30 - crash  (19:36)
reboot   system boot  4.10.0-38-generi Wed Aug  8 22:30 - 19:08  (20:37)
alphabra tty7         :0               Wed Aug  8 20:05 - crash  (02:25)
</pre>

Com o parâmetro -a lista mais informações.


<pre class="language-bash command-line">
<code>last</code>
alphabra tty7         Thu Aug  9 21:34    gone - no logout  :0
reboot   system boot  Thu Aug  9 21:30   still running      4.10.0-38-generic
alphabra tty7         Thu Aug  9 18:06 - down   (01:01)     :0
reboot   system boot  Thu Aug  9 18:06 - 19:08  (01:01)     4.10.0-38-generic
alphabra tty7         Wed Aug  8 22:30 - crash  (19:36)     :0
reboot   system boot  Wed Aug  8 22:30 - 19:08  (20:37)     4.10.0-38-generic
alphabra tty7         Wed Aug  8 20:05 - crash  (02:25)     :0
reboot   system boot  Wed Aug  8 20:05 - 19:08  (23:02)     4.10.0-38-generic

</pre>

## lastb

O `lastb` é similar ao `last`, exeto que por padrão busca as informações do arquivo de log `/var/log/btmp` que contêm todas as informações de tentativas de login mal sucedidas (ou `bad` login attemps).

No linux Mint o `lastb` é um link para o `last`:

<pre class="language-bash command-line">
<code>ls -la /usr/bin/lastb</code>
lrwxrwxrwx 1 root root 4 May 16 12:00 /usr/bin/lastb -> last
</pre>


## lastlog