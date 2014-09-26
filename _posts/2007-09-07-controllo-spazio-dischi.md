---
title: Controllo spazio dischi
author: Matteo Magni
layout: post
permalink: /2007/09/07/controllo-spazio-dischi/
dsq_thread_id:
  - 1592009365
categories:
  - linux
---
Per effettuare il controllo dello spazio sui dischi da shell:

**df**  
Il comando df visualizza a schermo lo spazio rimasto sulle partizioni e sui dischi del proprio sistema.  
`<br />
bonzo@parker:~$ df<br />
Filesystem        blocchi di   1K   Usati Disponib. Uso% Montato su<br />
/dev/hda4             28834744   3395584  23974436  13% /<br />
tmpfs                   648288         0    648288   0% /lib/init/rw<br />
udev                     10240       152     10088   2% /dev<br />
tmpfs                   648288         0    648288   0% /dev/shm<br />
/dev/hda6             72090684    265504  68163168   1% /home<br />
bonzo@parker:~$ `

*   Filesystem: periferica filesystem;
*   Blocchi di 1K: capacità totale del file system in blocchi da 1 k;
*   Usati: blocchi occupati;
*   Disponibili: blocchi liberi;
*   Uso %: percentuale di blocchi utilizzati;
*   Montato su: punto di montaggio.

Opzioni:

**a** include nell’elenco anche i filesystem con una dimensione di 0 blocchi, che sono di natura omessi.  
`<br />
bonzo@parker:~$ df -a<br />
Filesystem        blocchi di   1K   Usati Disponib. Uso% Montato su<br />
/dev/hda4             28834744   3395584  23974436  13% /<br />
tmpfs                   648288         0    648288   0% /lib/init/rw<br />
proc                         0         0         0   -  /proc<br />
sysfs                        0         0         0   -  /sys<br />
procbususb                   0         0         0   -  /proc/bus/usb<br />
udev                     10240       152     10088   2% /dev<br />
tmpfs                   648288         0    648288   0% /dev/shm<br />
devpts                       0         0         0   -  /dev/pts<br />
/dev/hda6             72090684    265504  68163168   1% /home<br />
bonzo@parker:~$ `

**h** Aggiunge a ciascuna dimensione un suffisso, come M per megabyte, G per gigabyte..

`bonzo@parker:~$ df -h<br />
Filesystem         Dimens. Usati Disp. Uso% Montato su<br />
/dev/hda4              28G  3,3G   23G  13% /<br />
tmpfs                 634M     0  634M   0% /lib/init/rw<br />
udev                   10M  152K  9,9M   2% /dev<br />
tmpfs                 634M     0  634M   0% /dev/shm<br />
/dev/hda6              69G  260M   66G   1% /home<br />
bonzo@parker:~$ `

**t** tipofs Limita l’elenco a filesystem del tipo specificato

**x** tipofs Limita l’elenco a filesystem non del tipo specificato 

Buon controllo a tutti

Gabba Gabba hey  
Bonzo

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>