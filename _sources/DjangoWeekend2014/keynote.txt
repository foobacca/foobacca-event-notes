Moving Targets
==============

- @brandon\_rhodes
- slides http://rhodesmill.org/brandon/slides/2014-02-cardiff/

* wolf/coyote/fox - the two ends of the spectrum ignore each other, but close things fight
* Similarly, the biggest rivalries will be between the most similar technologies (eg vi/emacs or vi/visual studio)
* the biggest arguments tend to be over the smallest differences

a moving target

* fixes problems
* adds missing features
* invalidates my complaints

Django has done a great job of being a moving target

* url mappers
* template systems
* ORMs

TemplateResponse (Django 1.3)

* request -> data -> document
* request -> data : build nested dicts/lists, in python, auth ...
* data -> document : template, interpolate data, for loops, HTML ...
* old state of the art - integration test, tested both together - compound, fragile, late
* another approach: request -> data (programmer/python test) data -> document (designer/browser test)
* became possible with TemplateResponse (1.3)
* so your view data becomes a first-class result (and can be used in debugging/testing)
* lets you write tests on day one that specify what the context will look like
* view tests: db1 -> context1, db2 -> context2 ...
* design tests: context-a -> page-a, context-b -> page-b ...
* ALSO, TemplateResponse can be modified by decorators, middleware -> less codeo

Persistent db connections (Django 1.6)

* by default Django opens a **new** db connection for *every view* it renders
* settings.py: CONN_MAX_AGE = 600 (off by default)
* skip 3-way tcp/ip handshake, skip auth
* reduce load on DB

Transactions - changes in 1.6

* if db is "serializable", you need to commit after a read before you see new data(!)
* autocommit now default for both reads and writes
* txn must be explicit

1.7 has built in data migration

**If I am not careful, my opinions tend to fossilize**
