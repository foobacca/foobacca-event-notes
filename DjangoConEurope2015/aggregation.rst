Django aggregations demystified
===============================

Theofanis Despoudis

Aggregations
------------

- database functions
- produce summaries over collections
- similar to reduce function
- return single value
- avg, max, min, sum, count, StdDev, variance

- setup

  - Gamer model
  - GameServer - m2m w Gamer
  - GameSession - inc multiple Gamer, one GamerServer
  - GameSessionResult - FK to session, user

.. code-block:: python

   Gamer.objects.all().aggregate(unique=Count('id'))
   Gamer.objects.all().exclude(won=False).aggregate(num_wins=Count('won'))
   # avg points per gave
   GameSessionResult.objects.all().aggregate(Avg('score'),StdDev('score'),Variance('score'))

Annotations
-----------

summary per row/object

.. code-block:: python

   scores = GameSessionResult.objects.all().annotate(Sum('gamersessionresult__score'))
   scores[0].gamesessionresult__score__sum
   scores = GameSessionResult.objects.all().annotate(
       sum_scores=Sum('gamesessionresult__score')),
       ...)

   Gamer.objects.all().annotate(sum_points=Sum('gamesessionresult__score'))\
       .filter(not null).order_by('sum_points')[:5]

   # group by
   GameServer.objects.values('region').annotate(num_users=Count('gamers'))

Practical Bits
--------------

- when in doubt - check the generated query 

  - django debug toolbar, debugsqlshell
  - ``print(queryset.query)``

- if you can do it in SQL, don't do it in python
- collect queries in a manager - but put in proxy object, so can apply diff orders
- KISS
