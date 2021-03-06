---
title: Shiny
description: Estatística interativa através de web apps
type: page
#featured_image: 'images/banners/software.jpg'
menu:
  main: {}
weight: 40
---

Nos últimos tempos tenho me interessado muito por aplicações web que demonstrem como a Estatística pode ser utilizada para ensino ou divulgação de informações. Por isso criei o site [shiny](http://shiny.estatistica.ccet.ufrn.br/). Nesse site divulgo apps criados por mim e por alunos que orientei, a fim de tornar o acesso à Estatística mais amplo do que é atualmente.

* [SRAG ou COVID-19?](http://shiny.estatistica.ccet.ufrn.br/srag/): 2020 trouxe um aumento muito grande nos casos de Síndrome Respiratória Aguda Grave (SRAG). Verifique a situação nos estados brasileiros e compare os dados a partir de 2011.

* [Doenças Cardiovasculares](http://shiny.estatistica.ccet.ufrn.br/DoencasCardiovasculares/): Entre com dados biométricos e descubra a sua probabilidade de ter uma doença cardiovascular, baseada em dados obtidos em uma amostra de 70 mil pessoas.

* [Jogadores Similares](http://shiny.estatistica.ccet.ufrn.br/JogadoresSimilares/): Escolha algum jogador de PES 2019 e veja quais são os outros 10 jogadores mais parecidos com ele.

* [Dashboard Deputados](http://shiny.estatistica.ccet.ufrn.br/DashboardDeputados/): Dashboard desenvolvido no `shiny` para o controle de gastos públicos. Baseado em um [pacote](https://github.com/mnunes/reembolsos/) escrito para o `R` no qual organizo os dados da [Operação Serenata de Amor](https://serenata.ai/) a respeito dos pedidos de reembolsos feitos pelos deputados federais brasileiros. Escrevi sobre o pacote [nesse post](http://marcusnunes.me/post/controle-de-gastos-publicos-como-verificar-quanto-os-deputados-federais-estao-gastando/) do meu blog.

* [Regressão Linear Interativa](http://shiny.estatistica.ccet.ufrn.br/regressao-linear-interativa/): Aplicativo utilizado para demonstrar como funciona a regressão linear simples. O usuário clica em locais do plano e uma reta é ajustada aos pontos criados, indicando desde a equação que melhor se ajusta aos dados, até a tabela ANOVA e os gráficos de diagnóstico. [[github]](https://github.com/mnunes/regressao)

* [Intervalos de Confiança](http://shiny.estatistica.ccet.ufrn.br/IC/): Ilustração de como os intervalos de confiança funcionam na teoria, através de simulação de Monte Carlo. É possível ajustar o nível de confiança, número de amostras a serem tomadas e o tamanho amostral a ser considerado. [[github]](https://github.com/mnunes/IntervalosDeConfianca)

* [Jogadores Similares](http://shiny.estatistica.ccet.ufrn.br/JogadoresSimilares/): Trabalho que orientei, no qual os alunos coletaram informações sobre as características físicas de mais de 11 mil jogadores de futebol e encontram quais deles são mais parecidos entre si. Utiliza técnicas de _data mining_ e _web scraping_ para ajudar o usuário a encontrar jogadores que lhe interessam para montar seu time no Pro Evolution Soccer. [[github]](https://github.com/soaresjulio/Jogadores-Similares)

* [Visualização gráfica e resumida dos resultados das edições do ENEM nos anos de 2010 a 2015](http://shiny.estatistica.ccet.ufrn.br/enem/): 32GB de dados do ENEM foram resumidos em apenas 420 gráficos, entre boxplots e histogramas. É possível analisar os resultados das provas por assunto, além de dividir os candidatos por região do país, sexo ou renda. [[github]](https://github.com/Marylaine/Visualiza-o-dos-Resultados-do-ENEM-2010-a-2015-)

Ficou interessado e gostaria de colaborar com a minha iniciativa? Se interessou pelos dashboards e gostaria de implementá-los em sua empresa? Então entre em [contato](https://marcusnunes.me/contato/) comigo que podemos conversar a esse respeito e ver a melhor maneira de procedermos com isso.

Ou siga meu tutorial [Como Instalar o shiny server em seu Próprio Servidor](https://marcusnunes.me/posts/como-instalar-o-shiny-em-seu-proprio-servidor/) para descobrir como virar o seu próprio sysadmin utilizando essa ferramenta.

