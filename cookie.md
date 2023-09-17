
# Cookie
 در Flask، می‌توانید از ماژول `Flask` و `make_response` برای کار با کوکی‌ها استفاده کنید. در زیر یک مثال ساده از چگونگی استفاده از کوکی در Flask آمده است:

```python
from flask import Flask, make_response

app = Flask(__name__)

@app.route('/')
def set_cookie():
    # ساخت یک پاسخ
    resp = make_response("کوکی تنظیم شد!")
    
    # تنظیم کوکی
    resp.set_cookie('username', 'john_doe')
    
    return resp

@app.route('/get_cookie')
def get_cookie():
    # دریافت کوکی
    username = request.cookies.get('username')
    
    if username:
        return f"نام کاربری: {username}"
    else:
        return "کوکی پیدا نشد!"

if __name__ == '__main__':
    app.run(debug=True)
```

در این مثال، مسیر `/` تنظیم کننده کوکی است. هنگامی که کاربر به این مسیر دسترسی پیدا می‌کند، یک پاسخ به او ارسال می‌شود که در آن کوکی `username` با مقدار `john_doe` تنظیم می‌شود.

مسیر `/get_cookie` مقدار کوکی `username` را با استفاده از `request.cookies.get('username')` دریافت می‌کند و اگر وجود داشته باشد، نام کاربری را نمایش می‌دهد، در غیر اینصورت پیامی نشان می‌دهد که کوکی یافت نشد.

اگر این برنامه را اجرا کنید و به مسیر `/` دسترسی پیدا کنید، کوکی تنظیم می‌شود. سپس با دسترسی به `/get_cookie`، نام کاربری از کوکی استخراج می‌شود و نمایش داده می‌شود.



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
