# Django arc
![image](https://user-images.githubusercontent.com/80549753/216788425-5a41fac7-51f1-484b-b8a4-ce5236216c3b.png)
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


Past this in your urls.py to Change the view
```python
admin.site.site_header = "Carton 🚃 Network Admin"
admin.site.site_title = "Carton 🚃 Network Admin Portal"
admin.site.index_title = "Welcome to Carton 🚃 Network Researcher Portal"
```
