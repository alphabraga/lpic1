---
layout: page
title: 107.1 Gerencie usuarios e grupos e arquivos de sistema relacionados
permalink: /107/107-1-gerencie-usuarios-e-grupos-e-arquivos-de-sistemas-relacionados
---

Canditatos devem ter a habilidade de adicionar, remover, suspender e mudar contas de usuários.

* Add, modify and remove users and groups
* Manage user/group info in password/group databases
* Create and manage special purpose and limited accounts


## /etc/passwd

E o arquivo que contem as informações de usuarios do sistema. Onde cada linha representa um usuario e os campos são divididos por `:`. Vejamos o arquivo abaixo:

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
2 Coluna
3 Coluna id do usuário no sistema
4 Coluna
5 Coluna
6 Coluna
7 Coluna
8 Coluna
9 Coluna
10 Coluna



## /etc/shadow
## /etc/group
## /etc/skel/
## chage
## getent
## groupadd
## groupdel
## groupmod
## passwd
## useradd
## userdel
## usermod