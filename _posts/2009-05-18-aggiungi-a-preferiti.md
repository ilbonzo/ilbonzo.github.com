---
title: Aggiungi a preferiti
author: Matteo Magni
layout: post
permalink: /2009/05/18/aggiungi-a-preferiti/
categories:
  - Development
tags:
  - Javascript
---
Funzione javascript per aggiungere una pagina ai preferiti

`<br />
function BookmarkPage(){<br />
if (window.sidebar)<br />
window.sidebar.addPanel(document.title, window.location,"");<br />
else if(document.all)<br />
window.external.AddFavorite(window.location, document.title);<br />
else if(window.opera &#038;&#038; window.print)<br />
alert("Utenti Opera: per aggiungere questo sito ai preferiti, cliccare su 'OK' poi premere CTRL-D");<br />
else<br />
alert("Utenti: per aggiungere questo sito ai preferiti, cliccare su 'OK' poi premere CTRL-D");}<br />
`

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>