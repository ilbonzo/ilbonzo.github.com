---
title: Sapere su che distro si sta lavorando
author: ilbonzo
layout: post
permalink: /2007/08/10/sapere-su-che-distro-si-sta-lavorando/
categories:
  - Development
comments: true
share: true
---
Capita a volte di non sapere su che distribuzione si sta lavorando, e di non avere a disposizione nessuno che sappia rispondere alla domanda.  
Ecco un comodo comando shell per visualizzare i dati della Release Linux:

esempi:  
`<br />
# lsb_release -a<br />
No LSB modules are available.<br />
Distributor ID: Ubuntu<br />
Description:    Ubuntu 6.06.1 LTS<br />
Release:        6.06<br />
Codename:       dapper<br />
`  
`<br />
$ lsb_release -a<br />
LSB Version:    lsb-3.1-ia32:lsb-3.1-noarch:*<br />
Distributor ID: MandrivaLinux<br />
Description:    Mandriva Linux<br />
Release:        2007.1<br />
Codename:       Official<br />
`

Per poter dare il comando ovviamente bisogna avere i privilegi di root.  
L&#8217;opzione -a visualizza tutte le informazioni, ce ne sono altre per avere risposta solo su alcuni dati.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >

</div>
