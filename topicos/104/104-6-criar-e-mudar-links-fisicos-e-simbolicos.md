---
layout: page
title: 104.5 Criar e Mudar links Físicos e Simbolicos (Peso 2)
permalink: 104/104-6-criar-e-mudar-links-fisicos-e-simbolicos
---

Cirar e gerenciar links físicos e simbolicos em um arquivo.

* Criar links
* Identificar links fisicos e simbolicos
* Copiar versus linking files
* Utilizar links para dar suporte a tarefas administrativas de sistema

## ln

### Links Físicos ou Hard Links

Links são apontamentos para arquivos. A utilização de links é bem comum para facilitar a administração do sistema.

Para exemplificar melhor vamos criar um arquivo chamado `aplicacao.conf`

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>echo "Minhas Configurações" > aplicacao.conf</code>
</pre>

Agora vamos criar um link físico desse arquivo. Para fazer isso basta utilizar o comando `ln`


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>ln aplicacao.conf ap.conf</code>
</pre>

Com o comando acima criamos um arquivo, ou melhor, um link físico do arquivo `aplicacao.conf` chamado `app.conf`. Se executarmos o comando `ls` nesses dois arquivos com o parametro `-i` veremos que os dois apontam para o mesmo `inode`.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>ls -li app.conf aplicacao.conf</code>
11010096 -rw-rw-r-- 2 alphabraga alphabraga 23 Abr 11 22:09 aplicacao.conf
11010096 -rw-rw-r-- 2 alphabraga alphabraga 23 Abr 11 22:09 app.conf
</pre>

A primeira coluna do output do comando `ls` exibe os `inodes` dos arquivos. Fica evidente que os dois arquivos tanto o link físico e o arquivo possuem o mesmo número de `inode`, ou seja, os dois arquivos na verdade apontam para o mesmo endereço no disco o que significa que os dois possuem o mesmo conteudo. Executando um `cat` nos dois arquivos podemos comprovar isso.


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>cat aplicacao.conf </code>
Minhas Configurações
<code>cat app.conf </code>
Minhas Configurações
</pre>


Uma alteração realizada utilizando o arquivo `app.conf` afeta o `aplicacao.conf`. Isso porque na verdade eles representam o mesmo endereço no disco. Podemos observar isso abaixo:

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>"Novas Configurações" >> aplicacao.conf </code>
<code>cat app.conf </code>
Minhas Configurações
Novas Configurações
</pre>

Mesmo alterando apenas o arquivo `aplicacao.conf` o arquivo `app.conf` tambem exeibe as modificações.

Caso seja realizada a exclusão de um dos arquivos (link ou arquivo) nada ocorre. A exclusão de um não interfere no outro.

Não é possivel criar links físicos em partições distintas. Veja no exemplo abaixo onde o usuario tenta criar links físicos em partições distintas.


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>df -h</code>
Sist.fichs      Tama  Ocup Livre Uso% Montado em
udev            1,9G     0  1,9G   0% /dev
tmpfs           385M  6,3M  378M   2% /run
/dev/sda2       231G   71G  149G  33% /
tmpfs           1,9G  4,2M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda1       511M  3,5M  508M   1% /boot/efi
tmpfs           385M   52K  385M   1% /run/user/1000
<code>touch /boot/efi/teste</code>
<code>ln /boot/efi/teste /link-teste</code>
ln: falhou ao criar hard link '/link-teste' => '/boot/efi/teste': Link entre dispositivos inválido
</pre>


**Não é permitida a criação de links físicos de pastas**. Veja abaixo:

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>mkdir minhas-configs</code>
<code>ln minhas-configs link-minhas-configs</code>
ln: minhas-configs: ligação persistente não autorizada para a pasta
</pre>


### Links Simbolicos

O para criar links simbolicos utilizamos o comando `ln` com parametro `-s`. Veja o exemplo abaixo:


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>touch novas-configs.app</code>
<code>ln -s novas-configs.app link-novas-configs</code>
<code>ls -li novas-configs.app link-novas-configs</code>
11010574 lrwxrwxrwx 1 alphabraga alphabraga 17 Abr 11 22:44 link-novas-configs -> novas-configs.app
11010481 -rw-rw-r-- 1 alphabraga alphabraga  0 Abr 11 22:43 novas-configs.app
</pre>

Já vemos de cara que eles possuem `inodes` diferentes, essa já seria uma diferença de links simbolicos e físicos. Alem disso vemos que existe um caracter `l` proximo aos caracteres de permissões. O `l` é de link, esse caractere não aparece em links físicos. Um link simbilico sempre tera as pemissoes `rwxrwxrwx`.

Podemos ainda criar links simbolicos de pastas. Essa já é a segunda diferença entre links fisicos e simbolicos. Veja o exemplo abaixo:


<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>mkdir minhas-configs && cd touch minhas-configs/pricipal.conf minhas-configs/secundaria.conf</code>
<code>ln -s minhas-configs configs</code>
<code>cd configs</code>
<code>ls -l</code>
-rw-rw-r-- 1 alphabraga alphabraga 0 Abr 11 22:41 pricipal.conf
-rw-rw-r-- 1 alphabraga alphabraga 0 Abr 11 22:41 secundaria.conf
</pre>

Já em links a exclusão do arquivo ou pasta na qual um link simbolico aponta causa um problema. Vamos ter um link quebrado que aponta para um lugar que não existe mais. Voltando ao primeiro exemplo dessa sessão onde foi criado um link simbolico chamado `link-novas-configs` iremos realizar a exclusão do arquivo `novas-configs.app` que é pra onde nosso link aponta.

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>ls -li novas-configs.app link-novas-configs </code>
11010574 lrwxrwxrwx 1 alphabraga alphabraga 17 Abr 11 22:44 link-novas-configs -> novas-configs.app
11010481 -rw-rw-r-- 1 alphabraga alphabraga  0 Abr 11 22:43 novas-configs.app
<code>rm novas-configs.app</code>
<code>cat link-novas-configs </code>
cat: link-novas-configs: Ficheiro ou directoria inexistente
</pre>

A referência foi perdida pois o arquivo na qual o link simbolico faz referencia não existe mais.

E possivel fazer links simbolicos de uma partição apontando um arquivo em outra partição. Veja abaixo:

<pre class="language-bash command-line" data-user="alphabraga" data-host="localhost">
<code>df -h</code>
Sist.fichs      Tama  Ocup Livre Uso% Montado em
udev            1,9G     0  1,9G   0% /dev
tmpfs           385M  6,3M  378M   2% /run
/dev/sda2       231G   71G  149G  33% /
tmpfs           1,9G  4,2M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda1       511M  3,5M  508M   1% /boot/efi
tmpfs           385M   52K  385M   1% /run/user/1000
<code>ln -s /boot/efi/teste /link-teste</code>
</pre>