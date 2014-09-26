---
title: Ajax, comunicare con il server
author: Matteo Magni
layout: post
permalink: /2007/06/19/ajax-comunicare-con-il-server/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1103923984
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - ajax
  - Javascript
  - PHP
---
Continuo il mio viaggio nello studio di Ajax.  
Oggi ho guardato come comunicare con il server, via GET o POST, ottenendo il risultato senza dover ricaricare la pagina dando all&#8217;applicazione un forte effetto web 2.0.

L&#8217;esempio è fatto di una pagina [getpost.html][1] nella quale c&#8217;è un form in cui inserire il nome ed il cognome. Dopo di ciò facendo click su invia i parametri con GET si vedrà il risultato della pagina get.php nella parte Risposta Server senza avere un ricaricamento della pagina.La stessa cosa si ottiene con Invia i parametri via POST, con la differenza che questa volta il colloquio con il server avverrà via POST.

Vediamo un attimo il codice Javascript:

Il bottone GET chiama la funzione *doRequestUsingGET()*;  
`<br />
function doRequestUsingGET()<br />
{<br />
    createXMLHttpRequest();<br />
    var queryString = "get.php?";<br />
    queryString = queryString + createQueryString()<br />
        + "&#038;timeStamp=" + new Date().getTime();<br />
    xmlHttp.onreadystatechange = handleStateChange;<br />
    xmlHttp.open("GET", queryString, true);<br />
    xmlHttp.send(null);<br />
}<br />
`

La funzione crea un oggetto XMLHttpRequest, poi costruisce la stringa della Chiamata GET con i valori inseriti dall&#8217;utente utilizzando la funzione *createQueryString()*:

`<br />
function createQueryString()<br />
{<br />
    var nome = document.getElementById("nome").value;<br />
    var cognome = document.getElementById("cognome").value;<br />
    var queryString = "nome=" + nome + "&#038;cognome=" + cognome;<br />
    return queryString;<br />
}<br />
`

Si continua impostando la proprietà *onreadystatechange* dell&#8217;oggetto XMLHttpRequest per l&#8217;uo della funzione *handleStateChange*. il metodo *open()* dice che la richiestà è di tipo GET, l&#8217;URL della richiesta con i valori e il metodo *send()* invia la richiesta al server. La risposta sarà gestita dalla funzione *handleStateChange*:

`<br />
function handleStateChange()<br />
{<br />
    if(xmlHttp.readyState == 4)<br />
{<br />
        if(xmlHttp.status == 200)<br />
{<br />
            parseResults();<br />
        }<br />
    }<br />
}<br />
`

Quest&#8217;ultima chiama la funzione *parseResult()*:

`function parseResults()<br />
{<br />
    var responseDiv = document.getElementById("rispostaServer");<br />
    if(responseDiv.hasChildNodes())<br />
{<br />
        responseDiv.removeChild(responseDiv.childNodes[0]);<br />
    }<br />
    var responseText = document.createTextNode(xmlHttp.responseText);<br />
    responseDiv.appendChild(responseText);<br />
}`

Tale funzione usando il DOM rimuove i risultati precedenti del server dal DIV &#8220;rispostaServer&#8221; e ci va a mettere quelli nuovi.

Se invece si effettua tutto via POST, la differenza sta nella modalità in cui si inviano i parametri al server.

`<br />
function doRequestUsingPOST()<br />
{<br />
    createXMLHttpRequest();<br />
    var url = "post.php";<br />
    var queryString = createQueryString();<br />
    xmlHttp.open("POST", url, true);<br />
    xmlHttp.onreadystatechange = handleStateChange;<br />
    xmlHttp.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");<br />
    xmlHttp.send(queryString);<br />
}<br />
`  
La differenza è che i parametri andranno cercati all&#8217;interno del corpo della richiesta e non nell&#8217;url.  
Per questo si usa il metodo *setRequestHeader()*, per dire al server che cerchi li i parametri.

Per completezza metto pure il codice delle pagine PHP:

*get.php  
*  
`<br />
echo 'Ciao';<br />
echo ' Il tuo nome è: '.$_GET['nome'];<br />
echo ', il tuo cognome è: '.$_GET['cognome'];<br />
echo ' [Metodo GET]';<br />
`

*post.php*  
`<br />
echo 'Ciao';<br />
echo ' Il tuo nome è: '.$_POST['nome'];<br />
echo ', il tuo cognome è: '.$_POST['cognome'];<br />
echo ' [Metodo POST]';<br />
`

L&#8217;esempio è molto semplice, ma si può fare la stessa cosa, avendo un parte lato serve molto più complicata, il tutto mantenedo questo aspetto di applicazione Desktop per una applicazione Web.

[*codice completo*][2]

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://blog.ilbonzo.org/upload/ajax/getpost.html
 [2]: http://blog.ilbonzo.org/upload/ajax/getpost.zip