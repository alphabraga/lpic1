---
layout: page
title: 103.1 Trabalhando com a Linha de Comando (Peso 4)
permalink: 103/103-1-trabalhando-com-a-linha-de-comando
---

## bash

O bash é o nome do tipo de shell que estamos utilizando. O `bash`, tambem conhecido como Bourne Again Shell é o que é cobrado na LPI. Existem outros tipos de shell como `csh`, `sh`, `ksh`.

## Executando comandos em sequencia

O shell tambem tem a opção de executar os comandos em sequencia. E para isso nós utilizamos os operadores:

# ; 

Esse operador permite a execução em sequencia dos comandos, os comandos são simplesmnete executados não importando se eles esão corretos ou ate mesmo sua execução foi realizada com sucesso. Como no exemplo abaixo:

Comandos executados em sequencia

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>comando1; comando2; comando3</code>
</pre>

## &&

Só executa o proximo comando caso o anterior tenha sido executado com sucesso

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>comando1 && comando2 && comando3</code>
</pre>

## echo 

Imprime uma string na tela

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>echo "Linux"</code>
</pre>

## env

Lista todas as variáveis de ambiente (environment) setadas:

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>env</code>
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
XDG_CONFIG_DIRS=/etc/xdg/xdg-mate:/etc/xdg
LC_TELEPHONE=pt_BR.UTF-8
LANG=en_US.UTF-8
DISPLAY=:0
SHLVL=1
LOGNAME=alphabraga
LANGUAGE=en_US
MANDATORY_PATH=/usr/share/gconf/mate.mandatory.path
COMPIZ_CONFIG_PROFILE=mate
XDG_VTNR=7
LC_NAME=pt_BR.UTF-8
SESSION_MANAGER=local/helix:@/tmp/.ICE-unix/2152,unix/helix:/tmp/.ICE-unix/2152
XAUTHORITY=/home/alphabraga/.Xauthority
QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/alphabraga
COLORTERM=mate-terminal
XDG_SESSION_ID=c2
PWD=/home/alphabraga
DESKTOP_SESSION=mate
LC_ADDRESS=pt_BR.UTF-8
DEFAULTS_PATH=/usr/share/gconf/mate.default.path
XDG_SESSION_DESKTOP=mate
GDMSESSION=mate
LC_IDENTIFICATION=pt_BR.UTF-8
</pre>

Você pode tambem usar o comando `printenv` para exibir a mesma informação. 

Para remover uma variável utilizamos o comando: 

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>unset NOMEVAR</code>
</pre>	

## export 

Coloca uma variável no ambiente, para colocar ela definitivamente no enviroment você deve colocar esse export dentro de .bash_profile ou em /etc/environment .

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>MEUNOME="ALFREDO"</code>
<code>echo $MEUNOME</code>
ALFREDO
<code>export MEUNOME</code>
<code>env | grep MEUNOME</code>
MEUNOME=ALFREDO
</pre>	

No exemplo acima foi criada a variável `MEUNOME` com o valor `ALFREDO`. Em seguida ela foi exportada utilziando o comando `export`, e por fim com o comando `env` verificamos se essa variável foi mesmo exportada. 

## pwd 

pwd significa `print working directory`, ou seja, exibir o diretorio corrente



<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>pwd</code>
/home/alphabraga
</pre>	


## set

O comando `set` quando executado sem parametros imprime variáveis de ambiente e variáveis locais além de funcões. O output dele é bem maior comparado ao `env`.

Acho que isso tá errado!!
**Comando relacionado com a capacidade de evitar sobrescrita de arquivos.**


## man 

Exibe os manuais dos comandos exemplo:

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>man cp</code>
CP(1)                                                                  User Commands

NAME
       cp - copy files and directories

SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --archive
              same as -dR --preserve=all

       --attributes-only
              don't copy the file data, just the attributes

</pre>	

Os dados refentes aos manuais ficam no diretorio /usr/share/man

## uname 

Exibe dados do so. Como versão do kernel distribuicao etc.

Com o parametro `-a` todas as informações, o `a` é de `all` .


<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>uname -a</code>
Linux helix 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
</pre>	


Só a informação a respeito do release do kernel informe o `-r`

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>uname -r</code>
4.13.0-37-generic
</pre>	


## history

O comando history é um comando interno do bash. Ele lista o conteudo do ~/.bash_history númerando as linhas. do output.

<pre class="language-bash command-line" data-user="alpahbraga" data-host="localhost">
<code>history</code>
1115  ldd jekyll 
1116  whereis jekyll 
1117  ldd /usr/bin/jekyll
1118  whereis java
1119  ldd /usr/bin/java
1120  whatis ldd
1121  exit
1122  cd Projects/my-awesome-site/
1123  jekyll serve
1124  whereis ln
1125  ldd /bin/ln
1126  locate sln
1127  sln
1128  cd /lib64/
1129  ls -la
1130  cat ld-linux-x86-64.so.2 
1131  q!
1132  sudo aptitude update
</pre>	

## ~/.bash_history

É o arquivo que contem o historico dos comandos. É esse aquivo que exibido pelo comando `history` . 

### Diferença entre .bashrc e .bash_profile

O .bash_profile é executado quando é realizado o login no bash, já o .bashrc é executado sempre se abre o bash dentro do gnome. é comum ver distribuições que colocam no final do arquivo .bash_profile o comando "source ~/.bashrc" dessa forma variáveis e configrações definidas em ambos os arquivos ficam disponiveis.