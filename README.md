# rick-and-morty
### Requirements:
- Endpoint, which return random character from the world of Rick and Morty series.
- Endpoint get search_string as an argument and return list of all characters, who contains the search_string in the name.
- On regular basis, app downloads data from external service to inner DB.
- Requests of implemented API should work with local DB (Take data from DB not from Rick & Morty API).
### Technologies to use:
- Public API: https://rickandmortyapi.com/documentation.
- Use Celery as task scheduler for data synchronization for Rick & Morty API.
- Python, Django/Flask/FastAPI, ORM, PostgreSQL, Git.
- All endpoints should be documented via Swagger.
### How to run:
- Create venv: `python -m venv venv`
- Activate it `suorce venv/bin/activate`
- Install requirements:`pip install -r requirements.txt`
- Create new Postgres DB & User
- Copy .env.sample -> .env and populate with all required data
- Run migrations: `python manage.py migrate`
- Run Redis Server: `docker run -d -p 6379:6379 redis`
- Run Celery worker for task handling: `celery -A rick_and_morty_api worker --loglevel=INFO`
- Run Celery beat for task scheduling: `celery -A rick_and_morty_api beat -l INFO --scheduler django_celery_beat.schedulers:DatabaseScheduler`
- Create schedule for running sync in BD
- Run app: `python manage.py runserver`