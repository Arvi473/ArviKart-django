
# 🛍️ ArviKart – E-Commerce Platform (Django)

ArviKart is a full-featured e-commerce web application built using the **Django Framework**, featuring category-based product listings, cart management, admin panel customization, and AWS deployment support.

---

## 🚀 Project Overview

**Tech Stack**

* **Backend:** Django 3.1+, Python 3.8
* **Database:** PostgreSQL / SQLite (local)
* **Frontend:** HTML, CSS, Bootstrap
* **Server:** AWS Elastic Beanstalk
* **Storage:** AWS S3 for media files
* **Others:** Pillow, Django Admin Honeypot, Python Decouple

**Main Features**

* Category and product management via Django Admin
* Product pagination and filtering by category
* Add-to-cart functionality
* Context processors for dynamic navigation and cart count
* Custom user model and admin interface
* Media & static file management
* Ready for AWS deployment (Elastic Beanstalk + RDS)

---

## ⚙️ Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Arvi473/ArviKart-django.git
cd ArviKart-django
```

### 2️⃣ Create and Activate Virtual Environment

```bash
python -m venv env
source env/Scripts/activate     # on Windows
# or
source env/bin/activate         # on Mac/Linux
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5️⃣ Create Superuser

```bash
python manage.py createsuperuser
```

### 6️⃣ Run Server

```bash
python manage.py runserver
```

Then open:
👉 [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

## 🧩 Key Django Apps

| App Name   | Description                                           |
| ---------- | ----------------------------------------------------- |
| `category` | Manage product categories                             |
| `store`    | Manage product details, pagination, and product pages |
| `accounts` | Custom user authentication and profile                |
| `carts`    | Shopping cart and cart items management               |

---

## 📦 Media and Static Setup

Add the following in `settings.py`:

```python
STATIC_URL = '/static/'
MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'media'
```

Run:

```bash
python manage.py collectstatic
```

---

## 🔐 Security and Best Practices

* Installed `django-admin-honeypot` for fake admin login protection
* Used `python-decouple` for environment variables
* Added `DEFAULT_AUTO_FIELD = 'django.db.models.AutoField'` for Django 4.x compatibility

---

## ☁️ AWS Deployment (Elastic Beanstalk)

1. Create a `.ebextensions/django.config` file:

   ```yaml
   option_settings:
     aws:elasticbeanstalk:container:python:
       WSGIPath: arvikart.wsgi:application
     aws:elasticbeanstalk:environment:proxy:staticfiles:
       /static: static
   ```

2. Initialize and Deploy:

   ```bash
   eb init -p python-3.8 arvikart-app
   eb create arvikart-env
   eb deploy
   ```

3. Add the AWS domain to `ALLOWED_HOSTS` in settings.

---

## 🔧 Future Enhancements

* User registration & profile management
* Product ratings & reviews
* Currency and language support
* Filter by size, color, and price range
* Enhanced security measures

---



