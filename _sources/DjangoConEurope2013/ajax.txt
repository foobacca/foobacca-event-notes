AJAX and Django
---------------

problems

- browser history
- deep linking - every page needs URL
- crawler visibility -> SEO indexing

hash fragment - ``domain.com/#/foo/bar/``

- + easy to implement
- + easy for webapps
- - bad for search engines


hash fragment - ``domain.com/#!/foo/bar/``

- + google replaces #! -> ``?_escaped_fragment_=``  - ajax-crawling
- + works for all browsers
- - deep links load first page and then load deeper page
- - multiple URLS for every page
- - maintain legacy urls
- o have to use #! in your sitemap.xml

pushstate

- + already done in back end, reuse URL in front end
- - harder to implement on front end (browser support - but graceful degradation)

PJAX PushState Ajax

- fetch whole page source (or parts)
- extract specified div and update content and title
- push URL

used

- django - template inheritance and filters, middleware
- backbone.js - router ...

conditionally extend base.html or base_pjax.html (which is a json template)

backbone handles link clicks and form submits

pitfalls

- caching - json/html come from same URL -> confuse browser -> cache-control set vary: x-requested-with
- safari (and until recently chrome) ignore vary: header - workaround to put `/_pjax/` at start of URL
- redirecting
- handled transparently wrt XMLHttpRequest - no chance to intercept
- middleware to catch redirect for ajax and return code

client side templates

- reuse server side templates if possible
- plate-js library can use django templates - but doesn't have full context
