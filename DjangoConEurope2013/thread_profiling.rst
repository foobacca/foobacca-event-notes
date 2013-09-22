Profiling
---------

https://speakerdeck.com/amjith/thread-profiling-in-python

* cprofile is easy to use
* run snake run - visualise cprofile output
* but in production, cprofile is too slow (100% overhead)
* in production, do targeted profiling - pick particular functions
* New Relic do this for django, flask, bottle - view handlers, sql calls - but can end up with "Application code" being it all

statistical profiler

* interrupt -> inquire -> collate
* interrupt - see what function is being run when you interrupt
* inquire - get stack trace
* collate - store and then generate reports

INTERRUPT by unix signals OR background thread

unix socket

* + v accurate
* - unix only
* - ignored in mod\_wsgi
* - can't interrupt C extensions

threads

* + cross platform
* + mod\_wsgi compatible
* - inaccurate for CPU heavy tasks
* - can't interrupt C extension

talk - how the GIL works in python by ???

COLLATE

* dictionary - key is tuple of file, line no, function - no context
* call tree - preserve context

existing tools

- statprof - signals, cli
- PLOP - signals, D3 call graph
- New Relic - threads, GUI
