---
layout: page
title: Realizar operações básicas de edição de arquivos utilizando o VI (Peso 3)
permalink: /103/103-8-realizar-operacoes-basicas-de-edicao-de-arquivos-utilizando-o-VI
---

Ter a capacidade de editar arquivos de texto utilizado o VI. Esse tópico tambem inclui a navegação utilizando o VI, modos do VI, inserindo, editando, excluindo, copiando e encontrando.


## [vi](#)

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis molestie sit amet erat vel aliquam. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Nulla facilisi. Aliquam malesuada non erat ut imperdiet. Aliquam et fringilla dolor. Morbi turpis quam, mattis in cursus non, posuere feugiat nibh. Donec ac est nisi. Proin pellentesque faucibus tristique.

veja aqui uma imagem com vários comandos do VIM

[![IMAGE ALT TEXT HERE](/lpic1/img/vi-help-sheet.jpg)](/lpic1/img/vi-help-sheet.jpg)


## Corelação de setas e teclas

<v^>
HJKL

Integer ut urna imperdiet, tempus lacus a, congue dui. Vivamus lacinia ac diam vitae ornare. Aenean vitae massa tellus. Vestibulum placerat, erat at dictum bibendum, est elit sagittis erat, sed maximus lacus justo porta sapien. Praesent dignissim nibh odio. Curabitur a ipsum sed justo fermentum rhoncus. Fusce eget justo vitae quam facilisis egestas ut at tellus. Integer pretium magna non est sagittis, quis tincidunt eros tincidunt. In in justo aliquet, tincidunt metus eget, pulvinar nibh. Quisque risus elit, viverra non venenatis in, convallis vel erat.

## [/, ?](#)

O VI em modo de visualização tem acapacidade derealiozar busca por caracteres basta digitar `Esc` e digitar `/` e fazer a sua busca ao final digite `Enter`. O cursor ficara em cima da primeira ocorrência para ir para a proxima ocorrencia digite `n` e para a anterior digite `N`. O `?` faz exatamente a mesma coisa só que ordem inversa. A busca começa no fim do documento e termina no topo, e com o `n` você sobre o arquivo e com `N` voce desce.


## [h,j,k,l](#)

Esses caracteres funcionam no modo de visualização da mesma forma que as setas do teclado.

<table class="table"> 
<thead>
<th>H</th>
<th>J</th>
<th>K</th>
<th>L</th> 
</thead>
<tbody>
<tr>
<td>ESQUERDA</td>
<td>BAIXO</td>
<td>CIMA</td>
<td>DIREITA</td>
</tr>
</tbody>
</table>



## [i, o, a](#)

Os carcteres `i`, `o` e `a` saem do modo de visualização e entram em modo de inserção de texto.

Com o `i` o cursor fica onde esta.

Com o `o` o cursor quebra uma linha e então podemos digitar nessa nova linha.

Com o `a` o cursor avança 1 caracter e então podemos digitar.

## [c, d, p, y, dd, yy](#)

Sed efficitur faucibus velit vitae venenatis. Proin efficitur felis at accumsan hendrerit. Pellentesque sed fermentum tortor, eu imperdiet ligula. Ut pharetra odio quis cursus fringilla. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Ut nunc ligula, blandit commodo porta convallis, sodales convallis risus. Sed commodo, arcu sed venenatis dapibus, leo neque pellentesque erat, eu ultrices elit nulla et velit.

Sed efficitur faucibus velit vitae venenatis. Proin efficitur felis at accumsan hendrerit. Pellentesque sed fermentum tortor, eu imperdiet ligula. Ut pharetra odio quis cursus fringilla. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Ut nunc ligula, blandit commodo porta convallis, sodales convallis risus. Sed commodo, arcu sed venenatis dapibus, leo neque pellentesque erat, eu ultrices elit nulla et velit.

## [ZZ, :w!, :q!, :e!](#)

O `:ZZ` salva e fecha o arquivo, da mesma forma que o `:x` porem o `:x` aceita um nome de arquivo para sobreescrever sem que o vi faça nenhuma pergunta.

O `:w!` escreve no arquivo sem preguntar nada. Esse comando também recebe o parametro com o nome do arquivo.

O `:q!` sai do editor sem salvar nada e sem perguntar nada

o `:e! <nomedo-arquvo>` da mesma forma que o `:e <nomedo-arquvo>` edita um arquivo sem sair do VI mas com o `!` o buffer é desconsiderado.
