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

## startx

Comando que inicia o servidor X

## xdpyinfo

texto aqui!

## xvinfo 

Exibe informações sobre as configurações suportadas pelo dispositivo.

	prints out the capabilities of any video adaptors associated with the display that are accessible through the X-Video
	extension.

### Qual o arquivo de configuração em que são definidos os diretórios que contém as fontes que podem ser utilizadas pelo servidor X?



Termos e utilitários:

* /etc/X11/xorg.conf
* xhost
* DISPLAY
* xwininfo
* xdpyinfo
* X