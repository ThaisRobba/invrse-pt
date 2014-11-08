---
layout:     post
title:      Brackets - Programando a web
date:       2014-10-08 12:00:00
permalink:  editor-brackets-review
categories: 
    - review
    - text editor
comments:   true
---

<a href="http://brackets.io" target="_blank">Brackets</a> é um editor bastante poderoso, desenvolvido pela <a href="http://www.adobe.com" target="_blank">Adobe</a> para "programar a internet". É altamente extensível com um bom repositório de plugins e conta com um sistema de dicas de JavaScript bastante poderoso. Tá, tudo isso é bem legal mas quão eficaz é ele para desenvolvimento de jogos?

![a first look at brackets]({{site.baseurl}}/assets/brackets/first_impression.png)

###Primeira impressão

Brackets é bonito e roda lisinho. A interface é agradável, com um contraste bom tanto na sintáxe quanto na árvore de arquivos (e entre os mesmos). A renderização de fontes é um teco estranha porque o Brackets não necessariamente segue as regras do sistema - num geral o resultado é bom mas sem dúvida pode variar de instalação para instalação.

O seletor de pastas é brilhante em sua simplicidade e efetividade. Mudar de um projeto pro outro é rápido e, como é tudo baseado nas suas pastas, é fácil reorganizar conforme necessário. Abrir um outro projeto não abre uma janela nova - eu honestamente prefiro assim mas entendo quem queira diferente.

A árvore de arquivos é ordenada de maneira clara e concisa, similar ao Sublime Text. Arquivos são adicionados à seção "Working Files" somente quando modificados - abrir um arquivo para visualização não inunda seu espaço de trabalho.

Num todo, a primeira impressão é insanamente positiva dado o quão agradável é se usar o Brackets.

###Não vá embora nunca

![quick editing in Brackets]({{site.baseurl}}/assets/brackets/edit.gif)

Para desenvolvedores da web, um dos maiores argumentos a favor do Brackets é o modo de edição rápida (Quick Edit). Em essência, ele te permite selecionar um pedaço de código e editar parâmetros relacionados sem sair do arquivo. Por exemplo, num arquivo HTML você pode editar todo o CSS sem nunca precisar abrir o arquivo de estilos.

Esse modo de edição pode ser modificado via plugins, permitindo coisas como edição de gradients CSS ou de curvas e afins.

Decididamente poderoso - mas nem todo esse poder beneficia o desenvolvedor de jogos. Seu uso acaba resumindo-se em alterações de cores - útil mas não necessariamente vital.

![changing colors in Brackets]({{site.baseurl}}/assets/brackets/colors.gif)

###Hinting? Sim por favor!

Brackets brilha quando trabalhando com JavaScript por causa do sistema inteligente de dicas (hinting) - não só ele te oferece nomes e opções sãs mas quando chamando uma função, ele te indica quais argumentos podem ser passados. Pode parecer uma coisa pequena (e de certo modo, é) mas é uma melhoria que poupa tempo. Depois que você acostuma, fica difícil voltar para sistemas mais burrinhos.

![js hinting under Brackets]({{site.baseurl}}/assets/brackets/js_hint.gif)

Essa característica do Brackets não é sem limites, infelizmente. As opções às vezes não fazem muito sentido (tal como oferecer dicas de jQuery quando não estou usando tal framework) e ele pena com arquivos grandes. Usando o game framework do Phaser, que pesa uns 2mb, ele não conseguia auto-completar. Nem preciso dizer a tristeza que foi - mas é algo que, com o tempo, pode ser melhorado.

###Preview instântaneo

Uma das coisas mais legais pros desenvolvedores HTML5 é o "Live Preview". Ao clicar no ícone de raio na barra de extensões, ele abre uma janela do Chrome (ou Chromium) e toda e qualquer mudança é recarregada automaticamente.

![live preview under Brackets]({{site.baseurl}}/assets/brackets/preview.gif)

Isso simplifica muito o processo de teste já que ajustes finos, tais como gravidade num jogo plataforma, podem ser iterados rapidamente. Também significa que você não vai precisar começar um servidor para testar seu jogo (yay!).

Se você quiser abrir o console para ver erros e afins, faça-o através do Brackets (**F12**). Ele vai abrir uma nova janela, com console e afins. Se você tentar abrir pelas ferramentas de desenvolvedor do Goggle, você encerra o Live Preview.

###Um colchete aqui, outro ali

Que o editor é lindo e um baita software, não há dúvida. Mas, pelo menos pra mim, tem sempre alguma coisinha extra que poderia ser útil. Se você é como eu, nada tema! O gerenciador de extensões está entre nós!

![Extension manager]({{site.baseurl}}/assets/brackets/extension_manager.png)

É como um canal direto para as extensões desenvolvidas pela comunidade, permitindo grande liberdade no modo que o editor funciona. Tem todo tipo de pacotes:

- Integração com Git
- Visão geral do código (à lá Exuberant CTags)
- Snippets
- Temas diferentes

Entre outros tantos que podem melhorar sua experiência de desenvolvimento.

###Tem minha recomendação?

Sim! Acoplado com algumas extensões essenciais, é de longe um dos melhores editores para os desenvolvedores de jogos em HTML5 e, conforme for evoluindo, eu prevejo que será cada vez mais presente em nossas vidas.
