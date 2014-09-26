---
title: Facciamo Ping
author: Matteo Magni
layout: post
permalink: /2007/05/30/facciamo-ping/
dsq_thread_id:
  - 1099137282
categories:
  - Networking
---
<p>Oggi per la prima volta (so che a molti sembrerà strano) ho avuto bisogno di usare il comando ping.</p>
<blockquote><p>Il ping è un termine onomatopeico nato per indicare un segnale sonoro di breve durata e di alta tonalità emesso da un sottomarino per segnalare la propria presenza e la propria raggiungibilità ad un altro sottomarino.<br />
Nel linguaggio informatico il termine è stato adottato per designare un particolare comando (presente su molti sistemi diversi, come UNIX, DOS, Windows95) che invia una successione di pacchetti ad una stazione per verificarne la raggiungibilità, e che ricorre a tal fine al protocollo ICMP.<br />
Vediamo come funziona: supponiamo che dalla stazione A si voglia controllare l&#8217;integrità della connessione fino alla stazione B. Si esegue il comando ping, passandogli come argomento l&#8217;indirizzo della stazione B. Il programma manda una serie di messaggi ICMP ECHO_REQUEST (generalmente uno al secondo) dalla stazione A verso la stazione B. Quando la stazione B riceve un pacchetto ECHO_REQUEST, il suo strato internet si occupa di rispondere con un nuovo datagramma ICMP ECHO_REPLY, che viene mandato indietro alla macchina A. il programma ping userà le informazioni così collezionate (esistenza dei pacchetti di ritorno, tempo intercorso per ogni pacchetto, etc.) per calcolare dei valori statistici sulla bontà della connessione e presentarli all&#8217;utente.
</p></blockquote>
<p><a href="http://www.inf.uniroma3.it/~patrigna/didactic/imp_elab/slides_icmp/icmp_5.html"></p>
<p>http://www.inf.uniroma3.it/~patrigna/didactic/imp_elab/slides_icmp/icmp_5.html</a></p>
<p>Ecco un piccolo esempio fatto dalla mia macchina al sito <a href="http://www.ilbonzo.org">www.ilbonzo.org</a>:<br />
<a href="http://magni.me/wp-content/uploads/2007/05/ping_1.png" rel="lightbox" title="Facciamo Ping"><img src="http://magni.me/wp-content/uploads/2007/05/ping_1.png" width="400" height="250" alt="Esempio del comando ping" /></a></p>
<p>Per fermare il comando bisogna usare Ctrl + c.<br />
in sostanza è un po&#8217; come telefonare per sentire se dà il libero.<br />
Si può usare con l&#8217;ip della macchina che si vuole raggiungere o con il nome, come nel caso del sito.</p>
<p>Prima o poi diventerò un po&#8217; più esperto nella gestione di reti, intanto da qualcosa bisogna pur cominciare&#8230;</p>
<p>Gabba, Gabba Hey<br />
Bonzo</p>
<div class='kindleWidget kindleLight' ><img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span></div><a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>