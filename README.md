# Django arc
![image](https://user-images.githubusercontent.com/80549753/216788425-5a41fac7-51f1-484b-b8a4-ce5236216c3b.png)
![image](https://user-images.githubusercontent.com/80549753/219374285-47f633c2-0d68-4612-ae47-cbe302cad1dd.png)
# More: https://github.com/Ayon-SSP/DjangoLearnBootStrap
# Django Setup
## 1. create project & app
```bash
django-admin startproject my_project # create project
cd my_project/
python3 manage.py startapp home # create app
python3 manage.py runserver # run server
```
## 2. Add in `url.py` project
```python
from django.urls import include, path
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('home.urls'))  # All the urs from home.urls will be added to urlpatterns
]
```
- create `urls.py` in app
```python
from django.contrib import admin
from django.urls import path
from home import views

urlpatterns = [
    path('', views.index, name='home' ),
    path('docs', views.docs, name='docs' ),
    path('about', views.about, name='about' ),
    path('services', views.services, name='services' ),
    path('contact', views.contact, name='contact' ),
    path('profile', views.profile, name='profile' ),
    path('bsLearning', views.bsLearning, name='bsLearning' ),

    path('LearningDTL', views.LearningDTL, name='bsLearning' ),
    path('add', views.add, name='Adding' ),
]

```

## 3. Add in `views.py` 
```python
from django.shortcuts import render, HttpResponse

# Create your views here.
def index(request):
    # return HttpResponse("<center><h1>Home 🏠 </h1></center>")
    # To send variables to the template, we use the render function
    context = {
        'Name' : 'Ayon Karmakar',
        'age' : 21,
        'hobbies' : ['Coding', 'Gaming', 'Sleeping', 'Eating', 'Watching Anime'],
        # 'hobbies' : {'p' :'Coding'}
        'profileImageUrl': 'https://avatars.githubusercontent.com/u/80549753?s=400&u=74659f0d3a599612e461950bd720e16345ebf4c8&v=4',
    }
    return render(request, 'index.html', context)
    # return render(request, 'bootstrapComp.html')

def docs(request):
    return HttpResponse("<center><h1>Docs 📚 </h1></center>")

def about(request):
    # return HttpResponse("<center><h1>About 🅰️ </h1></center>")
    return render(request, 'about.html')

def services(request):
    return HttpResponse("<center><h1>Services 🛠️ </h1></center>")

def contact(request):
    # return HttpResponse("<center><h1>Contact 📞 </h1></center>")

    if request.method == "POST": # if form is rendered else it will not be rendered
        name = request.POST.get('name')
        email = request.POST.get('email')
        phone = request.POST.get('phone')
        desc = request.POST.get('desc')
        date = request.POST.get('date')


    return render(request, 'contact.html')


    return render(request, 'contact.html')

def profile(request):
    # return HttpResponse("<center><h1>Profile 📝 </h1></center>")
    profileLinks = {
        'pL' : ['https://us.123rf.com/450wm/moremar/moremar1903/moremar190300013/moremar190300013.jpg?ver=6',
                'https://media.istockphoto.com/id/1193146236/vector/portrait-of-a-businessman-avatar-of-a-young-man-for-social-network.jpg?s=170667a&w=0&k=20&c=tzuR2fBVV1ThyKl3p-8DRPDj1yD4ttC5_myLku6CAT8=',
                'https://media.istockphoto.com/id/1190616457/vector/head-of-a-little-asian-girl-in-profile-the-face-of-a-child-on-the-side-portrait-avatar.jpg?s=612x612&w=0&k=20&c=P2MQJWGzhx86zrHnvjOL8jRc7IMtv7mu1AVYMHwyudw=',
                'https://media.istockphoto.com/id/1190616551/vector/head-of-a-little-asian-boy-in-profile-the-face-of-a-child-on-the-side-portrait-avatar.jpg?s=170667a&w=0&k=20&c=g24hXtlRXkXPCEGEtWijmxSV1Xu3TbPWY6oTRLNGTEI='
                ],
        'pL1' : 'https://media.istockphoto.com/id/1188460614/vector/portrait-of-a-young-beautiful-asian-fashion-woman-vector-flat-illustration-asian-cute-girl.jpg?s=612x612&w=0&k=20&c=1oOJoBKyyhS_VjqRGHoZ1p-zyfmnpAI7TYM_9y5DqzM=',
        'pL2' : 'https://media.istockphoto.com/id/1193146236/vector/portrait-of-a-businessman-avatar-of-a-young-man-for-social-network.jpg?s=170667a&w=0&k=20&c=tzuR2fBVV1ThyKl3p-8DRPDj1yD4ttC5_myLku6CAT8=',
        'pL3' : 'https://media.istockphoto.com/id/1190616457/vector/head-of-a-little-asian-girl-in-profile-the-face-of-a-child-on-the-side-portrait-avatar.jpg?s=612x612&w=0&k=20&c=P2MQJWGzhx86zrHnvjOL8jRc7IMtv7mu1AVYMHwyudw=',
        'pL4' : 'https://media.istockphoto.com/id/1190616551/vector/head-of-a-little-asian-boy-in-profile-the-face-of-a-child-on-the-side-portrait-avatar.jpg?s=170667a&w=0&k=20&c=g24hXtlRXkXPCEGEtWijmxSV1Xu3TbPWY6oTRLNGTEI='
    }
    return render(request, 'profiles.html',profileLinks)

def bsLearning(request):
    # return HttpResponse("<center><h1>Bootstrap Learning 📚 </h1></center>")
    return render(request, 'bootstrapComp.html')

def LearningDTL(request):
    # return HttpResponse("<center><h1>Bootstrap Learning 📚 </h1></center>")
    return render(request, 'learningDTL.html')

def add(request):

    n1 = request.POST['num1']
    n2 = request.POST['num2']

    res = int(n1) + int(n2)
    # return HttpResponse("<center><h1>Bootstrap Learning 📚 </h1></center>")
    return render(request, 'add.html', {'sum': res})
```

## 4. Add static dir in `settings.py` of project
Create static folder and add path
![image](https://user-images.githubusercontent.com/80549753/216835958-127cb89f-1019-44bd-9aec-0ed31c2d2501.png)
```python
STATICFILES_DIRS = [
    BASE_DIR / "static",
    # '/var/www/static/',
]
```

## 5. Add Templet's dir in `settings.py` of project
Create template folder and add path
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / "template",],  # Added manually the path of the template folder
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```


## x.To change the admin text
Past this in your urls.py to Change the view
```python
admin.site.site_header = "Carton 🚃 Network Admin"
admin.site.site_title = "Carton 🚃 Network Admin Portal"
admin.site.index_title = "Welcome to Carton 🚃 Network Researcher Portal"
```

## 🎋 Tamplet inheritance
```html
{% block title %}
{% endblock title %}

{% block body %}
{% endblock body %}
```
```html
{% extends 'base.html' %}

{% block title %} Website {% endblock title %}

{% block body %}
    This is body
{% endblock body %}
```



## 6. Data Base
For Admin settings
```bash
python3 manage.py makemigrations # To track changes ( changes in schema)
python3 manage.py migrate # (django used some default tables for authentications
```
```bash
python3 manage.py createsuperuser
```
![image](https://user-images.githubusercontent.com/80549753/217037738-c50bb329-7d60-4303-acdf-14913b6b2450.png)
![image](https://user-images.githubusercontent.com/80549753/217038013-def5a3a5-5c20-4e1f-8548-bdedc51900ef.png)


django install & vertualenv [`Link`](https://www.digitalocean.com/community/tutorials/how-to-install-the-django-web-framework-on-ubuntu-22-04)

## Forms Request
```html
{% extends 'base.html' %}

{% block title %}Contact{% endblock title %}

{% block content %}
<div class="container-fluid px-0 mb-3" >
    <img src="https://source.unsplash.com/1000x180/?phone,contact" class="d-block w-100 mx-0" alt="...">
</div>
<div class="container mb-3 py-4">
    <h1 class="text-center">Contact Us</h1>
    <form method="post" action="/contact">
    {% csrf_token %}
        <div class="form-group">
            <label for="name">Name</label>
            <input type="text" class="form-control" id="name" name="name" placeholder="Enter your Name">
        </div>

        <div class="form-group">
            <label for="email">Email address</label>
            <input type="email" class="form-control" id="email" name="email" placeholder="Enter Your Email">
        </div>

        <div class="form-group">
            <label for="phone">Phone Number</label>
            <input type="phone" class="form-control" id="phone" name="phone" placeholder="Enter Your Phone Number">
        </div>

        <div class="form-group">
            <label for="desc">Tell me about what you want to contact me for...</label>
            <textarea class="form-control" id="desc" rows="3" name="desc"></textarea>
        </div>
        <button class="btn btn-primary" type="submit">Submit</button>
    </form>

</div>
{% endblock content %}
```

```python
def add(request):

    n1 = request.POST['num1']
    n2 = request.POST['num2']

    res = int(n1) + int(n2)
    # return HttpResponse("<center><h1>Bootstrap Learning 📚 </h1></center>")
    return render(request, 'add.html', {'sum': res})
```

model.py
[docs](https://docs.djangoproject.com/en/4.2/ref/models/fields/)
```python
from django.db import models

# Create your models here.
class Contact(models.Model):
    name = models.CharField(max_length=122)
    email = models.CharField(max_length=122)
    phone = models.CharField(max_length=12)
    desc = models.TextField()
    date = models.DateField()

    def __str__(self):
        return self.name
```

1. First register the model in admin.py
2. app register in settings
3. Now to save changes and make table in db migrate

```bash
python3 manage.py makemigrations
```
> `makemigrations` - create changes and store in a file

> `migrate` - apply the pending changes created by makemigrations


![image](https://user-images.githubusercontent.com/80549753/220147028-ea765abf-bdae-4487-aa13-96d440ea1f93.png)

Need to make changes

```python
from django.contrib import admin

# Register your models here.

from home.models import Contact # This is the line that imports the Contact model from home/models.py
admin.site.register(Contact) # This is the line that registers the Contact model with the admin site
```
[Video to understand some connection ...](https://youtu.be/JxzZxdht-XY?t=6960)
Add app's Config settings.INSTALLED_APPS
![image](https://user-images.githubusercontent.com/80549753/220149116-8d26eff7-6058-49dd-81aa-784636a10ae8.png)


![image](https://user-images.githubusercontent.com/80549753/220148898-697e1ad9-ef82-4a52-8e70-5ab1064e9fd9.png)
![image](https://user-images.githubusercontent.com/80549753/220150437-68e27fed-ac85-452e-8caa-6b4e85adb782.png)
```python
python3 manage.py migrate
```
![image](https://user-images.githubusercontent.com/80549753/220150739-2d95dcf3-3810-4eed-8c21-951aa6e9b2ed.png)
![image](https://user-images.githubusercontent.com/80549753/220151203-0159c9cf-707c-4b67-90d3-701fdd6df942.png)
Sucessfully added

## Making queries in Django [`link`](https://docs.djangoproject.com/en/4.1/topics/db/queries/)
```
Contact.objects.all()
Contact.objects.all()[0]
Contact.objects.all()[0].name
Contact.objects.filter(name="AYON KARMAKAR")
```
![image](https://user-images.githubusercontent.com/80549753/224615431-0ad81b1d-1948-4d7c-be41-6247945e9a45.png)
![image](https://user-images.githubusercontent.com/80549753/224615773-3502dc09-366e-47b8-a29d-3d7d27d768f9.png)
![image](https://user-images.githubusercontent.com/80549753/224616022-84f100e4-7570-4fcd-9008-3f8749b5361a.png)


# connect Django with a PostgreSQL database
Change in settings.py
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'mydatabase',
        'USER': 'myuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```
# [Templates](https://docs.djangoproject.com/en/4.2/ref/templates/)
# for loop's and conditions. 
[Doc Link](https://docs.djangoproject.com/en/4.2/ref/templates/builtins/)
![image](https://github.com/Ayon-SSP/Learning_Django/assets/80549753/e5ff796d-846e-4307-867d-e9ca5304dd2f)
![image](https://github.com/Ayon-SSP/Learning_Django/assets/80549753/87d16ab9-9864-4147-b499-b5998a8eac6f)
# postgrase connection
![image](https://github.com/Ayon-SSP/Learning_Django/assets/80549753/bb64d825-a585-4994-bcf8-5ea0a5219f8e)

 # To flush all the data
 ```bash
 python3 manage.py flush
 ```
# Shell
![image](https://github.com/Ayon-SSP/Learning_Django/assets/80549753/d6d2d8f6-cb03-41ea-8b9e-3809c6823101)


# Django default auth [Link](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/) || [AuthFeatures](https://docs.djangoproject.com/en/4.0/topics/auth/default/#module-django.contrib.auth.views)
