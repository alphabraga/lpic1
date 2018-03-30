---
layout: page
title: 102 Instalação do Linux e Gerenciamento de Pacotes
permalink: /102/instalacao-do-linux-e-gerenciamento-de-pacotes
---

## bash


## echo 

Imprime uma string na tela

## env

Lista todas as variáveis de ambiente (environment) setadas:

	$alphabraga@vortex:~ env #lista todos as variaveis de ambiente

Você pode tambem usar o comando printenv para exibir a mesma informação 

Altera o valor de uma variável de ambiente,

Para remover uma variável utilizamos o comando: 

	unset NOMEVAR

## export 

Coloca uma variavel no ambiente, para colocar ela definitivamente no enviroment voce deve coloca esse export dentro de .bash_profile ou em /etc/environment


## pwd 

pwd significa print working directory, ou seja, exibir o diretorio corrente


## set

Comando relacionado com a capacidade de evitar sobrescrita de arquivos.


## man 

Exibe os manuais dos comandos exemplo:

	man cp

## uname 

Exibe dados do so. Como versão do kernel distribuicao etc.


## history

## .bash_history


### Diferença entre .bashrc e .bash_profile

O .bash_profile é executado quando é realizado o login no bash, já o bashrc é executado sempre se abre o bash dentro do gnome. é comum ver distrbuiçõies que colocam no final do arquivo .bash_profile o comando "source ~/.bashrc" dessa forma variaveis configrações definidas em ambos os arquivos ficam disponiveis