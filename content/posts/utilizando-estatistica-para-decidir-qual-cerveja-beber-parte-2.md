---
title: "Utilizando Estatística para Decidir qual Cerveja Beber - Parte 2"
description: "Web scraping a serviço do trabalhador brasileiro"
tags: ["análise", "data science", "r"]
date: 2018-02-27T11:30:00-03:00
draft: false
---

Sou maior de idade, pago meus impostos e contribuo para o PIB. Portanto, nada me impede de ocasionalmente beber uma ou outra cerveja em meus momentos de lazer. Embora eu tenha as minhas preferências pessoais neste assunto, estive pensando qual seria a opinião geral do brasileiro a respeito das cervejas disponíveis no mercado. <a href="https://g1.globo.com/economia/noticia/consumo-de-cerveja-deve-recuar-pelo-3-ano-seguido-em-2017-mas-faturamento-do-setor-cresce.ghtml">De acordo com o G1</a>, cada brasileiro consumiu, em média, 60,7 litros de suco de cevada em 2017, o que serve como indicativo do quanto o povo daqui curte uma ampola (ou talvez mais) deste diurético.

Pensando em analisar quantitativamente a opinião do brasileiro sobre as cervejas que consome, eu mostrei <a href="http://marcusnunes.me/post/utilizando-estatistica-para-decidir-qual-cerveja-beber-parte-1/">em meu post anterior</a> como fiz para obter informações a respeito de 

<ul>

  <li>Avaliação Geral</li>
  <li>Aroma</li>
  <li>Aparência</li>
  <li>Sabor</li>
  <li>Sensação</li>
  <li>Conjunto</li>

</ul>

das 1000 cervejas com mais avaliações no <a href="http://www.brejas.com.br/">Brejas</a>. 


## As Melhores Cervejas e Estilos

Podemos começar a análise com as 10 cervejas com avaliação geral mais alta:

<pre class="line-numbers"><code class="language-r"># cervejas melhor avaliadas

dados %>% 
  select(Nome, Geral, Votos) %>%
  arrange(desc(Geral))

# A tibble: 1,000 x 3
   Nome                                     Geral Votos
   <fct>                                    <dbl> <dbl>
 1 Westvleteren Abt 12                       4.70   106  
 2 Westvleteren Extra 8                      4.60    47
 3 Ola Dubh Special Reserve 40               4.60    33
 4 Founders KBS (Kentucky Breakfast Stout)   4.60    37
 5 Trappistes Rochefort 10                   4.50   213  
 6 Biertruppe Vintage Nº 1                   4.50    29
 7 Thomas Hardy's Ale                        4.50    41
 8 Gouden Carolus Cuvée van de Keizer Blauw  4.40    77
 9 St. Bernardus Abt 12                      4.40   140  
10 Founders Backwoods Bastard                4.40    32
# ... with 990 more rows</code></pre>

Ao que tudo indica, a cerveja <a href="http://www.brejas.com.br/cerveja/belgica/westvleteren-abt-12">Westvleteren Abt 12</a> é a melhor cerveja avaliada pelos usuários do Brejas. Com 106 votos, o que é quantidade razoável de avaliações, ela ficou com nota 4.7, de um máximo de 5. Nada mal.

Mas este tipo de informação é fácil de obter. O próprio Brejas nos informa isto. Podemos fazer coisas mais interessantes com este conjunto de dados. Por exemplo, qual será o estilo com maiores média e mediana entre os seus rótulos?



<pre class="line-numbers"><code class="language-r">dados %>% 
  select(Estilo, Nome, Geral) %>%
  group_by(Estilo) %>%
  summarise(Media=mean(Geral, na.rm=T), Mediana=median(Geral, na.rm=T)) %>%
  arrange(desc(Media))
# A tibble: 86 x 3
Estilo                             Media Mediana
<chr>                              <dbl>   <dbl>
1  Belgian Quadrupel / ABT          4.22    4.10
2  Bière de Champagne / Bière Brut  4.17    4.20
3  Belgian Dark Strong Ale          4.05    4.05
4  Wood Aged Beer                   4.05    4.20
5  Imperial / Strong Porter         4.03    4.00
6  Russian Imperial Stout           4.03    4.10
7  Belgian Specialty Ale            3.92    3.95
8  Black IPA                        3.91    3.90
9  Imperial / Double IPA            3.91    4.00
10 Oatmeal Stout                    3.90    3.90
# ... with 76 more rows</code></pre>

Note que, no total, 86 estilos de cerveja foram considerados. À primeira vista, o estilo preferido pelos usuários do site é o Belgian Quadrupel / ABT. Entretanto, olhar apenas a média ou a mediana de uma amostra não indica muita coisa. Veja o que acontece quando plotamos os <a href="https://pt.wikipedia.org/wiki/Diagrama_de_caixa">boxplots</a> das avaliações dos estilos de cerveja com as dez maiores médias, ordenados pela mediana:

![Estilos de Cerveja](/images/CervejaEstilos.png)

Perceba que não há nenhuma sugestão de diferença significante entre os grupos. Embora a média da Bière de Champagne / Bière Brut seja 4.17 e da Oatmeal Stout seja 3.90 (quase 7% a mais), não é possível perceber diferença significativa entre estes estilos de bebida. Até poderíamos testar se existe diferença de fato, mas seria perda de tempo.

## Relações entre as Características das Cervejas

Outra análise que podemos fazer é verificar as correlações entre as variáveis utilizadas para avaliar as cervejas:

![Correlações entre as Variáveis Consideradas](/images/CervejaCorrelacao.png)

Perceba como Aroma e Sabor estão fortemente correlacionados (0,94), mesma magnitude da correlação entre Sabor e Conjunto. Aroma e Conjunto ficam um pouco atrás, com 0,91. 

Aparência e Sensação, apesar de também possuírem alta correlação (0,71), são as duas variáveis menos correlacionadas. Talvez este seja um indicativo de que a Sensação que as cervejas geram em quem as bebe não corresponde à Aparência delas?


## Semelhanças entre os Estilos

Uma última análise que podemos fazer é o agrupamento de estilos. Como será que a avaliação dos brasileiros separa os 85 estilos de cerveja analisado aqui? Quais estilos será que estão mais próximos uns dos outros? Note que não estou procurando a similaridade dos estilos entre si, da forma que uma American Pale Ale e uma Blonde Ale são parecidas. Aqui eu agrupei os resultados de acordo com as informações que eu citei anteriormente (a saber, Aroma, Aparência, Sabor, Sensação e Conjunto). 

![Agrupamento dos Estilos de Cerveja](/images/CervejaDendrograma.png)

Este resultado pode ser interpretado como um sistema de recomendação. Se a pessoa gosta do estilo Saison/Farmhouse, é provável que também vá gostar do estilo Rauchbier, pois estes estilos aparecem bem próximos no diagrama acima (procure estes nomes no meio do gráfico, um pouco à esquerda). Por outro lado, uma Rauchbier é bem diferente de uma Lite American Lager (procure no extremo esquerdo do gráfico), pois estão em ramos bem diferentes do diagrama.


## Conclusão

Portanto, esta é a análise que realizei a respeito da opinião dos brasileiros sobre cerveja. Não é uma análise completa e exaustiva sobre o assunto. Sequer é representativa da população brasileira, pois apenas a opinião dos cadastrados no site Brejas foi levada em consideração. Ainda assim, creio que ele possa servir como baliza para quem já sabe qual o seu estilo preferido de cerveja e deseja se aventurar experimentando algo diferente, porém similar ao que gosta.

A função de scrap ainda não está perfeita. Existem algumas inconsistências na maneira com que o Brejas exibe os resultados das cervejas e que meu código não conseguiu pegar. Assim, alguns dados estão faltantes. Isto não chega a prejudicar a análise realizada, embora, é claro, dados completos sejam sempre melhores. Assim, fica a sugestão para quem quiser <a href="https://github.com/mnunes/Cerveja">analisar meu código</a> e ver como ele pode ser melhorado.

Como sempre, os códigos usados para obter os dados e para a análise realizada estão no meu <a href="https://github.com/mnunes/Cerveja">github</a>. Utilize este repositório para se inspirar e fazer as suas próprias análises.

Este post foi inspirado por um trabalho realizado pela <a href="http://kaylinwalker.com/tidy-text-beer/">Kaylin Walker</a>. 


