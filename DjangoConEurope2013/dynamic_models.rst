Dynamic Models in Django
------------------------

classic - models defined in development - inflexible

use cases

- custom content types for CMS eg. add end date
- customised products for an ecommerce shop
- clinical research forms

- config by domain experts is better than code customisation by developers
- dynamic models reduce the number of deployment cycles

As a user I 

- want to maintain my dynamic models easily with understanding django
- don't want to care what is static or dynamic
- search across both

As a developer

- want dynamic models to be integrated (admin, migrations, reversion ...)
- want to apply same API as for static
- any db
- customisable front end

criteria

- performance
- query-bility
- standard tools
- suuprted backend
- complexity/maintainability

EAV

- put attribute pairs in rows
- django-eav and eav-django
- not great performance

serialise dictionaries

- django-djsonfield
- django-picklefield
- django-dynamic-model

runtime schema updates

- use south etc
- dynamic-models, django-dymo, django-dynamo - all proof of concept really
- django-mutant - most mature currently

database specific

- hstore
- nosql
