---
layout: page
title: 109.2 Configuracao básica de redes (Peso 4)
permalink: /109/109-2-configuracao-basica-de-redes
---

Candidatos devem ter habilidade em ver, mudar e verificar configurações nos hosts

* Manualmente e automaticamente configurar interfaces de rede
* Configuração básica de TCP/IP
* Setar uma rota padrão

## Classes de Rede

As classes são definidas pelo primeiro octeto do endereço. Abaixo as sequencias:

* Classe A: 1 - 126 (1.0.0.0 até 126.255.255.255) 
* Classe B: 128 - 191 (128.0.0.0 - 191.255.255.255)  
* Classe C: 192 - 223 (192.0.0.0 - 223.255.255.255)

Observe que a faixa 127 é reseervada para loopback


### Endereço Privado

* Classe A: 10.0.0.0 até 10.255.255.255
* Classe B: 172.16.0.0 até 172.31.255.255
* Classe C: 192.168.0.0 até 192.168.255.255

### Endereço Público

??????????????


### Mascaras de Rede

* Classe A: 255.0.0.0 / 8
* Classe B: 255.255.0.0 / 16
* Classe C: 255.255.255.0 / 24


## /etc/hostname
## /etc/hosts
## /etc/nsswitch.conf
## ifconfig
## ifup
## ifdown
## ip
## route
## ping