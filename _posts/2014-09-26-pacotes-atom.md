---
layout:     post
title:      8 extensões essenciais pro Atom
date:       2014-09-26 20:00:00
permalink:  atom-pacotes-recomendados
categories: 
    - text editor
    - resource
comments:   true
---

Que o [Atom é um editor excelente]({{site.baseurl}}/review-editor-atom/), ninguém duvida. Mas é fato que a experiência pode ser melhorada - segue abaixo uma lista com 8 extensões que, acredito, são essenciais!

**Nota sobre a instalação dos pacotes:**

Existem dois jeitos de instalar extensões. Um deles é buscando pelo nome do pacote nas página de configurações dentro do Atom e a outra é usando a linha de comando. Em prol da eficiência, vou listar o comando.

###1. Autocomplete Plus

![Completion like a boss]({{site.baseurl}}/assets/atom/completion.png)

O Atom, por padrão, é capaz de auto completar palavras - não é tão automático ou integrado como gostaríamos. Esse pacote conserta isso, oferecendo as sugestões visualmente, incluindo blocos de código e caminhos de arquivos!

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install autocomplete-plus autocomplete-paths autocomplete-snippets

**Nota:**

O mapeamento do teclado pra esse pacote é, por padrão, a tecla **Tab**. Eu não gosto disso pois prefiro que ela funcione apenas com blocos de código. Eu mudei assim o meu arquivo de mapeamento de teclas:

    '.autocomplete-plus input.hidden-input':
      'enter': 'autocomplete-plus:confirm'
      'tab': 'unset!'

###2. Git Plus
![Imma gonna git ya!]({{site.baseurl}}/assets/atom/git_plus.png)

Com esse pacote basta abrir a paleta de comandos (Ctrl+Shift+P) e você ganha todas as funções essenciais do Git, tais como adicionar os arquivos, criar um 'commit' e empurrar de volta pro ramo.

Basicamente, dá para manejar repositórios inteiros direto do editor - uma mão na roda!

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

     apm install git-plus
     
###3. Git History
![Gonna git ya good!]({{site.baseurl}}/assets/atom/git_history.png)

Integramos o Git e agora, com esse pacote, podemos ver todo o histórico, commit por commit!

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:
 
    apm install git-history
    
###4. Git Blame
![Git!]({{site.baseurl}}/assets/atom/git_blame.png)

Ainda mais poder e integração com Git! Agora você consegue ver quem fez o que no arquivo, basta apertar **Ctrl+B**.

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install git-blame

###5. Open Last Project
![Hello old friends]({{site.baseurl}}/assets/atom/open_last.png)

Talvez uma das extensões mais simples e mais úteis - com ela instalada, o Atom lembra dos últimos arquivos abertos toda vez que você roda o aplicativo.

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install atom-open-last-project

###6. Color Picker
![Picking colors is easy]({{site.baseurl}}/assets/atom/color_picker.png)

Outra pequena adição que torna a vida mais fácil. Quando você precisar do código de uma cor, é só chamar o seletor de cores com **Ctrl+Alt+C**.

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install color-picker
    
###7. JSHint
![Sorry, commagain?]({{site.baseurl}}/assets/atom/jshint.png)

Adiciona linting dinâmico aos arquivos de JavaScript, com base nas regras do JSHint. Num geral é uma boa ideia para garantir uniformidade de código e evitar alguns errinhos bestas.

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install atom-jshint

###8. JSFormat
![Bam!]({{site.baseurl}}/assets/atom/jsformat.gif)

Essa extensão permite embelezar seu código de acordo com as diretrizes do js-beautify, com possibilidade de mudar algumas coisas conforme as opções que você configurar.

É vital para qualquer desenvolvedor que trabalhe com HTML5, especialmente em equipes. O código fica uniforme e legível - para de arrumar os espaços na mão e instale logo esse pacote!

Para instalar este pacote, copie e cole o códio abaixo na linha de comando:

    apm install jsformat-atom
    
###Por hoje é só pessoal!

E pra você, quais pacotes são essenciais? Qual extensão que você não consegue ficar sem?
