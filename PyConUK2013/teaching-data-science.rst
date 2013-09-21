===================================================
Teaching Data Science With Really Scrapable Web App
===================================================

* Matthew Hughes
* @matthewhughes
* https://github.com/matthewhughes/really-scrapable-web-app
* http://www.matthewhughes.co.uk/really-scrapable-web-app-is-a-new-way-to-learn-about-web-scraping/
* intern at scraperwiki.com

What is web scraping
--------------------

"the poor man's web API"

Examples:

* publicwhip - scrape hansard, what did your MP vote for/against
* minutemate.co.uk - stop going over monthly limit - scrape phone co site
* kitten finder

How to teach anything?
----------------------

Training wheels to start - easy, then build up to full use

Some sites have counter measures against scraping - if scraping done badly it can be viewed as DoS attack

Really Scrapable Web App
------------------------

Built RSWA to make it easy to start:

* tables
* unclean data
* data in text
* pagination
* user agent filtering
* JS rendering -> use selenium and web driver
* xml/json
* spreadsheets

Series of challenges, getting more difficult

Built on flask - easy to get going, good docs, fast development ...

Flask megatutorial_ was excellent

.. _megatutorial: http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world

Solutions:

* lxml
* PyQuery (jquery like HTML selection)
* Beautiful Soup
* *gasp* Nokogiri
* Webdriver/selenium

https://github.com/matthewhughes/RSWA-Solutions
