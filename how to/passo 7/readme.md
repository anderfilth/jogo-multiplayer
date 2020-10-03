# Game Multiplayer

## Passo 7
Agora, vamos implementar nossa primeira regra de negócio regra de negocio.

O player não pode sair do canvas. Vamos desenvolver:

```js
function handlerKeydown(event) {
  const keyPressed = event.key;
  const player = game.players[currentPlayerId];

  if (keyPressed === 'ArrowUp' && player.y - 1 >= 0) {
    player.y = player.y - 1;
    return;
  }
  if (keyPressed === 'ArrowDown' && player.y + 1 < screen.height) {
    player.y = player.y + 1;
    return;
  }
  if (keyPressed === 'ArrowLeft' && player.x - 1 >= 0) {
    player.x = player.x - 1;
    return;
  }
  if (keyPressed === 'ArrowRight' && player.x + 1 < screen.width) {
    player.x = player.x + 1;
    return;
  }
}
```

Excelente! Totalmente funcional. Mas está correto da forma que esta?

Se visualizar-mos melhor, podemos dizer que esse trecho representa a camada de input e justamente nessa camada que adicionamos a regra de negócio. Podemos seguir em frente e continuar a adicionar as outras regras de negócio nesse espaço, mas será mais dicícil de dar manutenção e de escalar a aplicação.

Esse tipo de código é bom pra protótipo. Mas vamos seguir com o desenvolvimento, evitando um alto nível de acoplamento.