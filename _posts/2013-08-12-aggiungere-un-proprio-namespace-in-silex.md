---
title: Aggiungere un proprio namespace in Silex
author: ilbonzo
layout: post
permalink: /2013/08/12/aggiungere-un-proprio-namespace-in-silex/
pdrp_attributionLocation:
  - end
thesis_title:
  - Aggiungere un proprio namespace in Silex
thesis_description:
  - "Se vogliamo aggiungere un nostro namespace personalizzato potendo caricare le classi attraverso l'autoloader dei Silex dobbiamo seguire questa procedura."
thesis_keywords:
  - php, silex, composer, namespace
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/08/silex_th.jpg
dsq_thread_id:
  - 1599277467
categories:
  - Development
tags:
  - PHP
  - Silex
comments: true
share: true
---
<img class="alignnone size-full wp-image-919 aligncenter" alt="silex" src="http://magni.me/wp-content/uploads/2013/08/silex.jpg" width="202" height="202" />

Se vogliamo aggiungere un nostro namespace personalizzato potendo caricare le classi attraverso l&#8217;autoloader dei Silex dobbiamo seguire questa procedura.

Creiamo la cartella per le nostre classi:  

    $ cd my-silex-project/src
    $ mkdir NewNamespace

Creiamo la classe che vogliamo caricare:  
$ vi src/NewNamespace/MyClass.php

Nella classe mettiamo il codice per registrare il nuovo namespace:  

    namespace NewNamespace;
    class MyClass {
        public function __construct() {
      }
    }

Aggiungiamo il nostro namespace al *composer.json* in modo che l&#8217;autoloader di **Silex** possa utilizzarlo:  

    {
      "require": {
          "silex/silex": "1.0.*@dev"
      },
      "autoload": {
          "psr-0": {
              "NewNamespace": "src/"
          }
      }
    }

Lanciamo* composer* update  

    $ composer update

Ora possiamo utilizzare le classi del nostro namespace nel progetto **Silex**.  

    use Silex\Application;
    use NewNamespace\MyClass;
    require_once __DIR__.'/../vendor/autoload.php';
    $app = new Application();
    //add myclass
    $app['myclass'] = function () {
        return new MyClass();
    };

<div class='kindleWidget kindleLight' >

</div>
