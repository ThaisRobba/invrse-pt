---
layout:     post
title:      Trabalhando de maneira presente
date:       2014-12-02 20:00:00
permalink:  trabalhando-de-maneira-presente
categories:
    - devlife
comments:   true
image: in_the_moment
---

Desenvolvemos práticas de trabalho que seguimos religiosamente, desenvolvemos listas de tarefas intermináveis. No nosso zelo excessivo acabamos por nos sabotar. Hoje estou aqui pra te ajudar a desfazer esse nó.

![timing is everything]({{site.baseurl}}/assets/in_the_moment.png)

###Faça somente conforme necessário

Na minha primeira tentativa de fazer uma engine, de componentes e entidades, eu criei um bando de funções para checar todo tipo de coisa. Isso aumentou (e muito) a complexidade sem oferecer nenhum benefício real - eu não tinha, até então, precisado daquelas funções mas ainda assim, lá estavam elas, entupindo meu código, ofuscando minhas intenções. Tudo porque eu pensei "Posso precisar delas um dia!".

###Resolva os problemas mais fáceis antes

Você pode escolher gastar incontáveis horas otimizando seu código para conseguir carregar o jogo um pouco mais rápido - ou você pode simplesmente comprimir as texturas e afins do jogo. No [Lava-Run]({{site.baseurl}}/jogos/lava-run) eu reduci o tamanho do jogo em dois terços só minificando o JavaScript e comprimindo as imagens.

###Conheça as regras - quebre-as conscientemente

Uma das principais regras de programação funcional e código limpo é que uma função deve fazer apenas uma coisa. Isso significa que funções maiores deveriam ser quebradas em funções menores.

É uma prática fantástica mas, quando você usa algo uma vez apenas, pode ter resultado negativo, reduzindo performance e diminuindo a clareza. Julgue caso a caso.
{%highlight javascript%}
var convidados = {
  confirmados: [],
  recusados: [],
  total: []
};

//A função abaixo faz duas coisas e isso é ok
function logGuest(name, isAttending) {
  if (isAttending){
    convidados.confirmados.push(name);
  } else {
    convidados.recusados.push(name);
  }
  
  convidados.total.push(name);
}
{%endhighlight%}


###Quando em dúvida, opte pelo mais simples

Dá para argumentar que talvez você queria que cada convidado seja um objeto para armazenar mais informação. Eles estão trazendo comida? Bebida? Um presente? Uma máquina de Karaôke?

Sim, faça isso - se você precisar dessa informação. Aqui nós não precisamos e por isso, focando em clareza, mantivemos essa estrutura enxuta. Como um bônus, estamos lidando apenas com arrays então a performance é melhor.

###Adapte-se à mudança, deixe amanhã ser amanhã

Como independentes nós não temos gerentes especializados controlando a produção. É muito fácil errarmos (pra cima ou pra baixo) nos prazos, não apenas pelo tempo que as coisas levam mas pelas ramificações que elas apresentam - talvez o gerador de partículas novo quebre coisas inesperadas e agora você tem que gastar esse tempo caçandos os bugs.

Tente pensar em listas de tarefas como um meio para não se perder. Mantenha-as bem curtas, elas nunca devem servir para guardar *tudo* o que você precisa fazer.

Tenha em mente que quanto menor o espaço de tempo que elas cobrem, mais fáceis elas se tornam para completar. Se suas listas estiverem enormes você logo vai perceber como as tarefas parecem brigar entre si e fica difícil escolher o próximo alvo.

Mantenha tudo o mais simples possível, faça listas diárias se possível e seu progresso vai se tornar óbvio.

###Torne isso seu

Tudo isso é muito bacana e tal mas você deve sempre focar em absorver apenas aquilo que te auxilia, deixando o resto de escanteio. Não existe nenhuma técnica de trabalho tão universal que possa atender à todos, sua melhor aposta é encontrar o que funciona pra você.

Tem dicas e ideias diferentes? Gostou? Comente abaixo!