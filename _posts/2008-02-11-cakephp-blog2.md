---
title: 'CakePHP, Blog[2]'
author: ilbonzo
layout: post
permalink: /2008/02/11/cakephp-blog2/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1098366247
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - cakePHP
  - PHP
---
Andiamo avanti con la realizzazione del blog scritto con <a href="http://cakephp.org" class="Tips3" title="CakePHP framework web">CakePHP</a>.

Devo creare il meccanismo la creazione, modifica e eliminzaione dei post.

**Aggiungere i Post**  
*/app/controllers/posts_controller.php*  
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
	function add()<br />
    {<br />
        if (!empty($this->data))<br />
        {<br />
            if ($this->Post->save($this->data))<br />
            {<br />
                $this->flash('Your post has been saved.','/posts');<br />
            }<br />
        }<br />
    }<br />
}<br />
?><br />
`

Il controller guarda che i dati inviati via POST non siano vuoti, se non lo sono utilizza il metodo per salvare i dati. Con il metodo flash è possibile visualizzare un messaggio che dice se i dati sono stati salvati.  
**  
Creo la vista add**  
*/app/views/posts/add.thtml*  
`<br />
< <h1>Add Post</h1><br />
<form method="post" action="<?php echo $html->url('/posts/add')?>"><br />
    <p><br />
        Title:<br />
        < ?php echo $html->input('Post/title', array('size' => '40'))?><br />
        < ?php echo $html->tagErrorMsg('Post/title', 'Title is required.') ?><br />
    </p><br />
    <p><br />
        Body:<br />
        < ?php echo $html->textarea('Post/body', array('rows'=>'10')) ?><br />
        < ?php echo $html->tagErrorMsg('Post/body', 'Body is required.') ?><br />
    </p><br />
    <p><br />
        < ?php echo $html->submit('Save') ?><br />
    </p><br />
</form><br />
`

ecco come si visualizza la pagina:  
*http://localhost/cake/posts/add*  
<a href='http://magni.me/wp-content/uploads/2008/02/003_add_post.png' title='creazione post' rel='lightbox'><img src='http://magni.me/wp-content/uploads/2008/02/003_add_post.thumbnail.png' alt='creazione post' /></a>

**Modifico il modello Post**  
*/app/models/post.php*  
aggiungo la validazione dei dati.

`<br />
< ?php<br />
class Post extends AppModel<br />
{<br />
    var $name = 'Post';<br />
    var $validate = array(<br />
        'title'  => VALID_NOT_EMPTY,<br />
        'body'   => VALID_NOT_EMPTY<br />
    );<br />
}<br />
?>`

L&#8217;array $validate dice a Cake come validare i dati quando è chiamato il metodo save(). I valori per queste chiave si possono vedere in /cake/libs/validators.php.

`<br />
/**<br />
 * Not empty.<br />
 */<br />
	define('VALID_NOT_EMPTY', '/.+/');<br />
/**<br />
 * Numbers [0-9] only.<br />
 */<br />
	define('VALID_NUMBER', '/^[-+]?\b[0-9]*\.?[0-9]+\b$/');<br />
/**<br />
 * A valid email address.<br />
 */<br />
	define('VALID_EMAIL', '/\A(?:^([a-z0-9][a-z0-9_\-\.\+]*)@([a-z0-9][a-z0-9\.\-]{0,63}\.(com|org|net|biz|info|name|net|pro|aero|coop|museum|[a-z]{2,4}))$)\z/i');<br />
/**<br />
 * A valid year (1000-2999).<br />
 */<br />
	define('VALID_YEAR', '/^[12][0-9]{3}$/');<br />
`

Ecco cosa succede se si prova ad inserire un post senza il titolo:

<a href='http://magni.me/wp-content/uploads/2008/02/004_cake_title_request.png' title='title request' rel='lightbox'><img src='http://magni.me/wp-content/uploads/2008/02/004_cake_title_request.thumbnail.png' alt='title request' /></a>

**Cancellare i post, azione delete**  
*/app/controllers/posts_controller.php*

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
	function add()<br />
    {<br />
        if (!empty($this->data))<br />
        {<br />
            if ($this->Post->save($this->data))<br />
            {<br />
                $this->flash('Your post has been saved.','/posts');<br />
            }<br />
        }<br />
    }<br />
	function delete($id)<br />
	{<br />
		$this->Post->del($id);<br />
		$this->flash('The post with id: '.$id.' has been deleted.', '/posts');<br />
	}<br />
}<br />
?><br />
`

Aggiungo il link delete nella vista index  
*/app/views/posts/index.thtml*

`<br />
< ?php<br />
echo $html->link(<br />
                'Delete',<br />
                "/posts/delete/{$post['Post']['id']}",<br />
                null,<br />
                'Are you sure?'<br />
            )<br />
?><br />
`

se clicco mi si apre un alert javascript che mi chiede se sono sicuro.  
Se disabilito javascript nel browser il post viene cancellato senza richiesta di conferma.

**Modificare i post, azione edit**  
*/app/controllers/posts_controller.php*

`<br />
	function edit($id = null)<br />
	{<br />
		if (empty($this->data))<br />
		{<br />
			$this->Post->id = $id;<br />
			$this->data = $this->Post->read();<br />
		}<br />
		else<br />
		{<br />
			if ($this->Post->save($this->data['Post']))<br />
			{<br />
				$this->flash('Your post has been updated.','/posts');<br />
			}<br />
		}<br />
	}<br />
`

**Creo la vista edit**  
*/app/views/posts/edit.thtml*

`<br />
<h1>Edit Post</h1><br />
<form method="post" action="< ?php echo $html->url('/posts/edit')?>"><br />
    < ?php echo $html->hidden('Post/id'); ?><br />
    <p><br />
        Title:<br />
        < ?php echo $html->input('Post/title', array('size' => '40'))?><br />
        < ?php echo $html->tagErrorMsg('Post/title', 'Title is required.') ?><br />
    </p><br />
    <p><br />
        Body:<br />
        < ?php echo $html->textarea('Post/body', array('rows'=>'10')) ?><br />
        < ?php echo $html->tagErrorMsg('Post/body', 'Body is required.') ?><br />
    </p><br />
    <p><br />
        < ?php echo $html->submit('Save') ?><br />
    </p><br />
</form><br />
`

aggiungo il link edit nella vista index  
*/app/views/posts/index.thtml*

`<br />
 < ?php echo $html->link('Edit', '/posts/edit/'.$post['Post']['id']);?><br />
`

**Modifica pagina di home**  
*/app/config/routes.php*

Nel file routes.php ci sono le configurazioni per i controller e le relative viste che si devono aprire per i vari indirizzi.

Modifico commentando  
`<br />
	//$Route->connect('/', array('controller' => 'pages', 'action' => 'display', 'home'));<br />
`  
e settando:  
`<br />
/**<br />
* Collegamento alla pagina index<br />
*<br />
*/<br />
	$Route->connect ('/', array('controller'=>'posts', 'action'=>'index'));<br />
`  
Così andando a http://localhost/cake mi apre direttamente la vista index del controller posts.

Ecco fatto, ora il sistema di gestione dei Post è finito, il prossimo obbiettivo è implementare un sistema di gestione degli utenti che possono inviare i post.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>

