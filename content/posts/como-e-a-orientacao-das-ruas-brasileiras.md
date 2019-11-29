---
title: "Urbanismo e Estatística: Como é a Orientação das Ruas das Capitais Brasileiras"
description: "É uma zona em alguns lugares, mas é bem ordenado em outros"
tags: ["análise", "brasil", "data science", "python", "urbanismo"]
draft: false
date: 2019-01-21T06:45:00-03:00
---

Uns meses atrás, um professor de planejamento urbano chamado Geoff Boeing criou em seu blog um post chamado [Comparing US City Street Orientations](https://geoffboeing.com/2018/07/comparing-city-street-orientations/). Neste texto ele compara a orientação das ruas de várias cidades dos Estados Unidos a fim de descobrir como é a organização espacial delas. Ele utilizou python para acessar o site Open Street Map e baixar dados a respeito das ruas e suas direções. 

Geoff Boeing foi generoso e disponibilizou um [jupyter notebook](https://github.com/gboeing/osmnx-examples/blob/master/notebooks/17-street-network-orientations.ipynb) para quem quisesse reproduzir seu trabalho. [Eu adaptei o notebook dele para português](https://github.com/mnunes/osmnx/blob/master/notebooks/ruas-cidades.ipynb) e criei visualizações similares para as capitais de estados brasileiros.

Mas antes de mostrar os resultados, eu vou comentar brevemente o que quer dizer com esta história de orientação das ruas.

Tome, por exemplo, Palmas, capital do Tocantins. Com suas ruas quase todas paralelas e perpendiculares, Palmas gera um gráfico polar que é majoritariamente uma cruz.

![Orientação das Ruas de Palmas](/images/orientacao-ruas-palmas.png)

Isto significa que boa parte das ruas das cidades seguem direções muito parecidas. Elas vão e vem numa direção e são cruzadas por ruas perpendiculares. Há alguns trechos que não seguem este comportamento geral, mas eles são minoria, como podemos ver em umas barras residuais muito pequenas em torno do centro da imagem.

São Paulo, por outro lado, é mais caótica:

[![Orientação das Ruas de São Paulo](/images/orientacao-ruas-sao-paulo.png)](/images/orientacao-ruas-sao-paulo.png)


Note que as ruas de São Paulo se espalham em várias direções diferentes. Isto se reflete no gráfico, que não exibe mais o comportamento ordenado e em forma de cruz de Palmas, mas sim um comportamento mais circular, indicando que praticamente não há direções de ruas dominantes na cidade. Embora o mapa mostre uma vizinhança da Praça da Sé, a análise foi realizada para todas as ruas da cidade.

O resultado final, com todas as capitais de estado, está abaixo (clique para ampliar).

<a href="/images/orientacao-ruas-capitais-brasileiras.png"><img src="/images/orientacao-ruas-capitais-brasileiras.png"></a>


Como a tua cidade se comporta em relação às outras? Qual a tua experiência com as capitais brasileiras? Este gráfico representa bem as tuas impressões a respeito das cidades que conhece? [Utilize este notebook para gerar gráficos similares para outras cidades do mundo](https://github.com/mnunes/osmnx/blob/master/notebooks/ruas-cidades.ipynb).

---

[Este artigo científico](https://ssrn.com/abstract=3224723) expande esta discussão, de maneira acadêmica, para 100 cidades ao redor do mundo.