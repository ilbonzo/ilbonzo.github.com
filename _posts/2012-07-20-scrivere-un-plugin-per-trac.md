---
title: Scrivere un plugin per Trac
author: Matteo Magni
layout: post
permalink: /2012/07/20/scrivere-un-plugin-per-trac/
Hide SexyBookmarks:
  - 0
Hide OgTags:
  - 0
thesis_thumb:
  - http://blog.ilbonzo.org/wp-content/uploads/2012/07/trac_logo_thumb.png
dsq_thread_id:
  - 1102850748
pdrp_attributionLocation:
  - end
categories:
  - Development
tags:
  - Python
  - Trac
---
[<img src="http://magni.me/wp-content/uploads/2012/07/trac_logo-150x73.png" alt="" title="trac_logo" width="150" height="73" class="aligncenter size-thumbnail wp-image-659" />][1]  
Recentemente mi sta capitando spesso di dover mettere le mani su <a href="http://trac.edgewall.org/" title="Trac Project Management"  target="_blank">Trac</a>, il gestore di progetti scritto in *Python*.  
Ecco quindi un piccolo tutorial su come scrivere un plugin per questo sistema.

Creiamo le directory che conterranno il codice:

<pre class="brush:bash">$ mkdir bonzo-plugin/
$ mkdir bonzo-plugin/bonzo/
</pre>

&nbsp;

Scriviamo il primo file, il quale conterrà il codice principale del plugin:

<pre class="brush:bash">$ vim bonzo-plugin/bonzo/bonzo.py</pre>

&nbsp;

Ecco il cuore del nostro plugin che semplicemente genera una nuova voce di menu &#8220;bonzo&#8221; che permette di aprire una nuova pagina di url [/bonzo].

<pre class="brush:python"># Bonzo plugin
import re
from genshi.builder import tag
from trac.core import *
from trac.web import IRequestHandler
from trac.web.chrome import INavigationContributor, ITemplateProvider
class BonzoPlugin(Component):
    implements(INavigationContributor, IRequestHandler, ITemplateProvider)
    # INavigationContributor methods
    def get_active_navigation_item(self, req):
        return 'Bonzo'
    def get_navigation_items(self, req):
        if 'TRAC_ADMIN' in req.perm: #QUESTO PERMETTE DI GESTIRE I PERMESSI DI QUESTO MENU
            yield ('mainnav', 'bonzo',
                tag.a('Bonzo', href=req.href.bonzo()))
    # IRequestHandler methods
    def match_request(self, req):
	if 'TRAC_ADMIN' in req.perm: #QUESTO PERMETTE DI GESTIRE I PERMESSI DI QUESTa pagina
        	return re.match(r'/bonzo(?:_trac)?(?:/.*)?$', req.path_info)
    def process_request(self, req):
        data = {}
        # This tuple is for Genshi (template_name, data, content_type)
        # Without data the trac layout will not appear.
        return 'bonzo.html', data, None
    # ITemplateProvider methods
    # Used to add the plugin's templates and htdocs 
    def get_templates_dirs(self):
        from pkg_resources import resource_filename
        return [resource_filename(__name__, 'templates')]
    def get_htdocs_dirs(self):
        return []
</pre>

&nbsp;

Per poter visualizzare la pagina dobbiamo scriver il nostro template che utilizza <a href="http://genshi.edgewall.org/" title="Genshi template languige" target="_blank">Genshi</a> come template language.

<pre class="brush:bash">$ vim bonzo-plugin/bonzo/templates/bonzo.html</pre>

&nbsp;

<pre class="brush:php">
&lt;html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:py="http://genshi.edgewall.org/"
      xmlns:xi="http://www.w3.org/2001/XInclude">
  &lt;xi:include href="layout.html" />
  

  
    <div id="ctxtnav" class="nav">
  
</div>

    

<div id="content" class="helloworld">
  <h1>
    Bonzo
  </h1>
      
</div>
  
&lt;/html>
</pre>

&nbsp;

A questo punto dobbiamo inserire il tutto in un modulo e per ciò ci basta fare un semplice file di una riga.

<pre class="brush:bash">$ vim /bonzo-plugin$ vim bonzo/__init__.py</pre>

&nbsp;

<pre class="brush:python"># Bonzo module
from bonzo import *
</pre>

&nbsp;

Finito, ora non ci resta che fare deploy del plugin.  
Creiamo il file di setup dove andiamo a mettere il nome del Plugin, la sua versione e andiamo ad settare quale sarà la directory contenente i templates.

<pre class="brush:bash">$ vim bonzo-plugin/setup.py </pre>

&nbsp;

<pre class="brush:python">from setuptools import find_packages, setup

# name can be any name.  This name will be used to create the .egg file.
# name that is used in packages is the one that is used in the trac.ini file.
# use package name as entry_points
setup(
    name='TracBonzo', version='0.1',
    packages=find_packages(exclude=['*.tests*']),
    entry_points = """
        [trac.plugins]
        bonzo = bonzo
    """,
    package_data={'bonzo': ['templates/*.html']},
)
</pre>

&nbsp;

Diamo il seguente comando per creare l&#8217;egg.

<pre class="brush:bash">$ python setup.py bdist_egg</pre>

&nbsp;

Se non ci sono errori ci ritroviamo una directory /dist con dentro un file .egg  
Ora abbiamo due strade:

*   Installare direttamente il plugin nella istanza di trac
*   installare il plugin a livello di environment

Per il primo caso ci basta copiare il file .egg dentro la directory /plugins dell&#8217;istanza di Trac e riavviare il webserver.  
Nel secondo caso, per installarlo nel virtual env posizionato in /var/trac-env, possiamo dare i seguenti comandi:

<pre class="brush:bash">sudo mkdir /var/trac-env
cd /var/trac-env/
sudo virtualenv python
sudo /var/trac-env/python/bin/easy_install   http://svn.edgewall.org/repos/trac/tags/trac-0.11
sudo /var/trac-env/python/bin/easy_install dist/TracBonzo-0.1-py2.6.egg</pre>

&nbsp;

Dopo aver riavviato il web server il plugin è disponibile nell&#8217;enviroment e basta attivarlo attraverso l&#8217;admin plugin.

<div class='kindleWidget kindleLight' >
  <img src="http://magni.me/wp-content/plugins/send-to-kindle/media/white-15.png" /><span>Send to Kindle</span>
</div>

<a rel="author" href="https://plus.google.com/111433366670841346629?rel=author"  >Google+</a>

 [1]: http://magni.me/wp-content/uploads/2012/07/trac_logo.png