**Universidade Federal do Cariri**  
**Bacharelado em Ciência da Computação**  
**Alunos:** Karla Mikaelly Paz de Almeida e Riquelme Jatay Ribeiro S. Bezerra  
**Professor:** Ramon Santos Nepomuceno  
# Trabalho de Circuitos Digitais
## Índice
* [Introdução](#introdução)
* [Sobre o jogo](#sobre-o-jogo)
* [Componentes](#componentes)
   + [Pontuador](#pontuador)
   + [LEDS](#leds)
   + [Memória de palpite](#memória-de-palpite)
   + [Somador](#somador)
   + [Cronômetro](#cronômetro)
   + [Placar final](#placar-final)
   + [Mostrar número em decimal](#mostrar-número-em-decimal)
   + [Muda jogador](#muda-jogador)
   + [Lógica de estado permanente](#lógica-de-estado-permanente)
     
## Introdução
Olá! Nesse documento, iremos explicar o funcionamento do projeto *Guess The Number XTREME* e como ocorreu a construção de cada um dos componentes.

![Visual do jogo](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/96864027-b9c0-41f2-8a9c-5119f225e3f6)
## Sobre o jogo 

O segundo projeto da disciplina consiste em uma continuação do primeiro projeto, um jogo para dois jogadores construido pela plataforma **logisim**. O objetivo do jogo ainda é o mesmo, porém agora, com o acréscimo de um cronômetro para controlar o tempo de cada jogador, paineis com a pontuação de cada, sinalização de quem é o jogador da vez e outros detalhes que serão explorados neste relatório. O sistema funciona da seguinte forma:
   - Para iniciar o jogo, o cronômetro deve ter o tempo estabelecido pelo botão "configurar", onde os botões de unidade e dezena dos minutos e segundos são ativados e podem ser modificados.
   - Após a configuração do tempo deve desativar o botão de configurar, o "start" é acionado e o jogo inicia, o jogador da vez é escolhido e sinalizado pelos led de "Jogador da vez", e enquanto este prepara seu palpite, o seu relógio decrementa. O palpite é colocado em n° binário e ja é convertido e mostrado no display como um n° de -8 a 7, o multiplexador determina qual será o palpite a ser dado e mostrado pelos leds "palpite X" e "palpite Y", após selecionar o palpite, este deve ser confirmado e o botão "avançar estado" é selecionado para ir para o outro palpite. 
   - O palpite do jogador da vez é analisado pelo somador e este determina se o jogador errou(os leds acendem para sinalizar se foi menor ou maior) ou se acertou (Os leds sinalizam se foi igual e que acertou) e o contador do placar é incrementado em 1 para o jogador que acertar a jogada.
   - O relógio tem um clock simultâneo para os dois jogadores, quando é a vez de um jogador, o clock dele é acionado e o do outro é pausado até que o jogador da vez encerre sua jogada, daí o clock do jogador da vez pausa e passa para o jogador que estava pausado anteriormente. Caso o cronômetro de um zere, o clock não passa para ele e o jogador da vez tem seu clock constante até que seu cronômetro zere também. 
   -  Quando o cronômetro de ambos os jogadores é zerado, o painel de resultado sinalizará "fim de jogo", que jogador ganhou e a pontuação de cada um (que ja foi computada durante todo o processo do jogo). Caso algum jogador atinja 15 pontos, o jogo é encerrado e o painel mostra que ele venceu. 

## Componentes
### Pontuador 
O pontuador é o circuito sequencial utilizado para calcular o placar de cada um dos jogadores. Neste circuito temos 4 flipflops para memória e lógica de estados, e a lógica utilizada no pontuador (circuito[2]) é uma tabela de transição que vai do 0 até o 15.

![Pontuador[01]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/214e18ab-db90-428d-9f81-b934971c59d4)
Pontuador[1]

![LógicaPontuador02](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/9371c910-1efe-4b9c-98c7-062ca4ddcade)
LógicaPontuador[2]
### LEDS 

No circuito [5], a entrada "chutar" é recebida(o chute é dado no circuitoCore) e armazenada, manda sinal para o led acender de acordo com qual chute foi dado, se X ou Y ou ver resultado, e dependendo de qual deles for selecionado também irá mandar o clock de subida para que o resuldado seja armazenado no flipflop.
![Leds [5]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/2e0d9f07-992c-4d1e-ad0c-2ef3030345a7)
Led [5]

### Memória de palpite 
É o circuito sequencial que recebe um chute, e assim que o clock é acionado, esse chute de entrada entra nos flipflops como estados próximos e é atualizado para estado atual, ou seja, o chute do usuário é armazenada e o estado atual é mostrado no visor.
![MemóriaPalpite[6]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/b1773ec3-9cc7-4373-acf2-266193655afa)
Circuito [6]

### Somador
Este é o circuito que recebe o palpite do jogador para coordenada X e Y, estende o sinal deles de 4 para 5 bits e compara com os números aleatórios gerados, nessa comparação ele vai ver se cada soma é igual e se os números são iguais entre si.
![Somador [7]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/303b4a37-4da1-43dd-b5e0-65ad6c363113)

### Cronômetro 
No cronômetro, foi utilizado o circuito da dezena[10] dos minutos e segundos (Esse decrementa de 5 a 0) e o circuito da unidade[11] dos minutos e dos segundos(Esse decrementa de 9 a 0), estes tem a entrada recebida, os bits são extendidos de 4 para 1 e depois de 1 para 4, entram nos flipflops e os estados atuais são enviados para o relógio e mostrados no display do cronômetro. O cronômetro tem o botão "reset" que reinicia, o "Config" que permite modificar os minutos e segundos enquanto estiver acionado, e quando não estiver, e o clock estiver ativado, os minutos e segundos serão decrementados até que o relógio zere, dando fim no tempo que o jogador da vez tem.
![RelogioOrganizado[12]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/6f8d1a62-a74a-4b41-975d-2f5d3bdd9123)
Cronômetro[12]

![ParteDezena[10]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/8db8ff2e-9499-4565-98a3-e3c07dd99f18)
Parte da dezena[10]

![PartedaUnidade](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/7816e35e-6958-447e-9138-19fbd15f92ad)
Parte da unidade[11]

### Placar final

Este circuito utiliza constantes para ser calculado. Se o relógio de ambos os jogares for zerado, ou algum atingir 15 acertos, ele indica qual jogador venceu ou se houve um empate.

![PlacarFinal[15]](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/3b327d0d-edd4-4814-a09f-48bac4e6dcfb)

### Mostrar número em decimal 
Esse circuito recebe um número em binário e atráves de um circuito ele converte esse número em um decimal que está entre -8 e 7

![image](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/5fcff956-6359-47f4-9796-8bfddda00718)

### Muda jogador 

![image](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/a5b76602-d359-4b6a-b112-04bec889f57c)

Essa lógica diz que: Toda vez que o circuito recebe um estado atual, ele passa pelo flipflop e é negado para seu estado próximo, passando para o oponente sempre que a jogada é finalizada. 

### Lógica de estado permanente 
Essa lógica garante que após o start, o jogo continua funcionando mesmo se o botão estiver em zero. O estado começa em 0, mas após receber o 1, ele continua em 1.

![image](https://github.com/RiquelmeJ/guessTheNumberXTREME/assets/131832121/ff6e744e-3ea1-46d2-be0c-8cd6d78e5b11)


