# Setting Up Your Environment

### Once you have created your PYAW account, start a bash shell and set up a virtual environment with Python 3.x and Django 4.
mkvirtualenv django4 --python=/usr/bin/python3.9 <br>
pip install django==4.0.7 ## this may take a couple of minutes <br>

### Note if you exit and re-start a new shell on PythonAnywhere - you need the following command to get back into your virtual environment in the new bash shell.
workon django4

### Lets make sure that your django was installed successfully and you are running the rght version of Python with the following commands:
python --version <br>
<!-- This should show something like Python 3.9.5 -->
python -m django --version <br>
<!-- This should show something like 4.0.7 -->

# Installing the Sample Code for DJ4E
### Lets also get a copy of the sample code for DJ4E checked out so you can look at sample code as the course progresses and install some important additional Django software libraries using pip.

cd ~ <br>
git clone https://github.com/csev/dj4e-samples <br>
cd dj4e-samples <br>
pip install -r requirements4.txt <br>
python manage.py check <br>

# When running 'check' works
### Once the check works do:
python manage.py makemigrations <br>
### Then run:
python manage.py migrate <br>

# Building Your Application
### Now that we have your Django set up and you have retrieved the sample code for DJ4E, lets build your first application in the PYAW shell:

cd ~ <br>
mkdir django_projects <br>
cd django_projects <br>
django-admin startproject mysite <br>

### At this point, keep your shell open in one tab and open the PythonAnywhere Files application in another browser tab and navigate to the ~/django_projects/mysite/mysite/settings.py and change the allowed hosts line (around line 28) to be:

ALLOWED_HOSTS = [ '*' ]

### Open web -> scroll down and make changes  
Source code: /home/drchuck/django_projects/mysite <br>
Working directory: /home/drchuck/django_projects/mysite <br>
Virtualenv: /home/drchuck/.virtualenvs/django4 <br>

### <p style="color:red;"> Replace drchuck with your account on PythonAnywhere.</p>

### Then edit the WGSI Configuration File and put the following code into it. Make sure to delete the existing content of the WGSI Configuration File file and completely replace it with the text below. This is slightly different from the sample in the PythonAnywhere tutorial.

import os <br>
import sys <br>

path = os.path.expanduser('~/django_projects/mysite') <br>
if path not in sys.path: <br>
    sys.path.insert(0, path) <br>
os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings' <br>
from django.core.wsgi import get_wsgi_application <br>
from django.contrib.staticfiles.handlers import StaticFilesHandler <br>
application = StaticFilesHandler(get_wsgi_application()) <br>

### Once the above configuration is complete, go back to the top of the PYAW Web tab, Reload your web application, wait a few seconds and check that it is up and visiting the URL for your application shown in in the Web tab on PYAW like:

http://(your-account).pythonanywhere.com/ <br>

# Adding Your Polls Application

## The first step is to make the polls application:
cd ~/django_projects/mysite <br>
python manage.py startapp polls <br>

## Do not run the runserver command on PythonAnywhere. Instead run the following command:
python manage.py check <br>
### And when there are no errors, you are done with the Django Tutorial, come back to these instructions - and navigate to the Web tab in Python anywhere and Reload your application and then test your application by navigating to:
(your-account).pythonanywhere.com/polls <br>
### You should see a line that looks like:
Hello, world. You're at the polls index. <br>

## Going forward, every time we make changes to our application, we should run
python manage.py check <br>


# Do you have two mysite folders?
<img src="https://www.dj4e.com/assn/dj4e_install/install_cleanup.png">

