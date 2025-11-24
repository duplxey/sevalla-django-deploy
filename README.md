# Deploying a Django App to Sevalla

Learn how to deploy a production-ready Django app to Sevalla.

Read the [blog post](https://sevalla.com/blog/deploy-django-app-to-sevalla/).

## How to use?

1. Clone the repository.

2. Create a virtual environment, activate it, and install the requirements:

  ```sh
  $ python3 -m venv venv && source venv/bin/activate
  (venv) $ pip install -r requirements.txt
  ```

3. Copy *.env.example* paste it as *.env* and change it accordingly.

4. Migrate the database & start the development server:

  ```sh
  (venv) $ python manage.py migrate
  (venv) $ python manage.py runserver
  ```

5. Start a Redis instance via Docker (alternatively use a locally installed one):

  ```sh
  (venv) $ docker run -d --name redis -p 6379:6379 redis
  ```

6. Start a Celery worker:

  ```sh
  (venv) $ celery -A core worker --loglevel=INFO --concurrency=1
  ```

7. Navigate to [http://localhost:8000/](http://localhost:8000/) and kick off a few tasks.
