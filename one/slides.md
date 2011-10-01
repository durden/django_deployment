<!SLIDE>

Python/Django Deployment
=================================

<!SLIDE bullets>

Luke Lee
========
- Embedded C Developer
- Python/Django enthusiast

<!SLIDE bullets>
.notes There are lots of deployment options, but I personally think they all
still have quirks and haven't found Utopia yet.  However, I want to
focus on arelatively new 'crop' of deployment options specific to
Python/Django apps.

Deployment Options
==================
    - Generic LAMP shared hosting
        - Rackspace cloud
        - Standard home LAMP
        - Webfaction
        - Amazon Web Services
    - Django/Python specific:
        - Gondor (Only django so far)
        - Epio (Django/flask/generic wsgi)
        - Django Zoom
        - Heroku (hybrid) (rails/django/flask/etc.)
        - Dotcloud (too many to list)
    - Platform/API specific:
        - App Engine

<!SLIDE bullets>

Why Django/Python Specific Deployment
=====================================

- I'm not a system admin so the generic lamp hosting is too much of a pain.
- App Engine is good, but afraid of being tied to Google.  However, the ease of
  deployment is unparalled so far.

Good news
---------
    - Built by people who use django
    - Know the pitfalls of deploying django
    - Configure less/code more
    - Ensure more 'standard' or 'rigid' deployment environment that is easily
      duplicated and transferred to new projects.
        - I'm not all that great at setting up environments, keeping up with
          all the little changes/tweaks to Apache, etc.
        - Essentially by limiting my choices to what works for 'most people'
          keeps me from doing obviously stupid things.

Downsides
---------
    - Typically tend to require a specific project layout and tends to be
      pretty painful to deploy if project was already created.
    - Very new services
    - Some don't offer pricing yet
    - Limited amount of features/services (maybe newest NoSQL missing, etc.)
    - Pricing can be complicated:
        - Gondor pricing based on per instance (wsgi process/db/etc)
        - Epio pricing more like AWS or App Engine (amount/hour)

- All the django hosting stuff is pretty new (within past 2 years).  The whole
  idea probably owes alot of its' roots to Heroku, which solved the deployment
  problem with Rails apps.

<!SLIDE bullets>

My Experiences
==============
    - Gondor
    - Epio
    - App Engine

<!SLIDE bullets>

Links
=====
    - http://www.pinboard.in/u:durden/t:django_deployment/
    - https://gist.github.com/1028560

    - @durden20
    - http://github.com/durden
    - http://www.lukelee.net

    - Showoff software = https://github.com/schacon/showoff

<!SLIDE bullets>

Todo
====
    - Go through all pinboard bookmarks and create a tag for django deployment.
    - Take hello world app and deploy on epio/gondor/heroku
        - Take good notes
    - Look over notes from gondor deployment to make sure I can answer
      questions about it.
    - Add some info. about how to deal with static files.  Gondor was pretty
      damn easy if it wasn't for this, and their UI is nice.
    - Maybe discuss deploying django 1.2 vs. 1.3
    - Explain 'general' way of deployment:
        - Download app/cli tool for deployment platform
        - Check out its documentation
        - Create account
        - Commit all the files (this will bite you sometimes on gondor)
