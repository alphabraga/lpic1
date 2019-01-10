---
layout: page
title: 107.1 Gerencie usuarios e grupos e arquivos de sistema relacionados
permalink: /107/107-1-gerencie-usuarios-e-grupos-e-arquivos-de-sistemas-relacionados
---

Canditatos devem ter a habilidade de adicionar, remover, suspender e mudar contas de usuários.

* Adicione, modifique e remova usuários e grupos;
* Gerenciar informações de usuários e grupos info e banco de dados de senha e grupos;
* Crie e gerencie contas de usuários com propósito especial e contas limitadas;

## id

O comando `id` exibe as informações sobre o usuário logado na sessão. O comando exibe os IDs de usuário e grupos ao qual ele pertence.

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

* 1 - Login
* 2 - Representa a senha que hoje fica no arquivo `passwd`
* 3 - Id do usuário
* 4 - Id do Grupo default do usuário
* 5 - Informações do usuário
* 6 - Diretório padrão do usuário 
* 7 - Shell padrão do usuário

Os usuários comuns do sistema possuem id apartir de 1000. Antes de 1000 são usuários de sistema.

O arquivo /etc/passwd deve ser editado usando o comando `vipw` que abre o editor de texto padrão e bloqueia a edição concorrente do arquivo evitando assim a possivel corrupção do arquivo.

## /etc/shadow

O arquivo `/etc/shadow` contém as senhas dos usuários do sistema. Antes elas ficavam no `passwd`.

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

Assim como o `passwd` o arquivo `/etc/shadow`, cada linha corresponde a senha do usuário onde as colunas são divididas por `:` 

* 1: coluna é o nome do usuário, que deve corresponder a um nome de usuário válido no passwd
* 2: é um hash que representa a senha. `*` significa que a conta esta bloqueada para login, um ` ` (espaço) significa que  aconta pode ser acessada sem senha
* 3: representa o número de dias desde 01/01/1970 que a senha foi alterada 
* 4: número minimo de dias para que a senha possa ser alterada
* 5: número de dias depois dos quais a senha TEM QUE SER ser alterada, por padrão o valor é 99999
* 6: número de dias para informar ao usuário que a senha TEM QUE SER ALTERADA
* 7: número de dias depois da senha ter sido expirada, ate que a conta seja bloqueada
* 8:O número de dias, a partir de 0 1 10 1 / 1 970, desde que a conta foi bloqueada;
9. Campo reservado.

O `/etc/shadow` pode ser tambem editado de forma segura, usando o comando `vipw` com o parametro `-s`:

	$ vipw -s


## pwconv

Esse comando converte uma senha que esta no arquivo passwd para o shadow

## pwunconv

Esse comando converte uma senha que esta no arquivo shadow para o passwd

## /etc/group

O arquivo que armazena os dados sobre os grupos do sistema. 

* 1 coluna com o nome do grupo
* 2 a senha do usuário
* 3 o id do grupo
* 4 os usuários que fazem parte do grupo separados por virgula.

	sys:x:3:
	adm:x:4:syslog,alphabraga
	tty:x:5:
	disk:x:6:
	lp:x:7:
	mail:x:8:
	news:x:9:
	uucp:x:10:
	man:x:12:
	proxy:x:13:
	kmem:x:15:
	dialout:x:20:
	fax:x:21:
	voice:x:22:



## /etc/login.defs

É um arquivo que contem varias configurações relativas a usuários como:

### criação do diretório home de forma automatica 

	CREATE_HOME	yes

### Faixa de UID para usuários comuns do sistema

	UID_MIN                  1000
	UID_MAX                 60000


## /etc/skel/

é o diretorio que é copiado para todo novo usuário criado com o comando `useradd` utizando a opção `-m`



## chage

Mostra e muda as informações do usuário. Apenas o root pode ver e mudar as informações de todos os usuários do sistema.

Utilização

	$ chage [options] LOGIN

* -m dias : mínimo de dias até que o usuário possa trocar uma senha modificada;
* -M dias : número máximo de dias que a senha permanecerá válida;
* -d dias  : número de dias decorridos em relação a 0 1 /0 1 / 1 970. Determina quan­
do a senha foi mudada. T arnbém pode ser expresso no formato de data local (dia/mês/ano) ;
* -E dias : número de dias decorridos em relação a 0 1 /0 1 / 1 970, a partir dos quais a conta não estará mais disponível. Também pode ser expresso no for­ mato de data local (dia/mês/ano);
* -I dias : inatividade ou tolerância de dias, após a expiração da senha, para que a conta seja bloqueada;
* -W dias : dias anteriores ao fim da validade da senha, quando será emitido um aviso sobre a expiração da validade.


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

O `useradd` é um comando utilizado pelo root para adicionar novos usuarios no sistema. As informações de usuários ficam no arquivo `passwd`

Opções do `useradd`:

* -c : comentário (informações adicionais do usuário)
* -d : caminho para o diretorio padrão do usuário
* -g : grupo padrão do usuário
* -G : grupos adicionais
* -u : definir o UID
* -s : shell padrão do usuário
* -p : senha do usuário
* -e : data de validade
* -k : copia estrutura de diretorio do /etc/skel
* -m : cria diretorio pessoal, caso o mesmo não exista 



Podemos usar tambem o `adduser` Diversas Definições podem ser preestabelecidas no arquivo `/etc/adduser.conf`. Veja uma parte do arquivo abaixo:

	# /etc/adduser.conf: `adduser' configuration.
	# See adduser(8) and adduser.conf(5) for full documentation.
	# The DSHELL variable specifies the default login shell on your
	# system.
	DSHELL=/bin/bash
	# The DHOME variable specifies the directory containing users' home
	# directories.
	DHOME=/home
	# If GROUPHOMES is "yes", then the home directories will be created as
	# /home/groupname/user.
	GROUPHOMES=no
	# If LETTERHOMES is "yes", then the created home directories will have
	# an extra directory - the first letter of the user name. For example:
	# /home/u/user.
	LETTERHOMES=no
	# The SKEL variable specifies the directory containing "skeletal" user
	# files; in other words, files such as a sample .profile that will be
	# copied to the new user's home directory when it is created.
	SKEL=/etc/skel



## userdel

Serve para apagar uma conta de usuário:

	$userdel alphabraga

Usado com a opção `-r` serve para apagar tambem o diretório pessoal:

	$ userdel -r alphabraga


## usermod