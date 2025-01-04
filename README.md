# نصب و راه‌اندازی پروژه
```sh
pip install django                   # نصب جنگو
django-admin startproject myProj .   # ایجاد پروژه جنگو
python manage.py runserver           # اجرای سرور توسعه
```
## ایجاد اپلیکیشن‌ها
```sh
python manage.py startapp posts      # ایجاد اپلیکیشن posts
python manage.py startapp profiles   # ایجاد اپلیکیشن profiles
```
## تنظیم مسیرها (URLs)
### در فایل urls.py اضافه کنید:
```sh
from posts.views import index, home
urlpatterns = [ path('index/', index), path('home/', home) ]
```
## تعریف ویوها (Views)
## در فایل views.py اضافه کنید:
```sh
def index(request): return HttpResponse("Hi Django")
def home(request): return HttpResponse("<h1> Django Course<h1>")
```
## مدل‌ها (Models)
### در فایل models.py اضافه کنید:
```sh
title = models.CharField(max_length=50)           # فیلد متنی با حداکثر 50 کاراکتر
text = models.TextField(blank=True)               # فیلد متنی قابل خالی بودن
is_enabled = models.BooleanField(default=True)    # مقدار پیش‌فرض True
publish_date = models.DateField(null=True, blank=True) # تاریخ انتشار
created_time = models.DateTimeField(auto_now_add=True) # تاریخ ایجاد خودکار
updated_time = models.DateTimeField(auto_now=True)     # تاریخ تغییر خودکار
```
## اضافه کردن اپلیکیشن به تنظیمات
## در settings.py اضافه کنید:
```sh
INSTALLED_APPS = ['posts']
```
## تنظیم پنل ادمین
### در admin.py اضافه کنید:
```sh
admin.site.register(Post, PostAdmin)
admin.site.register(Comment, CommentAdmin)
```
## مدیریت پایگاه داده
```sh
python manage.py makemigrations      # ایجاد فایل‌های مهاجرت
python manage.py migrate             # اعمال مهاجرت‌ها
python manage.py showmigrations      # نمایش وضعیت مهاجرت‌ها
```
## ایجاد کاربر مدیر
```sh
python manage.py createsuperuser     # ایجاد کاربر ادمین
```
## کار با مدل‌ها در شل جنگو
```sh
python manage.py shell               # ورود به محیط شل
```
## از داخل شل اجرا کنید:
```sh
from posts.models import Post
Post.objects.create(title="hi django")
Post.objects.all()
```