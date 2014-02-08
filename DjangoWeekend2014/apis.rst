APIs are Awesome
================

Paul Hallett @phalt\_ http://phalt.co - working at hubbub (crowdfunding stuff)

* eg google, twitter, facebook, linkedin
* Marvel Comics! pokeapi.co (pokemon) !
* pokeapi is Django - why not Flask etc? - 'cos of awesome packages

**Live demo** using tastypie (pokeapi)

* model with name field
* api.py
* create a ModelResource class, with Meta class with queryset
* add resource to urls.py
* runserver, test with http command
* https://github.com/phalt/tastypie_demo

REST?
-----

HTTP
~~~~

* HTTP VERBs (POST/PUT, GET, PUT, DELETE) = (CREATE, READ, UPDATE, DELETE)
* PUT vs POST: POST twice can create duplicate copies
* status codes - 200, 404, 403 (access denied), 204 (no content)

Stateless
~~~~~~~~~

* web browsers aren't stateless - cookies
* REST auth could use token in headers, OAuth

HATEOAS
~~~~~~~

* hypermedia as the engine of app state
* basically, include links to stuff in the responses

Confusion
---------

Twitter - says RESTful - but ...

- POST /direct_messages/destroy/ - should be DELETE /direct_messages/[ID]

flickr

- POST /services/rest/?method=flickr.activity.userComments - always POST!
- should be GET /services/rest/comments/[user id]/

Why do people get REST wrong?

REST is NOT a standard

Webhooks
--------

* eg pokemon text - text character name to number, get response
* web: request -> service -> response
* webhook: action -> external service -> HTTP POST to your own service
* webhook example: mandrill receive email on your behalf and hit a URL on your website with JSON representing the received email
