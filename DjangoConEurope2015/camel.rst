CAMEL, the Cardiff Maths e-learning project
===========================================

Dafydd Evans
slides - https://speakerdeck.com/dimbyd/the-cardiff-maths-e-learning-project

- 1 person project for now
- CArdiff Maths E Learning project -> CAMEL

- Cardiff Uni is mostly old school - print, mark with pen and paper
- on web, mostly latex -> PDF - very static
- typesetting - glyphs, fonts, Donald Knuth, TeX, LaTeX
- LaTeX documents are not "well formed" (closing tags etc)
- but LaTeX is excellent for equations
- until recently HTML wasn't great - but now MathJAX, which renders latex into nice equations in HTML
- MathJAX does fonts and characters, but doesn't do structure
- so can we take Latex and convert to mix of HTML and mathjax
- can then embed homework into pages
- wrote a cutom parser, using a subset of latex
- equations left inside <jax> tags, but structure converted into HTML
- use django-mptt for tree of chapters, pages etc (efficient retrieval and slow insertion, move etc)
- models subclass mptt.models.MPTTModel - trees auto-update ...
- provides nice templatetags and filters

- demo how to put lists in for homework -> HTML form
- free text box - make edit with latex format, update to show in page

All looks very nice.

Q - what happened to MathML
A - MathML is unreadable (too verbose - see e=mc2) while latex can be read, so mathjax is better
