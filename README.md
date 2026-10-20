## Spinne Project Documentation

## Overview

**Spinne** is a web application developed in Django (on the backend) focused on managing and cataloging books, authors and publishers. The project has API routes, support for media files (such as book covers) and automated scripts for populating data from CSV files.

---

## Main Backend Components

### `api` application

Contains the application's central business rule:
- **`models.py`**: Defines the database entities (Books, Authors, Publishers).
- **`serializers.py`**: Maps models to JSON formats used by the API.
- **`views.py` and `urls.py`**: Define the REST endpoints and the request processing logic.
- **`filters.py`**: Allows custom filtering and search on API endpoints.

### Population Scripts (`management/commands/`)

Django custom commands to populate the database from CSV files located in `backend/api/population/`:
- `population_authors.py`: Import authors from `authors.csv`.
- `population_books.py`: Imports books from `books.csv`.
- `population_publishers.py`: Imports publishers from `publishers.csv`.

---

## Media Files

The `backend/media/coverpage/` folder stores cover images of popular works in `.webp` format (e.g.: *A Guerra dos Thrones*, *Dom Casmurro*, *Ensaio Sobre a Cegueira*, *Cem Anos de Solitude*, among others).

---

## How to Execute the Project

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

4. **Populate the database:**

   ```bash
   python manage.py population_publishers
   python manage.py population_authors
   python manage.py population_books
   ```

5. **Start development server:**

   ```bash
   python manage.py runserver
   ```
