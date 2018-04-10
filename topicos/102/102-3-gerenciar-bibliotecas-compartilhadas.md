---
layout: page
title: 102.3 Gerenciar Bibliotecas Compartilhadas (Peso 1)
permalink: /102/102.3-nstalacao-do-linux-e-gerenciamento-de-pacotes
---

Esse tópico vai abordar a capacidade de determinar que bibliotecas comparilhadas programas dependem e instalar uma se necessário.

## Identificar bibliotecas compartilhadas

Para ideitificar que bibliotecas comparilhadas um determinado executável utiliza basta digitar o comando `ldd`, como no exemplo abaixo:

	usuario@maquina:~$ ldd /usr/bin/java

		linux-vdso.so.1 =>  (0x00007fff45dcf000)
		libjli.so => not found
		libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fea0f3ae000)
		/lib64/ld-linux-x86-64.so.2 (0x00007fea0f778000)

## Locais típicos de bibliotecas compartilhadas

## Carregar bibliotecas Compartilhadas

Termos e Utilitários:

* [ldd](#)
* [ldconfig](#)
* [/etc/ld.so.conf](#)
* [LD_LIBRARY_PATH](#)