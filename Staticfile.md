# فایل‌های استاتیک (Static files)

در فریم‌ورک Flask به فایل‌هایی اطلاق می‌شود که معمولاً شامل تصاویر، فایل‌های CSS، فایل‌های جاوااسکریپت و سایر منابع ثابت هستند که توسط وبسایت شما استفاده می‌شوند. این فایل‌ها توسط مرورگرها بارگیری می‌شوند و به صورت ثابت در مقابل تغییرات کاربران قرار دارند.

در Flask، شما می‌توانید این فایل‌های استاتیک را در دایرکتوری‌های مشخصی قرار دهید. به طور معمول، این فایل‌ها در یک دایرکتوری به نام `static` قرار می‌گیرند که در سطح ریشه پروژه Flask قرار دارد.

برای استفاده از یک فایل استاتیک در یک قالب HTML، می‌توانید از تگ `<link>` برای CSS یا تگ `<script>` برای جاوااسکریپت استفاده کنید و مسیر فایل را به صورت استاتیک در نظر بگیرید. به عنوان مثال:



```python
from flask import Flask, render_template, request, make_response

app = Flask(__name__)

age = 100

@app.route('/')
def index():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

## index.html

```html
<!doctype html>
<html>
    <head>
        <title>ورود</title>
        <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
    </head>
    <body>
     <p>
       Welcome To Our Websites
     </p>
     <script>src='js/hello.js'</script>
    </body>
</html>
```

```js
alert{"سلام این یک هشدار است"}
```

