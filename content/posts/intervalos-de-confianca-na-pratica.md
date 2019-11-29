---
title: "Intervalos de Confiança na Prática"
description: "Aprenda de maneira definitiva como trabalhar com intervalos de confiança"
tags: ["estatística", "ferramenta", "R", "shiny"]
draft: false
date: 2018-02-02T12:54:00-03:00
---

A construção de <a href="https://pt.wikipedia.org/wiki/Intervalo_de_confiança">Intervalos de Confiança</a> é bastante simples. Entretanto, seu conceito nem sempre é entendido por quem trabalha com eles, principalmente os iniciantes. Pensando nisso, desenvolvi <a href="http://shiny.estatistica.ccet.ufrn.br/IC">um aplicativo</a> capaz de simplificar o entendimento do processo.

Segundo o livro Estatística Básica (Bussab e Morettin, 2014), a definição de intervalo de confiança a 95% para o parâmetro da média populacional $\mu$, quando a variância populacional $\sigma^2$ é conhecida, é dada por

> Se pudéssemos construir uma quantidade grande de intervalos aleatórios da forma 
> 
> $$(\overline{X}-1.96S, \overline{X}+1.96S),$$
> 
> em que $S = \sigma_{\overline{X}}$, todos baseados em amostras de tamanho $n$, 95% deles conteriam o parâmetro $\mu$.

Ou seja, por esta definição, não temos a garantia de que o verdadeiro parâmetro $\mu$ estará dentro do intervalo de confiança calculado com 95% de chance. A única certeza que temos é que, se repetirmos o procedimento de construção do intervalo de confiança um número grande de vezes, 95% deles vão conter o parâmetro $\mu$.

Logicamente, isto significa que 5% dos intervalos de confiança calculados não possuem o verdadeiro parâmetro de interesse da população estudada. O problema é que nunca sabemos que intervalos de confiança são estes.

Embora eu tenha criado o aplicativo apenas para o parâmetro $\mu$, a lógica acima vale para a construção de qualquer intervalo de confiança.

<a href="http://shiny.estatistica.ccet.ufrn.br/IC">Experimente o aplicativo</a> por si mesmo e veja se ficou clara como a construção de intervalos de confiança é definida. O código utilizado para criar o aplicativo pode ser encontrado <a href="https://github.com/mnunes/IntervalosDeConfianca">no meu github</a>.