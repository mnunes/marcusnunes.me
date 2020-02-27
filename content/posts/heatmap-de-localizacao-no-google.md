---
title: "Heatmap com os dados de geolocalização do Google Location History: minha viagem pela Itália"
description: "Como utilizar o python para gerar um heatmap da sua localização no Google"
tags: ["ciência de dados", "google", "geolocalização", "heatmap", "itália", "python", "portugal", "viagem", "visualização de dados"]
draft: false
date: 2020-01-27T15:14:00-03:00
---

Uma das coisas que mais gosto na modernidade são os serviços de localização. Sim, eu sei que a minha suposta privacidade é completamente perdida quando compartilho meus dados de localização o tempo todo, mas acredito que as facilidades que isso me traz superam, e muito, as desvantagens. O problema é que eu não sabia muito o que fazer com estes dados.

Mas eis que um usuário do github chamado [luka1199](https://github.com/luka1199/) criou o repositório [Generate an interactive geo heatmap from your Google location data](https://github.com/luka1199/geo-heatmap) para auxiliar na geração de heatmaps a partir dos dados de localização dos usuários. Ele permite que qualquer pessoa baixe seus dados do Google e gere, com muito pouco trabalho, visualizações interessantes sobre seus hábitos de movimentação.

Por exemplo, este é o heatmap que gerei a partir das minhas férias na Itália e Portugal, entre Dezembro de 2019 e Janeiro de 2020. Comecei em Veneza e de lá desci para Florença, Roma, Nápoles, Catânia, Siracusa, Agrigento e Palermo, para depois seguir para Lisboa e Sintra, em Portugal.

![Mapa da Itália](/images/italia.png)

![Mapa de Portugal](/images/portugal.png)

Logicamente, estas são imagens estáticas, mas ao final do post eu coloquei o mapa interativo para vocês verem como ele funciona na prática.

Para quem já tem um pouco de experiência com [python](https://marcusnunes.me/tags/python), o script é muito fácil de usar:

1. Instale o [python 3+](https://www.python.org/downloads/) em seu computador
2. Baixe seus dados de localização a partir do [Google Takeout](https://takeout.google.com/)
3. Clone o [repositório](https://github.com/luka1199/geo-heatmap) com os scripts necessários em sua máquina local ou na nuvem
4. Rode o comando `pip install -r requirements.txt` na pasta com o repositório clonado
5. Por fim, execute `python geo_heatmap.py NomeDoArquivo.json` para gerar o seu mapa interativo

O meu heatmap interativo pode ser visualizado abaixo:

<iframe src="/images/heatmap.html" width=100% height=600></iframe>

Comente aqui embaixo o que você achou dessa ferramenta. Ou, caso não tenha conseguido usá-la, relate as suas dificuldades.

Aproveite que chegou até aqui e me siga no [instagram](https://instagram.com/grandeabobora/) para ver as fotos que estou publicando a respeito dessa viagem. 

{{< instagram B625CmDBMHU >}}










