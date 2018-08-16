---
layout: page
title: 105.1 
permalink: /105/105-1-modifique-e-utilize-o-ambientye-shell
---

105.1 Modifique e utilize o ambiente do Shell Peso 4


Candidatos deve ser capazes de modificar ambientes do shel para atender as necessidades dos usuários. E tambem é necessário que saibam modificar ambientes globais e perfils de usuários


* Definir variáveis de ambeintes (como o PATH), no momento do login ou quando um novo shell é iniciado
* Escrver funcções em Bash para comando frequentemente utilizados 
* Manter `skeleton directories` para novas contas de usuários
* The following is a partial list of the used files, terms and utilities:

## source

O comando source serve para executar arquivos de script. **Mas qual a diferença entre ele e o `sh` ou `bash` ?


## /etc/bash.bashrc

Esse arquivo é utilizado para definir funções e variáveis de ambiente.

## /etc/profile

Esse arquivo é utilizado para definir funções e variáveis de ambiente.

## env

Esse comando lista as variáveis de ambiente

## export

O comando export realiza o exportação de uma variável para o ambiente do `shell`.


## set

Esse comando lista todos as variáveis de ambiente e as funções definidas

## unset

Remove uma variável do ambiente.

## ~/.bash_profile


Arquivo que contem variaveis, funcoes e alias de um usuário expecifico

## ~/.bash_login

Arquivo que contem variaveis, funcoes e alias de um usuário expecifico


## ~/.profile


Arquivo que contem variaveis, funcoes e alias de um usuário expecifico

## ~/.bashrc

Arquivo que contem variaveis, funcoes e alias de um usuário expecifico

## ~/.bash_logout

Esse arquivo é envocado sempre que realizamos o logout do sistema e ele executa tudo que estiver dentro dele anntes de realizar o logout

## function

Vamos aprender como definir uma função no linux

	function meunome {

		echo "Alfredo"
	}

Ou então:


	sobrenome(){

		echo "Braga"
	}


## alias

O `alias` tem a funçõe de definir apelidos para comandos. Imagine que você utiliza o comando :


	nmap -Pn 127.0.01


Diversas vezes em seu terminal linux. E ter que digitar todo esse comando varias vezes pode ser entediante além de improdutivo
Mas você pode resolver esse problema você pode fazer um do `alias`. Basta definir no arquivo `~/.bash_bashrc` a linha:


	alias scanlocal="nmap -Pn 127.0.0.1"

Em seguida basta ler o arquivo `~/.bash_bashrc` com o comando `source`


	source ~/.bash_bashrc

Agora sim! O seu apelido esta disponivel em seu ambiente shell


	scanlocal	

## lists