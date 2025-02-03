# docker-installation-guide-ubuntu-20.04
راهنمای جامع نصب Docker روی Ubuntu 20.04 با چندین روش مختلف و مراحل اجرای نرم‌افزار، شامل اسکریپت خودکار، نصب از مخزن رسمی و نصب با APT.

برای نصب Docker روی Ubuntu 20.04، روش‌های مختلفی وجود دارد که در اینجا به سه روش رایج می‌پردازیم. همچنین بخش اجرای نرم‌افزار Docker را از این مراحل جدا می‌کنم و از ایموجی‌ها برای جذاب‌تر کردن متن استفاده می‌کنم!

### روش 1: نصب با استفاده از مخزن رسمی Docker

این روش، روش رسمی است که به طور مستقیم از مخزن Docker استفاده می‌کند.

#### 1. به‌روزرسانی سیستم 🔄

```bash
sudo apt update
sudo apt upgrade -y
```

#### 2. نصب پیش‌نیازها 🛠

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

#### 3. اضافه کردن کلید GPG و مخزن Docker 🔑

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

#### 4. نصب Docker 🚀

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

#### 5. بررسی وضعیت Docker ✔️

```bash
sudo systemctl status docker
```

---

### روش 2: نصب از مخزن Ubuntu

در این روش، از مخزن رسمی Ubuntu برای نصب Docker استفاده می‌شود. به دلیل قدیمی بودن برخی نسخه‌ها، این روش توصیه نمی‌شود، اما در صورتی که نیاز به نسخه‌ای قدیمی‌تر دارید، مفید است.

#### 1. نصب Docker از مخزن APT 👨‍💻

```bash
sudo apt update
sudo apt install docker.io -y
```

#### 2. بررسی وضعیت Docker 🧐

```bash
sudo systemctl status docker
```

---

### روش 3: نصب با استفاده از اسکریپت خودکار Docker

این روش راحت‌ترین و سریع‌ترین روش است که Docker را با استفاده از یک اسکریپت خودکار نصب می‌کند.

#### 1. دانلود و اجرای اسکریپت نصب خودکار 🌐

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

#### 2. بررسی وضعیت Docker 🔍

```bash
sudo systemctl status docker
```

---

### اجرای نرم‌افزار Docker 🖥

پس از نصب Docker، می‌توانید با استفاده از روش‌های زیر Docker را اجرا کنید.

#### 1. اجرای Docker بدون نیاز به `sudo` ⚡

برای اینکه نیازی به وارد کردن `sudo` در هر دستور نداشته باشید، کافی است کاربر خود را به گروه `docker` اضافه کنید:

```bash
sudo usermod -aG docker $USER
```

سپس از سیستم خارج شوید و دوباره وارد شوید یا سیستم را ریستارت کنید.

#### 2. اجرای کانتینر Docker 🏃‍♂️

حالا برای ساخت و اجرای Docker container از یک Dockerfile، دستورات زیر را وارد کنید:

1. ساخت تصویر Docker 📦

```bash
docker build -t my-node-app .
```

2. اجرای کانتینر Docker 🖱

```bash
docker run -p 3000:3000 my-node-app
```

حالا می‌توانید به `http://localhost:3000` بروید و پیامی که از داخل کانتینر ارسال می‌شود را مشاهده کنید.

---

### منابع رسمی Docker 📚

برای نصب و راهنمایی بیشتر، می‌توانید به مستندات رسمی Docker برای Ubuntu 20.04 مراجعه کنید:

[مستندات نصب Docker برای Ubuntu 20.04](https://docs.docker.com/engine/install/ubuntu/)

### حمایت از پروژه (Donate) 💖

اگر این راهنما مفید بود و خواستید از پروژه حمایت کنید، می‌توانید از لینک زیر برای دونیت استفاده کنید:

[حمایت مالی از پروژه](https://zarinp.al/colonel8002)
