---
layout: page
title: 106.1 Instale e configure o X11 (Peso 2)
permalink: /106/106-1-instale-e-configure-X11
---

Cadidados devem ser capazes de instalar e configurar o X11
Verificar se a placa de video e monitor é compativel com o servidor X
Precauções sobre fontes do servidor X
Entendimento básico e conhecimento do arquivo de configuração do servidor X

## /etc/X11/xorg.conf

É o principal arquivo de configuação do servidor X11. Em distribuições mais recentes esse arquivo não é criado por padrão. Sendo necessario criar o mesmo manualmente atravez do comando `Xorg -configure`. Mas lembre-se para executar o comando é necessario que o servidor X11 esteja parado. 
Esse arquivo pode ser utilizado principalmente no caso  de configurações específicas necessárias para algum dispositivo que esteja utilizando.

Veja abaixo o arquivo `xorg.conf`:


	Section "ServerLayout"
		Identifier     "X.org Configured"
		Screen      0  "Screen0" 0 0
		InputDevice    "Mouse0" "CorePointer"
		InputDevice    "Keyboard0" "CoreKeyboard"
	EndSection

	Section "Files"
		ModulePath   "/usr/lib/xorg/modules"
		FontPath     "/usr/share/fonts/X11/misc"
		FontPath     "/usr/share/fonts/X11/cyrillic"
		FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
		FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
		FontPath     "/usr/share/fonts/X11/Type1"
		FontPath     "/usr/share/fonts/X11/100dpi"
		FontPath     "/usr/share/fonts/X11/75dpi"
		FontPath     "built-ins"
	EndSection

	Section "Module"
		Load  "glx"
	EndSection

	Section "InputDevice"
		Identifier  "Keyboard0"
		Driver      "kbd"
	EndSection

	Section "InputDevice"
		Identifier  "Mouse0"
		Driver      "mouse"
		Option	    "Protocol" "auto"
		Option	    "Device" "/dev/input/mice"
		Option	    "ZAxisMapping" "4 5 6 7"
	EndSection

	Section "Monitor"
		Identifier   "Monitor0"
		VendorName   "Monitor Vendor"
		ModelName    "Monitor Model"
	EndSection

	Section "Device"
	        ### Available Driver options are:-
	        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
	        ### <percent>: "<f>%"
	        ### [arg]: arg optional
	        #Option     "ShadowFB"           	# [<bool>]
	        #Option     "DefaultRefresh"     	# [<bool>]
	        #Option     "ModeSetClearScreen" 	# [<bool>]
		Identifier  "Card0"
		Driver      "vesa"
		BusID       "PCI:0:2:0"
	EndSection

	Section "Screen"
		Identifier "Screen0"
		Device     "Card0"
		Monitor    "Monitor0"
		SubSection "Display"
			Viewport   0 0
			Depth     1
		EndSubSection
		SubSection "Display"
			Viewport   0 0
			Depth     4
		EndSubSection
		SubSection "Display"
			Viewport   0 0
			Depth     8
		EndSubSection
		SubSection "Display"
			Viewport   0 0
			Depth     15
		EndSubSection
		SubSection "Display"
			Viewport   0 0
			Depth     16
		EndSubSection
		SubSection "Display"
			Viewport   0 0
			Depth     24
		EndSubSection
	EndSection



Esse arquivo não existe mais em distribuições mais recentes pelo fato que o Servidor X já identifica de forma automatica no momento do boot todas as configurações do monitor, não sendo necessaria a criação do arquivo.

Ao rodar o comando `Xorg -configure` é criado um arquivo `xorg.conf.new` com as configurações detectadas. Em seguida esse arquivo deve ser movido para `/etc/X11/xorg.conf`

### Principais Sessões do arquivo xorg.conf

* Module : Carregamento dinâmico de módulos.
* Files : Arquivos utilizados pelo X (modulos e fontes)
* InputDevice : COnfigurações sobre Teclado ou sobre o Mouse
* Device : informações sobre placa de video
* Monitor: Configurações específicas do monitor utilizado, como HorizSync e VertRefresh.
* Screen : A seção screen é uma combinação entre o monitor e a placa de vídeo, dizendo ao X quais os modos que ele pode trabalhar. Na sub-seção Display, são informados por exemplo as resoluções suportadas, color depth (bits por pixel), e etc.


## startx

Comando que inicia o servidor X

## xdpyinfo

texto aqui!

## xvinfo 

Exibe informações sobre as configurações suportadas pelo dispositivo.

	prints out the capabilities of any video adaptors associated with the display that are accessible through the X-Video
	extension.

vamos executar o comndo para ver o output gerado:


	name of display:    :0
	version number:    11.0
	vendor string:    The X.Org Foundation
	vendor release number:    11804000
	X.Org version: 1.18.4
	maximum request size:  16777212 bytes
	motion buffer size:  256
	bitmap unit, bit order, padding:    32, LSBFirst, 32
	image byte order:    LSBFirst
	number of supported pixmap formats:    7
	supported pixmap formats:
	    depth 1, bits_per_pixel 1, scanline_pad 32
	    depth 4, bits_per_pixel 8, scanline_pad 32
	    depth 8, bits_per_pixel 8, scanline_pad 32
	    depth 15, bits_per_pixel 16, scanline_pad 32
	    depth 16, bits_per_pixel 16, scanline_pad 32
	    depth 24, bits_per_pixel 32, scanline_pad 32
	    depth 32, bits_per_pixel 32, scanline_pad 32
	keycode range:    minimum 8, maximum 255
	focus:  window 0x3c00007, revert to Parent
	number of extensions:    29
	    BIG-REQUESTS
	    Composite
	    DAMAGE
	    DOUBLE-BUFFER
	    DPMS
	    DRI2
	    DRI3
	    GLX
	    Generic Event Extension
	    MIT-SCREEN-SAVER
	    MIT-SHM
	    Present
	    RANDR
	    RECORD
	    RENDER
	    SECURITY

## xwininfo

Comando que exibe informações sobre uma janela já aberta do X:

	 alphabraga@helix  ~  xwininfo 

	xwininfo: Please select the window about which you
	          would like information by clicking the
	          mouse in that window.
	xwininfo: Window id: 0x3c00006 "xwininfo"
	  Absolute upper-left X:  0
	  Absolute upper-left Y:  50
	  Relative upper-left X:  0
	  Relative upper-left Y:  26
	  Width: 1920
	  Height: 1030
	  Depth: 32
	  Visual: 0x9b
	  Visual Class: TrueColor
	  Border width: 0
	  Class: InputOutput
	  Colormap: 0x3c00005 (not installed)
	  Bit Gravity State: NorthWestGravity
	  Window Gravity State: NorthWestGravity
	  Backing Store State: NotUseful
	  Save Under State: no
	  Map State: IsViewable
	  Override Redirect State: no
	  Corners:  +0+50  -0+50  -0-0  +0-0
	  -geometry 190x52+0-0



### Qual o arquivo de configuração em que são definidos os diretórios que contém as fontes que podem ser utilizadas pelo servidor X?

Resposta: /etc/xorg.conf CONFIRMAR



Termos e utilitários:

* /etc/X11/xorg.conf
* xhost
* DISPLAY
* xwininfo
* xdpyinfo
* X