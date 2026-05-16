# PROJETO-SNAKE-HUNGRY 1
NOME: Rian de Sousa e Sousa; CURSO: Ciência da Computação, 1° Ciclo; RA: 72.126.036-2
link do vídeo para youtube: https://youtu.be/i5Q4yCwUuQM

Neste projeto foi desenvolvido o jogo Snake Hungry, uma releitura moderna do clássico jogo da cobrinha, utilizando HTML, CSS e JavaScript para a construção da interface, estilização e implementação de toda a lógica da aplicação. Além disso, o Node.js juntamente com o Express foram utilizados para realizar o gerenciamento do servidor e das rotas responsáveis pelo carregamento das páginas do sistema. O jogo é executado diretamente no navegador por meio do elemento canvas, permitindo a renderização dinâmica de todos os componentes gráficos, como a cobra, os alimentos, a grade do tabuleiro e os obstáculos presentes durante a partida. O jogador controla a movimentação da cobra utilizando as teclas direcionais do teclado, devendo coletar os alimentos espalhados pelo mapa para aumentar sua pontuação e o tamanho da cobra.Todo o funcionamento da aplicação ocorre através da manipulação do DOM responsável pela interação entre o JavaScript e os elementos HTML da página. Além disso, o jogo utiliza atualização contínua através de um loop principal, garantindo movimentação fluida, verificação de colisões, atualização da pontuação e renderização em tempo real dos elementos presentes no canvas.

Explicação dos arquivos:

SERVIDOR:
O arquivo server.js é responsável por toda a configuração e inicialização do servidor da aplicação Snake Hungry. Ele foi desenvolvido utilizando o ambiente de execução Node.js juntamente com o Express, que facilita a criação de servidores web e o gerenciamento de rotas de forma simples e organizada.  Sua principal função é permitir que o navegador consiga acessar corretamente todas as páginas, arquivos CSS, JavaScript e imagens do projeto. Para isso, o servidor configura uma pasta pública chamada public, responsável por armazenar os arquivos estáticos da aplicação, como estilos, imagens e códigos JavaScript utilizados pelo jogo. Além disso, o arquivo define as rotas principais do sistema, determinando qual página HTML será exibida quando o usuário acessar determinados endereços no navegador. Por exemplo, ao acessar a rota /, o servidor carrega a página inicial do projeto; já nas rotas /cobra e /devs, são carregadas respectivamente a tela do jogo e a página do desenvolvedor. Outro papel importante do server.js é manter a aplicação em execução localmente através da porta 3000, permitindo que o jogo funcione em um ambiente web acessível pelo navegador através do endereço http://localhost:3000.

Principais funções do server.js:
#Importação de módulos
const express = require("express")  /*importa o framework Express*/
const path = require("path") /*ajuda a localizar arquivos e pastas*/

#Criação do servidor
const app = express() /*cria a aplicação do servidor*/

#Configuração da pasta pública
app.use(express.static(path.join(__dirname, "public"))) /*Permite que o CSS, javascript e o HTML sejam carregados*/

#Sistema de Rotas
app.get("/", (req, res) => {}) /*Define qual página será exibida*/

#Inicialização do servidor
app.listen(3000)

Após realizar todas as configurações necessárias e instalar as dependências do projeto, o servidor pode ser iniciado através do terminal utilizando o comando node server.js. Esse comando executa o arquivo principal da aplicação responsável pela criação do servidor utilizando Node.js e Express. Quando o servidor é iniciado corretamente, o terminal exibe a mensagem informando que a aplicação está rodando no endereço http://localhost:3000. A partir desse momento, o navegador já consegue acessar todas as páginas do sistema, incluindo o menu principal, a tela do jogo e a página do desenvolvedor. O servidor permanece em execução continuamente até que o processo seja encerrado manualmente no terminal.

PÁGINAS HTML:
Todos os HTML'S foi feita a importação do CSS:
<link rel="stylesheet" href="/css/style.css">
Essa linha conecta o arquivo CSS ao HTML.O CSS é responsável pela aparência visual do jogo, como cores, tamanhos, alinhamentos e animações.

O arquivo index.html funciona como a página inicial do projeto Snake Hungry. Ele é responsável por apresentar o jogo ao usuário antes da partida começar.Nessa página normalmente vai informar o título do jogo, as instruções, os controles do teclado e o botão para iniciar o jogo. O objetivo principal dessa tela é servir como menu inicial da aplicação.

O arquivo cobra.html é a principal página do projeto, pois é nele que o jogo realmente funciona.Essa página contém:o canvas do jogo, o placar, o recorde, a tela de game over e o botão de reinício.
Canvas: 
<canvas width="600" height="600"></canvas>
O canvas é a área onde todos os elementos do jogo são desenhados usando JavaScript. Dentro do canvas aparece a cobra, comida, obstáculo e a grade do cenário;

Pontuação:
<div class="score">
    Score: <span class="score--value">00</span>
</div>
Essa parte mostra a pontuação atual do jogador durante a partida. O JavaScript altera o valor automaticamente sempre que a cobra come uma comida;

Recorde:
<div class="high-score">0</div>
Mostra o maior recorde salvo no navegador utilizando localStorage;

Tela de Game Over:
<div class="menu-screen">
Essa área aparece quando o jogador perde. Ela exibe: Pontuação final, botão para reiniciar e tela de derrota;

Botão de Reinício:
<button class="btn-play">
    Jogar Novamente
</button>
Esse botão reinicia toda a partida quando clicado;

Importação do JavaScript:
<script src="/js/script.js"></script>
Importa o arquivo JavaScript responsável por toda a lógica do jogo.

O arquivo devs.html funciona como uma página de apresentação do desenvolvedor do projeto.Nele está meu nome, email, Ra, curso e a minha foto 

CSS:
O CSS é responsável por toda a aparência visual do projeto Snake Hungry. Ele melhora a experiência do jogador através de cores, alinhamentos, animações e efeitos visuais. Além disso, ajuda a organizar os elementos da interface e deixa o jogo mais moderno e agradável visualmente.

Reset e Configurações Gerais:
*{
    margin: 0; /*remove margens externas*/
    padding: 0; /*remove espaçamentos internos*/
    box-sizing: border-box; /*faz com que largura e altura incluam bordas e espaçamentos, facilitando o controle do layout*/
}
Esse trecho remove os espaçamentos padrões do navegador;

Corpo da Página:
body{
    background-color: #111; /*altera a cor de fundo*/
    display: flex; /*ativa o Flexbox para facilitar o alinhamento dos elementos*/
    justify-content: center; /*ativa o Flexbox para facilitar o alinhamento dos elementos*/
    align-items: center; /*centraliza verticalmente*/
}
O body define o estilo principal da página;

Estilo do Canvas:
canvas{
    border: 4px solid white; /*A borda branca destaca o canvas na tela*/
    background-color: black;/*O fundo preto melhora a visualização da cobra, comida e obstáculos*/
}
Esse estilo personaliza a área do jogo.

Sistema de Pontuação
.score{
    color: white;/*O color altera a cor do texto*/
    font-size: 2rem; /*O font-size aumenta o tamanho da fonte para facilitar a leitura*/
}
Define a aparência do placar.

Tela de Game Over:
.menu-screen{
    position: fixed;/*O position: fixed faz o menu ficar sobre o jogo*/
    display: none; /*O display: none mantém a tela escondida até o jogador perder*/
}
Essa classe controla a tela de derrota.

Botão de Reinício:
.btn-play{
    padding: 10px 20px; /*O padding aumenta o tamanho interno do botão*/
    cursor: pointer; /*muda o cursor do mouse para indicar que o botão pode ser clicado*/
}
Personaliza o botão de jogar novamente.

JS:
O arquivo script.js é a principal parte do projeto Snake Hungry, pois ele controla toda a lógica e funcionamento do jogo. É através dele que acontecem a movimentação da cobra, o sistema de pontuação, as colisões, os obstáculos, o aumento de velocidade e a atualização da tela em tempo real. O código foi dividido em várias partes para organizar melhor cada funcionalidade do jogo.

Seleção do Canvas:
const canvas = document.querySelector("canvas") /*área onde o jogo será desenhado*/
const ctx = canvas.getContext("2d") /*cria um contexto gráfico 2D chamado ctx*/

O primeiro passo do código é selecionar o elemento <canvas> do HTML. Esse contexto permite desenhar: Quadrados, linhas, cores, Objetos e elementos gráficos;

Seleção dos Elementos da Interface:
const score = document.querySelector(".score--value")/*Mostra a pontuação atual da partida*/
const finalScore = document.querySelector(".final-score > span")/*Mostra a pontuação final no menu de game over*/
const menu = document.querySelector(".menu-screen")/*Representa a tela que aparece quando o jogador perde*/
const buttonPlay = document.querySelector(".btn-play")/*Botão responsável por reiniciar a partida*/
const highScoreElement = document.querySelector(".high-score") /*Mostra o maior recorde salvo*/

Aqui o JavaScript seleciona vários elementos do HTML. Esses elementos serão manipulados durante o jogo;

Configurações do Jogo:
const size = 30 /*Define o tamanho de cada bloco*/
const initialPosition = { x: 270, y: 240 } /*Posição inicial da cobra*/
const initialSpeed = 400 /*Velocidade inicial do jogo*/

Essas constantes definem as configurações principais do jogo. A variável size determina o tamanho de cada bloco da cobra, comida e obstáculos. A variável initialPosition define a posição inicial da cobra dentro do canvas. Já initialSpeed define a velocidade inicial do jogo em milissegundos;

Variáveis Principais:
let speed = initialSpeed /*Velocidade atual*/
let snake = [initialPosition] /*Array da cobra*/
let direction /*Direção da cobra*/
let loopId /*ID do loop principal*/
let obstacles = [] /*Array de obstáculos*/

Essas variáveis armazenam informações importantes durante a execução do jogo. A variável speed guarda a velocidade atual da partida. O array snake armazena todas as partes do corpo da cobra. A variável direction guarda a direção atual do movimento. O loopId salva o identificador do loop principal do jogo. Já obstacles armazena todos os obstáculos do cenário;

Sistema de Pontuação:
const incrementScore = () => {
    score.innerText = +score.innerText + 10
}
Essa função aumenta a pontuação do jogador sempre que a cobra come a comida. O sinal + antes do score.innerText converte o texto em número. Depois disso, o valor 10 é somado ao placar;

Sistema de Ranking:
localStorage.getItem("highScore")
O sistema de ranking utiliza o localStorage, uma memória interna do navegador. Ele salva o maior recorde do jogador mesmo após fechar a página. Quando o jogo termina, o código compara a pontuação atual com o recorde salvo e atualiza caso a nova pontuação seja maior.

Funções Aleatórias:
const randomNumber = (min, max) =>
    Math.round(Math.random() * (max - min) + min)
Essa função gera números aleatórios. Ela é utilizada para criar posições aleatórias da comida e dos obstáculos dentro do canvas.

Posição Aleatória:
const randomPosition = () => {
    const number = randomNumber(0, canvas.width - size)
    return Math.round(number / size) * size
}
Essa função gera posições alinhadas na grade do jogo. Isso garante que comida e obstáculos apareçam corretamente dentro dos blocos;

Cor Aleatória:

const randomColor = () =>
`rgb(${randomNumber(0,255)},${randomNumber(0,255)},${randomNumber(0,255)})`
Essa função gera cores aleatórias para a comida utilizando o sistema RGB;

Sistema de Comida:
const food = {
    x: randomPosition(),
    y: randomPosition(),
    color: randomColor()
}
A comida é representada por um objeto contendo posição X, posição Y e cor. Sempre que a cobra come a comida, esses valores são alterados;

Sistema de Obstáculos:
const generateObstacles = () => {
Essa função gera obstáculos aleatórios no mapa. O código verifica para que os obstáculos não apareçam em cima da cobra ou da comida;

Funções de Desenho:
const drawFood = () => {}
const drawObstacles = () => {}
const drawSnake = () => {}
const drawGrid = () => {}
As funções de desenho são responsáveis por mostrar todos os elementos visuais do jogo dentro do canvas. Elas desenham a comida, os obstáculos, a cobra e a grade do cenário;

Movimento da Cobra:
const moveSnake = () => {
Essa função controla toda a movimentação da cobra. O código pega a cabeça da cobra, cria uma nova posição baseada na direção atual e adiciona essa nova cabeça ao array da cobra;

Crescimento da Cobra:
snake.push(newHead)
Esse comando adiciona uma nova parte ao corpo da cobra sempre que ela se move;

Remoção da Cauda:
snake.shift()
Esse comando remove a primeira posição do array da cobra, criando o efeito de movimentação;

Verificação de Comida:
const checkEat = () => {
Essa função verifica se a cabeça da cobra encostou na comida. Quando isso acontece, o placar aumenta, a velocidade aumenta e uma nova comida aparece.

Sistema de Velocidade:
speed = Math.max(100, speed - 10)o
A velocidade aumenta gradualmente conforme o jogador come comidas. O valor mínimo permitido é 100;

Sistema de Colisão:
const checkCollision = () => {
Essa função verifica colisões com: Paredes, corpo da cobra e obstáculos. Caso alguma colisão aconteça, o jogo termina;

Game Over:
const gameOver = () => {
Essa função é executada quando o jogador perde. Ela encerra o loop do jogo, atualiza o recorde, exibe o menu de game over e aplica um efeito de blur no canvas;

Loop Principal:
const gameLoop = () => {
O loop principal é responsável por atualizar continuamente todos os elementos do jogo. Ele limpa a tela, desenha os elementos, move a cobra e verifica colisões;

Atualização Contínua:
setTimeout(gameLoop, speed)
Esse comando faz o loop principal ser executado repetidamente, criando a animação do jogo;

Atualização Contínua:
setTimeout(gameLoop, speed)
Esse comando faz o loop principal ser executado repetidamente, criando a animação do jogo;

Bloqueio da Rolagem:
event.preventDefault()
Impede que a página do navegador role quando as setas do teclado forem utilizadas;

Sistema de Reset:
buttonPlay.addEventListener("click", () => {
Essa função reinicia completamente o jogo. Ela zera o placar, reseta a cobra, gera novos obstáculos e inicia uma nova partida.

Conclusão:
O desenvolvimento do Snake Hungry permitiu aplicar diversos conceitos importantes da programação web de forma prática e organizada. Durante o projeto foram utilizados HTML para estruturar as páginas, CSS para estilização da interface e JavaScript para toda a lógica do jogo, incluindo movimentação, colisões, pontuação, obstáculos, velocidade e atualização em tempo real do canvas. Além do funcionamento do jogo, o projeto também trabalhou conceitos como manipulação do DOM, arrays, objetos, eventos de teclado, funções, estruturas de repetição, armazenamento com localStorage e controle de animações. A separação dos arquivos em páginas e funções específicas ajudou na organização do código e facilitou a manutenção da aplicação. O resultado final foi um jogo funcional, interativo e totalmente executado no navegador, demonstrando como tecnologias web podem ser utilizadas no desenvolvimento de aplicações dinâmicas e jogos 2D.




































































