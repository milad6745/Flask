## Example

```python

from flask import Flask, redirect, url_for

# ساخت یک نمونه از کلاس Flask با نام اپلیکیشن app
app = Flask(__name__)

# تعریف یک مسیر برای صفحه اصلی ('/')
@app.route('/')
def index():
    # این تابع پاسخ متن 'Welcome to my website!' را بر می‌گرداند
    return 'Welcome to my website!'

# تعریف یک مسیر با نام کاربری به عنوان یک پارامتر داینامیک ('/user/<username>')
@app.route('/user/<username>')
def get_user(username):
    # اگر نام کاربری 'admin' باشد، کاربر به مسیر '/admin/' هدایت می‌شود
    if username == "admin":
        return redirect(url_for('admin'))
    # در غیر این صورت تا زمانی که مقداری برگردانده نشده است، مرورگر ممکن است منتظر بماند

# تعریف یک مسیر برای صفحه مدیریت ('/admin/')
@app.route('/admin/')
def admin():
    # این تابع پاسخ متن 'hello admin' را بر می‌گرداند
    return 'hello admin'

# اجرای اپلیکیشن در حالت دیباگ با درگاه ۶۰۶۰
if __name__ == '__main__':
    app.run(debug=True, port=6060)


```
