# Django arc
![image](https://user-images.githubusercontent.com/80549753/216788425-5a41fac7-51f1-484b-b8a4-ce5236216c3b.png)
![image](https://user-images.githubusercontent.com/80549753/219374285-47f633c2-0d68-4612-ae47-cbe302cad1dd.png)

```bash
django-admin startproject my_project # create project
cd my_project/
python3 manage.py startapp home # create app
python3 manage.py runserver # run server
```

For Admin settings
```bash
python3 manage.py makemigrations
python3 manage.py migrate
```

```bash
python3 manage.py createsuperuser
```
![image](https://user-images.githubusercontent.com/80549753/217037738-c50bb329-7d60-4303-acdf-14913b6b2450.png)
![image](https://user-images.githubusercontent.com/80549753/217038013-def5a3a5-5c20-4e1f-8548-bdedc51900ef.png)


django install & vertualenv [`Link`](https://www.digitalocean.com/community/tutorials/how-to-install-the-django-web-framework-on-ubuntu-22-04)

static
![image](https://user-images.githubusercontent.com/80549753/216835958-127cb89f-1019-44bd-9aec-0ed31c2d2501.png)


Add static dir in settings.py of project
```python
STATICFILES_DIRS = [
    BASE_DIR / "static",
    # '/var/www/static/',
]
```

Past this in your urls.py to Change the view
```python
admin.site.site_header = "Carton 🚃 Network Admin"
admin.site.site_title = "Carton 🚃 Network Admin Portal"
admin.site.index_title = "Welcome to Carton 🚃 Network Researcher Portal"
```



Forms Request
```python
def add(request):

    n1 = request.POST['num1']
    n2 = request.POST['num2']

    res = int(n1) + int(n2)
    # return HttpResponse("<center><h1>Bootstrap Learning 📚 </h1></center>")
    return render(request, 'add.html', {'sum': res})
```

model.py
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
