# sqlalchemy

SQLAlchemy یک کتابخانه‌ی پایتون است که برای کار با پایگاه داده‌های رابطه‌ای (مانند MySQL، PostgreSQL، SQLite و غیره) در پروژه‌های پایتون استفاده می‌شود. این کتابخانه امکاناتی مفید برای تعامل با پایگاه داده‌ها فراهم می‌کند و به شما این امکان را می‌دهد تا به راحتی مدل‌های داده‌ای خود را تعریف کرده و از آن‌ها در پروژه‌های خود استفاده کنید.

برای استفاده از SQLAlchemy در یک پروژه Flask، ابتدا باید این کتابخانه را نصب کنید. برای نصب آن می‌توانید از دستورات زیر استفاده کنید:

```
pip install Flask-SQLAlchemy
```

حالا بیایید یک مثال ساده از استفاده از SQLAlchemy در Flask ببینیم:

1. **استفاده در Flask**:

   بعد از نصب Flask-SQLAlchemy، می‌توانید آن را در پروژه Flask خود فراخوانی کنید. در ابتدا، باید اپلیکیشن Flask را ایجاد کنید و سپس تنظیمات مربوط به پایگاه داده را انجام دهید.

   ```python
   from flask import Flask
   from flask_sqlalchemy import SQLAlchemy

   app = Flask(__name__)
   app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///example.db'  # آدرس پایگاه داده
   db = SQLAlchemy(app)
   ```

2. **تعریف یک مدل**:

   بعد از تنظیمات، می‌توانید مدل‌های داده‌ای خود را تعریف کنید. به عنوان مثال، یک مدل ساده برای نمایش کاربران:

   ```python
   class User(db.Model):
       id = db.Column(db.Integer, primary_key=True)
       username = db.Column(db.String(80), unique=True, nullable=False)
       email = db.Column(db.String(120), unique=True, nullable=False)

       def __repr__(self):
           return f'<User {self.username}>'
   ```

   در این مثال، ما یک مدل به نام `User` تعریف کردیم که شامل سه فیلد (`id`، `username` و `email`) می‌باشد.

3. **استفاده در پروژه**:

   حالا می‌توانید از مدل `User` در پروژه‌ی خود استفاده کنید. مثلاً می‌توانید یک کاربر جدید ایجاد کنید و به پایگاه داده اضافه کنید:

   ```python
   new_user = User(username='john_doe', email='john@example.com')
   db.session.add(new_user)
   db.session.commit()
   ```

   این کد یک کاربر جدید به نام `john_doe` ایجاد کرده و آن را به پایگاه داده اضافه می‌کند.

   



```python
from flask import Flask, request, flash, url_for, redirect, render_template
# صدا زدن ماژول
from flask_sqlalchemy import SQLAlchemy

#کانفیگ دیتابیس
app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///students.sqlite3'
app.config['SECRET_KEY'] = "random string"

db = SQLAlchemy(app)
# ایجاد دیتابیس و روابط
class students(db.Model):
   id = db.Column('student_id', db.Integer, primary_key = True)
   name = db.Column(db.String(100))
   city = db.Column(db.String(50))
   addr = db.Column(db.String(200)) 
   pin = db.Column(db.String(10))

# تعریف روابط دیتابیس در پایتون
def __init__(self, name, city, addr,pin):
   self.name = name
   self.city = city
   self.addr = addr
   self.pin = pin
```
