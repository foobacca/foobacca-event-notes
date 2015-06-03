Lookups, Transforms and Expressions
===================================

- Anssi Kaariainen
- django core team, ORM, lookups and transforms

Lookups

.. code-block:: python

    Book.objects.filter(title__glob='Django*')
    Book.objects.filter(title__lower__glob='*DJanGo*')
    Book.objects.annotate(
      author_str=GroupConcat('authors__name')
    )

Why not ``extra()`` ?

- reuseability
- chainability
- multi-database support
- nicer looking code
- easier to support

Lookup Class

- a condition in the query's WHERE clause
- eg gt, lt ...

Create a custom lookup

- subclass models.Lookup
- set ``lookup_name``
- implement ``as_sql()``
- register to a Field

Demo - Glob Lookup

.. code-block:: python

    @models.CharField.register_lookup
    class GlobLookup(models.Lookup):
        lookup_name = 'glob'

        def as_sql(self, compiler, connection):
            lhs_sql, lhs_params = self.process_lhs(compiler, connection)
            rhs_sql, rhs_params = self.process_rhs(compiler, connection)
            return "%s glob %s" % (lhs_sql, rhs_sql), lhs_params + rhs_params

        Book.objects.filter(title__glob="*Django*")

Transform - case insensitive

Transform takes in a value, outputs a transformed value

- subclass models.Transform
- set ``lookup_name``
- implement ``as_sql()``
- register to a Field

.. code-block:: python

    # note it *is* register_lookup
    @models.CharField.register_lookup
    class LowerTransform(models.Transform):
        lookup_name = 'lower'

        def as_sql(self, compiler, connection):
            lhs_sql, lhs_params = compiler.compile(self.lhs)
            return 'lower(%s)' % lhs_sql, lhs_params

        Book.objects.filter(title__lower__glob="*django*")

- Can apply transform multiple times eg ``title__lower__lower__glob``
- Can apply to both sides with ``bilateral = True`` in class

Expressions

- An element in SELECT clause
- eg ``Avg('authors__age')``

Create expression in 1.8

- subclass models.Func or models.Aggregate
- set ``lookup_name``

.. code-block:: python

    # note it *is* register_lookup
    class GroupConcat(models.Aggregate):
        function = 'group_concat'

        Book.objects.all().annotate(
            authors_str=GroupConcat('author__name')
        )

        # combine various things - produces complex SQL query
        Book.objects.all().annotate(
            authors_str=GroupConcat('author__name')
        ).filter(
            authors_str__lower__glob="*a,m*"
        )

New in Django 1.8

- all expressions support arithmetic operations
- all aggregates are expressions

    annotate price_pre_page = Sum 'books__price' / Sum 'books__pages'

output_field

- When the type of the value changes - eg len charfield -> integerfield
- set ``output_field = models.IntegerField`` on class

.. code-block:: python

    annotate(
        name_len=Length('name')
    ).filter(name_len__gte(10))

Multiple SQL dialects

- django looks for (eg) ``as_postgres()`` method before ``as_sql()`` method
- so can use DB functions directly

Hstore and ArrayField

- in django.contrib.postgres
- HStoreField - key values

.. code-block:: python

    Dog.objects.create(
        name='Ruth',
        data={'breed': 'labrador', ...}
    )
    Dog.objects.filter(data__breed='labrador')
    Dog.objects.filter(data__breed__icontains='l')

ArrayField

.. code-block:: python

    Post.objects.create(
        name='first post',
        tags=['thoughts', 'django']
    )
    filter(tags__contains=['thoughts', 'django'])
    filter(tags__overlap=['thoughts', 'django'])
    filter(tags__1__lower__glob='*o*')

Next

- implement common expressions in Django core/contrib
- use in more places - eg order_by
- unify expression and transform implementation
- idea - ``.filter(F('name').substr(0, 25).icontains('anssi'))``

Much more in Django docs

https://www.djangoproject.com/fundraising/
