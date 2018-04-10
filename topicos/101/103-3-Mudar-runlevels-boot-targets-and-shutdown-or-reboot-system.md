

## 101.3 Mudar runlevels boot targets e desligar ou reiniciar o sistema (Peso 3)

Ter a capacidade de gerenciar `SysVinit` runlevel or systemd boot target of the system. This objective includes changing to single user mode, shutdown or rebooting the system. Candidatos devem ter a capacidade de  to alert users before switching runlevels / boot targets and properly terminate processes. This objective also includes setting the default SysVinit runlevel or systemd boot target. It also includes awareness of Upstart as an alternative to SysVinit or systemd.

Definir o `runlevel` padrão ou o `target` do `boot`

Mudar entre `runlevels` e `boot targets` incluindo o `single user mode`

Desligar e reiniciar a maquina pela linha de comando

Alertar usuários antes de mudar de `runlevels` ou `boot target` ou ate mesmo em outros eventos considerados importantes.

Finalizar processos de modo correto


Termos e Utilitários:

### [/etc/inittab](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)

Esse arquivo contem informações sobre o runlevel padrão do sistema

### [shutdown](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)

Esse comando realiza o desligamento da maquina:

    usuario@maquina:$~ shutdown now

O comando acima  desliga a maquina imediatamente

    usuario@maquina:$~ shutdown now -r

O parametro `-r` reinicia a maquina 

COLOCAR AQUI OUTRAS FORMAS DE DESLIGAR COM TEMPO ETC....

### [init](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)

Esse comando realiza a alteração de run level

### [/etc/init.d/](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)


### [telinit](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)

Esse comando realiza a alteração de run level

### [systemd](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)


### [systemctl](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)


### [/etc/systemd/](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)


### [/usr/lib/systemd/](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)



### [wall](/101.3-mudar-runlevels-boot-targets-e-desligar-ou-reiniciar-o-sistema)

Esse comando realiza o envio de mensagem para todos os usuários logados no sistema