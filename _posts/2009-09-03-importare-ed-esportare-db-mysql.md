---
title: Importare ed esportare db MySQL
author: Matteo Magni
layout: post
permalink: /2009/09/03/importare-ed-esportare-db-mysql/
dsq_thread_id:
  - 2645291508
categories:
  - Development
tags:
  - SQL
---
Per esportare un database Mysql:  
`mysqldump -u [user] -p  [database] > [database .sql]`

Per importare un database dal file creato precedentemente:  
`mysql -u [user] -p [database] < [database.sql]`</code>

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>