**Universidade Federal do Cariri**  
**Bacharelado em Ciência da Computação**  
**Alunos:** Karla Mikaelly Paz de Almeida e Riquelme Jatay Ribeiro S. Bezerra  
**Professor:** Ramon Santos Nepomuceno  
# Trabalho de Circuitos Digitais
## Índice
* [Introdução](#introdução)
* [Sobre o jogo](#sobre-o-jogo)
* [Componentes](#componentes)
   + 
## Introdução
Olá! Nesse documento, iremos explicar o funcionamento do projeto *Guess The Number XTREME* e como ocorreu a construção de cada um dos componentes.

![Visual do jogo](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/96864027-b9c0-41f2-8a9c-5119f225e3f6)
## Sobre o jogo 

O segundo projeto da disciplina consiste em uma continuação do primeiro projeto, um jogo para dois jogadores construido pela plataforma **logisim**. O objetivo do jogo ainda é o mesmo, porém agora, com o acréscimo de um cronômetro para controlar o tempo de cada jogador, paineis com a pontuação de cada, sinalização de quem é o jogador da vez e outros detalhes que serão explorados neste relatório. O sistema funciona da seguinte forma:
    -Para iniciar o jogo, o cronômetro deve ter o tempo estabelecido pelo botão "configurar", onde os botões de unidade e dezena dos minutos e segundos são ativados e podem ser modificados.
    -Após a configuração do tempo, o "start" é acionado e o jogo inicia, cada jogador da vez é sinalizado pelos led de "Jogador da vez", e enquanto este prepara seu palpite, o seu relógio decrementa. O palpite é determinado pelos leds "palpite X" e "palpite Y", após selecionar o palpite, este deve ser confirmado e o botão "avançar estado" é selecionado para ir para o outro palpite. 
    -O palpite do jogadoe da vez é analisado pelo comparador e este determina se o jogador errou(os leds acendem para sinalizar se foi menor ou maior) ou se acertou (Os leds sinalizam se foi igual e que acertou)
    -Quando o cronômetro de ambos os jogadores é zerado, o painel de resultado sinalizará "fim de jogo", que jogador ganhou e a pontuação de cada um (que ja foi computada durante todo o processo do jogo).
