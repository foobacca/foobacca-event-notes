The net is dark and full of terrors
===================================

James Bennett

History of Django and Security
------------------------------

- August 2006 - first published vuln in Django CVE-2007-0404
- found by member of team, published reported
- arbitrary command execution is bad - played down in announcement
- fix - download new copy of file and overwrite old one - not great

- 20 May 2015 - latest vuln - CVE-2015-3982
- now we do a full release to fix
- don't downplay seriousness
- credit to reporter
- Action: "upgrade immediately"

full list https://docs.djangoproject.com/en/dev/releases/security/

- pre-2007 - informal security process
- 2008 - 1.0 - template auto-escaping
  - controversial at time
  - philosophy - this is too important to leave off by default and just document
- 2010 - 1.2 - modern CSRF protection
  - old version - two middleware, in contrib, mentioned in docs
  - one middleware, in core, on by default
  - again, better to be safe by default
- 2012 - 1.4 - big deal, still supported
  - first release that took security seriously
  - hashing, crypto, signed cookies, clickjacking
  - sensitive errors - suppresses some things in error messages (debug, emails)
    such as passwords, etc
  - formal security process - https://www.djangoproject.com/security/
- 2013 - 1.5/1.6
  - Host header hardening
  - Increased hash iterations - PDKF2
  - Hash truncation
- 2014 - 1.7
  - system check framework
- 2015 - 1.8
  - security middleware
    - in browser XSS filter
  - deployment check

security process
- email security@djangoproject.com
- try to replicate
- private bug tracker, fix
- review, and if necessary backport to supported versions
- CVE identifier
- one week prior to release send to security notification list (mostly linux distros)
  - can be done more quickly if vuln is public
- do release, blog post, tell all the social media
- GOAL - ensure responsible reporting and disclosure of security issues

How Django tries to protect you
-------------------------------

- OWASP top ten vulnerabilities
  - injection attacks
  - auth and session management
  - cross site scripting XSS
  - direct object references - see database ID in URL and change number - Django encourages human readable URLs
  - misconfiguration - system check framework etc
  - sensitive data exposure - can't force you to use HTTPS, but provide support for it
  - function level access control - decorators, permission checks
  - CSRF
  - components with known vulnerabilities - require recent versions of databases, drivers, and notify common libs (eg xml libs)
  - unvalidated redirects and forward

- above and beyond
  - clickjacking
  - in-browser XSS
  - crypto signing APIs
  - constant time password hash check
  - every release has GPG signed hash file, and GPG signed tag in github

Django tries to be secure by default and offer the tools needed to help our users.

How we've screwed up over the years
-----------------------------------

- Why do we fail?

Input Validation

- people have "good ideas" -> vulnerability
  - accept language header - was caching in memory - but DoS via looong headers
- password reset using base36 - again loong tokens
  - now we reject anything longer than 13 chars (64 bits)
- formsets grow without bound - users can increase number to cause DoS
- no cap on password length - DoS due to very long passwords - now limit 4096 bytes

- Python is great - no buffer overflows, but can DoS yourself
- We learned this the hard way repeatedly
- Comes down to input validation before doing work
- Configure your webserver to cap the length of HTTP request headers and bodies

Algorithmic complexity

- URLField - verify_exists - check by fetching URL, can make that take a long time
- regex performance - can make them take VERY long time
- compressed image files - some routines decompress images - use huge amount of memory - DoS
- DoS via large image files, looking for headers
- Big O notation - algorithmic complexity
- what's the worst that could happen?
- figure out how much work your code does, how much work you could make it do, then how to make sure it does less
- learn about compressed formats, pathological regex
- so we don't accept everything in emails

Trust

- trust unsafe cookie value
- info leakage in admin
- CSRF via forged HTTP headers
- info leakage via admin history log
- XSS via admin trusting URLField values

- we can trust the HTTP Host header now
  - this caused 5 vulnerabilities
  - sometimes Django needs to generate full URL - but you should NEVER trust the host header
  - now Django requires an explicit whitelist of values in the host header

- don't trust your users
- don't trust your web server
- don't trust your database
- ALWAYS verify

article - default allow is the dumbest idea in history

There is no such thing as secure

Learn to pick yourselves up when you fall
