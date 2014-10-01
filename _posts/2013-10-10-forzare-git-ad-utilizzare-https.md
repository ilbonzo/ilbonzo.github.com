---
title: Forzare git ad utilizzare https
author: ilbonzo
layout: post
permalink: /2013/10/10/forzare-git-ad-utilizzare-https/
thesis_title:
  - Forzare git ad utilizzare https
thesis_description:
  - Forzare git ad utilizzare https
thesis_keywords:
  - git, github
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/05/github.png
pdrp_attributionLocation:
  - end
dsq_thread_id:
  - 1842128302
categories:
  - Development
tags:
  - git
  - github
  - tips
comments: true
share: true
---
Nel caso si voglia forzare git ad utilizzare sempre la connessione https, quando utilizza <a href="http://github.com/ilbonzo" target="_blank">github</a>, possiamo impostarlo attraverso questo comando.

<pre class="lang:sh decode:true " title="Forzare git ad usare https" >git config --global url.https://github.com/.insteadOf git://github.com/</pre>

<div class='kindleWidget kindleLight' >

</div>
