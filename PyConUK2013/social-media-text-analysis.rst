======================================
Detecting the right Apples and Oranges
======================================

Social media text analysis with scikit-learn and NLTK

* Ian Ozsvald
* @IanOzsvald
* applying parallel/NLP/ML in industry
* morconsulting.com
* showmedo.com
* ianozsvald.com - blog with articles about this
* annotate.io
* https://github.com/ianozsvald/social_media_brand_disambiguator

disambiguation is hard
======================

- apple, orange
- homeland, lost, defiance
- elite, valve
- cold, stuffy

Why?
====

current

* 400 million tweets per day
* not trained on social media (long texts, proper grammar, punctuation)
* doesn't take into account links
* rule building often "by hand"

Can we build auto-updating ... disambiguator

Data
====

Scikit-learn example

- apple (computers) or not for tweets that have text "apple" in them - 1 or 0
- matrix y="tweet index" x="unigram features"
- very sparse - have to learn from vast array of 0 texts to spot the few 1s
- Gold standard - 2014 tweets classified by hand (5 hours!)
- 2/3 is-brand, 1/3 not-brand (684)
- test/train, 584 each
- validation set, 100 of each

Results
=======

- first pass - LogisticRegression - fit to data, score test examples
- test against OpenCalais (92.5% precision (true -ve) (2 wrong)), 25% recall (true +ve))
- new tool (100% precision, 51% recall)
- not generalised - still working on it
- all on github
- blogged about it

Future
======

* add link following
* add temporal factors - tweets during apple keynote
* hash tags ...
* NLP meet in London
* bootstrap to larger data
* ...
