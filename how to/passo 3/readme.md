# Game Multiplayer

## Passo 3
Nessa etapa, vamos começar a desenvolver a parte de estrutura de dados do jogo.

Podemos notar que os dados da nossa estrutura inicial está jogado e fora de contexto, apresentando como se fossem agumas variaveis soltas.

Nosso objetivo agora, é exibir um canvas com 10px de largura, 10px de altura, e contenha 3 quadrados de 1 px cada, sendo eles 2 pretos e 1 verde. Cada quadrado preto irá representar um jogador, enquanto o quadrado verde, representa a frutinha, como objetivo do jogo. É importante destacar que iremos trabalhar com pixel nesse momento. Sendo assim, os pixels não precisam de informação de largura ou altura, tendo apenas as posições de coordenada x e y.

Como podemos representar isso em uma estrutura de dados? Como podemos fazer organizar as variaveis para trabalhar com essas informações?

A resposta para isso é que temos diversas formas de fazer. O que é importante de destacar é que tudo vai depender das necessidades de negócio e das limitações técnicas que nós queremos estipular.

Como por exemplo, a necessidade de identificar todos os ID's de todos os objetos que estão na tela, como os Id's dos usuários ou das frutinhas. Ou até a quantidade de responsabilidade você quer dividir entre as camadas, como por exemplo, quem fica responsavel por atribuir o valor da cor do pixel. Podemos fazer a escoha das cores virem do back-end. Ou você pode passar isso para o client-side. Podemos sentar e discutir todas essas combinações e tudo mais ou podemos criar um modelo inicial e ir evoluindo aos poucos, conforme a necessidade do jogo.

vamos criar a nossa primeira estrutura de dados, encapsulando as informações do ID dos jogadores e da fruta, assim como sua posiçao no canvas:

```js
const game = {
  players: {
    'player1': {x: 1, y: 1},
    'player2': {x: 9, y: 9},
  },
  fruits: {
    'fruit1': {x: 3, y: 1},
  },
};
```

