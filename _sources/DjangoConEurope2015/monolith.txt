Avoiding Monoliths
==================

- Single big monlith is bad
- Having many very small apps all being very inter-related is also not great
- 2nd iteration was fewer larger apps, less dependencies to follow between apps
- many models in few apps
- easier to understand
- rather than putting lots of business logic in models, added a service layer
- ideas from https://stackoverflow.com/questions/12578908/separation-of-business-logic-and-data-access-in-django
- the business logic is not only about the data
- models used for reading, but update/insert always done through service layer
