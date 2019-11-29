---
title: "Visualização Gráfica e Resumida dos Resultados das Edições do ENEM nos Anos de 2010 a 2015"
description: "Divulgando conhecimento"
tags: ["ferramenta", "R", "shiny", "visualização"]
draft: false
date: 2018-01-21T13:21:00-03:00
---

Analisar os resultados do ENEM é uma tarefa difícil. Embora os <a href="http://inep.gov.br/microdados">microdados</a> estejam disponíveis gratuitamente para quem quiser baixá-los, nem todos possuem o conhecimento técnico necessário para analisá-los a partir do zero. <a href="https://pt.stackoverflow.com/questions/154724/como-ler-os-microdados-do-enem-no-r">Até mesmo pesquisadores experientes precisam pedir ajuda para realizar esta tarefa</a>.

Pensando neste problema, orientei uma monografia no <a href="http://www.estatistica.ccet.ufrn.br/">Departamento de Estatística da UFRN</a> chamada <a href="https://monografias.ufrn.br/jspui/handle/123456789/5427">Visualização dos resultados das edições de 2010 a 2015 do ENEM através de um Shiny App</a>, de autoria de Marylaine Nascimento. Esta monografia se propôs a analisar, utilizando Estatística Descritiva, os resultados das últimas seis edições do ENEM disponíveis no site do INEP. Além da monografia, um <a href="http://shiny.estatistica.ccet.ufrn.br/enem/">aplicativo</a> foi criado, a fim de tornar mais acessível a pesquisa realizada.

Antes de realizar a análise, os milhões de microdados do ENEM entre 2010 e 2015 foram processados, a fim de que apenas as informações mais fundamentais sobre eles pudessem ser extraídas. Desta forma, gráficos que levavam mais de dez minutos para ficarem prontos passaram a levar menos de três segundos para serem completados. Um dos gráficos criados está logo abaixo. Ele compara o resultado geral do ENEM em 2015, separado por região do Brasil:

![Boxplots com dados do ENEM](/images/enem2015.png)


No total, o aplicativo apresenta 420 gráficos diferentes, além de tabelas e estatísticas sobre os resultados do ENEM entre 2010 e 2015. Qualquer pessoa é capaz de explorar os resultados do ENEM para as variáveis que escolhemos representar no <a href="http://shiny.estatistica.ccet.ufrn.br/enem/">aplicativo</a> desenvolvido.

Ainda há um pequeno bug que faz com que o primeiro gráfico gerado pelo usuário demore em torno de um minuto para aparecer na tela. Este bug ocorre apenas com o primeiro gráfico: todos os outros são gerados instantaneamente. Estamos trabalhando para corrigir isto e, em breve, todos os gráficos aparecerão com a mesma velocidade.

Os arquivos com o código deste aplicativo estão disponíveis no <a href="https://github.com/Marylaine/Visualiza-o-dos-Resultados-do-ENEM-2010-a-2015-">github da Marylaine Nascimento</a>.