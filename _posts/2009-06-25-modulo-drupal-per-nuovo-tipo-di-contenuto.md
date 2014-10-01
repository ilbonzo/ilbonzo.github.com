---
title: Modulo Drupal per nuovo tipo di contenuto
author: Matteo Magni
layout: post
permalink: /2009/06/25/modulo-drupal-per-nuovo-tipo-di-contenuto/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1104440029
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - drupal
  - PHP
---
In Drupal è molto semplice sviluppare un modulo che permeta di avere a disposizione un nuovo tipo di contenuto che estenda il classico nodo.

Vediamo come sviluppare un modulo che aggiunga il tipo di contenuto libro.

Creiamo la cartella node_book che andremo a mettere nella cartella modules del nostro sito.  
Dentro questa cartella mettiamo il file *node_book.info* con le specifiche del nodo:  
`<br />
; $Id$<br />
name = node book<br />
description = "nodo libro"<br />
core = 6.x<br />
`

e il file node_book.module con il codice vero e proprio.

Ecco i vari hook che si devono implementare:  
**Hook menu**  
`<br />
function node_book_menu()<br />
{<br />
	$items[] = array( 'path' => 'node_book', 'callback' => 'node_book_page', 'access' => true, 'type' => MENU_CALLBACK );<br />
      return $items;<br />
}<br />
`

**hook perm**  
`<br />
function node_book_perm()<br />
{<br />
  return array('create book node', 'edit own book nodes');<br />
}<br />
`  
**hook access**  
`function node_book_access($op, $node, $account) {<br />
  if ($op == 'create') {<br />
    // Only users with permission to do so may create this node type.<br />
    return user_access('create nameofnodetype', $account);<br />
  }<br />
  // Users who create a node may edit or delete it later, assuming they have the<br />
  // necessary permissions.<br />
  if ($op == 'update' || $op == 'delete') {<br />
    if (user_access('edit own nameofnodetype', $account) &#038;&#038; ($account->uid == $node->uid)) {<br />
      return TRUE;<br />
    }<br />
  }<br />
}`

**hook help**  
`function node_book_help($path, $arg) {<br />
  switch ($path) {<br />
    case 'admin/help#block':<br />
      return '
<p>'. t('Blocks are boxes of content that may be rendered into certain regions of your web pages, for example, into sidebars. Blocks are usually generated automatically by modules (e.g., Recent Forum Topics), but administrators can also define custom blocks.') .'</p>
<p>';</p>
<p>    case 'admin/build/block':<br />
      return t('
<p>Blocks are boxes of content that may be rendered into certain regions of your web pages, for example, into sidebars. They are usually generated automatically by modules, but administrators can create blocks manually.</p>
<p>If you want certain blocks to disable themselves temporarily during high server loads, check the "Throttle" box. You can configure the auto-throttle on the <a href="@throttle">throttle configuration page</a> after having enabled the throttle module.</p>
<p>You can configure the behaviour of each block (for example, specifying on which pages and for what users it will appear) by clicking the "configure" link for each block.</p>
<p>', array('@throttle' => url('admin/settings/throttle')));<br />
  }<br />
}`  
Ora passiamo agli hook che implementano veramente il nostro modulo:  
**hook form**  
`<br />
function node_book_form(&#038;$node) {<br />
$type = node_get_types('type', $node);<br />
  if ($type->has_title) {<br />
    $form['title'] = array(<br />
      '#type' => 'textfield',<br />
      '#title' => check_plain($type->title_label),<br />
      '#required' => TRUE,<br />
      '#default_value' => $node->title,<br />
      '#weight' => -5<br />
    );<br />
  }<br />
  if ($type->has_body) {<br />
    // In Drupal 6, we can use node_body_field() to get the body and filter<br />
    // elements. This replaces the old textarea + filter_form() method of<br />
    // setting this up. It will also ensure the teaser splitter gets set up<br />
    // properly.<br />
    $form['body_field'] = node_body_field($node, $type->body_label, $type->min_word_count);<br />
  }<br />
  // NOTE in node_example there is some addition code here not needed for this simple node-type<br />
 // Now we define the form elements specific to our node type.<br />
  $form['editor'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Editore'),<br />
    '#default_value' => isset($node->editor) ? $node->editor : '',<br />
  );<br />
  $form['book_author'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Autore'),<br />
    '#default_value' => isset($node->book_author) ? $node->book_author : '',<br />
  );<br />
  $form['place'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Luogo'),<br />
    '#default_value' => isset($node->place) ? $node->place : '',<br />
  );<br />
  $form['year'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Anno'),<br />
    '#default_value' => isset($node->year) ? $node->year : '',<br />
  );<br />
  $form['book_type'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Tipo'),<br />
    '#default_value' => isset($node->book_type) ? $node->book_type : '',<br />
  );<br />
  $form['magazine'] = array(<br />
    '#type' => 'textfield',<br />
    '#title' => t('Rivista'),<br />
    '#default_value' => isset($node->magazine) ? $node->magazine : '',<br />
  );<br />
  return $form;<br />
}`

**hook insert**  
/**  
* Implementation of hook_insert().  
*  
* As a new node is being inserted into the database, we need to do our own  
* database inserts.  
*/  
`function node_book_insert($node) {<br />
  db_query("INSERT INTO {node_book} (vid, nid, editor, book_author, place, year, book_type, magazine) VALUES (%d, %d, '%s', '%s', '%s', '%s', '%s', '%s')", $node->vid, $node->nid,$node->editor,$node->book_author,$node->place,$node->year,$node->book_type,$node->magazine);<br />
}`

**hook update**  
`/**<br />
 * Implementation of hook_update().<br />
 *<br />
 * As an existing node is being updated in the database, we need to do our own<br />
 * database updates.<br />
 */<br />
function node_book_update($node) {<br />
  // if this is a new node or we're adding a new revision,<br />
  if ($node->revision) {<br />
    node_book_insert($node);<br />
  }<br />
  else {<br />
    db_query("UPDATE {node_book} SET editor='%s', book_author='%s', place='%s', year='%s', book_type='%s', magazine='%s' WHERE vid = %d",  $node->editor, $node->book_author, $node->place, $node->year, $node->book_type, $node->magazine, $node->vid);<br />
  }<br />
}<br />
`

**hook nodeapi**  
`/**<br />
 * Implementation of hook_nodeapi().<br />
 *<br />
 * When a node revision is deleted, we need to remove the corresponding record<br />
 * from our table. The only way to handle revision deletion is by implementing<br />
 * hook_nodeapi().<br />
 */<br />
function node_book_nodeapi(&#038;$node, $op, $teaser, $page) {<br />
  switch ($op) {<br />
    case 'delete revision':<br />
      // Notice that we're matching a single revision based on the node's vid.<br />
      db_query('DELETE FROM {node_book} WHERE vid = %d', $node->vid);<br />
      break;<br />
  }<br />
}`

**hook_delete**  
/**  
* Implementation of hook_delete().  
*  
* When a node is deleted, we need to remove all related records from out table.  
*/  
function node\_book\_delete($node) {  
// Notice that we&#8217;re matching all revision, by using the node&#8217;s nid.  
db\_query(&#8216;DELETE FROM {node\_book} WHERE nid = %d&#8217;, $node->nid);  
}

**hook load**  
`/**<br />
 * Implementation of hook_load().<br />
 *<br />
 * Now that we've defined how to manage the node data in the database, we<br />
 * need to tell Drupal how to get the node back out. This hook is called<br />
 * every time a node is loaded, and allows us to do some loading of our own.<br />
 */<br />
function node_book_load($node) {<br />
  $additions = db_fetch_object(db_query('SELECT editor,book_author,place,year,book_type,magazine FROM {node_book} WHERE vid = %d', $node->vid));<br />
  return $additions;<br />
}<br />
`

**hook view**  
`/**<br />
 * Implementation of hook_view().<br />
 *<br />
 * This is a typical implementation that simply runs the node text through<br />
 * the output filters.<br />
 */<br />
function node_book_view($node, $teaser = FALSE, $page = FALSE) {<br />
    $node = node_prepare($node, $page);<br />
    $node->content['myfield'] = array(<br />
	'#value' => 'Editore: '.$node->editor.'<br />'.'Autore: '.$node->book_author.'<br >'.'Luogo: '.$node->place.'<br >'.'Anno: '.$node->year.'<br >'.'Tipologia: '.$node->book_type.'<br >',<br />
    	'#weight' => 1,<br />
  );<br />
  return $node;<br />
}<br />
`

Ora manca solo il DB, ecco la tabella per i campi in più del nostro nodo  
CREATE TABLE node_book (  
vid int(10) unsigned NOT NULL default &#8217;0&#8242;,  
nid int(10) unsigned NOT NULL default &#8217;0&#8242;,  
editor varchar(255) NOT NULL default &#8221;,  
book_author varchar(255) NOT NULL default &#8221;,  
place varchar(255),  
year varchar(255),  
book_type varchar(255),  
magazine varchar(255),  
PRIMARY KEY (vid, nid),  
KEY \`node\_type\_book_nid\` (nid)  
)

Dopo aver creato la tabella e attivato il modulo avrete un nuovo tipo di contenuto disponibile.

<div class='kindleWidget kindleLight' >
  
</div>

