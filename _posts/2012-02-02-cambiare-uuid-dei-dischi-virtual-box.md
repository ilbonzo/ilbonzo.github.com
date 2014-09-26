---
title: Cambiare UUID dei dischi Virtual Box
author: Matteo Magni
layout: post
permalink: /2012/02/02/cambiare-uuid-dei-dischi-virtual-box/
Hide OgTags:
  - 0
Hide SexyBookmarks:
  - 0
thesis_title:
  - Cambiare UUID dei dischi Virtual Box
thesis_description:
  - "Risolvere l'errore A hard disk with UUID {xxx} ... is already registered. su virtualbox"
thesis_thumb:
  - http://blog.ilbonzo.org/wp-content/uploads/2012/02/Schermata-VirtualBox-Errore-UUID-150x150.png
thesis_thumb_frame:
  - on
dsq_thread_id:
  - 1097093098
categories:
  - linux
  - virtualizzazione
tags:
  - LPI
  - virtual box
---
Durante i corsi che tengo su Linux, sia [LPI][1] che non, mi avvalgo molto spesso dell&#8217;utilizzo di macchine virtuali. Ultimamente sto usando principalmente [VirtualBox][2], e spesso mi capita di dover spostare i dischi virtuali per esigenze di spazio.

Facendo ciò ci si trova molte volte davanti un errore che impedisce alla macchina di avviarsi dicendo:  
`<br />
A hard disk with UUID {xxx} ... is already registered.<br />
`

[<img src="http://magni.me/wp-content/uploads/2012/02/Schermata-VirtualBox-Errore-UUID-300x150.png" alt="" title="Schermata-VirtualBox-Errore-UUID" width="300" height="150" class="aligncenter size-medium wp-image-599" />][3]

Risolvere tale problema è molto semplice, basta una istruzione da riga di comando:  
`<br />
bonzo@wolverine:/media/virtual_machine/HardDisks$ VBoxManage internalcommands sethduuid centos_standard.vdi<br />
`

Dove centos_standard.vdi è il nome dell&#8217;hard disk virtuale.  
Il risultato è questo:  
`UUID changed to: dcfb9352-fea2-494b-a1ab-8c469e5f99b3`

Riprovando ad avviare la macchina l&#8217;errore non verrà più rivelato.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://blog.ilbonzo.org/2010/09/28/certificazione-linux-lpic-1-junior-admin/ "Certificazione Linux LPIC-1 junior admin"
 [2]: http://blog.ilbonzo.org/2007/05/24/virtualizzazione/ "Virtualizzazione"
 [3]: http://magni.me/wp-content/uploads/2012/02/Schermata-VirtualBox-Errore-UUID.png