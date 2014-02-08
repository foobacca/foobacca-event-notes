Cheating at Rock, Paper, Scissors
=================================

Meta-programming in Python

- Matt J Williams, Cardiff University
- @voxmjw
- http://mattjw.net mattjw@mattjw.net
- https://github.com/mattjw/rps_metaprogramming
- slides http://www.mattjw.net/2014/02/rps-metaprogramming

Prog competition for iterated rock-paper-scissors

- 1000 rounds
- players have history
- 3 for win, 0 for draw, 1 for loss

template_bot.py examples

'good old rock'

.. code-block:: python

    def name():
        return 'Bart'

    def move(my, opp):
        return 'R'

random

.. code-block:: python

    def name():
        return 'Bart'

    def move(my, opp):
        return rand.sequence('RPS')

psychic bot?  predict what opponent will do, change what opponent will do!!

- level 1 - find opponent's move function, make them play a test move, select winning move
- inspect the stack, get the frame record -> from object -> ``f_back`` (check stack), ``f_locals`` (see if opp bot is in scope)
- ``is_instance(f, ModuleType)``, ``hasattr(f, 'name')`` and ``hasattr(f, 'move')``
- next step, fiddle the *pseudo* random number generator
- but when it plays itself which causes infinite recursion "Yuri Gellers all the way down"
- fix by checking if we're in the stack already - if so return random

Abstract syntax trees
---------------------

- how about just make the opponent do what we want
- python tools - ast module, compile, exec function
- make the first instruction of ``move()`` be ``return 'R'``
