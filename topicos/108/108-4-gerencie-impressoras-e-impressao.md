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

### lpq

O comando `lpq` exibe o status da fila de impressão. Utilziado sem parametros ele lista informações sobre a fila de impressão da impressora padrão:

	alphabraga@helix ~lpq 
	IMPRESSORA-GETIN-CORED is ready
	no entries

Para ver informações de uma impressora espefica use o parametro `-P`.

### lpadmin

Esse comando realiza a configuração de impressoras. Abaixo veremos os passsos para adicionar uma impressora "HP Deskjet 2510".

#### Primeiro vamos procurar o modulo

	$ lpinfo -m | grep "HP Deskjet 2510"
	drv:///hpcups.drv/hp-deskjet_2510_series.ppd HP Deskjet 2510 Series, hpcups 3.16.3

#### Depois o device

	$ lpinfo -v | grep "hp-deskjet"
	drv:///hpcups.drv/hp-deskjet_3510_series.ppd

#### Por fim, vamos adiocnar a impressora

O parametro `-E` é para habilitar a impressora.

	$lpadmin -p IMPRESSORA-HP -E -v "drv:///hpcups.drv/hp-deskjet_3510_series.ppd" -m "drv:///hpcups.drv/hp-deskjet_3510_series.ppd"

### lpoptions

O comando `lpoptions` exibe e altera parametros de impressoras.

Caso o comando seja executado sem parametros são exibidas as informações da impressora padrão:

	~ lpoptions 
	copies=1 device-uri=socket://10.10.1.243:9100 finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=1543840461 marker-colors=#000000,#000000 marker-levels=80,0 marker-names='Toner,Toner\ usado' marker-types=toner,waste-toner number-up=1 printer-commands=none printer-info=IMPRESSORA-GETIN-CORED printer-is-accepting-jobs=true printer-is-shared=true printer-location=10.10.1.243 printer-make-and-model='Ricoh MP 501 PDF' printer-state=3 printer-state-change-time=1543840461 printer-state-reasons=none printer-type=135380 printer-uri-supported=ipp://localhost/printers/IMPRESSORA-GETIN-CORED

Ou podemos simplesmente passar o nome da empresa como parametro:

	$ lpoptions IMPRESSORA-GETIN-CORED
	copies=1 device-uri=socket://10.10.1.243:9100 finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=1543840461 marker-colors=#000000,#000000 marker-levels=80,0 marker-names='Toner,Toner\ usado' marker-types=toner,waste-toner number-up=1 printer-commands=none printer-info=IMPRESSORA-GETIN-CORED printer-is-accepting-jobs=true printer-is-shared=true printer-location=10.10.1.243 printer-make-and-model='Ricoh MP 501 PDF' printer-state=3 printer-state-change-time=1543840461 printer-state-reasons=none printer-type=135380 printer-uri-supported=ipp://localhost/printers/IMPRESSORA-GETIN-CORED	


### lpr

Envia arquivos para empressora, passando apenas o arquivo ele manda para a impressora padrão:

	$ lpr /etc/passwd

Podemos definir a impressora com `-P`	

	lpr /etc/passwd -P NOMEDAIMPRESSORA

Podemos usar ainda assim

	$ grep alphabraga /etc/passwd | lpr 

## Identificar problemas comuns relacionados a impressão

texto aqui

### Adcionar e remover tarefas de filas de impressão

* CUPS configuration files, tools and utilities
* /etc/cups/
* lpd legacy interface (lpr, lprm, lpq)