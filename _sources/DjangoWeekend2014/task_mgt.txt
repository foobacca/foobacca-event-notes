Task Management with Celery & Django
====================================

- Claire Gowler
- @kitation
- https://github.com/kitation
- slides http://kitation.github.io/celery-talk/#/ (source at https://github.com/kitation/celery-talk )

Why Celery?
-----------

- When add user stories - add team design task, design review task ... sub tasks ...
- This can take 10 minutes for a form to reload - NOT GOOD

What is Celery?
---------------

- task mgt system written in python
- can offload tasks to workers
- support many messaging brokers, result backends ...
- lots of features
- lots of stuff from django-celery library is now in core celery

Getting Started
---------------

How Claire did it

- complex diagram with lots of arrows ...
- django puts task into redis, celery task picks up task, posts result to redis, django gets result

configure celery - celery.py

.. code-block:: python

    app = Celery('celery_est')
    app.config_from_object('settings')
    app.autodiscover_tasks(lambda: settings)

define task - tasks.py

.. code-block:: python

    def make_things(x):
        # does stuff

use tasks

.. code-block:: python

    make_things.delay(1)
    make_things.apply_async(task_id=...)
    result = make_things.apply_async(link=callback)

    tasks = [make_things.s(i) for i in xrange(5)]
    group_result = group(tasks).apply_async()

    result.status()
    result.ready()
    result.get()
    group_result.completed_count()
    group_result.waiting()

Tips and Tricks
---------------

- check out Flower - 3rd party monitoring webapp (and lots of other 3rd party apps)
- serialization defaults to Pickle (deprecated in 3.2) - change to JSON
- ``--autoreload`` is unreliable - restart your workers after code deploy
- everything is pending, but you know your IDs
- result retrieval has inconsistent API
- point Celery to the app with settings.py if you have old-school Django layout
