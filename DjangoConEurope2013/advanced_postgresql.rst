Advanced PostgreSQL
-------------------

database agnosticim is expensive

enjoy your database

custom types

* many built in types
* eg case insensitive text -> citext
* attributes you want to add occasionally (sparse) -> hstore (dict-like) - do queries etc 
* json type - validated going in, more features coming in 9.3 
* UUID - good for index if merging in data from other sources 
* ipv4 and ipv6 addresses - cidr comparisons 
* interval - store time intervals directly in db 
* define your own types! and then have custom indexes! 
* easy to integrate into Django - psycopg2, Field class, formfield and widget

custom indexes

* partial index - index subset of rows - eg most rows archived, only index active rows -> smaller faster index 
* multicolumn index
* expression index - eg index on just year of date field

custom SQL

* -lso add python version check
* bootstrap\_requirements.py
* custom use .sql inclusion mechanism -> requires each statement be on one line
* use south

custom constraints

* foreign key constraints implemented in ORM 
* push constraints into DB where possible 
* blocks bad data ...
* add constraints with south
* exclusion constraints - eg non-intersecting time ranges and same room

raw SQL 

* joining more than three tables -> use raw SQL 
* don't fall back into multiple query sets and iteration 
* django can still return model objects 
* full text search, geometric searches 
* complex joins that return a subset of lots of objects for view purposes 
* put SQL in the manager or the model 
* stored procedures (added by south)
