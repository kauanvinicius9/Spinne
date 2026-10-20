## Spinne Project Documentation

## 1. Overview

**Spinne** is a web application developed in Django (on the backend) focused on managing and cataloging books, authors and publishers. The project has API routes, support for media files (such as book covers) and automated scripts for populating data from CSV files.

---

## 2. Project Structure

```text
Spinne-main/
├── README.md
├── .gitignore
└── backend/
    ├── manage.py
    ├── db.sqlite3
    ├── api/
    │ ├── admin.py
    │ ├── apps.py
    │ ├── filters.py
    │ ├── models.py
    │ ├── serializers.py
    │ ├── tests.py
    │ ├── urls.py
    │ ├── views.py
    │ ├── management/
    │ │ └── commands/
    │ │ ├── population_authors.py
    │ │ ├── population_books.py
    │ │ └── population_publishers.py
    │ ├── migrations/
    │ │ └── 0001_initial.py
    │ └── population/
    │ ├──authors.csv
    │ ├── books.csv
    │ └── publishers.csv
    └── media/
        └── coverpage/
            └── [book covers in .webp format]
```

---

## 3. Main Backend Components

### 3.1. `api` application

Contains the application's central business rule:
- **`models.py`**: Defines the database entities (Books, Authors, Publishers).
- **`serializers.py`**: Maps models to JSON formats used by the API.
- **`views.py` and `urls.py`**: Define the REST endpoints and the request processing logic.
- **`filters.py`**: Allows custom filtering and search on API endpoints.

### 3.2. Population Scripts (`management/commands/`)

Django custom commands to populate the database from CSV files located in `backend/api/population/`:
- `population_authors.py`: Import authors from `authors.csv`.
- `population_books.py`: Imports books from `books.csv`.
- `population_publishers.py`: Imports publishers from `publishers.csv`.

---

## 4. Media Files

The `backend/media/coverpage/` folder stores cover images of popular works in `.webp` format (e.g.: *A Guerra dos Thrones*, *Dom Casmurro*, *Ensaio Sobre a Cegueira*, *Cem Anos de Solitude*, among others).

---

## 5. How to Execute the Project

### Prerequisites

- Python 3.x
- Virtualenv (recommended)

### Step by Step

1. **Access the backend directory:**

   ```bash
   cd Spinne-main/backend
   ```

2. **Install dependencies:**

   *(Make sure to activate your virtual environment and install Django and Django REST Framework)*

3. **Run database migrations:**

   ```bash
   python manage.py migrate
   ```

4. **Populate the database (optional):**

   ```bash
   python manage.py population_publishers
   python manage.py population_authors
   python manage.py population_books
   ```

5. **Start development server:**

   ```bash
   python manage.py runserver
   ```
