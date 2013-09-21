======================
Mining Python Software
======================

* Sarah Mount

What do we know about software?
===============================

* How to make it correct
* How long it will take to write
* expected bugs per kloc

Er ... yeah

Lots of studies done on students (as they're available to academics) but not necessarily good for industry.

WARNING: this is a work in progress - interim numbers

Where to find info
==================

Don't write your own scripts to scrape github, google code etc.  Use 

* ohloh - good API - github, google code, bitbucket ...
* github archive
* google bigquery interface

Code Clones
===========

* type 1: identical code, copy and pasted
* type 2: identical code, names changed, layout, comments etc
* type 3: as type 2, plus further modifications such as change in statement
* type 4: completely different code, same semantics (no tools auto-detect this yet)

Tool: Clone Digger

Take 500 most forked python repos on github, clone them, run clone digger (and other tools) over all code and collate results.

Code clones - most python projects similar - very low - but some stand out.  evervim and everpad have over 40,000 clones.

* Normalised clone density - take into account size of project
* length of code clones (lines of code cloned)

Aggregate Sentiment of Comments
===============================

Most pretty neutral - NewsBlur was amazingly happy
