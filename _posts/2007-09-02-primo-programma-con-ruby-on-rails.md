---
title: Primo programma con Ruby on Rails
author: Matteo Magni
layout: post
permalink: /2007/09/02/primo-programma-con-ruby-on-rails/
dsq_thread_id:
  - 1106588255
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - Ruby
  - Ruby on Rails
---
Un po&#8217; per i problemi con mod_ruby, un po&#8217; per la curiosità troppo forte ho iniziato a provare [Rails][1], il potente framework per la programmazione web.

L&#8217;installazione l&#8217;ho fatta tramite [Ruby Gems][2] e l&#8217;unico problema che mi ha dato ( su Debian e non su Mandriva) è stato il fatto che lo script rails per creare una nuova applicazione non era nella cartella giusta, e quindi il comando all&#8217;inizio non funzionava.  
Ecco il comando per installare Ruby via Gems:  
`gem install rails --include-dependencies`

Le applicazioni Rails saranno in /var/rails/.

Ecco passo per passo il primo programma fatto in Rails, una classica applicazione in stile Hello World.

Creiamo l&#8217;applicazione Rails:  
`<br />
nathan:/var/rails# rails hello_bonzo<br />
      create<br />
      create  app/controllers<br />
      create  app/helpers<br />
      create  app/models<br />
      create  app/views/layouts<br />
      create  config/environments<br />
      create  components<br />
      create  db<br />
      create  doc<br />
      create  lib<br />
      create  lib/tasks<br />
      create  log<br />
      create  public/images<br />
      create  public/javascripts<br />
      create  public/stylesheets<br />
      create  script/performance<br />
      create  script/process<br />
      create  test/fixtures<br />
      create  test/functional<br />
      create  test/integration<br />
      create  test/mocks/development<br />
      create  test/mocks/test<br />
      create  test/unit<br />
      create  vendor<br />
      create  vendor/plugins<br />
      create  tmp/sessions<br />
      create  tmp/sockets<br />
      create  tmp/cache<br />
      create  tmp/pids<br />
      create  Rakefile<br />
      create  README<br />
      create  app/controllers/application.rb<br />
      create  app/helpers/application_helper.rb<br />
      create  test/test_helper.rb<br />
      create  config/database.yml<br />
      create  config/routes.rb<br />
      create  public/.htaccess<br />
      create  config/boot.rb<br />
      create  config/environment.rb<br />
      create  config/environments/production.rb<br />
      create  config/environments/development.rb<br />
      create  config/environments/test.rb<br />
      create  script/about<br />
      create  script/breakpointer<br />
      create  script/console<br />
      create  script/destroy<br />
      create  script/generate<br />
      create  script/performance/benchmarker<br />
      create  script/performance/profiler<br />
      create  script/process/reaper<br />
      create  script/process/spawner<br />
      create  script/process/inspector<br />
      create  script/runner<br />
      create  script/server<br />
      create  script/plugin<br />
      create  public/dispatch.rb<br />
      create  public/dispatch.cgi<br />
      create  public/dispatch.fcgi<br />
      create  public/404.html<br />
      create  public/500.html<br />
      create  public/index.html<br />
      create  public/favicon.ico<br />
      create  public/robots.txt<br />
      create  public/images/rails.png<br />
      create  public/javascripts/prototype.js<br />
      create  public/javascripts/effects.js<br />
      create  public/javascripts/dragdrop.js<br />
      create  public/javascripts/controls.js<br />
      create  public/javascripts/application.js<br />
      create  doc/README_FOR_APP<br />
      create  log/server.log<br />
      create  log/production.log<br />
      create  log/development.log<br />
      create  log/test.log<br />
`  
Il comando rails crea la struttura dell&#8217;applicazione hello_bonzo creando una serie di cartelle e file.

Creiamo un controller vuoto:  
`nathan:/var/rails# cd hello_bonzo/<br />
nathan:/var/rails/hello_bonzo# script/generate controller Hello_bonzo<br />
      exists  app/controllers/<br />
      exists  app/helpers/<br />
      create  app/views/hello_bonzo<br />
      exists  test/functional/<br />
      create  app/controllers/hello_bonzo_controller.rb<br />
      create  test/functional/hello_bonzo_controller_test.rb<br />
      create  app/helpers/hello_bonzo_helper.rb<br />
`  
Abbiamo creato un controller vuoto, il file:  
var/rails/hello\_bonzo/apps/controller/hello\_bonzo_controller.rb  
che contiene questo codice:  
`<br />
class HelloBonzoController < ApplicationController<br />
end`

Proviamo a vedere l'applicazione lanciando il server integrato.  
Ecco il risultato:  
`<br />
nathan:/var/rails/hello_bonzo# script/server<br />
=> Booting Mongrel (use 'script/server webrick' to force WEBrick)<br />
=> Rails application starting on http://0.0.0.0:3000<br />
=> Call with -d to detach<br />
=> Ctrl-C to shutdown server<br />
** Ruby version is not up-to-date; loading cgi_multipart_eof_fix<br />
** Starting Mongrel listening at 0.0.0.0:3000<br />
** Starting Rails with development environment...<br />
** Rails loaded.<br />
** Loading any Rails specific GemPlugins<br />
** Signals ready.  TERM => stop.  USR2 => restart.  INT => stop (no restart).<br />
** Rails signals registered.  HUP => reload (without restart).  It might not work well.<br />
** Mongrel available at 0.0.0.0:3000<br />
** Use CTRL-C to stop.<br />
`  
Per me parte [Mongrel][3] perché l'ho installato (`gem install mongrel`), se no di default partirebbe webrick, il server integrato.  
Vado alla pagina con porta 3000:

http://0.0.0.0:3000/hello_bonzo

Mi dice:

> Unknown action  
> No action responded to index

non c'è metodo all'azione index

Creo il metodo index rendendo così il controller:  
`<br />
class HelloBonzoController < ApplicationController<br />
	def index<br />
	end<br />
end`

Richiamo la pagina:

> Template is missing  
> Missing template script/../config/../app/views/hello_bonzo/index.rhtml 

Manca la view.  
Creo il file:  
/var/rails/app/views/hello_bonzo/index.rhtml

Nel file scrivo:  
`<html><br />
	<br />
	<body></p>
<h1>Hello Bonzo</h1>
<p>oggi è: <%= @time %></p>
<p><%= link_to "Goodbye", :action => "goodbye" %></p>
<p>	</body><br />
</html><br />
`  
(ilcodice html viene interpretato dal browser, quindi sul post non riuscite a vederlo, dovete vedere il sorgente della pagina)  
Per usare time inserisco nel metodo index del controller la riga:  
`@time = Time.now`  
se ricarico la pagina ho:

> Hello Bonzo
> 
> oggi è: Sun Sep 02 23:43:01 +0200 2007
> 
> Goodbye 

Trasformo così il controller aggiungendo il metodo goodbye:  
`<br />
class HelloBonzoController < ApplicationController<br />
	def index<br />
		@time = Time.now<br />
	end<br />
	def goodbye<br />
	end<br />
end<br />
`  
Nella cartella /app/views/hello_bonzo  
Metto il file goodbye.rhtml:  
`<br />
<html><br />
	<br />
	<body></p>
<h1>Goodbye Bonzo</h1>
<p>Grazie di essere passato da noi</p>
<p><%= link_to "Hello Bonzo", :action => "index" %><br />
	</body><br />
</html><br />
`

Alla fine avrò una semplice applicazione in cui ho due pagine collegate tra loro da un link.  
Per ora non è molto, ma intanto comincio a prendere confidenza con Ruby, Rails e MVC.

Gabba Gabba Hey  
Bonzo

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://www.rubyonrails.org/
 [2]: http://rubyforge.org/projects/rubygems/
 [3]: http://mongrel.rubyforge.org/