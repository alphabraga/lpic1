---
layout: page
title: 107.1 Automatize Tarefas administrativas agendando rotinas
permalink: /107/107-2-automatize-tarefas-adiministrativas-agendando-rotinas
---

Candidatos devem ser a habilidade de utilizar o cron e o anacron para executar tarefas em intervalos regulares e também para executar tarefas em momentos expecificos.

Gerenciar tarefas no `cron`.

Configurar acesso de usuários no cron e serviços

Configurar o anacron

## /etc/cron.{d,daily,hourly,monthly,weekly}/


## /etc/at.deny


## /etc/at.allow


## /etc/crontab

O arquivo `contrab` é chamado tambem de cron do sistema e só pode ser editado pelo usuário root. E Nesse arquivo podemos definir na sexta coluna o nome do usuário quevai executar aquela tarefa agendada

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



## /etc/cron.allow


## /etc/cron.deny


## /var/spool/cron/


## crontab


## at


## atq


## atrm


## anacron


## /etc/anacrontab