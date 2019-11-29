---
title: "Resultados da Competição de Ciência de Dados da UFRN 2019"
description: "Descubra quem apresentou a melhor análise de dados para o problema proposto neste ano"
tags: ["ciência de dados", "competição", "ufrn"]
draft: false
date: 2019-10-31T19:03:00-03:00
---

[Conforme eu havia avisado anteriormente](https://marcusnunes.me/posts/competicao-de-ciencia-de-dados-da-ufrn-2019/), o Departamento de Estatística da UFRN promoveu mais um vez a sua tradicional competição de Ciência de Dados entre os alunos da universidade. 

![Logo da Competição de Ciência de Dados da UFRN 2019](/images/ccd_2019.png)

Desta vez, a banca avaliadora não contava apenas com professores do Departamento de Estatística como na [competição de 2018](https://marcusnunes.me/posts/como-foi-a-competicao-de-ciencia-de-dados/). No centro da foto abaixo, que contempla todos os competidores, é possível ver lado a lado Leonardo Bezerra, professor do IMD, Carla Vivacqua e eu, professores do Departamento de Estatística.

![Competidores presentes na edição de 2019](/images/IMG_2195.jpg)

Foram 21 competidores divididos em 7 equipes. O desafio era os dados coletados pelo INMET - Instituto Nacional de Meteorologia. Estes dados podem ser baixados a partir do endereço [https://www.dropbox.com/s/7rriacb7c6vzf3m/ccd_2019.zip?dl=0](https://www.dropbox.com/s/7rriacb7c6vzf3m/ccd_2019.zip?dl=0) . O arquivo zipado tem 214MB. Eles foram obtidos com a ajuda de um pacote do R chamado inmetr - [https://github.com/jdtatsch/inmetr](https://github.com/jdtatsch/inmetr) - , criado pelo Professor Jonatan Tatsch, da Universidade Federal de Santa Maria.

São dois arquivos dentro do zip. O arquivo `inmetr.csv` possui informações sobre as seguintes variáveis:

    variável                                descrição       unidade
        date                     data e hora da coleta             -
          id                   ID da estação de coleta             -
        prec                              precipitação            mm
        tair                         temperatura do ar graus Celsius
          tw                temperatura de bulbo úmido graus Celsius
        tmax                  temperatura máxima do ar graus Celsius
        tmin                  temperatura mínima do ar graus Celsius
       urmax                   umidade relativa máxima             %
        patm                       pressão atmosférica           hPa
        pnmm pressão atmosférica média ao nível do mar           hPa
          wd                          direção do vento         graus
       wsmax                          rajadas de vento           m/s
           n                              horas de sol             h
          cc                       cobertura de nuvens             -
        evap                                evaporação            mm
          ur                          umidade relativa             %
          ws                       velocidade do vento           m/s

O arquivo `bdmep_meta.csv` possui informações sobre as estações de coleta, relacionando-as com a variável id do arquivo `inmetr.csv`.

As equipes precisaram seguir algumas poucas regras gerais:

- O prazo limite para a entrega das análises era 23:59 de 27 de outubro de 2019.

- As apresentações deveriam se limitar a 10 minutos e 3 slides

- Qualquer análise era válida, desde visualizações dos dados até algum tipo de modelagem

Após as apresentações, a banca decidiu que as 3 equipes melhores colocadas foram estas listadas abaixo, com as suas respectivas apresentações e relatórios linkados na sequência:

## 3º Lugar: numberOne

![Number One: Jordão de Lima Alves](/images/IMG_2174.jpg)

Jordão de Lima Alves (Ciências Atuariais) criou a equipe de um homem só e faturou o terceiro lugar. Ele utilizou métodos de séries temporais para analisar alguns dados climatológicos da cidade de Apodi, no Rio Grande do Norte. Saiba mais detalhes sobre o trabalho dele lendo os [slides](/images/ciencia_de_dados_2019/numberOne_Apresentacao.pdf) e o [relatório](/images/ciencia_de_dados_2019/numberOne_Relatorio.pdf) entregues.


## 2º Lugar: weeee

![weeee: André Fellipe da Silva, Ianca Maria Leite da Costa, Vítor Saraiva Ramos, André Luis Andrade Machado e Mariana Costa](/images/IMG_2178.jpg)

Os alunos André Fellipe da Silva (Graduação em Engenharia Elétrica), Ianca Maria Leite da Costa (Graduação em Engenharia Elétrica), Vítor Saraiva Ramos (Mestrado em Engenharia Elétrica e de Computação), André Luis Andrade Machado (Graduação em Engenharia Elétrica) e Mariana Costa (Graduação em Engenharia de Produção) se reuniram para analisar os dados meteorológicos disponíveis sobre 19/08/2019, o "dia que virou noite" devido à fumaça proveniente das queimadas na Amazônia. Baixe os [slides](/images/ciencia_de_dados_2019/weeee_Apresentacao.pdf) e o [relatório](/images/ciencia_de_dados_2019/weeee_Relatorio.pdf) para ver o que esta equipe produziu. Acesse a [apresentação de slides na web](http://bit.ly/slides_wee) para ver uma animação que a equipe produziu para ilustrar os seus achados. As análises podem ser reproduzidas com o [código em python](https://github.com/vitorsr/ccd) escrito pela equipe.

## 1º Lugar: Featuring the Future

![Number One: Daniel Marx Pinto Carvalho, Marcos Vinícius Gomes Jacinto, Gilvandro César de Medeiros e Marcus Vinicius Oliveira de Brito](/images/IMG_2185.jpg)

Os grandes campeões do evento foram os alunos Daniel Marx Pinto Carvalho (Graduação em Tecnologia da Informação), Marcos Vinícius Gomes Jacinto (Programa de Pós-Graduação em Geodinâmica e Geofísica), Gilvandro César de Medeiros (Bacharelado em Ciências e Tecnologia) e Marcus Vinicius Oliveira de Brito (Graduação em Engenharia Elétrica). Como o conjunto de dados disponibilizado durante a competição possuía muitos dados faltantes, eles utilizaram _deep learning_ para imputar as informações faltantes, além de analisar o potencial eólico das cidades brasileiras utilizando a distribuição Weibull. Seus achados estão disponíveis nos [slides](/images/ciencia_de_dados_2019/Featuring_the_Future_Slides.pdf), no [relatório](/images/ciencia_de_dados_2019/Featuring_the_Future_Relatorio.pdf) e no [código](https://github.com/gilvandrocesardemedeiros/CCD) fornecidos pela equipe.


