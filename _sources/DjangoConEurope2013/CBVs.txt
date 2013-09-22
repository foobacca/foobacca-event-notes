Class Based Views - untangling the mess
---------------------------------------

history

- lots of common patterns in view
- generic views - template, single object, list of objects, forms ...
- but generic views don't allow logic insertion, limited config options ...
- so let's go class based (released in Django 1.3, talked about since 1.0)

why bad reaction?

- confusion over purpose
- confusion over implementation choices - complexity necessary, but not obvious why
- ravioli code - nicely packaged, but internals opaque, steep learning curve
- bad docs

Purpose - 2 distinct but connected bodies of work

- class based views
    - class based analog of view
    - http verb based methods
    - get automatic code for free - OPTIONS, HEAD, HTTP 405 ...
- class based generic views
    - built on top of class based views
    - analogs of the old generic views
    - address limits of functional approach
    - requires learning to know how and where to extend

Implementation Choices

- django wiki page on Class Based Views - lots of discussion archived here
- what does class view mean?
    - (btw, admin is a class based view)
    - factory classmethod, returns function that invokes dispatch()
    - (could have done, urls.py could be either callable or class - but wanted to keep urls.py contract clear, as other things use that. trade off)

Ravioli

- goal: replace function-based generics with class-based generic
- end point - series of mixins
    - basic update view has 9 classes! wtf
    - but then create view reuses almost all of that
    - another single class change creates a JSON response instead of a template response
- allows for maximum reuse
- very flexible
- easy to add mixins
- BUT you need to grok it
- bad docs originally, but much better now, and need to decide about best practice

Next

- better docs
- decide on standard way of eg login required
- extend
- experiment with API - django's admin?

Have we solved the wrong problem?

- multiple forms and formsets (see bug #18830 about FormCollection )
- conditional forms
- continuous scrolling, not pagination
- ajax support (eg in place editing)
- pjax
- multiple "actions" per page
