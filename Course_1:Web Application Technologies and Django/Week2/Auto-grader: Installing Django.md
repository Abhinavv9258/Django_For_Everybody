# Setting Up Your Environment
Once you have created your PYAW account, start a bash shell and set up a virtual environment with Python 3.x and Django 4.

mkvirtualenv django4 --python=/usr/bin/python3.9
pip install django==4.0.7 ## this may take a couple of minutes

Note if you exit and re-start a new shell on PythonAnywhere - you need the following command to get back into your virtual environment in the new bash shell.

workon django4
Lets make sure that your django was installed successfully and you are running the rght version of Python with the following commands:

python --version
<!-- This should show something like Python 3.9.5 -->
python -m django --version
<!-- This should show something like 4.0.7 -->

# Installing the Sample Code for DJ4E
Lets also get a copy of the sample code for DJ4E checked out so you can look at sample code as the course progresses and install some important additional Django software libraries using pip.

cd ~
git clone https://github.com/csev/dj4e-samples
cd dj4e-samples
pip install -r requirements4.txt
python manage.py check

# When running 'check' works
Once the check works do:
python manage.py makemigrations
Then run:
python manage.py migrate

# Building Your Application
Now that we have your Django set up and you have retrieved the sample code for DJ4E, lets build your first application in the PYAW shell:

cd ~
mkdir django_projects
cd django_projects
django-admin startproject mysite
At this point, keep your shell open in one tab and open the PythonAnywhere Files application in another browser tab and navigate to the ~/django_projects/mysite/mysite/settings.py and change the allowed hosts line (around line 28) to be:

ALLOWED_HOSTS = [ '*' ]


Source code: /home/drchuck/django_projects/mysite
Working directory: /home/drchuck/django_projects/mysite
Virtualenv: /home/drchuck/.virtualenvs/django4

Replace drchuck with your account on PythonAnywhere.

Then edit the WGSI Configuration File and put the following code into it. Make sure to delete the existing content of the WGSI Configuration File file and completely replace it with the text below. This is slightly different from the sample in the PythonAnywhere tutorial.

import os
import sys

path = os.path.expanduser('~/django_projects/mysite')
if path not in sys.path:
    sys.path.insert(0, path)
os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'
from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())

Once the above configuration is complete, go back to the top of the PYAW Web tab, Reload your web application, wait a few seconds and check that it is up and visiting the URL for your application shown in in the Web tab on PYAW like:

http://(your-account).pythonanywhere.com/

# Adding Your Polls Application

## The first step is to make the polls application:
cd ~/django_projects/mysite <br>
python manage.py startapp polls

## Do not run the runserver command on PythonAnywhere. Instead run the following command:
python manage.py check
### And when there are no errors, you are done with the Django Tutorial, come back to these instructions - and navigate to the Web tab in Python anywhere and Reload your application and then test your application by navigating to:
(your-account).pythonanywhere.com/polls
### You should see a line that looks like:
Hello, world. You're at the polls index.

## Going forward, every time we make changes to our application, we should run
python manage.py check


# Do you have two mysite folders?
<img src="https://www.dj4e.com/assn/dj4e_install/install_cleanup.png">

