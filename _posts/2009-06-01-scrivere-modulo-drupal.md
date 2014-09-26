---
title: Scrivere Modulo Drupal
author: Matteo Magni
layout: post
permalink: /2009/06/01/scrivere-modulo-drupal/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1103608726
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - drupal
  - PHP
---
Ultimamente mi sono concentrato molto su [Drupal][1], soprattutto per la sua flessibilità e modularità.  
La possibilità di scrivere un modulo, che aggiunge funzioni, senza andare a toccare il core del resto del cms è veramente molto utile e produttivo.

Ecco un esempio di primo modulo che chiameremo `nodelist`:  
Creiamo un file **nodelist.info** che contiene le informazioni del modulo.

`; $Id: nodelist.info Exp $<br />
name = Nodelist<br />
description = visualizza list nodi<br />
package = node<br />
version = VERSION<br />
core = 6.x`

`; Information added by drupal.org packaging script on 2008-08-14<br />
version = "6.4"<br />
project = "drupal"`

Creare il file **nodelist.module** in cui scriveremo il modulo vero e proprio.

Per fare ciò utilizziamo i famosi [Hook][2] di Drupal.  
Le varie function per convenzione si chiameranno nodelist_[hook].

`<br />
/**<br />
* Display help and module information<br />
* @param path which path of the site we're displaying help<br />
* @param arg array that holds the current path as would be returned from arg() function<br />
* @return help text for the path<br />
*/<br />
function nodelist_help($path, $arg) {<br />
  $output = '';<br />
  switch ($path) {<br />
    case "admin/help#nodelist":<br />
      $output = '<p>'.t("Displays links to nodes ") .'</p>';<br />
      break;<br />
  }<br />
  return $output;<br />
}<br />
/**<br />
* Valid permissions for this module<br />
* @return array An array of valid permissions for the mailing module<br />
*/<br />
function nodelist_perm() {<br />
  return array('access nodelist content');<br />
} // function nodelist_perm()<br />
/**<br />
*<br />
* @return<br />
*/<br />
function nodelist_block($op='list', $delta=0) {<br />
  // listing of blocks, such as on the admin/block page<br />
  if ($op == "list") {<br />
    $block[0]["info"] = t("node List");<br />
    return $block;<br />
  } else if ($op == 'view') {<br />
  // our block content<br />
    // content variable that will be returned for display<br />
    $block_content = '';<br />
    $result =  db_query("SELECT nid, title, created FROM {node} ");<br />
    while ($links = db_fetch_object($result)) {<br />
      $block_content .= l($links->title, 'node/'.$links->nid) . '<br />';<br />
    }<br />
    // check to see if there was any content before setting up the block<br />
    if ($block_content == '') {<br />
      // no content from a week ago, return nothing.<br />
      return;<br />
    }<br />
    // set up the block<br />
    $block['subject'] = 'node';<br />
    $block['content'] = $block_content;<br />
    return $block;<br />
  }<br />
}<br />
`

Con questi file dentro la cartella nodelist e caricata nella cartella modules vi troverete la possibilità di abilitare il nuovo modulo.  
Abilitandolo avrete il nuovo blocco a disposizione.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://drupal.org
 [2]: http://api.drupal.org/api/group/hooks