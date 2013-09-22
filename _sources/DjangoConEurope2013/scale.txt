Does your stuff scale
---------------------

p.ota.to grew from 1 developer to 70 - with django and google app engine

scalability

- load
- functional - add more features without too much effort
- organisational - do more, hire better people
- geographic

django and google app engine
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

why?

- auto-scaling
- services and APIs
- no sys admin

caveats

- sandbox - can't run `pip install`
- file system - block store, but no traditional fs
- portability - lock in?

options for g a e

- django-nonrel - django fork with nosql back end
    - shallow learning curve, more reusable
    - BUT familiarity can be misleading, can feel 'heavy'/kludgy
- djappengine
    - built in to app engine, use appengine data store directly
    - "best of both worlds", use NDB
    - learning curve steeper, not portable
- app engine + cloud sql
    - google's version of django
    - fully supported django
    - relational database
    - more set up, not as scalable as other options

technical scaling
~~~~~~~~~~~~~~~~~

load

- planning
- caching
- offline tasks
- preparation - load tests, profiling

functional

- django!
- app engine
    - services/apis
        - memcache, email, search, images ...
    - versioning
        - 10 testable versions per app
        - A/B testing, traffic splitting
    - sdk

scaling organisation and culture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

organisational

- be a minimalist
- remove bottlenecks and overhead
- autonomy
- build lots of small apps internally - just do it
- "just make good things"

geographic

- build and deploy from anywhere - trains, pubs, beaches
