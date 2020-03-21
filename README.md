# Be-Techy(content aggregator)
It is a web application which aggregates data (Technology news articles) from multiple websites. 

## Table of contents
### Requirements:
 - IDLE: IDE for Python

 - Django: Python Web framework

 - News API: Python client library 

### Implementation:
You can simply install django by using this command:
```bash
pip install django 
```
OR try [django installation](https://simpleisbetterthancomplex.com/series/2017/09/04/a-complete-beginners-guide-to-django-part-1.html#hello-world)

OK after installing django you need to make account in [News API](https://newsapi.org/), 
because we are going to fetch the data from their and also you need to get your api key from their. 
for the installation of this library you can simply use:
```bash
pip install newsapi-python    
```

Open Command Prompt
you need to use this command for creating of project in django.

```bash
django-admin startproject News
```
You can change the name of the project according to your choice.


After that you need to migrate your migrate your project by this command:
```bash
python manage.py migrate
```

Now you need to create a new app in your django project.
django apps are the small pieces of a website or a web application, in django project as many apps you want you can create.
```bash
python manage.py createapp NewsApp 

```
### OR

```bash
python manage.py startapp NewsApp 

```
you need to add your new app in the django setting Installed App section like this .

![set](https://user-images.githubusercontent.com/59923183/77224962-98214000-6b90-11ea-88f5-0a71741e0ba7.PNG)


The structure of django project:
```

News/
 |-- News/
 |    |-- __init__.py
 |    |-- asgi.py
 |    |-- settings.py
 |    |-- urls.py
 |    |-- wsgi.py
 |-- NewsApp/                <-- our new django app!
 |    |-- migrations/
 |    |    +-- __init__.py
 |    |-- static/
 |    |    +-- images
 |    |-- __init__.py
 |    |-- admin.py
 |    |-- apps.py
 |    |-- models.py
 |    |-- urls.py
 |    |-- tests.py
 |    +-- views.py
 |-- templates/
 |    |-- index.html
 |    |-- techcrunch.html (other 5 websites)
 |-- db.sqlite3
 +-- manage.py
```
also you can see that there is a templates folder and seven html files in their,
so these are the html files.

index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Be Techy</title>
    <style>body.solid {border-style: solid;}</style>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
   <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
   </head>
<body class="solid" >
{% load static %}
<div class="jumbotron" style="background-image: url({% static 'tc3.jpg' %}); color:black,min-height: 300;">

{% load static %}
<img align="left" src="{% static "bte.png" %}" alt="BeTechy" style="margin-top:-34px"; height="135" width="155">

    <h1 style="color:black;font-size:50px;font-family:Arial Black" align="center">
        Be Techy: Latest News 
    </h1>
</div>

<center>
   <a class="btn btn-secondary btn-lg" role="button" href="http://127.0.0.1:8000/TechRadar" style="background-color:gray;font-size: 28px;">TechRadar</a>&nbsp;&nbsp;&nbsp;&nbsp;
  <a class="btn btn-primary btn-lg" role="button" href="http://127.0.0.1:8000/techcrunch" style="font-size: 28px;">Techcrunch</a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a class="btn btn-secondary btn-lg" role="button" href="http://127.0.0.1:8000/wired" style="background-color:gray;font-size: 28px;">Wired</a>
	 &nbsp;&nbsp;&nbsp;&nbsp;
	<a class="btn btn-primary btn-lg" role="button" href="http://127.0.0.1:8000/theverge" style="font-size: 28px;">The Verge</a>
&nbsp;&nbsp;&nbsp;&nbsp;
<a class="btn btn-secondary btn-lg" role="button" href="http://127.0.0.1:8000/thenextweb" style="background-color:gray;font-size: 28px;">The Next Web</a>
&nbsp;&nbsp;&nbsp;&nbsp;
<a class="btn btn-primary btn-lg" role="button" href="http://127.0.0.1:8000/engadget" style="font-size: 28px;">Engadget</a>
<br>
</center><br><br>
<div class="container">
  <div class="row" >

{% for new, des,i,ur in mylist %}
<div class="col-lg-4" >
<div class="thumbnail" style="border-color: black;border-width: 2px;">

<a href="{{ur}}" target="_blank">
<br><h1> {{new}}</h1> <br>
<img src="{{i}}" alt="" width="390" height="240">
</a>
<br><div class="caption" style="font-size: 20px;">     
<b>Description: </b>{{des}}
	</div>
</div>
</div>

{% endfor %}   

</div></div>
</body>
</html>
```

techcrunch.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Techcrunch News</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
  
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
</head>
<body>
{% load static %}
<div class="jumbotron" style="background-image: url({% static 'tc3.jpg' %}); color:black,min-height: 300;">
{% load static %}
<img align="left" src="{% static "techcrunch.png" %}" alt="Techcrunch" style="margin-top:-0px"; height="80" width="350">

      <h1 style="color:black;font-family:Eras Demi ITC;" align="center">
      <b> Techcrunch News</b>

    </h1>

</div>
<div class="container">
  <div class="row">

{% for new, des,i,ur in mylist %}
<div class="col-lg-4" >
<div class="thumbnail" style="border-color: black;border-width: 2px;">

<a href="{{ur}}" target="_blank">
<br><h1> {{new}}</h1> <br>
<img src="{{i}}" alt="" width="390" height="240">
</a>
<br><div class="caption" style="font-size: 20px;">     
<b>Description: </b>{{des}}
    </div>
</div>
</div>

{% endfor %}   

</div></div>


</body>
</html>
```
For other 5 wesites do same.

Add templates to settings.py. See below picture:

![tem](https://user-images.githubusercontent.com/59923183/77226012-b8ee9300-6b9a-11ea-93b5-935bc389357d.PNG)

And also add static folder path at the end in settings.py:
```python

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/3.0/howto/static-files/

STATIC_URL = '/static/'
```

And this is our views.py that we have created for seven url functions. 
One for main index page and six for other technical websites.

NewsApp\views.py:

```python
from django.shortcuts import render
from newsapi import NewsApiClient


def index(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='TechRadar,techcrunch,wired,engadget,the-next-web,the-verge')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'index.html', context={"mylist":mylist})



def TechRadar(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='TechRadar')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'TechRadar.html', context={"mylist":mylist})



def techcrunch(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='techcrunch')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'techcrunch.html', context={"mylist":mylist})
#google-news,engadget,business-insider,wired,the-times-of-india,techcrunch,the-verge,the-next-web

def wired(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='wired')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'wired.html', context={"mylist":mylist})

def theverge(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='the-verge')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'theverge.html', context={"mylist":mylist})

def thenextweb(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='the-next-web')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'thenextweb.html', context={"mylist":mylist})


def engadget(request):
    newsapi = NewsApiClient(api_key="b0f75ce660c0466a9a98c2478f8abb62")
    topheadlines = newsapi.get_top_headlines(sources='engadget')


    articles = topheadlines['articles']

    desc = []
    news = []
    img = []
    ur = []

    for i in range(len(articles)):
        myarticles = articles[i]

        news.append(myarticles['title'])
        desc.append(myarticles['description'])
        img.append(myarticles['urlToImage'])
        ur.append(myarticles['url'])


    mylist = zip(news, desc, img, ur)


    return render(request, 'engadget.html', context={"mylist":mylist})
```

Also one important issue you need to create a new python file in your NewsApp django app 
and add these codes for url routing.

NewsApp\urls.py:

```python
from django.urls import path
from .views import index,TechRadar, techcrunch, wired ,theverge, thenextweb, engadget 

urlpatterns = [
path('', index, name = 'index'),
path('TechRadar/', TechRadar, name = 'TechRadar'),
path('techcrunch/', techcrunch, name = 'techcrunch'),
path('wired/', wired, name = 'wired'),
path('theverge/', theverge, name = 'theverge'),
path('thenextweb/', thenextweb, name = 'thenextweb'),
path('engadget/', engadget, name = 'engadget'),

]
```

Also in your main urls.py you need to add these codes.

News\urls.py:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('NewsApp.urls'))
]
```

So now run your django project and this will be the result, you can use this command for runing your django project.
Copy the file path which contains manage.py file.
```
Ex: F:\News
```

```bash
python manage.py runserver
```
Open Browser and Enter this URL:
```
http://127.0.0.1:8000/
```

## OR To execute existing file:

Download News.rar file

Extract it.

Open the News folder.

Copy the file path which contains manage.py file.
```
Ex: F:\News
```

To run it type this in Command prompt:
```bash
python manage.py runserver
```
Open Browser and Enter this URL:
```
http://127.0.0.1:8000/
```

## Result:
Index page:

![resultbetechy](https://user-images.githubusercontent.com/59923183/77226630-d1ad7780-6b9f-11ea-9606-22bfecd4e42c.png)


Techcrunch :

![techcrunchbetechy](https://user-images.githubusercontent.com/59923183/77226631-d5d99500-6b9f-11ea-9402-89df2c1e76f3.png)

## Team Members

[@saloneesp](https://github.com/orgs/RAITG11/people/saloneesp)

[@shweta235](https://github.com/orgs/RAITG11/people/shweta235)

[@SonaliMalage](https://github.com/orgs/RAITG11/people/SonaliMalage)





