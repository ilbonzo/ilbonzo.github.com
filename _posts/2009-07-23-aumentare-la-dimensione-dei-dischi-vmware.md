---
title: Aumentare la dimensione dei dischi VMware
author: ilbonzo
layout: post
permalink: /2009/07/23/aumentare-la-dimensione-dei-dischi-vmware/
dsq_thread_id:
  - 1097401487
categories:
  - virtualizzazione
tags:
  - VMware
---
A volte capita di dover aumentare le dimensioni di un disco VMware, perché quando lo si è creato si è stati troppo tirchi nel dedicare spazio alla macchina virtuale.  
VMware server mette a disposizione un comando per ridimensionare i file vmdk

in Linux:  
`vmware-vdiskmanager -x sizeGB file.vmdk`  
In Windows:  
`C:Program FilesVMwareVMware Server> vmware-vdiskmanager -x 15GB "C:virtual_machinesdebiandebian.vmdk"`

Ora ovviamente la macchina virtuale vedrà lo spazio aggiunto come spazio libero, quindi dovrete modificare lo schema delle partizioni per consentire al sistema operativo di potere usare lo spazio aggiuntivo.

I metodi possono essere vari, uno su tutti usare un livecd linux con gparted o simili per aggiungere o modificare le partizioni sul disco VMware.

Fatto ciò avrete disponibile tutto il nuovo spazio.

<div class='kindleWidget kindleLight' >
  
</div>

