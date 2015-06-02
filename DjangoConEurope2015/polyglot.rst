Django's role in a polyglot world
=================================

David Gouldin
@dgouldin
slides - https://django-ployglot.herokuapp.com

- Django is 10 years old
- it is not a CMS (but was built to make one)
- used to be LAMP - one (relational) datastore, all on one server
- now much more service orientated - can even treat the web browser as a service that runs stuff
- expectations for responsiveness, "app-like"

Django strengths
- python
- "perfectionists with deadlines"
- orm & migrations (though doesn't cover entire SQL standard)
- the admin
- django rest framework (for REST API)
- celery (async work queue)

Django weaknesses
- c10k - 10000 concurrent connections to web service - alternatives async.io, twisted, but lose library support

JS client integration
- community then expect JS on the server

Push to web clients
- no good solution in Django - long connections - but kills server
- polyglot can use socket.io, websocketd, golang

async task results
- add task ids to initial response
- then have client poll other endpoint to get status of task id
- OR can use pubsub/async to subscribe to task, and then result gets pushed to client

- react.js - but then need js running on the server
- run node on server - React.renderToString(BaseElement)
- can have node on separate subdomain - have node to initial web page, then have Django as a service provider

Shared auth across services
- django.contrib.auth
- have node proxy auth to django
- access token, check with django
- have separate auth service that django and others use - but more heavyweight

Take away points
----------------

- Say no to full stack python - not feasible for the web
- HTTP is your friend (and pubsub is the back up)
- Think about web browsers as service consumers

Questions
---------

- when is it worth the effort?  When it seems like a webapp - plain webpage (eg blog) doesn't need it
- testing? service contracts are really important - can test each service in isolation, and then just do a few integration tests
