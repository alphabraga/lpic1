---
layout: page
title: 102.1 Desenhar o Layout do Disco Rigido (Peso 2)
permalink: /102/102-1-desenhando-o-layout-do-disco-rigido
---

## Definição de Partição

Partição é uma parte de um disco. O particionamento nada mais é do que dividir um disco rigido em partes. Os nomes dessas partições no Linux são definidas na seguinte forma. Nome do disco mais número da partição. Por exemplo:


* **sda1**
* **sda2**
* **sda3**
* **sda4**


## Definição de ponto de montagem

As partições precisam ser adicionandas a arvore de diretórios do Linux. E ai entram os pontos de montagem que nada mais são que do diretórios que estão associados e esssas partições. Sendo assim dizemos que a partição


## Diretório / (root) 

Diretório raiz do Linux	

## Diretório /var

Arquivos "variáveis", como logs, base de dados, páginas Web e arquivos de e-mail.

>...variable data files. This includes spool directories and files, administrative and logging data, and transient and temporary files.
Fonte FHS 

## Diretório home

Local onde ficam os arquivos de usuários comuns

## Diretório /boot

Arquivos do Boot loader (ex: núcleo, initrd).

## Partição de swap

É importante lembrar que uma partição com ID 82 (0x82) será designada para área de swap, enquanto que partições com ID 83 (0x83), Linux Native, serão utilizadas para arquivos do Linux.


Ter a capacidade de desenhar o esquema de particionamento  de discos para sistemas Linux.


* Alocar `filesystem` e espaço de `swap` para alocar partições e discos
* Customize o design de acordo com as caracteriscicas e uso do sistema
* Asegure que a partição de boot esta de acordo com os requerimentos de boot da arquitetura de hardware
* Conhecimentos básicos das funcionalidades do LVM

### Termos e Utilitários:

* / (root) filesystem
* /var filesystem
* /home filesystem
* /boot filesystem
* swap space
* mount points
* partitions