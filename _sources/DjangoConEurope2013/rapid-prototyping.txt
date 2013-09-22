Django for rapid prototyping
----------------------------

from twilio

A little history

- naval battles in the American Civil War
- drove boats through (old) mine field in Battle of Mobile(?) Bay
- "damn the torpedos"
- sometimes the best thing to do is grit your teeth and go full speed ahead

- take part in lots of hackathons
- feed junk food and caffiene to developers and see what happens
- learnt a lot about prototyping (and django in that role)
- "throw away code" to get stuff going - but weird, we don't normally throw code away
- do try to avoid "proto-duction"

django is good for prototyping is good because:

- pedigree (built for newsroom) good for rapid getting stuff done
- flexible

- foreman is useful tool - make file
- two scoops project - good basic layout
- plato (from mozilla) - good for security, but django 1.3, uses jinja templating

static files - django.contrib.staticfiles is good - look inside both project and application folders

heroku good to get up and running quickly

config management really pays off 

- chef recipes for django on ubuntu precise - nginx, gunicorn, ...
- salt also good

REST API

- tasty pie
- django rest framework
    - more tightly coupled
    - bit more time to set up, but lets you work with Django Views
    - easy browsable interface

social auth

- rats nest - lots of options
- django-social-auth seems to be the best option currently, bit of set up required
- django-allauth also a decent option, good for facebook

south migrations

celery as task queue is really good part of django ecosystem

- can use db as back end for small instances, rabbitmq later
- config mgt helps

testing

- still need to do testing - the mistakes you make twice are the ones that kill you
- nose and django test client
