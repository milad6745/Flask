# Flask

فلسک (Flask) یک چارچوب وب میکرو فریم ورک برای پایتون است که برای ساخت برنامه‌های وب کوچک و متوسط به صورت ساده و انعطاف‌پذیر طراحی شده است. در اینجا یک مقدمه مختصر برای شروع کار با Flask آمده است:

** نصب Flask:**
ابتدا نیاز است Flask را بر روی سیستم خود نصب کنید. این کار به راحتی با استفاده از `pip` انجام می‌شود. اجرای دستور زیر را در ترمینال یا خط فرمان سیستم عامل خود انجام دهید:

```bash
sudo apt update
sudo apt install python3 python3-venv

python -m venv venv # دومی مسیر فایل های محیط مجازیمان است

venv\Scripts\Activate

(venv)pip install Flask
```

** چک کردن پکیج ها **
```bash
(venv) pip freeze   چک میکنیم چه پکیج هایی داخل محیط مجازیمان نصب است
blinker==1.6.2
click==8.1.7
Flask==2.3.2
importlib-metadata==6.8.0
itsdangerous==2.1.2
Jinja2==3.1.2
MarkupSafe==2.1.3
werkzeug==2.3.7
zipp==3.16.2
```

** بهتر است این پکیج ها را در هنگام گار کردن با فلاسک نصب کنیم **

```bash
pip install python-dotenv simplejson watchdog
```
