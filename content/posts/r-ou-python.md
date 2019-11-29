---
title: "R ou Python? Qual a melhor ferramenta para trabalhar com Ciência de Dados?"
description: "A resposta definitiva para esta dúvida interminável"
tags: ["ciência de dados", "discussão", "excel", "julia", "programação", "python", "R"]
draft: false
date: 2019-10-09T16:26:00-03:00
---

Já vou começar este texto opinativo com a resposta definitiva para a pergunta do título:

# Qual é a melhor ferramenta para Análise de Dados?

A melhor ferramenta para análise dados é a ferramenta que o usuário mais conhece. Seja Excel, [R](https://marcusnunes.me/tags/r/), [python](https://marcusnunes.me/tags/python/), Minitab, SAS, SPSS ou qualquer outra. O que importa é obter os resultados desejados de maneira rápida e confiável. Cada usuário vai ter necessidades diferentes e é muito provável que a melhor ferramenta para uma pessoa não sirva para outra.

Isto posto, afirmo que a minha linguagem preferida de programação para análise de dados é o [R](https://marcusnunes.me/tags/r/). Ela não é a linguagem mais popular do mundo, nem a mais rápida e nem a mais simples de aprender. Entretanto, é a que **me** serve melhor para aquilo que **eu** faço.

<!--No restante do texto vou comparar [R](https://marcusnunes.me/tags/r/) e [python](https://marcusnunes.me/tags/python/) dentro das minhas limitações e dos meus conhecimentos e dizer porque prefiro uma em relação à outra.-->

# Por que usar uma linguagem de programação para analisar dados?

O principal motivo é a documentação do processo de análise de dados. De maneira geral, ao utilizar uma ferramenta como Excel ou SPSS, o usuário não documenta aquilo que faz. Ele clica nos menus, obtém o seu resultado e termina o seu serviço. Não há nada de errado em fazer isso. O problema é que análises mais complexas acabam gerando mais passos intermediários entre a importação de dados e o resultado final da análise. A imagem abaixo, adaptada do livro [R for Data Science](https://r4ds.had.co.nz/), exemplifica bem como é o workflow geral de uma análise de dados do início ao fim:

![](/images/workshop.png)

Perceba que há muitos passos envolvidos. O processo completo, que começa pela importação dos dados, passa pela modelagem e finaliza na comunicação dos resultados, envolve muitos passos diferentes. Em especial, a parte destacada pelo retângulo azul, pode demorar muito. Encontrar o modelo ideal para os dados não é uma tarefa trivial. Assim, documentar estes passos é fundamental não apenas para que consigamos organizar nossas ideias, mas também para informar os outros membros da nossa equipe a respeito do trabalho que realizamos.

# Por que usar o R para analisar dados?

A figura abaixo, obtida no [site da linguagem julia](https://julialang.org/benchmarks/), compara a velocidade de diversas linguagens de programação:

![](/images/benchmarks.png)

Note que [R](https://marcusnunes.me/tags/r/) não é a mais rápida em nenhuma tarefa. Mesmo assim, prefiro utilizá-la porque escrevo código mais rápido nesta linguagem. O ganho de performance que eu teria rodando código em [python](https://marcusnunes.me/tags/python/) seria perdido na hora de escrever os programas, pois sempre tenho que ficar checando manuais quando uso python. Ocorre o oposto quando uso R, pois sou fluente na linguagem e escrevo código para ela como escrevo meus textos em português ou em inglês.

O [R](https://marcusnunes.me/tags/r/) apresenta algumas outras facilidades que eu já não consigo viver sem. Como preparo muito material didático, esta linguagem permite que eu mescle conteúdo teórico, trechos de códigos e outputs de programas de maneira muito prática. Sério, dá uma olhada neste material do [Workshop de R Básico](https://htmlpreview.github.io/?https://github.com/mnunes/workshopR/blob/master/inst/doc/workshopR.html) que ministro e veja como a qualidade gráfica é impressionante. Faz quase 10 anos que uso R Sweave e seu sucessor RMarkdown com muito sucesso e não tenho interesse em aprender uma nova ferramenta se as que conheço atualmente já me satisfazem a contento. 

Acabei utilizando esta característica do [R](https://marcusnunes.me/tags/r/) para criar aplicações do RMarkdown em outras áreas. Por exemplo, os [relatórios](https://github.com/mnunes/modeloLEA/blob/master/documento_final.pdf) dos alunos que participam do meu projeto de [consultoria estatística gratuita](http://marcusnunes.me/consultoria/) são escritos usando RMarkdown, através de um [pacote que eu mesmo criei](https://github.com/mnunes/modeloLEA).


# Conclusão

Eu uso [R](https://marcusnunes.me/tags/r/) porque ele facilita a minha vida. Programo na linguagem desde 2008 e, antes disso, utilizei S-Plus, sua versão proprietária. Por isso, o [R](https://marcusnunes.me/tags/r/) é a minha opção preferida para analisar dados, preparar material didático e escrever relatórios e artigos científicos.





