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

Additional locations for library files can specified in the /etc/ld.so.conf file. The ld.so.conf file may include all files under the /etc/ld.so.conf.d directory, depending on your distribution. Listing 5 shows the contents of /etc/ld.so.conf on a 64-bit Fedora 12 system.

## Carregar bibliotecas Compartilhadas

Termos e Utilitários:

* [ldd](#)
* [ldconfig](#)
* [/etc/ld.so.conf](#)
* [LD_LIBRARY_PATH](#)