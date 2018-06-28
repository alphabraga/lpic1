---
layout: page
title: 104.3 Controle a Montagem e Desmontagem de Sistemas de Arquivos (Peso 3)
permalink: 104/104-3-controlar-a-montagem-e-desmontagem-de-sistemas-de-arquivos
---



## mount

Monta dispositivos em um diretorio espeficicado. Lembre-se que quando um diretório com arquivos dentro dele é escolhido como ponto de montagem de um dispositivo os arquivos dentro dele ficam indisponiveis ate que esse dispositivo seja desmontado. Veja abaixo dois exemplos de utilização docomando mount:

Executando o comando sem parametros ele exibe todos os dispositivos montados

<pre class="command-line language-bash">
<code>mount</code>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1939980k,nr_inodes=484995,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393300k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,quota,usrquota,grpquota,errors=remount-ro,data=ordered)
</pre>

No comando abaixo estamos montando o dispositivo `/dev/db1` no diretório `/mnt/disco`:

<pre class="command-line language-bash">
<code>mount /dev/sdb1 /mnt/disco</code>
</pre>

Veja abaixo algumas opções importantes:

<table class="table table-bordered">
	<tbody>
	<tr>
		<td> -a </td><td>Monta todos os dispositivos listados em /etc/fstab, exeto dispotivos com a opção noauto</td>
	</tr>
	<tr>
		<td>-l</td><td>lista todos os dispositivos montados, mesmo que executar o mount sem parametros</td>
	</tr>	
	<tr>
		<td>-o</td><td>Escolha as opções de montagem</td>
	</tr>	
	<tr>
		<td>-r / --read-only</td><td>Monta dispositivo apenas para leitura</td>
	</tr>	
	<tr>
		<td>-w / --rw</td><td>Monta para leitura e gravação</td>
	
	</tr>	
	<tr>
		<td>-U</td><td>Monta dispositivo pela sua label</td>
	</tr>	
	<tr>
		<td>-U</td><td>Monta dispositivo pelo seu UUID</td>
	</tr>	
	<tr>
		<td>-t</td><td>Tipo de sistema de arquivos a ser escolhido na montagem</td>
	</tr>
	</tbody>	
</table>

Se o comando mount é utilizado apenas com o dispositivo ou com o ponto de montagem, o mesmo será montado de acordo com os parametros definidos dentro do /etc/fstab.

## umont

Para desmontar um sistema de arquivos utilizamos o comando umont. Com o parametro -a desmonta todos os dispositivos que não estejam ocupados no momento.

Pode user utilizado apenas com o nome do dispositivo

<pre class="command-line language-bash">
<code>umount /dev/sdb1 </code>
</pre>

Ou apenas com o ponto de montagem

<pre class="command-line language-bash">
<code>umount /mnt/disco</code>
</pre>



## /etc/fstab

<pre class="command-line language-bash">
<code>cat /etc/fstab</code>

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# file system mount point   type  options       dump  pass
# / was on /dev/sda2 during installation
UUID=a08fb228-a38a-48d5-845f-075be67cd17d /               ext4    usrquota,grpquota,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=22B0-1D2D  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=a5955c2a-0ae2-49d2-b3a8-57c2028d4ed3 none            swap    sw              0       0
</pre>


Veja abaixo a Ordem e espeficiação de cada uma das colunas o fstab:


<table class="table table-bordered">
	<tr>	
		<td>File System</td><td>Nome do dispositivo a ser montado</td>
	</tr>	
	<tr>	
		<td>Mount Point</td><td>Ponto de montagem</td>
	</tr>	
		<tr>	
		<td>Type</td><td>Tipo do sistema de arquivos</td>
	</tr>	
		<tr>	
		<td>Options</td><td>Opções (Ver opções disponiveis na tabela anterior)</td>
	</tr>	
	<tr>	
		<td>Dump</td><td>Realiza o backup</td>
	</tr>
	<tr>	
		<td>Pass</td><td>Realiza verificação do dispositivo (segue a ordem dos numeros dessa coluna)</td>
	</tr>	
</table>


File System

* Candidatos devem ter a capacidade de configurar a montagem de sistemas de arquivos.
* Manualmente montar e desmontar sistemas de arquivos
* Configurar sistemas de arquivos para montar no momento do boot
* Configurar sistemas de arquivos montaveis por usuários communs

Termos e Utilitários:

* [/etc/fstab](#)
* [/media/](#)
* [mount](#)
* [umount](#)