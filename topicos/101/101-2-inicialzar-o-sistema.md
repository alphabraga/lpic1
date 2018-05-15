---
layout: page
title: 101.2 Inicializar o Sistema (Peso 3)
permalink: /101/101-2-inicializar-o-sistema
---

Guiar o sistema durante o processo de boot.

Prover comandos comuns para o `bootloader` e opções para o Kernel no momento do `boot`.
Demonstrar conhecimento da sequência de `boot` da BIOS até a finalização do boot.
Conhecimento de `SysVinit` e `systemd`.
Mensagens de `Awareness` da inicialização do sistema.
Verificar eventos de `boot` nos arquivos de log.

## Processo de Boot

Abaixo podemos visualizar a sequência de boot:

	BIOS > MBR > BOOTLOADER > KERNEL > INIT

* A BIOS localiza e executa a MBR
* O MBR (Master Boot Record) executa o Bootloader
* O Bootloader (GRUB/LILO) seleciona e executa o Kernel e initird 
* O Kernel executa o **/sbin/init**
* O init executa os programas do runlevel/target definido 

## dmesg

Esse comando exibe informações sobre o boot do sistema com se fosse um log.

<pre class="language-bash command-line">
<code>dmseg</code>
[    0.000000] microcode: microcode updated early to revision 0x84, date = 2018-01-21
[    0.000000] Linux version 4.10.0-38-generic (buildd@lgw01-amd64-059) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 (Ubuntu 4.10.0-38.42~16.04.1-generic 4.10.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-38-generic root=UUID=d63830a6-1c03-4e03-9b4b-5f6e5d3e373a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
[    0.000000] x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000903ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000090400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
</pre>


## BIOS

A palavra `BIOS` significa Basic Input Output System. Nada mais é que um firmware que guarda as configurações básicas da máquina como data e hora, ordem de dispositivos para o boot, configuraçõs básicas de teclado e etc.

## Bootloader

O Bootloader é um software que reside na MBR que é responsável por realizar o carregamento do Kernel do Linux. Existem dois tipos de bootloader's o LILO, mais antigo, e o GRUB que é que mais atual e que consequentemente é mais cobrado na LPI.

## Kernel

O Kernel interage a um nível mais baixo dentro do Linux. Ele coordena a utilização de memória, dispositivos, processamento etc.

## initramfs

> O initramfs é uma imagem de sistema de arquivos da raiz (root) utilizado para realizar o boot do Kernel, ele é disponibilizado como um arquivo cpio comprimido.

Fonte: https://wiki.debian.org/initramfs

Ele também é carregado pelo bootloader para dar suporte ao Kernel. Ele é temporário e carregado em mémoria RAM.

## init

Tem a função de iniciar os primeiros processos e serviços do Linux. **É o processo de ID 1**
É o sistema que configura o os serviços que rodam no Linux. Ele funciona utilizando o conceito de `runlevels`.

Principais inits utilizados

### SysVinit

### systemd

Systemd é um gerenciador de sistema e de serviços para o Linux, compativel com o SysV. Systemmd utiliza sockets e D-BUS para inicialização de serviços, oferece a iniciação por demanda de `daemons`, rastreia processos utilizando o controle de grupos do Linux, suporta `snaphotting` e o `restoring` de um determinado estado do sistema.

### Upstart