Web accessibility is not an option
==================================

Xavier Dutreilh

The Problem
-----------

Consider life without the web - and all the small opportunities it has brought you.

Some people have issues - because we design websites for non-disabled people

Disability is a consequence of an impairment

- from birth or acquired later
- progressive or non-progressive
- visual, hearing, motor or cognitive
- visual - blind, low-vision, colour blind
- hearing - deaf, or limited hearing
- motor - limited dexterity or loss of limbs
- cognitive - learning issues or memory loss

How to do web accessibility

- try using a screen reader!
- provide alt text to non text content

  - just alt="Image of Xavier" - still bad, as screen reader says ``"image of {}".format(alt_text)``
  - alt="Xavier" is appropriate, or alt="Xavier giving a talk"

- provide appropriate doc structure with tags

  - ``<header></header><nav></nav><main><article></article></main><footer></footer>``

- don't use lists when not a list - screen reader noise
- do tables properly - ``<thead>`` section really helps
- provide appropriate validation and errors for forms

  - Django is pretty good, more relevant for JS front end stuff
  - use label tag with for attr - ``<label for="name">Name</label><input name="name" ...>``

- appropriate link description to links

  - screen reader will collect links on page and read to user without surrounding context
  - Bad - ``<a href="/articles">Read all articles`</a>``
  - Better - ``<a href="/articles">Read all articles</a>``

- caption and transcripts for audio and video
- accessibility for non-html content (eg PDF)

  - same guidelines as web, when building in Word (or whatever)

- allow users to skip repetitive elements on the page

  - ``<a href="#content" class="hidden-except-screen-readers">Skip to main content</a>``

- Do not rely on colour alone to convey info

  - bad - ``<span class="label green"></span>``
  - good - ``<span class="label green">some label</span>``

- make sure content is clearly written and easy to read (hard to apply)

  - writing in second language
  - sometimes assumes shared culture
  - "Write explicit, clear, simple and positive sentences"

- Use clear fonts, relative units (better for zooming) and strong contrasts

  - and avoid blinking or moving text at all costs
  - or any moving element

- make browser side JS code accessible

  - most screen readers use JS
  - avoid device dependent events

- design to standards - avoid hacks

  - avoid inline styles, deprecated tags and missing attributes

Where do we go?

- learn about impairment and disability
- listen to people with disabilities (and the variety)
- guidelines - WCAG, ATAG, UUAG, ARIA
- try accessibility tools on laptop or smartphone - screen reader, high colour contrast ...
- validate your web app with WAVE
- chrome accessibility developer tools
- provide your skills to accessibility organisations

Comments and Questions

- Designers - get out of my way - eg restrict zoom with viewport setting
- is there a cmd line tool to validate, so it can be used in unit tests
- don't build a second version - allow skipping info
