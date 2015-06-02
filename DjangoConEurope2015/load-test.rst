Using Python to load-test web apps
==================================

Yulia Zozulya

FunkLoad
--------

- Looks like TestCase
- has setUpCycle() and tearDownCycle() - run before/after threads spawned/finish
- big config file
- spawns threads (with small delay)
- each thread runs test in a loop
- why FunkLoad?
  - familiar structure (from TestCase)
  - smoke tests with unittest runners
  - benchmark can be distributed between multiple machines
  - good docs - tips and tricks for performance
  - easily extensible
- why not?
  - uses default python threading module only - single core etc
  - default reports not configurable

Multi-Mechanize Transaction
---------------------------

- Transaction class
- config file - lighter than FunkLoad
- runner - spawns threads, with delay
- threads can be grouped into UserGroup - uses subprocesses, so multicore
- why use mm t?
  - uses multiprocessing
  - report graphics more configurable (and more out of the box)
- why not?
  - API not as obvious/simple as FunkLoad
  - distributed workflow not supported out of the box

locust.io TaskSet and Locust
----------------------------

- TaskSet, Locust base classes
- TaskSet tasks can be weighted
- Locust doesn't use threads - events and greenlets
- why use?
  - greenlets much faster for i/o than pthreads
  - light web UI for monitoring
  - distributed workflow supported
  - heterogenous tests - more realistic
  - no separate config - all in python
- why not?
  - tricky terminology and relations

Why not use Python (2) ?
------------------------

- GIL
- above all use python 2
