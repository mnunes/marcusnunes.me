---
title: "Como Instalar o shiny server em seu Próprio Servidor"
description: "Crie o seu próprio servidor web de aplicativos estatísticos interativos"
tags: ["linux", "servidor", "R", "shiny", "ubuntu"]
draft: false
date: 2019-05-01T14:10:00-03:00
---

# Introdução

O pacote [shiny](https://marcusnunes.me/shiny/) do R é uma excelente ferramenta para criar aplicações web com as seguintes funções:

1. mostrar como a Estatística pode ser utilizada para ensino 
2. divulgação de informações públicas através de uma ferramenta interativa
3. ferramenta de controle de produção em empresas (dashboards, no jargão popular)


[Eu mantenho uma página no site da universidade](http://shiny.estatistica.ccet.ufrn.br) com aplicações criadas por mim e por meus alunos que ilustram o poder desta ferramenta.

Qualquer pessoa pode utilizar gratuitamente o site [shinyapps.io](https://www.shinyapps.io/) para hospedar as suas próprias criações. Entretanto, por ser um serviço gratuito, ele apresenta diversas limitações de uso. Por isso, o tutorial abaixo mostra como instalar o shiny em um servidor utilizando Ubuntu 18.04, a versão LTS mais atual de uma das distribuições de Linux mais utilizadas. 

Caso o seu uso do [shiny](https://marcusnunes.me/tags/shiny/) seja acadêmico, [mande um email para mim](https://marcusnunes.me/contato/) que podemos conversar a respeito de hospedagem gratuita para o seu aplicativo no [meu site](http://shiny.estatistica.ccet.ufrn.br), sem limitação alguma.



## Instalação do R

Vou assumir a partir de agora que o leitor dispõe de um servidor remoto com Ubuntu 18.04 instalado e que possui privilégios de administrador nesta máquina. Na verdade, é possível utilizar comandos bem parecidos com estes para instalar o shiny em qualquer servidor Linux. Bastam pequenas alterações no script.

Antes de instalar o R, é preciso fazer a atualização do Ubuntu através do comando

    sudo apt-get update && sudo apt-get dist-upgrade

Para um uso despreocupado da ferramenta, recomendo pelo menos 10GB de espaço em disco disponível. Dá para instalar o shiny com menos espaço do que isso, mas é possível que falte espaço para pacotes do R ou para os dados a serem analisados.  Para checar o espaço disponível na sua máquina, rode o comando

    df -h

Em seguida, é necessário instalar alguns pacotes extras no Ubuntu. Isto é resolvido através do comando

    sudo apt install apt-transport-https software-properties-common

Para instalar o R, é necessário alterar o arquivo de sistema com informações sobre repositórios de programas. Isto é feito da seguinte forma no Ubuntu:

    sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9

Agora sim podemos finalmente instalar o R. Rodo os comandos abaixo caso ele ainda não esteja instalado em seu servidor. 

    sudo apt update
    sudo apt install -y r-base r-base-core r-recommended

Alguns pacotes do R precisarão de programas especiais para serem instalados. Estes programas são instalados da seguinte maneira:

    sudo apt install -y build-essential libcurl4-openssl-dev libxml2-dev openjdk-8-jdk git libssl-dev

Além disso, o java exige algumas configurações extras que devem ser realizadas da seguinte maneira:

    export LD_LIBRARY_PATH=/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server
    sudo R CMD javareconf

Por fim, caso seu servidor tenha pouco espaço em disco, é preciso atualizar o local em que os pacotes do R serão instalados. Para fazer isso, abra o arquivo `Renviron` com o seguinte comando:

    sudo nano /usr/lib/R/etc/Renviron

Após o editor de texto estar aberto, procure a primeira linha abaixo e comente-a, colocando o caractere `#` na sua frente. Em seguida, copie e cole a instrução `R_LIBS_USER=${R_LIBS_USER-‘~/Library/R/3.5/library’}` logo abaixo. No final ,é isto que deve estar presente no arquivo:

    #R_LIBS_USER=${R_LIBS_USER-‘~/R/x86_64-pc-linux-gnu-library/3.0’}
    R_LIBS_USER=${R_LIBS_USER-‘~/Library/R/3.5/library’}

Com o R configurado, agora é hora de iniciar o programa como usuário root para instalar pacotes para todos os usuários. Rode 

    sudo -i R

para fazer isto. Vamos instalar alguns pacotes da maneira como sempre foi feito no R:

    install.packages(c("shiny", "tidyverse", "devtools"), 
	  repos = "https://cran.rstudio.com/",
	  dependencies=TRUE)

Estou colocando `repos="https://cran.rstudio.com/"` como repositório porque já vi alguns usuários reportarem que tiveram problemas ao instalar o shiny sem fazer isso. 

Em seguida, devemos deixar a pasta dos pacotes legível para o shiny. Para saber que pasta é esta, rode o comando abaixo no R:

    .libPaths() # /usr/local/lib/R/site-library é o meu resultado; isto pode variar

Para deixar a pasta dos pacotes legível para o shiny, saia do R e rode o seguinte comando no terminal:

    sudo chmod 777 /usr/lib/R/site-library # lembre-se de alterar o que vem depois de 777 com o resultado de .libPaths()



## Instalação do shiny server

Finalmente, podemos instalar o servidor do shiny. O endereço de download abaixo pode estar desatualizado no momento em que este post está sendo lido. [Visite este site](https://www.rstudio.com/products/shiny/download-server/) para obter a versão mais recente do servidor.

    sudo apt install -y gdebi-core
    wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.9.923-amd64.deb
    sudo gdebi shiny-server-1.5.9.923-amd64.deb

Rode o comando abaixo para permitir que outros usuários vejam seus apps:

    sudo chmod -R 777 /srv

Por fim, teste o seu novo servidor em um browser, substituindo o ip abaixo pelo ip ou domínio do seu site:

    127.0.0.1:3838

Tudo deve estar funcionando neste momento. Parabéns!

## Instalação dos web apps

Para rodar os seus próprios apps no servidor, copie a pasta com os arquivos dos apps (em geral, `global.R`, `server.R` e `ui.R`) para o servidor e mova-os para a pasta `/srv/shiny-server/`:

    sudo mv PastaComApp /srv/shiny-server/

Agora é só acessar os apps através da pasta na qual eles estão

    127.0.0.1:3838/PastaComApp


## Manutenção do Servidor

Para substituir a porta do servidor e não ter que ficar digitando a porta de acesso toda vez que desejar acessar um app, rode

    sudo nano /etc/shiny-server/shiny-server.conf

Dentro do editor, altere a linha 

    listen 3838;

para

    listen 80;

Reinicie o servidor do shiny:

    sudo systemctl restart shiny-server

Para verificar seu status, isto é, para checar se ele está rodando de fato, rode

    sudo systemctl status shiny-server

Este comando deve retornar a informação de que o sistema está rodando.

Eu recomendo que, para evitar problemas de segurança, o seu Ubuntu seja atualizado periodicamente. Para isso, rode o comando

    sudo apt-get update && sudo apt-get dist-upgrade -y && sudo apt-get autoremove -y

Para atualizar os pacotes do R, rode

    sudo Rscript -e 'update.packages(repos="http://cran.rstudio.com", ask=FALSE); source("http://bioconductor.org/biocLite.R"); biocLite(ask=FALSE)'


## Conclusão

Estes são os passos gerais para a instalação do shiny server em uma máquina rodando Linux. Em condições normais, este procedimento leva em torno de duas a três horas para ser completado. O tempo vai depender de vários fatores, como a experiência de quem estiver realizando-o, a velocidade de conexão à internet do servidor e até mesmo a facilidade en resolver alguns detalhes chatos que podem surgir pelo caminho.

Caso a sua empresa esteja interessada em fazer uso deste serviço e não tenha pessoal habilitado, saiba que estou disponível para prestar [consultoria](https://marcusnunes.me/consultoria/) no assunto. Além disso, ofereço treinamento personalizado em R e estatística. [Entre em contato](https://marcusnunes.me/contato/) para saber mais a respeito.

Não custa lembrar que se o uso do [shiny](https://marcusnunes.me/tags/shiny/) pela tua parte é acadêmico, [mande um email para mim](https://marcusnunes.me/contato/) que podemos conversar a respeito de hospedagem gratuita para o seu aplicativo no [meu site](http://shiny.estatistica.ccet.ufrn.br), sem limitação alguma.
