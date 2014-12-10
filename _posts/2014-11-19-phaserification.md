---
layout:     post
title:      Construindo jogos de Phaser com Browserify
date:       2014-11-19 20:00:00
permalink:  construir-phaser-com-browserify
categories: 
    - tutorial
    - programming
    - resource
comments:   true
image: phaserification
---

Fazer projetos maiores usando JavaScript pode ser um problemão - não existe interface nativa (por enquanto) para importar as dependências de um arquivo e o método atual de resolução involve adicionar e mexer manualmente num arquivo html. Além disso, sendo JS uma língua 'script', não há nenhum modo nativo de concatenar vários arquivos num só (e na ordem correta).

Como resolvemos isso tudo então? Com NodeJS!

###Conheça o Browserify

Browserify é um dos muitos carregadores disponíveis para JavaScript. Ele te permite criar arquivos como módulos:

{%highlight javascript%}
//square.js
module.exports = function(num) {
    return num*num;
};
{%endhighlight%}

Que você pode então importar em outros arquivos:

{%highlight javascript%}
//main.js
var square = require('./square.js');

console.log(square(4)); //resultado apresentado será 16
{%endhighlight%}

Bem legal né?
Você também pode exportar vários módulos a partir de um arquivo único, assim óh:

{%highlight javascript%}
//math.js
exports.square = function(num) {
    return num*num;
};

exports.double = function(num) {
    return num*2;
};
{%endhighlight%}

Que nós podemos requerer assim:
{%highlight javascript%}
//main.js
var square = require('./math.js').square;
var double = require('./math.js').double;

console.log(square(4)); //resultado apresentado será 16
console.log(double(4)); //resultado apresentado será 8
{%endhighlight%}

###Como que isso funciona?

A ideia básica é que cada arquivo é envolto numa função e então concatenados num arquivo único que é chamado pelo script do Browserify, resolvendo as dependências e chamando os módulos em ordem.

O primeiro passo é instalar e pra isso você vai precisar do npm - ele vem com o NodeJS então <a href="http://nodejs.org/download/" target="_blank">instale-o primeiro!</a> Depois é só abrir a linha de comando e digitar:

    npm install -g browserify beefy

Usuários Mac e Linux podem precisar prefixar um comando sudo, dependendo das permissões. Depois que a instalação terminar, você pode fazer isso na linha de comando:

    browserify path/to/main.js > path/to/output.js

Bem legal. Mas e pra usar com Phaser?

###Phaserificação

Eu recomendo estruturar a pasta do seu jogo assim:

    Game Name
        ├── index.html  
        └── src
            ├── images
            ├── sounds
            ├── libs
            |   └── phaser.js
            ├── states
            |   ├── boot.js
            |   ├── menu.js
            |   ├── play.js
            |   └── load.js
            └── game.js

Dentro do game.js você vai criar uma instância do Phaser e requerer todos os estados de jogo, assim:

{%highlight javascript%}
//game.js

//Usamos window.game ao invés de var game porque queremos ele acessível por todos os módulos
window.game = new Phaser.Game(800, 600, Phaser.AUTO);

game.state.add('play', require('./states/play.js'));
game.state.add('load', require('./states/load.js'));
game.state.add('menu', require('./states/menu.js'));
game.state.add('boot', require('./states/boot.js'));
game.state.start('boot');
{%endhighlight%}

Dentro do index.html você vai adicionar dois scripts: phaser.js e o bundle.js que é gerado pelo Browserify.

{%highlight html%}
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8" content="content">
  <title>Phaser Game</title>
</head>

<body>
  <script src="./src/libs/phaser.js" charset="utf-8"></script>
  <script src="bundle.js"></script>
</body>

</html>
{%endhighlight%}

É assim que um arquivo de estado de jogo vai ser:

{%highlight javascript%}
//states/play.js

module.exports = {
    create: function(){
    //Igual a função create normalmente usada
    },
    update: function(){
    //Lógica de jogo vem aqui
    },
};
{%endhighlight%}

E é só isso!

###Moooito legal

Bacana mas e se quisermos automatizar um pouco mais? Pra isso podemos usar o Beefy. É como um micro servidor que conversa com o Browserify e permite coisas legais como observar seus arquivos por mudanças e atualizar tudo automaticanete. Se você não o instalou ainda:

    npm install -g beefy

Lembrando que usuários Mac & Linux podem precisar usar sudo.

Agora é só executar o seguinte comando na raíz do projeto:
    
    beefy src/game.js:bundle.js --live --open --bug=true
    
Uma janela do seu browser favorito vai abrir com seu jogo rodando. Sucesso!

###Indo além

Eu recomendo muito ler mais sobre o <a href="https://github.com/chrisdickinson/beefy" target="_blank">Beefy</a> e sobre o <a href="https://github.com/substack/browserify-handbook" target="_blank">Browserify</a> para que você possa refinar as coisas ao seu modo.

Pra facilitar a vida, eu fiz <a href="https://github.com/OttoRobba/browserify-phaser" target="_blank">um template simples</a> que você pode <a href="https://github.com/OttoRobba/browserify-phaser/archive/master.zip" target="_blank">puxar aqui</a>. É basicamente um projeto vazio (e você precisa instalar Beefy e Browserify) com o esqueleto do jogo - só pra facilitar o início do projeto! Pode modificá-lo a vontade e se puder mostrar as mudanças que tu fizer, melhor ainda!
