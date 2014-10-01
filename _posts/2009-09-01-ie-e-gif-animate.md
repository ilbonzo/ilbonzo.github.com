---
title: Bug di IE con le gif animate
author: ilbonzo
layout: post
permalink: /2009/09/01/ie-e-gif-animate/
dsq_thread_id:
  - 1097088934
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - Javascript
---
Purtroppo su IE ogni volta che inviamo un form le gif animate vengono fermate.

Ecco uno scenario tipico per questo errore: una form per inviare una foto dove si vuole fare attendere l&#8217;utente che finisca l&#8217;upload dandogli la sensazione, tramite una gif animata, che la pagina web stia lavorando.  
`<br />
<form onSubmit="gif()" name="myform" action="#" method="post" enctype="multipart/form-data"><br />
<p id="wait"><br />
<img id="WaitImage" src="images/loadingAnimation.gif"/><br /><br />
<strong>&Egrave; in corso l'invio ...<br /><br />
L'operazione potrebbe richiedere qualche minuto, attendi senza chiudere questa finestra.<br />
</strong><br />
</p><br />
</form><br />
`

Visto che su IE la gif che era nascosta, quando invio la form smette di essere animata, bisogna trovare un modo per farla ripartire.

Tutto si può fare dando l&#8217;impressione ad IE di aver modificato l&#8217;immagine con Javascript un tempo successivo all&#8217;invio della form, tramite questa istruzione:  
`<br />
setTimeout('document.getElementById("WaitImage").src = "images/loadingAnimation.gif"', 200);<br />
`

`<br />
<script type="text/javascript"><br />
function gif()<br />
{<br />
	if (document.forms["myform"]["file"].value != "")<br />
	{<br />
	  		document.getElementById('bottone_carica').style.display = 'none';<br />
	  		document.getElementById('wait').style.display = 'block';<br />
	  		setTimeout('document.getElementById("WaitImage").src = "images/loadingAnimation.gif"', 200);<br />
	}<br />
}<br />
</script><br />
`

Così la gif bloccata ripartirà a eseguire la sua animazione.

<div class='kindleWidget kindleLight' >
  
</div>

