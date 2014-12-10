---
layout:     post
title:      Criar uma tela de menu com Phaser e Browserify
date:       2014-12-10 20:00:00
permalink:  create-menu-screen-in-phaser
categories: 
    - tutorial
    - programming
    - phaser
comments:   true
image: phaser_menu
---

Eu estou me preparando pra Global Game Jam que vai acontecer em Janeiro - parte disso inclui rever meu modelo base de jogo. [Tem coisas pré-prontas como tela de loading com Browserify e afins](http://invrse.com.br/construir-phaser-com-browserify).

![loading screen]({{site.baseurl}}/assets/loading_screen.png)

Eu achei que seria uma boa adicionar uma tela de menu, só pra não ter que gastar tempo depois criando uma durante a jam. Você pode [baixar as imagens que usaremos nesse tutorial aqui].({{site.baseurl}}/assets/create_menu_phaser_assets.zip).

###A premissa

O menu que faremos deverá aceitar tanto teclado quanto mouse/toque, como fosse um menu de Final Fantasy ou Zelda. Algo como isso:

![loading screen]({{site.baseurl}}/assets/create_menu_ff.png)

Vamos precisar fazer algumas coisas então:

- Mostrar um ponteiro para informar ao jogador qual item está selecionado.
- Guardar a posição do ponteiro para saber a função de qual botão chamar.
- Possibilitar mouse/toque para interagir com o menu.
- Mostrar o logo do jogo

###Mãos à obra!

Eu vou usar como base o meu [template com Browserify](http://invrse.co/build-phaser-with-browserify) - você pode acompanhar o tutorial sem ele mas eu recomendo altamente seu uso por simplificar a estruturação do jogo.

Antes de mais nada, nós carregamos nossas imagens e afins. Eu costumo usar um estado específico de jogo para carregar tudo.

{% highlight javascript %}
//load.js
module.exports = {
    preload: function() {
        game.load.image('menu_title', 'assets/menu_game_title.png');
        game.load.image('menu_arrow', 'assets/menu_arrow.png');
        game.load.image('menu_button1', 'assets/menu_button.png');
        game.load.image('menu_button2', 'assets/menu_button2.png');
        game.load.image('menu_button3', 'assets/menu_button3.png');
    }
};

{% endhighlight %}

O segundo passo é criar um estado para o menu.

{%highlight javascript%}
//menu.js
module.exports = {
    create: function() {
        //Adicione a imagem de título do jogo pra ver se está tudo ok
        this.gameTitle = game.add.image(
            game.world.centerX, game.world.centerY - 150, 'menu_title');
        this.gameTitle.anchor.setTo(0.5, 0.5);
    },
    
    update: function() {}
};
{%endhighlight%}

Simples né?

###Mostrando itens do menu

A maneira mais fácil de mostrar itens no menu vai ser com o botões do Phaser (Phaser.Buttons). Já que estamos usando Browserify, vamos tomar vantagem de sua modularidade.

Podemos fazer assim:

{% highlight javascript %}
//menu_buttons.js
module.exports = {
    draw: function () {
        this.button1 =  game.add.button(game.world.centerX,
        game.world.centerY - 50, 'menu_button1', this.playState);
        this.button1.anchor.setTo(0.5, 0.5);

        this.button2 = game.add.button(game.world.centerX,
        game.world.centerY + 50, 'menu_button2', this.playState);
        this.button2.anchor.setTo(0.5, 0.5);

        this.button3 = game.add.button(game.world.centerX,
        game.world.centerY + 150, 'menu_button3', this.playState);
        this.button3.anchor.setTo(0.5, 0.5);
    },

    playState: function () {
        game.state.start('play');
    }
};
{% endhighlight %}

So que isso num vai funcionar tão bem com o ponteiro e o código em si é bem feio. Melhoramos um pouco para isso:

{% highlight javascript %}
//menu_buttons.js
module.exports = {
    //Guardamos o quanto que cada botão está do centro da tela
    pos: [-50, 50, 150],
    //Guardamos quais chamadas cada botão tem
    callbacks: ['playState', 'playState', 'playState'],
    draw: function () {
        //Criamos nossos botões usando uma função construtora, yay!
        this.button1 = this.addButton(1, this.playState);
        this.button1.anchor.setTo(0.5, 0.5);

        this.button2 = this.addButton(2, this.playState);
        this.button2.anchor.setTo(0.5, 0.5);

        this.button3 = this.addButton(3, this.playState);
        this.button3.anchor.setTo(0.5, 0.5);
    },

    addButton: function (button, func) {
        return game.add.button(game.world.centerX,
        game.world.centerY + this.pos[button - 1],
        'menu_button' + button, func);
    },

    playState: function () {
        game.state.start('play');
    }
};
{% endhighlight %}

Bacana! Dá para melhorar mais mas por enquanto basta. Vamos retornar ao nosso menu.js, no qual fazemos isso:

{% highlight javascript %}
//menu.js
var buttons = require('../entities/menu_buttons.js');

module.exports = {
    create: function() {
    buttons.draw();
    },
    
    update: function() {}
};
{% endhighlight %}

Bam! Agora temos nossos botões e eles já funcionam com mouse/toque.

###Adicionando o ponteiro

Criamos um novo arquivo para desenhar, mover e controlar o ponteiro - eu nomeei o meu de arrow já que a imagem usada é de uma setinha. Esse vai ser um teco mais complexo então leia os comentários com cuidado!

{% highlight javascript %}
module.exports = {
    draw: function () {
        //A posição inicial é no primeiro botão
        this.arrow = game.add.image(game.world.centerX - 100,
        game.world.centerY - 50, 'menu_arrow');
        this.arrow.anchor.setTo(0.5, 0.5);
        
        //A seta vai levar 200ms para descer/subir pelo menu
        this.arrow.moveDelay = 200;
        
        //Controlamos se a seta deve ou não mexer
        this.arrow.canMove = true;
        
        //Guardamos a informação de em qual botão a seta está
        this.arrow.currentButton = 1;
        
        //Adicionamos um tween horizontal pra seta ficar legal
        game.add.tween(this.arrow)
            .to({
                x: this.arrow.x - 10
            }, 700, Phaser.Easing.Quadratic.Out)
            .to({
                x: this.arrow.x
            }, 400, Phaser.Easing.Quadratic.In)
            .loop()
            .start();
    },

    //Here we will set the rules for how it moves
    //We need to pass the variable holding the cursor keys
    //and the object that holds the buttons.
    move: function (cursors, buttons) {
        if (cursors.down.isDown && this.arrow.canMove) {
            //This stops the arrow from traveling way too fast
            this.arrow.canMove = false;
            
            //Which is reset to true after a 255ms delay
            this.allowMovement();
            
            if (this.arrow.currentButton === 1) {
                //I made a custom tween function for this
                this.tween(buttons, 2);
            } else if (this.arrow.currentButton === 2) {
                this.tween(buttons, 3);
            } else {
                this.tween(buttons, 1);
            }
        }

        if (cursors.up.isDown && this.arrow.canMove) {
            this.arrow.canMove = false;
            this.allowMovement();
            if (this.arrow.currentButton === 1) {
                this.tween(buttons, 3);
            } else if (this.arrow.currentButton === 2) {
                this.tween(buttons, 1);
            } else {
                this.tween(buttons, 2);
            }
        }

        if (game.input.keyboard.isDown(Phaser.Keyboard.ENTER)) {
            //This will activate the button that the pointer is at
            this.activateButton(buttons, this.arrow.currentButton);
        }
    },

    tween: function (buttons, buttonNum) {
        game.add.tween(this.arrow)
            .to({
                y: game.world.centerY + buttons.pos[buttonNum - 1]
            }, this.arrow.moveDelay, Phaser.Easing.Quadratic.In)
            .start();
        this.arrow.currentButton = buttonNum;
    },

    allowMovement: function () {
        game.time.events.add(255, (function () {
            this.arrow.canMove = true;
        }), this);
    },

    activateButton: function (buttons, currentButton) {
        buttons[buttons.callbacks[currentButton - 1]]();
    }
};
{% endhighlight %}

###Adding pointer to menu

The first thing we do is requiring the arrow file.

{% highlight javascript %}
//menu.js
var arrow = require('../entities/menu_arrow.js');
{% endhighlight %}

Then we can call the arrow.draw() and arrow.move() in create and update, respectively.

{% highlight javascript %}
//menu.js
module.exports = {
    create: function() {
    buttons.draw();
    arrow.draw();
    },
    
    update: function() {
    arrow.move();
    }
};
{% endhighlight %}

This will break though, because we need to pass the cursor keys and the buttons object for the arrow.move function. We can add keyboard interation by adding the following line to menu.js' create function:

{% highlight javascript %}
this.cursors = game.input.keyboard.createCursorKeys();
{% endhighlight %}

Our final menu.js file will look like this:
{% highlight javascript %}
var buttons = require('../entities/menu_buttons.js'),
    arrow = require('../entities/menu_arrow.js');

module.exports = {
    create: function () {
        this.cursors = game.input.keyboard.createCursorKeys();
        this.gameTitle = game.add.image(game.world.centerX,
        game.world.centerY - 200, 'menu_title');
        this.gameTitle.anchor.setTo(0.5, 0.5);
        buttons.draw();
        arrow.draw(buttons, 1);
    },

    update: function () {
        arrow.move(this.cursors, buttons);
    }
};
{% endhighlight %}

###End Result

<iframe src="{{site.baseurl}}/examples/phaser-menu/index.html" width="100%" height="480px" seamless frameborder="0"></iframe>

###Download template

You can download the template (including instructions for use with Browserify, loading screen and menu) at my <a href="https://github.com/OttoRobba/browserify-phaser/tree/menu" target="_blank">github repo</a>!

I hope this is helpful, let me know what you think. :)