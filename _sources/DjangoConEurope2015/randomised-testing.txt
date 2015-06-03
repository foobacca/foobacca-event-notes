Hypothesis, randomised testing for Django
=========================================

Rae Knowler
@raeknowler
CKAN, Symfony, Django
slides - 

@drmaciver - hypothesis author
@sinister_katze - fuzzy, loves catching bugs

- slides - 
- http://hypothesis.readthedocs.org
- https://github.com/bellisk/hypothesis-django-example
- Property based testing library
- inspired by Haskell's Quickcheck

Why is it so great?

- **lots** of randomised data

  - say name is string, email, number
  - come up with 2000 customers!
  - if fail, work down to simplest string with bug (eg ! mark)

- can deal with complex data types - eg Django Models
- works with pytest, unittest - just a library

hypothesis-django

- tests look similar to Django tests
- custom field types
- generate child models
- can generate fixtures for Django (new!)

pip install hypothesis hypothesis-django

Example

- StockSubscription model

  - fields: symbol, last notified, NotificationsPerDay
  - methods - ``__str__``, next_notification_time

- tests - use hypothesis version of models, TestCase, and ``given``
- given decorator - tells hypothesis type of fields, in combination with hypothesis.strategies.integers
- hypothesis finds a falsifying example (0 values -> divide by 0)

Example 2

- Portfolio model
- want to find median value
- test generates list of StockSubscription, max len 100
- test asserts median value is from 0 to 100
- finds bug - if 2 in list, this causes error in median function

Hypothesis is awesome

- it makes your tests way simpler - hypothesis will find the edge cases
- it finds subtle bugs
- simple tests that are insanely effective
