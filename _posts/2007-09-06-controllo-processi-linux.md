---
title: Controllo processi Linux
author: ilbonzo
layout: post
permalink: /2007/09/06/controllo-processi-linux/
dsq_thread_id:
  - 1876164506
categories:
  - linux
---
Un processo è un programma in esecuzione.  
Ogni processo sul sistema ha un ID di processo (PID) numerico. Per avere un elenco dei processi si usa il comando ps.

**ps**  
`colosso:~# ps<br />
  PID TTY          TIME CMD<br />
 3857 pts/1    00:00:00 bash<br />
 3863 pts/1    00:00:00 ps<br />
colosso:~# `

*   PID ID del processo
*   TTY la periferica di terminale in cui il processo è in esecuzione
*   STAT Stato del processo, ciò che il processo sta facendo e dove risiede la sua memoria.
*   TIME La quantità di tempo della CPU (minuti e secondi) che il processo ha utilizzato fino a quel momento.
*   COMMAND 

**  
ps ax **  
Tutti i processi, non solo quelli in esecuzione.  
`<br />
colosso:~# ps ax<br />
  PID TTY      STAT   TIME COMMAND<br />
    1 ?        Ss     0:02 init [2]<br />
    2 ?        S      0:00 [migration/0]<br />
    3 ?        SN     0:00 [ksoftirqd/0]<br />
    4 ?        S<     0:00 [events/0]<br />
    5 ?        S<     0:00 [khelper]<br />
    6 ?        S<     0:00 [kthread]<br />
    9 ?        S<     0:00 [kblockd/0]<br />
 ....<br />
 3838 ?        Ss     0:00 /usr/sbin/sshd<br />
 3853 ?        Ss     0:00 sshd: root@pts/1<br />
 3857 pts/1    Ss     0:00 -bash<br />
 3987 pts/1    R+     0:00 ps ax`

**  
ps u**  
ci da le caratteristice dei processi

`colosso:~# ps u<br />
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND<br />
root      3064  0.1  2.3  18384 11904 tty7     Ss+  08:54   0:06 /usr/bin/X :0 -dpi 96 -audit<br />
root      3208  0.0  0.0   1576   496 tty1     Ss+  08:54   0:00 /sbin/getty 38400 tty1<br />
root      3209  0.0  0.0   1576   496 tty2     Ss+  08:54   0:00 /sbin/getty 38400 tty2<br />
root      3210  0.0  0.0   1576   496 tty3     Ss+  08:54   0:00 /sbin/getty 38400 tty3<br />
root      3211  0.0  0.0   1576   496 tty4     Ss+  08:54   0:00 /sbin/getty 38400 tty4<br />
root      3212  0.0  0.0   1572   492 tty5     Ss+  08:54   0:00 /sbin/getty 38400 tty5<br />
root      3213  0.0  0.0   1576   496 tty6     Ss+  08:54   0:00 /sbin/getty 38400 tty6<br />
root      3696  0.0  0.2   3716  1080 pts/0    S    10:08   0:00 su<br />
root      3697  0.0  0.3   3960  1656 pts/0    S+   10:08   0:00 bash<br />
root      3857  0.0  0.3   3952  1652 pts/1    Ss   10:10   0:00 -bash<br />
root      4060  0.0  0.1   3424   980 pts/1    R+   10:19   0:00 ps u<br />
colosso:~#<br />
`  
se li combiniamo:  
`colosso:~# ps aux<br />
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND<br />
root         1  0.0  0.1   1940   644 ?        Ss   08:53   0:02 init [2]<br />
root         2  0.0  0.0      0     0 ?        S    08:53   0:00 [migration/0]<br />
root         3  0.0  0.0      0     0 ?        SN   08:53   0:00 [ksoftirqd/0]<br />
root         4  0.0  0.0      0     0 ?        S<   08:53   0:00 [events/0]<br />
root         5  0.0  0.0      0     0 ?        S<   08:53   0:00 [khelper]<br />
root         6  0.0  0.0      0     0 ?        S<   08:53   0:00 [kthread]<br />
root         9  0.0  0.0      0     0 ?        S<   08:53   0:00 [kblockd/0]<br />
...<br />
bonzo     3672  0.0  0.1   2480   780 ?        S    10:08   0:00 gnome-pty-helper<br />
bonzo     3673  0.0  0.6   5680  3204 pts/0    Ss   10:08   0:00 bash<br />
root      3696  0.0  0.2   3716  1080 pts/0    S    10:08   0:00 su<br />
root      3697  0.0  0.3   3960  1656 pts/0    S+   10:08   0:00 bash<br />
root      3838  0.0  0.2   4924  1088 ?        Ss   10:09   0:00 /usr/sbin/sshd<br />
root      3853  0.0  0.4   7716  2340 ?        Rs   10:10   0:00 sshd: root@pts/1<br />
root      3857  0.0  0.3   3952  1652 pts/1    Ss   10:10   0:00 -bash<br />
root      4077  0.0  0.1   3424   980 pts/1    R+   10:20   0:00 ps aux<br />
`

Il risultato dell'istruzione può essere particolarmente lungo, in questo caso potremo utilizzare un ulteriore argomento,  
**|more**, per impaginare l'output prodotto:  
**ps ax | less**

E' inoltre possibile sapere se un determinato processo è in esecuzione grazie all'utilizzo incrociato di ps e grep:**  
ps ax | grep bash**

`colosso:~# ps ax | grep bash<br />
 3673 pts/0    Ss     0:00 bash<br />
 3697 pts/0    S+     0:00 bash<br />
 3857 pts/1    Ss     0:00 -bash<br />
 4123 pts/1    S+     0:00 grep bash<br />
colosso:~#<br />
`  
ps produce un'immagine statica dei processi in corso, in pratica fotografa lo stato del sistema al momento in cui viene lanciata l'istruzione di monitoraggio delle esecuzioni.  
**  
top**  
Se si desidera ottenere un output più particolareggiato, dinamico e aggiornabile sarà necessario utilizzare il comando top; l'output di top consente di visualizzare tutti processi correnti e le relative informazioni rilevanti come per esempio il carico sulla CPU.  
Il programma top visualizza lo stato corrente del sistema e molti campi che potreste vedere in un listato ps, ma aggiorna anche la visualizzazione ogni secondo.  
`<br />
colosso:~# top<br />
top - 10:26:43 up  1:33,  3 users,  load average: 0.00, 0.00, 0.01<br />
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie<br />
Cpu(s):  1.0%us,  0.7%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st<br />
Mem:    516876k total,   496928k used,    19948k free,    80100k buffers<br />
Swap:   498004k total,        0k used,   498004k free,   202788k cached</p>
<p>  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND<br />
 3632 bonzo     16   0 38200 7904 6464 S  1.0  1.5   0:05.25 gnome-cups-icon --sm-client-id default3<br />
 4196 root      15   0  2224 1168  860 R  1.0  0.2   0:00.50 top<br />
    1 root      15   0  1940  644  552 S  0.0  0.1   0:02.27 init [2]<br />
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [migration/0]<br />
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 [ksoftirqd/0]<br />
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 [events/0]<br />
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [khelper]<br />
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 [kthread]<br />
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 [kblockd/0]<br />
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpid]<br />
 ...<br />
 2461 root      15   0  1580  380  308 S  0.0  0.1   0:00.00 /sbin/klogd -x<br />
 2497 root      24   0  4884  916  672 S  0.0  0.2   0:00.00 /usr/sbin/hpiod<br />
 2500 hplip     15   0  9688 4876 1108 S  0.0  0.9   0:00.05 python /usr/sbin/hpssd<br />
`

Per usare bene top abbiamo una serie di utili opzioni che si usano premendo sulla voce corrispondente nella tastiera:

* k: ferma un processo.  
* n: mostra il numero dei processi visualizzati sulla base di una cifra specificata dall'utente.  
* u: ordina l'output per utente.  
* P: ordina per quantità di CPU utilizzata.  
* M: ordina per quantità di memoria impiegata.  
* Barra spaziatrice: aggiorna l'output.

Buon controllo a tutti  
Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>

