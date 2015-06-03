True beauty is on the inside, but users are shallow
===================================================

Loek Van Gent
@loek1pc
work for 1% club - platform for small projects that have a social impoact
slides - http://slideshare.net/LoekvanGent/shallow

- Idea - let's make multi-tenant site, and white-label site
- BIG refactor
- history - simple, static

how do we write better front end code?

- project true_beauty, apps heart, spirit
- two scoops - group your front-end - put template and static in overall project directory - then front end guys don't have to search across whole project

front end tools

- js requirements - bower
- structured CSS - Sass, less ...
- build front end (convert sass to css, minify) - grunt
- install grunt etc - npm
- starting to look like an entire project within the project
- django to provide data, django rest framework to provide REST API
- js framework - angular, backbone, ember, react ...

- ember cli for front end

.. code-block:: bash

   ember new good_looks
   cd good_looks
   ember app route something ...

   ember serve --proxy http://localhost:8000

Sum up

- love your front end - it's the only thing the users see
- group your front end - get all that JS etc in one place
- use tools to help structure the front end code
- start using Ember - it's the future (or angular, react ... but not backbone)
