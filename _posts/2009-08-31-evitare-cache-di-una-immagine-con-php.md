---
title: Evitare Cache di una immagine con PHP
author: Matteo Magni
layout: post
permalink: /2009/08/31/evitare-cache-di-una-immagine-con-php/
pdrp_attributionLocation:
  - end
dsq_thread_id:
  - 1417880554
categories:
  - Development
tags:
  - PHP
---
Se volete che una immagine venga ripescata dalla cache in PHP è molto semplice, basta accodare una stringa che varia ogni volta all&#8217;indirizzo dell&#8217;immagine.  
Il Browser sarà così ingannato e penserà di dover recuperare una nuova immagine.  
Per esempio si potrebbe usare la funzione time che ritorna il timestamp.

`<br />
'<img src="immagine.jpg?t='.time().'"/>'<br />
`

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>