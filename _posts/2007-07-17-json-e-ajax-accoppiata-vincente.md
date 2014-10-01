---
title: Json e Ajax accoppiata vincente
author: ilbonzo
layout: post
permalink: /2007/07/17/json-e-ajax-accoppiata-vincente/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1102523915
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - ajax
  - Javascript
  - PHP
---
[Json][1] è un formato di testo indipendente dal linguaggio che usa convenzioni simili a quelle della famiglia dei linguaggi C.

Si basa su due strutture di dati supportate praticamente da tutti i linguaggi di programmazione moderni:

• una raccolta di coppie nome/valore [oggetti, record, dizionari...]  
• una raccolta ordinata di valori [array...]

Inoltre Json è basato su un sottoinsieme di Javascript Standard, quindi non ci dovrebbero essere problemi di compatibilità con i vari browser.

**  
Oggetto json**  
insieme ordinato di coppie nome/valore. inizia e termina con una parentesi graffa{};  
**  
Array Json**  
raccolta ordinata di valori che inizia e termina con le parentesi quadre [];  
**  
Valore Json**  
Vengono separati da una virgola e possono essere: Stringa, numero, true e false, oggetto, array, null

In particolare il vanto di Json è di essere un formato di scambio molto più leggero di xml.  
**  
*Esempio di utilizzo Json  
***

File Json[  
json.js][2]

File html con i form da cui far partire il nostro esempio  
[  
json_first.html][3]

`function doJSON() {<br />
    var user = getUserObject();<br />
    var userAsJSON = JSON.stringify(user);<br />
    alert("ecco l'oggetto User di Json :n " + userAsJSON);<br />
    var url = "json_first.php?timeStamp=" + new Date().getTime();<br />
    var postVar= 'user_data='+encodeURIComponent(userAsJSON);<br />
    createXMLHttpRequest();<br />
    xmlHttp.open("POST", url, true);<br />
    xmlHttp.onreadystatechange = handleStateChange;<br />
    xmlHttp.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");<br />
    xmlHttp.send(postVar);<br />
}`  
La funzione crea un oggetto User con i valori della form,  
`<br />
function getUserObject() {<br />
    return new User(document.dati.username.value, document.dati.mail.value);<br />
}<br />
function User(username, mail) {<br />
    this.username = username;<br />
    this.mail = mail;<br />
}`

e lo invia via Post in formato Json al server sotto forma d querystring:

Ecco il post della pagina:

user_data {&#8220;username&#8221;:&#8221;bonzo&#8221;,&#8221;mail&#8221;:&#8221;ilbonzo.org@gmail.com&#8221;}

La pagina php processa i dati e li rimanda alla prima pagina

json_first.php

`$jsonString= stripslashes($_POST['user_data']);<br />
var_dump(json_decode($jsonString));<br />
$jsonPost=json_decode($jsonString);<br />
echo 'username: ';<br />
echo $jsonPost->username;<br />
echo ' mail: ';<br />
echo $jsonPost->mail;`

L&#8217;esempio è molto semplice, ma serve solo per capire le potenzialità di Json e Ajax.  
[Scarica esempio][4]

*Nota:  
*Json su PHP si può usare dalla versione 5.2, prima serviva il repository PECL.

Gabba Gabba Hey

Bonzo

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://www.json.org
 [2]: http://blog.ilbonzo.org/upload/ajax/json.js
 [3]: http://blog.ilbonzo.org/upload/ajax/json_first.html
 [4]: http://blog.ilbonzo.org/upload/ajax/json.zip