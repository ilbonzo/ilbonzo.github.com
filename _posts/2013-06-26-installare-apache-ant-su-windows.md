---
title: Installare Apache Ant su Windows
author: ilbonzo
layout: post
permalink: /2013/06/26/installare-apache-ant-su-windows/
thesis_title:
  - Installare Apache Ant su Windows
thesis_description:
  - Per lo sviluppo su Android viene utilizzato Ant, ecco come installarlo su windows
thesis_keywords:
  - apache, ant, java, android, windows
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/06/project-logo.gif
pdrp_attributionLocation:
  - end
dsq_thread_id:
  - 1437737898
categories:
  - Development
  - windows
tags:
  - Android
  - Ant
  - Java
comments: true
share: true
---
<img src="http://magni.me/wp-content/uploads/2013/06/554px-Apache-Ant-logo.svg_-300x185.png" alt="554px-Apache-Ant-logo.svg" width="300" height="185" class="aligncenter size-medium wp-image-886" />  
**[Apache Ant][1]** è un software molto utile per lo sviluppo in *Java*:

> Apache Ant è un software per l&#8217;automazione del processo di build. È simile a make ma scritto in Java ed è principalmente orientato allo sviluppo Java. Ant è un progetto Apache, open source, ed è rilasciato sotto licenza Apache.

Per lo sviluppo su *Android* per esempio viene utilizzato Ant per gestire la build, ecco come installarlo su *Windows*:  
<!--more-->

1.  Installare il Java Development Kit <http://www.oracle.com/technetwork/java/javase/downloads/index.html>
2.  Aggiungere la variabile di ambiente JAVA_HOME, ad esempio 

    C:\Program Files\Java\jdk1.7.0_25

3.  Aggiungere la variabile alla variabile di Ambiente PATH il percorso dei binari 
    
    %JAVA_HOME%\bin

4.  Sacricare **ANT** in versione binaria <http://ant.apache.org/bindownload.cgi>
5.  Estrarre lo zip in una cartella, esempio 
    
    C:\Ant

6.  Impostare la variabile di ambiente ANT_HOME inserendo il percorso dove abbiamo scompattato **ANT**, esempio        
    C:\Ant

7.  A questo punto per verificare che sia tutto ok apriamo una riga di comando e diamo il comando ant -version:

    C:\Users\magnim>ant -version
    
    Apache Ant(TM) version 1.9.1 compiled on May 15 2013

Se l'output non da errori vuol dire che Ant è installato correttamente.


 [1]: http://ant.apache.org/ "apache Ant"
