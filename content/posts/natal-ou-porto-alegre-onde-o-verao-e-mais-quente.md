---
title: "Natal ou Porto Alegre: Onde o Verão é Mais Quente?"
description: "A temperatura nem sempre é o que parece ser"
tags: ["análise", "clima", "R", "visualização", "temperatura"]
draft: false
date: 2018-02-06T16:01:00-03:00
---

## Um Pouco de História

Eu moro em Natal, RN, mas sou natural de <a href="https://pt.wikipedia.org/wiki/S%C3%A3o_Leopoldo">São Leopoldo, RS</a>. Também sou professor de Estatística. Quando falo de análise de dados com meus alunos, tem uma afirmação minha da qual eles sempre duvidam: Porto Alegre é mais quente do que Natal no verão.

Só quem morou no sul e sudeste, em cidades com clima subtropical e afetadas pela continentalidade, sabem do que estou falando. Embora nossa memória nos traia às vezes, sempre tive a impressão de que os verões em Porto Alegre são muito mais quentes do que os verões aqui em Natal.

Para provar ou desprovar esta afirmação, baixei os dados do <a href="http://www.inmet.gov.br/projetos/rede/pesquisa/">BDMEP - Banco de Dados Meteorológicos para Ensino e Pesquisa</a> referentes à temperatura máxima diária em Natal e Porto Alegre entre 1 de janeiro de 2002 e 31 de dezembro de 2016. Ou seja, são 15 anos de dados de temperatura diária nestas duas cidades que irão sustentar (ou não) minha afirmação.

## Análise Descritiva

Abaixo vemos todas as observações disponíveis para as temperaturas das duas cidades:

![Natal vs Poa - Todos os Anos](/images/Comparacao-Natal-Poa-Completa.png)

Este gráfico, que possui informação desde 1961, não ficou bom. Faltam muitos dados dos anos 70 e 80, além de algumas informações do início dos anos 2000. Por isso, resolvi manter apenas os dados de 1 de janeiro de 2002 em diante:



![Natal vs Poa - Temperatura Média](/images/Comparacao-Natal-Poa-Media.png)



Pronto. Melhor agora.

Podemos ver claramente no gráfico como Porto Alegre tem dias mais quentes do que Natal, principalmente no início do ano, na época do verão. Mas a quantidade deles é muito inferior ao que eu me lembro. Algo não parece certo.

Mas este gráfico mostra as temperaturas <em>médias</em> diárias. Acontece que Porto Alegre tem uma amplitude de temperatura muito alta, inclusive no verão. Os dias começam frescos, mas acabam esquentando muito. Por isso refiz os gráficos, agora considerando a temperatura <em>máxima</em> atingida no dia:


![Natal vs Poa - Temperatura Máxima](/images/Comparacao-Natal-Poa-Maxima.png)



Bingo! A quantidade de dias de calor intenso em Porto Alegre, com a máxima passando dos 35ºC, é muito maior do que em Natal. Inclusive, Natal não teve um dia sequer, nos últimos 15 anos, em que a temperatura máxima passou dos 35ºC.

Portanto, como eu lembrava, Porto Alegre é uma cidade muito mais quente do que Natal no verão.


Mais detalhes a respeito desta análise, como seu o código e os dados utilizados nela, estão na <a href="https://github.com/mnunes/Natal-Vs-PortoAlegre">minha página no github</a>.


