Introducing Wagtail
===================

Slogan is "Django content management made beautiful"

- Matt Westcott
- @wagtailcms
- http://wagtail.io/
- https://github.com/torchbox/wagtail/

Torchbox is the company

- "We do digital stuff for the good guys"
- clients are charities, NGOs and education.
- Use drupal and django.
- http://www.torchbox.com/

Wagtail is a new django based CMS - looks very clean.  Built for RCA originally

Why a new CMS?
--------------

- There are already 20ish Django based CMS, and one or two non-Django based ones
  ...  Hard to evaluate without spending lots of time
- Flexibility (we're against it) (sometimes)
- conventional CMS (eg drupal) has blocks that can be rearranged very flexibly -
  so you get block based websites, and your code has to cope with lots of eventualities
- so for RCA give a fixed set of fields to fill in

.. code-block:: html+django

    {% load image_tags rich_text %}

    <div>
        <h1>{{ self.title }}</h1>

        {% image ... %}
    </div>

The self is the modelpage being rendered

Your data, your way
-------------------

show complex data models

.. code-block:: python

    EventPage.objects.filter(
        date__gte=datetime.today(),
        ...
    )

Django-ish, but not too Django-ish

instead of model-view-template, have wagtail URL router -> model -> template

Versioning and workflow
-----------------------

- Might have several versions of a page around - edit, 2nd person approves/publishes the edit.
- so we have to save (at least) 2 versions of each page, and be able to show preview
- solution - django-modelcluster - patch ForeignKey.  Keep edits around in the object
  without saving to the database.  For longer storage, pages get serialised to JSON!
- "some fairly evil hacking around with Django internals"
