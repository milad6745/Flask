
# Cookie
 در Flask، می‌توانید از ماژول `Flask` و `make_response` برای کار با کوکی‌ها استفاده کنید. در زیر یک مثال ساده از چگونگی استفاده از کوکی در Flask آمده است:



# Example
```python
from flask import Flask, render_template, request, make_response

app = Flask(__name__)

@app.route('/')
def index():
    username = request.cookies.get('username')
    if username:
        return f"سلام {username}! شما وارد شده‌اید."
    else:
        return render_template('login.html')

@app.route('/login', methods=['POST'])
def login():
    username = request.form.get('username')
    
    if username:
        resp = make_response(f"ورود شما با موفقیت ثبت شد. سلام {username}!")
        resp.set_cookie('username', username)
        return resp
    else:
        return "لطفا نام کاربری خود را وارد کنید."

if __name__ == '__main__':
    app.run(debug=True)
```

```html
<!doctype html>
<html>
    <head>
        <title>ورود</title>
    </head>
    <body>
        <h2>لطفا وارد شوید</h2>
        <form action="/login" method="post">
            <input type="text" name="username" placeholder="نام کاربری">
            <input type="submit" value="ورود">
        </form>
    </body>
</html>
```
بطور کلی، این کد یک برنامه Flask ایجاد می‌کند که از کاربر نام کاربری دریافت می‌کند، آن را در یک کوکی ذخیره می‌کند و اگر کاربر قبلاً وارد شده باشد، نام کاربری را از کوکی بازیابی می‌کند. حالا دستورات خط به خط را توضیح می‌دهم:

`from flask import Flask, render_template, request, make_response`:

در اینجا ما ماژول‌هایی که برای اجرای این برنامه Flask لازم هستند را وارد می‌کنیم. این ماژول‌ها شامل `Flask` برای ایجاد برنامه Flask، `render_template` برای نمایش قالب‌های HTML، `request` برای دسترسی به اطلاعات درخواست HTTP و `make_response` برای ایجاد یک پاسخ سفارشی هستند.

`app = Flask(__name__)`:

در اینجا یک نمونه از کلاس `Flask` ایجاد می‌شود و به متغیر `app` اختصاص داده می‌شود. این نمونه به عنوان اصلی‌ترین قسمت برنامه Flask عمل می‌کند.

`@app.route('/')`: 

این دکوراتور مسیر اصلی وب‌سایت را تعریف می‌کند که از آدرس `/` شروع می‌شود. هنگامی که کاربر به این مسیر دسترسی پیدا می‌کند، تابع `index()` اجرا می‌شود.

`def index():`: 

این تابع به عنوان مدیریت کننده مسیر اصلی عمل می‌کند. ابتدا چک می‌شود که آیا کوکی با نام "username" وجود دارد یا نه. اگر وجود داشته باشد، نام کاربری از کوکی می‌خواند و نمایش می‌دهد وگرنه از کاربر درخواست می‌کند که نام کاربری خود را وارد کند.

`@app.route('/login', methods=['POST'])`: 

این دکوراتور مسیر "/login" را تعریف می‌کند و تنها از متد POST پشتیبانی می‌کند. این مسیر برای دریافت نام کاربری از فرم استفاده می‌شود.

`def login():`: 

این تابع به عنوان مدیریت کننده مسیر "/login" عمل می‌کند. نام کاربری از فرم POST دریافت می‌شود. اگر کاربر نام کاربری وارد کند، یک پاسخ ساخته شده و با پیام خوش آمدگویی و نام کاربری تنظیم می‌شود و به عنوان کوکی به کاربر داده می‌شود.

`if __name__ == '__main__':`: 

این شرط بررسی می‌کند که برنامه به عنوان اصلی اجرا شده باشد و نه به عنوان یک ماژول در داخل یک برنامه دیگر. اگر برنامه به عنوان اصلی اجرا شود، دستور `app.run(debug=True)` فراخوانی می‌شود تا وب‌سرور Flask روشن شود.

با این کد، شما می‌توانید یک برنامه Flask ایجاد کنید که نام کاربری را از کاربر دریافت کرده و در کوکی ذخیره کند، و در صورت ورود مجدد کاربر، نام کاربری را از کوکی بازیابی کند.
