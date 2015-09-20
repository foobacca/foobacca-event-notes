Simplicity is a Feature
=======================

Cory Benfield
@Lukasaoz
https://speakerdeck.com/lukasa/simplicity-is-a-feature

The big take away:

Simplicity is about defaults
----------------------------

Build your software in library

Example: multipart http upload

3 levels
--------

* low level
* features
* simplicity

low level - eg httplib
~~~~~~~~~~~~~~~~~~~~~~

* don't try to "help" - give user complete control
* to the point of letting people do "invalid" stuff

feature level - eg urllib3
~~~~~~~~~~~~~~~~~~~~~~~~~~

* users no semantics of the problem, but don't need to understand every detail
* still have quite a bit of control
* only support valid cases

simplicity level - eg requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* this should be the default if someone searches how to do something
* does not have to support all valid use cases - 80% is fine, to keep it simple 
* lots of defaults, to make it easy for users
* "do the right thing"
* allow user to drop to level 2 - requests has an object giving access to urllib3
* can do multipart file load in one logical line!

80%
---

* understand the domain
* see what most users are doing
* solve the problems for most people
* you can't make everyone happy all of the time, but you can make some people ecstatic!

requests like libraries

* flask is the requests of web serving
