What it's really like building RESTful APIs with Django
=======================================================

Paul Hallett
@phalt_

Lessons learnt from converting a big legacy app to RESTful API

- Working for lyst
- old API was basically rpc style - doesn't match well to HTTP
- used just one URL api.lyst.com/rpc/v1/
- use POST even when just getting stuff
- really hard to debug

Rebuild with Django REST Framework

- Why?

  - Batteries included API framework

What was learned

- good opportunity to look at what you have and think about what's been learnt
- examine technical debt
- what does the mobile app care about

  - products
  - users, registration

- design first, code second
- resources (in the REST sense)

  - they don't always map directly to models
  - eg model Cart - loads of fields, no separation of concerns

- DRF Serializers

  - similar to Django forms
  - link to model, list the fields you want to include
  - so can have 3 resources based on single model, with different subsets of fields
  - and lots of other flexible options

- DRF Routers

  - great for a CRUD based service, but if different might ignore it

- DRF Permissions

  - set DEFAULT_PERMISSION_CLASSES to AdminOnly
  - then set them for each view with permission_classes class attribute

- DRF Authentication

  - even if you have one consumer, should still have auth
  - I recommend token auth for simple cases
  - more complex, use OAuth2

    - bit of a headache to install, but much more powerful
    - eg can expire a permission
    - pip install django-oauth2-toolkit

HTTP

- HTTP only provides so much
- HTTP checkout (process and purchase items)
  
  - initial thought make a new HTTP verb
  - went for ``HTTP POST https://api.lyst.com/cart/checkout/``
  - pass in ID for card

Asynchronous

- shouldn't care about other things going on
- timeouts
- clients can poll
- we tried "web hook"

  - callback_url, push_notification
  - send a ``HTTP1.1 202 ACCEPTED``

Documentation

- your API can be great, but without docs it's a bad API
- swagger can auto-generate docs
- but sometimes you're bending the standard REST rules, so just wrote our own
- in particular doc the auth - how do I get a token
- give some curl examples
