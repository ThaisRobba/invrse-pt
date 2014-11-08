---
layout:     post
title:      Phaser - Game Framework HTML5 
date:       2014-10-10 12:00:00
permalink:  phaser-review
categories: 
    - review
    - game framework
comments:   true
---

Vamos ser honestos: game design é *muito* divertido mas é um trabalho difícil e complexo.

Eu sempre favoreço ferramentas que tornam o processo de desenvolvimento mais fácil e mais rápido sem comprometer a qualidade - <a href="http://phaser.io" target="_blank">Phaser</a> é uma dessas ferramentas.

É um game framework (estrutura base de jogo, em tradução livre) para jogos em HTML5. É todo feito em JavaScript por <a href="http://www.photonstorm.com/" target="_blank">gente muito mais inteligente do que eu</a> (e que estão fazendo isso há bastante tempo).

![Phaser logo]({{site.baseurl}}/assets/phaser_logo.jpg)

###Veloz & multi-plataforma

Uma das coisas mais legais de game frameworks HTML5 é que, óbvio, eles rodam em browsers. Phaser faz um trabalho fantástico de integração com os browsers, rodando perfeitamente até mesmo nos navegadores de mobiles (que são especialmente infernais).

Essa performance é obtida graças ao contínuo trabalho no framework e ao fato do mesmo ser construído em cima do PixiJS - sem dúvida o melhor renderizador 2D pra webGL no momento. Basicamente, é tudo bem rápido.

Usando a ferramenta benchmark (análise de performance) do PixiJS, <a href="http://www.goodboydigital.com/pixijs/bunnymark/" target="_blank">BunnyMark</a>, eu consigo por volta de 100,000 coelhos rodando lisinho em 30 frames por segundo (Firefox, Ubuntu, using a GTX650 Ti). Nem sei o que fazer com tantos coelhos.

![bunnies everywhere]({{site.baseurl}}/assets/phaser_bunnymark.png)

Até nos aparelhos móveis roda tudo direitinho. Meu Galaxy S2 consegue uns 512 coelhos em 30fps no Google Chrome - ele não suporta WebGL então acaba rodando em canvas (que é mais lento).

###Características

Além de ser veloz e furioso, Phaser tem várias coisas úteis. Seguem abaixo algumas dignas de atenção:

- #####Flexivél
    
    É "apenas JavaScript" e é open source.
    
    O código fonte é fácil de ler e entender e <a href="https://github.com/photonstorm/phaser
" target="_blank">está disponível no GitHub</a> - alterações, patches e afins são bem vindos.

    Você pode também extender o Phaser com plugins!
    
- #####Suporte a Tilemaps e Tiled

    <a href="http://www.mapeditor.org/" target="_blank">Tiled</a> é uma ferramenta open-soruce incrível para a criação de mapas 2D. Integrar com Phaser é muito fácil.

    ![tiled integration]({{site.baseurl}}/assets/phaser_tiled.gif)

    Eu e meu time o usamos na SPJam 2014. Todos se adaptaram rapidamente à ferramenta, me deixando livre para focar noutras áreas do jogo enquanto eles faziam os níveis.

- #####Física
    
    Phaser vem com 3 escolhas diferentes para sistemas de física, desde o mais básico e mais veloz 'Arcade' até o mais completo e avançado 'P2'.
    
    As funções da biblioteca de física são extremamente úteis e simplificam (e muito) o trabalho necessário nos jogos.
    
    A biblioteca 'Arcade' tem, por exemplo, uma função que checa se o sprite está tocando o chão, retornando um valor booleano, tornando muito fácil evitar pulos infinitos em jogos plataforma.
    
- #####Camera, Sprites, Animação & Partículas

    São sistemas por si só bastante poderosos e capazes que te poupam muitas horas que seriam investidas reinventando a roda.
    
    Phaser aproveita por completo a natureza prototípica orientada a objetos do JavaScript. Sprites, por exemplor, herdam uma série de propriedades que torna muito mais fácil interagir com eles.

    {% highlight javascript %}
//exemplo simples mostrando as propriedades e métodos padrão

if (sprite.alive && sprite.overlap(spikes)) {
    sprite.damage(1);
}
    {% endhighlight %}


###Documentação

Eu não sou um expert de JavaScript - na melhor das hipóteses, sou proficiente. A <a href="http://docs.phaser.io" target="_blank">documentação do Phaser</a> sempre me dá uma certa sensação de ser a Alice descendo a toca do coelho.

"Tá, 'Game' é o objeto pai, 'add' é uma propriedade dele que referencia o 'GameObjectFactory'. Este último tem um método chamado 'image', então se eu quiser adicionar uma imagem preciso escrever..."

        game.add.image(x, y, key, frame, group);

Isso, para mim, é contra-intuitivo. Meu primeiro instinto seria ir direto na classe 'Image' na documentação mas isso não necessariamente ajudaria.

Depois que a ficha caiu, eu consegui compreender todos os elogios que a documentação recebe.

###Comunidade

Ativa e em crescimento, a comunidade do Phaser é um bom sinal do quão saudável o framework está e quão longe ele pode ir.

Os <a href="http://www.html5gamedevs.com/forum/14-phaser/" target="_blank">fóruns</a> tem atividade constante, com os usuários contruindo com dúvidas, respostas, plugins e afins.

Richard, o criador do Phaser, costuma inclusive responder nos tópicos, o que é por si só um benefício extra.

![community]({{site.baseurl}}/assets/phaser_community.png)

###Recursos extras

O framework conta também com um diretório repleto de <a href="http://examples.phaser.io" target="_blank">exemplos</a> - você consegue fazer vários jogos simples lendo e aprendendo do código ali disponível.

Há também um tópico no fórum com <a href="http://www.html5gamedevs.com/topic/4320-list-of-phaser-tutorials/page-1" target="_blank">tutoriais de Phaser</a> e uma <a href="https://github.com/photonstorm/phaser/wiki" target="_blank">seção wiki no Gihub</a>.

###Conclusão

Phaser é um framework com grande ênfase em velocidade - tanto em termos de performance como de desenvolvimento. Eu sinto que consigo ser bastante produtivo e que estou evoluindo rapidamente.

Conforme a adoção amplia e graças ao suporte existente, eu acredito que ele vai durar e crescer ao longo dos anos. Eu fico tranquilo que ele não vai desaparecer do dia pra noite.

Tem a minha recomendação!