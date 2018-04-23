---
layout: page
title: 101.2 Inicializar o Sistema (Peso 3)
permalink: /101/101-2-inicializar-o-sistema
---

Guiar o sistema durante o processo de boot.

Prover comandos comuns para o `boot loader` e opções para o Kernel no momento do `boot`
Demonstrar conhecimento da sequência de `boot` da BIOS até a finalização do boot
Conhecimento de `SysVinit` e `systemd`
Menssagens de `Awareness` da inicialização do sistema
Verificar eventos de `boot` nos arquivos de log 

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

A palavra `BIOS` significa Basic Input Output System. E nada mais é que um firmware que guarda as configurações básicas da maquina como data e hora, ordem de dispositivos para o boot, configuraçõs basicas de teclado etc..

## bootloader

## kernel

## initramfs

## init

É o sistema que configura o os serviços que rodam no Linux. Ele funciona utilizando o conceito de `runlevels`.

## SysVinit


## systemd

Teste