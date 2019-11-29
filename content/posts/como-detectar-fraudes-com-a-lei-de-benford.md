---
title: "Como Detectar Fraudes nas Contas dos Deputados Federais Utilizando a Lei de Benford"
description: "Vamos procurar possíveis números maquiados em relatórios de gastos de deputados federais"
tags: ["analise", "ferramenta"]
draft: true
date: 2018-07-27T08:15:00-03:00
---

## Introdução

Neste texto vou mostrar como procurar por fraudes nos pedidos de reembolsos feitos pelos deputados federais brasileiros. Pra quem não sabe, [eu criei uma ferramenta](http://marcusnunes.me/post/controle-de-gastos-publicos-como-verificar-quanto-os-deputados-federais-estao-gastando/)


## O Que Diz a Lei de Benford?

A Lei de Benford diz que um conjunto de números é dito satisfazer a Lei de Benford se o primeiro dígito $d$ deste número ocorrer com probabilidade $P(d)$ dada por

$$P(d) = \log_{10} \left( 1 + \frac{1}{d} \right)$$

Esta fórmula indica que, quanto maior o valor do dígito, menor a probabilidade dele ocorrer. A tabela abaixo deixa isto mais explícito:

| $d$  | $P(d)$ |
|--:|---|
| 1  |  30,1% |
| 2  |  17,6% |
| 3  |  12,5% |
| 4  |   9,7% |
| 5  |   7,9% |
| 6  |   6,7% |
| 7  |   5,8% |
| 8  |   5,1% |
| 9  |   4,6% |

Ou seja, se tivermos um conjunto grande de números coletados de maneira adequada, se espera que 30,1% destes números comecem com o algorismo 1; 17,6% deles comecem com o dígito 2; 12,5% dele com o dígito 3; e assim por diante. 

Mais informações sobre este assunto podem ser obtidas na [Wikipedia em Inglês](https://en.wikipedia.org/wiki/Benford%27s_law), pois o [verbete sobre a Lei de Benford em português](https://pt.wikipedia.org/wiki/Lei_de_Benford) não é muito completo.

## E como usar isso na prática?

A ideia é simples: se a proporção dos dígitos dos pedidos de reembolsos dos deputados federais fugirem destas características, talvez seja interessante passar um pente fino nestes dados, a fim de detectar qualquer irregularidade cometida.







