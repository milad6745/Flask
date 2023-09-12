# Send_file
تابع send_file در فریمورک Flask برای ارسال فایل‌های استاتیک و پویا به مرورگر کاربر استفاده می‌شود. این تابع به شما اجازه می‌دهد فایل‌های مختلفی از جمله تصاویر، ویدئوها، فایل‌های صوتی، فایل‌های متنی و ... را به عنوان پاسخ به درخواست ارسال کنید.

با کمال میل، کد شما را توضیح می‌دهم:

```python
from flask import Flask, redirect, url_for, send_file

app = Flask(__name__)

@app.route('/')
def index():
    return 'Welcome to my website!'
```

1. در این بخش، ابتدا ما کتابخانه‌ها و توابع مورد نیاز را از فریمورک Flask فراخوانی می‌کنیم و یک نمونه از کلاس Flask با نام `app` می‌سازیم.

2. سپس با استفاده از دکوراتور `@app.route('/')`، تابع `index` را به مسیر اصلی (`'/'`) اختصاص می‌دهیم.

3. تابع `index` با بازگرداندن رشته 'Welcome to my website!' به عنوان پاسخ به درخواست مربوطه، پیام خوش‌آمدگویی را به کاربر نمایش می‌دهد.

```python
@app.route('/login')
def login():
    # مسیر فایل HTML مورد نظر را مشخص کنید
    html_file_path = 'login.html'
    # ارسال فایل به عنوان پاسخ
    return send_file(html_file_path, mimetype='text/html')
```

4. در این قسمت، تابع `login` به مسیر `/login` اختصاص می‌یابد. 

5. در تابع `login`، ابتدا مسیر فایل HTML (`'login.html'`) را در `html_file_path` مشخص می‌کنیم.

6. سپس با استفاده از تابع `send_file`، فایل HTML مورد نظر را به عنوان پاسخ به درخواست ارسال می‌کنیم.

```python
@app.route('/succ')
def succ():
    return 'successfully login'
```

7. در این بخش، تابع `succ` به مسیر `/succ` اختصاص می‌یابد.

8. تابع `succ` با بازگرداندن رشته 'successfully login' به عنوان پاسخ به درخواست مربوطه، پیام موفقیت‌آمیز بودن ورود کاربر را نمایش می‌دهد.

```python
if __name__ == '__main__':
    app.run(debug=True,port=6060)
```

9. در نهایت، با استفاده از شرط `if __name__ == '__main__':`، ما اطمینان حاصل می‌کنیم که این اسکریپت به عنوان اسکریپت اصلی اجرا شده است و سپس اپلیکیشن Flask را اجرا می‌کنیم با دیباگ فعال و درگاه 6060.



فایل login.html برای لاگین کردن ، که پس از لاگین به ما پیام موفقیت آمیز بودن میدهد .
```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>
            <form action="http://localhost:6060/succ" method="GET">
            username :</br> <input type="text" name="username"><br/>
            password : </br> <input type="password" name="password"><br/>
            Email: </br><input type="email" name="mail"><br/>
            Are Youre Sure sign in <input type="checkbox"><br/>
            
            <!-- برای اینکه مورد بگذلزیم که کاربر تنها یک گزینه را بتواند انتخاب کند از تایپ رادیو استفاده میکنیم و حتما برای ارتباط موارد باید نام ها را یکی بگزاریم -->
            what's You Gender ? <br>
            male<input type="radio" name="gender" value="male">
            female<input type="radio" name="gender" value="female">
        
            <button type="submit" > Submit</button>
            </form>
    </p>
</body>
</html>
```
