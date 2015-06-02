Give your pony wings
====================

Benjamin Wohlwend
@piquadrat_ch

- I like my code to be lazy
- Making your code not do too much work makes your code faster
- make a stackoverflow clone - for pony owners
- use Django - models for Question, Answer, Tag, User ...
- views for QuestionList, QuestionView
- templates ...
- go live - happy until ...
- someone linked from ponynews and
- we have a performance problem (or maybe several problems)
- so how do you find the issues
- django-debug-toolbar, django-dev-server, ...
- django-debug-toolbar is great - lots of features - SQL queries shown - hundreds of queries for one page
- django-devserver - shows number of sql queries, number of duplicates, time for request

The big three
- reduce database queries
- do less work
- if all else fails - cache

Less SQL queries
- select_related()
  - use to preload objects referenced by ForeignKey
  - eg looking up user in template
- prefetch_related()
  - similar for reverse ForeignKey and ManyToMany
  - so get all tags for all questions in one query

Overall, go from 121 queries to 3 queries!

Do less work
- move work out of request/response cycle (eg celery)
- only fetch data that we need - QuerySet.defer() can skip unneeded large columns (or only())
- let others do the work (eg do calculations in the database with annotate/aggregate)

Caching
- doing properly gives you great scaling
- but cache invalidation is really hard
- can also make code hard to test and understand
- so recommend only use it when necessary
- cache_page decorator - put it on view - timeout
- template caching with {% cache %}
- ORM caching with jonny-cache or django-cache-machine
- caching http proxy like Varnish

Much more in book - High Performance Django
