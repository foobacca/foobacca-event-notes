Conformity and you - a question of style
========================================

Greg Chapple

https://github.com/gchp
@gregchapple
http://gregchapple.com

- not generally the most exciting topic
- starting a project - think about language, framework, libraries, test coverage - style not so much
- every line of code follows some sort of style convention - intentional or not - similar to your accent
- naming, single vs double quotes, strict line length ...
- we pick up the style/accent from who we learnt from

patterns vs style

- inconsistent styles

  - mixed quotes
  - spacing

- consistent patterns

  - list comprehensions rather than multiple for loops

- switching cost from project to project
- lack of consistency inside and between projects
- need a documented style guide for contributors

- pep8
- flake8
- jshint
- gofmt

- naming conventions
- use of lambdas
- globals, exceptions, indentation, semicolons, whitespace, comments ...

people take criticism of coding style much more readily from a program than from a person

from PEP8

- code is read more often than it is written - see also PEP20
- consistency is important - most important within a module

examples from open source projects:

- docstrings with single/triple quotes
- method argument arrangement
- when new lines are put in, with what indentation

Use your judgement - readability is the aim, not slavish rule-following

"Write your code as if the person who will maintain it is a psychopath who knows where you live"

- gofmt has some early python equivalents - yapf, pyfmt, autopep8
