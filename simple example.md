
** 2. ساخت یک برنامه ساده:**
حال می‌توانید یک برنامه ساده با Flask ایجاد کنید. ایجاد یک پرونده با نام `app.py` و محتوای زیر را در آن قرار دهید:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run()
```

این برنامه یک وب سرور ایجاد می‌کند که به درخواست‌های ریشه (`/`) پاسخ می‌دهد و متن "Hello, World!" را به عنوان پاسخ برمی‌گرداند.

**3. اجرای برنامه:**
برای اجرای برنامه، به ترمینال بروید و دستور زیر را در مسیر پرونده `app.py` وارد کنید:

```bash
python app.py
```

این دستور وب سرور Flask را راه‌اندازی می‌کند و شما بر می‌توانید از مرورگر خود به آدرس `http://127.0.0.1:5000/` بروید تا پیام "Hello, World!" را مشاهده کنید.

**4. ایجاد روت‌های دلخواه:**
شما می‌توانید روت‌های دلخواه برای برنامه خود ایجاد کنید. به عنوان مثال، برای ایجاد یک روت با مسیر `/about` که پیام "صفحه درباره‌ما" را نمایش دهد، می‌توانید به روش زیر عمل کنید:

```python
@app.route('/about')
def about():
    return 'صفحه درباره‌ما'
```

حالا با مراجعه به `http://127.0.0.1:5000/about` در مرورگر خود، متن "صفحه درباره‌ما" را مشاهده خواهید کرد.

این مقدمه به شما کمک می‌کند تا با مفاهیم ابتدایی Flask آشنا شوید. از اینجا به بعد می‌توانید با مطالعه مستندات رسمی Flask و آزمایش‌های بیشتر، توانایی‌های پیشرفته‌تری را از این فریم‌ورک یاد بگیرید.