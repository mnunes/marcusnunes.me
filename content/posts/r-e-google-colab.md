---
title: "Como Usar o R no Google Colab"
description: "Edite seus códigos no R sem precisar comprometer a sua máquina local"
tags: ["google colab", "python", "r"]
draft: true
date: 2021-02-07T16:45:00-03:00
---

Semana passada descobri que é possível rodar códigos do R no Google Colab sem chamar funções do python para isso. Clique no link abaixo para testar essa solução no seu navegador:

[https://colab.research.google.com/#create=true&language=r](https://colab.research.google.com/#create=true&language=r)

O documento que se abre é um jupyter notebook com o runtime do R rodando por trás:

![Runtime do R no Google Colab](/images/colab_runtime.png)

Essa é uma alternativa ao [RStudio Cloud](https://rstudio.cloud/) para aqueles que não gostam de emular a IDE do RStudio dentro do navegador. Entretanto, há uma pequena limitação no uso do Google Colab com o R.

![Pacotes do R no Google Colab](/images/colab_pacotes.png)

Embora muitos pacotes conhecidos do R já venham instalados, como o famoso `tidyverse`, seu irmão `tidymodels`, que utilizo para modelagem em meu [curso de Big Data para estatísticos](https://introbigdata.org/), não está lá. É possível instalá-lo, mas essa instalação não é definitiva. Cada vez que a sessão for finalizada, é necessário reinstalar todos os pacotes novamente.

Me diga nos comentários qual é a sua experiência usando R na nuvem, seja no RStudio Cloud ou no Google Colab.