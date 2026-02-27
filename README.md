# 🎓 Online Learning Platform (OCMS)

A full-stack **Online Course Management System** built with **Django** and **Django REST Framework**. The platform provides a premium, cinematic learning experience with course management, student enrollment tracking, progress monitoring, and a review system — all powered by a RESTful API and a modern glassmorphism-styled frontend.

---

## ✨ Features

- **User Authentication** — Secure JWT-based registration, login, and session management.
- **Course Management** — Hierarchical content structure: **Categories → Courses → Modules → Lectures**.
- **Student Enrollment** — Enroll in courses and track lecture-by-lecture progress.
- **Reviews & Ratings** — Students can rate and review courses they've completed.
- **Analytics Dashboard** — Aggregated system-wide statistics (users, courses, enrollments).
- **Premium Frontend** — Glassmorphism UI with smooth animations, dark mode, and the Outfit font family.
- **Caching** — Redis-backed caching on high-frequency API endpoints for optimal performance.

---

## 🛠️ Tech Stack

| Layer          | Technology                            |
|----------------|---------------------------------------|
| Backend        | Django, Django REST Framework          |
| Database       | PostgreSQL                            |
| Caching        | Redis (via `django-redis`)            |
| Authentication | JWT (`djangorestframework-simplejwt`) |
| Filtering      | `django-filter`                       |
| Frontend       | HTML, Vanilla CSS, JavaScript         |
| Typography     | Google Fonts (Outfit)                 |

---

## 📁 Project Structure

```
ocms/
├── accounts/        # Custom User model, authentication & user API
├── courses/         # Categories, Courses, Modules, Lectures (CRUD)
├── enrollments/     # Student enrollments & lecture progress tracking
├── reviews/         # Course ratings & review system
├── dashboard/       # Analytics & system-wide statistics
├── frontend/        # HTML templates, CSS, and client-side JS
├── ocms/            # Django project settings & root URL config
└── manage.py        # Django management entry point
```

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10+**
- **PostgreSQL** — Create a database named `ocms_db`
- **Redis** — Running on port `6380`

### 1. Clone the Repository

```bash
git clone https://github.com/JohithKumar/online-learning-platform.git
cd online-learning-platform
```

### 2. Create a Virtual Environment

```bash
python -m venv env

# Windows
.\env\Scripts\activate

# macOS / Linux
source env/bin/activate
```

### 3. Install Dependencies

```bash
pip install django djangorestframework django-filter django-redis psycopg2-binary djangorestframework-simplejwt
```

### 4. Apply Database Migrations

```bash
cd ocms
python manage.py makemigrations
python manage.py migrate
```

### 5. Create a Superuser (Admin Access)

```bash
python manage.py createsuperuser
```

### 6. Run the Development Server

```bash
python manage.py runserver
```

The application will be accessible at **http://127.0.0.1:8000/**

---

## 🌐 Application Routes

| Page             | URL                                  |
|------------------|--------------------------------------|
| Landing Page     | `http://127.0.0.1:8000/`             |
| Login            | `http://127.0.0.1:8000/login/`       |
| Register         | `http://127.0.0.1:8000/register/`    |
| Course Library   | `http://127.0.0.1:8000/courses/`     |
| User Profile     | `http://127.0.0.1:8000/profile/`     |
| Reviews          | `http://127.0.0.1:8000/reviews/`     |
| Admin Portal     | `http://127.0.0.1:8000/admin/`       |

---

## 📡 API Endpoints

| Endpoint                  | Method | Description                    |
|---------------------------|--------|--------------------------------|
| `/api/users/`             | GET    | List all users                 |
| `/api/categories/`        | GET    | List course categories         |
| `/api/courses/`           | GET    | List all courses               |
| `/api/modules/`           | GET    | List course modules            |
| `/api/lectures/`          | GET    | List lectures                  |
| `/api/enrollments/`       | GET    | List enrollments               |
| `/api/reviews/`           | GET    | List course reviews            |
| `/analytics/`             | GET    | System analytics dashboard     |
| `/api/token/`             | POST   | Obtain JWT access token        |
| `/api/token/refresh/`     | POST   | Refresh JWT token              |

---

## 🏗️ Architecture Highlights

- **RESTful API** — Function-based views with `@api_view` decorators and `ModelSerializer` for consistent JSON responses.
- **Redis Caching** — `@cache_page(100)` on frequently accessed endpoints to reduce database load.
- **Frontend Integration** — Django `TemplateView` serves HTML pages; the frontend fetches data asynchronously via `fetch()` calls to the API.
- **JWT Security** — `IsAuthenticated` permission enforced on core API views.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
