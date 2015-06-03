Demystifying mixins with Django
===============================

Ana Balica
@anabalica
slides - http://www.slideshare.net/AnaBalica/djangocon2015-demystifying-mixins-with-django

- mixins controlled way to add to your classes
- NOT a special python construct - just ordinary python class
- inherit from object

- single responsibility
- not meant to be extended to another Mixin
- not meant to be instantiated
- implemented using multiple inheritance
  - order matters (method resolution order)

Say copy/paste a feature between classes that are otherwise different

.. code-block:: python

    class MyMixin(object):
        def mymethod(self):
            pass

    class Foo(BaseFoo, MyMixin):
        # read as MyMixin is the base class, extended by BaseFoo, extended by Foo
        # so this is bad
        pass

    class Foo(MyMixin, BaseFoo):
        # better
        pass

extensions goes from right to left

Class Based Views example

.. code-block:: python

    class LoginRequiredMixin(object):
        def dispatch(self, request, *args, **kwargs):
            if not request.user.is_authenticated():
                raise PermissionDenied
            return super(LoginRequiredMixin, self).dispatch(request, *args, **kwargs)

    class AboutView(LoginRequiredMixin, TemplateView):
        template_name = "about.html"

- alternative - TemplateView <- LoginRequiredTemplateView <- AboutView
- but then DetailView needs LoginRequiredDetailView, UpdateView ... - duplicated code
- so Mixin approach reduces duplication

Useful methods in class based views

- dispatch() - check permissions
- get_context_data() - add more data to the context
- get_template_names() - more flexible selection of template

How to learn

- Just read the source code
- https://docs.djangoproject.com/en/1.8/topics/class-based-views/mixins/
- http://ccbv.co.uk/

- django-braces is a package with lots of useful mixins
- don't do too much chaining of mixins - hard to understand execution flow

Summary

- single responsibility
- plug-in functionality
- isn't creating a subtyping relation (so not SOLID, breaks Liskov)
