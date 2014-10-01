---
title: Finalmente si stampa
author: ilbonzo
layout: post
permalink: /2009/06/16/finalmente-si-stampa/
dsq_thread_id:
  - 1130791700
categories:
  - Development
comments: true
share: true
---
<p>Finalmente ho configurato la stampante canon iP 1500 PIXMA su Ubuntu.</p>
<p>Grazie ad un post su ubuntuforums.org:<br />
<a href="http://ubuntuforums.org/showthread.php?t=487890">http://ubuntuforums.org/&#8230;.</a></p>
<p>Ecco come ho fatto:</p>
<blockquote><p>
The first step is to open up your source list and add this to it</p>
<p><code>deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./</code></p>
<p>If you don&#8217;t know how to open up your source list you can do it by putting this in the terminal</p>
<p><code>gksudo gedit /etc/apt/sources.list</code></p>
<p>you can use whatever text editor you like to edit your source list.</p>
<p>After adding that to your source list you need to do this in the terminal</p>
<p><code>sudo apt-get update</code></p>
<p>Next you need to install these files</p>
<p><code>sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj</code></p>
<p>Cupsys will be automatically restarted and you can select printer in cupsys configuration which is<br />
http://localhost:631 or if you don&#8217;t want to do that you can go to System>Admistration>Printer>Add Printer.</p>
<p>To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description the ony thing you really have to fill in is the name. After you done filling in the information click continue. The next page is asks you to select your printer which should be Canon iP1500 USB # (Canon iP1500). Hit continue and then it will ask you for your driver, select the Canon Pixma iP1500 Ver.2.50 (en) then click on add printer.</p>
<p>To add the printer the other way once you click on add printer a new window will open up that say&#8217;s add a printer at the top and Step 1 of 3: Printer connection. As long as your printer is turned on it should show up in &#8220;Use a detected printer&#8221;, if it doesn&#8217;t you can select it in &#8220;Use another printer by speciying a port&#8221; and selecting Canon iP1500 USB # (Canon iP1500) then click forward. The next page is where you select the printer driver. The manufacturer is Canon if it already isn&#8217;t selected and the Driver is Pixma iP1500 Ver.2.50, then click forward. Finally the next screen is the printer information you don&#8217;t really have to worry about filling in the rest of the information if you don&#8217;t want to just click &#8220;Apply&#8221; and now your iP1500 printer should show up under printers.</p>
<p>Right click on your printer and then click on Print a Test Page and your printer should crank out a test page, if it doesn&#8217;t please let me know and we can try to figure out why.
</p></blockquote>
<p>Un grazie per aver creato il pacchetto:<br />
<a href=" http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon"></p>
<p>http://mambo.kuhp.kyoto-u.ac.jp/&#8230;</a></p>
