---
layout: post
title: Esconder menus do Atom
date: 2014-10-01 10:00
permalink: esconder-menu-atom
categories: 
    - text editor
comments: true
---

Eu sou daquelas pessoas que se sente feliz usando ferramentas bem feitas - usar programas que integram harmonicamente com o sistema, que funcionam como esperado é, ao meu ver, algo belo.

Quando eu uso o Atom, no entanto, me dá uma tristeza a feiúra desnecessária dos menus.

![Awful menus must die]({{site.baseurl}}/assets/atom/with_menu.png)


###Rearrumando átomos

Em certos aplicativos, menus fazem sentido. No caso do Atom, com a paleta de comandos, eles parecem largamente irrelevantes.

Abra uma janela do terminal e cole o código a seguir:

    sudo gedit '/opt/atom/resources/app/src/browser/atom-window.js'

**Nota:** Substitua o gedit pelo editor que você preferir utilizar

**Nota para usuários do Windows:** A pasta do Atom deve estar instalada em  C:\Arquivos de Programas ou similar.

No arquivo atom-window.js, ache o código abaixo:

{% highlight javascript %}
this.browserWindow = new BrowserWindow({
    show: false,
    title: 'Atom',
    icon: this.constructor.iconPath,
    'web-preferences': {
      'subpixel-font-scaling': false
    }
  });
{% endhighlight %}

E substitua-o pelo código abaixo:

{% highlight javascript %}
this.browserWindow = new BrowserWindow({
        show: false,
        title: 'Atom',
        'auto-hide-menu-bar': true,
        icon: this.constructor.iconPath,
        'web-preferences': {
          'subpixel-font-scaling': false
        }
      });
{% endhighlight %}

###Que trabalheira!

Num mundo ideal, o editor deveria vir com a opção de esconder/mostrar o menu. Até alguém colocar isso no código final, essa é a opção que temos. No lado positivo, apertando a tecla **ALT** você retoma a funcionabilidade do menu.

![Beauty incarnate]({{site.baseurl}}/assets/atom/without_menu.png)

Tenha em mente que será necessário refazer isso a cada atualização do Atom.