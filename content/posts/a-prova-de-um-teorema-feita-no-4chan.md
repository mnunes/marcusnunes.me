---
title: "A Prova de um Teorema feita no 4chan"
description: "O que animes, matemática e um reduto de trolls tem em comum?"
tags: ["4chan", "anime", "analise combinatória", "teorema"]
draft: false
date: 2018-10-25T8:20:00-03:00
---

O  [4chan](https://pt.wikipedia.org/wiki/4chan) é um site que existe desde 2003 e serve para que seus usuários compartilhem imagens (e posteriormente memes) de forma anônima. [Em 2011](http://4watch.org/superstring/), um usuário publicou a seguinte pergunta no 4chan:

![The Haruhi Problem](/images/haruhi.jpg)

> Qual é o menor número de episódios de Haruhi que você deve assistir para que todos os 14 episódios originais sejam vistos em todas as ordens possíveis?

Este problema pode ser generalizado da seguinte maneira: 

> Suponha que exista uma série de TV com n episódios. Você deseja assistir os episódios em todas as ordens possíveis. Qual é o menor número de episódios que você precisa assistir?
 
Esta pergunta foi inspirada na obra [Suzumiya Haruhi no Yūutsu](https://pt.wikipedia.org/wiki/Suzumiya_Haruhi_no_Y%C5%AButsu) ("A Melancolia de Haruhi Suzumiya"), um anime cuja primeira temporada consistia em 14 episódios exibidos fora de ordem cronológica.

À primeira vista o enunciado parece confuso, mas vamos ver como ele funciona com um exemplo prático. Vamos supor que estamos interessados em um seriado com n=3 episódios. Todas as ordens possíveis para assistir os episódios deste seriado são seis:

* 1, 2, 3

* 1, 3, 2

* 2, 1, 3

* 2, 3, 1

* 3, 1, 2

* 3, 2, 1

Uma solução ingênua para assistir os episódios em todas as ordens possíveis seria colocar todas as sequências acima uma ao lado da outra e assistir os episódios na seguinte ordem:

1, 2, 3; 1, 3, 2; 2 1, 3; 2, 3, 1; 3, 1, 2; 3, 2, 1 

Mas isso faria o espectador ter que assistir 18 episódios em sequência. Veja como é possível resolver este problema assistindo menos episódios com a sequência a seguir:

1, 2, 3, 1, 2, 1, 3, 2, 1

Perceba que todas as permutações de três números estão incluídas na sequência acima. Eu as destaquei estas subsequências em negrito logo abaixo:

* **1, 2, 3**, 1, 2, 1, 3, 2, 1
* 1, 2, 3, 1, 2, **1, 3, 2**, 1
* 1, 2, 3, 1, **2, 1, 3**, 2, 1
* 1, **2, 3, 1**, 2, 1, 3, 2, 1
* 1, 2, **3, 1, 2**, 1, 3, 2, 1
* 1, 2, 3, 1, 2, 1, **3, 2, 1**

Ou seja, em vez de assistir 18 episódios, o espectador pode assistir apenas 9. Isto se chama [superpermutation](https://en.wikipedia.org/wiki/Superpermutation) e é um problema bastante conhecido em matemática. O interessante é que nenhum matemático havia provado qual seria o limite inferior da comprimento da menor sequência de números que satisfaz esta propriedade.

[E é aí que entra o 4chan](http://4watch.org/superstring/). Um usuário postou a imagem que abre este texto e uma conversa se iniciou. Ao final, foi demonstrado que a menor sequência que satisfaça a propriedade descrita pelo problema deve ter, pelo menos, comprimento n!+(n−1)!+(n−2)!+n−3, em que n é o número de elementos da sequência. 

No caso do anime A Melancolia de Haruhi Suzumiya, seriam necessários assistir no mínimo 93.884.313.611 (93 bilhões, 884 milhões, 313 mil e 611) episódios para que todos eles fossem assistidos em todas as ordens possíveis.

[A prova do teorema está aqui](http://mathsci.wikia.com/wiki/The_Haruhi_Problem). 

Isto gerou alguns inconvenientes. Por exemplo, como citar este resultado em novas pesquisas na área de combinatória? Afinal, o autor está creditado como Anonymous. Além disso, não é um resultado que faça parte da literatura matemática, pois não foi publicado em uma revista com revisão por pares. Enfim, são perguntas para as quais eu desconheço a resposta e, caso alguém saiba, por favor contribua nos comentários.

E esta, crianças, é a história de como o 4chan ajudou a matemática a avançar seus conhecimentos.

