continuous integration
----------------------

lion taming / code taming

old way 

- deploy by hand
- hack till it works
- confusion - *special* decisions

lion taming - understand, conditioning, behaviour -> response trust

- understand -> deploy hard
- conditioning -> CI
- push -> test-> green
- happy
- trust - it works in live

team

- committed to quality
- everyone deploys
- identical environments
- everyone is responsible

working code

- tests 
    - unit, acceptance (user's viewpoint)
    - quick, reliable
    - slow tests -> fail
- no pylint fail
- commit often, rollback
- both dev + qa responsible
- don't let tests rot
- break tests - triage: right now vs asap

repeatable build

- automated
- no manual changes

deploy

- script <env> <version>
- not just code - config infrastructure
- always follow the pipeline - even in emergencies

rollback

- you will break stuff!
- blue is the new green (blue is working on live)
- canary servers
- databasea - keep backwards compatible

release

- last step - automatic
- small changes, frequent, get experience, less risk - maybe, maybe just to staging server

tips

- split in components
- rehearse releases - get very good at them
- manage and test infrastructure - eg test email sending
- all environments equal (vagrant)
- automate everything, if really not possible then document, but will drift
