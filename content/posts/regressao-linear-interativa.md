---
title: "Regressão Linear Interativa"
description: "Aprenda como a regressão linear simples funciona"
tags: ["ferramenta", "R", "shiny", "visualização"]
draft: false
date: 2018-05-02T07:21:00-03:00
---

# tl; dr

<a href="http://shiny.estatistica.ccet.ufrn.br/regressao-linear-interativa/" target="_blank">Este é o link do aplicativo</a>, caso o texto abaixo seja desinteressante.


# Introdução

Regressão linear é um dos tópicos que ensino em uma disciplina chamada Métodos Estatísticos. Como é uma disciplina do terceiro semestre do Bacharelado em Estatística, é comum encontrar alunos que nunca viram um tópico como este ser tratado anteriormente. Assim, alguns ficam sem entender direito quando falo sobre relação linear, pontos de influência e tudo o mais. 

Pensando nisso, na semana passada procurei na internet uma maneira de ensinar regressão linear de forma interativa. Eu queria que pontos aparecessem sempre que o usuário clicasse em uma tela e, a partir destes pontos, uma reta fosse ajustada. Encontrei alguns sites por aí fazendo isso, mas nenhum deles fazia exatamente o que eu queria. Alguns até ajustavam a reta aos pontos, mas não forneciam mais informações a respeito do ajuste realizado, como tabela ANOVA, gráficos de diagnóstico etc. Além disso, nenhum deles havia usado o `R` pra fazer isto.

Aí tive uma ideia. Por que não fazer eu mesmo um aplicativo assim?

# Aplicativo Interativo no shiny

Pensando nestas limitações, criei eu mesmo um <a href="http://shiny.estatistica.ccet.ufrn.br/regressao-linear-interativa/" target="_blank">aplicativo interativo para estudo da regressão linear simples</a>. Abaixo está uma imagem dele:

![Aplicativo em funcionamento](/images/regressao-linear-interativa.png)

Seu uso é muito simples. Ele é formado por três abas:

- Gráfico: nesta aba o usuário clica em uma janela gráfica e pontos vão aparecendo. A partir do segundo ponto, uma reta é ajustada aos dados presentes na tela. Além de calcular a reta em si, o aplicativo informa do valor do R^2 do ajuste, bem como os valores dos coeficientes estimados e seus respectivos testes de hipóteses e fornece a tabela ANOVA do modelo.

- Diagnóstico: aqui vemos quatro gráficos de diagnóstico plotados. Estes gráficos permitem detectar se as hipóteses a respeito dos resíduos do modelo foram violadas, além de permitir a identificação de outliers e pontos de influência.

- Dados: todos os pontos colocados no gráfico podem ser baixados e utilizados em outros programas estatísticos. Se for necessário mostrar algo atípico em algum programa como Excel ou SPSS, por exemplo, é possível criar um conjunto de dados com comportamento inadequado nesta ferramenta e copiar os dados presentes nesta aba, a fim de reproduzir em outro ambiente os resultados encontrados.

[Teste a ferramenta](http://shiny.estatistica.ccet.ufrn/regressao-linear-interativa/). Garanto que vale a pena.

<hr />

Gostou? Então compartilhe este post ou a ferramenta que criei em suas redes sociais. Quem sabe este trabalho pode ser utilizado nas aulas ou cursos de quem está lendo este texto?


Se tiver alguma dúvida ou sugestão, mande um email para marcus arroba marcusnunes.me que eu responderei o mais rápido possível.




