=========
Byte Code
=========

* Larry

Why?
====

some bad reasons

* what's really going on (but where did you stop)
* hand tuned byte code !@#! (can be broken from one python version to the next)

Example

.. code-block:: python

    def gunk(a=1, *args, b=3):
        print(args)
        c = None
        return (a + b, c)

disassemble with the dis library

.. code-block:: python

    >>> dis.dis(gunk)

shows the byte code

* opcodes
* big picture
* asdfsa
