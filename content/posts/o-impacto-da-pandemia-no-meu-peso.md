---
title: "O impacto da COVID-19 no meu peso"
description: "Se chorei ou se sorri, o importante é que não estou obeso"
tags: ["ciência de dados", "covid-19", "dieta", "r", "visualização"]
draft: false
date: 2021-02-26T19:22:00-03:00
---

26 de fevereiro de 2020. [Segundo a Wikipedia, essa é a data do início da pandemia de COVID-19 no Brasil](https://pt.wikipedia.org/wiki/Pandemia_de_COVID-19_no_Brasil), com a confirmação de que um homem de 61 anos, morador de São Paulo, que retornou da Itália.

(**trivia:** dois meses antes disso eu estava na Itália. [aqui tem um heatmap mostrando por onde passei](https://marcusnunes.me/posts/heatmap-de-localizacao-no-google/))


Baseado no post que escrevi um ano e meio atrás, intitulado [1000 Dias Com Ela: A Dieta](https://marcusnunes.me/posts/1000-dias-com-ela-a-dieta/), resolvi analisar como meu peso se comportou nesses últimos 366 dias. E esse foi o resultado:


```{r, echo=FALSE, message=FALSE}
# preparacao

library(tidyverse)
theme_set(theme_bw())
library(lubridate)

# leitura dos dados

dados <- 
	read.csv(file = "data-mfp.csv") %>%
	mutate(Date = ymd(Date)) %>%
	filter(Date >= ymd("2020-02-26"))

# grafico

ggplot(dados, aes(x = Date, y = Weight)) +
	geom_line() +
	# academia
	annotate("text", x = ymd("2020-03-18"), y = 76.9, label = "Academia fecha") +
	geom_segment(aes(x = ymd("2020-03-18"), y = 74.6, xend = ymd("2020-03-18"), yend = 76.7), col = "red") +
	# corrida
	annotate("text", x = ymd("2020-10-12"), y = 73.7, label = "Corridas na rua\ncom mais de 4km") +
	geom_segment(aes(x = ymd("2020-10-12"), y = 75.9, xend = ymd("2020-10-12"), yend = 74), col = "red") +
	# nutricionista
	annotate("text", x = ymd("2021-01-15"), y = 76.9, label = "Vou à Nutricionista") +
	geom_segment(aes(x = ymd("2021-01-15"), y = 76.2, xend = ymd("2021-01-15"), yend = 76.7), col = "red")
```

![O impacto da COVID-19 no meu peso](/images/covid-19-dieta.png)


Há três datas em destaque no gráfico acima. Abaixo eu explico o significado delas: 

* 18 de Março de 2020: a academia que eu frequentava fechou. A partir desse dia eu fiquei completamente sedentário. Passava os dias sem sair de casa. O gráfico mostra que claramente perdi peso, possivelmente devido à minha perda de massa muscular.

* 12 de Outubro de 2020: depois de tentar largar o sedentarismo, finalmente consegui voltar a ter preparo físico suficiente para correr por mais de 4km na rua. Passei a levantar às 5:15 da manhã para evitar encontrar muitas pessoas. Um pouco antes dessa data eu completei o programa [C25K](http://www.c25k.com/), que me levou do sofá a completar 5km de corrida sem parar.

* 15 de Janeiro de 2021: só passei a ter mais consistência em meu emagrecimento a partir da ida à minha nutricionista. Estou fazendo uma dieta com baixa ingestão de carboidratos e o resultado tem sido bastante bom: 3.5kg a menos em 6 semanas (ou 42 dias). 


Os códigos e dados usados nesse post podem ser encontrados no [github](https://github.com/mnunes/MyFitnessPal) (me segue lá).

