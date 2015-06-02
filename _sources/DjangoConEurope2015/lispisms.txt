Lispisms
========

Shai Berger
https://bitbucket.org/shaib/lispism/

what is special about lisp

- invented - recursion, dynamic typing, garbage collection
- are there more gems to uncover?
- almost macros were considered and rejected in python
- MacroPy does some of it

dynamically scoped variables (DSV)

- for years, people ask for request object to be available globally
- answer: Globals are evil! toe code to system, value change unpredictably
- so use thread locals
- but there's more to Evil than being harmful
- globals are ***ing convenient
- we prefer not to pass connections into every QuerySet
- settings can be accessed everywhere

What if we could have globals that do behave

- every change is temporary, applied only down the call chain - think with statement
- then each piece of code can be reasoned about

Local change is the norm in Lisp
- example, and equivalent in python
- but python likes mutables and objects - managing bindings is not enough
- obvious problem is that code inside can still change object state
- solution: make objects immutable
- what if we need to change just part of the object
- solution: special syntax for attribute change

lispism library
- special object called ``D``

::
   D.let(a=1, b=2):
       print D.a
       D.let(a=3, b=4):
           ...

Builtin containers are replaced by immutables - eg list -> tuple

Freezing

Limitations
- freezing can be worked around, but will avoid mistaken changes
- can't control C extensions
- generators - yield inside let breaks the contract
- ``__dict__`` access is a problem (plan to fix it)

Future

- threading
- use MacroPy macros for better sub-object control
- implement lisp restarts
  - separate What from How in error handling
  - code detects error handles it, but can't make decision
  - higher code sets map of extension -> action label
  - low level code lists action labels, and actions for each case
  - intermediate code knows nothing
