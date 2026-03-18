# MCON 504 — Test 1: RecipeShare API

## Overview

In this test you will complete a partially-implemented Flask REST API for a recipe-sharing application. The models (`User` and `Recipe`) and the database configuration are already provided. **Your job is to implement the TODO items** in two files:

| File | What you need to do |
|---|---|
| `app/services.py` | Implement **five** service functions that interact with the database |
| `app/routes.py` | Implement **three** route handlers that call the service functions |

When you are finished, the API should support **creating**, **reading**, **updating**, and **deleting** recipes.

---

## Project Layout

```text
test-one/
├── app/
│   ├── __init__.py        # App factory (do NOT modify)
│   ├── config.py          # Database configuration (do NOT modify)
│   ├── extensions.py      # SQLAlchemy & Migrate instances (do NOT modify)
│   ├── models.py          # User & Recipe models (do NOT modify)
│   ├── services.py        # ⬅️  TODO – implement service functions here
│   └── routes.py          # ⬅️  TODO – implement route handlers here
├── requirements.txt
├── run.py                 # Entry point
├── seed.py                # Seeds the DB with sample data
└── README.md              # (this file)
```

---

## Setup (do this first)

### 1. Create & activate a virtual environment

### 2. Install dependencies



## Test Instructions

Complete the following steps **in order**.

### Step 1 — Implement the TODOs

Open the two files marked with TODOs and implement every function that contains a `# TODO` comment. Each function has a docstring describing exactly what it should do.

#### `app/services.py` — Service Functions

| Function | Description |
|---|---|
| `get_all_recipes()` | Query all recipes ordered by `created_at` descending and return a list of dicts |
| `get_recipe_by_id(recipe_id)` | Fetch a single recipe by id (404 if not found) and return it as a dict |
| `create_recipe(data)` | Create a new `Recipe` from the data dict, save it, and return the new recipe as a dict |
| `delete_recipe(recipe_id)` | Fetch a recipe by id (404 if not found) and delete it |
| `update_recipe(recipe_id, data)` | Fetch a recipe by id (404 if not found), update the fields present in `data`, save, and return the updated recipe as a dict |

#### `app/routes.py` — Route Handlers

| Route | Method | Description |
|---|---|---|
| `/api/recipes` | `POST` | Parse the JSON body, validate required fields (`title`, `description`, `instructions`, `prep_time`, `user_id`), call `create_recipe()`, and return the result with status **201** |
| `/api/recipes/<id>` | `PUT` | Parse the JSON body, call `update_recipe()`, and return the updated recipe |
| `/api/recipes/<id>` | `DELETE` | Call `delete_recipe()` and return a **204 No Content** response |

> The `GET` routes and the home route are already implemented for you.

### Step 2 — Initialize the database, create a migration, and apply it

Make sure to add migrations to git so they are tracked by version control.


### Step 3 — Seed the database (optional, but recommended for testing)

```bash
python seed.py
```

### Step 4 — Run the server

```bash
flask run
```

or

```bash
python run.py
```



### Step 5 — Test your endpoints

Use **curl**, **Postman**, or any HTTP client to verify each endpoint.

#### Create a recipe (`POST`)

```bash
curl -X POST http://127.0.0.1:5000/api/recipes \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Tomato Soup",
    "description": "Simple homemade soup.",
    "instructions": "Cook tomatoes, blend, and simmer.",
    "prep_time": 30,
    "user_id": 1
  }'
```

Expected: **201 Created** with the new recipe JSON.

#### Update a recipe (`PUT`)

```bash
curl -X PUT http://127.0.0.1:5000/api/recipes/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Updated Tomato Soup",
    "prep_time": 25
  }'
```

Expected: **200 OK** with the updated recipe JSON.

#### Delete a recipe (`DELETE`)

```bash
curl -X DELETE http://127.0.0.1:5000/api/recipes/1
```

Expected: **204 No Content** (empty response body).

---

## Grading Criteria

- All five service functions in `services.py` are correctly implemented.
- All three route handlers in `routes.py` are correctly implemented.
- The database is initialized and migrated without errors.
- `POST`, `PUT`, and `DELETE` requests produce the correct responses.

Good luck!
