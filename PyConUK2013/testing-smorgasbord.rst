========================
A smorgasbord of testing
========================

* David Winterbottom
* tangentlabs
* django-oscar

kent beck - "my philosophy is to test as little as possible to reach a given level of confidence"

stages

* write tests at all
* write readable tests
* write fast readable tests

Dexterity
=========

(using nose)

run parts of test suite - https://github.com/alonho/nosecomplete

feature
-------

* custom test runner - turn things on and off
* ``--with-specplugin`` - BDD-style output

refactor a feature
------------------

* ``--attr=shipping`` - explicit decorators
* ``--select-tests=shipping`` - more automatic

fix failing tests
-----------------

* fail fast
* editor friendly paths ``--with-progressive`` - give vim line to open at line
* no plugins
* parallelise ``--processes=8`` and tox -> detox

Speed
=====

Getting out of the zone as test suite takes longer - 10-15 seconds can be too long.

split tests into 3 directories

* unit - don't hit db, all very fast
* integration - hit db etc  ( blog.codewhisperer.com/2010/10/16/integrated-tests-are-a-scam
* functional - selenium, high level

they changed from 400 tests in 50 seconds to 700 tests in 12 seconds

* use fast (md5) password hasher in tests
* ``--processes=8``

Readability
===========

Book: xUnit Test Patterns

* bad naming
* heavy set up
* unclear assertions
* not clear what test does
* sloppy coding

Useful libraries

* PyHamcrest - ``assert_that(shipping.charge, is_(equal_to(D('4.99))))``
* should_dsl - ``user.email |should| contain("@")``
* https://wiki.python.org/moin/PythonTestingToolsTaxonomy

