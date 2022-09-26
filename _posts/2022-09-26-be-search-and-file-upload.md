---
layout: post
title: 🐻 Search & Automatic Deploys 🐻
tags: phase-3 phase-3-be full-text-search deploy file-upload
---

## Today's Topics

- Implementing search, including Postgres full-text search

## 🎯 Project due on Thursday afternoon

**Please include a README** in your project repo. The README should:

- be written in Markdown
- include your production application's URL
- have instructions for getting your application running locally, so that any developer could pull it down and run it. If your setup makes any assumptions about the environment (e.g., you have Python 3.10.2 installed locally), you should state them in the README.

**Your README should include clear documentation for your API's available endpoints.**

👉 If your project meets minimum requirements today, HUZZAH! 🎉 That is awesome. You should be working on **at least one additional or spicy feature**.

👉 If your project does not yet meet minimum requirements, you should aim for meeting them **by the end of the day Wednesday**.



### Requirements for QuestionBox, Back End

#### Note

Depending on how you've constructed your API, you might have separate endpoints for all of the below, or some of the functionality might be combined in a single endpoint (for instance, if you nested answers in the question detail endpoint, like `questions/4/answers`). What matters is that you have endpoints that your front-end team can use to perform all the necessary actions they need and that are documented in your README.

⚠️ Be sure to test that you have implemented permissions-checking correctly for these endpoints. For example, your API should not allow a user who is not the question-asker to mark an answer as accepted.

- token login, logout, and register (i.e., create a new user)
- list all questions
- list answers to a specific question
- show details about a specific question
- create a question (if authenticated)
- create an answer to a question (if authenticated and if you are not the question asker)
- mark an answer as "accepted" (if you are the question asker)
- list of own questions for an authenticated user
- list of own answers for an authenticated user
- star/favorite questions or answers
- unstar/unfavorite questions or answers
- search questions (possibly both questions and answers)
- A README with endpoints documented

### Requirements for Social Cards, Back End

⚠️ Be sure to test that you have implemented permissions-checking correctly for these endpoints. For example, your API should not allow a user who is not the creator of a card to update a card.

- token login, logout, and register (i.e., create a new user)
- list all cards
- list all cards you've created (you, the authenticated user)
- list all cards created by a user that you follow
- show details of one card
- create a new card (if authenticated)
- update a card (if authenticated and it's your card)
- delete a card (if authenticated and it's your card)
- follow another user (if authenticated)
- unfollow another user (if authenticated)
- list all the users you follow
- A README with endpoints documented

## Handling requests that include attached files

#### Using Insomnia

- Select the right HTTP method for your endpoint.
- Choose binary file attachment from the body menu (where you normally put the body of a request)
- Set headers on the Headers tab (this example assumes an image file in jpeg format, named `profile-photo.jpg`):

  ```txt
  Content-Type: image/jpeg
  Content-Disposition: attachment; filename=profile-photo.jpg
  ```

For more information on the values for `Content-Type`:

- [MDN Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types)

#### CORS for file upload

Assuming you are using `django-cors-headers`, you'll need to add the following to `settings.py` to allow the request headers necessary for file attachments:

```py
# in settings.py

from corsheaders.defaults import default_headers

CORS_ALLOW_HEADERS = list(default_headers) + [
    'content-disposition',
]
```

## 📖 Read | 📺 Watch | 🎧 Listen

### File Upload

- [Django File (and Image) Uploads Tutorial](https://learndjango.com/tutorials/django-file-and-image-uploads-tutorial) -> A good and very recent post from Will Vincent; he does not include all the necessary info to make file uploads work in production but otherwise it's a good overview.
- 📖 [File Upload with DRF](https://goodcode.io/articles/django-rest-framework-file-upload/)
- 🎧 + 📖 [Success with Static Files](https://www.mattlayman.com/django-riffs/success-static-files/)
- 📖 [What is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) -> Skim this -- this is Amazon's documentation and it gets really in-depth.
    - 📺 [Introduction to S3](https://www.youtube.com/watch?v=77lMCiiMilo) -> Also from Amazon

### Search

- 📖 [Basic and Full-Text Search with Django and Postgres](https://testdriven.io/blog/django-search/)
- 📖 [If you want A LOT more detail about full-text search in Postgres and Django, this blog piece has you covered](https://pganalyze.com/blog/full-text-search-django-postgres)
- 📖 [Blog post with more on full-text search](https://www.netlandish.com/blog/2020/06/22/full-text-search-django-postgresql/)
- 📺 [Search from the Ground Up](https://www.youtube.com/watch?v=is3R8d420D4&list=PL2NFhrDSOxgXXUMIGOs8lNe2B-f4pXOX-&index=2) -> Will Vincent talk at DjangoCon 2019 explaining search in detail
- 📺 [Pretty Printed: How to Perform Full Text Searches in Django with Postgres](https://www.youtube.com/watch?app=desktop&v=139a0fm0YFY)

## 🔖 Resources

### 📁 Creating a README

- [Make a README](https://www.makeareadme.com/)
- [Awesome README](https://github.com/matiassingers/awesome-readme) _way more here than you actually need but you might like this mega-list of resources._

### `@action` decorator in ViewSets

- [DRF Docs: Marking extra actions for routing with the `@action` decorator](https://www.django-rest-framework.org/api-guide/viewsets/#marking-extra-actions-for-routing)
- [DRF Docs: Routing for extra actions](https://www.django-rest-framework.org/api-guide/routers/#routing-for-extra-actions)

### Filtering and search

- [DRF - Filtering](https://www.django-rest-framework.org/api-guide/filtering/) -> Includes how to filter your output based on GET parameters, which you will want to do for using search terms.
- [Django Docs: full-text search & the search lookup](https://docs.djangoproject.com/en/4.0/ref/contrib/postgres/search/#the-search-lookup)
- [Django Docs: SearchVector](https://docs.djangoproject.com/en/4.0/ref/contrib/postgres/search/#searchvector) -> You'll need this if you want to search against more than a single field

### File uploads

- [Django Docs: ImageField](https://docs.djangoproject.com/en/3.2/ref/models/fields/#imagefield)
- [Django Docs: FileField](https://docs.djangoproject.com/en/3.2/ref/models/fields/#filefield)
- [Pillow: Python Imaging Library](https://pillow.readthedocs.io/en/stable/)
    - [`django-imagekit`](https://django-imagekit.readthedocs.io/en/latest/) -> If you want to resize images when they are uploaded, or do any kind of image processing, you will need this. Don't add it unless you know you need it.
- [How to Set Up Amazon S3](https://simpleisbetterthancomplex.com/tutorial/2017/08/01/how-to-setup-amazon-s3-in-a-django-project.html)
    - [AWS S3 Free Tier Info](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=categories%23storage)
- [`django-storages`](https://django-storages.readthedocs.io/en/latest/index.html)
- [DRF `FileUploadParser`](https://www.django-rest-framework.org/api-guide/parsers/#fileuploadparser) _Without this you will get errors about unsupported media types_

## 🦉 Code & Notes

- [Notes on Django Queries](https://github.com/Momentum-Team-13/notes/blob/main/django-queries.md) These are the same notes you may have seen at the beginning of the Phase. I'm including them here for easy reference, as they show examples of queries and filters that might come in handy for search endpoints.
