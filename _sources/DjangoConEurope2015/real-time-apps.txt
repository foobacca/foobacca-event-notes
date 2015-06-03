Effortless real time apps in Django
===================================

Aaron Bassett
@aaronbassett
slides - https://speakerdeck.com/aaronbassett/effortless-real-time-apps-in-django

- 1996 - iframes - can refresh part of web page
- ajax - do polling request
- long polling - open request, keep open until something to say, then start new request
- all are HACKY
- 2010 - websockets - effortless real time apps

- short polling - 100000 users poll every system, 871 byte header -> 83MB per second
- websockets - 0.2 MB per second
- also save data for mobile users

- http://swampdragon.net python package
- uses django, tornado and redis
- redis is in-memory key value store, can also write to disk, pubsub built in
- tornado - python, non-blocking webserver
- django

- browser - tornado - redis - swampdragon/django - postgres

- build another todo app

.. code-block:: shell

   pip install swampdragon
   apt-get install redis  # or brew - but windows not supported, use VM, cloud ...

- swamp dragon has dragon admin, similar to django-admin.py, createproject command with standard structure
- adds settings to settings.py and creates server.py - similar to manage.py, but runs tornado server
- in production, do some WSGI thing

- Code - swampdragon.models.SelfPublishModel - mixin, when model saved, push object to redis
- uses serializers, convert python object to json, so browser can consume it
- swampdragon.serializers.model_serializer - then subclass it for your model
- can feel similar to django-rest-framework - but not quite interoperable, branch of swampdragon supports DRF serializers
- then have routers, analagous to views, swampdragon.route_handler.ModelRouter
- methods - get_list, create, delete, get_object ...

- use Angular.js for browser (but can use any other js framework, or raw js if you want)

.. code-block:: javascript

    $dragon.subscribe('todo-item', $scope.channel, {todo_list__id: 1})
    $dragon.getList('todo-item', ...)
    $dragon.onReady(function() {
        $dragon.subscribe(...);
        $dragon.getList(...);
        $dragon.getSingle(...);
    });

    $dragon.onMessageChannel(
        ...
    );

 code at https://github.com/aaronbassett/djangocon-swampdragon

- more complexity - more things to manage/go wrong
- so use PaaS - firebase, pusher, pubnub ...
- DaaS (database as a service)

http://www.leggetter.co.uk/2013/12/09/choosing-realtime-web-app-tech-stack.html

Using Pusher instead - rewrite the SelfPublishModel - don't need Router then
Can use pusher angular library

https://github.com/aaronbassett/djangocon-pusher

Working on stuff for Glasgow Council
requirement is to see when someone else is trying to edit thing at same time as you
only want to see notifications for single object - so create per-object channels

created django-pusherable package - on pypi and github
