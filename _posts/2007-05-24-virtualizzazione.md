---
title: Virtualizzazione
author: Matteo Magni
layout: post
permalink: /2007/05/24/virtualizzazione/
dsq_thread_id:
  - 1364147409
categories:
  - Networking
  - open source
  - virtualizzazione
---
Ultimamente ho avuto la fortuna di partecipare a un evento della Dell in tour in Italia.  
Durante questo evento è stato lasciata la parola ad alcuni Vendor che collaborano con Dell, in particolare mi ha colpito l&#8217;intervento fatto da [VMware][1] che ha illustrato i vantaggi della virtualizzazione in ambito server.  
Le cose dette effettivamente cambiano molto le carte in tavola, e la faccenda si fa molto interessante.  
In pratica, oggi si è abituati a usare un server fisico per ogni applicazione critica: posta, server web, ecc&#8230;  
Ciò porta ad uno sfruttamento dei server al massimo del 20%, con un evidente spreco di risorse.  
Con la virtualizzazione lo sfruttamento può arrivare fino al 70%.  
Come?  
Mettendo più macchine virtuali su un solo server fisico, rendendo la macchina fisica da eventuali blocchi della macchina virtuale.  
Tra le possibilità c&#8217;è quella di usare più macchine fisiche, esempio 3 su cui mettere 8 macchine virtuali, e in caso di problemi hardware spostare una macchina virtuale da una macchina fisica all&#8217;altra a caldo.![vmware][2]  
Ovviamente questo darebbe grossi miglioramenti in termini di prestazioni, sfruttamento delle risorse e costi.  
La cosa interessante è anche la [possibilità di spostare a caldo][3] una macchina virtuale da un server fisico ad un altro.

La tecnologia è in grande crescita e diventa d&#8217;obbligo cominciare a conoscerla.  
Queste le Alternative Open a VMware: [Xen][4], [OpenVZ][5], [VirtualBox][6].  
Ovviamente VMware avendo iniziato prima è molto più avanti, ma le cose si muovono in fretta, e sia Suse che Red Hat includono Xen nelle loro release Enterprise.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://www.vmware.com/
 [2]: http://magni.me/wp-content/uploads/2007/05/products_vmfs_diagram.jpg
 [3]: http://www.clever-consulting.it/05solutions/060706-VM-vmware_vmotion_drs_ha.html
 [4]: http://it.wikipedia.org/wiki/Xen
 [5]: http://openvz.org/
 [6]: http://www.virtualbox.org/