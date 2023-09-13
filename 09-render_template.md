# rendet template

 در فریمورک وب فلاسک (Flask) یک تابع است که برای رندر کردن صفحات HTML و نمایش آنها به کاربران استفاده می‌شود. این تابع از بسته `flask` در پایتون قابل استفاده است.

از `render_template` برای ایجاد و بازگرداندن صفحات HTML استفاده می‌شود. این تابع بر اساس قالب‌های HTML که شما ایجاد کرده‌اید وجود دارد و داده‌هایی که می‌خواهید در صفحه نمایش داده شود را دریافت می‌کند. سپس این تابع این داده‌ها را به قالب HTML شما منتقل می‌کند و صفحه HTML را با داده‌های جدید به شکل نهایی رندر می‌کند.

این مثال ساده نشان می‌دهد چگونه `render_template` در Flask استفاده می‌شود:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    return 'Welcome to my website!'

@app.route('/login')
def login():
    return render_template('login.html')
 


@app.route('/succ')
def succ():
    return 'succeccfully login'

if __name__ == '__main__':
    app.run(debug=True,port=6060)
```
```text
مسیر کپی کردن فایل html
project_directory/
    app.py
    templates/
        login.html
```
