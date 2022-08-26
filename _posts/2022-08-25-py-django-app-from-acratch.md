---
layout: post
title: Django CRUD
tags: phase-2 django crud
---

## 🎯 Project: Django Duplex
**Due Thursday, Sept. 1**

Goal for Monday: Replicate what you have in Django music in this new app.

[Assignment Link](https://classroom.github.com/a/c1ExkMow)


## 🔖 Resources

- [Setting Up Django App Video](https://us02web.zoom.us/rec/share/JH1X-QQw-jQnuiAQy6cv06JN_B4NkR_3vOLLF8zKl5-a7RSlq9v36K3W6-8-jo8O.A37KEJXcRjlZvwUY?startTime=1661451407000)
Passcode: R6OM9h%!
- [User and Registration video]()
  - Caution: don't do makemigrations and migrate until you have added your User model
  - TL;DR Here's what to do to implement basic registration and login using Django Registration Redux
    - Make sure you have a `base.html` template in the root of your `templates` directory and that it contains `{% block content %}{% endblock %}`
   - Run `pipenv install django-registration-redux` and add "registration" to the top of the INSTALLED_APPS list in `settings.py`
   - Add the urls to your urls.py as desribed here - [Django Registration Redux one-step backend](https://django-registration-redux.readthedocs.io/en/latest/simple-backend.html)
   - These are the [urls](https://django-registration-redux.readthedocs.io/en/latest/urls.html) you now have access to, all beginning with `accounts/`. 
- [Making a Gitignore file](https://www.toptal.com/developers/gitignore/)
- [Custom User model in Django App](https://docs.djangoproject.com/en/4.1/topics/auth/customizing/#using-a-custom-user-model-when-starting-a-project)
  - Note: decide how you are going to configure the User model at the *beginning* of the project.

 .


## 🦉 Code & Notes

- [Starting Code for app from class](https://github.com/Momentum-Team-14/django-duplex-rlconley/pull/1/files)