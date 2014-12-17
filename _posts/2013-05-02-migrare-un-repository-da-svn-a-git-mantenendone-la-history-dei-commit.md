---
title: Migrare un repository da Svn a Git mantenendone la history dei commit
author: ilbonzo
layout: post
permalink: /2013/05/02/migrare-un-repository-da-svn-a-git-mantenendone-la-history-dei-commit/
pdrp_attributionLocation:
  - end
thesis_title:
  - Migrare un repository da Svn a Git mantenendone la history dei commit
thesis_description:
  - Nel caso si voglia portare un repository svn su git mantenendone la history dei vari commit si può seguire questa procedura.
thesis_keywords:
  - subversion, git, bitbucket, sourceforge, github
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/05/github.png
dsq_thread_id:
  - 1256127935
categories:
  - Development
tags:
  - git
  - subversion
comments: true
share: true
---
<img src="http://magni.me/wp-content/uploads/2013/05/img0372-300x225.jpg" alt="IMG_0372" width="300" height="225" class="alignleft size-medium wp-image-795" /> 

Nel caso si voglia portare un repository [**svn**][1] su [**git**][2] mantenendone la history dei vari commit si può seguire questa procedura.  

**Installare git svn:**  

    $ sudo aptitude install git-svn


**Importare il *trunk***

Clonare con git il repo svn:  

    $ git svn clone -s http://url.com/myrepos
    
L'opzione -s va usata per specificare che il repo svn ha la struttura [trunk/branches/tags]

Creare il repository git remoto (per esempio su [bitbucket][3] o [github][4]).  

Aggiungere il repository remoto:  

    $ git remote add origin https://ilbonzo@bitbucket.org/ilbonzo/myrepos.git

Fare push di tutto su origin:  

    $ git push -u --all origin

**Gestione dei *branches*:**

Lista dei branches importati da svn  

    $ git branch -r
    FirstBranch
    SecondBranch
  
Diciamo a git di tenere traccia di quei branch  

    $ git branch --track FirstBranch
    $ git branch --track SecondBranch

Inviamo i branch sul repo remoto  

    $ git push -u --all origin

Finalmente il nostro codice è su **git** con tutti i vantaggi del caso.

<div id="pdrp_endAttribution">
  photo by: <a href="http://flickr.com/41894185093@N01/16372763" target="_blank" class="pdrp_link pdrp_attributionLink"> Jon_Aquino</a>
</div>

 [1]: http://it.wikipedia.org/wiki/Subversion
 [2]: http://it.wikipedia.org/wiki/Git_(software)
 [3]: http://bitbucket.org/ilbonzo
 [4]: http://github.com/ilbonzo
