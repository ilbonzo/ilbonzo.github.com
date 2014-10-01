---
title: Aggiornare il fork di un repository github dal repository originale
author: Matteo Magni
layout: post
permalink: /2013/08/09/aggiornare-il-fork-di-un-repository-github-dal-repository-originale/
thesis_title:
  - Aggiornare il fork di un repository github dal repository originale
thesis_description:
  - 'Se abbiamo fatto un fork di un repository su github e vogliamo aggiornare il nostro repo con le modifiche fatte anche sul repo originale dobbiamo eseguire le seguenti operazioni:'
thesis_keywords:
  - git, github. fork, repository, code
pdrp_attributionLocation:
  - end
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/08/fork2.png
dsq_thread_id:
  - 1587618112
categories:
  - Development
tags:
  - git
  - github
---
<p style="text-align: left;">
  <img class="size-medium wp-image-907 aligncenter" alt="fork" src="http://magni.me/wp-content/uploads/2013/08/fork-300x165.png" width="300" height="165" /><br /> Se abbiamo fatto un fork di un repository su <a href="https://github.com/ilbonzo">github</a> e vogliamo aggiornare il nostro repo con le modifiche fatte anche sul repo originale dobbiamo eseguire le seguenti operazioni:
</p>

*Aggiungiamo l&#8217;url del repository originale nei remote*  
`<br />
$ git remote add --track master openovate https://github.com/Openovate/eden.git<br />
`

*Verifichiamo che il repo sia stato aggiunto*  
`<br />
$ git remote<br />
`

*Eseguiamo il fetch del repository originale, questo creerà un branch chiamato openovate/master*  
`<br />
$ git fetch openovate<br />
`

*Eseguiamo il merge con il nostro master*  
`<br />
$ git merge openovate/master<br />
`

*Mandiamo al nostro origin le nuove modifiche*  
`<br />
$ git push origin master<br />
`

<div class='kindleWidget kindleLight' >
  
</div>

