## Example

```python

from flask import Flask, redirect, url_for


ساخت یک نمونه از کلاس Flask با نام اپلیکیشن app
app = Flask(__name__)

تعریف یک مسیر برای صفحه اصلی ('/')
@app.route('/')
def index():
این تابع پاسخ متن 'Welcome to my website!' را بر می‌گرداند
    return 'Welcome to my website!'

تعریف یک مسیر با نام کاربری به عنوان یک پارامتر داینامیک ('/user/<username>')
@app.route('/user/<username>')
def get_user(username):
اگر نام کاربری 'admin' باشد، کاربر به مسیر '/admin/' هدایت می‌شود
    if username == "admin":
        return redirect(url_for('admin'))
در غیر این صورت تا زمانی که مقداری برگردانده نشده است، مرورگر ممکن است منتظر بماند

تعریف یک مسیر برای صفحه مدیریت ('/admin/')
@app.route('/admin/')
def admin():
این تابع پاسخ متن 'hello admin' را بر می‌گرداند
    return 'hello admin'

اجرای اپلیکیشن در حالت دیباگ با درگاه ۶۰۶۰
if __name__ == '__main__':
    app.run(debug=True, port=6060)


```

 `from flask import Flask, redirect, url_for`:
   
ابتدا ما از Flask و دو تابع `redirect` و `url_for` از فریمورک Flask وارد می‌کنیم.

 `app = Flask(__name__)`:
یک نمونه از کلاس Flask با نام `app` ایجاد می‌کنیم. این نمونه به عنوان اپلیکیشن اصلی برای وبسایت ما عمل می‌کند.

 `@app.route('/')`:
این خط کد به Flask می‌گوید که تابع `index` باید به مسیر '/' پاسخ دهد.

 `def index():`:
تعریف تابع `index` که درخواست‌هایی به مسیر اصلی ('/') را پردازش می‌کند.

 `return 'Welcome to my website!'`:
تابع `index` پیام 'Welcome to my website!' را به عنوان پاسخ به درخواست مربوطه برمی‌گرداند.

 `@app.route('/user/<username>')`
این خط کد به Flask می‌گوید که تابع `get_user` باید به مسیر '/user/<username>' پاسخ دهد، که `<username>` یک پارامتر داینامیک است.

 `def get_user(username):`
تعریف تابع `get_user` که مقدار `username` را از URL دریافت می‌کند.

 `if username == "admin"
در این قسمت، مقدار `username` بررسی می‌شود. اگر برابر با "admin" باشد، کاربر به مسیر '/admin/' هدایت می‌شود.

 `return redirect(url_for('admin'))`
اگر کاربر نام کاربری "admin" داشته باشد، از `redirect` و `url_for` برای هدایت کاربر به مسیر '/admin/' استفاده می‌شود.

 `@app.route('/admin/')`
تعریف تابع `admin` که به مسیر '/admin/' پاسخ می‌دهد.

 `return 'hello admin'
 تابع `admin` پیام 'hello admin' را به عنوان پاسخ به
