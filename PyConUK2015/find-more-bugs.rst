Find More Bugs
==============

David MacIver
@drmaciver

https://bit.ly/finding-more-bugs-pycon-uk

Your software has bugs
----------------------

NASA takes bugs very seriously - the cost of bugs is very high, so they invest a lot in testing
Also medical software and avionics

Most web stuff - bugs are embarrassing, but not critical

Your users should not be your QA team
-------------------------------------

Bug test cases - I did a thing, I expected this, this happened
But most users don't know how to communicate bugs
Or they use bugs to make money from you

So what do you do?
------------------

Make it cheaper to find bugs
Users as QA - there are many many users - testing is very parallelisable
Computers are faster than people, so use them

hypothesis
----------

inspired by QuickCheck (Haskell

.. code:: python

    from hypothesis import given
    import hypothesis.strategies as st

    def mean(xs):
        return sum(xs) / len(xs)

    @given(st.lists(st.floats()))
    def test_mean(xs):
        mean(xs)

This finds division by zero error and shows you the input that gives the error

.. code:: python

    @given(st.lists(st.floats()))
    def test_mean(xs):
        m = mean(xs)
        if xs:
            assert m <= max(xs) and m >= min(xs)

Can say the empty list is not valid

.. code:: python

    @given(st.lists(st.floats()) min_size=1)

Can say the list cannot contain ``nan`` or infinity

.. code:: python

    assume(not any(math.isnan(n) or math.isinf(n) for n in xs))

More issues - slightly odd floating point edge case issues
