---
layout: page
title: 108.2 Sistema de Logs (Peso 3)
permalink: /108/108-2-sistema-de-logs
---

Configurar o serviço do syslog. Esse objetivo também inclui cofngurar o serviço de logs para enviar para um servidor de logs, ou ate mesmo aceitar logs atuando como uma central de logs. Utilizar o systemd joournal subsystem, e conhecimento sobre o rsyslog and syslog-ng como uma alternativa. 

* Configurar o serviço do syslog
* Entender as `standard facilities`, propriedades e ações
* Configuração do `logrotate`
* Conhecimentos de rsyslog e syslog-ng


## Introdução

O syslog é o sistema de gerenciamento padrão de logs (original do linux). Atualmente temos o rsyslog, que é uma verão otimizada do syslogd, o rsyslog é o mais utilizado atualmente. A LPI pede que conheça-mos melhor o syslogd.


## syslog.conf

O arquivo de configuração do syslogd é o `/etc/syslog.conf`. Podem existir ainda arquivos dentro do diretório "/etc/syslog.d".  Veja abaixo o arquivo syslog.conf:

	A configuration file might appear as follows:

	# Log all kernel messages, authentication messages of
	# level notice or higher and anything of level err or
	# higher to the console.
	# Don't log private authentication messages!
	*.err;kern.*;auth.notice;authpriv.none  /dev/console

	# Log anything (except mail) of level info or higher.
	# Don't log private authentication messages!
	*.info;mail.none;authpriv.none          /var/log/messages

	# The authpriv file has restricted access.
	authpriv.*                                              /var/log/secure

	# Log all the mail messages in one place.
	mail.*                                                  /var/log/maillog

	# Everybody gets emergency messages, plus log them on another
	# machine.
	*.emerg                                                 *
	*.emerg                                                 @arpa.berkeley.edu

	# Root and Eric get alert and higher messages.
	*.alert                                                 root,eric

	# Save mail and news errors of level err and higher in a
	# special file.
	uucp,news.crit                                          /var/log/spoolerr 


Sempre depois de alterar o arquivo é preciso reiniciar o serviço. Para iniciar, parar ou, reinicar o serviço de logs execute:

	sudo /etc/init.d/inetutils-syslogd start|stop|restart


## facility

O criador da mensagem (auth, authpriv, cron, daemon, kern, lpr, mail)

## priority

Urgência ou importância da mensagem. 

	<=====================+DETALHES-======================>
	debug, info, notice, warning, err, crit, alert , emerg
	<=====================-IMPORTANTE+====================>

## action

Destino das mensagens. Que pode ser:

### todos usuários

Basta colocar um asterisco `*` e o log sera enviado para a tela de todos os usuários:

	uucp.emerg                                          *

Todos os usuarios receberão em sua tela logs do facility `uucp`

### usuário

	basta colocar o nome do usuario e a mensgem de log sera impressa no bash do usuário

### arquivo

basta indicar o arquivo como no exemplo abaixo:

	uucp,news.crit                                          /var/log/spoolerr

Podemos ainda infromar dessa forma:

	uucp,news.crit                                          -/var/log/spoolerr

O log não sera salvo imediatamente no arquivo após sua geração. Essa funcionalidade gaante maior performace do syslogd.	

### servidor de log remoto

A mensagem é enviada para um servidor de logs. A sintaxe segue abaixo:


	*.* 		@10.1.38.223

### Sintaxe


#### `.`

	mail.notice			/var/log/meus-logs.log 

Define que da facility `mail` as prioritys notice, warning, err, crit, alert , emerg serão enviadas para o arquivo /var/log/meus-logs.log. Ou seja o `.` pega as priorites apartir da informada até a mais critica

#### `.=`

Já com o `.=` é selecionada exatamente a priority definida:


	mail.=notice			/var/log/meus-notices-do-mail.log 

Aqui só pega o `notice` do `mail`.


#### `*`

A utilização do `*` define todos os elementos para a regra. Na regra abaixo todas as prioritys do facility `mail` iram para o log:


	mail.*				/var/log/mail.log

Podemos colocar ainda o asterisco na facility:


	*.emerg				/var/log/emerg.log

Todos os logs da priority `emerg` de todas as facilitys iram para o log definido

## Configurar servidor para receber logs


Basta editar o arquivo /etc/default/inetultils-syslogd e colocar a opção "r" de remote


	SYSLOGD_OPTS="r"

## syslogd

O syslogd é o nome do daemon do syslog. Podemos verificar isso listando o processo: 

	ps axu | grep syslog
	syslog    1107  0.0  0.0 256388  3008 ?        Ssl  Dez26   0:00 /usr/sbin/syslogd


## klogd

É um daemon do sistema que intercepta e cria logs de mensagens do Kernel.

## /var/log/

O principal diretório de logs do linux `/var/log`

## logger

O comando `logger` executa a geração de logs onde podemos indicar no comando a facility e a priority. No comando abaixo estamos gerando log usando o comando `logger`:


	logger -p local0.debug "teste de criação de log"

O comando `logger` pode ainda ser executado com a opção `-t` (de tag).


	logger -p local0.debug -t TESTE "teste de criação de log"


## logrotate


## /etc/logrotate.conf


## /etc/logrotate.d/


## journalctl


## /etc/systemd/journald.conf


## /var/log/journal/