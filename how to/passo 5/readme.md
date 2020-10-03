# Game Multiplayer

## Passo 5
Nessa etapa, vamos fazer alguns testes no dev tools e alterando as estruturas de dados.

Vamos tentar mover nossa fruta para a posição ```x = 4``` e ```y = 1```:
```js
game.fruits['fruit1'] = {x: 4, y: 1};
```

Opa! Não redenrizou...

Para resolver esse problema de renderização, uma das estratégias que podemos usar, é chamar a nossa função ```renderScreen()``` dentro dela de forma recursiva. Com isso, toda vez que a nossa estrutura de dados sofrer uma atualização, a camada de apresentação irá atualizar as posições de cada elemento com a última versão desses dados.

Utilizando essa estratégia, o browser fornece uma função especial para chamar esse tipo de situação no momento certo, otimizado para executar apenas quando a nossa estrutura de dados sofrer atualização. Essa função se chama ```requestAnimationFrame()``` e ela é ótima para renderização do tipo: se a aba do navegador está inativa.

Vamos adicionar o ```requestAnimationFrame()``` no nosso código:
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

  requestAnimationFrame(renderScreen);
}
```

Vamos tentar novamente mover nossa fruta para a posição ```x = 4``` e ```y = 1```:
```js
game.fruits['fruit1'] = {x: 4, y: 1};
```

O que houve? duplicou a fruta?

Esse é um comportamento comum no canvas e em qualquer função de renderização. Nó utilizamos apenas a função para adicionar o elemento dentro do canvas e em nenhum momento executamos a função de deletar os elementos passados. 

Para não transformar essa implementação num inferno, há uma técnica no desevolvimento dos jogos, onde limpamos a tela, onde, antes de desehar a próxima animação, remove a tela inteira e comaça tudo do zero. Fazer isso, é bem simples:
```js
function renderScreen() {

  // Adiciona 
  context.fillStyle = 'white';
  context.fillRect(0, 0, 10, 10);

  ...
```

E agora? Mais alguma surpresa? Vamos tentar novamente mover nossa fruta para a posição ```x = 4``` e ```y = 1```:
```js
game.fruits['fruit1'] = {x: 4, y: 1};
```

Agora sim!

Agora imagine esses dados vindo do back-end?