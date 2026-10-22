<div align="center">

# TaskCore • Django Multi-User Task Orchestration Engine
### *Relational Task Lifecycle Tracking, Session-Isolated CRUD & Django ORM State Management*

[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Framework: Django](https://img.shields.io/badge/Django-4.x%20%7C%205.x-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Database: SQLite](https://img.shields.io/badge/Database-SQLite3_Relational-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org/)
[![Authentication: Session Based](https://img.shields.io/badge/Auth-Django_Session_Isolation-success?style=for-the-badge)](https://docs.djangoproject.com/en/stable/topics/auth/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

<p align="center">
  A production-structured Django web application providing strict user-isolated task management, stateful completion toggles, real-time pending counters, and parameterized search filters.
</p>

</div>

---

## 🚀 Key Architectural Capabilities

- **Strict User Isolation:** Enforces row-level access control so users only read, mutate, and delete their own private task models.
- **Full CRUD Lifecycle:** Clean Django Class-Based Views (`ListView`, `DetailView`, `CreateView`, `UpdateView`, `DeleteView`) implementing the complete task workflow.
- **Search & Filter Pipeline:** Dynamic query filtering by title substring without compromising database pagination.
- **Session-Based Authentication:** Native secure password hashing (PBKDF2/Argon2) and CSRF protection on all forms.

---

## ⚡ Quickstart & Local Setup

```bash
# Clone the repository
git clone https://github.com/ExeDevCentral/proyectopython01.git
cd proyectopython01

# Install requirements
pip install django

# Run database migrations
python3 manage.py migrate

# Start development server
python3 manage.py runserver
```

Access the application in your browser at `http://127.0.0.1:8000/`.

---

## 📂 Repository Structure

```text
proyectopython01/
├── base/                   # Core Django application (models, views, forms, templates)
│   ├── templates/base/     # Authentication and task view templates
│   ├── models.py           # Task relational schema with User foreign key
│   └── views.py            # Generic class-based views for task workflows
├── mi_web/                 # Django project settings and root URL routing
├── manage.py               # Django CLI management entry point
├── .gitignore              # Standard Python and Django exclusions
└── README.md               # Technical documentation
```

---

## 👨‍💻 Author

**Exequiel Echevarria**
- GitHub: [@ExeDevCentral](https://github.com/ExeDevCentral)
