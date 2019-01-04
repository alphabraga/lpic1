---
layout: page
title: 108.4 Gerencie impressoras e impressao
permalink: /108/108-4-gerencie-impressoras-e-impressao
---

Candidatos devem ter habilidade de gerenciar filas de impressão e tarefas de impressão de usuários utilizando o CUPS e a interface de compatibilidade LPD.

## Configuração Básica do CUPS (impressoras locais e remotas)

## lpinfo -v

Lista os dispositivos disponiveis, conectados no usb, na rede, compartilhados em outras maquinas:

	alphabraga@helix  ~  lpinfo -v
	network https
	network beh
	network ipp
	serial serial:/dev/ttyS0?baud=115200
	serial serial:/dev/ttyS4?baud=115200
	network ipps
	network http
	network ipp14
	direct hp
	network socket
	network lpd
	network smb
	direct hpfax
	network dnssd://MX-M565N%20(5502545100)._printer._tcp.local/
	network dnssd://RICOH%20Aficio%20SP%205200DN%20%5B4FE46F%5D._pdl-datastream._tcp.local/


### lpinfo -m

Lista os modulos (drivers) disponiveis:

	alphabraga@helix  ~  lpinfo -m | head
	lsb/usr/cupsfilters/Fuji_Xerox-DocuPrint_CM305_df-PDF.ppd Fuji Xerox
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-1000-md2k.ppd Alps MD-1000 Foomatic/md2k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-1300-md1xMono.ppd Alps MD-1300 Foomatic/md1xMono
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-1300-md2k.ppd Alps MD-1300 Foomatic/md2k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-1500-md1xMono.ppd Alps MD-1500 Foomatic/md1xMono
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-1500-md2k.ppd Alps MD-1500 Foomatic/md2k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-2000-md2k.ppd Alps MD-2000 Foomatic/md2k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-4000-md2k.ppd Alps MD-4000 Foomatic/md2k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-5000-md5k.ppd Alps MD-5000 Foomatic/md5k
	foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Alps-MD-5000-md50Eco.ppd Alps MD-5000 Foomatic/md50Eco



### lpstat

O `lpstat -a` exibe o status das impressoras configuradas, abaixo exemplo do comando:


	alphabraga@helix  ~  lpstat -a
	IMPRESSORA-GETIN-CORED accepting requests since Seg 03 Dez 2018 09:34:21 -03
	Ricoh-Aficio-SP-5200DN accepting requests since Ter 26 Jun 2018 11:42:32 -03

O comando `lpstat -t` exibe mais informações (**status do serviço, destino padrão ou impressora padrão dentro outras informações**), veja o output:

	alphabraga@helix  ~  lpstat -t
	scheduler is running
	system default destination: IMPRESSORA-GETIN-CORED
	device for IMPRESSORA-GETIN-CORED: socket://10.10.1.243:9100
	device for Ricoh-Aficio-SP-5200DN: socket://10.10.1.221:9100
	IMPRESSORA-GETIN-CORED accepting requests since Seg 03 Dez 2018 09:34:21 -03
	Ricoh-Aficio-SP-5200DN accepting requests since Ter 26 Jun 2018 11:42:32 -03
	printer IMPRESSORA-GETIN-CORED is idle.  enabled since Seg 03 Dez 2018 09:34:21 -03
	printer Ricoh-Aficio-SP-5200DN is idle.  enabled since Ter 26 Jun 2018 11:42:32 -03


### lpstat -d

Exibe a impressora padrão:

	alphabraga@helix  ~  lpstat -d
	system default destination: IMPRESSORA-GETIN-CORED


## Gerenciar filas de impressão

texto aqui

## Identificar problemas comuns relacionados a impressão

texto aqui

### Adcionar e remover tarefas de filas de impressão

* CUPS configuration files, tools and utilities
* /etc/cups/
* lpd legacy interface (lpr, lprm, lpq)