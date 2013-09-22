Mock your database
------------------

* your database is slow
* why do I care - speed - faster unit tests

naive test - create objects, get stuff from query, 8 database queries

- 5.2 seconds for 1000 tests on Postgres
- 3.9 seconds for 1000 tests on sqlite

factoryboy doesn't make like quicker (but does make code simpler)

factoryboy build() - create but not save - but m2m fields cause trouble - got to 4 queries

prefetch - factory build, give pk, build other, set \_result\_cache
\_prefeteched\_objects\_cache ... Down to 1 second, 0 database queries!
but ugly code, and only works with all()

* mock library - patch class, assign pk
* 1.2 seconds, 0 database queries

Avoiding the database is faster - much bigger difference than between postgres and sqlite

A better way
~~~~~~~~~~~~

Carl Meyer - "Mocking the database usually isn't worth it" (from testing
Django talk)

mock redis in python (using dict) -> partly due to nice api, queryset

https://github.com/mjtamlyn/django-test-db

- not db at all
- patch queryset to provide api, but not hit db
- run your local tests fast, then use production db for CI
- prototype! do not bet granny on it

Now we try the naive test again -> 0 database queries, 0.7 seconds

issues

- some things don't go through queryset
- auto patching
- more filter lookups
- extensibility

future

- write code and tests naively
- use test-db locally for fast testing cycle
- deploy to CI and run same code against real DB
