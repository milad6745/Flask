
```python
from flask import Flask, redirect, url_for
app = Flask(__name__)

@app.route('/admin')
def hello_admin():
   return 'Hello Admin'

@app.route('/guest/<guest>')
def hello_guest(guest):
   return 'Hello %s as Guest' % guest

@app.route('/user/<name>')
def hello_user(name):
   if name =='admin':
      return redirect(url_for('hello_admin'))
   else:
      return redirect(url_for('hello_guest',guest = name))

if __name__ == '__main__':
   app.run(debug = True)
```


1. `from flask import Flask, redirect, url_for`: در این خط، ما از ماژول‌های Flask مربوط به فریمورک Flask و توابع `redirect` و `url_for` استفاده می‌کنیم.

2. `app = Flask(__name__)`: در این خط، یک نمونه از کلاس Flask ایجاد می‌شود. `__name__` نشانگر نام ماژول فعلی است.

3. `@app.route('/admin')`: این خط کد یک دکوراتور است که متد `hello_admin` را به URL `/admin` ارتباط می‌دهد.

   - در این متد، "Hello Admin" برگشت داده می‌شود.

4. `@app.route('/guest/<guest>')`: این خط کد یک دکوراتور است که متد `hello_guest` را به یک URL با یک متغیر متغیری به نام `guest` ارتباط می‌دهد.

   - در این متد، مقدار متغیر `guest` به عنوان مهمان دریافت شده و در پیام خوش‌آمدگویی استفاده می‌شود.

5. `@app.route('/user/<name>')`: این خط کد یک دکوراتور است که متد `hello_user` را به یک URL با یک متغیر به نام `name` ارتباط می‌دهد.

   - در این متد، اگر `name` برابر با "admin" باشد، کاربر به `hello_admin` هدایت می‌شود و در غیر این صورت به `hello_guest` با مهمانی با نام `name` هدایت می‌شود.

6. `if __name__ == '__main__':`: این بخش کد بررسی می‌کند که آیا این فایل به عنوان یک فایل اجرایی اجرا شده است یا به عنوان یک ماژول وارد شده است.

   - اگر به عنوان فایل اجرایی اجرا شده باشد، برنامه Flask را با وضعیت debug فعال اجرا می‌کند.

این برنامه یک وب‌اپلیکیشن ساده ایجاد می‌کند که به وابستگی از آدرس درخواست‌ها، پاسخ مناسب را برمی‌گرداند. برای مثال، اگر شما به `http://localhost:5000/user/john` مراجعه کنید، برنامه پاسخ `Hello john as Guest` را خواهد داد.
