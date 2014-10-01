---
title: Linux su windows
author: ilbonzo
layout: post
permalink: /2008/03/19/linux-su-windows/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1102732604
categories:
  - linux
  - windows
comments: true
share: true
---
Spesso capita di dover lavorare su una postazione windows e di sentire la mancanza di linux o di qualche suo programma specifico.  
Magari è solo una sensazione da geek, più che una vera esigenza, ma spesso questa situazione provoca grossi stati di &#8220;ansia&#8221;. Di solito per supplire a questa mancanza si ricorre ad una bella virtualizzazione ed ai programmi multipiattaforma (mozilla,OOo&#8230;).  
Oltre a tutto ciò ci sono anche altri modi che permettono ad un utente Linux di sentirsi a casa anche se sta lavorando su una postazione Windows.

**  
[Sudowin][1]**  
Si tratta di un programma sviluppato per i sistemi Microsoft che inspirandosi al comando Linux SUDO simula la gestione dei permessi delle distribuzioni come Ubuntu.

<a rel="shadowbox" href='http://magni.me/wp-content/uploads/2008/03/01_sudowin.png' title='installazione sudowin' class="option"><img src='http://magni.me/wp-content/uploads/2008/03/01_sudowin.thumbnail.png' alt='installazione sudowin' /></a>

Questo permette di eseguire programmi come amministratore da un account limitato senza dover abbandonare l&#8217;account in uso. In questo modo, l&#8217;utente resta sempre il proprietario dei file installati, delle chiavi di registro e così via che lo riguardano. A differenza di RunAs, inoltre, tutte le icone presenti sul desktop restano visibili nella loro posizione.

<a rel="shadowbox" href='http://magni.me/wp-content/uploads/2008/03/02_sudowin1.png' title='Sudowin' class="option"><img src='http://magni.me/wp-content/uploads/2008/03/02_sudowin1.thumbnail.png' alt='Sudowin' /></a>

**  
[AndLinux][2]**  
Permette di far funzionare una distribuzione Linux come Ubuntu 7.10 sotto Windows, sia in modalità shell di comandi che grafica attraverso Xming. E questo grazie al fatto che, basandosi sul progetto Cooperative Linux (coLinux), andLinux utilizza dei propri driver per emulare i dispositivi hardware ed eseguire il kernel di Linux in Supervisor Mode (Ring 0)

Nell&#8217;installazione viene chiesto quanta RAM volete dedicare ad andLinux.

<a rel="shadowbox" href='http://magni.me/wp-content/uploads/2008/03/03_andlinux.png' title='Installazione andLinux' class="option"><img src='http://magni.me/wp-content/uploads/2008/03/03_andlinux.thumbnail.png' alt='Installazione andLinux' /></a>

Si può scegliere se usarlo come servizio o farlo partire manualmente da Prompt.  
Bisogna decidere se andLinux accederà alle cartelle condivise di windows e se si come (per esempio usando Samba)

<a rel="shadowbox" href='http://magni.me/wp-content/uploads/2008/03/04_andlinux1.png' title='andLinux software' class="option"><img src='http://magni.me/wp-content/uploads/2008/03/04_andlinux1.thumbnail.png' alt='andLinux software' /></a>

E&#8217; ancora in Beta, ma sembra funzionare già bene.

<a rel="shadowbox" href='http://magni.me/wp-content/uploads/2008/03/05_andlinux.png' title='andLinux screeshots' class="option"><img src='http://magni.me/wp-content/uploads/2008/03/05_andlinux.thumbnail.png' alt='andLinux screeshots' /></a>

**  
[KDE 4.0 su windows][3]**  
Il nuovo DE ha un livello di astrazione tale che si potrà eseguire pure su windows.  
Per adesso però siamo ancora indietro, aspettiamo novità.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >

</div>



 [1]: http://sourceforge.net/projects/sudowin/
 [2]: http://www.andlinux.org/
 [3]: http://windows.kde.org/
