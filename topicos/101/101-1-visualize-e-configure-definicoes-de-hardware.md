---
layout: page
title: 101.1 Visualize e configure definições de hardware (Peso 2)
permalink: /101/101-1-visualize-e-configure-definicoes-de-hardware
---

Nesse tópico será necessário a habilidade de visualizar e configurar sistemas de hardware fundamentais. Isso pode ser feito de duas formas **com comandos específicos** e **vendo arquivos no sistema de arquivos especial**.

* Feramentas e utilitários para listar diversas de informações de hardware (lsusb, lspci.)
* Feramentas e utilitários para manipular dispositivos USB
* Entendimento conceitual de [sysfs](#), [udev](#), [dbus](#)

## /sys/

Faz parte da partição virtual pois não guarda de fato arquivos e sim informações dinâmicas.Esse é um diretorio que é mais focado em **guardar informações de dispositivos de hardware**.

O `/sys/` é montado utilizando um tipo de filesystem chamado de `sysfs`. O comando `df` exibe o sistema de arquivos `sysfs`:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>df -t sysfs -a
Sist.fichs     1K-blocos  Ocup Livres Uso% Montado em
sysfs                  0     0      0    - /sys
</code>
</pre>



Veja abaixo o conteudo do diretório:

    ├── block
    │   ├── loop0 -> ../devices/virtual/block/loop0
    │   ├── loop1 -> ../devices/virtual/block/loop1
    │   ├── loop2 -> ../devices/virtual/block/loop2
    │   ├── loop3 -> ../devices/virtual/block/loop3
    │   ├── loop4 -> ../devices/virtual/block/loop4
    │   ├── loop5 -> ../devices/virtual/block/loop5
    │   ├── loop6 -> ../devices/virtual/block/loop6
    │   ├── loop7 -> ../devices/virtual/block/loop7
    │   └── sda -> ../devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
    ├── bus
    │   ├── acpi
    │   ├── clockevents
    │   ├── clocksource
    │   ├── container
    │   ├── cpu
    │   ├── edac
    │   ├── event_source
    │   ├── gpio
    │   ├── hdaudio



## /proc/

Guarda informações sobre **processos ativos no sistema e recursos de hardware**. Nesse diretório ficam arquivos que são cobrados na LPI 101 como o [/proc/interrups](#), [/proc/dma](#), [/proc/ioports](#) e o [/proc/modules](#). 

Abaixo conteúdo do diretório:

    ├── acpi
    ├── asound
    ├── buddyinfo
    ├── bus
    ├── cgroups
    ├── cmdline
    ├── consoles
    ├── cpuinfo
    ├── crypto
    ├── devices
    ├── diskstats
    ├── dma
    ├── driver
    ├── execdomains
    ├── fb
    ├── filesystems
    ├── fs
    ├── interrupts
    ├── iomem
    ├── ioports
    ├── irq
    ├── kallsyms
    ├── kcore
    ├── keys
    ├── key-users
    ├── kmsg


## /proc/ioports

Esse arquivo contém informações sobre **endereços de memória utilizados pela CPU para se comunicar com dispositivos de hardware**. Abaixo o conteúdo do arquivo `/proc/ioports`


    0000-0cf7 : PCI Bus 0000:00
    0000-001f : dma1
    0020-0021 : pic1
    0040-0043 : timer0
    0050-0053 : timer1
    0060-0060 : keyboard
    0061-0061 : PNP0800:00
    0064-0064 : keyboard
    0070-0077 : rtc0
    0080-008f : dma page reg
    00a0-00a1 : pic2
    00c0-00df : dma2
    00f0-00ff : fpu
    00f0-00f0 : PNP0C04:00
    02f8-02ff : serial
    03f8-03ff : serial
    0400-043f : pnp 00:02
    0440-045f : pnp 00:02
    0460-047f : pnp 00:02
    0580-05ff : pnp 00:02
    0580-0583 : ACPI PM1a_EVT_BLK
    0584-0587 : ACPI PM1a_CNT_BLK
    0588-058b : ACPI PM_TMR
    05a0-05af : ACPI GPE0_BLK
    05b0-05b3 : iTCO_wdt.0.auto
    05b0-05b3 : iTCO_wdt
    05d0-05d0 : ACPI PM2_CNT_BLK
    05e0-05ff : iTCO_wdt.0.auto
    05e0-05ff : pnp 00:02
    05e0-05ff : iTCO_wdt



## /proc/interrupts

IRQ, ou Interrups Requests, são canais de comunicação que são utilizados pelos dispositivos para enviar comandos para a CPU. Esses comandos ou sinais são enviados a CPU e ela tem que parar de fazer o que estiver fazendo a atender a essas requisições. Os canais de número menor tem maior prioridade que os demais.


Veja a tabela abaixo com informações básicas sobre o IRQ:

     IRQ 0  - Timmer do sistema (relógio)
     IRQ 1  - Teclado
     IRQ 2  - Cascateador de IRQ
     IRQ 3  - Portal Serial 2
     IRQ 4  - Portal Serial 1
     IRQ 5  - Livre
     IRQ 6  - Drive de Disquetes
     IRQ 7  - Porta Paralela
     IRQ 8  - Relogio da CMOS
     IRQ 9  - Placa de Video
     IRQ 10 - Livre
     IRQ 11 - Controlador USB
     IRQ 12 - Porta PS/2
     IRQ 13 - Coprocessador Aritmético
     IRQ 14 - IDE Primária
     IRQ 15 - IDE Secundária

Executando o comando `cat /proc/interrups` temos o output abaixo:

             CPU0       CPU1       CPU2       CPU3       
      0:         16          0          0          0  IR-IO-APIC   2-edge      timer
      1:          2       1543      15908       1133  IR-IO-APIC   1-edge      i8042
      7:          0          0          0          0  IR-IO-APIC   7-fasteoi   INT3432:00, INT3433:00
      8:          1          0          0          0  IR-IO-APIC   8-edge      rtc0
      9:        104        115       1280         83  IR-IO-APIC   9-fasteoi   acpi
     12:         18       8604     177407      10087  IR-IO-APIC  12-edge      i8042
     40:          0          0          0          0  DMAR-MSI   0-edge      dmar0
     41:          0          0          0          0  DMAR-MSI   1-edge      dmar1
     42:        147        280      23940        358  IR-PCI-MSI 327680-edge      xhci_hcd
     43:       8302       2062      59673       2578  IR-PCI-MSI 512000-edge      ahci[0000:00:1f.2]
     44:          0          0          0          0  IR-PCI-MSI 1048576-edge      enp2s0
     45:        542         79     128084     144606  IR-PCI-MSI 32768-edge      i915
     46:          9          5          0          0  IR-PCI-MSI 360448-edge      mei_me
     47:        195      62775        136         33  IR-PCI-MSI 524288-edge      ath10k_pci
     48:        333        241         10         67  IR-PCI-MSI 442368-edge      snd_hda_intel:card1
     49:         60         66         55          2  IR-PCI-MSI 49152-edge      snd_hda_intel:card0
    NMI:         79         93         91         88   Non-maskable interrupts
    LOC:     220605     232216     218771     215687   Local timer interrupts
    SPU:          0          0          0          0   Spurious interrupts
    PMI:         79         93         91         88   Performance monitoring interrupts
    IWI:          0          1          1          0   IRQ work interrupts
    RTR:          1          0          0          0   APIC ICR read retries

Os números nas colunas `CPUn` exibe o número de vezes que uma requisição é enviada para aquele canal. Podemos fazer um teste e após realizar a digitação de algum texto no teclado e verificar que o número de requisições aumentou no canal `1`.


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat /proc/interrupts | egrep "^  1:"
  1:        135       2448      27391       2109  IR-IO-APIC   1-edge      i8042
</code>
</pre>


## /proc/dma

DMA significa Direct Memory Access, ou seja, acesso direto a memória, esse arquivo contém endereços de mémoria utilizado pelo hardware na qual não precisam do intermédio da CPU para acessa-los. Isso permite uma comunicação mais dinâmica uma vez que um interédiario foi removido.

## /proc/meninfo

Exibe informações de memória. É com as informações desse arquivo que o comando `free` trabalha.


## /proc/cpuinfo

Exibe informações de processador

## /proc/modules

Esse arquivo contem informações sobre os modulos utilizados pelo Linux. É esse arquivo que é lido pelo comando [lsmod](#).

Abaixo iremos realizar um cat no arquivo /proc/modules 


<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat /proc/modules"</code>
quota_v2 16384 2 - Live 0x0000000000000000
quota_tree 20480 1 quota_v2, Live 0x0000000000000000
parport_pc 32768 0 - Live 0x0000000000000000
ppdev 20480 0 - Live 0x0000000000000000
lp 20480 0 - Live 0x0000000000000000
parport 49152 3 parport_pc,ppdev,lp, Live 0x0000000000000000
autofs4 40960 2 - Live 0x0000000000000000
hid_generic 16384 0 - Live 0x0000000000000000
usbhid 49152 0 - Live 0x0000000000000000
hid 118784 2 hid_generic,usbhid, Live 0x0000000000000000
i915 1830912 85 - Live 0x0000000000000000
i2c_algo_bit 16384 1 i915, Live 0x0000000000000000
drm_kms_helper 167936 1 i915, Live 0x0000000
</pre>

Podemos observar acima nomes de modulos carregados pelo sistema. Mas o comando lsmod disponibiliza essas mesmas informações de forma mais legível.

## /dev/

Esse diretório faz referências a dispositivos do sistema inclusive de armazenamento. É o processo de nome `udev` que monta esses dispositivos que ficam exibidos nesse diretório.

## dbus

Tem duas funções:

* Realiza a comunicação entre processos
* Informa aos processos a situação de dispositivos de hardware

## lsmod

Lista os modulos que estão sendo utilizados pelo sistema. Existe uma coluna que informa se o módulo é utilizado por outros módulos e o número de utilizações.

<pre class="language-bash command-line">
  <code>lsmod</code>
Module                  Size  Used by
psmouse               139264  0
uas                    24576  0
usb_storage            69632  1 uas
rfcomm                 77824  14
ccm                    20480  2
pci_stub               16384  1
vboxpci                24576  0
bnep                   20480  2
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxnetadp,vboxnetflt,vboxpci
joydev                 20480  0
btusb                  45056  0
input_leds             16384  0
btrtl                  16384  1 btusb
dell_wmi               16384  0
i2c_designware_platform    16384  0
dell_wmi_aio           16384  0
i2c_designware_core    20480  1 i2c_designware_platform
sparse_keymap          16384  2 dell_wmi,dell_wmi_aio
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
</pre>

## lspci

Lista os dispositivos de hardware que estão no barramento PCI do computador.

<pre class="language-bash command-line">
  <code>lspci</code>
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 20)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
</pre>

No lado esquerdo do output vemos os IDS dos dispositivos e do lado direito uma breve descrição sobre os mesmo. 
Para ver mais detalhes sobre os dispositivos utilizamos a opção `-v`, para exibir as informações de forma verbosa usamos `-vv`, para exibir mais informações ainda com `-vvv`.


<pre class="language-bash command-line">
  <code>lspci -v</code>
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
        Subsystem: Samsung Electronics Co Ltd Broadwell-U Host Bridge -OPI
        Flags: bus master, fast devsel, latency 0
        Capabilities:
        Kernel driver in use: bdw_uncore

00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09) (prog-if 00 [VGA controller])
        DeviceName:  Onboard IGD
        Subsystem: Samsung Electronics Co Ltd Broadwell-U Integrated Graphics
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: 
        Kernel driver in use: i915
        Kernel modules: i915

00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
        Subsystem: Samsung Electronics Co Ltd Broadwell-U Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f731c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: 
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
        Subsystem: Samsung Electronics Co Ltd Broadwell-U Processor Thermal Subsystem
        Flags: fast devsel, IRQ 16
        Memory at f7310000 (64-bit, non-prefetchable) [size=32K]
        Capabilities:
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
</pre>

Para ver mais informações apenas de um dispositivo específico utilizamos a opção `-s` seguido do ID do dispositivo (o `s` seria de seleção)

<pre class="language-bash command-line">
  <code>lspci -s00:04.0 -v </code>
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
        Subsystem: Samsung Electronics Co Ltd Broadwell-U Processor Thermal Subsystem
        Flags: fast devsel, IRQ 16
        Memory at f7310000 (64-bit, non-prefetchable) [size=32K]
        Capabilities: 
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
</pre>

## lsusb

Lista os dispositivos de hardware que estão no barramento USB do computador. Semelhante ao comando `lspci` esse comando com a opção `-v` exibe uma saída mais verbosa e também com a opção `-s` exibe as informações apenas de um dispositivo ** passando o número de BUS e DEVICE**

Listando todos os dispositivos no barramento USB:


<pre class="language-bash command-line">
  <code>lsusb</code>
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 2232:1063 Silicon Motion 
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 1ea7:0064  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
</pre>
 

Listando um dispositivo espefico, utilizando `-s bus:device`

<pre class="language-bash command-line">
<code>lsusb -s001:002</code>
Bus 001 Device 002: ID 1ea7:0064
</pre>

Listagem verbosa dos dispositivos:

<pre class="language-bash command-line">
<code>lsusb -v</code>
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Device Descriptor:
      bLength                18
      bDescriptorType         1
      bcdUSB               3.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         3 
      bMaxPacketSize0         9
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0003 3.0 root hub
      bcdDevice            4.13
      iManufacturer           3 
      iProduct                2 
      iSerial                 1 
      bNumConfigurations      1
      Configuration Descriptor:
        bLength                 9
        bDescriptorType         2
        wTotalLength           31
        bNumInterfaces          1
        bConfigurationValue     1
        iConfiguration          0 
        bmAttributes         0xe0
          Self Powered
          Remote Wakeup
        MaxPower                0mA
        Interface Descriptor:
    Couldn't open device, some information will be missing
          bLength                 9
          bDescriptorType         4
          bInterfaceNumber        0
          bAlternateSetting       0
          bNumEndpoints           1
          bInterfaceClass         9 Hub
    Couldn't open device, some information will be missing
</pre>


É importante frizar que os módulos estão localizados no diretório `/lib/modules/`.

##modinfo

Segundo `man` o comando `modinfo` tem a seguinte descrição:

> Exibir informação sobre modulos do Kernel do Linux

Sendo assim o `modinfo` exibe informações detalhadas a respeito de um módulo

Abaixo vamos utilizar o modinfo para exibir informações a respeito do módulo

<pre class="language-bash command-line">
  <code>modinfo joydev</code>
filename:       /lib/modules/4.13.0-41-generic/kernel/drivers/input/joydev.ko
license:        GPL
description:    Joystick device interfaces
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     E0E4A2F5EAE529EF007ECC6
alias:          input:b*v*p*e*-e*1,*k*2C0,*r*a*m*l*s*f*w*
alias:          input:b*v*p*e*-e*1,*k*130,*r*a*m*l*s*f*w*
alias:          input:b*v*p*e*-e*1,*k*120,*r*a*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*6,*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*8,*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*2,*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*0,*m*l*s*f*w*
depends:        
intree:         Y
name:           joydev
vermagic:       4.13.0-41-generic SMP mod_unload 
</pre>

Podemos ainda pegar informação apenas de um campo especifico desse modulo utilizando o parâmetro -F

<pre class="language-bash command-line">
<code>modinfo -F license joydev</code>
GPL
</pre>


##rmmod

Comando utilizado para remover um módulo. Ignorando as dependencias.


<pre class="language-bash command-line">
  <code>sudo rmmod psmouse</code>
</pre>


Se executarmos o `lsmod` veremos que o `psmouse` não pararece mais na listagem:


<pre class="language-bash command-line">
  <code>lsmod | grep psmouse</code>
</pre>

##insmod

Comando para instalar o modulo, ignorando as dependências. **Observe que para remover um módulo com rmmod passamos como parâmetro apenas o nome do módulo, já com o insmod passamos o caminho para o arquivo**.

<pre class="language-bash command-line">
  <code>sudo insmod /lib/modules/4.10.0-38-generic/kernel/drivers/input/mouse/psmouse.ko</code>
</pre>


## modprobe

Carrega um módulo no sistema. Com o parâmetro `-r` ele remove um modulo. **O diferencial desse comando e que ele carrega ou descarrega automaticamente as dependêcias do módulo definido no comando**. E nele você passa tanto para remover quanto para carregar apenas o nome do modulo não o arquivo.

## Identificar e Configurar o Hardware

### IDE

falta

### PATA

falta

### SATA

falta

### SCSI

falta