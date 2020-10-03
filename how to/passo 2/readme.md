# Game Multiplayer

## Passo 2
Agora podemos programar todos os graficos dentro do canvas e vamos utilizar programação para isso !

Antes de continuar-mos, precisamos pensar de forma abstrata o conceito. Temos um canvas desenhado em formato quadrado, com 500px de largura e 500px de altura, onde podemos desenhar o que quisermos.

Vamos imaginar que precisamos desenhar um quadrado vermelho dentro desse espaço. Como podemos representar essa figura, com exatidão, utilizando apenas informação ou apenas dados? Como podemos descrever as informações que esse quadrado tem?

vamos começar com o primeiro dado: a Cor. Sabemos que precisamos no mínimo de uma variável para armazenar a cor vermelha.

Vamos para a próxima etapa que é definir o posicionamento e o tamanho do quadrado. Não temos como escapar que em um espaço bi dimensional, onde temos que definir, onde o quadrado começa a ser desenhado, qual que é a coordenadaX e também qual que é a coordenadaY, e logo na sequencia, qual que é o tamanho, qual é a largura ou altura que o quadrado irá ocupar.

Então, nós temos um espaço virtual que contém 500px de altura e 500px de largura. iremos desenhar um quadrado vermelho que começa na posição inicial na coordenadaX 0 e a coordenadaY0 e vai ter 250px de largura e 250px de altura.

Agora temos os dados. Vamos codar?!

vamos criar o arquivo chamado ```game.js```.

Dentro desse arquivo, vamos adicionar as seguintes instruções:
```js
const screen = document.getElementById('screen');
const context = screen.getContext('2d');

const color = 'red';
const positionX = 0;
const positionY = 0;
const width = 250;
const height = 250;

context.fillStyle = color;
context.fillRect(positionX, positionY, width, height);
```
