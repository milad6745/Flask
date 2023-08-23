در فلاسک، می‌توانید از آدرس‌های پویا با استفاده از "روتینگ دینامیک" یا "URL Variable" استفاده کنید. این قابلیت به شما اجازه می‌دهد تا ورودی‌های مختلفی که به این آدرس‌ها ارسال می‌شوند، به صورت پارامترهای متغیر در تابع‌های مربوط به این آدرس‌ها در برنامه‌ی فلاسکتان ارسال کنید.

برای استفاده از آدرس‌های پویا در فلاسک، می‌توانید از `<variable_type:variable_name>` در روتینگ‌ها استفاده کنید. در اینجا، `variable_type` نوع داده‌ای است که می‌خواهید در این متغیر پویا استفاده کنید و `variable_name` نام متغیری است که شما تعریف می‌کنید. این متغیرها پس از تعریف در تابع مربوطه با استفاده از آرگومان‌ها قابل دسترسی هستند.

در ادامه یک مثال از استفاده از آدرس‌های پویا در فلاسک آورده شده است:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, World!"

@app.route('/user/<username>')
def show_user_profile(username):
    return f"User: {username}"

if __name__ == '__main__':
    app.run()
```

در این مثال، آدرس `/user/<username>` و `/post/<int:post_id>` آدرس‌های پویا هستند. ورودی‌هایی که به این آدرس‌ها ارسال می‌شوند، به صورت پارامترهای متغیر `username` و `post_id` به توابع `show_user_profile` و `show_post` منتقل می‌شوند.

به عنوان مثال، آدرس `/user/john` به تابع `show_user_profile` با پارامتر `username='john'` ارسال می‌شود و آدرس `/post/123` به تابع `show_post` با پارامتر `post_id=123` ارسال می‌شود.
    return f"Post ID: {post_id}"

if __name__ == '__main__':
    app.run()

استفاده از مقدار های فلوت و intiger در url dynamic

```
from flask import Flask

app = Flask(__name__)


@app.route("/user/<int:id>")
def number(id):
    return f'this number is {id}'


@app.route("/user/<float:id>")
def number_float(id):
    return f'this number is float {id}'

if __name__ == "__main__":
    app.run(debug=True)
```
