How does Django start?
======================

- Marc Tamlyn
- @mjtamlyn
- github.com/mjtamlyn
- slides https://speakerdeck.com/mjtamlyn/how-does-django-start

The old days
------------

(up to 1.6)

* at some point a model is imported
* metaclass: ModelBase.__new__() triggers django.db.models.loading.AppCache init
* reverse relations now work
* Most other bits of code inspect settings.INSTALLED_APPS directly

**Problem is "at some point"** - sometimes deploys can fail unpredictably

The long and winding road
-------------------------

``#3591`` bug 

- opened Feb 2007 (django 0.96 released March 2007)
- "Add support for custom app label and verbose name"
- Feb 2007 - design decision needed
- Sept 2007 - assigned to Adrian Holovaty
- Dec 2007 - accepted by Jacob
- various attempted patches
- PyCon 2008 - "The state of Django" - Adrian Holovaty - sprints
  - goals were similar
  - scope became about rewriting how django handles applications
  - class InstalledApps()
- app_label is used in lots of places - which ones should change?
- clear requirement for App.path
- 2009 - basically nothing happened
- Feb 2010 - revert to Design decision needed
- Google SoC 2010 - "medium complexity" - multiple instances of apps, avoid names clashes, i18n of app names
- Sept 2010 - "Fixed on a branch"
- 2011 - ongoing work - unpopular details (Metaclasses for Apps, reloadable app cache)
- 2012 - patch brought up to speed, conflicts, broken tests, effort died
- 2013 - migrations needed an app cache
- Dec 2013 - Aymeric takes a holiday - timezones, python 3, db txn, debug toolbar, 2 scoops review
- **and** rethink the approach, minimal change

Now
---

- ``class Apps()``
- ``class AppConfig()``
- no models.py required
- customisable verbose name
- reliable place for start up code (not just "at the bottom of models.py")
- customise label ...
- merged! -> Django 1.7

What does it mean for you?
--------------------------

- may break existing projects and libraries
- hopefully it's because you did it wrong ...
- now have much stricter startup sequence
- django.setup() configures settings, imports all applications
- trying to use the app registry before it's loaded will error "Apps not loaded"

The following will break

- modules level code which requires the apps to be loaded will break
  - eg ugettext() - use ugettext_lazy() - ugettext() requires apps to be loaded
- code relying on import order of models.py files may break
- code relying on ``for app in INSTALLED_APPS``

Good stuff

- i18n names in contrib apps
- no need for admin.autodiscover() in urls (as we have a consistent place for start up)

Use cases

- registering signals in my project specific app
- making my 3rd party app have an i18n name in admin
- customise a 3rd party app

.. code-block:: python

    from django import apps
    from django.db.models.signals import post_save

    class BlogApp(apps.AppConfig):
        name = 'blog'

        def ready(self):
            from .models import Post
            from .signals import flush_cache
            post_save.connect(flush_cache, sender=Post)

    # ...

    INSTALLED_APPS = (
        # ...
        'blog.app.BlogApp',
        # ...
    )

3rd party app with i18n verbose name

.. code-block:: python

    from django import apps

    class PonyConfig(apps.AppConfig):
        name = 'ponies'
        verbose_name = _('mor ponies')

    # ...

    INSTALLED_APPS = (
        # ...
        'ponies.apps.PonyConfig',
        # ...
    )

customise a 3rd party app

.. code-block:: python

    class MyPonyConfig(PonyConfig):

        def ready(self):
            # stuff


    INSTALLED_APPS = (
        # ...
        'myproject.apps.MyPonyConfig',
        # ...
    )

Note this makes it a little tricky to work out whether a model has been loaded.

Future
------

- AppAdmin - more advanced API for custom appearance of apps in admin
- App specific settings
- set up time customise of models - add fields, change field lengths, add indexes
