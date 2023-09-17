## http Method
 در وب، متدهای HTTP از جمله GET، POST، PUT و DELETE برای ارتباط بین مرورگر و سرور استفاده می‌شوند. توضیحات مهم مقاله به شرح زیر است:

 **GET Method**:
   - این یکی از متدهای HTTP است که برای دریافت اطلاعات از سرور استفاده می‌شود.
   - در Flask، شما می‌توانید با استفاده از دکوراتور `@app.route` و متد `methods=['GET']` یک مسیر را برای درخواست‌های GET تعریف کنید.
   - مثال:


```python
@app.route('/getdata', methods=['GET'])
def get_data():
return 'This is a GET request.'
```

 **POST Method**:
   - این متد برای ارسال اطلاعات به سرور استفاده می‌شود (مثلاً ارسال فرم‌ها).
   - در Flask، شما می‌توانید با استفاده از دکوراتور `@app.route` و متد `methods=['POST']` یک مسیر را برای درخواست‌های POST تعریف کنید.
   - مثال:
```python
@app.route('/submitdata', methods=['POST'])
def submit_data():
return 'This is a POST request.'
```

 **PUT Method**:
   - این متد برای به روزرسانی اطلاعات موجود در سرور استفاده می‌شود.
   - در Flask، شما می‌توانید با استفاده از دکوراتور `@app.route` و متد `methods=['PUT']` یک مسیر را برای درخواست‌های PUT تعریف کنید.
   - مثال:
```python
@app.route('/updatedata', methods=['PUT'])
def update_data():
return 'This is a PUT request.'
```

 **DELETE Method**:
   - این متد برای حذف اطلاعات از سرور استفاده می‌شود.
   - در Flask، شما می‌توانید با استفاده از دکوراتور `@app.route` و متد `methods=['DELETE']` یک مسیر را برای درخواست‌های DELETE تعریف کنید.
   - مثال:
```python
@app.route('/deletedata', methods=['DELETE'])
def delete_data():
return 'This is a DELETE request.'
```

5. **استفاده از متدهای چندگانه**:
   - در Flask، شما می‌توانید چندین متد را برای یک مسیر مشخص کنید، به عنوان مثال:

```python
@app.route('/multiplemethods', methods=['GET', 'POST'])
def multiple_methods():
if request.method == 'GET':
return 'This is a GET request.'
elif request.method == 'POST':
return 'This is a POST request.'
```

   - در این مثال، این مسیر هر دو متد GET و POST را قبول می‌کند و با توجه به نوع درخواست، پاسخ متناظر را ارسال می‌کند.

این مقاله به شما اطلاعات کلیدی درباره استفاده از متدهای HTTP در فریمورک Flask ارائه می‌دهد. در صورتی که سوال یا درخواست اطلاعات بیشتری دارید، لطفاً بپرسید.


## Example
```python
from flask import Flask, redirect, url_for, request
app = Flask(__name__)

@app.route('/success/<name>')
def success(name):
   return 'welcome %s' % name

@app.route('/login',methods = ['POST', 'GET'])
def login():
   if request.method == 'POST':
      user = request.form['nm']
      return redirect(url_for('success',name = user))
   else:
      user = request.args.get('nm')
      return redirect(url_for('success',name = user))

if __name__ == '__main__':
   app.run(debug = True)
```
