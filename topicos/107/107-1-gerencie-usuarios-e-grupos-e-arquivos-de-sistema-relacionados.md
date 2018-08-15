---
layout: page
title: 107.1 Gerencie usuarios e grupos e arquivos de sistema relacionados
permalink: /107/107-1-gerencie-usuarios-e-grupos-e-arquivos-de-sistemas-relacionados
---

Canditatos devem ter a habilidade de adicionar, remover, suspender e mudar contas de usuários.

* Adicione, modifique e remova usuários e grupos
* Gerenciar informações de usuários e grupos info e banco de dados de senha e grupos
* Crie e gerencie contas de usuários com propostio especial e contas limitadas

## id

O comando `id` exibe as informações sobre o usuário logado na sessão.


<pre class="command-line language-bash">
<code>id</code>
uid=1000(alphabraga) gid=1000(alphabraga) groups=1000(alphabraga),4(adm),24(cdrom),27(sudo)
</pre>

Podemos ainda passar um usuário como parâmetro para visualizar as informações daquele usuário:

<pre class="command-line language-bash">
<code>id www-data</code>
uid=33(www-data) gid=33(www-data) groups=33(www-data)
</pre>

## groups

O comando `groups` tem um comportamento semelhante ao `id`. Só que ele retorna apenas informações sobre os grupos. Veja abaixo que digitando apenas `groups` no terminal é retornado os grupos do usuário logado.

<pre class="command-line language-bash">
<code>groups</code>
usuario1 adm cdrom sudo dip plugdev lpadmin sambashare
</pre>

Ou podemos passar um usuário:

<pre class="command-line language-bash">
<code>groups mysql</code>
mysql : mysql
</pre>



## /etc/passwd

É o arquivo que contêm as informações de usuários do sistema. Onde cada linha representa um usuário e os campos são divididos por `:`. Vejamos o arquivo abaixo:

	lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
	mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
	news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
	uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
	proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
	www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
	backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
	list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
	irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
	gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
	nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
	systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/bin/false
	systemd-network:x:101:103:systemd Network Management,,,:/run/systemd/netif:/bin/false
	systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd/resolve:/bin/false
	systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false
	syslog:x:104:108::/home/syslog:/bin/false
	_apt:x:105:65534::/nonexistent:/bin/false
	messagebus:x:106:110::/var/run/dbus:/bin/false
	uuidd:x:107:111::/run/uuidd:/bin/false
	lightdm:x:108:114:Light Display Manager:/var/lib/lightdm:/bin/false

As colunas são:

1 Coluna login do usuario no sistema 
2 Coluna Representa a senha que hoje fica no arquivo `passwd`
3 Coluna id do usuário no sistema
4 Coluna id do gruopo default do usuário
5 Coluna ???????????????????????????????
6 Coluna diretório padrão do usuário 
7 Coluna o shell padrão do usuário

## /etc/shadow

O arquivo `/etc/shadow` contem as senhas dos usuários do sistema. Antes elas ficavam no `passwd`.

	root:!:17712:0:99999:7:::
	daemon:*:17494:0:99999:7:::
	bin:*:17494:0:99999:7:::
	sys:*:17494:0:99999:7:::
	sync:*:17494:0:99999:7:::
	games:*:17494:0:99999:7:::
	man:*:17494:0:99999:7:::
	lp:*:17494:0:99999:7:::
	mail:*:17494:0:99999:7:::
	news:*:17494:0:99999:7:::
	uucp:*:17494:0:99999:7:::
	proxy:*:17494:0:99999:7:::
	www-data:*:17494:0:99999:7:::
	backup:*:17494:0:99999:7:::
	list:*:17494:0:99999:7:::
	irc:*:17494:0:99999:7:::
	gnats:*:17494:0:99999:7:::
	nobody:*:17494:0:99999:7:::
	systemd-timesync:*:17494:0:99999:7:::
	systemd-network:*:17494:0:99999:7:::
	systemd-resolve:*:17494:0:99999:7:::
	systemd-bus-proxy:*:17494:0:99999:7:::
	syslog:*:17494:0:99999:7:::
	_apt:*:17494:0:99999:7:::
	messagebus:*:17494:0:99999:7:::
	uuidd:*:17494:0:99999:7:::
	lightdm:*:17494:0:99999:7:::
	ntp:*:17494:0:99999:7:::

## /etc/group


## /etc/skel/


## chage

Mostra e muda as informações do usuário. Apenas o root pode ver  e mudar as informações de todos os usuários do sistema.

Abaixo o help do chage:

	Usage: chage [options] LOGIN

	Options:
	  -d, --lastday LAST_DAY        set date of last password change to LAST_DAY
	  -E, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
	  -h, --help                    display this help message and exit
	  -I, --inactive INACTIVE       set password inactive after expiration
	                                to INACTIVE
	  -l, --list                    show account aging information
	  -m, --mindays MIN_DAYS        set minimum number of days before password
	                                change to MIN_DAYS
	  -M, --maxdays MAX_DAYS        set maximim number of days before password
	                                change to MAX_DAYS
	  -R, --root CHROOT_DIR         directory to chroot into
	  -W, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS

Com a opção `-l` listamos as informações de um determinado usuario também passado como parametro:

<pre class="command-line language-bash">
<code>chage -l alphabraga</code>
Last password change					: Jun 30, 2018
Password expires					: never
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 7
</pre>


## getent

O comando `getent` fornece informações de usuários, grupos e elementos de rede.

Para pegar informações de usuarios passamos como parametro o nome `passwd`:

<pre class="command-line language-bash">
<code>getent passwd alphabraga</code>
alphabraga:x:1000:1000:alphabraga,,,:/home/alphabraga:/usr/bin/zsh
</pre>

Para pegar informações de grupos passamos `group`:

<pre class="command-line language-bash">
<code>getent group alphabraga</code>
alphabraga:x:1000:
</pre>

## groupadd


## groupdel


## groupmod


## passwd


## useradd


## userdel


## usermod