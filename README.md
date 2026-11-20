# DefeatAcademy

An educational testing platform built with Django by a five-person team at a KSE hackathon (Autumn 2025, top-10 finish). I was the team's tech lead.

Users register, browse courses, take timed multiple-choice tests and track their results on a personal statistics page. Authors can create their own courses, tests and questions.

## Features

- Registration and login (Django auth)
- Courses → tests → questions with multiple-choice answers
- Timed tests with automatic scoring
- Profile page with test history, number of tests taken and average score
- Course, test and question creation for authors
- Bulk import of questions from JSON with a management command

## Tech stack

Python 3.13 · Django 6 · SQLite for local development (PostgreSQL-ready via `dj-database-url`) · HTML templates

## Data model

`Course` → `Test` → `Question` → `Choice`, plus `Result` that links a user to a test with the score, percentage and timestamp.

## Run locally

```bash
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env              # set DJANGO_SECRET_KEY
python manage.py migrate
python manage.py import_tests questions.json   # optional: load sample questions
python manage.py createsuperuser
python manage.py runserver
```

Then open http://127.0.0.1:8000.

## Project structure

```
academy/          courses, tests, results, statistics, JSON import command
users/            registration and auth
defeat_academy/   project settings and URLs
questions.json    sample question set
```
