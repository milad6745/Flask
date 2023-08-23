from flask import Flask, redirect, url_for

app = Flask(__name__)

# مسیر اصلی
@app.route('/')
def home():
    return "صفحه اصلی"

# مسیر دیگر
@app.route('/dashboard')
def dashboard():
    return "داشبورد کاربری"

# مسیری که باعث انتقال به داشبورد می‌شود
@app.route('/go_to_dashboard')
def go_to_dashboard():
    # استفاده از تابع redirect و url_for
    return redirect(url_for('dashboard'))

if __name__ == '__main__':
    app.run(debug=True)
