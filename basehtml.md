# base.hml
در فریم‌ورک Flask، بهترین راه برای نمایش یک Navbar در تمام صفحات، استفاده از بیسیک لی‌آوت (Base Layout) است. این به شما امکان می‌دهد تا الگویی مشترک را در تمام صفحات استفاده کنید.

اینجا یک نمونه‌ای از چگونگی ایجاد بیسیک لی‌آوت در فلاسک را مشاهده می‌کنید:

**ایجاد بیسیک لی‌آوت**:

   در پوشه‌ی `templates` شما، یک فایل به نام `base.html` ایجاد کنید و در آن Navbar و ساختار اصلی صفحات خود را قرار دهید.

   به عنوان مثال، فایل `base.html` می‌تواند به این صورت باشد:
- base.html
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>عنوان صفحه</title>
       <!-- اینجا می‌توانید لینک‌های مورد نیاز مانند Bootstrap را قرار دهید -->
   </head>
   <body>

   <!-- Navbar -->
   <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
       <a class="navbar-brand" href="#">نام سایت شما</a>
       <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
           <span class="navbar-toggler-icon"></span>
       </button>
       <div class="collapse navbar-collapse" id="navbarNav">
           <ul class="navbar-nav ml-auto">
               <li class="nav-item active">
                   <a class="nav-link" href="#">خانه <span class="sr-only">(current)</span></a>
               </li>
               <li class="nav-item">
                   <a class="nav-link" href="#">صفحه اصلی</a>
               </li>
               <li class="nav-item">
                   <a class="nav-link" href="#">درباره ما</a>
               </li>
               <li class="nav-item">
                   <a class="nav-link" href="#">تماس با ما</a>
               </li>
           </ul>
       </div>
   </nav>

   <!-- محتوای اصلی صفحه -->
   - about.html
   {% block content %}{% endblock %}
<p> About us </p>
   </body>
   </html>
   ```
```python
from flask import Flask, render_template, request
app = Flask(__name__)



@app.route('/',methods = ['POST', 'GET'])
def index():
    return render_template("index.html")

@app.route('/home',methods = ['POST', 'GET'])
def home():
    return render_template("home.html")

@app.route('/about')
def about():
    return render_template("about.html")


if __name__ == '__main__':
   app.run(debug = True)
```


**استفاده در صفحات دیگر**:

   حالا می‌توانید این بیسیک لی‌آوت را در صفحات دیگر خود استفاده کنید. برای این کار، از `{% extends 'base.html' %}` در ابتدای فایل و از `{% block content %}{% endblock %}` برای جایگزین کردن محتوای اصلی استفاده کنید.

   به عنوان مثال:

   ```html
   {% extends 'base.html' %}

   {% block content %}
   <!-- محتوای اصلی صفحه -->
   <h1>صفحه اصلی</h1>
   <!-- ادامه محتوا -->
   {% endblock %}
   ```

با این کار، هر صفحه‌ی جدیدی که از بیسیک لی‌آوت استفاده می‌کند، Navbar شما را خواهد داشت.
