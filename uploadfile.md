آپلود فایل در فریمورک Flask به شما امکان می‌دهد تا کاربران به وسیله‌ی وب از طریق یک فرم فایل به سرور شما فایل ارسال کنند. برای این کار، نیاز به استفاده از یک فرم HTML برای بخش آپلود و همچنین کد پایتون در سمت سرور دارید تا فایل‌ها را پردازش کنید.

**مراحل آپلود فایل در Flask**:

1. **ایجاد یک فرم HTML**:

   برای شروع، نیاز به یک فرم HTML دارید که به کاربر اجازه آپلود فایل را بدهد. به عنوان مثال:

   ```html
   <!doctype html>
   <html lang="en">
   <head>
     <meta charset="utf-8">
     <title>آپلود فایل در Flask</title>
   </head>
   <body>
     <h1>آپلود فایل</h1>
     <form action="/upload" method="post" enctype="multipart/form-data">
       <input type="file" name="file">
       <input type="submit" value="آپلود">
     </form>
   </body>
   </html>
   ```

   در این فرم، ما یک فایل انتخابی ایجاد کرده‌ایم که کاربر می‌تواند یک فایل انتخاب کند و سپس آن را ارسال کند.

2. **پردازش فایل در Flask**:

   سپس باید سمت سرور کدی برای پردازش فایل ارسالی بنویسید. به عنوان مثال:

   ```python
   from flask import Flask, request, render_template

   app = Flask(__name__)

   @app.route('/')
   def index():
       return render_template('upload.html')

   @app.route('/upload', methods=['POST'])
   def upload_file():
       uploaded_file = request.files['file']
       if uploaded_file.filename != '':
           uploaded_file.save(uploaded_file.filename)
           return 'فایل با موفقیت آپلود شد.'
       return 'هیچ فایلی انتخاب نشده است.'

   if __name__ == '__main__':
       app.run(debug=True)
   ```

   در این مثال، دو روت اصلی داریم. روت اول (`/`) صفحه فرم آپلود را نشان می‌دهد و روت دوم (`/upload`) فایل آپلود شده را دریافت و ذخیره می‌کند.

   توجه کنید که ما از `enctype="multipart/form-data"` در فرم HTML استفاده کرده‌ایم که این نوع ارسال اطلاعات را برای آپلود فایل فراهم می‌کند.

3. **اجرای وب‌اپلیکیشن**:

   حالا کافی است وب‌اپلیکیشن Flask را اجرا کنید (`python app.py`) و به آدرس `http://localhost:5000` در مرورگر خود بروید. شما باید یک فرم آپلود فایل ببینید که به کاربر اجازه می‌دهد یک فایل را انتخاب کند و ارسال کند.

این یک مثال ساده از آپلود فایل در فریمورک Flask بود. برای پروژه‌های بزرگ‌تر، ممکن است نیاز به افزودن امنیت‌های بیشتر و مدیریت فایل‌های بارگذاری شده باشد.
