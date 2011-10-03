<!SLIDE bullets>

Python/Django Deployment
========================

- [http://durden.github.com/django_deployment](http://durden.github.com/django_deployment)

<!SLIDE bullets>

Luke Lee
========
- Embedded C Developer
- Python/Django enthusiast

<!SLIDE bullets>

Overview
========
- Different deployment strategies
- Why specific Python/Django deployment
- General 'flow' of deployment
- My deployment experiences

<!SLIDE bullets incremental>

Deployment Options
==================
- LAMP
- Platform/API specific
- Django/Python specific

.notes There are lots of deployment options, but I personally think they
all still have quirks and haven't found Utopia yet.  However, I want to
focus on a relatively new 'crop' of deployment options specific to
Python/Django apps.

<!SLIDE bullets incremental>

LAMP Hosting
===================
- Rackspace cloud
- Webfaction
- Amazon Web Services
- Homebrew LAMP

<!SLIDE bullets incremental>

Platform/API specific
=====================
- App Engine

<!SLIDE bullets incremental>

Django/Python specific
======================
- Gondor
- Epio
- Heroku
- Django Zoom
- Dotcloud

<!SLIDE bullets incremental>

Why Specific Deployment
=======================

- Not a system admin
- Concentrate on code
- Avoid vendor lock-in

<!SLIDE bullets incremental>

Good News
=========
- Built by people who use Django
- Understand pitfalls of deploying Django
- Configure less/code more
- Ensure more 'standard' or 'rigid' environment
- Easily duplicated and transferred to new projects.

.notes I'm not all that great at setting up environments, keeping up with
all the little changes/tweaks to Apache, etc.  Essentially by limiting my
choices to what works for 'most people' keeps me from doing obviously stupid
things.

<!SLIDE bullets incremental>

Bad News
========
- Very new
- Some don't offer pricing yet
- Pricing can be complicated
- Require specific project layout
- Painful to deploy existing projects
- Limited amount of features/services
- Very different ways to handle settings.py/paths/etc.

.notes All the Django hosting stuff is pretty new (within past 2 years).
The whole idea probably owes a lot of its' roots to Heroku, which solved the
deployment problem with Rails apps.

<!SLIDE bullets incremental>

General deployment flow
=======================
- Create account
- Download app/cli tool
- Read documentation (syncdb/static files/shell)
- Commit all files (most/all deployed with vcs)

<!SLIDE bullets>

My Experiences
==============
- Epio
- Gondor
- Heroku

<!SLIDE smaller>

Epio
====
- Python 2.7
- Postgres/Redis
- Allows 3rd party libraries (some C extensions)
- Git/Hg
- Any wsgi app
- 1 instance/5GB BW/2GB DB
- Pricing based on pay per use (amount/hour)

<!SLIDE smaller>

Epio
====
- Create production_settings.py
- Create config file epio.ini
- Reference production_settings.py in epio.ini
- Override settings.py

<!SLIDE smaller>

Gondor
======
- Python 2.7
- Postgres
- Allows 3rd party libraries (some C extensions)
- Git/Hg
- Django/Pinax
- Pricing based on per instance (wsgi process/db/etc)
- Redis caching

<!SLIDE smaller>

Gondor
======
- Requires a bit more work
- Forces modifications to sys.path
- Creation of wsgi.py, modifications to settings.py
- [install notes gist](https://gist.github.com/1028560)

<!SLIDE smaller>

Heroku
======
- Python 2.7
- Postgres
- Allows 3rd party libraries (some C extensions)
- Uses Cedar stack
- Any Python framework
- Git/svn
- Pricing based on per instance (wsgi process/db/etc)
- 5MB database/750 dyno hours

<!SLIDE smaller>

Heroku
======
- [codrspace](http://blooming-samurai-1554.herokuapp.com/)
- [install notes](http://blooming-samurai-1554.herokuapp.com/durden/)
- [gist](https://gist.github.com/1256423)
- Auto-injects code into your settings.py to avoid sys.path changes, etc.

<pre style='font-size:12pt'><code>
diff --git a/requirements.txt b/requirements.txt
index 4b39bab..deed5a4 100644
--- a/requirements.txt
+++ b/requirements.txt
@@ -3,4 +3,5 @@ django
psycopg2==2.4.2
Markdown==2.0.3
Pygments
<font color="red">
--e git://github.com/kennethreitz/requests.git#egg=requests
</font>
<font color="green">
+requests
+#-e git://github.com/kennethreitz/requests.git#egg=requests
</font>
</pre></code>

<!SLIDE smaller>

Tips/tricks
===========
- Use staticfiles or Django 1.3
- Django 1.3 seems more popular/easy to deploy
- Create branches to track different deployments for each project
- How to store/track specific deployment settings for collaboration

<!SLIDE>

Changelog
=========
<table style="margin-left: 20%; text-align: center;font-size: 130%; line-height: 150%;">
    <thead>
        <tr>
            <th style="padding: 10px 8px;">Service</th>
            <th style="padding: 10px 8px;">Commits</th>
            <th style="padding: 10px 8px;">Files changed</th>
            <th style="padding: 10px 8px;">Insertions</th>
            <th style="padding: 10px 8px;">Deletions</th>
        </tr>
    </thead>
    <tr>
        <td>Epio</td>
        <td>12</td>
        <td>18</td>
        <td>115</td>
        <td>26</td>
    </tr>
    <tr>
    <tr>
        <td>Gondor</td>
        <td>11</td>
        <td>49</td>
        <td>1126</td>
        <td>12</td>
    </tr>
    <tr>
        <td>Gondor</td>
        <td>10</td>
        <td>16</td>
        <td>130</td>
        <td>12</td>
    </tr>
    <tr>
        <td>Heroku</td>
        <td>7</td>
        <td>107</td>
        <td>5219</td>
        <td>5217</td>
    </tr>
    <tr>
        <td>Heroku</td>
        <td>9</td>
        <td>7</td>
        <td>8</td>
        <td>7</td>
    </tr>
</table>

<!SLIDE smaller>

Links
=====
- Code
    - [references](http://www.pinboard.in/u:durden/t:Django_deployment/)
    - [presentation code](https://github.com/durden/django_deployment)
    - [showoff](https://github.com/schacon/showoff)

- Me
    - [@durden20](http://twitter.com/#!/durden20)
    - [http://github.com/durden](http://github.com/durden)
    - [http://www.lukelee.net](http://www.lukelee.net)

<!SLIDE bullets>

Extra Notes
===========
- Open up the following files for viewing in presentation:
    - ~/Documents/code/web/frameworks/django/codrspace/production_settings.py
    - ~/Documents/code/web/frameworks/django/codrspace/epio.ini
    - ~/Documents/code/web/frameworks/django/gondor_deployments/blog/blog_template/.gondor/config
    - Gists:
        - [gondor](https://gist.github.com/1028560)
        - [heroku](https://gist.github.com/1256423)
