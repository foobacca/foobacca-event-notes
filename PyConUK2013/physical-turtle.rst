=============================
Physical Turtle for Education
=============================

* Mike Sandford
* http://www.mikedeplume.com
* http://www.mikedeplume.com/2013/02/20/a-physical-turtle/
* https://pypi.python.org/pypi/PhysicalTurtle
* https://bitbucket.org/mikedeplume/physical-turtle

.. code-block:: sh

    pip install physical-turtle

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
