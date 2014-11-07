---
layout:     post
title:      Brackets & Snippets
date:       2014-10-24 20:00:00
permalink:  brackets-snippets
categories: 
- resource
- text editor
comments:   true
---

Uma das coisas que eu mais sinto falta no <a href="http://brackets.io" target="_blank">Brackets</a> é um sistema para criar "code snippets" (blocos de código).

###Snip quem?

![Snippets completion example]({{site.baseurl}}/assets/brackets/what_is_a_snippet.gif)

Veja-os como blocos de código pré-prontos, pra evitar o tédio de certas funções e afins.
Funcionam com base em pedaços menores de texto que podem ser expandidos - poupando tempo e sanidade!

###Conheça Emmet

Emmet é um sistema bastante famoso entre desenvolvedores front-end - ele simplifica muito a programação de arquivos HTML trazendo uma série de facilidades. Em essência, é um sistema de snippets anabolizado.

![emmet gone crazy]({{site.baseurl}}/assets/brackets/emmet_expand.gif)

É raro ver Emmet ser usado para coisas fora do reino do HTML/CSS mas é claramente possível, então eu decidi ver o que acontecia ao usá-lo com JavaScript. Não é perfeito mas tem algumas coisas muito legais.

![emmet and javascript]({{site.baseurl}}/assets/brackets/js_snippets.gif)

- Usar tecla **Tab** para expandir os blocos de código
- Aceita parâmetros especiais com o sustenido (#) e ponto.
- É fácil criar novos snippets
- Pode expandir um único trecho em muitos blocos

Para instalar Emmet no Brackets, basta procurar por ele no gerenciador de extensões.
Eu recomendo uma leitura rápida da <a href="http://docs.emmet.io/" target="_blank">documentação</a> do Emmet para entender melhor como ele funciona.

###Livre como Liberdade

Eu fiz arquivos de configuração especiais pro Brackets, você pode <a href="https://github.com/OttoRobba/javascript-emmet" target="_blank">vê-los no Github</a> ou  [baixá-los aqui!](https://github.com/OttoRobba/javascript-emmet/archive/master.zip)

Depois que você descompactar o arquivo em algum lugar, é só abrir no menu Emmet > Preferences e colocando o endereço da pasta extraída.

Estou desenvolvendo uma outra versão especificamente para Phaser mas não está pronta ainda.

Se isso te ajudou, se você tiver comentários ou ideias, sinta-se a vontade para contribuir!
