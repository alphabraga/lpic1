---
layout: page
title: 110.2 Configure a Seguranca do Host
permalink: /110/110-2-configure-a-seguranca-do-host
---

* Candidatos devem ter conhecimantos de como confiurar a segurança básica de um host
* Conhecimeneto de senhas do `shadow` e como elas funcionam
* Desligar serviços de rede que  não estão sendo utilizados de fato
* Entender as regras de do TCP wrappers

## /etc/nologin


O arquivo `/etc/nologin` por padrão não existe no sistema de arquivos. Quando ele é criado impede o login de todos os usuarios do sistema com excessão do root. E no momento do login o contéudo do arquivo é exibido 

## /etc/passwd


Caso na linha corresponde ao usuário exista a entrada "/bin/false" ou "/usr/sbin/nologin" no final da linha significa que o usuário não realiza login, essa conta de usuário é apenas para serviços etc...

## /etc/shadow

Antigamente as senhas dos usuários ficavam no arquivo `passwd`. E o passwd é lido pelos usuarios comuns. Essa situação acabava crianda um problema de segurança uma vez que diversos usuários teriam acesso a senha de outros usuários.

Para resolver isso foi criado o arquivo `shadow`. Abaixo vamos ver as permissões do arquivo `shadow`:

<pre class="command-line language-bash">
<code>ls -l /etc/shadow</code>
-rw-r----- 1 root shadow 1393 Oct  3 20:29 /etc/shadow
</pre>

Usuários comuns não podem ser o `shadow`. Vejamos abaixo, o usuario de nome `carlos` tentando ler o arquivo `shadow`:


<pre class="command-line language-bash">
<code>cat /etc/shadow</code>
cat: /etc/shadow: Permission denied
</pre>

Mas com o usuario root podemos ver o conteudo do arquivo:

<pre class="command-line language-bash" data-user="root">
<code>cat /etc/shadow</code>
messagebus:*:17494:0:99999:7:::
uuidd:*:17494:0:99999:7:::
lightdm:*:17494:0:99999:7:::
ntp:*:17494:0:99999:7:::
avahi-autoipd:*:17494:0:99999:7:::
avahi:*:17494:0:99999:7:::
dnsmasq:*:17494:0:99999:7:::
colord:*:17494:0:99999:7:::
geoclue:*:17494:0:99999:7:::
speech-dispatcher:!:17494:0:99999:7:::
hplip:*:17494:0:99999:7:::
kernoops:*:17494:0:99999:7:::
pulse:*:17494:0:99999:7:::
nm-openvpn:*:17494:0:99999:7:::
rtkit:*:17494:0:99999:7:::
saned:*:17494:0:99999:7:::
usbmux:*:17494:0:99999:7:::
alphabraga:$6$7ywJrxab$HO/sepmXKEevLRuV22PUAuNfPDJoD429aaP2CG/45htoX.lpwPbIjkf7jV6vC3p2Otq4lfW11RUjljt8T8gYd0:17712:0:99999:7:::
mysql:!:17745:0:99999:7:::
</pre>


Existem cenários, geralmente em sistemas linux antigos, onde as senhas ainda estão no arquivo `passwd`. Quando isso é identificado é preciso executar i comando pwconv que transfere as senhas do arquivo `passwd` para o `shadow`


## Desligar serviços que não estão sendo utilizados


Existem serviços que por não estar sendo utilizados ou por serem desconhecidos e por isso representaram um risco ao sistema devem ser desabilitados.


Vamos desabilitar o serviço `cups-browsed`, vamos estabelecer aqui que ele não é cricual para o funcionamento de nosso servidor e portando vamos desativa-lo.

Usando o comando abaixo verificamos que o mesmo esta sendo executado:

<pre class="command-line language-bash">
<code>ps axu | grep cups-browsed </code>	
root      7739  0.0  0.2 274812  9664 ?        Ssl  13:55   0:00 /usr/sbin/cups-browsed
</pre>


Podemos ainda verficar se ele esta sendo executado com o comando: 

<pre class="command-line language-bash">
<code>systemctl status cups-browsed </code>	
root      7739  0.0  0.2 274812  9664 ?        Ssl  13:55   0:00 /usr/sbin/cups-browsed
</pre>


Para para o serviço e em seguida desabilitar o mesmo do sistema executamos:

<pre class="command-line language-bash">
<code>systemctl stop cups-browsed</code>	
<code>systemctl disable cups-browsed</code>	
</pre>

Podemos checar se os comandos executados foram realizados com sucesso com 

<pre class="command-line language-bash">
<code>systemctl is-enabled cups-browsed</code>	
</pre>


Podemos verificar se existem outros serviços que podem ser desabilitados no arquivo `/etc/initab`


Ou você tem em execução em sua maquina o serviço inetd ou xinetd

## /etc/inetd.conf

É o principal arquivo de configuração do `inetd`

## /etc/xinetd.d/

## /etc/xinetd.conf

## /etc/inetd.d/

## /etc/inetd.conf

## /etc/inittab

## /etc/init.d/

## /etc/hosts.allow

## /etc/hosts.deny