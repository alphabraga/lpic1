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


## su

O comando `su` possibilita realizar o login de um usuário no sistema. No exemplo abaixo vamos realizar o login do usuario `joao`.


<pre class="language-bash command-line" data-user="carlos" >
<code>su joao</code>
senha: [informar a senha]
</pre>

É importante resaltar, que dessa forma, os arquivos configuração de ambiente como `/etc/profile`, `~/bash_profile` não são executados e por consequência as configurações e variáveis de ambeinte não são criadas nesse ambiente. Para que isso seja realziado com o uso do `su` devemos utilizar com o `-`, desse forma:

<pre class="language-bash command-line" data-user="carlos" >
<code>su - joao</code>
senha: [informar a senha]
</pre>

Assim as variaveis de ambeinte de demais configurações ficam disponiveis nesse shell.

Using su without -l or - starts bash as an interactive, but non-login shell, which doesn't read from either of the files you specified. Use the -l or - option or put the relevant config into /root/.bashrc.

Quick summary of config files:

Login shell (-l/--login) reads /etc/profile first, and then the first it finds of: ~/.bash_profile, ~/.bash_login, and ~/.profile.
Interactive but non-login shell (-i) reads /etc/bash.bashrc and ~/.bashrc, in that order (unless the --rcfile option is used and tells it to look elsewhere).
Non-interactive shells, e.g. started from within another program without using the -l or -i flags, reads the file specified in the BASH_ENV environment variable.
When run as sh as a login shell, it will read /etc/profile and ~/.profile, in that order.
When run as sh as an interactive non-login, it reads the file specified in ENV.


## usermod


## ulimit


## who 

## w 

## last

Lista o últimos login realizado com sucesso dos usuários.

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

O `lastb` é similar ao `last`, exeto que por padrão busca as informações do arquivo de log `/var/log/btmp` que contem todas as informações de tentativas de login mal sucedidas (ou `bad` login attemps).

No linux Mint o `lastb` é um link para o `last`:

<pre class="language-bash command-line">
<code>ls -la /usr/bin/lastb</code>
lrwxrwxrwx 1 root root 4 May 16 12:00 /usr/bin/lastb -> last
</pre>




