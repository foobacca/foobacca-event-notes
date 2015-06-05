How to write a view
===================

David Winterbottom
slides - https://speakerdeck.com/codeinthehole/how-to-write-a-view

Views give you a lot of freedom - can lead to WTF moments

Separation of concerns
----------------------

- Have layers only concerned with one thing
- see also SRP - single responsibility principle
- MVC - model view controller - originally GUI, now used in web frameworks, some parts moving into the browser
- Model layer - data, business logic (the rules, aka domain logic)
- View layer - what is presented to the user
- Controller - takes in request, orchestrates model interactions, passes stuff to view

- Django - MTV - Model, Template, View - see Django FAQ
- template is roughly equivalent to view
- view is roughly equivalent to controller
- so model -> models, forms
- view -> templates, statics
- controller -> django view, user, requests, responses

What is a view

- HTTP requests into domain request, do work, translate into HTTP response

Problem

- django views are too big

  - separation of concerns is broken
  - business logic, validation done in views
  - persistence logic - start/end transaction, even SQL queries
  - persentation layer - some work done in the view

- Django does blur the layers a bit

  - models mix business logic and persistence
  - modelforms and generic CBVs mix up stuff
  - fine most of the time, enormously productive, but need to be aware of the boundaries, and sometimes step back and separate things out

- MODEL != models.py

  - moving logic so you have thin views and fat models, but that puts too much in models
  - MODEL = domain/models.py domain/forms.py domain/services.py
  - don't try and force everything into your model
  - though "service" is an over-used word

.. code-block:: python

    from ..service.service import Service

    service = Service()

- too much!! - keep it simple - simple functions are fine if they work

view smells

- pass request/response to a domain function
- validation logic
- manipulate or saving models

  - article - tom christie, dab apps - http://dabapps.com/blog/django-models-and-encapsulation/
  - any change to model, write a different function, maybe put it in model layer

- sending email, access network ...

generic CBVs

- can bend them too much

Keep views boring

- don't do anything interesting
- HTTP <-> domain
