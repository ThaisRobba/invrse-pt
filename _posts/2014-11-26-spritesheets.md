---
layout:     post
title:      Introdução a sprite sheets
date:       2014-11-26 20:00:00
permalink:  intro-a-sprite-sheets
categories:
- tutorial
- art
comments:   true
image: spritesheets
---

Adicionar uma imagem num jogo é, geralmente, bem fácil - as ferramentas e as engines provêm soluções simples e nós já conhecemos bem o que são imagens.

Uma coisa que eu percebi, no entanto, é que poucas pessoas sabiam como fazer com animações complexas. Criam-se várias imagens diferentes? Faz-se um gif? O que fazer?

###Imagens sobrepostas

A técnica mais básica para animação é sobrepor um quadro com outro de maneira rápida - nosso cérebro mescla as imagens e temos a ilusão de movimento.

Um exemplo clássico disso são os zootrópicos - eles giram uma tira de papel num eixo e se olharmos através das frestas dele, o que percebemos é uma animação.

<iframe width="100%" height="320" src="//www.youtube.com/embed/5_8fX-N3Ji4" frameborder="0" allowfullscreen mute="true"></iframe>

###Movendo sprites

Para essa explicação eu vou usar uma personagem que eu fiz chamada Blue (uau quanta criatividade!).

![Animated Blue]({{site.baseurl}}/assets/Blue.gif)

Cada quadro da animação é desenhado separadamente para depois serem agrupados numa grade. Cada célula é retangular e tem a mesma largura e a mesma altura, o que nos permite dizer ao nosso software as coordenadas X e Y de cada quadro no desenho.

![Blue sprite sheet]({{site.baseurl}}/assets/blue_grid.png)

X aumenta para a direita, Y aumenta para baixo. Na nossa sprite sheet acima:

- Quadro 1 começa em (0,0) e vai até (256,256)
- Quadro 2 começa em (256,0) e vai até (512,256)
- Quadro 3 começa em (512,0) e vai até (768, 256)

###Dicas para criar sua própria sprite sheet

As grades podem ser tão altas e largas quanto necessário mas tenha sempre em mente os limites da memória da placa de vídeo. Uma boa ideia é usar medidas que são potências de 2 para evitar bugs com alguns hardwares.

Você não precisa decorar as coordenadas dos quadros, - a maior parte dos frameworks faz isso por você - basta saber a altura e a largura da sprite sheet e da célula.

Em termos de ferramentas, existem vários jeitos de se criar sprite sheets. Existem scripts para <a href="http://alessandroituarte.com/blag/2012/07/03/470" target="_blank">Photoshop</a> e <a href="http://registry.gimp.org/node/27943" target="_blank">Gimp</a>. Tem também editores que exportam de maneira nativa, tal como o fantástico <a href="http://www.piskelapp.com/" target="_blank">Piskel</a> ou, se você preferir, dá para fazer manualmente ou implementar outra solução.

O princípio básico é sempre o mesmo: faça os quadros individuais e depois coloque-os numa grade.

###Nota de fechamento

É completamente viável utilizar uma grade disforme de imagens - a automação fica um tanto mais complexa porque é necessário saber as coordenadas individuais. Isso fica pra um tutorial futuro.

Espero que isso tenha sido útil, me fale nos comentários o que você achou e, se tiver gostado, compartilhe!
