---
layout: page
title: 104.4 Gerenciar Cotas de Disco (Peso 1)
permalink: 104/104-4-gerenciar-cotas-de-disco
---

Ter a capacidade de gerenciar cotas de disco de usuários.

Configurar cotas de disco para um sistema de arquivos 
Editar, verificar e gerar relatórios de cotas


Para se beneficiar do uso de cotas devemos habilitar o mesmo no /etc/fstab e colocar o parametro de `quota` para usuários e grupos. Adicionando o **usrquota**, **grpquota**


<pre class="language-bash command-line">
<code>vim /fstab</code>
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# / was on /dev/sda2 during installation
UUID=a08fb228-a38a-48d5-845f-075be67cd17d /               ext4    errors=remount-ro,usrquota,grpquota 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=22B0-1D2D  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=a5955c2a-0ae2-49d2-b3a8-57c2028d4ed3 none            swap    sw              0       0
</pre>

Apos aplicar esses dois parametros na partição "/" ao reiniciarmos o sistema, executarmos o comando `quotacheck -cugm` dois arquivos serão criados no "/" (se tivessemos editado outra partição esses arquivos seriam criados na raiz da partição) dois arquivos são criados:


Como já foi dito ou você reinicia a máquina ou executa o comando:


<pre class="laguage-bash command-line">
<code>quotacheck -cugmf /</code>
</pre>

O `c` é para criar, `u` usuários, `g` grupos, `m` e o `f` forcar e a partiçao.

* aquota.user
* aquota.group

## Termos e Utilitários

## quota

## edquota


## repquota


## quotaon