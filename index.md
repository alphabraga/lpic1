# Home

## Topico 101: Arquitetura do Sistema

### 101.1 Visualize e configure definições de hardware

Peso: 2

Descrição: Candidates should be able to determine and configure fundamental system hardware.

Areas Chave de Conhecimento:

Tools and utilities to list various hardware information (e.g. lsusb, lspci, etc.)
Tools and utilities to manipulate USB devices
Conceptual understanding of sysfs, udev, dbus
The following is a partial list of the used files, terms and utilities:

	/sys/
	/proc/
	/dev/
	modprobe
	lsmod
	lspci
	lsusb
 

## 101.2 Boot the system
Peso: 3

Descrição: Candidates should be able to guide the system through the booting process.

Areas Chave de Conhecimento:

Provide common commands to the boot loader and options to the kernel at boot time
Demonstrate knowledge of the boot sequence from BIOS to boot completion
Understanding of SysVinit and systemd
Awareness of Upstart
Check boot events in the log files
Terms and Utilities:

	dmesg
	BIOS
	bootloader
	kernel
	initramfs
	init
	SysVinit
	systemd
 

### 101.3 Mudar runlevels / boot targets and shutdown or reboot system
Peso: 3

Descrição: Candidates should be able to manage the SysVinit runlevel or systemd boot target of the system. This objective includes changing to single user mode, shutdown or rebooting the system. Candidates should be able to alert users before switching runlevels / boot targets and properly terminate processes. This objective also includes setting the default SysVinit runlevel or systemd boot target. It also includes awareness of Upstart as an alternative to SysVinit or systemd.

Areas Chave de Conhecimento:

Set the default runlevel or boot target
Change between runlevels / boot targets including single user mode
Shutdown and reboot from the command line
Alert users before switching runlevels / boot targets or other major system events
Properly terminate processes
Terms and Utilities:

	/etc/inittab
	shutdown
	init
	/etc/init.d/
	telinit
	systemd
	systemctl
	/etc/systemd/
	/usr/lib/systemd/
	wall

## Topico 102: Linux Installation and Package Management

### 102.1 Design hard disk layout

Peso: 2

Descrição: Candidates should be able to design a disk partitioning scheme for a Linux system.

Areas Chave de Conhecimento:

Allocate filesystems and swap space to separate partitions or disks
Tailor the design to the intended use of the system
Ensure the /boot partition conforms to the hardware architecture requirements for booting
Knowledge of basic features of LVM
Terms and Utilities:

	/ (root) filesystem
	/var filesystem
	/home filesystem
	/boot filesystem
	swap space
	mount points
	partitions
 
### 102.2 Install a boot manager

Peso: 2

Descrição: Candidates should be able to select, install and configure a boot manager.

Areas Chave de Conhecimento:

Providing alternative boot locations and backup boot options
Install and configure a boot loader such as GRUB Legacy
Perform basic configuration changes for GRUB 2
Interact with the boot loader
The following is a partial list of the used files, terms and utilities:

	menu.lst, grub.cfg and grub.conf
	grub-install
	grub-mkconfig
	MBR
 

### 102.3 Manage shared libraries
Peso: 1

Descrição: Candidates should be able to determine the shared libraries that executable programs depend on and install them when necessary.

Areas Chave de Conhecimento:

Identify shared libraries
Identify the typical locations of system libraries
Load shared libraries
Terms and Utilities:

	ldd
	ldconfig
	/etc/ld.so.conf
	LD_LIBRARY_PATH
 

### 102.4 Use Debian package management
Peso: 3

Descrição: Candidates should be able to perform package management using the Debian package tools.

Areas Chave de Conhecimento:

Install, upgrade and uninstall Debian binary packages
Find packages containing specific files or libraries which may or may not be installed
Obtain package information like version, content, dependencies, package integrity and installation status (whether or not the package is installed)
Terms and Utilities:

	/etc/apt/sources.list
	dpkg
	dpkg-reconfigure
	apt-get
	apt-cache
	aptitude

 

### 102.5 Use RPM and YUM package management
Peso: 3

Descrição: Candidates should be able to perform package management using RPM and YUM tools.

Areas Chave de Conhecimento:

Install, re-install, upgrade and remove packages using RPM and YUM
Obtain information on RPM packages such as version, status, dependencies, integrity and signatures
Determine what files a package provides, as well as find which package a specific file comes from
Terms and Utilities:

	rpm
	rpm2cpio
	/etc/yum.conf
	/etc/yum.repos.d/
	yum
	yumdownloader

## Topico 103: GNU and Unix Commands

### 103.1 Work on the command line
Peso: 4

Descrição: Candidates should be able to interact with shells and commands using the command line. The objective assumes the Bash shell.

Areas Chave de Conhecimento:

Use single shell commands and one line command sequences to perform basic tasks on the command line
Use and modify the shell environment including defining, referencing and exporting environment variables
Use and edit command history
Invoke commands inside and outside the defined path
Terms and Utilities:

	bash
	echo
	env
	export
	pwd
	set
	unset
	man
	uname
	history
	.bash_history
 

103.2 Process text streams using filters
Peso: 3

Descrição: Candidates should should be able to apply filters to text streams.

Areas Chave de Conhecimento:

Send text files and output streams through text utility filters to modify the output using standard UNIX commands found in the GNU textutils package

Terms and Utilities:

	cat
	cut
	expand
	fmt
	head
	join
	less
	nl
	od
	paste
	pr
	sed
	sort
	split
	tail
	tr
	unexpand
	uniq
	wc
 

103.3 Perform basic file management
Peso: 4

Descrição: Candidates should be able to use the basic Linux commands to manage files and directories.

Areas Chave de Conhecimento:

Copy, move and remove files and directories individually
Copy multiple files and directories recursively
Remove files and directories recursively
Use simple and advanced wildcard specifications in commands
Using find to locate and act on files based on type, size, or time
Usage of tar, cpio and dd
Terms and Utilities:

	cp
	find
	mkdir
	mv
	ls
	rm
	rmdir
	touch
	tar
	cpio
	dd
	file
	gzip
	gunzip
	bzip2
	xz
	file globbing
 

103.4 Use streams, pipes and redirects
Peso: 4

Descrição: Candidates should be able to redirect streams and connect them in order to efficiently process textual data. Tasks include redirecting standard input, standard output and standard error, piping the output of one command to the input of another command, using the output of one command as arguments to another command and sending output to both stdout and a file.

Areas Chave de Conhecimento:

Redirecting standard input, standard output and standard error
Pipe the output of one command to the input of another command
Use the output of one command as arguments to another command
Send output to both stdout and a file
Terms and Utilities:

	tee
	xargs
 

### 103.5 Create, monitor and kill processes
Peso: 4

Descrição: Candidates should be able to perform basic process management.

Areas Chave de Conhecimento:

Run jobs in the foreground and background
Signal a program to continue running after logout
Monitor active processes
Select and sort processes for display
Send signals to processes
Terms and Utilities:

	&
	bg
	fg
	jobs
	kill
	nohup
	ps
	top
	free
	uptime
	pgrep
	pkill
	killall
	screen
 

### 103.6 Modify process execution priorities

Peso: 2

Descrição: Candidates should should be able to manage process execution priorities.

Areas Chave de Conhecimento:

Know the default priority of a job that is created
Run a program with higher or lower priority than the default
Change the priority of a running process
Terms and Utilities:

	nice
	ps
	renice
	top
 

103.7 Search text files using regular expressions
Peso: 2

Descrição: Candidates should be able to manipulate files and text data using regular expressions. This objective includes creating simple regular expressions containing several notational elements. It also includes using regular expression tools to perform searches through a filesystem or file content.

Areas Chave de Conhecimento:

Create simple regular expressions containing several notational elements
Use regular expression tools to perform searches through a filesystem or file content
Terms and Utilities:

	grep
	egrep
	fgrep
	sed
	regex(7)
 

### 103.8 Perform basic file editing operations using vi
Peso: 3

Descrição: Candidates should be able to edit text files using vi. This objective includes vi navigation, basic vi modes, inserting, editing, deleting, copying and finding text.

Areas Chave de Conhecimento:

Navigate a document using vi
Use basic vi modes
Insert, edit, delete, copy and find text
Terms and Utilities:

	vi
	/, ?
	h,j,k,l
	i, o, a
	c, d, p, y, dd, yy
	ZZ, :w!, :q!, :e!

## Topico 104: Devices, Linux Filesystems, Filesystem Hierarchy Standard


### 104.1 Create partitions and filesystems
Peso: 2

Descrição: Candidates should be able to configure disk partitions and then create filesystems on media such as hard disks. This includes the handling of swap partitions.

Areas Chave de Conhecimento:

	Manage MBR partition tables
	Use various mkfs commands to create various filesystems such as:
	ext2/ext3/ext4
	XFS
	VFAT
	Awareness of ReiserFS and Btrfs
	Basic knowledge of gdisk and parted with GPT

Terms and Utilities:

	fdisk
	gdisk
	parted
	mkfs
	mkswap
 

### 104.2 Maintain the integrity of filesystems
Peso: 2

Descrição: Candidates should be able to maintain a standard filesystem, as well as the extra data associated with a journaling filesystem.

Areas Chave de Conhecimento:

Verify the integrity of filesystems
Monitor free space and inodes
Repair simple filesystem problems
Terms and Utilities:

	du
	df
	fsck
	e2fsck
	mke2fs
	debugfs
	dumpe2fs
	tune2fs
	XFS tools (such as xfs_metadump and xfs_info)
 

### 104.3 Control mounting and unmounting of filesystems
Peso: 3

Descrição: Candidates should be able to configure the mounting of a filesystem.

Areas Chave de Conhecimento:

Manually mount and unmount filesystems
Configure filesystem mounting on bootup
Configure user mountable removable filesystems
Terms and Utilities:

	/etc/fstab
	/media/
	mount
	umount
 

### 104.4 Manage disk quotas

Peso: 1

Descrição: Candidates should be able to manage disk quotas for users.

Areas Chave de Conhecimento:

Set up a disk quota for a filesystem
Edit, check and generate user quota reports
Terms and Utilities:

	quota
	edquota
	repquota
	quotaon
 

104.5 Manage file permissions and ownership

Peso: 3

Descrição: Candidates should be able to control file access through the proper use of permissions and ownerships.

Areas Chave de Conhecimento:

Manage access permissions on regular and special files as well as directories
Use access modes such as suid, sgid and the sticky bit to maintain security
Know how to change the file creation mask
Use the group field to grant file access to group members
Terms and Utilities:

	chmod
	umask
	chown
	chgrp
 

### 104.6 Create and change hard and symbolic links

Peso: 2

Descrição: Candidates should be able to create and manage hard and symbolic links to a file.

Areas Chave de Conhecimento:

Create links
Identify hard and/or soft links
Copying versus linking files
Use links to support system administration tasks
Terms and Utilities:

	ln
	ls
 

### 104.7 Find system files and place files in the correct location

Peso: 2

Descrição: Candidates should be thoroughly familiar with the Filesystem Hierarchy Standard (FHS), including typical file locations and directory classifications.

Areas Chave de Conhecimento:

Understand the correct locations of files under the FHS
Find files and commands on a Linux system
Know the location and purpose of important file and directories as defined in the FHS
Terms and Utilities:

	find
	locate
	updatedb
	whereis
	which
	type
	/etc/updatedb.conf


## Topico 103: GNU and Unix Commands

### 103.1 Work on the command line

Peso: 4

Descrição: Candidates should be able to interact with shells and commands using the command line. The objective assumes the Bash shell.

Areas Chave de Conhecimento:

Use single shell commands and one line command sequences to perform basic tasks on the command line
Use and modify the shell environment including defining, referencing and exporting environment variables
Use and edit command history
Invoke commands inside and outside the defined path
Terms and Utilities:

bash
echo -  imprime uma string na tela

env       - lista todas as vaiáveis de ambiente (environment) setadas:

$alphabraga@vortex:~ env #basta digitar o comando sem argumentos

vocẽ pode tambem usar o comando printenv para exibir a mesma informação 

altera o valor de uma variável de ambiente,



 Para remover uma variável utilizamos o comando: unset NOMEVAR

export - Coloca uma variavel no ambiente, para colocar ela definitivamente no enviroment voce deve coloca esse export dentro de .bash_profile ou em /etc/environment


pwd - pwd significa print working directory, ou seja, exibir o diretorio corrente ou exibir diretorio atual


set comando relacionado com a capacidade de evitar sobrescrita de arquivos.
man programa q exibe os manuais dos comandos exemplo: man cp
uname exibe dados do so. Como versão do kernel distribuicao etc...
history
.bash_history


Diferença entre .bashrc e .bash_profile

O .bash_profile é executado quando é realizado o login no bash, já o bashrc é executado sempre se abre o bash dentro do gnome. é comum ver distrbuiçõies que colocam no final do arquivo .bash_profile o comando "source ~/.bashrc" dessa forma variaveis configrações definidas em ambos os arquivos ficam disponiveis





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

O programa /sbin/init é invocado no inicio do processo de boot identifica o novel de execucao.

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












 



	