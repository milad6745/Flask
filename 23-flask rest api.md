# Rest api with flask 
یک REST API با استفاده از Flask ا که با دریافت یک شناسه (ID)، نام مربوط به آن شناسه را بازگردانی می‌کند. 
با این حال، برخی اشکالات کوچک در کد وجود دارد. من آن‌ها را بررسی کردم و اصلاحات زیر را انجام دادم:

`method` باید به `methods` تغییر کند.


```python
from flask import Flask, jsonify

app = Flask(__name__)

data = {
    1: "milad",
    2: "Roham",
    3: "ali"
}

@app.route('/<int:id>', methods=['GET'])
def get_name(id):
    if id in data:
        return jsonify({'id': id, 'name': data[id]})
    else:
        return jsonify({'message': 'آیدی مورد نظر یافت نشد'}), 404

if __name__ == '__main__':
    app.run()
```

اکنون این کد باید بدرستی کار کند. برای تست، مطمئن شوید که سرور Flask اجرا شده و به آدرس `http://localhost:5000` متصل شوید. سپس در مرورگر خود به `http://localhost:5000/2` بروید. این باید نام "Roham" را برگرداند.
