---
layout: post
title: 🐻 API Progress Check-In 🐻
tags: phase-3 phase-3-be admin password
---

## 🗓️ Today's Topics

- How are the projects coming along? 👀
- Automatic deploys from GitHub
- Paginating your API

## 🎯 Project

Keep on going. 💪 🚀

We will use class time today to get you past any blockers you may be experiencing and to talk through next steps.

By now you should have provided your front end with endpoints to see data and gotten djoser installed so that your log in and log out endpoints are working.

By tomorrow you should have the ability to create at least questions or cards via POST requests, and maybe more.

## 📖 Read | 📺 Watch | 🎧 Listen

On Monday we'll be covering full-text search in your API, but if you have time you can check these resources out in advance.

- [Search from the Ground Up](https://www.youtube.com/watch?v=is3R8d420D4&list=PL2NFhrDSOxgXXUMIGOs8lNe2B-f4pXOX-&index=2) -> DjangoCon 2019 video explaining search in detail
- 📖 [Basic and Full-Text Search with Django and Postgres](https://testdriven.io/blog/django-search/)
- 📖 [Blog post with more on full-text search](https://www.netlandish.com/blog/2020/06/22/full-text-search-django-postgresql/)
- 📖 [If you want A LOT more detail about full-text search in Postgres and Django, this blog piece has you covered](https://pganalyze.com/blog/full-text-search-django-postgres)

## 🔖 Resources

### Authentication

Make sure you are sharing the Djoser information with your front end. You should include the authentication endpoints in your API documentation or project README.

- [Base Endpoint Guide for Djoser](https://djoser.readthedocs.io/en/latest/base_endpoints.html) -> includes create a new user and other nice stuff
- [Token Authentication Endpoint Guide for Djoser](https://djoser.readthedocs.io/en/latest/token_endpoints.html) -> details on the token auth endpoints

### Creating a properly hashed password

In order to save a properly hashed password when you create a new user in the Django Admin, make sure you are using `UserAdmin` in `admin.py` so that you have that option in the admin interface. If you don't do this and save an unhashed password, you will run into authentication errors.

```py
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
...
admin.site.register(User, UserAdmin)
```

You can also change a password from the command line:

- [Django Docs: Changing a password](https://docs.djangoproject.com/en/4.0/topics/auth/default/#changing-passwords)

### Pagination

- [DRF docs: Pagination](https://www.django-rest-framework.org/api-guide/pagination/)


