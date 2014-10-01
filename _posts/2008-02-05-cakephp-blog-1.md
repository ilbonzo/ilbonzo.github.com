---
title: 'CakePHP, Blog [1]'
author: ilbonzo
layout: post
permalink: /2008/02/05/cakephp-blog-1/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1098457871
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - cakePHP
  - PHP
---
Comincio a fare &#8220;sul serio&#8221; con l&#8217;uso di CAkePHP, ora proverò a creare un blog.

**Creazione database**

> Per prima cosa  
> Ecco alcuni accorgimenti sulle regole che devono seguire le tabelle (naming convention):
> 
> *   I nomi devono essere in plurale inglese (posts ad esempio), in modo che i modelli corrispondenti abbiano nomi in singolare;
> *   tutte le tabelle devono avere una chiave primaria chiamata id; 
> *   le chiavi esterne utilizzate per costruire le relazioni tra le tabelle devono essere nomiate utilizzando il singolare della tabella a cui fanno riferimento seguito da \_id (post\_id per esempio);
> *   è possibile includere i campi created e modified che verranno automaticamente aggiornati da CakePHP quando si opererà sui record. 
> 
> Cake contiente una classe *inflections* che si occupa di ottenere i plurali dei vari nomi.

Creo il database **blog_cake**.

Creo la tabella **posts**.  
`<br />
/* First, create our posts table: */<br />
CREATE TABLE posts (<br />
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,<br />
    title VARCHAR(50),<br />
    body TEXT,<br />
    created DATETIME DEFAULT NULL,<br />
    modified DATETIME DEFAULT NULL<br />
);<br />
`  
`<br />
/* Then insert some posts for testing: */<br />
INSERT INTO posts (title,body,created)<br />
    VALUES ('il titolo', 'Questo è il contenuto di un post.', NOW());<br />
INSERT INTO posts (title,body,created)<br />
    VALUES ('secondo titolo', 'Altro contenuto di un post.', NOW());<br />
INSERT INTO posts (title,body,created)<br />
    VALUES ('Divetimento', 'Divertiamoci.', NOW());<br />
`

Imposto i dati di connessione al database nel file */app/config/database.php*  
`<br />
var $default = array('driver'   => 'mysql',<br />
                     'connect'  => 'mysql_pconnect',<br />
                     'host'     => 'localhost',<br />
                     'login'    => '<utente>',<br />
                     'password' => '
<password>',<br />
                     'database' => 'blog_cakel' );
</password></utente>`

Cake contiene una Classe AppModel da cui si parte per ottenere i nuovi modelli, estendendo tale classe di partenza.

**Creo il modello Post:**

*/app/models/post.php*

`<br />
< ?php<br />
class Post extends AppModel<br />
{<br />
    var $name = 'Post';<br />
}<br />
?><br />
`

**Creo il controller Post**  
Dato che abbiamo deciso di seguire le convenzioni sui nomi sarà possibile accedere ai modelli implementati direttamente attraverso $this->NOME_MODELLO.  
*/app/controllers/posts_controller.php*

`< ?php<br />
class PostsController extends AppController<br />
{<br />
    var $name = 'Posts';<br />
}<br />
?><br />
`

Ci aggiungo l&#8217;azione index

`<br />
< ?php<br />
class PostsController extends AppController<br />
{<br />
    var $name = 'Posts';<br />
    function index()<br />
    {<br />
        $this->set('posts', $this->Post->findAll());<br />
    }<br />
}<br />
?>`

Il metodo index registra un array con tutti i post inseriti utilizzando il metodo set, che rende disponibile questo array alla vista.

**Creo la vista index**  
*  
/app/views/posts/index.thtml*

`<br />
<h1>Blog</h1><br />
    < ?php foreach ($posts as $post): ?><br />
    <dl><br />
		<dt><br />
		<h3>< ?php echo $html->link($post['Post']['title'], "/posts/view/".$post['Post']['id']); ?></h3><br />
        < ?php<br />
			echo $post['Post']['id'];<br />
			echo '<br/>';<br />
			echo $post['Post']['created'];<br />
			echo '<br/&#038;gt';<br />
			echo '<br/>';<br />
		?><br />
		</dt><br />
		<dd><br />
		< ?php<br />
			echo $post['Post']['body'];<br />
		?><br />
		</dd><br />
	</dl><br />
   < ?php endforeach; ?><br />
`

Vado con il browser all&#8217;indirizzo:  
*http://localhost/cake/posts/*  
ed ecco il risultato:

<a href='http://magni.me/wp-content/uploads/2008/01/001_post.png' title='cakePHP blog' rel='lightbox'><img src='http://magni.me/wp-content/uploads/2008/01/001_post.thumbnail.PNG' alt='cakePHP blog' /></a>

Ora aggiungo l&#8217;azione view al controller, per gestire la visualizzazione di un singolo post.

`<br />
< ?php<br />
class PostsController extends AppController<br />
{<br />
    var $name = 'Posts';<br />
    function index()<br />
    {<br />
        $this->set('posts', $this->Post->findAll());<br />
    }<br />
	function view($id = null)<br />
    {<br />
        $this->Post->id = $id;<br />
        $this->set('post', $this->Post->read());<br />
    }<br />
}<br />
?><br />
`

**Creo la vista view**  
*/app/views/posts/view.thtml*

`<br />
<h2>< ?php echo $post['Post']['title']?></h2><br />
<p><small>Created: < ?php echo $post['Post']['created']?></small></p><br />
<p>< ?php echo $post['Post']['body']?></p><br />
`

Ora se clicco sul titolo del primo post, mi sposto all&#8217;indirizzo:  
*http://localhost/cake/posts/view/1*

e vedo la vista view di questo post.

<a href='http://magni.me/wp-content/uploads/2008/02/002_single_post1.png' title='post singolo' rel='lightbox'><img src='http://magni.me/wp-content/uploads/2008/02/002_single_post1.thumbnail.png' alt='post singolo' /></a>

Così ho completato tutte le pagine per visualizzare il blog, la prossima volta passo alle pagine per inserimento, modifica e cancellazione dei post.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>

