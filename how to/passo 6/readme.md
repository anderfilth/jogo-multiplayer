# Game Multiplayer

## Passo 6
Antes de continuarmos, vamos fazer uma pequena refatoração.

Há uma função mais adequada para a limpeza do canvas chamada ```clearRect()```. Vamos atualizar o código?
```js
context.clearRect(0, 0, 10, 10);
...
```

Outra refatoração importante é adicionar ```const``` no ```for in```:
```js
for (const playerId in game.players) {
  ...
}
for (const fruitId in game.fruits) {
  ...
}
```

Agora, o nosso objetivo é capiturar o input do usuário, atualizar o estado do jogo e renderizar em tela. Vamos escutar os eventos que o navegador emite, toda vez que o teclado é usado. Vamos capiturar esses eventos de forma simples e direto. e depois vamos aos poucos melhorando o código.

Vamos ouvir os eventos de pressionar a tecla:
```js
document.addEventListener('keydown', handlerKeydown);

function handlerKeydown(event) {
  console.log(event.key);
}
```

Ao clicar-mos nas teclas, vemos que podemos visualizar o valores que digitamos. Vamos destacar o uso das teclas ```ArrowUp```, ```ArrowDown```, ```ArrowLeft``` e ```ArrowRight```, que são os valores representados pelas setas do teclado.

Então, podemos mapear os eventos da seguinte forma:
```js
function handlerKeydown(event) {
  const keyPressed = event.key;

  if (keyPressed === 'ArrowUp') {
    console.log('up');
    return;
  }
  if (keyPressed === 'ArrowDown') {
    console.log('down');
    return;
  }
  if (keyPressed === 'ArrowLeft') {
    console.log('left');
    return;
  }
  if (keyPressed === 'ArrowRight') {
    console.log('right');
    return;
  }
}
```

Se testarmos isso no dev tools, veremos que cada interação com as teclas, temos o log. Agora que mapeamos as teclas no evento, podemos então alterar a state da nossa estrutura de dados diretamente. Vamos simular que teremos um players já conectado: ```player1``` em uma variavel. Seguindo a lógica, toda vez que pressionarmos a tecla pra cima, o objeto no eixo Y terá o valor subtraído em 1, assim como que pra baixo irá somar 1. Para as setas direita e esquerda, vamos seguir da mesma forma, só que com o eixo X. A seta da direita irá soma 1 e da esquerda irá subtrair.

Vamos aplicar:
```js
// simulando o id do jogador
const currentPlayerId = 'player1';
...

function handlerKeydown(event) {
  const keyPressed = event.key;
  const player = game.players[currentPlayerId];

  if (keyPressed === 'ArrowUp') {
    player.y = player.y - 1;
    return;
  }
  if (keyPressed === 'ArrowDown') {
    player.y = player.y + 1;
    return;
  }
  if (keyPressed === 'ArrowLeft') {
    player.x = player.x - 1;
    return;
  }
  if (keyPressed === 'ArrowRight') {
    player.x = player.x + 1;
    return;
  }
}
```