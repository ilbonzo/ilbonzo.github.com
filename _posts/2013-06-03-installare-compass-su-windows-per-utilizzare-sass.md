---
title: Installare Compass su Windows per utilizzare Sass
author: ilbonzo
layout: post
permalink: /2013/06/03/installare-compass-su-windows-per-utilizzare-sass/
thesis_title:
  - Installare Compass su Windows per utilizzare Sass
pdrp_attributionLocation:
  - end
thesis_description:
  - piccolo howto per configurare Compass su windows al fine di lavorare con Sass
thesis_keywords:
  - sass, compass, css
thesis_thumb:
  - http://magni.me/wp-content/uploads/2013/06/sass.png
dsq_thread_id:
  - 1354831746
categories:
  - css
  - windows
tags:
  - Compass
  - Sass
---
[<img src="http://magni.me/wp-content/uploads/2013/06/sass-compass-300x148.png" alt="sass-compass" width="300" height="148" class="alignleft size-medium wp-image-825" />][1]Da poche settimane ho la &#8220;fortuna&#8221; di dover lavorare in ambiente Windows, quindi mi sto scontrando con la configurazione dell&#8217;ambiente di lavoro.  
  
  
Ecco un piccolo howto per configurare **[Compass][2]** su windows al fine di lavorare con **[Sass][3]**:

1.  Installare Ruby sulla macchina:  
    <http://rubyinstaller.org/downloads/>
2.  Aprire il prompt di MS-DOS con Ruby
3.  Installare le gemme  
    `$ gem update --system<br />
$ gem install compass`
4.  Verificare che compass sia installato correttamente lanciare il comando  
    `<br />
ruby 2.0.0p195 (2013-05-14) [i386-mingw32]</p>
<p>C:\Users\magnim>compass -v<br />
Compass 0.12.2 (Alnilam)<br />
Copyright (c) 2008-2013 Chris Eppstein<br />
Released under the MIT License.<br />
Compass is charityware.<br />
Please make a tax deductable donation for a worthy cause: http://umdf.org/compass<br />
` 

*L&#8217;installazione è completa.*

**Compilare i .scss**  
Per generare i css lanciare da riga di comando:  
`<br />
C:\Users\magnim>compass compile --config compass.config.rb`

**Compass in background**  
Per avere compass che in background genera i css che vengono modificati lanciare da riga di comando:  
`<br />
C:\Users\magnim>compass watch --config compass-config.rb`

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://magni.me/wp-content/uploads/2013/06/sass-compass.png
 [2]: http://compass-style.org/ "Compass Style"
 [3]: http://sass-lang.com/ "Sass"