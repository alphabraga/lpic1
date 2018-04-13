---
layout: page
title: 102.3 Gerenciar Bibliotecas Compartilhadas (Peso 1)
permalink: /102/102-3-gerenciar-bibliotecas-compartilhadas
---

##Introdução

Esse tópico vai abordar a capacidade de determinar que bibliotecas comparilhadas programas dependem e instalar uma se necessário.

Uma biblioteca pode ser compreendida como um grupo de funcionalidades que programas utilzam para realizar determinadas tarefas. Quando estamos criando um programa podemos definir essas bibliotecas de forma estatica ou dinamica ao executavel.

> Static link significa que o programa final irá conter a biblioteca no proprio executável (lib.a). Dynamic link significa que as bibliotecas necessarias são carregadas na memoria RAM quando o programa é executado (lib.so).

Quando desenvolvedores escrevem uma aplicação, eles fazem o uso de bibliotecas existentes para prover a funcionalidade necessaria a sua aplicação. Quando a aplicação é compilada existem duas opções disponiveis:

Construir a aplicação com todas as bibliotecas compiladas dentro da aplicação. Isso é conhecido como `statically linking`. Como vantagem a aplicação não possui dependencias, mas o programa fica maior e uma mesma biblioteca pode ficar carregada na memoria.

Utilizar o `Dynamically link` que chama as depencias no momento da execução. Executáveis que utilizam `Dynamically links`  são menores em comparação as mesmas aplicações desenvolvidas utilziando o metodo anterior, já que eles não contem biblioteca.  Atulização permite que programas em execução que utilizam a mesma biblioetca , compartilhme muma unica cópia dessa mesma biblioetca, o que ajuda na utilização de memoria. Por essa razão a maioria dos programas utilizam `Dynamically links`.

## Identificar bibliotecas compartilhadas

Para ideitificar que bibliotecas comparilhadas um determinado executável utiliza basta digitar o comando `ldd` seguido do executável, como no exemplo abaixo:

<pre class="language-bash command-line">
<code>ldd /usr/bin/java</code>
linux-vdso.so.1 =>  (0x00007fff45dcf000)
libjli.so => not found
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fea0f3ae000)
/lib64/ld-linux-x86-64.so.2 (0x00007fea0f778000)
</pre>


## Locais típicos de bibliotecas compartilhadas

Para que o Linux encontre as bibliotecas requeridas pela aplicação em tempo de execução, o Linux precisa saber onde encontra-las. Por padrão ele busca nesses locais:

* /lib: - Amplamente utilizada por programas localizadas em /bin
* /usr/lib - Utilizada principalmente por programas em /usr/bin

## /etc/ld.so.conf

Locais adicionais para que o sistema busque por bibliotecas podem ser definidos em `/etc/ld.so.conf`. Em distribuições baseadas em debian esse arquivo aponta para o diretorio `/etc/ld.so.conf.conf.d` .

<pre class="language-bash command-line">
<code>cat /etc/ld.so.conf</code>
include /etc/ld.so.conf.d/*.conf
</pre>

Ou seja manda incluir todos os arquivos com a extensão `.conf` que estão dentro da pasta `/etc/ld.conf.d`


<pre class="language-bash command-line">
<code>ls -l /etc/ld.so.conf.d/</code>
total 12
-rw-rw-r-- 1 root root 38 Nov 24  2014 fakeroot-x86_64-linux-gnu.conf
-rw-r--r-- 1 root root 44 Jan 27  2016 libc.conf
-rw-r--r-- 1 root root 68 Abr 14  2016 x86_64-linux-gnu.conf
lrwxrwxrwx 1 root root 43 Jan 25 14:22 x86_64-linux-gnu_EGL.conf -> /etc/alternatives/x86_64-linux-gnu_egl_conf
lrwxrwxrwx 1 root root 42 Jan 25 14:22 x86_64-linux-gnu_GL.conf -> /etc/alternatives/x86_64-linux-gnu_gl_conf
</pre>

## Carregar bibliotecas Compartilhadas

Vamos realizar a inclusão de bibliotecas `fake` em nosso sistema e em seguida vamos verificar se ele realmente as carregou. 


Primeiramente vamos criar a lib fake

<pre class="language-bash command-line" data-user="root" data-host="localhost">
<code>mkdir /tmp/my-libs</code>
<code>cp /usr/lib/x86_64-linux-gnu/libuniquewm-1.2.so.9 /tmp/my-libs/libuniq-1.2.so.9</code>
</pre>

Em seguida vamos editar o arquivo `/etc/ld.so.conf` e incluir nosso diretorio com a nova lib. E recarregar as libs com o comando `ldconfig`

<pre class="language-bash command-line" data-user="root" data-host="localhost">
<code>echo "/tmp/my-libs/" >> /etc/ld.so.conf</code>
<code>ldconfig</code>
</pre>


Para ver as libs carregas basta digitar o mesmo comando com o parametro `-p`. Mas como queremos apenas ver se a nossa lib foi carregada usaremos o comando `grep`

<pre class="language-bash command-line" data-user="root" data-host="localhost">
<code>ldconfig -p | grep /tmp/my-libs/</code>
libuniquewm-1.2.so.9 (libc6,x86-64) => /tmp/my-libs/libuniquewm-1.2.so.9
</pre>


Existe ainda a váriavel de ambiente `LD_LIBRARY_PATH` que tambem pode ser utilizada para informar o local de bibliotecas no sistema.

Vale ainda resaltar que o comando ldconfig na verdade atualiza o arquivo `/etc/ld.so.cache` . É esse arquivo que é utilziado como banco de dados pelo Linux.


Termos e Utilitários:

* [ldd](#)
* [ldconfig](#)
* [/etc/ld.so.conf](#)
* [LD_LIBRARY_PATH](#)