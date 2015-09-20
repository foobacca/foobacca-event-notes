Testing Django CMS
==================

Iacopo Spaletti
@yakky
http://nephila.co.uk/talk/testing-apps.html#/

djangocms-helper

http://djangocms-helper.readthedocs.org/

like django-admin.py

helper file - cms_helper.py in root of project

.. code:: python

    HELPER_SETTINGS = {
        INSTALLED_APPS = [
        ]
        ...
    }

How does it work

* merge app settings with defaults ones
* run django

Does

* settings magic
* migrations
* django 1.8 TEMPLATE settings
* cms stuff

Can run any command - by default it runs the tests

* server - execute bundled project so can interact
* makemigrations - both south and django
* compilemessages/makemessages

Writing tests

* djangocms_helper.base_test.BaseTestCase - various helpers
* mock helpers - Request object set up with more stuff - get_request, post_request, get_page_request (for CMS)

.. code:: python

    request = get_request(page=, lang=, user=, path=, use_middlewares=)
    request.COOKIES
    request.session
    request.current_page
    request.user
    # etc

* help render django cms plugins
* BaseTestCase.get_plugin_context
* BaseTestCase.render_plugin - requires placeholder object
* this does hit the database

apphooks

* load apphooks during tests

.. code:: python

    app_page = api.create_page('page', 'project.html', ... apphook='MyApp')
    app_page.publish('en')
    self.reload_urlconf()  # <-- THIS

user logins

.. code:: python

    with self.login_user_context(self.user):
        self.client.get()

creating data

* static fixtures, code, factories
* CMS - ``_pages_data``

.. code:: python

    class MyTestCase(BaseTestCase):
        _pages_data = (
            {'', ... },
        )

* data - create CMS pages - parent, apphook
* data - create users - admin, normal etc
* data - create image objects
    * create_image()
    * create_django_image_object()
    * create_filer_image_object()

other projects that use it

* django-filer
* djangocms-blog
* djangocms-page-meta
* aldryn-* (events, newsblog)
