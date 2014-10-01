---
title: Plugin shadowbox per wordpress
author: Matteo Magni
layout: post
permalink: /2008/01/31/plugin-shadowbox-per-wordpress/
enclosure:
  - |
    |
        http://blog.ilbonzo.org/gallery/kayak.mov
        860878
        video/quicktime
        
  - |
    |
        http://blog.ilbonzo.org/gallery/kayak.mp4
        848200
        video/mp4
        
  - |
    |
        http://blog.ilbonzo.org/gallery/kayak.avi
        1519768
        video/x-msvideo
        
  - |
    |
        http://blog.ilbonzo.org/gallery/cat.wmv
        422489
        video/x-ms-wmv
        
  - |
    |
        http://images.apple.com/movies/paramount/beowulf/beowulf-tr2_h.640.mov
        120
        video/quicktime
        
  - |
    |
        http://blog.ilbonzo.org/gallery/alien.flv
        1784892
        video/x-flv
        
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
dsq_thread_id:
  - 1100507445
categories:
  - CMS
tags:
  - wordpress
---
Ho letto di questo componente [Shadowbox][1] che è una specie di Lightbox, slimbox che consente di inserire molti tipi di contenuti: non solo foto ma video da youtube, animazioni flash, pagine html, ecc.. 

Ho quindi pensato di provare a creare il mio primo plugin per wordpress integrando questo componente.

Qui intanto gli esempi di come funziona Shadowbox:

## <a name="demos">Demos</a>

### Images

<a rel="shadowbox" href="http://farm2.static.flickr.com/1177/1150569783_61dbc56834.jpg" class="option">Single Image (Flickr)</a>  
<a rel="shadowbox[Aston Martin]" href="http://blog.ilbonzo.org/gallery/aston_martin/vantage.jpg" class="option" title="Aston Martin Vantage">Image Gallery</a>

<a rel="shadowbox[Aston Martin]" href="http://blog.ilbonzo.org/gallery/aston_martin/vanquish.jpg" class="hidden" title="Aston Martin Vanquish S">image</a>  
<a rel="shadowbox[Aston Martin]" href="http://blog.ilbonzo.org/gallery/aston_martin/db9.jpg" class="hidden" title="Aston Martin DB9">image</a> 

### <a name="lgimage-demo">Large Image</a>

You may have to shrink your browser window to view the effect here. See the [handleLgImages][2] option for more information.

<table class="thumbs" border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td>
      Clipped (no resizing)
    </td>
    
    <td>
      Resized
    </td>
    
    <td>
      Draggable
    </td>
  </tr>
  
  <tr>
    <td>
      <a rel="shadowbox;options={handleLgImages:'none'}" href="http://blog.ilbonzo.org/gallery/greatwall.jpg" title="Great Wall of China"><img src="http://blog.ilbonzo.org/gallery/greatwall-thumb.jpg" alt="" /></a>
    </td>
    
    <td>
      <a rel="shadowbox" href="http://blog.ilbonzo.org/gallery/greatwall.jpg" title="Great Wall of China"><img src="http://blog.ilbonzo.org/gallery/greatwall-thumb.jpg" alt="" /></a>
    </td>
    
    <td>
      <a rel="shadowbox;options={handleLgImages:'drag'}" href="http://blog.ilbonzo.org/gallery/greatwall.jpg" title="Great Wall of China"><img src="http://blog.ilbonzo.org/gallery/greatwall-thumb.jpg" alt="" /></a>
    </td>
  </tr>
</table>

### Thumb Gallery

Unlike the previous image gallery, this one is triggered by thumbnail links. It also uses a [skip counter][3] and is [continuous][4].

<table class="thumbs" border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td>
      <a rel="shadowbox[MustangThumbs];options={counterType:'skip',continuous:true}" href="http://blog.ilbonzo.org/gallery/mustang/red.jpg"><img src="http://blog.ilbonzo.org/gallery/mustang/red-thumb.jpg" alt="Red" /></a>
    </td>
    
    <td>
      <a rel="shadowbox[MustangThumbs];options={counterType:'skip',continuous:true}" href="http://blog.ilbonzo.org/gallery/mustang/blue.jpg"><img src="http://blog.ilbonzo.org/gallery/mustang/blue-thumb.jpg" alt="Red" /></a>
    </td>
    
    <td>
      <a rel="shadowbox[MustangThumbs];options={counterType:'skip',continuous:true}" href="http://blog.ilbonzo.org/gallery/mustang/grey.jpg"><img src="http://blog.ilbonzo.org/gallery/mustang/grey-thumb.jpg" alt="Red" /></a>
    </td>
  </tr>
</table>

### Flash

<a rel="shadowbox;width=400;height=300" class="option" title="Girl Skipping" href="http://blog.ilbonzo.org/gallery/skip.swf">Single SWF</a>  
<a id="flash1" rel="width=600;height=450" class="option" title="Hollywood or Bust" href="http://blog.ilbonzo.org/gallery/old_man.swf">SWF Gallery</a>  
<a rel="shadowbox;width=600;height=450" class="option" title="Alien" href="http://blog.ilbonzo.org/gallery/alien.flv">Flash Video</a>

### Movies

<a rel="shadowbox;width=292;height=218" class="option" title="Unfortunate Kayaker" href="http://blog.ilbonzo.org/gallery/kayak.mov">Single Movie (mov)</a>  
<a rel="shadowbox;width=292;height=218;options={showMovieControls:false}" class="option" title="Unfortunate Kayaker" href="http://blog.ilbonzo.org/gallery/kayak.mp4">Single Movie (mpeg-4, controller disabled)</a>  
<a rel="shadowbox;width=318;height=218;options={autoplayMovies:false}" class="option" title="Unfortunate Kayaker" href="http://blog.ilbonzo.org/gallery/kayak.avi">Single Movie (avi, autoplay disabled)</a>

<a rel="shadowbox;width=320;height=240" class="option" title="Curious Cat" href="http://blog.ilbonzo.org/gallery/cat.wmv">Single Movie (wmv)</a>  
<a rel="shadowbox;width=640;height=272" class="option" title="Beowulf Trailer" href="http://images.apple.com/movies/paramount/beowulf/beowulf-tr2_h.640.mov">Apple.com Trailer</a>  
<a rel="shadowbox;width=405;height=340" class="option" title="David Beckham" href="http://www.youtube.com/v/wbzLpteC8ng&autoplay=1">YouTube</a>  
<a rel="shadowbox;width=405;height=340" class="option" title="While My Ukulele Gently Weeps" href="http://video.google.com/googleplayer.swf?docid=1352016870638076087&autoplay=1">Google Video</a>  
<a rel="shadowbox[Movies];width=405;height=340;options={continuous:true}" class="option" title="YouTube" href="http://www.youtube.com/v/JPSzcRbFArA&autoplay=1">Movie Gallery</a>  
<a rel="shadowbox[Movies];width=292;height=218" class="hidden" title="QuickTime" href="gallery/kayak.mov">MOV</a>

<a rel="shadowbox[Movies];width=320;height=240" class="hidden" title="Windows Media" href="http://blog.ilbonzo.org/gallery/cat.wmv">WMV</a>  
<a rel="shadowbox[Movies];width=600;height=450" class="hidden" title="Flash Video" href="http://blog.ilbonzo.org/gallery/alien.flv">FLV</a>  
<a rel="shadowbox" class="option" title="Google.com" href="http://www.google.com/">External Website</a>  
<a rel="shadowbox" class="option" title="This page" href="http://blog.ilbonzo.org/">This page</a>  
<a rel="shadowbox[Mixed];options={counterType:'skip',continuous:true}" class="option" title="JPG" href="gallery/aston_martin/vanquish.jpg">Mixed Content Gallery</a>  
<a rel="shadowbox[Mixed];width=520;height=390" class="hidden" title="SWF" href="http://blog.ilbonzo.org/gallery/caveman.swf">swf</a>

<a rel="shadowbox[Mixed];width=292;height=218" class="hidden" title="MPEG-4" href="http://blog.ilbonzo.org/gallery/kayak.mp4">movie</a>  
<a rel="shadowbox[Mixed]" class="hidden" title="IFRAME" href="http://blog.ilbonzo.org/">iframe</a> 

Il Plugin è molto semplice, basta caricare la cartella che si ottiene scompattando l&#8217;archivio compresso nelal cartella /wp-content/plugins, andare nella parte di amministrazione e attivare il plugin.

Per utilizzarlo basta aggiungere **rel=&#8221;shadowbox&#8221;** ai link che volete aprire in questo modo.

ecco un po&#8217; di esempi presi dal sito di [shadowbox][1]

`</p>
<h3><a name="markup">Markup</a></h3>
<p>The simplest way to use Shadowbox is through your HTML markup. At the very least, you must add a <code>rel="shadowbox"` attribute to your links. For example, say you have this link to an image on your page:

<pre>&lt;a href="myimage.jpg">My Image&lt;/a></pre>

In order to set up this link for use with Shadowbox, simply change it to this:

<pre>&lt;a href="myimage.jpg" rel="shadowbox">My Image&lt;/a></pre>

If you would like to display a title for your image, simply add a `title` attribute to the link.

<pre>&lt;a href="myimage.jpg" rel="shadowbox" title="My Image">My Image&lt;/a></pre>

You must explicitly tell Shadowbox the dimensions to use to display content other than images. This is done by adding a few parameters to the end of the `rel` attribute, separated by semi-colons (like a CSS style declaration). To specify a movie's height and width, use the `height` and `width` parameters. Note: unlike in CSS, these values must always be specified in pixels.

<pre>&lt;a href="mymovie.swf" rel="shadowbox;height=140;width=120">My Movie&lt;/a></pre>

Additionally, you may set Shadowbox options on a per-link basis. To do this, you must include a [JSON][5]-formatted parameter called `options`. An example could be:

<pre>&lt;a href="myimage.jpg" rel="shadowbox;options={overlayOpacity: 0.5, resize: false}">My Image&lt;/a></pre>

In addition to displaying single images and movies, Shadowbox is also capable of displaying galleries of content. In order to designate a link as part of a gallery, you must add the gallery name to the `rel` attribute between square brackets immediately following the word "shadowbox". For example, the following markup creates a gallery called "Vacation" with two pictures:

<pre>&lt;a href="beach.jpg" rel="shadowbox[Vacation]">The Beach&lt;/a>
&lt;a href="pier.jpg" rel="shadowbox[Vacation]">The Pier&lt;/a></pre>

Galleries may be composed of content of many different types. The following markup is a compressed version of the last [demo][6] above. It demonstrates how various media can be combined into a single gallery.

<pre>&lt;a rel="shadowbox[Mixed];options={counterType:'skip',continuous:true}" href="vanquish.jpg">jpg&lt;/a>
&lt;a rel="shadowbox[Mixed];width=520;height=390" href="caveman.swf">swf&lt;/a>
&lt;a rel="shadowbox[Mixed];width=292;height=218" href="kayak.mp4">movie&lt;/a>
&lt;a rel="shadowbox[Mixed]" href="index.html">iframe&lt;/a></pre>

</code>

Per ora il plugin funziona con mootools, ma è facilmente adattabile ad altre librerie javascript, visto che shqdowbox include i vari adapter per queste librerie.

*   [Yahoo! User Interface Library][7] (yahoo, dom, event, anim)
*   [Ext][8] (standalone, ext-core.js)
*   [Prototype][9] + [Scriptaculous][10]
*   [jQuery][11]
*   [MooTools][12] (requires Fx.Styles and its dependancies)
*   [Dojo Toolkit][13] (thanks Peter Higgins)

[Scarica il plugin versione 0.1][14]  
Ovviamente spero che se ci sono reeori qualcuno me lo segnali.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://mjijackson.com/shadowbox/
 [2]: #handlelgimages
 [3]: #countertype
 [4]: #continuous
 [5]: http://www.json.org/
 [6]: #demos
 [7]: http://developer.yahoo.com/yui/
 [8]: http://extjs.com
 [9]: http://prototypejs.org/
 [10]: http://script.aculo.us/
 [11]: http://jquery.com/
 [12]: http://mootools.net/
 [13]: http://dojotoolkit.org/
 [14]: http://blog.ilbonzo.org/upload/shadowbox.tar.gz