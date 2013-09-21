=============================
Physical Turtle for Education
=============================

* Mike Sandford
* http://www.mikedeplume.com
* Presentation - https://bitbucket.org/mikedeplume/turtle_presentation (*and it's written with the turtle module!*)
* Blog article - http://www.mikedeplume.com/2013/02/20/a-physical-turtle/
* https://pypi.python.org/pypi/PhysicalTurtle
* Software https://bitbucket.org/mikedeplume/physical-turtle

.. code-block:: sh

    pip install physicalturtle

Draw an obstacle
================

draw polygons

.. code-block:: python

    forward(step)
    right(angle)

Terminate loop by counting steps, or angles

make it so the turtle can feel the obstacle
===========================================

.. code-block:: python

    tk.touch_right()   # are we touching something on the right

end up with gap as turtle stops before hitting the solid line

NB - if turtle starts on solid line, it can't move.

Simple outline following
========================

test if barrier still there, move forward a bit, test again ...

* go round entire object
* go round object until going back in original direction - though the simplistic version (``totalturn % 360 == 0``) can lead to loops
* learning - think about object, what's possible
* thinking about how to draw the maze can be more interesting than navigating the maze
* lots of things that teachers can talk about
