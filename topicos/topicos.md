---
layout: page
title: 101.1 Visualize e configure definições de hardware
permalink: /topicos-extendido/
order: 2
---

## Topico 101: Arquitetura do Sistema

### 101.1 Visualize e configure definições de hardware

Peso: 2

Ter habilidade de visualizar e configurar sistemas de hardware fundamentais.

Feramentas e utilitarios para listar diversas de informações de hardware (e.g. lsusb, lspci, etc)
Feramentas e utilitarios para Manipular dispositivos USB
Entendimento conceitual de sysfs, udev, dbus

A seguir uma lista de arquivos, utilitários e termos:

* [/sys/](#)
* [/proc/](#)
* [/dev/](#)
* [modprobe](#)
* [lsmod](#)
* [lspci](#)
* [lsusb](#)
 

## 101.2 Inicializar o Sistema

Peso: 3

Descrição: Candidatos devem ter a capacidade de guiar o sistema durante o processo de boot.

Areas Chave de Conhecimento:

Provide common commands to the boot loader and options to the kernel at boot time
Demonstrar conhecimento da sequencia de boot  da BIOS to boot completion
Conhecimento de SysVinit e systemd
Awareness of Upstart
Check boot events in the log files

Termos e Utilitários:

* [dmesg](#)
* [BIOS](#)
* [bootloader](#)
* [kernel](#)
* [initramfs](#)
* [init](#)
* [SysVinit](#)
* [systemd](#)
 

### 101.3 Mudar runlevels / boot targets and shutdown or reboot system
Peso: 3

Descrição: Candidatos devem ter a capacidade de  to manage the SysVinit runlevel or systemd boot target of the system. This objective includes changing to single user mode, shutdown or rebooting the system. Candidatos devem ter a capacidade de  to alert users before switching runlevels / boot targets and properly terminate processes. This objective also includes setting the default SysVinit runlevel or systemd boot target. It also includes awareness of Upstart as an alternative to SysVinit or systemd.

Areas Chave de Conhecimento:

Set the default runlevel or boot target
Change between runlevels / boot targets including single user mode
Shutdown and reboot from the command line
Alert users before switching runlevels / boot targets or other major system events
Properly terminate processes

Termos e Utilitários:

* [/etc/inittab](#)
* [shutdown](#)
* [init](#)
* [/etc/init.d/](#)
* [telinit](#)
* [systemd](#)
* [systemctl](#)
* [/etc/systemd/](#)
* [/usr/lib/systemd/](#)
* [wall](#)

## Topico 102: Linux Installation and Package Management

### 102.1 Design hard disk layout

Peso: 2

Descrição: Candidatos devem ter a capacidade de  to design a disk partitioning scheme for a Linux system.

Areas Chave de Conhecimento:

Allocate filesystems and swap space to separate partitions or disks
Tailor the design to the intended use of the system
Ensure the /boot partition conforms to the hardware architecture requirements for booting
Knowledge of basic features of LVM
Termos e Utilitários:

* [/ (root) filesystem](#)
* [/var filesystem](#)
* [/home filesystem](#)
* [/boot filesystem](#)
* [swap space](#)
* [mount points](#)
* [partitions](#)
 
### 102.2 Instalar um gerenciador de boot

Peso: 2

Descrição: Candidatos devem ter a capacidade selecionar, instalar e configurar um gerenciador de boot.

Areas Chave de Conhecimento:

Providing alternative boot locations and backup boot options
Install and configure a boot loader such as GRUB Legacy
Perform basic configuration changes for GRUB 2
Interact with the boot loader
The following is a partial list of the used files, Termos e Utilitários:

* [menu.lst, grub.cfg and grub.conf](#)
* [grub-install](#)
* [grub-mkconfig](#)
* [MBR](#)
 

### 102.3 Manage shared libraries
Peso: 1

Descrição: Candidatos devem ter a capacidade de  to determine the shared libraries that executable programs depend on and install them when necessary.

Areas Chave de Conhecimento:

Identify shared libraries
Identify the typical locations of system libraries
Load shared libraries
Termos e Utilitários:

* [ldd](#)
* [ldconfig](#)
* [/etc/ld.so.conf](#)
* [LD_LIBRARY_PATH](#)
 

### 102.4 Use Debian package management

Peso: 3

Descrição: Candidatos devem ter a capacidade de  to perform package management using the Debian package tools.

Areas Chave de Conhecimento:

Install, upgrade and uninstall Debian binary packages
Find packages containing specific files or libraries which may or may not be installed
Obtain package information like version, content, dependencies, package integrity and installation status (whether or not the package is installed)
Termos e Utilitários:

* [/etc/apt/sources.list](#)
* [dpkg](#)
* [dpkg-reconfigure](#)
* [apt-get](#)
* [apt-cache](#)
* [aptitude](#)

 

### 102.5 Use RPM and YUM package management
Peso: 3

Descrição: Candidatos devem ter a capacidade de  to perform package management using RPM and YUM tools.

Areas Chave de Conhecimento:

Install, re-install, upgrade and remove packages using RPM and YUM
Obtain information on RPM packages such as version, status, dependencies, integrity and signatures
Determine what files a package provides, as well as find which package a specific file comes from
Termos e Utilitários:

* [rpm](#)
* [rpm2cpio](#)
* [/etc/yum.conf](#)
* [/etc/yum.repos.d/](#)
* [yum](#)
* [yumdownloader](#)

## Topico 103: GNU and Unix Commands

### 103.1 Work on the command line Peso: 4

Descrição: Candidatos devem ter a capacidade de  to interact with shells and commands using the command line. The objective assumes the Bash shell.

Areas Chave de Conhecimento:

Use single shell commands and one line command sequences to perform basic tasks on the command line
Use and modify the shell environment including defining, referencing and exporting environment variables
Use and edit command history
Invoke commands inside and outside the defined path
Termos e Utilitários:

* [bash](#)
* [echo](#)
* [env](#)
* [export](#)
* [pwd](#)
* [set](#)
* [unset](#)
* [man](#)
* [uname](#)
* [history](#)
* [.bash_history](#)
 

103.2 Process text streams using filters
Peso: 3

Descrição: Candidates should should be able to apply filters to text streams.

Areas Chave de Conhecimento:

Send text files and output streams through text utility filters to modify the output using standard UNIX commands found in the GNU textutils package

Termos e Utilitários:

* [cat](#)
* [cut](#)
* [expand](#)
* [fmt](#)
* [head](#)
* [join](#)
* [less](#)
* [nl](#)
* [od](#)
* [paste](#)
* [pr](#)
* [sed](#)
* [sort](#)
* [split](#)
* [tail](#)
* [tr](#)
* [unexpand](#)
* [uniq](#)
* [wc](#)
 

103.3 Perform basic file management
Peso: 4

Descrição: Candidatos devem ter a capacidade de  to use the basic Linux commands to manage files and directories.

Areas Chave de Conhecimento:

Copy, move and remove files and directories individually
Copy multiple files and directories recursively
Remove files and directories recursively
Use simple and advanced wildcard specifications in commands
Using find to locate and act on files based on type, size, or time
Usage of tar, cpio and dd
Termos e Utilitários:

* [cp](#)
* [find](#)
* [mkdir](#)
* [mv](#)
* [ls](#)
* [rm](#)
* [rmdir](#)
* [touch](#)
* [tar](#)
* [cpio](#)
* [dd](#)
* [file](#)
* [gzip](#)
* [gunzip](#)
* [bzip2](#)
* [xz](#)
* [file globbing](#)
 

103.4 Use streams, pipes and redirects
Peso: 4

Descrição: Candidatos devem ter a capacidade de  to redirect streams and connect them in order to efficiently process textual data. Tasks include redirecting standard input, standard output and standard error, piping the output of one command to the input of another command, using the output of one command as arguments to another command and sending output to both stdout and a file.

Areas Chave de Conhecimento:

Redirecting standard input, standard output and standard error
Pipe the output of one command to the input of another command
Use the output of one command as arguments to another command
Send output to both stdout and a file
Termos e Utilitários:

* [tee]
* [xargs]
 

### 103.5 Create, monitor and kill processes

Peso: 4

Descrição: Candidatos devem ter a capacidade de  to perform basic process management.

Areas Chave de Conhecimento:

Run jobs in the foreground and background
Signal a program to continue running after logout
Monitor active processes
Select and sort processes for display
Send signals to processes
Termos e Utilitários:

* [&](#)
* [bg](#)
* [fg](#)
* [jobs](#)
* [kill](#)
* [nohup](#)
* [ps](#)
* [top](#)
* [free](#)
* [uptime](#)
* [pgrep](#)
* [pkill](#)
* [killall](#)
* [screen](#)
 

### 103.6 Modify process execution priorities

Peso: 2

Descrição: Candidates should should be able to manage process execution priorities.

Areas Chave de Conhecimento:

Know the default priority of a job that is created
Run a program with higher or lower priority than the default
Change the priority of a running process
Termos e Utilitários:

* [nice](#)
* [ps](#)
* [renice](#)
* [top](#)
 

103.7 Search text files using regular expressions
Peso: 2

Descrição: Candidatos devem ter a capacidade de  to manipulate files and text data using regular expressions. This objective includes creating simple regular expressions containing several notational elements. It also includes using regular expression tools to perform searches through a filesystem or file content.

Areas Chave de Conhecimento:

Create simple regular expressions containing several notational elements
Use regular expression tools to perform searches through a filesystem or file content
Termos e Utilitários:

* [grep](#)
* [egrep](#)
* [fgrep](#)
* [sed](#)
* [regex(7)](#)
 

### 103.8 Perform basic file editing operations using vi
Peso: 3

Descrição: Candidatos devem ter a capacidade de  to edit text files using vi. This objective includes vi navigation, basic vi modes, inserting, editing, deleting, copying and finding text.

Areas Chave de Conhecimento:

Navigate a document using vi
Use basic vi modes
Insert, edit, delete, copy and find text
Termos e Utilitários:

* [vi](#)
* [/, ?](#)
* [h,j,k,l](#)
* [i, o, a](#)
* [c, d, p, y, dd, yy](#)
* [ZZ, :w!, :q!, :e!](#)

## Topico 104: Devices, Linux Filesystems, Filesystem Hierarchy Standard


### 104.1 Create partitions and filesystems Peso: 2

Descrição: Candidatos devem ter a capacidade de  to configure disk partitions and then create filesystems on media such as hard disks. This includes the handling of swap partitions.

Areas Chave de Conhecimento:

* [Manage MBR partition tables](#)
* [Use various mkfs commands to create various filesystems such as:](#)
* [ext2/ext3/ext4](#)
* [XFS](#)
* [VFAT](#)
* [Awareness of ReiserFS and Btrfs](#)
* [Basic knowledge of gdisk and parted with GPT](#)

Termos e Utilitários:

* [fdisk](#)
* [gdisk](#)
* [parted](#)
* [mkfs](#)
* [mkswap](#)
 

### 104.2 Maintain the integrity of filesystems Peso: 2

Descrição: Candidatos devem ter a capacidade de  to maintain a standard filesystem, as well as the extra data associated with a journaling filesystem.

Areas Chave de Conhecimento:

Verify the integrity of filesystems
Monitor free space and inodes
Repair simple filesystem problems
Termos e Utilitários:

* [du](#)
* [df](#)
* [fsck](#)
* [e2fsck](#)
* [mke2fs](#)
* [debugfs](#)
* [dumpe2fs](#)
* [tune2fs](#)
* [XFS tools (such as xfs_metadump and xfs_info)](#)
 

### 104.3 Control mounting and unmounting of filesystems

Peso: 3

Descrição: Candidatos devem ter a capacidade de  to configure the mounting of a filesystem.

Areas Chave de Conhecimento:

Manually mount and unmount filesystems
Configure filesystem mounting on bootup
Configure user mountable removable filesystems
Termos e Utilitários:

* [/etc/fstab](#)
* [/media/](#)
* [mount](#)
* [umount](#)
 

### 104.4 Manage disk quotas

Peso: 1

Descrição: Candidatos devem ter a capacidade de  to manage disk quotas for users.

Areas Chave de Conhecimento:

Set up a disk quota for a filesystem
Edit, check and generate user quota reports
Termos e Utilitários:

* [quota](#)
* [edquota](#)
* [repquota](#)
* [quotaon](#)
 

104.5 Manage file permissions and ownership

Peso: 3

Descrição: Candidatos devem ter a capacidade de  to control file access through the proper use of permissions and ownerships.

Areas Chave de Conhecimento:

Manage access permissions on regular and special files as well as directories
Use access modes such as suid, sgid and the sticky bit to maintain security
Know how to change the file creation mask
Use the group field to grant file access to group members
Termos e Utilitários:

* [chmod](#)
* [umask](#)
* [chown](#)
* [chgrp](#)
 

### 104.6 Create and change hard and symbolic links

Peso: 2

Descrição: Candidatos devem ter a capacidade de  to create and manage hard and symbolic links to a file.

Areas Chave de Conhecimento:

Create links
Identify hard and/or soft links
Copying versus linking files
Use links to support system administration tasks
Termos e Utilitários:

* [ln](#)
* [ls](#)
 

### 104.7 Find system files and place files in the correct location

Peso: 2

Descrição: Candidates should be thoroughly familiar with the Filesystem Hierarchy Standard (FHS), including typical file locations and directory classifications.

Areas Chave de Conhecimento:

Understand the correct locations of files under the FHS
Find files and commands on a Linux system
Know the location and purpose of important file and directories as defined in the FHS
Termos e Utilitários:

* [find](#)
* [locate](#)
* [updatedb](#)
* [whereis](#)
* [which](#)
* [type](#)
* [/etc/updatedb.conf](#)


## Topico 103: GNU and Unix Commands

### 103.1 Work on the command line (Peso 4)

Ter a capacidade de interagir com comandos do shell.

Utilizar comandos unicos e multiplos comandos em uma unica linha para realizar tarefas básicas 
Utilizar e modificar variaveis de ambiente incluindo, definindo, referenciando e exportando variáveis de ambiente.
Usar e editar o historico de comandos
Chamar comandos dentro e fora do PATH definido







Identificar e editar configs de hardware

Pode ser feito de duas formas
- com commandos espeficicos
- vendo arquivos no sistema de arquivos especial

Commandos de Inspeção

lspci : listar components conectados ao barramento pci.
lsusb: listar dispositivos USB conectados a máquina.

Os commandos listar os dispositivos, se estão funcionando depende se existe no sistema o modulo correspondente.

Para ver detalhes de dispositivo

lspci -s <endereco> -v

Onde endereco é o número exibido no começo pelo comando lspci.

Para ver os modulos presentes no sistema:

lsmod

Para ver cada um dos modulos disponíveis e os dispositivos conectados.

Utilizar a opcao -v para ver detalhes assim como no comando lspci. Já para ver os detalhes de um dispositivo expeficico se utilizar -d com ID do mesmo.

Os commandos lspci,lsmod,lsusb são facilitadores. Pois ele lê o contêudo dos sistemas de arquivos de /proc e /sys.

/proc exibe informações de processos ativos e recursos de hardware.

-/proc/cpuinfo dados de processadores
-/proc/dma informacoes de canais de acesso direto a memoria
-/proc/ioports informacoes sobre enderecos de memoria utilizados por dispositivos.
-/proc/interrupts info sobre irqs dos processadores.

O /sys armazena dados sobre dispositivos e o /proc sobre processos ativos alem de dispositivos.

Outro directorio importante é o /dev que exibe informacoes sobre dispositivos de armazenento encontrados no sistema.

-/dev/hda1 representa a particao 1 do primeiro disco ide identificado pelo so.

Dispositivos Coldplug:  É preciso desligar o sistema para conectar. Examples: dispositivos pci, dispositivos ide, CPU,  modules de memoria.

Hot plug: dispositivos que podem ser conectados a maquina em funcionando e usalos imediatamente.

...........
....
..
.
Dispositivos de armazenento

...........
....
...
....
Dispositivos SCSI
.......
...
..

Inicio boot do sistema

......
....

..

Alternar runlevels, desligar e reninciar o sistema.

O run level é o grau de interacao do usuario com o sistema.

O programa /sbin/init é invocado no inicio do processo de boot identifica o nível de execucao.

............

Os runlevels vão de 0-6 e podem variar suas funcoes entre distros. Mas via de regra no arquivo /etc/inittab que defini os runlevels tambem traz informacoes sobre cada um.

O formato das entradas nesse arquivo é 

id:runlevels:acao: processo

-id : ate 4 characters para identificar a entrada no inittab
-runlevels lista runlevels Na qual as acoes de entrada deveram ser executadas


Comandos bash

- $! Mostra pid do ultimo comando executadas
- $$ pid do shell atual
- $? Mostra se o ultimo comando executadas com sucesso ( 0 OK, 1 error)
- ~alphabraga vai pro home do usuario alphabraga


Tenho em Mente que:

;      Significa de fim instrucao
&&  Significa 'and' 'e' para p portugues
||     Significa 'or', 'ou'

Executa os 3 independent do results deles:

Commando 1; commando 2; commando 3

Executa o proximo se o anterior retornar 0

Commando 1 && command 2 && commando 3

Executa o proximo se o anterior falar

Commando 1 || Commando 2 || Commando 3


Tipos de arquivo 

- Arquivo comun
d Diretorio
l Link
b dispositivo de bloco
c dispositivo de caracter
p Pipe
s Socket de Comunicação





Permissões



Adicionando permissão usando modo letras. Usar o comando chmod:

Quando adicionados (+) ou removemos (-) permissões estamos utilizando o MÉTODO DIFERENCIAL para manipular as permissões. Quando utilizamos o sinal "=" estamos utilizando a ATRIBUIÇÃO DIRETA e o terceiro método é o OCTAL  


Exemplo:

DIFERENCIAL

chmod u+x nome-script.sh
chmod u-x nome-script.sh
chmod u+rwx nome-script.sh
chmod u+rwx,g+r nome-script.sh
chmod o+x nome-script.sh

ATRIBUIÇÃO DIRETA

chmod a=x nome-script.sh (a de all)


OCTAL

Por padrão um arquivo tem permissão inicial a 666 - umask ( 666 menos a umask ) já diretórios tem permissão padrão 777 - umask. Umask padrão é 002. i o arquivo fica 664 e o diretório fica 775


Modo octal

R - read vale 4
W - write vale 2
X - execute vale 1
________________
Total         7

PERMISSOES ESPECIAIS

SUID

quando o arquivo for executado por um usuário qualquer ele será executado como se fosse o dono do arquivo.

Essa permissão especial é indicada pela letra 's' no primeiro conjunto de permissões. Exemplo "rws", caso o arquivo não possua permissão de execução a letra fica maiúscula "S".

Um Exemplo clássico para essa situação é o comando passwd que precisa editar o arquivo /etc/passwd. Mas esse arquivo é do root. Ai temos um problema pois um usuário comum não poderia editar esse arquivo usando o comando passwd. Mas ao comando /usr/bin/passwd é atriuida a permissão SUID:


alphabraga@sharp:~$ ls -la /usr/bin/passwd
-rwsr-xr-x 1 root root 54256 Mai 16  2017 /usr/bin/passwd


SGID

Mesma coisa do SUID mas aplicado ao grupo. O mesmo se aplica a representação de letra

Ele determina que todos os arquivos abaixo deve devam ter o grupo que ele possui


STICK BIT

Só o usuário dono do arquivo pode apagar o arquivo. Utilizado na pasta /tmp


Comando tar



tar [parametros] [arquivo_de_destino.tar] arquivo*

parametros

c -  create Cirar um novo arquivo
t - lista os arquivos
x - extract extrair um arquivo
p - preservar as permissões originais
f - file Espeficicar o arquivo (??? que arquivo??? o de origem ou de destino)
v -  Verbose Exibe as informações da operações (arquivos qye foram agrupados, extraidos etc...)
r -  Adiciona um arquio a um tar já existente
z - compacta usando o gzip
j - compacta usando o bzip2
J - compacta usando xz


Para extrair um arquivo expecifico de um tar basta realizar
$ tar -xvf xmen.tar ciclope.txt


Para remover um arquivo:

$ tar -f xmen.tar --delete wolverine.txt


Para descobrir que método foi utilizado para compactar o arquivo voce pode utilizar o comando file: $ file arquivo.tar.gz (não quer dizer que voce criou o arquivo com a extensao gz que ele foi feito com gzip)

Os parametros podem ser digitados com ou sem o "-" Exemplo:

é valido:
$  tar -cpvf arquivo.tar arquivo-1.txt arquivo-2.txt

é valido:
$  tar cpvf arquivo.tar arquivo-1.txt arquivo-2.txt



Topico 101

BIOS - BASIC INPUT OUTPUT

POST - PRIMARY ON SELF TEST

DMA - DIRECT MEMORY ACCESS

para ver as informações sobre o MDA que é uma area de memoria reservada para alguns perifericos. Essa memoria é liberada diretamente para o hardware sem a intervenção do processar. Isso melhora o desenpenho.

IO

IRQ - INTERRUPTS REQUESTS


São canais de comunicação entre o hardware e a o processar. quando o processador recebe uma mensagem nesse canal ele deve para de fazer o qu eesta fazendo e receber essa mensagem nesse canal esse canais possuim prioridades



Topic 105: Shells, Scripting and Data Management
105.1 Customize and use the shell environment
Weight: 4

Description: Candidates should be able to customize shell environments to meet users’ needs. Candidates should be able to modify global and user profiles.

Key Knowledge Areas:

Set environment variables (e.g. PATH) at login or when spawning a new shell
Write Bash functions for frequently used sequences of commands
Maintain skeleton directories for new user accounts
Set command search path with the proper directory
The following is a partial list of the used files, terms and utilities:

source
/etc/bash.bashrc
/etc/profile
env
export
set
unset
~/.bash_profile
~/.bash_login
~/.profile
~/.bashrc
~/.bash_logout
function
alias
lists
 

105.2 Customize or write simple scripts
Weight: 4

Description: Candidates should be able to customize existing scripts, or write simple new Bash scripts.

Key Knowledge Areas:

Use standard sh syntax (loops, tests)
Use command substitution
Test return values for success or failure or other information provided by a command
Perform conditional mailing to the superuser
Correctly select the script interpreter through the shebang (#!) line
Manage the location, ownership, execution and suid-rights of scripts
Terms and Utilities:

for
while
test
if
read
seq
exec
 

105.3 SQL data management
Weight: 2

Description: Candidates should be able to query databases and manipulate data using basic SQL commands. This objective includes performing queries involving joining of 2 tables and/or subselects.

Key Knowledge Areas:

Use of basic SQL commands
Perform basic data manipulation
Terms and Utilities:

insert
update
select
delete
from
where
group by
order by
join
Topic 106: User Interfaces and Desktops
106.1 Install and configure X11
Weight: 2

Description: Candidates should be able to install and configure X11.

Key Knowledge Areas:

Verify that the video card and monitor are supported by an X server
Awareness of the X font server
Basic understanding and knowledge of the X Window configuration file
Terms and Utilities:

/etc/X11/xorg.conf
xhost
DISPLAY
xwininfo
xdpyinfo
X
 

106.2 Setup a display manager
Weight: 1

Description: Candidates should be able to describe the basic features and configuration of the LightDM display manager. This objective covers awareness of the display managers XDM (X Display Manger), GDM (Gnome Display Manager) and KDM (KDE Display Manager).

Key Knowledge Areas:

Basic configuration of LightDM
Turn the display manager on or off
Change the display manager greeting
Awareness of XDM, KDM and GDM
Terms and Utilities:

lightdm
/etc/lightdm/
 

106.3 Accessibility
Weight: 1

Description: Demonstrate knowledge and awareness of accessibility technologies.

Key Knowledge Areas:

Basic knowledge of keyboard accessibility settings (AccessX)
Basic knowledge of visual settings and themes
Basic knowledge of assistive technology (ATs)
Terms and Utilities:

Sticky/Repeat Keys
Slow/Bounce/Toggle Keys
Mouse Keys
High Contrast/Large Print Desktop Themes
Screen Reader
Braille Display
Screen Magnifier
On-Screen Keyboard
Gestures (used at login, for example GDM)
Orca
GOK
emacspeak
Topic 107: Administrative Tasks
107.1 Manage user and group accounts and related system files
Weight: 5

Description: Candidates should be able to add, remove, suspend and change user accounts.

Key Knowledge Areas:

Add, modify and remove users and groups
Manage user/group info in password/group databases
Create and manage special purpose and limited accounts
Terms and Utilities:

/etc/passwd
/etc/shadow
/etc/group
/etc/skel/
chage
getent
groupadd
groupdel
groupmod
passwd
useradd
userdel
usermod
 

107.2 Automate system administration tasks by scheduling jobs
Weight: 4

Description: Candidates should be able to use cron or anacron to run jobs at regular intervals and to use at to run jobs at a specific time.

Key Knowledge Areas:

Manage cron and at jobs
Configure user access to cron and at services
Configure anacron
Terms and Utilities:

/etc/cron.{d,daily,hourly,monthly,weekly}/
/etc/at.deny
/etc/at.allow
/etc/crontab
/etc/cron.allow
/etc/cron.deny
/var/spool/cron/
crontab
at
atq
atrm
anacron
/etc/anacrontab
 

107.3 Localisation and internationalisation
Weight: 3

Description: Candidates should be able to localize a system in a different language than English. As well, an understanding of why LANG=C is useful when scripting.

Key Knowledge Areas:

Configure locale settings and environment variables
Configure timezone settings and environment variables
Terms and Utilities:

/etc/timezone
/etc/localtime
/usr/share/zoneinfo/
LC_*
LC_ALL
LANG
TZ
/usr/bin/locale
tzselect
timedatectl
date
iconv
UTF-8
ISO-8859
ASCII
Unicode
Topic 108: Essential System Services
108.1 Maintain system time
Weight: 3

Description: Candidates should be able to properly maintain the system time and synchronize the clock via NTP.

Key Knowledge Areas:

Set the system date and time
Set the hardware clock to the correct time in UTC
Configure the correct timezone
Basic NTP configuration
Knowledge of using the pool.ntp.org service
Awareness of the ntpq command
Terms and Utilities:

/usr/share/zoneinfo/
/etc/timezone
/etc/localtime
/etc/ntp.conf
date
hwclock
ntpd
ntpdate
pool.ntp.org
 

108.2 System logging
Weight: 3

Description: Candidates should be able to configure the syslog daemon. This objective also includes configuring the logging daemon to send log output to a central log server or accept log output as a central log server. Use of the systemd journal subsystem is covered. Also, awareness of rsyslog and syslog-ng as alternative logging systems is included.

Key Knowledge Areas:

Configuration of the syslog daemon
Understanding of standard facilities, priorities and actions
Configuration of logrotate
Awareness of rsyslog and syslog-ng
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
 

108.3 Mail Transfer Agent (MTA) basics
Weight: 3

Description: Candidates should be aware of the commonly available MTA programs and be able to perform basic forward and alias configuration on a client host. Other configuration files are not covered.

Key Knowledge Areas:

Create e-mail aliases
Configure e-mail forwarding
Knowledge of commonly available MTA programs (postfix, sendmail, qmail, exim) (no configuration)
Terms and Utilities:

~/.forward
sendmail emulation layer commands
newaliases
mail
mailq
postfix
sendmail
exim
qmail
 

108.4 Manage printers and printing
Weight: 2

Description: Candidates should be able to manage print queues and user print jobs using CUPS and the LPD compatibility interface.

Key Knowledge Areas:

Basic CUPS configuration (for local and remote printers)
Manage user print queues
Troubleshoot general printing problems
Add and remove jobs from configured printer queues
Terms and Utilities:

CUPS configuration files, tools and utilities
/etc/cups/
lpd legacy interface (lpr, lprm, lpq)
Topic 109: Networking Fundamentals
109.1 Fundamentals of internet protocols
Weight: 4

Description: Candidates should demonstrate a proper understanding of TCP/IP network fundamentals.

Key Knowledge Areas:

Demonstrate an understanding of network masks and CIDR notation
Knowledge of the differences between private and public “dotted quad” IP addresses
Knowledge about common TCP and UDP ports and services (20, 21, 22, 23, 25, 53, 80, 110, 123, 139, 143, 161, 162, 389, 443, 465, 514, 636, 993, 995)
Knowledge about the differences and major features of UDP, TCP and ICMP
Knowledge of the major differences between IPv4 and IPv6
Knowledge of the basic features of IPv6
Terms and Utilities:

/etc/services
IPv4, IPv6
Subnetting
TCP, UDP, ICMP
 

109.2 Basic network configuration
Weight: 4

Description: Candidates should be able to view, change and verify configuration settings on client hosts.

Key Knowledge Areas:

Manually and automatically configure network interfaces
Basic TCP/IP host configuration
Setting a default route
Terms and Utilities:

/etc/hostname
/etc/hosts
/etc/nsswitch.conf
ifconfig
ifup
ifdown
ip
route
ping
 

109.3 Basic network troubleshooting
Weight: 4

Description: Candidates should be able to troubleshoot networking issues on client hosts.

Key Knowledge Areas:

Manually and automatically configure network interfaces and routing tables to include adding, starting, stopping, restarting, deleting or reconfiguring network interfaces
Change, view, or configure the routing table and correct an improperly set default route manually
Debug problems associated with the network configuration
Terms and Utilities:

ifconfig
ip
ifup
ifdown
route
host
hostname
dig
netstat
ping
ping6
traceroute
traceroute6
tracepath
tracepath6
netcat
 

109.4 Configure client side DNS
Weight: 2

Description: Candidates should be able to configure DNS on a client host.

Key Knowledge Areas:

Query remote DNS servers
Configure local name resolution and use remote DNS servers
Modify the order in which name resolution is done
Terms and Utilities:

/etc/hosts
/etc/resolv.conf
/etc/nsswitch.conf
host
dig
getent
Topic 110: Security
110.1 Perform security administration tasks
Weight: 3

Description: Candidates should know how to review system configuration to ensure host security in accordance with local security policies.

Key Knowledge Areas:

Audit a system to find files with the suid/sgid bit set
Set or change user passwords and password aging information
Being able to use nmap and netstat to discover open ports on a system
Set up limits on user logins, processes and memory usage
Determine which users have logged in to the system or are currently logged in
Basic sudo configuration and usage
Terms and Utilities:

find
passwd
fuser
lsof
nmap
chage
netstat
sudo
/etc/sudoers
su
usermod
ulimit
who, w, last
 

110.2 Setup host security
Weight: 3

Description: Candidates should know how to set up a basic level of host security.

Key Knowledge Areas:

Awareness of shadow passwords and how they work
Turn off network services not in use
Understand the role of TCP wrappers
Terms and Utilities:

/etc/nologin
/etc/passwd
/etc/shadow
/etc/xinetd.d/
/etc/xinetd.conf
/etc/inetd.d/
/etc/inetd.conf
/etc/inittab
/etc/init.d/
/etc/hosts.allow
/etc/hosts.deny
 

110.3 Securing data with encryption
Weight: 3

Description: The candidate should be able to use public key techniques to secure data and communication.

Key Knowledge Areas:

Perform basic OpenSSH 2 client configuration and usage
Understand the role of OpenSSH 2 server host keys
Perform basic GnuPG configuration, usage and revocation
Understand SSH port tunnels (including X11 tunnels)
Terms and Utilities:

ssh
ssh-keygen
ssh-agent
ssh-add
~/.ssh/id_rsa and id_rsa.pub
~/.ssh/id_dsa and id_dsa.pub
/etc/ssh/ssh_host_rsa_key and ssh_host_rsa_key.pub
/etc/ssh/ssh_host_dsa_key and ssh_host_dsa_key.pub
~/.ssh/authorized_keys
ssh_known_hosts
gpg
~/.gnupg/








 



	