---
layout: page
title: 103.2 Processando fluxos de texto utilizando filtros (Peso 3)
permalink: 103/103-2-processando-fluxos-de-texto-utilizando-filtros
---

Candidatos devem ter habilidade de aplicar filtros em fluxos de texto.

## cat

De acordo com o man o comando `cat`:

> cat - concatena arquivos e imprimi na saída padrão

Vamos utilizar o comando para enviar para a saída padrão o conteúdo do arquivo `linux-loop.txt`.

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat linux-loop.txt</code>
Linux Corp.


Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp
</pre>

Agora vamos utilizar o mesmo comando para concatenar dois arquivos:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat linux-loop.txt windows-loop.txt</code>
Linux Corp.


Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.
Linux Corp.Windows Corp.
Windows Corp.

Windows Corp.
Windows Corp.

Windows Corp.
Windows Corp.
Windows Corp.




Windows Corp.
Windows Corp.
Windows Corp.
Windows Corp.
Windows Corp.
Windows Corp.
Windows Corp.
</pre>

Parametros do comando cat

## -n

Ele númera as linhas da saída:

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat -n linux-loop.txt</code>
1 Linux Corp.
2 
3 
4 Linux Corp.
5 Linux Corp.
6 Linux Corp.
7 Linux Corp.
8 Linux Corp.
9 Linux Corp.
10 Linux Corp.
11 Linux Corp.
12 Linux Corp.
13 Linux Corp.  
</pre>

## -b

Ele só númera as linhas não brancas

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat -n linux-loop.txt</code>
1 Linux Corp.


2 Linux Corp.
3 Linux Corp.
4 Linux Corp.
5 Linux Corp.
6 Linux Corp.
7 Linux Corp.
8 Linux Corp.
9 Linux Corp.
10 Linux Corp.
11 Linux Corp.
</pre>

## -A

Com o parametro -A todos os carateres especiais são exibidos

<pre class="command-line language-bash" data-user="alphabraga" data-host="localhost">
<code>cat -A linux-loop.txt</code>
Linux Corp.$
$
$
Linux Corp.^I^I$
Linux Corp.$
Linux Corp.$
Linux Corp.$
Linux Corp.$
Linux Corp.$
Linux Corp.$
Linux Corp.^I^I$
Linux Corp.$
Linux Corp.%    
</pre>

O `$` significa final de linha e o `^I` representa um tab.
            


## cut

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## expand

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## fmt

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## head

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## join

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## less

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## nl

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## od

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## paste


Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.


## pr

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## sed

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## sort

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## split

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## tail

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.

## tr

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## unexpand

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## uniq

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.



## wc

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur vulputate lectus eu nunc varius, a commodo ligula tempus. Aenean rhoncus consequat massa, in interdum tellus laoreet blandit. Ut a urna sollicitudin, ullamcorper turpis eu, suscipit nibh. Sed semper justo non dignissim lacinia. Suspendisse sit amet faucibus eros. Praesent vestibulum consectetur nulla in ultricies. Vestibulum auctor eget felis eu malesuada. Mauris sit amet tellus a nibh mattis pulvinar. Etiam tristique velit in est sollicitudin, eu feugiat felis tristique. Duis sed dui fermentum, sodales lorem vestibulum, tristique urna.


