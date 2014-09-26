---
title: Aggiornare mysql dalla versione 4 alla 5
author: Matteo Magni
layout: post
permalink: /2007/09/26/aggiornare-mysql-dalla-versione-4-alla-5/
dsq_thread_id:
  - 1103140252
categories:
  - linux
  - SQL
---
<p>Oggi ho dovuto aggiornare Mysql dalla versione 4 alla 5 e mysqlcheck mi diceva che le tabelle erano da aggiornare.</p>
<p>Ecco come risolvere il problema:</p>
<p><code>mysqlcheck --check-upgrade --all-databases --auto-repair<br />
mysql_fix_privilege_tables<br />
</code></p>
<p>Se volete dettagli trovate tutto sul sito di Mysql:<br />
<a href="http://dev.mysql.com/doc/refman/5.0/en/upgrading-from-4-1.html"></p>
<p>http://dev.mysql.com/doc..</a></p>
<p><a href="http://dev.mysql.com/doc/refman/5.0/en/mysql-upgrade.html"></p>
<p>http://dev.mysql.com/doc/refman/5.0/en/mysql-upgrade.html</a></p>
<p>Buon aggiornamento a tutti.</p>
<p>Gabba Gabba hey<br />
Bonzo</p>
<div class='kindleWidget kindleLight' ><img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span></div><a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>