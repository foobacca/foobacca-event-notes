Getting past Django ORM limits with Postgres
--------------------------------------------

"postgres is the emacs of databases"

* postgres has many many data types - but django does least common denominator across supported dbs
* Indexes - lots of variety - ``CREATE INDEX CONCURRENTLY``
* array type - eg good for tags

* ``pip install djorm-ext-pgarray djorm-ext-expressions``
* user ArrayField, SqlExpression

extensions

- dblink - link between db instances
- citext - case insensitive
- fuzzy string matching
- hstore 
    - key/value store within postgres 
    - create as column 
    - django_hstore support it 
    - ``hstore.Manager()``, ``hstore.DictField()`` ...
- json
    - pg 9.2 can use PLV8
    - pg 9.3 more powerful
- ... (many more)

queueing

- celery can kill database
- pg has pub/sub queue
- celery backend - trunk - uses pg queue stuff

text search

- pg has rich full text search
- ``import djorm_pgfulltext`` - SearchManager, VectorField ... mymodel.objects.search(...)

indexes

- btree, generalised inverted index (GIN), generalised search tree (GIST), k nearest neighbours (KNN), space partitioned GIST (SP-GIST) ... !!
- btree as default
- GIN - multiple values in one column (array/hstore)
- GIST - full text, shapes, GIS

geospatial

- shape types
- geodjango

read only

- flip site into read only mode - do migrations!
- django-db-tools - dbtools.middleware.ReadOnlyMiddleware, settings.READ_ONLY_MODE (or from environment variable ...) - null user session, disable database ...

connections

- psycopg2:connect - no persistent connections until 1.6
- can use pg bouncer
- django-postgrespool, djorm-ext-pool, django-db-pool
