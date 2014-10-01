---
title: Menu orizzontale con i css
author: Matteo Magni
layout: post
permalink: /2007/11/08/lista-css-orizzontale/
dsq_thread_id:
  - 1098390387
categories:
  - css
---
Vediamo come creare un menu orizzontale partendo da un elenco puntato tramite i css:

Ecco il codice html con l&#8217;elenco che diventerà il nostro menu:  
`<br />
<div id="navigation_1"><br />
<ul><br />
      <li id="home"><a href="#" title="Home ">Home</a></li><br />
      <li id="contatti"><a href="#" title="Contatti">Contatti</a></li><br />
      <li id="azienda"><a href="#" title="azienda">azienda</a></li><br />    </ul><br />
</div>`  
`<br />
<div id="navigation_2"><br />
<ul><br />
      <li id="home"><a href="#" title="Home ">Home</a></li><br />
      <li id="contatti"><a href="#" title="Contatti">Contatti</a></li><br />
      <li id="azienda"><a href="#" title="azienda">azienda</a></li><br />    </ul><br />
</div><br />
`

Senza alcune proprietà css avremmo dei semplici elenchi puntati che non sono certo adatti a chi desidera un menu orizzontale:

<div id="navigation_1">
  <ul>
    <li id="home">
      <a href="#" title="Home">Home</a>
    </li>
    <li id="contatti">
      <a href="#" title="Contatti">Contatti</a>
    </li>
    <li id="azienda">
      <a href="#" title="Azienda">Azienda</a>
    </li>
  </ul>
</div>

<div id="navigation_2">
  <ul>
    <li id="home">
      <a href="#" title="Home">Home</a>
    </li>
    <li id="contatti">
      <a href="#" title="Contatti">Contatti</a>
    </li>
    <li id="azienda">
      <a href="#" title="Azienda">Azienda</a>
    </li>
  </ul>
</div>

Ora passiamo al foglio di stile, abbiamo due modi per rendere il menu orizzontale e centrato:  
`<br />
div#navigation_1{text-align: center}<br />
li{display: inline} /*rendo gli elementi li inline*/<br />
`

Oppure  
`<br />
div#navigation_2{text-align: center}<br />
div#navigation_2 ul{width: 375px; margin: 0 auto; list-style-type:none;}<br />
div#navigation_2 li{float: left;width: 75px} /*Rendo gli elemnti li float*/<br />
`

Tutto ciò perché per creare un menu accessibile una elenco è molto meglio che mettere dei link uno dopo l&#8217;altro distanziati da uno spazio; il documento in quel caso non avrebbe una struttura logica e chiara per chi naviga con i browser testuali per esempio.  
Ora basta sbizzarrirsi per rendere il menu gradevole a chi naviga con i css stando però siamo tranquilli che il tutto sarà comprensibile anche per chi i css li ha disattivati.

[Visualizza l&#8217;esempio completo][1]

Buona accessibilità a tutti allora.  
Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://blog.ilbonzo.org/upload/css/lista.html