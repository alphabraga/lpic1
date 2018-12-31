---
layout: page
title: 107.1 Automatize Tarefas administrativas agendando rotinas
permalink: /107/107-2-automatize-tarefas-adiministrativas-agendando-rotinas
---

Candidatos devem ser a habilidade de utilizar o cron, anacron e o at para executar tarefas em intervalos regulares e também para executar tarefas em momentos expecificos.

* Gerenciar tarefas no `cron`.
* Configurar acesso de usuários no cron e serviços
* Configurar o anacron

## Cron

A cron é um deamon. E por conta disso as tarefas agendadas no cron só são executadas se o mesmo estiver em execução. Execurando o comando abaixo verficamos que o cron esta em execução:


	ps axu | grep cron
	root      1046  0.0  0.0  29012   752 ?        Ss   Dez26   0:00 /usr/sbin/cron -f
	alphabr+ 12915  0.0  0.0  14228   952 pts/1    S+   14:28   0:00 grep --color=auto cron



## /etc/cron.{d,daily,hourly,monthly,weekly}/

Como podemos ver no comando abaixo esses diretorios ficam localizados dentro de `/etc`:

	alphabraga@helix /etc $ ls -ld cron*
	drwxr-xr-x 2 root root 4096 Dez 17 13:11 cron.d
	drwxr-xr-x 2 root root 4096 Dez 27 10:55 cron.daily
	drwxr-xr-x 2 root root 4096 Nov 24  2017 cron.hourly
	drwxr-xr-x 2 root root 4096 Nov 24  2017 cron.monthly
	drwxr-xr-x 2 root root 4096 Ago  1 13:02 cron.weekly

Os scripts cotidos dentro dessas pastas são executados conforme descrição do diretorio. Isso acontece por conta de definições no arquivo `/etc/crontab`. Que pode ser observado melhor na sessão a respeito do contrab.

## /etc/at.deny


## /etc/at.allow


## /etc/crontab

O arquivo `contrab` é chamado tambem de cron do sistema e só pode ser editado pelo usuário root. E nesse arquivo podemos definir na sexta coluna o nome do usuário que vai executar aquela tarefa agendada

	# /etc/crontab: system-wide crontab
	# Unlike any other crontab you don't have to run the `crontab'
	# command to install the new version when you edit this file
	# and files in /etc/cron.d. These files also have username fields,
	# that none of the other crontabs do.

	SHELL=/bin/sh
	PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

	# m h dom mon dow user  command
	17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
	25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
	47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
	52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

### m (Minute)

Nessa coluna é definido o minuto. Valores de 0 a 59.

### h (Hour)

Definda a hora. Os valores vão de 0 à 23.

### dom (Day of Month)

Dia do Mẽs. Os valores vão de 0 à 31.

### mon (Month)

Mês. Os valores vão de 1 à 12.

### dow (Day of Week)

Dia da semana. Os valores vão de 0 à 7, onde:

* 0 e 7 = Dom
* 1 = Seg
* 2 = Ter
* 3 = Qua
* 4 = Qui
* 5 = Sex
* 6 = Sab




## /etc/cron.allow e /etc/cron.deny

É possivel definir que usuários podem agendar tarefas, apenas fazendo o uso dos arquivos `/etc/cron.allow` e `/etc/cron.deny`. 

Esses arquivos não existem por padrão, é preciso criar-los. O arquivo cron.allow tem prioridade frente ao cron.deny, ou seja, se o nome de usuário estiver nos dois arquivos o usuário tera permissão de usar o cron, caso esteja apenas no deny aí sim ele não tera acesso ao cron.Se o arquivo cron.allow estiver vazio nenhum usuario tera acesso. Lembrando que o root não esta incluido nessas regras pois o root sempre tem acesso indepentende de como os arquivos cron.allow e cron.deny estão definidos.

## /var/spool/cron/


## crontab

O comando contab permite a manipulação de agendamento de tarefas de usuários. O aquivo `/etc/crontab` são tarefas globais, tarefas de sistema. Já as tarefas manipuldas pelo comando crontab são do usuário que executa o comando.


A opção `-l` exibe as tarefas agendadas do usuário logado:


	alphabraga@helix ~ $ crontab  -l
	no crontab for alphabraga


Para adcionar, editar ou excluir tarefas do contrab basta utilizar a opção `-e`:

		alphabraga@helix ~ $ crontab  -e


O editor de texto é aberto para a edição do arquivo. Depois de edita-lo, você pode listar o conteudo do mesmo com a opção `-l`: 


	alphabraga@helix ~ $ crontab  -l
	# Edit this file to introduce tasks to be run by cron.
	# 
	# Each task to run has to be defined through a single line
	# indicating with different fields when the task will be run
	# and what command to run for the task
	# 
	# To define the time you can provide concrete values for
	# minute (m), hour (h), day of month (dom), month (mon),
	# and day of week (dow) or use '*' in these fields (for 'any').# 
	# Notice that tasks will be started based on the cron's system
	# daemon's notion of time and timezones.
	# 
	# Output of the crontab jobs (including errors) is sent through
	# email to the user the crontab file belongs to (unless redirected).
	# 
	# For example, you can run a backup of all your user accounts
	# at 5 a.m every week with:
	# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
	# 
	# For more information see the manual pages of crontab(5) and cron(8)
	# 
	# m h  dom mon dow   command

	*/5	*	*	*	*	date >> /tmp/tempo


Caso você for o usuário root você pode ver o corntab de outros usuários do sistema. No exemplo abaixo o usuário root lista o contab do usuário alphabraga:

	crontab -u alphabraga -l

Podemos ainda apagar os dados da crontab com um simples comando. Utilizando a opção `-r`. É possivel ainda combinar com a opção `-u`:

	crontab -r -u alphabraga 

É possivel tambem importar a configuração do corntab direto de um arquivo

## at

O comando `at` serve para agenar uma tarefa no sistema.

	-executes commands at a specified time. (do man do at)


Exemplo de uso do comando at para agendar uma tarefa a meia noite:

## atq


## atrm


## anacron

O cron só funciona se a maquina estiver ligada, cso você tenha um agendamento agendado a cada 1 hora essas tarefas serão perdidas se sua maquina for desligada por algumas horas.

Ao contário do cron que é um daemon, o anacron é executado quando a maquina é iniciada e de tempos em tempos. É comum usar o anacron em máquinas desktop. No anacron não existe agendamento por usuário, por conta disso temos apenas o arquivo `/etc/anacrontab`

## /etc/anacrontab


	# /etc/anacrontab: configuration file for anacron
	# See anacron(8) and anacrontab(5) for details.
	SHELL=/bin/sh
	PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
	HOME=/root
	LOGNAME=root
	# These replace cron's entries
	1       5       cron.daily      run-parts --report /etc/cron.daily
	7       10      cron.weekly     run-parts --report /etc/cron.weekly
	@monthly        15      cron.monthly    run-parts --report /etc/cron.monthly


Na primeira coluna temos o campo `periodo` indicando de quantos em quantos dias uma tarefa sera executada. Na primeira linha temos `1`. Por tanto, o comando sera executado a cada dia e na ultima linha temos `7` dessa forma o comando sera executado a cada 7 dias. Não é possivel definir as horas, a menor unidade de medida é o dia. Podemos usar ainda esses formatos na primeira coluna:

 * @monthy
 * @dayly
 * @weekely

A segunda coluna é o `delay`. Ela define quantos minutos depois da coluna `periodo` ser atingida o comando vai ser exectado.
A terceira coluna é apenas um identificador. Esse identificador serve para identificar a execução de sua tarefa em logs.