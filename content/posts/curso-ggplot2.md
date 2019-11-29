---
title: "Curso ggplot2"
description: "Como fazer gráficos mais bonitos no `R`"
tags: ["ensino", "ferramenta", "ggplot2", "R", "visualização"]
draft: false
date: 2018-05-21T09:21:00-03:00
---

Recentemente fui convidado pela organização do [2º Encontro Paraibano de Estatística](https://sites.google.com/site/epbest2018/) para ministrar um minicurso durante o evento. O tema que escolhi foi visualização de dados:

> **Visualização de dados com `ggplot2`**
> 
> Seja na análise dos resultados de algum experimento ou na modelagem de big data, todo trabalho estatístico começa com a visualização dos dados coletados. Embora seja negligenciada às vezes, a visualização é de suma importância para ajudar a levantar hipóteses, confirmar suspeitas e avaliar suposições. Neste minicurso veremos uma implementação da gramática de gráficos, um paradigma que favorece a construção de gráficos pensando-os como uma superposição de camadas diferentes. Os gráficos construídos com o pacote ggplot2 são pensados uma parte de cada vez, tornando o processo mais natural e intuitivo, permitindo ao mesmo tempo maior controle e flexibilidade aos gráficos gerados.

O minicurso correu super bem. Além disso, tive um bom _feedback_ vindo dos participantes. Como escrevi um pacote no `R` para que ficasse mais fácil de compartilhar o material deste curso, como seus códigos, slides e soluções dos exercícios com quem foi até a UFPB participar do evento, achei que seria interessante divulgar este pacote para os três leitores deste blog. Aí vai ele então.

O pacote está hospedado no [GitHub](https://github.com/mnunes/curso.ggplot2). Para instalá-lo no seu computador, rode os comandos

    install.packages("devtools") # caso o pacote devtools não esteja instalado
    devtools::install_github("mnunes/curso.ggplot2", build_vignettes=TRUE)
    
Dependendo dos pacotes do `R` que seu computador já possua em disco, a instalação do pacote `curso.ggplot2` pode acabar demorando um pouco. Se tudo correr bem, o comando
    
    vignette("curso.ggplot2")

vai abrir o material que utilizei durante o evento. Há alguns exercícios ao final deste material. As respostas dos exercícios estão disponibilizadas [neste link](https://github.com/mnunes/curso.ggplot2/blob/master/exercicios.Rmd).

Não esqueça de conferir os outros minicursos que ministrei na aba [Ensino](/ensino/) deste site.





