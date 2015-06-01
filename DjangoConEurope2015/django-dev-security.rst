A sincere tale of Django, developers and security
=================================================

Erik Romijn
@erikpub

- used to think security was about knowing everything, and I didn't know everything
- now - more about the way you think about things

Things I don't know about

- computers work differently - they don't know what you meant - so ask:
- how does it know that?
- how might someone implement this in software?  How would you explain to a toddler?

Example - oege - shared linux server for students

- register.php - enter uni username and password - register and email your details
- cat register.php - permission denied
- but write php script to read it, and as php run by webserver - it works
- script - runs sudo /path/to/script.sh user pass
- write php script to call script, create other accounts, change root password, etc

Relentlessly question, take things apart and think creatively

Django
------

- "reassuringly secure" - password storage, auth, CSRF, DoS ...
- Django reduces the number of things you can screw up - eg auth system
- good docs - Security in Django
- Read "Two Scoops of Django" - good security section

Can introduce remote code execution

- SESSION_ENGINE - signed_cookies
- SERIALISER - PickleSerializer
- SECRET_KEY = 'not really secret'

But the above aren't default, and settings doc has warnings

Django forms are also good
- apple app id allowed dropbox credentials to be lost

https://www.ponycheckup.com/ - does automatic checks

If you think you've found something, email security@djangoproject.com

Common Issues
-------------

1 - absent or misconfigured https
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- https - essential for sensitive data - eg login details
- plain http - no integrity - could have stuff added, or replaced
- proper https
  - enable for entire site
  - redirect all users to https, enable HSTS
  - set the secure flag on cookies
  - all in settings SECURE_*
  - set the right cyphers, versions etc - https://ssllabs.com/ssltest/
  - Book - Bulletproof SSL and TLS - practical, crypto concepts, vulnerabilities

2 - Happy path only testing
~~~~~~~~~~~~~~~~~~~~~~~~~~~

- eg View with login_required
- abstract to mixin
- test, does login, then gets page
- forget mixin, the test still passes
- you need to test that anonymous users can't view, that users w/o permissions can't view ...

3 - Media Uploads
~~~~~~~~~~~~~~~~~

- see one file, then guess path of another file
- SECURE_SSL_REDIRECT - doesn't help
- properly
    - ideally different storage, different domain
    - at least do strict check on filetype, extension, mime type
    - access control - serve through Django (slow) OR use x-sendfile to tell webserver to serve file

4 - Outdated Software
~~~~~~~~~~~~~~~~~~~~~

- django 1.3 has 20 missing patches, 1.5 has 7, 1.6 has 1
- requires.io - extracts all dependencies, versions, tells you about security issues!

Human Factors
-------------

- ING Bank login "My ING"
- someone searches for "My" - hits first link, types in username and password without seeing what site is
- people will give password to someone claiming to be from IT
- password strength library - https://github.com/dropbox/zxcvbn
- two factor auth (2FA)

Risks
-----

- What about the NSA?
- Yes, the NSA can hack you
- but you can be secure enough about to stop hackers
- backup and recovery is also important
- how long can you reasonably be offline for?

Why it matters
--------------

- "it's been fine for the last year"
- sometimes companies phone up and ask for passwords - they haven't thought it through
- many people find security really annoying ... until something goes wrong
- quote "There is now way I can single handlely save the world ... ashamed to let one day go by without making an effort" Isaac Asimov
