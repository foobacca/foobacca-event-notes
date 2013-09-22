Lightning talks
---------------

single page application
~~~~~~~~~~~~~~~~~~~~~~~

- django + extjs
- django - json api
- extjs - store (from json api) -> model -> controller -> view (and back again)

Don't Trust - Check
~~~~~~~~~~~~~~~~~~~

- memcachier by Heroku - check shows memcache on EC2 3x faster
- django-tastypie - some pages 1.3s with tastypie, 34ms with django template

YOU NEED TO EXPERIMENT

- djangotune.com
- askthepony.com

django rest framework
~~~~~~~~~~~~~~~~~~~~~

Tom Christie

learning from project with over 100 contributors

- be negative - aim to be a net negative contributor
- it's your fault - you haven't made it happen yet - don't defer/wait for others
- forget about DRY - goals are simplicity, maintainability ...
- hyperlink all the things
- deprecation policy makes changes easier
- no such thing as a core dev

django-downloadview
~~~~~~~~~~~~~~~~~~~

- static file view
- filefield in a model -> ObjectDownloadView
- django not meant to stream files -> use reverse proxy to web server

django home pages - DHP
~~~~~~~~~~~~~~~~~~~~~~~

like PHP joke actually built it in Django so you can put python code in
the template

pony checker
~~~~~~~~~~~~

http://www.ponycheckup.com

run security checks remotely -> produce report

analyzed 3703 websites -> "oh the humanity"

almost no perfect sites 

- 7% in debug mode
- 97& no clickjack (1 line in 1.4)
- 83% no HTTPOnly session (default in 1.4)

what's new in Django-CMS 3.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ben - Divio

2011 - first release with front end editing

- can add front end editing to your own app
- keep end user out of admin
- don't interfere with your markup
- let the content editors play with the content, without fear -> undo easily
- keep developer friendly

improved layout when editing mode, draft and then publish

Localisation 2.0 - L20n
~~~~~~~~~~~~~~~~~~~~~~~

http://l20n.org/

Content localn vs UI localn - UI is focus for now

problems with old approach

- english centric
- one-to-one strings
- plurals (if you're lucky)

do-able now, but makes code messy and horrible

-  Isolated
-  Many-to-many
-  grammar-agnostic

managing mail in django apps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

django-mail-factory

- create your mail and defined params
- register mail
- allows for review(?)

python-deployer
~~~~~~~~~~~~~~~

- more declarative than fabric
- start interactive shell with `./client.py`
- interactive shell quite powerful
- run commands on multiple servers

60 second django project set up
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

have a project skeleto

2 scoops project layout
