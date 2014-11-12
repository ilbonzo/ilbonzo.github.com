---
title: Reimpostare la password di root in Mysql
author: ilbonzo
layout: post
permalink: /2013/06/20/reimpostare-la-password-dellutente-root-in-mysql/
thesis_title:
  - "Reimpostare la password dell'utente root in Mysql"
pdrp_attributionLocation:
  - end
thesis_description:
  - |
    Nel caso si voglia reimpostare la password dell'utente root di <strong><a href="http://www.mysql.com/" title="MySQL">Mysql Server</a></strong> abbiamo due metodi:
    Se ci fossimo dimenticati la password di root precedentemente impostata la procedura da seguire è questa...
thesis_keywords:
  - MySQL, Linux, Database, SQL
dsq_thread_id:
  - 1414307854
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/06/database_3.png
categories:
  - SQL
tags:
  - MySQL
comments: true
share: true
---
<p style="text-align: center;">
  <a href="http://magni.me/wp-content/uploads/2013/06/mysql_logo.png"><img class="size-medium wp-image-844 aligncenter" alt="mysql_logo" src="http://magni.me/wp-content/uploads/2013/06/mysql_logo-300x155.png" width="300" height="155" /></a>
</p>

Nel caso si voglia reimpostare la password dell&#8217;utente root di **[Mysql Server][1]** abbiamo due metodi:

**Primo metodo**  
`mysqladmin -u root -p password secret`

*secret* sarà la nostra nuova password.  
Per fare la modifica ci verrà però chiesta l&#8217;attuale password di root, quindi è necessario conoscerla.

**Secondo metodo**  
Se ci fossimo dimenticati la password di root precedentemente impostata, la procedura da seguire è invece questa:  
<!--more-->


Prima di tutto dobbiamo fermare il servizio *mysql*.  
`service mysqld stop`

Ora dobbiamo avviare il servizio, disabilitando i sistemi di autenticazione  
`mysqld --skip-grant-tables &`

Aggiungendo l&#8217;opzione &#8211;skip-networking possiamo disabilitare l&#8217;accesso da remoto per evitare che qualcuno sfrutti questa temporanea apertura.  
`mysqld --skip-grant-tables --skip-networking &`

Ora possiamo accedere a Mysql senza password:  
`mysql -u root mysql`

Entrati nella shell di mysql settiamo la nuova password di root:  
`UPDATE user SET password=PASSWORD("newpassword") WHERE User='root';`

`FLUSH PRIVILEGES;`

`exit;`

Ora riavviamo il processo mysql ed avremo la possibilità di accedere con la nuova password  
`service mysqld restart`


 [1]: http://www.mysql.com/ "MySQL"
