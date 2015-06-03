Lightning Talks Day 3
=====================

Me + Web Apps
-------------

Ben

- medical student
- prototype ideas for medical web apps
- want fast dev, more magic, less code
- found django tutorial hard
- discovered Web2Py and PythonAnywhere
- almost no config
- web based IDE
- great docs
- MVC really is MVC
- built online notice board
- nothing I couldn't do with Web2Py - what am I missing?

Speech to text transcription
----------------------------

Sheryll

- supporting deaf people
- special keyboard - vowels in the middle
- learn the keyboard, play it like a piano
- single keys become short words, press keys together to get single letter
- most vowels are single keys
- for the word "judge" - press 9 keys at the same time!
- can get words wrong - heard "whisky", actually "wsgi" - can reconfigure keyboard for jargon in particular conference
- ask for info, jargon, terms in advance to get the names into the dictionary
- electronic shorthand - only about 100 wpm, these keyboards get to 250 wpm - can keep up with most people (but Russell ...!)

DjangoBeer
----------

Iacopo

- there used to be a circus
- DjangoBeer happened in Florence in 2014, during EuroPython
- rebooted as monthly meeting, all things web
- code and beer thrive together - socialising people, community
- see you in Florence - last Tuesday of each month

Systers
-------

Ana B

- orgs to help coders
- djangogirls, pyladies, rails girls, black girls code, she++ ...
- systers is part of the Anita Borg Institute
- community for women in STEM
- over 5500 members, in 60 countries
- founded in 1987, by Anita Borg, started as email list with 12 members
- http://systers.org - subscribe to email list
- aim to increase women in computer science and help make envionment more conducive

I wrote my first line of code 1 year ago
----------------------------------------

Geraint Palmer

- phd student
- feb 2014 - first line of VBA - for and if
- oct 2014 - grew up, discovered python
- taught python almost immediately - I learned it much better that way
- googled things
- found nice text editor (atom/sublime) and learned command line
- installed first library
- discovered pip
- pair programmed
- git, testing, docs
- python namibia
- django con europe!

Do I need to update my Django project
-------------------------------------

Mounir Messelmeni

- deadlines
- some versions not getting security updates
- Django now only support python 2.7+ - 2.6 has been dropped
- preparation - read release notes, new virtualenv, eg 1.8 dropped contrib.comment
- data backup!
- migration - south -> django migrations
- deprecated functions, any unavailable packages
- TESTS
- staging deploy ...
- python 3

.. code-block:: bash

    pip install caniusepython3
    caniusepython3 -r requirements.txt

The Missing Method Murder Mystery
---------------------------------

Baptiste

- true story
- class with two methods

.. code-block:: python

    class Foo(object):
        def foo(self):
            return "foo"

        def bar(self):
            return "bar"

    >>> f = Foo()
    >>> f.foo()
    'foo'
    >>> f.bar()
    method not found

bar was indented with tabs - python sees tab as 8 spaces, so bar is function inside foo!

- highlight the tabs
- start using python3 - will give error if tabs and spaces mixed

Sprinting
---------

Russell Kieth-McGee

What is a sprint?

- people get together after conference to hack on code
- next 2 days are sprint

What needs to be done

- bug triage, replicate problems
- patches - write them
- patches - test it, code quality
- patches - add tests to patches
- tests!
- docs also required for new features
- docs - can also be improved
- docs - first draft is really helpful, working examples

What to work on?

- django core
- django libraries
- django project website
- django community resources

- pick an area that interests you
- scratch your own itch

- Ask a core dev!
- Ask the person next to you
- IRC #django-sprint
- docs.djangoproject.com - contributor guide - link at bottom of page

DjangoGirls also sprinting
