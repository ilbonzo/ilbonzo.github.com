---
title: Slimbox wordpress plugin
author: ilbonzo
layout: post
permalink: /2008/01/17/slimbox-wordpress-plugin/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1108689455
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - Javascript
  - wordpress
---
Come ho già avuto occasione di dire, mi piacciono molto le finestre modali per la visualizzazione delle immagini e dove potevo le ho sempre inserite.  
Fino ad ora ho utilizzato in particolare <a href="http://www.huddletogether.com/projects/lightbox2/" class="Tips3" title="huddletogether.com lightbox2">lightbox</a>, ma ovviamente ho testato anche altre soluzioni. Ultimamente però ho preso la decisione di utilizzare principalmente <a href="http://mootools.net/" class="Tips3" title="framework javascipt mootools">mootools</a> come framework javascript quindi, visto che è più funzionale caricare solo una libreria per non appesantire troppo i client, ho deciso di sostituire lightbox con <a href="http://www.digitalia.be/software/slimbox" class="Tips3" title="Finestra modale con slimbox">slimbox</a> utilizzando il plugin relativo anche sul blog:

[slimbox wordpress plugin/][1]

Eccone alcuni esempi con immagini che già sono state usate nel mio blog.

<a href='http://magni.me/wp-content/uploads/2008/01/06_ruby.png' title='ruby 06' rel="lightbox"><img src='http://magni.me/wp-content/uploads/2008/01/06_ruby.thumbnail.png' alt='ruby 06' /></a>

Sequenza

<a href='http://magni.me/wp-content/uploads/2007/05/g_evolution.png' title='tab ricezione mail' rel="lightbox[roadtrip]"><img src='http://magni.me/wp-content/uploads/2007/05/g_evolution.png' alt='tab ricezione mail' width="200" height="150" /></a> <a href='http://magni.me/wp-content/uploads/2007/05/g_evolution.png' title='tab ricezione mail' rel="lightbox[roadtrip]"><img src='http://magni.me/wp-content/uploads/2007/05/g_evolution.png' alt='tab ricezione mail' width="200" height="150" /></a>

il codice è questo:

`Single example:<br />
<a href=”img1.jpg” rel=”lightbox” title=”my caption”>thumbnail1</a><br />
Image set example:<br />
<a href=”img1.jpg” rel=”lightbox[roadtrip]”>thumbnail1</a><br />
<a href=”img2.jpg” rel=”lightbox[roadtrip]”>thumbnail2</a><br />
<a href=”img3.jpg” rel=”lightbox[roadtrip]”>thumbnail3</a>`

Ogni volta che si inserisce una immagine bisogna aggiungere l&#8217;attributo rel, lightbox se è solo una immagine o lightbox[roadtrip] se si vuole creare una sequenza.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://www.4mj.it/slimbox-wordpress-plugin/