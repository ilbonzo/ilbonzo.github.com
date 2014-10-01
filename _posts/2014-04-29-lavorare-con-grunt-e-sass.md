---
title: Lavorare con Grunt e Sass
author: ilbonzo
layout: post
permalink: /2014/04/29/lavorare-con-grunt-e-sass/
pdrp_attributionLocation:
  - end
thesis_title:
  - Lavorare con Grunt e Sass
thesis_description:
  - |
    Lavorando con Sass si sente subito l'esigenza di avere un tool che ci generi in automatico i file .css, le possibilità sono tante, una di queste può essere l'uso di Grunt.
    Ecco come configurare Grunt per avere il watch dei file .scss automatico.
thesis_keywords:
  - grunt, sass, devops, nodejs, frontend
thesis_thumb:
  - http://magni.me/wp-content/uploads/2014/04/grunt-logo-th.png
dsq_thread_id:
  - 2647033383
categories:
  - css
  - DevOps
tags:
  - Grunt
  - nodejs
  - Sass
comments: true
share: true
---
Lavorando con **<a href="http://sass-lang.com/" target="_blank">Sass</a>** si sente subito l&#8217;esigenza di avere un tool che ci generi in automatico i file .css, le possibilità sono tante, una di queste può essere l&#8217;uso di **<a href="http://gruntjs.com/" target="_blank">Grunt</a>**.

[<img src="http://magni.me/wp-content/uploads/2014/04/grunt-logo-1.png" alt="grunt-logo-1" width="250" height="333" class="aligncenter size-full wp-image-987" />][1]

Per iniziare installiamo *NodeJs*:  
*su Ubuntu*

<pre class="lang:sh decode:true " >$ apt-get install python-software-properties
 $ apt-add-repository ppa:chris-lea/node.js
 $ apt-get update
 $ apt-get install nodejs
</pre>

*su OSx*

<pre class="lang:sh decode:true " >$ brew install node</pre>

<!--more-->


Poi dobbiamo configurare le dipendenze npm:

<pre class="lang:sh decode:true " >$ npm init
$ npm install grunt --save-dev
$ npm install grunt-contrib-sass --save-dev
$ npm install grunt-contrib-watch --save-dev
</pre>

A questo punto avremo un *packeage.json* simile a questo:

<pre class="lang:js decode:true " >{
  "name": "my-project",
  "version": "0.0.1",
  "devDependencies": {
    "grunt": "^0.4.4",
    "grunt-contrib-sass": "~0.7.3",
    "grunt-contrib-watch": "~0.6.1"
  }
}
</pre>

Per usare grunt da riga di comando dobbiamo installare *Grunt Cli*

<pre class="lang:sh decode:true " >$ sudo npm install -g grunt-cli
</pre>

Installiamo *Sass* (necessità di Ruby installato)

<pre class="lang:sh decode:true " >$ sudo gem install sass
</pre>

Configuriamo *Grunt* creando un *Gruntfile.js* così:

<pre class="lang:js decode:true " >module.exports = function(grunt) {
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),
        sass: {
            dist: {
                files: {
                    'styles/style.css' : 'sass/style.scss',
                    'styles/style-ie.css' : 'sass/style-ie.scss',
                }
            }
        },
        watch: {
            css: {
                files: '**/*.scss',
                tasks: ['sass']
            }
        }
    });
    grunt.loadNpmTasks('grunt-contrib-sass');
    grunt.loadNpmTasks('grunt-contrib-watch');
    grunt.registerTask('default',['watch']);
}
</pre>

A questo punto quando lavoriamo ci basterà lanciare grunt ed avremo il watch sui sass che, appena modificati, verranno compilati dalla cartella sass e spostati nella cartella styles.

<pre class="lang:sh decode:true " >$ grunt
</pre>

<div class='kindleWidget kindleLight' >

</div>



 [1]: http://magni.me/wp-content/uploads/2014/04/grunt-logo-1.png
