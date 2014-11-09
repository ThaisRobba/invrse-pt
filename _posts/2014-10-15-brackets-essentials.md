---
layout:     post
title:      8 extensões essenciais pro Brackets
date:       2014-10-15 20:00:00
permalink:  brackets-extensoes-essenciais
categories: 
    - text editor
comments:   true
---

O repositório de extensões do Brackets é enorme e separar o joio do trigo não é tarefa fácil dada a ferramenta de busca não tão evoluida. Depois de testar e pesquisar bastante, eu compilei uma lista das minhas favoritas que, eu acredito, são essenciais para todos os desenvolvedores de jogos.


###1. Extension Rating
![Extension Rating]({{site.baseurl}}/assets/brackets/extension_rating.png)

Esse pacote torna o processo de descoberta de novas extensões uma moleza. Ele busca e apresenta informações como número de downloads, data de atualização, data de lançamento, ele designa etiquetas (top, trending, popular, etc...) e mostra um seletor para filtrar mais facilmente a busca.

No gerenciador de extensões, procure por:

    Extensions-Rating

###2. Brackets Git
![Extension Rating]({{site.baseurl}}/assets/brackets/git.png)

Essa é provavelmente a melhor experiência que eu já tive com Git. O pacote integra-se perfeitamente com o Brackets, é muito poderoso e estupidamente fácil de usar.

Sério. Eu me sentiria confortável ensinando um novato a usar Git através do Brackets (e confiaria na pessoa ainda por cima).

A extensão tem padrões bons, suficientes para 98% das pessoas que usam o sistema e permite, pros mais avançados, abrir o terminal de comando direto no diretório do projeto.

No gerenciador de extensões, procure por:

    brackets-git martin
    
###3. Console Plus
![Extension Rating]({{site.baseurl}}/assets/brackets/console_plus.png)

Essa extensão é muito útil porque ela facilita num dos pontos mais chatos do Live Preview do Brackets. Basicamente, todo e qualquer erro que você tiver do seu jogo vai aparecer nesse console - o arquivo onde está o erro é clicável então você rapidinho chega no culpado.

No gerenciador de extensões, procure por:

    console-plus
    
###4. JSHint

Brackets vem com o JSLint por padrão - é um ótimo sistema de linting mas não necessariamente o meu favorito.

Instalar o JSHint é fácil com esse pacote e você pode configurar um arquivo .jshintrc na raíz do projeto, pra garantir que suas opções sejam honradas no projeto todo.

Bônus: Compartilhar o arquivo .jshintrc com sua equipe garante um código homogêneo.

Meu .jshintrc para trabalhar com Phaser é assim:

    {
        "undef": false,
        "unused": false
    }

No gerenciador de extensões, procure por:

    JSHint raymond

###5. Interactive Linter
![Extension Rating]({{site.baseurl}}/assets/brackets/linting.gif)

Agora sim! Pra que perder tempo decifrando informações num painel se podemos usar indicadores direto na linha onde existe o erro? Baixe, use, ame.

No gerenciador de extensões, procure por:

    interactive-linter

###6. JSBeautifier
![Extension Rating]({{site.baseurl}}/assets/brackets/beautify.gif)

A maneira mais fácil de garantir um estilo claro e homogêneo - após instalar a extensão, é só ir no menu Edit > Beautify on Save. Pronto, agora é só trabalhar normalmente e tudo sempre ficará organizado!

No gerenciador de extensões, procure por:

    jsbeautifier

###7. Zen Pane
![Extension Rating]({{site.baseurl}}/assets/brackets/zenpane.gif)

Brackets (versão 1.0) acabou de implementar a opção de visualizar dois arquivos ao mesmo tempo - útil mas não está perfeira. Essa extensão deixa um tanto mais claro em qual arquivo você está mexendo e evita erros bestas.

No gerenciador de extensões, procure por:

    zen-pane
    
###8. Code Folding
![Code folding]({{site.baseurl}}/assets/brackets/code_folding.png)

Por padrão, Brackets não tem como dobrar blocos de código (code folding) - é algo que está planejado mas, pelo menos por enquanto, essa extensão quebra esse galho.

No gerenciador de extensões, procure por:

    code-folding
    
###E você

Essas extensões te ajudam? O que mais você usa?