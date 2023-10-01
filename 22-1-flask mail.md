Flask-Mail یک افزونه برای فریمورک Flask است که ارسال ایمیل‌ها را در برنامه‌های وب Flask ساده‌تر می‌کند. با استفاده از Flask-Mail، شما می‌توانید ایمیل‌های خود را ارسال کنید و دریافت کنید.

**چگونگی استفاده از Flask-Mail**:

1. **نصب Flask-Mail**:

   ابتدا باید این افزونه را نصب کنید:

   ```bash
   pip install Flask-Mail
   ```

2. **استفاده در برنامه Flask**:

   برای استفاده از Flask-Mail، باید این افزونه را به برنامه Flask خود اضافه کنید.

   ```python
   from flask import Flask
   from flask_mail import Mail, Message
   ```

   سپس نیاز است تنظیمات مربوط به ارسال ایمیل‌ها را در برنامه خود تنظیم کنید:

   ```python
   app.config['MAIL_SERVER'] = 'smtp.example.com'
   app.config['MAIL_PORT'] = 587
   app.config['MAIL_USERNAME'] = 'youremail@example.com'
   app.config['MAIL_PASSWORD'] = 'yourpassword'
   app.config['MAIL_USE_TLS'] = True
   app.config['MAIL_USE_SSL'] = False

   mail = Mail(app)
   ```

   در این مثال، تنظیمات مربوط به سرور SMTP، پورت و اطلاعات احراز هویت ایمیل شما تعیین می‌شوند. همچنین با ایجاد یک نمونه از کلاس `Mail`، می‌توانید از قابلیت‌های Flask-Mail استفاده کنید.

3. **ارسال ایمیل**:

   حالا می‌توانید ایمیل‌ها را ارسال کنید. برای این کار، یک شیء از کلاس `Message` ایجاد کنید و آن را به روش `send` ارسال کنید:

   ```python
   msg = Message('موضوع ایمیل', sender='youremail@example.com', recipients=['recipient@example.com'])
   msg.body = 'این یک پیام تست از Flask-Mail است.'
   mail.send(msg)
   ```

   در این مثال، یک پیام با موضوع، فرستنده و گیرنده مشخص شده ارسال می‌شود.

این یک مثال ساده از استفاده از Flask-Mail است. با استفاده از این افزونه، شما می‌توانید ایمیل‌ها را در برنامه‌های Flask به سادگی ارسال کنید.


```Example
from flask import Flask
from flask_mail import Mail, Message

app =Flask(__name__)
mail=Mail(app)

app.config['MAIL_SERVER']='smtp.gmail.com'
app.config['MAIL_PORT'] = 465
app.config['MAIL_USERNAME'] = 'yourId@gmail.com'
app.config['MAIL_PASSWORD'] = '*****'
app.config['MAIL_USE_TLS'] = False
app.config['MAIL_USE_SSL'] = True
mail = Mail(app)

@app.route("/")
def index():
   msg = Message('Hello', sender = 'yourId@gmail.com', recipients = ['id1@gmail.com'])
   msg.body = "Hello Flask message sent from Flask-Mail"
   mail.send(msg)
   return "Sent"

if __name__ == '__main__':
   app.run(debug = True)
```
