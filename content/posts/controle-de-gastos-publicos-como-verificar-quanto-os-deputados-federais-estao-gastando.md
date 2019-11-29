---
title: "Controle de gastos públicos: como verificar quanto os deputados federais estão gastando"
description: "Uma maneira de controlar o dinheiro do contribuinte"
tags: ["análise", "ferramenta", "política", "R", "shiny"]
draft: false
date: 2018-04-02T11:40:00-03:00
---

2018 é ano de eleição. Em teoria, alguns milhões de brasileiros que vão às urnas em 7 de outubro escolher seus candidatos para vários cargos. Infelizmente, os debates sobre as eleições no Brasil ficam concentrados na escolha dos nomes para os cargos do executivo. As pessoas tendem a se preocupar com o novo presidente, muitas vezes imaginando que vão eleger um salvador da pátria que vai, magicamente, resolver todos os problemas do país. O <a href="https://pt.wikipedia.org/wiki/Sebastianismo" target="_blank">sebastianismo</a> pode ter acabado em Portugal, mas continua firme e forte por aqui.

![Rei Sebastião](/images/rei_sebastiao.png)

O problema é que depois das eleições vem a realidade e a <em><a href="https://pt.wikipedia.org/wiki/Realpolitik" target="_blank">realpolitik</a></em> chega com força. O presidente não governa sozinho. Ele precisa negociar com os deputados e senadores. Portanto, escolher um bom deputado, alguém que não seja um dos <a href="http://politica.estadao.com.br/noticias/geral,chamado-de-chefe-da-quadrilha-de-achacadores--temer-processa-cid-gomes,10000006308" rel="noopener" target="_blank">400 achacadores do congresso</a>, é tão importante quanto escolher o presidente.

O site <a href="http://www.politicos.org.br/" rel="noopener" target="_blank">Ranking dos Políticos</a> tenta organizar as informações disponíveis sobre os atuais deputados e senadores. Este site junta informações de diversas fontes, a fim de avaliar como está o cumprimento dos deveres dos nobres legisladores.

Outra organização interessada em avaliar o desempenho dos deputados e senadores é a <a href="https://serenata.ai/"  rel="noopener" target="_blank">Operação Serenata de Amor</a>. Este pessoal pega as informações disponibilizadas pela Câmera e pelo Senado, formata elas de maneira acessível e distribui para quem quiser verificar. Inclusive, escreveram um <a href="https://github.com/okfn-brasil/serenata-toolbox/">módulo para python</a> que simplifica demais esta tarefa.

O problema é que é um módulo para python. Nem todos os estatísticos do Brasil trabalham com o python. Em geral, a gente<sup>1</sup> entende mais de R. Pensando nisso, utilizei a <a href="https://github.com/okfn-brasil/serenata-toolbox/" rel="noopener" target="_blank">ferramenta criada pelo Serenata de Amor</a> para baixar os dados de reembolso dos deputados. Em seguida, criei um pacote com os dados de reembolsos pedidos pelos deputados e pagos pelo governo, disponibilizando para quem quiser usar. A seguir vou mostrar como instalar e utilizar o pacote que criei, além de mostrar algumas análises que fiz. 




## Como Usar o Pacote

Meu pacote não está no cran. Hospedei ele no <a href="http://github.com/mnunes/reembolsos" rel="noopener" target="_blank">GitHub</a> (me segue lá), uma rede social para programadores. Apesar de isto me dar um pouco mais de liberdade, acaba deixando a instalação do pacote menos direta para o usuário, pois é necessário realizar um passo a mais antes da instalação. 

Para instalar meu pacote <a href="http://github.com/mnunes/reembolsos" rel="noopener" target="_blank"><code>reembolsos</code></a>, é necessário instalar primeiramente o pacote <code>devtools</code> através do comando

<pre class="line-numbers"><code class="language-r">install.packages("devtools")
</code></pre>

Com o <code>devtools</code> instalado, fica trivial instalar meu pacote:


<pre class="line-numbers"><code class="language-r">library(devtools)
install_github("mnunes/reembolsos")
</code></pre>

Ou seja, com três linhas de código<sup>2</sup> é possível ter acesso a todos os pedidos de reembolsos feitos pelos deputados e senadores entre 2009 e 2017. São 9 anos de dados reais e livres, disponíveis para quem quiser analisar.

A instalação deve demorar um pouquinho, pois os deputados e senadores pediram vários reembolsos nos último 10 anos. No dia em que publiquei este post, haviam 3.099.310 pedidos únicos de reembolso (sim, três milhões). Portanto, há várias informações a serem baixadas. Seja paciente.





## O que dá pra fazer com o Pacote

Excelente pergunta. Dá pra fazer tudo com este pacote. Quer dizer, tudo o que envolva analisar pedidos de reembolso dos deputados federais. Por exemplo, dá pra verificar quanto dinheiro foi reembolsado para os deputados brasileiros entre 2009 e 2017:


<pre class="line-numbers"><code class="language-r">library(reembolsos)
theme_set(theme_bw())

camara %>%
  select(total_net_value, year) %>%
  group_by(year) %>%
  summarise(total=sum(total_net_value)) %>%
  print(n=Inf) %>%
  ggplot(., aes(x=year, y=total/1e6)) +
  geom_line() +
  labs(x="Ano", y="Reembolsos (em milhões de R$)") +
  scale_x_continuous(breaks = seq(2009, 2017, 1), minor_breaks = NULL) +
  scale_y_continuous(limits = c(0, 250))

# A tibble: 9 x 2
   year      total
  <int>      <dbl>
1  2009 115404993.
2  2010 154391858.
3  2011 171927438.
4  2012 170508922.
5  2013 188930589.
6  2014 196061150.
7  2015 213804407.
8  2016 221070448.
9  2017 225362468.
</code></pre>

![Reembolsos Totais](/images/reembolsos_totais.png)






Perceba que este resultado não faz discriminação nenhuma, nem leva em conta a inflação do período. Ele apenas mostra os reembolsos totais pagos a todos os deputados somados. Não é possível ver muita coisa, a não ser que estes gastos vem aumentando com o tempo. Entretanto, é possível fazer uma análise como esta por partido:

<pre class="line-numbers"><code class="language-r">camara %>%
  select(party, total_net_value, year) %>%
  group_by(party, year) %>%
  summarise(total=sum(total_net_value)) %>%
  ggplot(., aes(x=year, y=total/1e6, colour=party)) +
  geom_line() +
  labs(x="Ano", y="Reembolsos (milhões de R$)", colour="Partido") +
  scale_x_continuous(breaks = seq(2009, 2017, 1), minor_breaks = NULL) +
  scale_y_continuous(limits = c(0, 35))
</code></pre>



![Reembolsos por Partido](/images/reembolsos_partido.png)





Embora consigamos ver algumas coisas interessantes, como uma grande diminuição no valor de reembolsos feitos aos deputados do PT após 2014 (o que não deveria ser uma surpresa, pois o partido elegeu menos deputados nas últimas eleições se comparado com o número de eleitos em 2010), esta visualização está muito poluída. Vamos nos restringir apenas aos 7 partidos com o maior valor total de reembolsos pagos:

<pre class="line-numbers"><code class="language-r">maiores <- camara %>%
  select(party, total_net_value, year) %>%
  group_by(party) %>%
  summarise(total=sum(total_net_value)) %>%
  arrange(desc(total)) %>%
  head(n=7) %>%
  select(party) %>%
  unlist() %>%
  as.vector()

camara %>%
  select(party, total_net_value, year) %>%
  filter(party %in% maiores) %>%
  group_by(party, year) %>%
  summarise(total=sum(total_net_value)) %>%
  group_by(year) %>%
  print(n=Inf) %>%
  ggplot(., aes(x=year, y=total/1e6, colour=party)) +
  geom_line() +
  labs(x="Ano", y="Reembolsos por Partido (milhões de R$)", colour="Partido") +
  scale_x_continuous(breaks = seq(2009, 2017, 1), minor_breaks = NULL) +
  scale_y_continuous(limits = c(0, 35))
</code></pre>


![Reembolsos por Partido - Top 7](/images/reembolsos_partido_top7.png)







Pronto. A visualização melhorou um pouco. Temos PT e PMDB liderando os reembolsos, com valores totais na ordem de R$25 milhões em 2017, e um grupo de cinco outros partidos com valores de reembolso variando entre R$15 e R$20 milhões no mesmo ano.

Mas PMDB e PT possuem os maiores números de deputados. É natural que eles gastem mais em termos absolutos. Como será que é o gasto médio por reembolso se analisarmos apenas estes sete partidos?



<pre class="line-numbers"><code class="language-r">camara %>%
  select(party, total_net_value, year) %>%
  filter(party %in% maiores) %>%
  group_by(party, year) %>%
  summarise(media=mean(total_net_value)) %>%
  group_by(year) %>%
  print(n=Inf) %>%
  ggplot(., aes(x=year, y=media, colour=party)) +
  geom_line() +
  labs(x="Ano", y="Reembolsos Médios por Partido (R$)", colour="Partido") +
  scale_x_continuous(breaks = seq(2009, 2017, 1), minor_breaks = NULL) +
  scale_y_continuous(limits = c(0, 800))
</code></pre>



![Reembolsos por Partido - Média do Top 7](/images/reembolsos_partido_top7_media.png)



Hum... Os deputados do PR apresentaram valor médio de quase R$800 por reembolso pago. Aliás, dentro do grupo de sete partidos considerado, os deputados do PR são os que tem o reembolso médio mais alto desde 2009. Os deputados do PT foram os que pediram reembolsos médios de menor valor em 2017. Como eles são em número maior e apresentam mais pedidos, o valor total de todos os reembolsos acaba ficando mais alto do que os outros partidos.

Mas as análises que podem ser realizadas não ficam apenas em comparar partidos. É possível comparar deputados e os lugares onde eles gastaram o nosso dinheiro. Podemos ver, por exemplo, todas as vezes em que um deputado fez uma refeição em algum restaurante e gastou mais do que a média dos outros deputados. Um bom restaurante para fazermos isto é o McDonald's, pois ele está presente no Brasil inteiro e muita gente tem ideia de quanto custa uma refeição neste local.

Veja como o pacote <a href="http://github.com/mnunes/reembolsos" rel="noopener" target="_blank"><code>reembolsos</code></a> permite que vejamos quais foram os gastos mais altos da história da câmara nesta lanchonete:


<pre class="line-numbers"><code class="language-r">camara %>%
  select(year, supplier, congressperson_name, party, total_net_value) %>%
  filter(grepl("donald", supplier, ignore.case=TRUE)) %>%
  arrange(desc(total_net_value))

# A tibble: 643 x 5
    year supplier                           congressperson_name party total_net_value
   <int> <fct>                              <fct>               <fct>           <dbl>
 1  2009 MC DONALDS                         CELSO RUSSOMANNO    PRB              84.0
 2  2014 MC DONALDS                         FRANCISCO FLORIANO  DEM              80.0
 3  2014 MC DONALDS                         EURICO JÚNIOR       PV               73.0
 4  2015 MC DONALDS                         CELSO RUSSOMANNO    PRB              71.5
 5  2009 MC DONALD'S -LMO COMERCIO DE ALIM… PAULO ROBERTO PERE… PTB              67.2
 6  2015 MC DONALDS                         CÉSAR MESSIAS       PSB              64.5
 7  2013 MCDONALDS COMÉRCIO DE ALIMENTOS L… MAGDA MOFATTO       PR               64.0
 8  2016 MC DONALDS                         CÉSAR MESSIAS       PSB              60.0
 9  2010 MC DONALDS                         JOSÉ MENTOR         PT               57.0
10  2015 MC DONALD'S COM DE ALIM LTDA       POMPEO DE MATTOS    PDT              57.0
# ... with 633 more rows
</code></pre>

Dentre os 643 gastos feitos pelos deputados no McDonald's, alguns se destacam. Note que em 2009, Celso Russomanno, deputado federal pelo PRB, gastou R$84,00 em apenas uma ida ao McDonald's. Se hoje, em 2018, depois de nove anos de inflação acumulada, um Big Mac com refrigerante e batata frita média custa menos de R$25,00, podemos dizer que R$84,00 foi um gasto bastante elevado para o padrão desta lanchonte.

O interessante é que podemos comparar o gasto do deputado com os outros 642 pedidos de reembolso realizados neste mesmo restaurante, calculando a média e o desvio padrão dos reembolsos. E aí descobrimos o seguinte:

<pre class="line-numbers"><code class="language-r">
camara %>%
  select(year, supplier, congressperson_name, party, total_net_value) %>%
  filter(grepl("donald", supplier, ignore.case=TRUE)) %>%
  summarise(Media=mean(total_net_value), SD=sd(total_net_value))

# A tibble: 1 x 2
  Media    SD
  <dbl> <dbl>
1  23.1  12.3
</code></pre>

A média de pedidos de reembolso no McDonald's, entre 2009 e 2017, sem considerar a inflação, foi de R$23,10, com desvio padrão de R$12,30. Ou seja, este gasto específico de R$84,00 está 4,94 desvios padrão acima da média dos gastos dos outros deputados federais neste restaurante. Pra quem é leigo no assunto, isto significa que é um gasto <strong>muito alto</strong>. Talvez seja interessante investigar os detalhes desta compra pra ver que não houve algum cadastro errado no valor informado e reembolsado para o deputado. Deputado este que não foi o único a gastar muito no McDonald's:

<pre class="line-numbers"><code class="language-r">
camara %>%
  select(year, supplier, congressperson_name, party, total_net_value) %>%
  filter(grepl("donald", supplier, ignore.case=TRUE)) %>%
  arrange(desc(total_net_value)) %>%
  mutate(z=scale(total_net_value))

# A tibble: 643 x 6
    year supplier                      congressperson_na… party total_net_value     z
   <int> <fct>                         <fct>              <fct>           <dbl> <dbl>
 1  2009 MC DONALDS                    CELSO RUSSOMANNO   PRB              84.0  4.94
 2  2014 MC DONALDS                    FRANCISCO FLORIANO DEM              80.0  4.61
 3  2014 MC DONALDS                    EURICO JÚNIOR      PV               73.0  4.05
 4  2015 MC DONALDS                    CELSO RUSSOMANNO   PRB              71.5  3.92
 5  2009 MC DONALD'S -LMO COMERCIO DE… PAULO ROBERTO PER… PTB              67.2  3.58
 6  2015 MC DONALDS                    CÉSAR MESSIAS      PSB              64.5  3.36
 7  2013 MCDONALDS COMÉRCIO DE ALIMEN… MAGDA MOFATTO      PR               64.0  3.32
 8  2016 MC DONALDS                    CÉSAR MESSIAS      PSB              60.0  2.99
 9  2010 MC DONALDS                    JOSÉ MENTOR        PT               57.0  2.75
10  2015 MC DONALD'S COM DE ALIM LTDA  POMPEO DE MATTOS   PDT              57.0  2.75
# ... with 633 more rows
</code></pre>


Perceba que 7 deputados gastaram no McDonald's valores pelo menos 3 desvios padrão acima da média dos gastos dos outros deputados. Aparentemente, tinha gente muito faminta indo comer neste local.

Veja bem: pedir reembolso por gastos com alimentação do deputado não é algo ilegal. Não há problema algum nisso. <a href="http://www2.camara.leg.br/comunicacao/assessoria-de-imprensa/cota-parlamentar">O site da Câmara esclarece isto muito bem</a>. Entretanto, o deputado não pode usar o dinheiro do contribuinte para pagar refeições para alguém que não seja ele próprio. Assim sendo, talvez seja interessante verificar detalhadamente o que houve neste episódio. O Serenata de Amor já faz isto de forma automatizada. <a href="https://jarbas.serenata.ai/layers/#/documentId/1613811" rel="noopener" target="_blank">Podemos ver, por exemplo, que o local do maior reembolso foi uma lanchonte localizada em São Paulo, no Itaim Bibi</a>. Infelizmente, não temos acesso à nota fiscal escaneada.



## Conclusão

As aplicações deste pacote são muitas. É possível desde escrever artigos analisando os gastos dos deputados, até construir ferramentas interativas que permitam à sociedade fazer as suas próprias análises. Ou, quem sabe, criar algoritmos capazes de identificar gastos muito discrepantes que os deputados podem ter realizado, como a compra de R$84,00 que o Celso Russomano fez no McDonald's.

Entretanto, o pacote ainda não está pronto. É necessário completar e traduzir o help para o português, bem como adicionar os pedidos de reembolso do Senado Federal. Estes são trabalhos futuros, a serem realizados brevemente (ou não).

Quem estiver interessado em brincar com estes dados só precisa entrar no <a href="http://github.com/mnunes/reembolsos" rel="noopener" target="_blank">GitHub do pacote <code>reembolsos</code></a> e seguir as instruções para instalá-lo em seu computador.

E caso queira apenas fazer uma consulta rápida, utilize este [aplicativo interativo feito no shiny](http://shiny.estatistica.ccet.ufrn.br/DashboardDeputados/), criado pelo meu aluno Rayland Magalhães.




<hr>

<sup><sup>1</sup> Eu não sou estatístico, na verdade. Como meu curso de graduação foi um Bacharelado em Matemática Aplicada e tenho apenas um Doutorado em Estatística, a lei não permite que eu seja considerado um estatístico. Por isso me identifico como Cientista de Dados.</sup>

<sup><sup>2</sup> Ou apenas uma, se o usuário já tiver o <code>devtools</code> instalado e resolver executar o comando <code>devtools::install_github("mnunes/reembolsos")</code> para instalar este pacote</sup> 