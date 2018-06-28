---
layout: page
title: 108.1 Sistema de Logs (Peso 3)
permalink: /108/108-1-sistema-de-logs
---

Configurar o serviço do syslog. Esse objetivo tambem inclui cofngurar o serviço de logs para enviar para um servidor de logs, ou ate mesmo aceitar logs atuando como uma central de logs. Utilizar o systemd joournal subsystem, e conhecimento sobre o rsyslog and syslog-ng como uma alternativa. 

Configurar o serviço do syslog
Entender as `standard facilities`, propriedades e ações
Configuração do `logrotate`
Conhecimentos de rsyslog e syslog-ng
Terms and Utilities:

syslog.conf
syslogd
klogd
/var/log/
logger
logrotate
/etc/logrotate.conf
/etc/logrotate.d/
journalctl
/etc/systemd/journald.conf
/var/log/journal/