Fractal Architectures
---------------------

twitter: @lvh email: ``_@lvh.io``

web apps without centralised data stores

fractal

- app that has everything required to deal with requests
- server has multiple instances of app
- multiple servers

* ``n*k`` databases!
* don't we want to avoid sharding?
* well - if we plan to architect this way, we can work with it and it has advantages
* helps if most users are working with own data - eg email web UI
* practicality beats purity - so leave SMTP as external service (eg mailgun)
* persistence - use sqlite for short term instance (or axiom - object store built on top of sqlite)

* aside - axiom is really nice, simple, sqlite only, does migrations
* lvh/axiombook - docs
* alternatives - redis, postgres (each instance has own db) ...

* long term storage - need it for backup, load spreading, etc - S3 etc - dropbox?!?
* manhole - ssh to server, python shell with access to full server objects
* using twisted for async (single threaded) as axiom blocks - but sqlite is really fast
* local - really low latency
* computation is rarely the bottleneck - getting data to right place at right time is

problems

- some of my data doesn't fit
    - aggregate data across many users
    - world data used by many users
    - solutions:
        - duplication (for small-ish things that don't change too much)
        - delegation (sharded across local instance, but tight coupling)
        - separation (have separate stores that aren't users)

- querying across stores is hard
    - analytics -> use separation
    - big data -> specialised tools
    - transactions ->
        - dblink, some tools,
        - paxos,
        - raft (distributed algorithm)
