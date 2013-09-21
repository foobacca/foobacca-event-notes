=============
Oh Py, Behave
=============

* Colin Moore-Hill

Silly intro referencing LotR, monty python and holy grail ...

BDD
===

Behaviour Driven Development

* Business people - see opportunites
* Technical people - see details, 1s and 0s

Test Automation - Holy Grail? Or Very Naughty Boy?

Cohn's Triangle - UI at top, Service, Unit at bottom

behave
======

* python implementation of BDD framework
* uses Gherkin like syntax

Initial state
steps that represent actions
new state

Feature:
As an IT professional
I want to explain how BDD works
So That others can ...

Scenario:

Code sample

Features:

``@Tags`` ...

environment.py - `before_step()`, `after_step()`, scenario, ...

Lessons
=======

* don't rush into automation
* don't spend hours arguing about correct language
* have the conversations and write scenarios with team
* add test to CI as early as possible
* use your scenarios
* Include the subject matter experts (SME), domain experts and customers
* keep scenarios precise and use examples to reinforce the scenario
* every scenario is negotiable and subject to change at any time
* your scenarios are your living documentation
* don't add implementation details in scenarios

References
==========

* http://pythonhosted.org/behave/index.html
* ...
