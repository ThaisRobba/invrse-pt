---
layout:     post
title:      Cola do Phaser
date:       2014-10-17 20:00:00
permalink:  cola-phaser
categories:
    - game framework
    - resource
comments:   true
---

<a href="http://phaser.io" target="_blank">Phaser</a> - o game framework para HTML5 [que eu analisei]({{site.baseurl}}/phaser-review) - é bem fácil de user. Mas com uma colinha, fica mais fácil ainda.

Cada parte da cola é associada diretamente com partes da documentação pra facilitar o aprendizado.

###Criando um jogo

<small>Referência: <a href="http://docs.phaser.io/Phaser.Game.html#Game" target="_blank">http://docs.phaser.io/Phaser.Game.html#Game</a></small>

{% highlight javascript %}
//Todos os parâmetros são opcionais (e existem outro além desses)
//Geralmente queremos pelo menos a altura e largura.
//Lembre-se que essa variável herdará uma série de propriedades e funções.
var game = new Phaser.Game(largura, altura, renderizador, "div_pai");
{% endhighlight %}

###Criando um estado de jogo (game state)

<small>Referência: <a href="http://docs.phaser.io/Phaser.State.html" target="_blank">http://docs.phaser.io/Phaser.State.html</a></small>

{% highlight javascript %}
playState = {
    init: function() {
    //Chamada assim que entramos nesse estado
    },

    preload: function() {
    //Recursos que devem ser carregados antes de chamar create()
    },

    create: function() {
    //Adicionar sprites, sons, etc...
    },

    update: function() {
    //Lógica do jogo, colisão, movimento, etc...
    }
};
{% endhighlight%}

###Gerenciando estados de jogo
<small>Referência: <a href="http://docs.phaser.io/Phaser.StateManager.html" target="_blank">http://docs.phaser.io/Phaser.StateManager.html</a></small>

{% highlight javascript %}
game.state.add('play', playState);
game.state.start('play');

//O StateManager também tem algumas funções de uso diverso, úteis também para debugging
console.log("Atualmente no estado de jogo: "+ game.state.getCurrentState());
{% endhighlight%}

###Ajustar o jogo a qualquer tamanho de tela

<small>Referência: <a href="http://docs.phaser.io/Phaser.ScaleManager.html" target="_blank">http://docs.phaser.io/Phaser.ScaleManager.html</a></small>


{% highlight javascript %}
this.scale.scaleMode = Phaser.ScaleManager.SHOW_ALL;
this.scale.pageAlignHorizontally = true;
this.scale.pageAlignVertically = true;
this.scale.setScreenSize(true);
{% endhighlight %}

###Usando globais

<small>Referência: <a href="http://www.html5gamedevs.com/topic/4247-where-to-put-global-var-in-the-basic-template/" target="_blank">http://www.html5gamedevs.com/topic/4247-where-to-put-global-var-in-the-basic-template/</a></small>

{% highlight javascript %}
//Declare-as fora que qualquer função
game.global = {
    mute: false,
    score: 0,
    bestScore: 100
};

//Porque aí podemos chamá-las em qualquer estado
game.global.mute = true;
game.global.bestScore = game.global.score;
{% endhighlight %}

###Usando armazenagem local

<small>Referência: <a href="http://www.w3schools.com/html/html5_webstorage.asp" target="_blank">http://www.w3schools.com/html/html5_webstorage.asp</a></small>

{% highlight javascript %}
//Só é possível guardar strings
localStorage.setItem('itemKey', 'myContent');

//Mas é possível guardar objetos inteiros fazendo isso:
localStorage.setItem('myObject', JSON.stringify(myObject));

//Depois que armazenar, é só pedir a string de volta
localStorage.getItem('itemKey');
{% endhighlight %}

###Carregado uma imagem/música/recurso

<small>Referência: <a href="http://docs.phaser.io/Phaser.Loader.html" target="_blank">http://docs.phaser.io/Phaser.Loader.html</a></small>

{% highlight javascript %}
function preload() {
    game.load.image('key', 'path/to/file.png');
    game.load.audio('key', ['path/to/file.mp3', 'path/to/file.ogg']);
    game.load.spritesheet('key', 'path/to/file', frameWidth, frameHeight);
}
{% endhighlight %}

###Definindo uma cor de fundo

<small>Referência: <a href="http://docs.phaser.io/Phaser.Stage.html" target="_blank">http://docs.phaser.io/Phaser.Stage.html</a></small>

{% highlight javascript %}
//Escolhi um azul acizentado
game.stage.backgroundColor = '#6d94b5';
{% endhighlight %}


###Gerando número aleatórios

<small>Referência: <a href="http://docs.phaser.io/Phaser.RandomDataGenerator.html" target="_blank">http://docs.phaser.io/Phaser.RandomDataGenerator.html</a></small>

{% highlight javascript %}
var num = game.rnd.integerInRange(120, 480);
var intNum = game.rnd.integer();
var fracNum = game.rnd.frac();
//Dentre outras!
{% endhighlight %}

###Adicionando objetos de jogo

<small>Referência: <a href="http://docs.phaser.io/Phaser.GameObjectFactory.html" target="_blank">http://docs.phaser.io/Phaser.GameObjectFactory.html</a></small>

{% highlight javascript %}
function create() {
    //Imagem, sprite, audio e afins são métodos do GameObjectFactory
    game.add.image(x, y, 'key');
    var player = game.add.sprite(x, y, 'key', frame, group);
}
{% endhighlight %}

###Reposicionar a referência de posicionamento dum objeto

<small>Referência: <a href="https://github.com/photonstorm/phaser/wiki/Graphics" target="_blank">https://github.com/photonstorm/phaser/wiki/Graphics</a></small>

{% highlight javascript %}
//Objetos tem uma propriedade de âncora
//Ela vai de 0 (topo esquerdo) até 1 (canto inferior direito)
//O padrão é 0,0 mas é fácil mudar
image.anchor.x = 0.2;
image.anchor.y = 1;

//This sets it in the middle
image.anchor.setTo(0.5,0.5);
{% endhighlight %}

###Escalonar um objeto

<small>Referência: <a href="https://github.com/photonstorm/phaser/wiki/Graphics" target="_blank">https://github.com/photonstorm/phaser/wiki/Graphics</a></small>

{% highlight javascript %}
//A escala dos objetos é 1, por padrão
//Valores negativos essencialmente espelham o objeto no eixo em questão
image.scale.x = -1;

//Isso dobra o tamanho do objeto
image.scale.setTo(2,2);
{% endhighlight %}

###Mostrar uma imagem

<small>Referência: <a href="http://docs.phaser.io/Phaser.Image.html" target="_blank">http://docs.phaser.io/Phaser.Image.html</a></small>

{% highlight javascript %}
function create() {
    game.add.image(x, y, 'key');
}
{% endhighlight %}

###Trabalhar com sprites

<small>Referência: <a href="http://docs.phaser.io/Phaser.Sprite.html" target="_blank">http://docs.phaser.io/Phaser.Sprite.html</a></small>

{% highlight javascript %}
function create() {
    //Atribua-o a uma variável para podermos chamá-lo mais tarde
    var sprite = game.add.sprite(x, y, 'key');

    //Agora podemos acessar seus métodos e propriedades
    sprite.x = 200;
    sprite.y = 300;
}
{% endhighlight %}

###Adicionando e tocando animações

<small>Referência: <a href="http://docs.phaser.io/Phaser.AnimationManager.html" target="_blank">http://docs.phaser.io/Phaser.AnimationManager.html</a></small>

{% highlight javascript %}
function create() {
    sprite.animations.add('name', [frames], frameRate, loop);
    sprite.animations.play('name', frameRate, loop, killOnComplete);
}
{% endhighlight %}

###Trabalhando com animações

<small>Referência: <a href="http://docs.phaser.io/Phaser.Animation.html" target="_blank">http://docs.phaser.io/Phaser.Animation.html</a></small>

{% highlight javascript %}
function create() {
    //Atribua-o a uma variável para podermos chamá-lo mais tarde
    var run = sprite.animations.add('name', [frames], frameRate, loop);

    //O segundo parâmentro é o contexto, geralmente 'this'
    run.onStart.add(listener, this);
}

function listener() {
    console.log("Você começou a correr!");
}
{% endhighlight %}


###Mostrar texto

<small>Referência: <a href="http://docs.phaser.io/Phaser.Text.html" target="_blank">http://docs.phaser.io/Phaser.Text.html</a></small>

{% highlight javascript %}
function create() {
    //Atribua-o a uma variável para podermos chamá-lo mais tarde
    var label = game.add.text(x, y, "texto", {style}, group);
    label.text = "Estou mudando o texto dentro da variável label!";
}
{% endhighlight %}

###Tweening

<small>Referência: <a href="http://docs.phaser.io/Phaser.Tween.html" target="_blank">http://docs.phaser.io/Phaser.Tween.html</a></small>

{% highlight javascript %}
//Adicionando um sprite exemplo mas dá para usar tweens com quase qualquer coisa
var player = game.add.sprite(100, 100, 'player');

game.add.tween(player)
    .to({x:500}, 400) //muda o player.x para 500 num período de 400ms
    .start();
{% endhighlight %}


###Tocar música

<small>Referência: <a href="http://docs.phaser.io/Phaser.Sound.html" target="_blank">http://docs.phaser.io/Phaser.Sound.html</a></small>

{% highlight javascript %}
function create() {
    //Atribua-o a uma variável para podermos chamá-lo mais tarde
    var music = game.add.audio('key', volume, loop);
    music.loop = true;
    music.play();
}
{% endhighlight %}


###Trabalhando com temporizadores (timers)

<small>Referência: <a href="http://docs.phaser.io/Phaser.Timer.html" target="_blank">http://docs.phaser.io/Phaser.Timer.html</a></small>

{% highlight javascript %}
//Três tipos de timers: em loop, evento único, repetir.
var looping = game.time.events.loop(delay, callback, context);
var once = game.time.events.add(delay, callback, context);
var repeat = game.time.events.repeat(delay, repeatCount, callback, context);

//Você também pode passar mais parâmetros no fim.
//Eles serão usados como argumentos na callback

game.time.events.pause(loopingTimer);
game.time.events.remove(once);
{% endhighlight %}

###Entrada (input)

<small>Referência: <a href="http://docs.phaser.io/Phaser.Input.html" target="_blank">http://docs.phaser.io/Phaser.Input.html</a></small>

{% highlight javascript %}
//Input pode vir do mouse, toque, teclado, joysticks, etc...
//Esse é o objeto pai, com as propriedades que determinam como funciona toda entrada.

//Configura em um segundo o tempo para um clique duplo
game.input.doubleTapRate = 1000;

//Aumenta o hitbox do toque
game.input.circle = 66;
{% endhighlight %}

###Entrada de mouse e toque

<small>Referência: <a href="http://docs.phaser.io/Phaser.Pointer.html" target="_blank">http://docs.phaser.io/Phaser.Pointer.html</a></small>

{% highlight javascript %}
if (game.input.mousePointer.isDown()) {
    console.log("Posição X do mouse quando você clicou: "+game.input.mousePointer.x);
}
{% endhighlight %}

###Entrada de teclado

<small>Referência: <a href="http://docs.phaser.io/Phaser.Keyboard.html" target="_blank">http://docs.phaser.io/Phaser.Keyboard.html</a></small>

<small>Código das teclas: <a href="http://docs.phaser.io/Keyboard.js.html#sunlight-1-line-557" target="_blank">http://docs.phaser.io/Keyboard.js.html#sunlight-1-line-557</a></small>

{% highlight javascript %}
if (game.input.keyboard.justReleased(Phaser.Keyboard.SPACEBAR, 10000)) {
    console.log("Barra de espaço foi pressionada nos últimos 10 segundos.");
}

//Assigning Up, Down, Left and Right to a variable
var arrow =  game.input.keyboard.createCursorKeys();
if (arrow.up.isDown) {
    console.log("Você está apertando a seta pra cima!");
}

//Isso impede que as setas rolem a página
game.input.keyboard.addKeyCapture(arrow);
{% endhighlight %}

###Trabalhando com grupos

<small>Referência: <a href="http://docs.phaser.io/Phaser.Group.html" target="_blank">http://docs.phaser.io/Phaser.Group.html</a></small>

{% highlight javascript %}
//Lembre-se de atribuir à uma varíavel para poder referenciar mais tarde
var enemies = game.add.group();

//Podemos adicionar um objeto que criamos previamente
enemies.add(button);

//Ou criar um objeto diretamente no grupo
enemies.create(x, y, 'enemy_sprite');

//Você pode usar setAll para modificar propriedades de todos os membros do grupo
enemies.setAll('x', 500);
{% endhighlight %}


###Adicionando física aos sprites
<small>Referência: <a href="http://docs.phaser.io/Phaser.Physics.Arcade.html" target="_blank">http://docs.phaser.io/Phaser.Physics.Arcade.html</a></small>

{% highlight javascript %}
function create() {
    //Primeiro iniciamos o sistema
    game.physics.startSystem(Phaser.Physics.ARCADE);

    //Depois criamos nossos objetos e ativamos as propriedades físicas neles
    sprite = game.add.sprite(x, y, 'key');
    game.physics.enable(sprite, Phaser.Physics.ARCADE);

    //Agora nosso sprite tem um objeto body como propriedade
    sprite.body.velocity.setTo(x, y);
    sprite.body.bounce.set(0.8);
}
{% endhighlight %}

###Manejando colisões

<small>Referência: <a href="http://docs.phaser.io/Phaser.Physics.Arcade.html#collide" target="_blank">http://docs.phaser.io/Phaser.Physics.Arcade.html#collide</a></small>

{% highlight javascript %}
function update() {
    //Você pode colidir um grupo com ele mesmo
    game.physics.arcade.collide(sprites);
    
    //Você pode chamar uma função quando ocorre uma colisão
    game.physics.arcade.collide(sprites, monsters, callback);
    
    //Você pode checar parâmetros adicionar com uma processCallback
    //Se essa processCallback for falsa, a colisão não ocorre
    game.physics.arcade.collide(sprites, monsters, null, processCallback);
    
    //As seguintes colisões são possíveis:
    //Sprite vs Sprite ou
    //Sprite vs Grupo ou
    //Grupo  vs Grupo ou
    //Sprite vs Tilemap Layer ou
    //Grupo  vs Tilemap Layer
}
{% endhighlight %}

###Câmera

<small>Referência: <a href="http://docs.phaser.io/Phaser.Camera.html" target="_blank">http://docs.phaser.io/Phaser.Camera.html</a></small>

{% highlight javascript %}
//Vamos seguir um míssel pela tela
game.camera.follow(missile);

//Quando ele explodir, essa função permite zerar a câmera
game.camera.reset();

//Aconteceu algo legal, vamos mover a câmera para lá!
game.camera.x = 500;
{% endhighlight %}

###Partículas

<small>Referência: <a href="http://docs.phaser.io/Phaser.Particles.Arcade.Emitter.html" target="_blank">http://docs.phaser.io/Phaser.Particles.Arcade.Emitter.html</a></small>

{% highlight javascript %}
emitter = game.add.emitter(x, y, maxParticles);
emitter.makeParticles('image');
emitter.setAlpha(min, max, rate, easing, yoyo);

//Para usar gravidades com o emissor, inicie o sistema de física
game.physics.startSystem(Phaser.Physics.ARCADE);
emitter.gravity = 200;
emitter.start();
{% endhighlight %}

###Contribua!

Eu gostaria de continuar revisitando essa cola de tempos em tempos - tanto para garantir sua relevância como para ampliá-la e refiná-la.

Eu estou aberto a sugestões, melhorias e correções - ou via <a href="https://github.com/OttoRobba/invrse-pt/blob/gh-pages/_posts/2014-10-17-phaser-cheatsheet.md" target="_blank">gitHub</a> ou nos comentários abaixo.

Gostaria também de saber as opiniões, então aproveite e deixa a sua abaixo!
