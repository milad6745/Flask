در فریمورک Flask می‌توانید از دستورات حلقه‌ای مانند `for` برای تکرار اطلاعات در قالب‌های HTML استفاده کنید. این کار معمولاً برای نمایش لیست‌ها یا مجموعه‌های داده در صفحات وب مفید است.

برای مثال، فرض کنید که یک لیست از نام‌ها داشته باشیم و می‌خواهیم آنها را در یک صفحه HTML نمایش دهیم. در اینجا نمونه‌ای از چگونگی استفاده از حلقه `for` در یک قالب HTML در Flask آمده است:

```html
<!DOCTYPE html>
<html>
<head>
    <title>نمایش نام‌ها</title>
</head>
<body>
    <h1>لیست نام‌ها</h1>
    <ul>
        {% for name in names %}
            <li>hi {{ name }} , How Are You?</li>
        {% endfor %}
    </ul>
</body>
</html>
```

حالا در داخل برنامه Flask خود، می‌توانید این قالب را با استفاده از `render_template` و با ارسال لیست نام‌ها به عنوان داده، نمایش دهید:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def base():
    names=['milad','roham','ali','mohammad']
    return render_template('base.html',names=names)
```
![image](https://github.com/milad6745/Flask/assets/113288076/be189064-69d6-49df-babf-2185a219dad9)


در این مثال، متغیر `names` به عنوان داده‌ای که باید در قالب نمایش داده شود به قالب ارسال می‌شود. در قالب HTML، از حلقه `for` استفاده شده تا هر عنصر از لیست `names` را نمایش دهد.

نتیجه این کد، صفحه‌ای است که نام‌ها را به شکل یک لیست نمایش می‌دهد.
