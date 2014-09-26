---
title: CakePHP, installazione
author: Matteo Magni
layout: post
permalink: /2008/01/28/cakephp-installazione/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1098337772
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - cakePHP
  - PHP
---
Visto che conosco e lavoro soprattutto con PHP ma mi affascina molto <a href="http://www.rubyonrails.org/" class="Tips3" title="Framework ruby">Ruby on Rails</a> ho deciso di provare <a href="http://cakephp.org" class="Tips3" title="framework PHP">CakePHP</a>, framework web PHP da molti paragonato al celebre framework scritto in Ruby.

![cakePHP][1]

### Installazione di cakePHP:

<a href="http://manual.cakephp.org/chapter/installing" class="Tips3" title="Manuale cakePHP">Manuale cakePHP</a>

**Requisiti:**

*   An HTTP server (like Apache) with the following enabled: sessions, mod_rewrite (not absolutely necessary but preferred)
*   PHP 4.3.2 or greater. Yes, CakePHP works great in either PHP 4 or 5.
*   A database engine (right now, there is support for MySQL 4+, PostgreSQL and a wrapper for ADODB).

Userò Apache, PHP 5 e MySQL.

**Scaricare la versione stabile e scompattarla**

<a href="http://cakeforge.org/frs/?group_id=23&#038;release_id=371" class="Tips3" title="cakePHP stable release">cake_1.1.19.6305.tar.gz</a>

Esistono due tipi di configurazione per lo sviluppo e per la produzione.

**Produzione**  
In ambiente di produzione è meglio installare CakePHP in una directory indipendente configurando poi il Web server in modo che la cartella di root corrisponda a /path/di/cakephp/app/webroot.

**Sviluppo**  
In ambiente di sviluppo è sufficiente scompattare i sorgenti nella directory di root, all&#8217;interno della directory cake.

Io utilizzerò la configurazione per lo sviluppo.

**Schema applicazione**  
/app  
&nbsp;&nbsp;&nbsp;/config  
&nbsp;&nbsp;&nbsp;/controllers  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/components  
&nbsp;&nbsp;&nbsp;/models  
&nbsp;&nbsp;&nbsp;/plugins  
&nbsp;&nbsp;&nbsp;/tmp  
&nbsp;&nbsp;&nbsp;/vendors  
&nbsp;&nbsp;&nbsp;/views  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/elements  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/errors  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/helpers  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/layouts  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/pages  
&nbsp;&nbsp;&nbsp;/webroot  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/css  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/files  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/img  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/js  
&nbsp;&nbsp;&nbsp;/index.php  
/cake  
/docs  
/vendors  
/index.php

**Configurazione Apache**  
attivo il modulo mod_rewrite ed ed utilizzo il file .htaccess fornito all&#8217;interno dell&#8217;installazione standard per poter utilizzare URL puliti e chiari da leggere che non facciano uso di query string.  
<a href="http://server.html.it/articoli/leggi/2033/riscrivere-gli-url-con-il-modulo-modrewrite-di-apa/" class="Tips3" title="configurare mod_rewrite">riscrivere gli url con il modulo modrewrite di apache</a>

**Configurazione database**  
E&#8217; necessario configurare l&#8217;accesso al database. Per fare questo bisogna modificare il file app/config/database.php.default e rinominarlo in database.php, modificando i valori dell&#8217;array $default.  
`<br />
var $default = array('driver'   => 'mysql',<br />
                     'connect'  => 'mysql_connect',<br />
                     'host'     => 'localhost',<br />
                     'login'    => 'user',<br />
                     'password' => 'password',<br />
                     'database' => 'project_name',<br />
                     'prefix'   => '');<br />
`

Creo il database cake

Se vado a http://localhost/cake vedo:

> CakePHP Rapid Development
> 
> Your database configuration file is present.
> 
> Cake is able to connect to the database.
> 
> CakePHP release information is on CakeForge  
> Read the release notes and get the latest version  
> Editing this Page
> 
> To change the content of this page, create: /app/views/pages/home.thtml.  
> To change its layout, create: /app/views/layouts/default.thtml.  
> See the views section of the manual for more info  
> You can also add some CSS styles for your pages at: app/webroot/css/. 

Ora sono pronto per scrivere la mia prima applicazione con CakePHP.

Gabba gabba hey  
Bonzo

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://magni.me/wp-content/uploads/2008/01/cake-logo.png