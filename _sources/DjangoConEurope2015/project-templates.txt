Project templates - alternatives and tools
==========================================

Emmanuelle Delescolle

What does a Django project look like?

- having a core app with most logic bothers me
- saw talk - Mark Lavin - Anatomy of a Django Project

  - a Django project is not a thing

- put more things in the base project directory

  - environ.py.dist
  - manage.py
  - requirements.txt
  - settings.py
  - urls.py

settings.py

- Put ``project`` at top of INSTALLED_APPS list - load my stuff first
- template loading magic

- Use the ``--template`` argument to ``django-admin.py startproject``
- Various availabe on the internet
- template looks pretty similar to project, but

  - use dir name project_name - converted to your actual project name
  - in files, can use ``{{ project_name }}`` and that will also be converted
  - but only python source files are template-able by default
  - want to do stuff in sass, create a virtualenv, ...

Solution

- cookiecutter by audreyr and pydanny
- every file is template-able (using jinja2)
- you can add hooks for more automation

.. code-block:: bash

    $ cookiecutter django_template/cc_project_app
    # questions asked to set variables

- cookiecutter template is similar to django project template, but directory name can be ``{{ cookiecutter.project_name }}``
- cookiecutter.json defines the questions/variables used
