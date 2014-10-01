---
title: Migrare un repository da Svn a Git mantenendone la history dei commit
author: Matteo Magni
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
---
<img src="http://magni.me/wp-content/uploads/2013/05/img0372-300x225.jpg" alt="IMG_0372" width="300" height="225" class="alignleft size-medium wp-image-795" /> Nel caso si voglia portare un repository [**svn**][1] su [**git**][2] mantenendone la history dei vari commit si può seguire questa procedura.  
  
  
  
  
  
  
<!--more-->

  
**Installare git svn:**  
`<br />
$ sudo aptitude install git-svn<br />
`

**Importare il *trunk***

1.  Clonare con git il repo svn:  
    `<br />
$ git svn clone -s http://url.com/myrepos<br />
`  
    L&#8217;opzione -s va usata per specificare che il repo svn ha la struttura [trunk/branches/tags]</p> 
2.  Creare il repository git remoto (per esempio su [bitbucket][3] o [github][4]).  
      
    
3.  Aggiungere il repository remoto:  
    `<br />
$ git remote add origin https://ilbonzo@bitbucket.org/ilbonzo/myrepos.git<br />
`</p> 
4.  Fare push di tutto su origin:  
    `<br />
$ git push -u --all origin<br />
`</p> 

**Gestione dei *branches*:**

1.  Lista dei branches importati da svn  
    `<br />
$ git branch -r<br />
FirstBranch<br />
SecondBranch<br />
`</p> 
2.  Diciamo a git di tenere traccia di quei branch  
    `<br />
$ git branch --track FirstBranch<br />
$ git branch --track SecondBranch<br />
`</p> 
3.  Inviamo i branch sul repo remoto  
    `<br />
$ git push -u --all origin<br />
` 

Finalmente il nostro codice è su **git** con tutti i vantaggi del caso.

<div id="pdrp_endAttribution">
  photo by: <a href="http://flickr.com/41894185093@N01/16372763" target="_blank" class="pdrp_link pdrp_attributionLink"> Jon_Aquino</a>
</div>

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://it.wikipedia.org/wiki/Subversion
 [2]: http://it.wikipedia.org/wiki/Git_(software)
 [3]: http://bitbucket.org/ilbonzo
 [4]: http://github.com/ilbonzo