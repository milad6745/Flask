# Data To Template
 
 به شما یاد می‌دهد چگونه از فریمورک وب Flask در زبان پایتون برای ارسال داده‌های فرم از یک صفحه وب به یک قالب HTML استفاده کنید.

مراحل اصلی آموزش عبارتند از:

**ایجاد یک فرم HTML**: در این مرحله، شما یک فرم HTML می‌سازید که شامل مواردی مانند ورودی‌ها (input fields) و دکمه ارسال (submit button) است. این فرم به کمک تگ‌های HTML ساخته می‌شود.

**ارسال داده‌های فرم به Flask**: وقتی کاربر فرم را پر کرده و دکمه ارسال را فشار می‌دهد، اطلاعات فرم به سرور Flask ارسال می‌شود.

**دریافت داده‌ها در Flask**: با استفاده از Flask، شما می‌توانید داده‌های فرم را از درخواست HTTP دریافت کرده و آن‌ها را بررسی کنید.

**انتقال داده‌ها به یک قالب HTML**: در این مرحله، داده‌های دریافت شده از فرم در Flask به یک قالب HTML منتقل می‌شوند تا بتوانند در صفحه وب نمایش داده شوند.

**نمایش داده‌ها در صفحه وب**: در این مرحله، داده‌های دریافت شده از فرم در Flask در قالب HTML نمایش داده می‌شوند و کاربران می‌توانند آن‌ها را ببینند.

با استفاده از این مراحل، شما می‌توانید داده‌هایی که کاربران در یک فرم وارد می‌کنند را ارسال کرده و در Flask پردازش کنید و سپس نتیجه را در یک صفحه وب به کاربران نمایش دهید.



# Example

```python
from flask import Flask, render_template, request
app = Flask(__name__)

@app.route('/')
def student():
   return render_template('student.html')

@app.route('/result',methods = ['POST', 'GET'])
def result():
   if request.method == 'POST':
      result = request.form
      return render_template("result.html",result = result)

if __name__ == '__main__':
   app.run(debug = True)
```

student.htm
'''html
<html>
   <body>
      <form action = "http://localhost:5000/result" method = "POST">
         <p>Name <input type = "text" name = "Name" /></p>
         <p>Physics <input type = "text" name = "Physics" /></p>
         <p>Chemistry <input type = "text" name = "chemistry" /></p>
         <p>Maths <input type ="text" name = "Mathematics" /></p>
         <p><input type = "submit" value = "submit" /></p>
      </form>
   </body>
</html>
```

result htm
```html
<!doctype html>
<html>
   <body>
      <table border = 1>
         {% for key, value in result.items() %}
            <tr>
               <th> {{ key }} </th>
               <td> {{ value }} </td>
            </tr>
         {% endfor %}
      </table>
   </body>
</html>
```

این کد یک برنامه Flask ساده را تعریف می‌کند که از دو مسیر استفاده می‌کند. اجزای مهم کد به شرح زیر است:

`from flask import Flask, render_template, request`:
در اینجا از فریمورک Flask، توابع `render_template` برای نمایش قالب‌های HTML و `request` برای دسترسی به اطلاعات فرم استفاده شده است.

`app = Flask(__name__)`:
یک نمونه از کلاس Flask ایجاد شده و به متغیر `app` اختصاص داده می‌شود. این نمونه به عنوان اصلی‌ترین قسمت برنامه Flask عمل می‌کند.

`@app.route('/')`:
این خط کد یک دکوراتور برای مسیر اصلی وب‌سایت ("/") تعریف می‌کند. هنگامی که کاربر به این مسیر دسترسی پیدا می‌کند، تابع `student()` اجرا می‌شود.

`def student():`:
این تابع، که به عنوان مدیریت کننده مسیر اصلی عمل می‌کند، از تابع `render_template` برای نمایش قالب HTML به نام "student.html" استفاده می‌کند.

`@app.route('/result',methods = ['POST', 'GET'])`:
این خط کد نیز یک دکوراتور برای مسیر "/result" تعریف می‌کند. این مسیر برای دریافت داده‌های فرم ارسالی از کاربر برای نمایش نتیجه استفاده می‌شود. این مسیر از متد‌های POST و GET پشتیبانی می‌کند.

`def result():`:
این تابع به عنوان مدیریت کننده مسیر "/result" عمل می‌کند. در صورتی که درخواست از نوع POST باشد، داده‌های فرم از طریق `request.form` دریافت می‌شوند و در متغیر `result` ذخیره می‌شوند. سپس تابع `render_template` برای نمایش قالب HTML به نام "result.html" با استفاده از داده‌های دریافت شده فراخوانی می‌شود.

`if __name__ == '__main__':`:
این شرط بررسی می‌کند که برنامه به عنوان اصلی اجرا شده باشد و نه به عنوان یک ماژول در داخل یک برنامه دیگر. اگر برنامه به عنوان اصلی اجرا شود، دستور `app.run(debug = True)` فراخوانی می‌شود تا وب‌سرور Flask روشن شود.

با این کد، شما می‌توانید یک برنامه Flask ایجاد کنید که دو مسیر دارد: یک مسیر برای نمایش یک فرم و دیگری برای دریافت و نمایش نتایج ارسالی از فرم.
