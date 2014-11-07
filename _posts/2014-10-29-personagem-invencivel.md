---
layout:     post
title:      Tornar uma personagem invencível
date:       2014-10-29 12:00:00
permalink:  tornar-uma-personagem-invencivel
categories: 
    - phaser
    - tutorial
comments:   true
---

Esse mês eu ajudei um usuário nos fóruns do HTML5 GameDev <a href="http://www.html5gamedevs.com/topic/9970-invincible-for-a-while-when-you-hit/#entry58847" target="_blank">em como trabalhar com a invencibilidade</a>. Eu achei que seria legal partilhar do assunto e da resposta aqui.

![Man of steel]({{site.baseurl}}/assets/phaser/superman.jpg)

###Inconquistável

Ser invencível significa que, num dado contexto, alguém ou algo não pode ser derrotado, destruído or morto. A primeira definição raramente acontece em jogos já que perder costuma ser parte integral da experiência.

Pense na estrela do Mario Kart, que faz com que seu corredor não possa ser ferido por cascos, bananas e afins. Enquanto você não pode ser *destruído*, você ainda pode ser *derrotado* por cair, perder tempo e chegar em último. O bônus é então temporário e não remove o desafio do jogo.

![borderlands 2 bee shield immunity]({{site.baseurl}}/assets/phaser/borderlands.jpg)

Em game design, os termos invulnerabilidade e invencibilidade são usados como sinônimos mas alguns jogos, tais como Final Fantasy ou Borderlands, permitem que você seja parcialmente invulnerábel (através de imunidade/resistência a certos tipos de dano).

###O que vem de baixo não me atinge!

Um uso comum de invencibilidade - especialmente em jogos "beat 'em up" - está em impedir dano extra, após um baque inicial. Pense jogos como BattleToads e Street Rage. Fazer isso com Phaser é bastante fácil mas a lógica básica é sempre a mesma.


{% highlight javascript %}
create: function() {
    player.invincible = false; //Primeiro criamos a propriedade
},

onHit: function(damage) { //Chamamos essa função quando o jogador é atingido
    if (!player.invincible) { //Se o jogador for invencível, nada acontece
      player.health -= damage;

      //Alteramos a propriedade
      player.invincible = true;
      
      //e daí adicionamos um temporizador (timer) para restaurar a vulnerabilidade apos 2 segundos
      game.time.events.add(2000, (function() {
           player.invincible = false;
      }), this); 
    }
}
{% endhighlight %}

###Quem é que manda aqui?

Alguns jogos implementam essa mecânica em vários pontos - um chefe com pontos fracos que só podem ser atingidos a cada tanto, pequenas criaturas invulneráveis após tomarem dano de fogo, o jogador sendo invulnerável após ser golpeado...

Nosso código de antes funciona mas ele pode ser bem melhor, mais flexível. Eu adaptei-o assim:

{% highlight javascript %}
create: function() {
    boss.invincible = false; //mesma ideia de antes
},

//Agora nós aceitamos três argumentos,
//Quem está colidindo, quanto de dano e quanto tempo dura a invulnerabilidade
onHit: function(entity, damage, invulTime) {
    if (!entity.invincible) {
      entity.health -= damage;

      //Agora usamos uma função
      this.toggleInvincible(entity); 
      
      //Um timer, tal como antes - dessa vez passamos um quarto argumento
      //Esse argumento é repassado pra função toggleInvincible
      game.time.events.add(invulTime, this.toggleInvincible, this, entity); 
    }
},

toggleInvincible: function(entity) {
    entity.invincible = !entity.invincible;
}
{% endhighlight %}

Já deu pra ver que fica bem mais fácil usar isso com várias entidades diferentes - além do código ficar mais limpo e claro!

###Eu disparei 5 timers ou 6?

Esse código é um exemplo do quão fácil é manejar temporizadores no Phaser, quão simples é a lógica (estamos apenas alterando um valor booleano depois de um tempo) e a flexibilidade fenomenal que herdamos disso. Esse mesmo estilo de código funciona bem com reciclagem de inimigos, quão rápido uma arma pode disparar ou bônus (buffs) temporários.

Você implementaria diferente? Conte nos comentários abaixo!