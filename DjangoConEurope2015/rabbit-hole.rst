Into the rabbit hole
====================

Ola Sendecka
@asendecka
Django Core team
Django Girls co-founder

- A story of Alice in Djangoland.
- Using model with BooleanField is_archived and manager with .filter(is_archived=False)
- But found a ModelForm didn't show the instance she wanted to look at
- Use function to do magic - preserve_existing_choices - insert current value in select
- Hit error page
- Changed to extend ModelChoiceIterator to insert the current value
- Form now displays properly, but form save gives error
- So extend ModelChoiceField and override to_python() method
- Then tried to change select widget to RadioSelect - but that didn't work.
- Looked at __init__() method - but it's big and hairy, so didn't want to mess with it
- So instead use normal ModelChoiceField, and inject her to_python() method
- It worked! But it was ugly, fragile - she felt ashamed
- She'd spent hours, unexpected stuff happened, not good

She'd been in a rabbit hole

- rabbit hole - you get so caught up in a detail, that you spend lots of time buried there, get sidetracked, change direction a lot and end up somewhere unexpected
- you can follow the steps, but lots of confusion and frustration
- some think rabbit holes are good - in flow mode
- but every time I end up in a rabbit hole, I feel frustrated, helpless, angry, stupid
- next time I would do things differently

- to understand the rabbit hole I wanted to read things - I have 2 bits of advice
- ziegarnik effect 
  - the tendency to have intrusive thoughts about something started but never finished
  - so even though you want to move on, you keep going back, feel guilty ..
  - expts show that people remember unfinished puzzles much better than solved ones
  - sometimes we've invested too much - hard to objectively judge
- sunk cost fallacy
  - you get emotionally invested in the project once you've put time into it
  - so you feel you can't stop - the time spent would be "wasted"
  - so you keep going
  - connected to personal responsibility - so affects person responsible for committing resources
  - so you end up doing unwise things and continuing investing when you should stop

So how did Alice end up in the rabbit hole in the first place
- django was doing lots of magic to make it easy - so she assumed her change would be easy
- concentrated on surface level issue - symptom, not cause
- continues building on previous partial solution, rather than backing out and starting again
- convinced she was very close to a solution
- cannot give up - too proud, wanting to prove - can be ok on side project, but not good in your job, or a big open source project

What to do:

- first notice that you are in a rabbit hole
  - don't notice when time passes
  - always almost done
  - forget to eat, drink, go to toilet ...
  - when you do step away, you can't stop thinking about the problem
  - haven't spoken with anyone for some time
  - feel cranky about any interruptions
- how to get out
  - estimate time for your next task and set timer
  - make a todo list
  - rubber duck - explain your problem to someone/duck/... - write an email to someone
  - take a longer break - and actually stop thinking about the issue!
  - ask for help

What are your stories about rabbit holes?  How do you get out of them?

- where can I ask for help on Django?
- good to have colleague, even remotely.  Maybe someone else on the internet
- helping others online makes it more likely that others will help you
