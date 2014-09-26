---
title: Resoconto PHPday
author: Matteo Magni
layout: post
permalink: /2007/05/19/resoconto-phpday/
dsq_thread_id:
  - 1111790148
pdrp_attributionLocation:
  - end
categories:
  - eventi
tags:
  - PHP
---
PHPday

Arrivato in ritardo ovviamente, forse perché inconsciamente non volevo sentire l&#8217;intervento di Microsoft&#8230;.

Microsoft e PHP insieme un po&#8217; stonano&#8230;.

Premetto che ho deciso di seguire il canale Developer (quello seguito da più persone) quindi non dirò molto dei vari Talk del canale Enterprise. Di molti talk è possibile trovare il materiale sul sito del [PHPday][1].

Il primo intervento ascoltato è stato quello di [Francesco Trucchia][2] che ci ha parlato dello sviluppo RAD di PHP con strumenti Open-source, in particolare ci ha illustrato il framework [Symfony][3].  
Dopo una breve introduzione ha provato a farci vedere come si può sviluppare un Blog con questo strumento in pochi minuti. Il tempo a sua disposizione purtroppo non è bastato, però la potenza del Framework è sembrata reale, per questo motivo credo che nei prossimi mesi lo riempirò di email per farmi aiutare a studiare Symfony&#8230;. auguri.  
Ecco le slide utilizzate:

[http://www.slideshare.net/fullo&#8230;.][4]

Scusate la pausa pranzo&#8230;.  
<a href="http://magni.me/wp-content/uploads/2007/05/dscf3194.jpg" rel="lightbox" title="Pausa pranzo"><img src="http://magni.me/wp-content/uploads/2007/05/dscf3194.miniatura.jpg" width="130" height="100" alt="Pausa pranzo al phpday" /></a>  
Nel pomeriggio abbiamo ascoltato:  
[Jacopo Romei][5] che ci ha parlato dell&#8217;XP (eXtreme Programming):

> &#8220;Insieme di pratiche empiriche per lo sviluppo del software che ha come obbiettivo la soddisfazione del cliente.&#8221;

Con una presentazione molto spigliata è riuscito a farmi entrare in questo argomento a me sconosciuto.  
Interessante lo strumento [Gobby][6]: Editor che permette di avere N cursori gestite da più persone in remoto. Insieme a [Skype][7] ottimo strumento per il Pair Programming.  
Ecco le slide del Talk:  
[http://www.slideshare.net/fullo/&#8230;][8]

Subito dopo [Gabriele Lana][9] ci ha parlato di Testing web application:  
Sintesi dell&#8217;intervento  
Debug Sucks&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;- Test Rocks.  
Facendo notare che i Bug è meglio evitarli all&#8217;inizio, invece che risolverli, perché i Test hanno un costo misurabile in maniera migliore dei Bug.  
Ci ha parlato dei test facendo anche delle parentesi su quali sono gli strumenti che si possono usare:  
Test Unitari: [PHPunit][10];  
Test Funzionali: [Selenium][11];  
Test di accettazione: [PHPfit][12];

Ecco le slide del Talk:  
[http://www.slideshare.net/fullo/&#8230;][13]  
Dopo il coffee Break [Enrico Zimuel][14] ha parlato di sicurezza delle applicazioni in PHP  
L&#8217;intervento, risultato un po&#8217; meno spumeggiante rispetto a quelli precedenti è in realtà stato molto utile, per chi come me non è così padrone di un argomento molto importante come quello della sicurezza in PHP.

I consigli sulle cose da fare sempre per evitarsi molti problemi:  
• filtrare sempre input;  
• Tenere Register Globals sempre OFF;  
• Formattare sempre Output;

Le varie tecniche illustrate, in maniera molto generale visto il poco tempo a disposizione, per fare danni in applicazioni PHP sono state:  
• SQL injection  
• Cross site scripting  
• Exposed source code  
• Session fixation  
• Session Hijacking  
• Cross-site request forgeries  
Ecco le slide del Talk:  
[www.slideshare.net/fullo/&#8230;][15]

Alla fine l&#8217;intervento di Andrea Giardina che ha parlato di [PHP For Applications][16]  
Applicazione che permetti di creare applicazioni web a partire da applicazioni scritte in particolare per Access.  
In particolare non ha usato slide ma ha fatto in tempo reale un piccolo esempio realizzando una applicazione riguradante un catalogo di libri.  
P4A è ancora compatibile con PHP4 anche se stanno pensando di migrare a PHP5

Come partner erano presenti:  
• [Microsoft][17], non manca mai&#8230;.  
• [Zend][18] che ha tenuto un talk del canale Enterprise e che ringrazio per avermi regalato PHPprofessionale, purtroppo due giorni prima lo avevo già comprato. Peccato 12 euro che potevo risparmiare&#8230; Tra tutti all&#8217;interno dei Talk il marchio più pubblicizzato.  
• [Yahoo][19] che ha tenuto un talk del canale Enterprise.

Molto interessante il fatto che si potesse seguire l&#8217;evento su [UstreamTv][20], la prossima volta se non riuscirò a venire avrò un&#8217;alternativa. Ecco i potenti mezzi con cui si è Filmato l&#8217;evento di webtv:  
<a href="http://magni.me/wp-content/uploads/2007/05/dscf3196.jpg" rel="lightbox" title="Webcam phpay"><img src="http://magni.me/wp-content/uploads/2007/05/dscf3196.miniatura.jpg" width="130" height="100" alt="Webcam phpday per Ustream.tv" /></a>  
Inoltre su [twitter][21] si avevano continui aggiornamenti sui talk che stavano.

Evento sicuramente interessante e ben organizzato, ringrazio il [GrUSP][22] del quale sono diventato socio ordinario, ci si vede il prossimo anno.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://www.phpday.it/site/
 [2]: http://www.cphp.it/
 [3]: http://www.symfony-project.com/
 [4]: http://www.slideshare.net/fullo/francesco-trucchia-rapid-application-developement-con-strumenti-open-source
 [5]: http://www.phpday.it/site/phpday-2007/calendario-conferenze/canale-developers/jacopo-romei-abbattere-i-rischi-di-insuccesso-con-extreme-programming/
 [6]: http://gobby.0x539.de/trac/
 [7]: http://www.skype.com/intl/it/helloagain.html
 [8]: http://www.slideshare.net/fullo/jacopo-romei-abbattere-i-rischi-di-insuccesso-con-extreme-programming/
 [9]: http://www.gabrielelana.it/
 [10]: http://phpunit.sourceforge.net/
 [11]: http://www.openqa.org/selenium/
 [12]: http://developer.berlios.de/projects/phpfit/
 [13]: http://www.slideshare.net/fullo/gabriele-lana-testing-web-applications/12
 [14]: http://www.zimuel.it/
 [15]: www.slideshare.net/fullo/enrico-zimuel-la-sicurezza-delle-applicazioni-in-php/
 [16]: http://p4a.crealabsfoundation.org/
 [17]: www.microsoft.com/italy/
 [18]: http://www.zend.com/
 [19]: http://it.yahoo.com/
 [20]: http://www.ustream.tv/
 [21]: http://twitter.com/fullo
 [22]: http://www.grusp.it/