Local Development with Docker
=============================

stefan foulis

docker-compose up - and we're running!

What is docker?  What are the benefits?
---------------------------------------

- (sort of) like a VM (lxc) but much more efficient
- great tools for building and sharing app envs
- dev/prod parity
- image is like a template - snapshot of VM
- container - an instance of an image - running app
- registry - store/share images

Basic Docker Concerts
---------------------

- docker push/pull
- hub.docker.com has various images ready to go - redis, django, postgres
- images would in layers

  - debian 8
  - python 3.4
  - django (python 3)
  - mysite v1

- docker file

.. code-block:: none

   FROM django:python3-onbuild
   RUN apt-get ...
   RUN mkdir
   WORKDIR ...
   COPY localfs to docker

Create docker-ised django project
---------------------------------

.. code-block:: bash

   docker build -t mydjangoimage
   docker run ... django-admin.py startproject mysite .
   docker run ... python manage.py runserver 0.0.0.0:8000

django-compose
--------------

- cmd line tool that runs yaml file describing stack

yaml example

.. code-block:: yaml

   web:
     build: .
     volumes:
      - .:/usr/src/app
     ports:
     links:
       # to other images below
     env:
       # set environment variables

   postgres:
     ...

   redis:
     ...

- run commands in container - including bash
- need to rebuild occasionally - new dependencies
- pdb is hard - ``docker-compose run`` - then get an interactive console
- or ``docker exec ... /bin/bash`` - then run ps ...

nice urls with proxy
--------------------

- docker - nginx proxy - reverse proxy for docker, nice magic for real URLs
- ssh termination ...

- much faster than vagrant
- can mount directories from outside the container into the container, eg for postgres data store
