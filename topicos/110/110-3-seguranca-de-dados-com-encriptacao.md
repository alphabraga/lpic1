---
layout: page
title: 110.3 Segurança de Dados com-Encriptação (Peso 3)
permalink: /110/110-3-seguranca-de-dados-com-encriptacao
---

O candidato deve ter capacidade de utilizar tecnicas de chave publica para dar segurança a comunicação

### Entender as regras do servidor OpenSSH 2 em relação as chaves

É um protocolo de criptografia de rede, que cria um canal seguro de comunicação entre dois hosts, sendo um cliente e um servidor.

Essa comunicação é realizada utilizando chaves assimétricas, ou seja, um conjunto de chves publicas e privadas.

O `openssh2` é a implementação mais comum do `SSH` (Secure Shell).

Para poder entender o funcionamento do protocolo vamos seguir o seginte exemplo. Existem duas maquinas o `cliente` e o `servidor`. 

O cliente possui um par de chaves, sendo uma chave publica e uma privada, o mesmo tambem é válido para o servidor. 

A maquina  `cliente` e a maquina `servidor` iram fornecer para o outro a sua chave publica, ou seja, eles iram trocar as chaves publicas. 

E toda a vez que o `cliente` quiser realizar o envio de uma mensagem para o `servidor` o `cliente` irá realizar a criptografia da mensagem utilizando a chave publica que o `servidor` mandou para ele. 

Essa mesma mensagem será descriptiografada utilizando a chave privada do servidor. 

**É valido lembrar que a chave privada nunca deve ser compartilhada com ninguem em nenhuma hipotese**.    


### Realizar configuração e utilização básica do **cliente** OpenSSH 2

O diretorio onde ficam as configurações básicas do **cliente ssh** é `/etc/ssh`. E o arquivo de configuração é o `/etc/ssh/ssh_config`.


### Realizar configuração e utilização básica do **servidor** OpenSSH 2

O diretorio onde ficam as configurações básicas do **servidor ssh** tambem é o `/etc/ssh`. Mas o arquivo de configuração é o `/etc/ssh/sshd_config`. o `d` no nome do arquivo é referente a palavra **deamon**.

Vejamos abaixo os arquivos da pasta `/etc/ssh`:

<pre class="command-line language-bash">
<code>ls -l /etc/ssh</code>
-rw-------. 1 root root 125811 Aug 31  2017 moduli
-rw-r--r--. 1 root root   2047 Aug 31  2017 ssh_config
-rw-------. 1 root root   3888 May 21  2016 sshd_config
-rw-------. 1 root root    668 May 21  2016 ssh_host_dsa_key
-rw-r--r--. 1 root root    590 May 21  2016 ssh_host_dsa_key.pub
-rw-------. 1 root root    963 May 21  2016 ssh_host_key
-rw-r--r--. 1 root root    627 May 21  2016 ssh_host_key.pub
-rw-------. 1 root root   1675 May 21  2016 ssh_host_rsa_key
-rw-r--r--. 1 root root    382 May 21  2016 ssh_host_rsa_key.pub
</pre>

Nesse diretorio podemos verificar que exitem arquivos com `key` e `key.pub` no final. Esses arquivos são as chaves privadas e publicas respectivamente. No momento da instalação do servidor ele já cria chaves utilizando o algoritimo `dsa` e `rsa`.

É importante verificar as permissões dos arquivos. Veja que as chaves privadas apenas podem ser lidas e escritas pelo dono, no caso o root. Já as cheves publicas podem ser **lidas** por outros usuários. 


### Realizar configuração básica do GnuPG, utilização e revogação

### Entender túneis SSH (incluindo tnúneis X11) 

### ssh

Para realizar a conexão a um servidor utilizando o protocolo `ssh` usamos o comando ssh. É preciso ter em mãos as seguintes informações: nome do usuário remoto, senha desse usuário e por fim o endereço do servidor que desejamos acessar (pode ser endereço, ip ou ate mesmo um hostname). Veja o comando abaixo:


<pre class="command-line language-bash">
	<code>ssh usuario-remoto@nome-da-maquina</code>
	Digite a senha:
</pre> 

Existe também a sintaxe:

<pre class="command-line language-bash">
	<code>ssh -l usuario-remoto nome-da-maquina</code>
	Digite a senha:
</pre> 

Podemos ainda omitir o nome do usuário, dessa forma:

<pre class="command-line language-bash" data-user="damian">
	<code>ssh nome-da-maquina</code>
	Digite a senha:
</pre> 

Omitindo o nome do usuário, o ssh admite que você está tendando fazer login com um usuário de mesmo nome que o atual. Ou seja `damian`.

### ssh-keygen

### ssh-agent

### ssh-add

###  ~/.ssh/id_rsa and id_rsa.pub

###  ~/.ssh/id_dsa and id_dsa.pub

###  /etc/ssh/ssh_host_rsa_key and ssh_host_rsa_key.pub

###  /etc/ssh/ssh_host_dsa_key and ssh_host_dsa_key.pub

### ~/.ssh/authorized_keys


### ssh_known_hosts

### gpg


### ~/.gnupg/