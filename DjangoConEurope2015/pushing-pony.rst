Pushing the Pony's Boundaries
=============================

- loves the Django Admin
- started coding at 14, writing games, PHP
- 6 years of building admin interfaces

Admin
-----

- Inside
- admin magic
- future of the admin

How the Admin Works
-------------------

- been there since the early days
- not the most beautiful part of the codebase
- 3 main classes
    - AdminSite
    - ModelAdmin 2000 loc
    - ChangeList

AdminSite

- AdminSite encapsulates an instance of the admin site
- login, logout ... are methods on the AdminSite object (see get_urls() )
- some dynamic urls generated from self._registry.items()
- can set eg list_display when registering your model (prob not a great idea ...)
- can set site_title etc in SiteAdmin

ModelAdmin

- encapsulates all admin options and functionality for any given model
- actions_on_top actions_on_bottom - add actions to list view
- fieldsets - linked models
- list_display_links - add links in list view
- list_editable - eg checkboxes in list view (though look at bug 11313 - multiuser)
- ordering - can override model ordering in the admin
- radio_fields - have radio buttons when editing model object, instead of select
- save_as - "save as new" - edit a model and save as new object
- show_full_result_count - showing full count - can be used to turn off - eg slow NoSQL databases

ChangeList

- field errors, searching, ordering ...

Magic Tricks
------------

Django Girls
~~~~~~~~~~~~

- started 9 months ago
- 60 workshops have happened - 1245 women have been taught - N America, S America, Africa, Europe
- all run from Django site
- multilingual
- each organiser can access the admin, but only their own page/event
- need more advanced permissions
- use djangosuit (?) to add a nice sidebar
- maintenance team of 6 people who have superuser access
- EventAdmin - get_queryset() - filter events by team user is in
- get_form() - if not superuser - override queryset to filter by user/team
- some organisers edited an old event to create new event - solve by "only edit future events"
- use get_readonly_fields() (django 1.8) - if not superuser, if not object.event.is_upcoming, return field list
- display all organisers as list on ChangeList view
- show organizer column in ChangeList view
- display status of event - custom method fields "is_event_over"
- display images in list - custom field get_logo_display() - returns HTML link
- custom actions - a way to publish multiple events with one click
- select multiple in list view - add custom action to select box
- actions = ['show_on_homepage'] - add method (queryset update) and add short_description

Don't
~~~~~

- use django admin as your user facing interface
- waste too much time trying to customise

Do
~~

- make your managers life easier with small tricks
- ensure your admins can't break the site (with too much power)

The Future
----------

- admin doesn't rely on many other bits of Django - backwards compatibility has costs and benefits
- admin created when best practice of Django were evolving - hard to refactor - big bag of code
- django-admin2 trying - in alpha for 3 years
- django 1.9 will have an updated CSS for the admin - try it now - pip install django-flat-theme
