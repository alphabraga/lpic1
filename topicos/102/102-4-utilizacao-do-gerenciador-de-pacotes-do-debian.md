---
layout: page
title: 102.4 Utilização do gerenciador de pacotes do Debian (Peso 3)
permalink: /102/102-4-utilizacao-do-gerenciador-de-pacotes-do-debian
---

Ter a capacidade de realizar o gerenciamento de pacotes usando as ferramentas para gerenciamento de pacotes do Debian.

Instalar, atualizar  e desistalar pacotes binários do Debian.
Procurar pacotes contendo arquivos espeficos ou bibliotecas que podemo ou não ser instaladas
Obter informações sobre pacotes, como versão, conteudo, depencias, integridade e status da instalação (em outras palavras verificar se o pacotes esta ou não instalado)


## dpkg

Utilitário Debian para realizar a instalação de pacotes .deb. Possue os argumentos

## -l

Para listar todos os pacotes instalados


<pre class="language-bash command-line">
<code>dpkg -l</code>
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome                                        Versão                                       Arquitectura Descrição
+++-===========================================-============================================-============-================================================================================
ii  a11y-profile-manager-indicator              0.1.10-0ubuntu3                              amd64        Accessibility Profile Manager - Unity desktop indicator
ii  account-plugin-facebook                     0.12+16.04.20160126-0ubuntu1                 all          GNOME Control Center account plugin for single signon - facebook
ii  account-plugin-flickr                       0.12+16.04.20160126-0ubuntu1                 all          GNOME Control Center account plugin for single signon - flickr
ii  account-plugin-google                       0.12+16.04.20160126-0ubuntu1                 all          GNOME Control Center account plugin for single signon
ii  accountsservice                             0.6.40-2ubuntu11.3                           amd64        query and manipulate user account information
ii  acl                                         2.2.52-3                                     amd64        Access control list utilities

</pre>

Ou verificar um pacote especifico

<pre class="language-bash command-line">
<code>dpkg -l perl</code>

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome                         Versão              Arquitectura        Descrição
+++-============================-===================-===================-=============================================================
ii  perl                         5.22.1-9ubuntu0.2   amd64               Larry Wall's Practical Extraction and Report Language
</pre>

## -L

Listar todos os arquivos que pertencem a um pacote



<pre class="language-bash command-line">
<code>dpkg -L apache2</code>
/.
/etc
/etc/apache2
/etc/apache2/mods-enabled
/etc/apache2/conf-enabled
/etc/apache2/apache2.conf
/etc/apache2/mods-available
/etc/apache2/mods-available/setenvif.conf
/etc/apache2/mods-available/proxy_express.load
/etc/apache2/mods-available/auth_basic.load
/etc/apache2/mods-available/session_dbd.load
/etc/apache2/mods-available/deflate.load
/etc/apache2/mods-available/authz_core.load
/etc/apache2/mods-available/authn_core.load
/etc/apache2/mods-available/cgid.load
/etc/apache2/mods-available/cache_disk.conf
/etc/apache2/mods-available/auth_form.load
/etc/apache2/mods-available/log_debug.load
/etc/apache2/mods-available/cache_socache.load
/etc/apache2/mods-available/mpm_worker.conf
</pre>

## --get-selections

Assim como os parametro `-l` o `--get-selections` relaciona os pacotes instalados


<pre class="language-bash command-line">
<code>dpkg --get-selections</code>
a11y-profile-manager-indicator                  install
account-plugin-facebook                         install
account-plugin-flickr                           install
account-plugin-google                           install
accountsservice                                 install
acl                                             install
acpi-support                                    install
acpid                                           install
activity-log-manager                            install
adduser                                         install
adium-theme-ubuntu                              install
</pre>

## -I

O parametro `-I` serve para verificar as informações sobre um pacote debian. Por exemplo, vamos inspecionar o pacote do virtualbox.

<pre class="language-bash command-line">
<code>dpkg -i virtualbox-5.2_5.2.6-120293_Ubuntu_xenial_amd64.deb</code>
 73557468 bytes de tamanho: arquivo de controle=21540 bytes.
    1615 bytes,    20 linhas      control              
   65873 bytes,   718 linhas      md5sums              
    3434 bytes,   103 linhas   *  postinst             #!/bin/sh
    1853 bytes,    53 linhas   *  postrm               #!/bin/sh
    2435 bytes,    71 linhas   *  preinst              #!/bin/bash
    1681 bytes,    59 linhas   *  prerm                #!/bin/sh
     275 bytes,     8 linhas      shlibs               
    2531 bytes,    55 linhas      templates            
      60 bytes,     2 linhas      triggers             
 Package: virtualbox-5.2
 Version: 5.2.6-120293~Ubuntu~xenial
 Architecture: amd64
 Maintainer: Oracle Corporation info@virtualbox.org
 Installed-Size: 182291
 Pre-Depends: debconf (>= 1.1) | debconf-2.0
 Depends: libc6 (>= 2.15), libcurl3 (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.97), libfontconfig1 (>= 2.11.94), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:3.4), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libpng12-0 (>= 1.2.13-4), libsdl1.2debian (>= 1.2.11), libsm6, libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 5.2), libvpx3 (>= 1.5.0), libx11-6, libx11-xcb1, libxcb1 (>= 1.8), libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxrender1, libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
 Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, kmod | kldutils | module-init-tools, linux
</pre>

## - - contents

Lista todos os arquivo que estão dentro do .deb

<pre class="language-bash command-line">
<code>dpkg --contents virtualbox-5.2_5.2.6-120293_Ubuntu_xenial_amd64.deb</code>
drwxr-xr-x root/root         0 2018-01-15 13:40 ./
drwxr-xr-x root/root         0 2018-01-15 13:40 ./etc/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./etc/init.d/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./etc/vbox/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/scalable/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/scalable/apps/
-rw-r--r-- root/root     65439 2017-12-19 04:15 ./usr/share/icons/hicolor/scalable/apps/virtualbox.svg
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/scalable/mimetypes/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/40x40/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/40x40/apps/
-rw-r--r-- root/root      6227 2017-12-19 04:16 ./usr/share/icons/hicolor/40x40/apps/virtualbox.png
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/40x40/mimetypes/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/64x64/
drwxr-xr-x root/root         0 2018-01-15 13:40 ./usr/share/icons/hicolor/64x64/apps/
-rw-r--r-- root/root      7884 2017-12-19 04:15 ./usr/share/icons/hicolor/64x64/apps/virtualbox.png
</pre>

## -s

Para descobrir o status de um pacote e saber se ele esta instalado

## -S

Podemos tambem descobrir qual pacote arquivo criou determinado arquivo passando apenas o caminho absoluto do arquivo para o dpkg, basta usar o parametro `-S` (seria de source)

<pre class="language-bash command-line">
<code>dpkg -S /usr/share/doc/bash/INTRO.gz</code>
bash: /usr/share/doc/bash/INTRO.gz
</pre>

## -i

Para realizar a instalação do pacote

## -r

Para remover um pacote

<pre class="language-bash command-line">
<code>dpkg -r nome.deb</code>
</pre>


O pacote não esta mais disponivel para uso. Mas ele ainda aparece se executarmos um dpkg -l ou um --get-selections. No --get-selections ele aparece como deinstall (isso mesmo deinstall) ou desistalado.

Para remover um pacote totalmente do sistema devemos usar o `-P` ou o `--purge`. E ai sim ele apaga todos os arquivos de config todos os vestigios desse pacote no sistema.


### Termos e Utilitários:

* /etc/apt/sources.list
* dpkg
* dpkg-reconfigure
* apt-get
* apt-cache
* aptitude

