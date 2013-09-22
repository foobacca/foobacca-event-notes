Advanced Python - metaclasses
-----------------------------

https://github.com/ingleby/prescons

metaclass

Examples:
- add ``base_fields`` attribute to Django models
- ``class Meta: abstract = True`` -> meta class throws error
- ForeignKey -> add xyz_set manager object

classes recap:
- isinstance, type
- create classes dynamically

.. code-block:: python

    name = 'ExampleClass'
    bases = (object,)
    attrs = {
        '__init__': lambda self: print('hello from __init__')
    }
    ExampleClass = type(name, bases, attrs)

    def create_class(name, bases, attrs):
        # ...
        return type(name, bases, attrs)

can add to attrs, bases etc

- Q: what is type?
- type is a class
- classes are factories for creating objects

we can subclass type

.. code-block:: python

    class FormType(type):
        def __new__(cls, name, bases, attrs):
        fields = {k: v for k, v in attrs.items() if isinstance(v, forms.Field)}
        attrs['base_fields'] = fields
        return type.__new__(cls, name, bases, attrs)

    PonyForm = FormType(name, bases, attrs)

in Django - search for **metaclass** - see ModelBase in
django/db/models.py for lots of big/hairy metaclass stuff

Python 3

.. code-block:: python

    class Form(metaclass=FormType):
        ...

For supporting both 2.x and 3.x, see library called six.

key points:

-  classes are factories for creating objects
-  metaclasses are factories for creating classes
-  (missed the last one)
