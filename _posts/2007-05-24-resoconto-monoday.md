---
title: Resoconto MONOday
author: Matteo Magni
layout: post
permalink: /2007/05/24/resoconto-monoday/
dsq_thread_id:
  - 1098323360
categories:
  - Development
---
Tempo fa mi ero iscritto alla [mailing-list di mono][1], ma per mesi non mi era arrivato niente, pensavo che fosse tutto fermo quando un giorno mi è arrivata una Mail da [Massimiliano Mantione][2] che parlava del primo [Mono Day][3] in Italia.  
![mono][4]  
Ho colto la palla al balzo e quindi oggi (ormai ieri&#8230;) sono stato a Modena ad assistere alla mattinata dedicata a questo rivoluzionario Framework.

Ecco un piccolo resoconto della giornata:

Carlo Baffè (Novell italia) che ha fatto una panoramica generale su Suse e Novell, dopo di ciò è passato al framework e Ha fatto alcuni esempi &#8220;eclatanti&#8221; su dove è stato utilizzato MONO. Questi i più famosi:

*   [MP3 player][5] dal [Blog Miguel De Icaza][6]
*   [Second Life ][7](molte cose stanno migrando a mono per avere minor uso di memoria e maggiori prestazioni.

Molto utile lo strumento [Mono Migration analyzer][8] (MoMa), che permette di capire che fatica dovrò fare per portare su MONO una applicazione scritta per Windows.

Dopo l&#8217;introduzione di Novell si è lasciato spazio ad alcuni partner di Novell qui in italia.

[Nexida:][9]

*   Umberto Ballestrazzi che ha fatto una piccola presentazione di che cosa fa Nexida.
*   Luca Cavicchioli che ci ha illustrato un po&#8217; il mondo dello sviluppo con Mono: quali sono i toolkit, gli ambienti di sviluppo, ecc&#8230;  
    Dopo ci ha fatto vedere come sviluppare una piccola applicazione con MonoDevelop e GTK# e poi fare girare l&#8217;eseguibile sia su Linux che su Windows. Sorprendente per tutti quelli che per avere applicazioni Cross-platform fino ad ora dovevano fare una versione per ogni sistema operativo.
*   Stefano invece ci ha mostrato la realizzazione di una applicazione web usando il RAD Templte2code di Nexida. Poi ci ha mostrato una applicazione web complessa già fatta e commercializzata da nexida che poteva girare pure su linux senza nessuna fatica per fare il porting.

[  
NBfactory:][10]  
Luca Turco che ha illustrato Ubiware: Soluzione per gli agenti commerciali che operano sul campo, sottolinenado spesso il vantaggio di non dover far scegliere al cliente una determinata piattaforma, tanto scrivendo con MONO l&#8217;applicazione è Cross-Platform. 

Infine l&#8217;intervento del Guru italiano di MONO:

[Massimiliano Mantione][2] (Mono Hacker).  
Intervento veramente interessante nel quale è partito dalla storia di mono; ha raccontato che all&#8217;inizio Miguel De Icaza aveva deciso di sviluppare MONO perchè come disse: &#8220;Unix sucks&#8221;, cioè che come ambiente di sviluppo Linux era troppo frammentato, e quindi poco produttivo (per Ximian sviluppare Evolution fu per questo motivo veramente troppo dispendioso).  
Il fatto che poi fosse pure utile per migrare da Windows a Linux era al tempo solo un buon effetto collaterale. Con l&#8217;acquisto da parte di Novell invece quest&#8217;ultimo è diventato per ovvi motivi commerciali fondamentale.  
Andando avanti si è sempre di più entrati nel tecnico, prossime release e mancanze nel progetto, fino a parlare un po&#8217;del JIT su cui Massi lavora per Ximian. Purtroppo qui le mie conoscenze si sono rivelate un po&#8217; troppo scarse, comunque Massi è stato molto bravo a far capire le potenzialità e gli obbiettivi del progetto.

In conclucione ottimo evento che spero verrà replicato il prossimo anno, intanto mi sa che comincerò a provare serimente monodevelop che da poco ho installato sul mio pc.  
Gabba Gabba Hey  
Bonzo

P.S. ho pure imparato che Mono significa scimmia in spagnolo&#8230;.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://www.freelists.org/webpage/mono-it
 [2]: http://primates.ximian.com/~massi/blog/
 [3]: http://http://www.novell.com/global/italia/eventi/monoday.html
 [4]: http://magni.me/wp-content/uploads/2007/05/mono.jpg
 [5]: http://www.sandisk.com/sansaconnect/
 [6]: http://tirania.org/blog/archive/2007/Apr-10.html
 [7]: http://secondlife.com/
 [8]: http://www.mono-project.com/MoMA
 [9]: http://www.nexida.com/
 [10]: http://http://www.nbfactory.com/