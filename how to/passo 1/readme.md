# Game Multiplayer

## Primeiros passos

Antes de iniciar, precisamos estabelecer a arquitertura inicial do nosso projeto.
O primeiro passo a ser executado será em criar os arquivos:
```
index.html
index.css
```

index.html:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Jogo Multiplayer</title>
  <link rel="stylesheet" href="index.css" />
</head>
<body>
  <canvas id="screen" width="500" height="500"></canvas>
</body>
</html>
```

index.css:
```css
#screen {
  border: 1px #CCC solid;
}
```

para testar o front, utilizar o comando:
```
npx http-server
```

