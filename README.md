# RecipeShare Flask Starter

A starter Flask backend for a **RecipeShare** project using:

- Flask
- PostgreSQL
- Flask-SQLAlchemy
- Flask-Migrate
- python-dotenv



## Project Structure

```text
recipeshare-flask-starter/
├── app/
│   ├── __init__.py
│   ├── config.py
│   ├── extensions.py
│   ├── models.py
│   └── routes.py
├── .env.example
├── .gitignore
├── README.md
├── requirements.txt
├── run.py
└── seed.py
```

## Features Included

- Flask app factory
- PostgreSQL configuration via environment variables
- SQLAlchemy models for `User` and `Recipe`
- Relationship: one user can have many recipes
- Basic API endpoints:
  - `GET /`
  - `GET /api/recipes`
  - `GET /api/recipes/<id>`
  - `POST /api/recipes`
- Seed script with starter data

## 1. Create and activate a virtual environment

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows PowerShell

```cmd
python -m venv .venv
.venv\Scripts\Activate.bat
```

## 2. Install dependencies

```bash
pip install -r requirements.txt
```

## 3. Create the PostgreSQL database

In PostgreSQL:

```sql
CREATE DATABASE recipeshare;
```

## 4. Set environment variables

Copy `.env.example` to `.env` and update the connection string.

Example:

```env
DATABASE_URL=postgresql://postgres:password@localhost/recipeshare
FLASK_APP=run.py
FLASK_ENV=development
```

## 5. Initialize migrations

```bash
flask db init
flask db migrate -m "Create user and recipe tables"
flask db upgrade
```

## 6. Seed the database

```bash
python seed.py
```

## 7. Run the app

```bash
flask run
```

Or:

```bash
python run.py
```

## Sample Endpoints

### Get all recipes

```http
GET /api/recipes
```

### Get one recipe

```http
GET /api/recipes/1
```

### Create a recipe

```http
POST /api/recipes
Content-Type: application/json
```

Example body:

```json
{
  "title": "Tomato Soup",
  "description": "Simple homemade soup.",
  "instructions": "Cook tomatoes, blend, and simmer.",
  "prep_time": 30,
  "user_id": 1
}
```


