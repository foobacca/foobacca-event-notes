===============
Lightning Talks
===============

Raspberry Jam demo
==================

Flying saucers in minecraft

Kivy
====

https://github.com/Ian-Foote/Kivy-Talk

You are a brain
===============

recommend http://www.amazon.co.uk/Thinking-Fast-Slow-Daniel-Kahneman/dp/0141033576/ref=sr_1_1?ie=UTF8

NHS Hackdays
============

http://nhshackday.com

built ins to avoid itertools
============================

You can use map, reduce, list comprehensions and lambdas for most uses of itertools

though python 3, ``reduce()`` has moved to ``functools.reduce()``

Teacher
=======

* Vikki Dodd @vikkiville

Computing GCSEs abandoned a few years ago, but now brought back. From Sept 2014 computing is compulsory from age of 4 to 16.  Includes design and create basic programs from the age of 4

Speaker from "Computing in School" organisation

Python - could be taught from 10.  Kids have to learn textual language.

Problem - many teachers have no computing education.  Need support from professionals in schools.

- join Computing in Schools
- STEM ambassador

EuroSciPy 2014
==============

http://www.euroscipy.org/ - in Cambridge, prob August 2014

- cartopy (GIS)
- openGL
- bigger data systems
- machine learning
- NLP

Encode/Decode
=============

Mark Shannon

Data representation 

- binary 1001010010111010
- big endian, little endian, ascii, latin-1, utf-8

If you have data you need to know what it means. *All* data needs an encoding or it is just a stream of bytes with no meaning

python - a string has meaning, bytes don't

::

    bytes + encoding
    /\ encode/decode \/
    semantic data

Ubiquitous Larch
================

Geoffery 

- notebook like ipython notebook - looks nice
- demo live editing and interaction through web browser
- and live audio capture, playback, fft ...

http://ubiquitouslarch.pythonanywhere.com/

Antiques Codeshow
=================

Gail Ollis

PhD work - hidden impact of programmers' psychological differences on software development

"Programming is the art of telling another human being what one wants the computer to do" Donald Knuth

wave 8" floppy disk around - 500 kb

story of test harness for naval radar built in 1978 - used 8" floppy - still used in updated systems in 1988, 1995

Moral: software can hang around for a hell of a long time

Future of PyRun
===============

eGenix

- python runtime env in single file
- small footprint - 10MB, 3-4 MB compressed
- cross platform (except windows)

.. code-block:: sh

    wget https://downloads.egenix.com/python/install-pyrun
    chmod +x install-pyrun
    ./install-pyrun
    ./bin/pyrun

Solr - opening the black box
============================

Alex Moon @barthes_simpson

https://github.com/alex-moon/solr-play

- Indexing engine, full text search
- schema.xml
- solrconfig.xml
- dump data into it using HTTP (update URL) and json - pretty easy
- don't have to use haystack - then Solr is a black box
- slow to index, fast to search

Education via writing games
===========================

- coursera - intro to python for writing games
- code sculptor - python in browser, save, give URL, email to people
- peer assessment
- week 1 rock, paper, scissors, lizard, spock
- week 4 pong
- week 5 black jack , and here's OOP
- week 8 asteroid clone
- content of quizzes was overly mathematical, but core course is great

Relationships
=============

Daniele Procide

- you are not with the perfect person
- commit to the person and make it good
- same goes for software

Orionrobots - Inspired by PyCon
===============================

Danny Watkins

Inspired by PyCon UK 2012. Always been a robot nut. Now make a cheap robot and have a robot shop, sold 20 of them.

orion explorer1 robot avoiding walls http://www.youtube.com/watch?v=ElXsXAcqrUE

http://shop.orionrobots.co.uk - bare kit £55, complete £70

Adventures in Open Computer Vision
==================================

Jon Cage

OpenCV, C++ with Python bindings

- Project - auto gas + elec meter reading - python, OpenCV
- tried smart meters - couldn't get data out
- have server in cupboard with meters, add webcam, read visual meter output
- transform image to normalised reading
- opencv - python bindings incomplete, docs worse - please help

http://stackoverflow.com/questions/17259232/how-do-i-programmatically-find-the-pixel-locations-of-specific-features-in-an-im

Enumerated data types in Python
===============================

Simon Sapin, @SimonSapin

types:

composition: tuple, namedtuple ...

enumerated data type

- C: tagged union
- Rust: enum
- python:
    - pep435 - like C
    - dynamic typing
    - oop, class heirarchy
    - tuples ``('circle', x, y, r)`` ...

Is there a better way?

Live Wires
==========

Christian technology camp, every August

Help Me!
========

Sarah Mount - will shortly be teaching bioinformatics with python - Sarah would like to know more about bioinformatics

new features in twisted
=======================

- hostname endpoints ("happy eyeballs") - handle ipv4 and ipv6 in parallel - try both
- deferred cancellation
- stream parsing - https://github.com/twisted/parsley-protocols
- twisted mail updates
- Tubes - create a composable flow-control and back-pressure friendly way to arrange parsing, processing and emitting data
- secure by default
- structured logging
- EDNS and DNSSEC
- twisted.positioning (GPS)
- and lots more

Twisted for the Win website - good examples of twisted usage - http://twistedftw.org/

slides at http://pyconuk.net/Twisted

Teachers need
=============

exactly one screenful of python that does something interesting

- crack a password
- pygame
- ...

needs readme, put it on github

Dryparse
========

Larry Hastings

Problem with argparse - too verbose, too much boilerplate

didn't like alternatives, created dryparse (python 3 only)

.. code-block:: sh

    hg clone [-U] source [target]

.. code-block:: python

    def clone(source, target, U):
        ....

https://bitbucket.org/larry/dryparse
