---
title: "Analise os dados abertos da ANAC"
description: "Pacote no R para com os dados dos voos regulares da Agência Nacional de Aviação Civil"
tags: ["anac", "ciência de dados", "r"]
draft: false
date: 2019-12-26T7:36:00-03:00
---

Organizei todos os registros de voos do site da ANAC em um pacote do R. São mais de 20 milhões de informações referentes a todos os voos civis registrados no Brasil desde 2000, com as seguintes variáveis:

- `ICAOEmpresaAerea` - Código designador da empresa no padrão da ICAO, com três letras.
- `NumeroVoo` - Numeração do voo, com até 4 caracteres numéricos.
- `CodigoAutorizacaoDI` - Caractere utilizado para identificar o tipo de autorização para cada etapa de voo conforme IAC 1504, podendo ser 0 (voo regular), 1 (voo extra com HOTRAN), 2 (voo extra sem HOTRAN), 3 (voo de retorno), 4 (inclusão de etapa em um voo previsto em HOTRAN), 5 (voo cargueiro), 6 (voo de serviço), 7 (voo de fretamento), 9 (voo charter), A (voo de instrução) ou B (voo de experiência).
- `CodigoTipoLinha` - Identifica o tipo de operação realizada, conforme IAC 1504, sendo N (nacional), I (internacional), R (regional), H (sub-regional), E (especial), C (cargueiro), G (cargueiro internacional) e L (rede postal).
- `ICAOAerodromoOrigem` - Código ICAO do aeroporto de origem.
- `ICAOAerodromoDestino` - Código ICAO do aeroporto de destino.
- `PartidaPrevista` - Data e horário da partida prevista em horário de Brasília.
- `PartidaReal` - Data e horário da partida realizada informada pela empresa aérea, em horário de Brasília.
- `ChegadaPrevista` - Data e horário da chegada prevista em horário de Brasília.
- `ChegadaReal` - Data e horário da chegada realizada, informada pela empresa aérea, em horário de Brasília.
- `SituacaoVoo` - Campo informando se o voo foi realizado ou cancelado.
- `CodigoJustificativa` - Identifica o motivo do atraso, cancelamento e demais alterações em relação ao voo planejado, conforme IAC 1504.


[Visite meu github](https://github.com/mnunes/anac/) para encontrar o link para baixar o pacote e as suas instruções de uso.





