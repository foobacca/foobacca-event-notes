Processing Payments
-------------------

Threats:

* XSS 
* Phishing 
* SQL injection 
* remote execution 
* ourselves

OWASP - detection points - good checklist of things to think about

* XSS - Content Security Policy - whitelist where js will be executed - Moz DN docs
* navigator.mozPay -> web standards
* database, problem of anonymising data -> second database
* encrypt some fields - django-aesfield

proxy manages credentials, solitude manages database, provides API to
Marketplace which manages transaction data 

proxy is SOAP proxy that uses lxml to parse xml and insert credentials

don't use http request directly and then have to deal with HTTP in business logic
curling - wrapper around slumber

django-paranoia - allow everything to go through, but tell "security"

* ParanoidForm
    * check if extra form fields -> log
    * check if fewer form fields -> log
    * check if form contains ascii character less than 32 (except ``\t \r \n``)
* changes during session 
    * user agent
    * ip address (can be legit, eg mobile -> reverse geo ip look up)
