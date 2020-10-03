# Game Multiplayer

## Passo 4
Nessa etapa, vamos alterar a renderização do canvas para 10px de largura e 10px de altura e adicionar os jogadores e as frutas definido pela estrutura de dados.

Altere o canvas para 10px de largura e 10px de altura:
```html
<canvas id="screen" width="10" height="10"></canvas>
```

vamos remover esse trecho:
```js
const color = 'red';
const positionX = 0;
const positionY = 0;
const width = 250;
const height = 250;

context.fillStyle = color;
context.fillRect(positionX, positionY, width, height);
```
E vamos redenrizar dinamicamente, conforme a nossa estrutura de dados.
```js
function renderScreen() {
  for (playerId in game.players) {
    const player = game.players[playerId];
    context.fillStyle = 'black';
    context.fillRect(player.x, player.y, 1, 1);
  }

  for (fruitId in game.fruits) {
    const fruit = game.fruits[fruitId];
    context.fillStyle = 'green';
    context.fillRect(fruit.x, fruit.y, 1, 1);
  }
}

renderScreen();
```

Se atualizar-mos a página, veremos que o canvas ficou muito pequeno. Vamos atualizar o CSS, para que melhore a visualização:
```css
#screen {
  border: 10px #CCC solid;
  width: 400px;
  height: 400px;
  image-rendering: pixelated;
  image-rendering: crisp-edges;
  image-rendering: -moz-crisp-edges;
}
```


