# نصب و به‌روزرسانی Kali Linux و pip در اینترنت محدود ایران

این ریپازیتوری یک راهنمای ساده برای به‌روزرسانی **Kali Linux** و نصب پکیج‌های **Python pip** در شرایط اینترنت محدود ایران است. بسیاری از کاربران هنگام اجرای `apt update` یا نصب پکیج‌های پایتون با سرعت پایین یا خطاهای اتصال به مخازن مواجه می‌شوند. در این راهنما از **mirror های سریع‌تر** برای مخازن Debian و PyPI استفاده می‌شود تا دانلود و نصب پکیج‌ها پایدارتر و سریع‌تر انجام شود.

در این آموزش ابتدا نسخه سیستم بررسی می‌شود و سپس مخازن مناسب برای `apt` تنظیم می‌شوند. بعد از آن یک mirror برای `pip` تنظیم می‌کنیم تا نصب کتابخانه‌های پایتون بدون مشکل انجام شود. این روش برای کاربرانی که در شبکه‌های محدود یا کند کار می‌کنند بسیار کاربردی است.

## تشخیص نسخه سیستم

ابتدا نسخه سیستم را بررسی کنید:

`cat /etc/os-release`

## تنظیم مخازن apt

فایل مخازن را ویرایش کنید:

`sudo nano /etc/apt/sources.list`

محتوای زیر را داخل فایل قرار دهید:

```
deb http://mirror.arvancloud.ir/debian testing main contrib non-free non-free-firmware  
deb http://mirror.arvancloud.ir/debian-security testing-security main contrib non-free non-free-firmware  
deb http://mirror.arvancloud.ir/debian testing-updates main contrib non-free non-free-firmware
```

سپس لیست پکیج‌ها را به‌روزرسانی کنید:

`sudo apt update`

## تنظیم Mirror برای pip

ابتدا پوشه تنظیمات pip را ایجاد کنید:

`mkdir -p ~/.pip`

سپس فایل تنظیمات را باز کنید:

`nano ~/.pip/pip.conf`

محتوای زیر را داخل فایل قرار دهید:
```
[global]  
index-url = https://mirror-pypi.runflare.com/simple  
trusted-host = mirror-pypi.runflare.com  
timeout = 60
```
## نصب یک پکیج پایتون (مثال)

برای تست می‌توانید یک کتابخانه نصب کنید:

`pip install requests`

## نتیجه

اگر مراحل بالا به‌درستی انجام شده باشد، اکنون سیستم شما می‌تواند پکیج‌های **apt** و **pip** را از mirror های سریع‌تر دریافت کند و فرآیند نصب و به‌روزرسانی در اینترنت محدود با مشکل کمتری انجام خواهد شد.
تهیه شده در 26/4/2026 - توسط تیم Acyber.ir

## Test 
```
sudo apt install -y python3-requests python3-bs4 python3-lxml python3-selenium python3-scapy python3-flask python3-django python3-cryptography python3-paramiko python3-numpy python3-pandas python3-matplotlib python3-tqdm python3-colorama python3-rich python3-aiohttp python3-pil python3-yaml python3-urllib3 python3-dateutil python3-psutil python3-click python3-jinja2 python3-bcrypt python3-openssl python3-redis python3-websocket python3-httpx
```
