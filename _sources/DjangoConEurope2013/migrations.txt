Migrating the Future
--------------------

* Andrew Godwin, South
* andrew@aeracode.org
* (slides have lots of good diagrams) - http://speakerdeck.com/andrewgodwin/migrating-the-future
* https://github.com/andrewgodwin/django/tree/schema-alteration/
* blog http://aeracode.org/category/django-diaries/

Why replace south?

* 5 years of learning 
* poor vcs branching, and merging 
* huge migration file size 
* migrations sets get too large

south ->

* django.db.migrations - migration commands etc
* django.db.backends.schema - SQL generation, db abstraction

Changes:

* new migration format 
    * declarative - so work out state from previous migrations 
* dependencies 
    * so if two migrations are created on parallel branches, it still works 
    * dependencies explicitly stated in files 
    * create merge migration, or ask 
* squashing (of many old migrations) 
    * complications with dependencies between apps

Field API changes coming up - might be backwards incompatible ...
