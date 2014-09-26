---
title: Gestione dei processi di Windows da command line
author: Matteo Magni
layout: post
permalink: /2013/07/05/gestione-dei-processi-di-windows-da-command-line/
thesis_title:
  - Gestione dei processi di Windows da command line
thesis_description:
  - 'Per fermare/gestire i processi su macchine windows attraverso la command line, in modo simile a come si fa su linux ecco alcuni comandi utili:'
pdrp_attributionLocation:
  - end
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/07/ps1.jpg
dsq_thread_id:
  - 1469537900
categories:
  - DevOps
  - windows
tags:
  - sysadmin
---
<p style="text-align: left;">
  <img class="size-thumbnail wp-image-896 aligncenter" alt="ps" src="http://magni.me/wp-content/uploads/2013/07/ps-150x150.jpg" width="150" height="150" /><br /> Ecco alcuni comandi utili per fermare/gestire i processi su macchine <strong>windows</strong> attraverso la command line, in modo simile a come si fa abitualmente su <em>linux</em>
</p>

*Ottenere la lista dei processi:*  
`<br />
tasklist /v<br />
`

*Fermare un processo in base al PID:*  
`<br />
taskkill /f /pid 1234<br />
`

*Fermare un processo in base al nome:*  
`<br />
taskkill /f /im java*<br />
`

L&#8217;opzione /f serve per forzare l&#8217;interruzione del processo.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>