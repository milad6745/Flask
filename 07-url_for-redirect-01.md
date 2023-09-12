## Example

```python
from flask import Flask, redirect, url_for

app = Flask(__name__)

@app.route('/')
def index():
    return 'Welcome to my website!'

@app.route('/user/<username>')
def get_user(username):
    if username == "admin":
        return redirect(url_for('admin'))


@app.route('/admin/')
def admin():
    return 'hello admin'


if __name__ == '__main__':
    app.run(debug=True,port=6060)
```
