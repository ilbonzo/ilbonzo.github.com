---
title: Eliminare .svn
author: Matteo Magni
layout: post
permalink: /2009/02/23/eliminare-svn/
Hide OgTags:
  - 0
Hide SexyBookmarks:
  - 0
dsq_thread_id:
  - 1110500281
categories:
  - Development
tags:
  - subversion
---
Windows:  
`<br />
for /f "tokens=* delims=" %%i in ('dir /s /b /a:d *svn') do (<br />
rd /s /q "%%i"<br />
)<br />
`

Linux:  
`<br />
find ./ -name .svn -exec rm -rf {} +<br />
`

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>