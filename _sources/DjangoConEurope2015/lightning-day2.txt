Lightning Talks Day 2
=====================

Django and robotic telescopes
-----------------------------

Edward Gomez
http://lcogt.net

- Galaxy pictures - pretty
- 12 telescopes currently operating "the sun never rises on our telescopes"
- telescopes size of double decker bus, family car, R2D2 - clusters
- 1000 ish active users (250 astronomers, 750 school kids)
- web requests to server, then telescopes controlled
- django to take requests, schedule optimiser, save results
- image pipeline, python archive, served by django
- try it, http://bit.do/lco-dj-signup
- work on it http://lcogt.net/jobs

Real time web thing
-------------------

Craig Stone

- slides not working
- mashing django and angular
- django-angular and djangular
- use ``{% verbatim %}`` tag around angular framework

API by example
--------------

Carlos Barrobes
@technomilk

- an approach to testing across services
- before - single app
- want to split it up

  - UI in angular
  - backend in django/DRF

- want both teams to work independently
- want each part to be tested separately
- backend team should not dictate the API
- ABE - API by example - in json files
- 3 repos - backend, client, mocks
- all begins with pull request to the mocks repo

  - signed off by at least one person from each team
  - PR is documented discussion
  - ABE files is documented API

- ABE mocks are versioned dependency for both front and back end

https://github.com/txels
https://github.com/apibyexample

git-crypt
---------

Thomas
github.com/alphacc
slides - https://github.com/alphacc/djangoconeu2015

- admins have secret in git, but other users can't read secret
- transparent encrypt/decrypt when check in/out
- you need a GPG key
- brew install git-crypt
- git-crypt init /path/to/key
- files to encrypt in .gitattributes ``*.key filter=git-crypt diff=git-crypt``

http://www.theport.ch
http://www.theport.ch/portfolio-item/the-port-presentation

Using StreamingHTTPResponse for JSON & HTML
-------------------------------------------

Matthew Somerville
@dracos

- stop your server falling over with hacks and bug fixes
- request for every map boundary
- started 50M, 500M looksup ... total almost 2G
- was loading it all into memory - should have been using StreamingHTTPResponse
- then had to sort out middleware ...
- but we're not doing a generator, but was using a dictionary
- created iterdict - not really a dict, but allows generator
- new total 215 MB
- gzip with unicode caused death
- HTML version - django doesn't stream templates, so had to iterate django template
- jinja2 does support iterating template

shakeslide - Predicting landslides
----------------------------------

@DrRobParker
@g...

- Geologist at Cardiff Uni
- using Django to predict landslides triggered by earthquakes
- building a global db of landslides
- then using machine learning, models, ... for prediction
- then made website doing near real time prediction - shakeslide
- Nepal - predictions made - huge areas, real risk
- landslide dams - landslide blocks river, water builds up, bursts -> massive damage

- built 2 worker profiles
- 1 is data source provider - constantly updating
- queuing system
- 2 renders hidef images

BDD with goat
-------------

Ilja, cuescience
slides and code - https://github.com/cuescience/djangocon2015-goat

- BDD - behave lib - test written in natural language
- type annotations - use python 3 - but types specified twise
- goat is addon to behave - can then use python 3 function annotations
- context is repeated a lot - do implicit argument injection
- pip install goat
