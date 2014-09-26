---
title: PDO, Abstraction Layer
author: Matteo Magni
layout: post
permalink: /2008/06/16/pdo-abstraction-layer/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1102732611
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - PHP
---
Finalmente con la versione 5.1 PHP ha un nuovo livello di astrazione per la connettività con i database veramente valido.  
**[PDO][1], PHP Data Objects**

Ho deciso di studiarlo un po&#8217;:

Creo un Database di prova:  
`<br />
DROP TABLE IF EXISTS first_table;<br />
`  
`<br />
--CREATE TABLE first_table (<br />
--id INT(10) NOT NULL AUTO_INCREMENT,<br />
--name VARCHAR(255) NOT NULL,<br />
--surname VARCHAR(255) NOT NULL,<br />
--PRIMARY KEY (id)<br />
--) TYPE=MyISAM;<br />
`  
`<br />
CREATE TABLE first_table (<br />
id INT(10) NOT NULL AUTO_INCREMENT,<br />
name VARCHAR(255) NOT NULL,<br />
surname VARCHAR(255) NOT NULL,<br />
PRIMARY KEY (id)<br />
) TYPE=innoDB;<br />
`  
`<br />
INSERT INTO first_table (name,surname) VALUES ('matteo','magni');<br />
INSERT INTO first_table (name,surname) VALUES ('john','starks');<br />
INSERT INTO first_table (name,surname) VALUES ('michael','jordan');<br />
INSERT INTO first_table (name,surname) VALUES ('kobe','bryant');<br />
INSERT INTO first_table (name,surname) VALUES ('earvin','johnson');<br />
INSERT INTO first_table (name,surname) VALUES ('larry','bird');<br />
INSERT INTO first_table (name,surname) VALUES ('patrick','ewing');<br />
INSERT INTO first_table (name,surname) VALUES ('reggie','miller');<br />
INSERT INTO first_table (name,surname) VALUES ('ron','harper');<br />
INSERT INTO first_table (name,surname) VALUES ('anfernee','hardaway');<br />
INSERT INTO first_table (name,surname) VALUES ('tim','hardaway');<br />
INSERT INTO first_table (name,surname) VALUES ('mitch','richmond');<br />
INSERT INTO first_table (name,surname) VALUES ('jason','williams');<br />
INSERT INTO first_table (name,surname) VALUES ('allen','iverson');<br />
INSERT INTO first_table (name,surname) VALUES ('dwayne','wade');<br />
`

Lo importo così dopo aver creato il DB pdo  
`<br />
mysql -p -D pdo < pdo.sql<br />
`  
Per le prove utilizzerò sia la versione con tabella MyISAM che quella con tabella InnoDB, la differenza è che per la prima non sono disponibili le transazioni.

**Usiamo le eccezioni per connetterci al DB**  
</code>`<br />
//USO le eccezioni<br />
$string_dsn = 'mysql:host=localhost;dbname=pdo'; // mysql<br />
$string_username = 'user';<br />
$string_password = 'password';<br />
try {<br />
    $mypdo = new PDO($string_dsn, $string_username, $string_password);<br />
}<br />
catch(PDOException $e) {<br />
    echo 'Errore di connessione: '.$e->getMessage();<br />
}<br />
`

Query fatta con errore, mi restituisce il numero dell&#8217;errore:  
`<br />
$mypdo->exec('SELECT * FROM SELECT'); // errore generato appositamente<br />
echo 'Errore N: '.$mypdo->errorCode();<br />
` 

Se la uso così è molto utile, mando io il messaggio che voglio:  
`<br />
if($mypdo->errorCode() !== '' || !$mypdo->exec('SELECT * FROM SELECT'))<br />
    echo 'errore nella query SELECT * FROM SELECT';<br />
`

Così mi ritorna un array di tre elementi con le notizie sull&#8217;errore:  
`<br />
var_dump($mypdo->errorInfo());<br />
//array di tre elementi<br />
if(count($mypdo->errorInfo()) == 1) // ... tutto ok<br />
if(count($mypdo->errorInfo()) > 1) { // ... ci sono errori<br />
    $errorinfo = $mypdo->errorInfo();<br />
    echo $errorinfo[2]; // stringa con l' errore<br />
}<br />
`

**QUERY** semplice senza preparare niente,  
Mi ritorna i dati accessibili sia con il numero della colonna (partendo da 0) che con il nome della colonna  
Query senza parametri aggiuntivi per stabilire che Fetch usare:

`<br />
foreach($mypdo->query('SELECT * FROM first_table') as $row)<br />
{<br />
    echo '--------------<br />';<br />
    echo '1: '.$row[0].' - 2: '.$row[1].'<br />';<br />
    echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
`  
mi ritorna i dati accessibili sia con il numero della colonna (partendo da 0) che con il nome della colonna.

Esplicito il tipo di Fetch con il parametro PDO\_FETCH\_*  
**PDo::FETCH_BOTH** #usatelo come mysql fetch_array, risultato duplicato, quello di default  
`<br />
foreach($mypdo->query('SELECT * FROM first_table', PDO::FETCH_BOTH) as $row)<br />
{<br />
    echo '--------------<br />';<br />
    echo '1: '.$row[0].' - 2: '.$row[1].'<br />';<br />
    echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
`

**PDO::FETCH_ASSOC** #usatelo come mysql\_fetch\_assoc  
`<br />
foreach($mypdo->query('SELECT * FROM first_table', PDO::FETCH_ASSOC) as $row)<br />
{<br />
    echo '--------------<br />';<br />
    echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
`

**PDO::FETCH_NUM **#analogo a mysql\_fetch\_row  
`<br />
foreach($mypdo->query('SELECT * FROM first_table', PDO::FETCH_NUM) as $row)<br />
{<br />
    echo '--------------<br/>';<br />
    echo '1: '.$row[0].' - 2: '.$row[1].'<br/>';<br />
}<br />
`

**PDO::FETCH_OBJ **#ritorna un oggetto con le proprieta&#8217; che hanno il nome dei campi  
`<br />
foreach($mypdo->query('SELECT * FROM first_table', PDO::FETCH_OBJ) as $row)<br />
{<br />
    echo '--------------<br />';<br />
    echo 'id->'.$row->id.' - name-> '.$row->name.'<br />';<br />
}<br />
`

**PDO::FETCH_LAZY **#combina \*\_BOTH e \*\_OBJ  
`<br />
foreach($mypdo->query('SELECT * FROM first_table', PDO::FETCH_LAZY) as $row)<br />
{<br />
    echo '--------------<br />';<br />
    echo '1: '.$row[0].' - 2: '.$row[1].'<br />';<br />
    echo 'id:  '.$row['id'].' - name: '.$row['name'].'<br />';<br />
    echo 'id->'.$row->id.' - name-> '.$row->name.'<br />';<br />
}<br />
`

**PDO::FETCH_BOUND** #Lo vediamo con bindColumn,  
restituiti come attributi alle variabili PHP

Per Evitare problemi con DB case sensitive e non case sensitive  
Setto che i nomi delle colonne siano restituiti sempre minuscoli  
`<br />
$mypdo->setAttribute(PDO::CASE_LOWER);<br />
/*<br />
 * Psso usare anche<br />
 * PDO::CASE_UPPER<br />
 * PDO::CASE_NATURAL come sono fornite dal driver, metodo di default<br />
 */<br />
`  
oppure si usa sempre FETCH_NUM

**Utilizzo delle Transazioni**

inizio la transazione

Su Mysql devo usare tabelle InnoDB perchè MyIsam non supportano le transazioni

Però&#8230;  
The following example begins a transaction and issues two statements that  
modify the database before rolling back the changes.  
On MySQL, however, the DROP TABLE statement automatically commits the  
transaction so that none of the changes in the transaction are rolled back.

Quindi niente drop per una transazione.  
`<br />
$mypdo->beginTransaction();<br />
$mypdo->exec('DROP TABLE first_table');<br />
$mypdo->rollBack(); // la tabella mytable rimarra' invariata <img src='http://magni.me/wp-includes/images/smilies/icon_smile.gif' alt=':-)' class='wp-smiley' /><br />
`

come detto su MySQL la cancella lo stesso.

`<br />
$mypdo->beginTransaction();<br />
$mypdo->exec("INSERT INTO first_table (name,surname) VALUES ('gianni','morandi')");<br />
$mypdo->rollBack(); // la tabella mytable rimarra' invariata <img src='http://magni.me/wp-includes/images/smilies/icon_smile.gif' alt=':-)' class='wp-smiley' /><br />
`

`<br />
$mypdo->beginTransaction();<br />
$mypdo->exec("INSERT INTO first_table (name,surname) VALUES ('gianni','morandi')");<br />
$mypdo->commit(); // la tabella mytable rimarra' invariata <img src='http://magni.me/wp-includes/images/smilies/icon_smile.gif' alt=':-)' class='wp-smiley' /><br />
`  
mi inserisce il nuovo valore.

### Prepared Statement

**Metodo Fetch**  
Metodo implementato nello statement che è in grado di spostare il cursore dei risultati di una query in un ciclo.  
Gli posso passare i parametri come a query.  
/*  
* PDO::FETCH\_ASSOC, PDO::FETCH\_BOTH, PDO::FETCH\_BOUND, PDO::FETCH\_LAZY,  
* PDO::FETCH\_OBJ, PDO::FETCH\_NUM  
*/  
`<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('UPDATE first_table SET name = "pippo" WHERE id = 17');<br />
// eseguo la query<br />
$stpdo->execute();<br />
$mypdo->commit();<br />
echo 'SELECT';<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table');<br />
// eseguo la query<br />
$stpdo->execute();<br />
//stampo a video il contenuto dell'array che mi crea fetch<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`

**La potenza prepare e execute **  
Potenza del metodo prepare  
`<br />
$mypdo->beginTransaction();<br />
$stpdo = $mypdo->prepare('UPDATE first_table SET name = ? WHERE id = ?');<br />
//i punti interrogativi saranno sostituiti da execute<br />
$stpdo->execute(array('gianni', 17));<br />
$mypdo->commit();<br />
echo 'SELECT';<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table');<br />
// eseguo la query<br />
$stpdo->execute();<br />
//stampo a video il contenuto dell'array che mi crea fetch<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`  
Posso preparare la query una volta e fare poi i vari inserimenti.  
**potenza prepare e execute ancora**  
`<br />
$mypdo->beginTransaction();<br />
$stpdo = $mypdo->prepare('UPDATE first_table SET name = :name WHERE id = :id');<br />
//i punti interrogativi non sempre sono chiari, così lo è di più<br />
$stpdo->execute(array(':name'=>'marcello',':id'=>17));<br />
$mypdo->commit();<br />
echo 'SELECT';<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table');<br />
// eseguo la query<br />
$stpdo->execute();<br />
//stampo a video il contenuto dell'array che mi crea fetch<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`

**Metodo fetchAll**  
ritorna un array le righe del resultset  
`<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table');<br />
// eseguo la query<br />
$stpdo->execute();<br />
$row=$stpdo->fetchAll();<br />
//stampo a video il contenuto dell'array che mi crea fetch<br />
var_dump($row);<br />
$mypdo->commit();<br />
`

**Metodo fetchAll**  
`<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table');<br />
// eseguo la query<br />
$stpdo->execute();<br />
$row=$stpdo->fetchAll(PDO::FETCH_OBJ);<br />
//così ho un array di oggetti<br />
//stampo a video il contenuto dell'array che mi crea fetch<br />
var_dump($row);<br />
$mypdo->commit();<br />
`

### Metodi bind

**bindParam**  
`<br />
$id=10;<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare("SELECT * FROM first_table WHERE id = ? ");<br />
$stpdo->bindParam(1,$id, PDO::PARAM_INT);<br />
$stpdo->execute();<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`  
Oppure:  
`<br />
$id=10;<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare("SELECT * FROM first_table WHERE id = :id ");<br />
$stpdo->bindParam(':id',$id, PDO::PARAM_INT);<br />
$stpdo->execute();<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$id=13;<br />
$stpdo->bindParam(':id',$id, PDO::PARAM_INT);<br />
$stpdo->execute();<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`  
Così ho preparato la query una volta sola, ed ho legato :id al valore della variabile $id.

**bindValue**  
`<br />
$id=10;<br />
$mypdo->beginTransaction();<br />
$stpdo = $mypdo->prepare('SELECT * FROM first_table WHERE id < ? ');<br />
$stpdo->bindValue(1, $id, PDO::PARAM_INT);<br />
$stpdo->execute();<br />
while ($row=$stpdo->fetch())<br />
{<br />
     echo 'id: '.$row['id'].' - name: '.$row['name'].'<br />';<br />
}<br />
$mypdo->commit();<br />
`

**bindColumn**  
`<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare("SELECT * FROM first_table ");<br />
$stpdo->bindColumn(1,$id);<br />
$stpdo->bindColumn(2,$name);<br />
$stpdo->bindColumn(3,$surname);<br />
$stpdo->execute();<br />
while($row = $stpdo->fetch(PDO::FETCH_BOUND))<br />
    echo $id.' '.$name.' '.$surname.'<br />'; // stampo i nomi<br />
$mypdo->commit();<br />
`  
In pratica specifico prima come devono chiamarsi i dati letti da una query e di che tipo devono essere.  
a variabile $id non l&#8217;avevo mai creata, nonostante ciò non ho avuto nessun notice o warning perche&#8217; questa viene popolata e inizializzata ( se inesistente ) automaticamente all&#8217; interno della chiamata a bindColumn.  
Poi la variabile viene automaticamente riassegnata ad ogni ciclo del while ,  
permettendoci di evitare i soliti $row[N] per il fetch\_row o $row['key'] per il fetch\_assoc.

**bindColumn**  
`<br />
$mypdo->beginTransaction();<br />
// preparo la query<br />
$stpdo = $mypdo->prepare("SELECT * FROM first_table ");<br />
$stpdo->bindColumn(1,$id, PDO::PARAM_INT);<br />
$stpdo->bindColumn(2,$name, PDO::PARAM_STR);<br />
$stpdo->bindColumn(3,$surname, PDO::PARAM_STR);<br />
$stpdo->execute();<br />
while($row = $stpdo->fetch(PDO::FETCH_BOUND))<br />
    echo $id.' '.$name.' '.$surname.'<br />'; // stampo i nomi<br />
$mypdo->commit();<br />
`

i parametri non modificano il risultato, ma &#8220;forse&#8221; ottimizzano le query

così abbiamo visto anche come funizona PDO::FETCH_BOUND

E se volessi usare Postgres invece di Mysql?  
Semplice creo il DB pgsql come quello mysql e basta che cambi queste rige con i diversi parametri di connessione:  
`<br />
$string_dsn = 'pgsql:host=localhost;dbname=pdo'; // pgsql<br />
$string_username = 'user';<br />
$string_password = 'password';<br />
`

ed il gioco è fatto, bello no?!

Lo studio l&#8217;ho fatto partendo da questi link:

<http://it2.php.net/pdo>  
[Pillola PDO][2]

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://it2.php.net/pdo
 [2]: http://forum.html.it/forum/showthread.php?s=&#038;postid=8143487