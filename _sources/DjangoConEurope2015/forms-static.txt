Forms are static - no they aren't
=================================

Markus Holtermann
@m_holtermann
slides - https://speakerdeck.com/markush/forms-are-static-no-they-arent

django-dynamic-forms

- talking about django.forms
- most important thing - user data validation
- can also be used for data from API or similar
- static?  the form in the page doesn't change while you interact with it

what about request dependent forms

- eg captcha only shown for anonymous users
- still static - need to modify code to make changes, do testing etc

What are non-static forms

- forms that can change layout - which fields present, order of fields
- doesn't require changes on code level

Why do you need them?

- had small client, organised events, each event had different details for form
- so wanted client to be able to change form themselves

How does that work?

- ModelForm does dynamic class construction, uses Meta class
- but ultimately still static - and models aren't modified during app runtime
- ``type(name, bases, attrs)`` rocks!
- form instance stored in database
- FormModel - Name, Actions, ..., URLs
- FormFieldModel - wrap Django form fields - name, label ... options
- will be able to use data from postgres json fields once Django 1.9
- in admin, form meta stuff, then inline for adding fields
