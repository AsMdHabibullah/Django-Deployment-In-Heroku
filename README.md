
# Deploy Django Project in Heroku Live Server Step by Step.


```
Steo 01.
```
01. First you need to download & setup python environment variable in your machine for python & django programming.
02. Install git in your machin
03. Setup git in your machin
04. Goto Django project main directory
05. Write -> git init
06. Test git -> git status
07. Write -> git add . / git add -A
08. Write -> git commit -m "Your massage here"
```

Step 02.
```
09. Create a Heroku account
10. Install heroku Cli in your machin -> sudo snap install heroku --classic / sudo snap install --classic heroku
11. heroku --version
12. heroku login
13. heroku create personalprotfolio (your-project-name or any name)
14. heroku open
```

Step 03.
```
15. pip install whitenoise
16. pip install django_heroku
```
Step 04
```
17. Open your settings.py file

BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

STATIC_URL = '/static/'

STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'static'),
)

In MIDDLEWARE just past 'whitenoise.middleware.WhiteNoiseMiddleware',

Top of the settings file just import "import django_heroku" And Bottom of Settings file just pest "django_heroku.settings(locals())"

STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
```

Step 05.
```
18. python manage.py collectstatic --noinput
19. heroku config:set DEBUG_COLLECTSTATIC=1 or heroku config:set DISABLE_COLLECTSTATIC=1
20. git push heroku master
21. heroku poen 
```
Now you see an Error -> like-> heroku logs --tail
```
22. Install gunicorn -> pip install gunicorn
23. Now you need to create a requirements.txt & Procfile in your manin project directory.
24. In Procfile write like this -> web: gunicorn backapp.wsgi --log-file -
25. write -> pip freeze > requirements.txt
26. git push heroku master
27. Now you see remote: Verifying deploy... done.
```
But
You need to create database table, otherwaise you see an Server 500 Error.
So..........
```
28. heroku run python manage.py migrate
29. heroku run bash
Now you can  see like this ->  ~ $ 

    You need to create superuser
30. python manage.py createsuperuser
31. Your User Name
32. Email
33. Password
34. Confirm Password

```
# Done..:) Hurrah Your App in live now. You can see just writ command - > heroku poen
```
