Circus
------

http://blog.ziade.org/slides/djangocon2012/circus.html

(mozilla guy, tarek, site http://circus.io/ )

* typical set up - nginx, gunicorn, django, celery
* Supervision tools - supervisord 

but missing features -> circus

built on

* psutil- nice lib
* zeromq, PyZMQ (inc event loop from tornado)
* ...

we can replace gunicorn with circus, using http://chausette.readthedocs.org -
circus manages tcp socket binding, wsgi and django processes directly -
benchmark to faaster than gunicorn + gevent
