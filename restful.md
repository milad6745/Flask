Flask-RESTful یک افزونه (Extension) برای فریمورک Flask است که توسعه و ایجاد وب‌سرویس‌های RESTful بسیار ساده‌تر می‌کند. RESTful به معنی "نمایش منابع" است و یک مدل طراحی معماری برای وب‌سرویس‌هاست که استانداردهایی برای ارسال و دریافت داده‌ها ارائه می‌دهد.

**چگونگی استفاده از Flask-RESTful**:

1. **نصب Flask-RESTful**:

   ابتدا باید این افزونه را نصب کنید:

   ```bash
   pip install Flask-RESTful
   ```

2. **استفاده در برنامه Flask**:

   برای استفاده از Flask-RESTful، افزونه را به برنامه Flask خود اضافه کنید.

   ```python
   from flask import Flask
   from flask_restful import Api, Resource

   app = Flask(__name__)
   api = Api(app)
   ```

   در این مثال، ما افزونه Flask-RESTful را به برنامه اضافه کرده‌ایم و یک نمونه از کلاس `Api` ایجاد کرده‌ایم.

3. **تعریف منابع**:

   حالا می‌توانید منابع (Resources) خود را تعریف کنید. یک منبع در Flask-RESTful یک کلاس است که از کلاس `Resource` ارث‌بری می‌کند.

   ```python
   class HelloWorld(Resource):
       def get(self):
           return {'hello': 'world'}
   ```

   در این مثال، یک منبع به نام `HelloWorld` ایجاد شده است که یک متد `get` دارد. این متد درخواست GET را پاسخ می‌دهد.

4. **ثبت منبع در API**:

   حالا باید منبع را در API ثبت کنید:

   ```python
   api.add_resource(HelloWorld, '/')
   ```

   این دستور می‌گوید که منبع `HelloWorld` را در آدرس ریشه (`/`) ثبت کن.

5. **اجرا و تست**:

   حالا وب‌اپلیکیشن را اجرا کنید و به آدرس `http://localhost:5000` بروید. شما باید پیامی مشابه `{'hello': 'world'}` ببینید.

این یک مثال بسیار ساده از استفاده از Flask-RESTful است. با این افزونه، شما می‌توانید منابع و وب‌سرویس‌های RESTful خود را بسیار سریع و به شکل مهیا ایجاد کنید.
