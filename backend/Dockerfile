FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Статика админки копируется в общий volume при старте контейнера
CMD ["sh", "-c", "python manage.py collectstatic --noinput && cp -r /app/collected_static/. /backend_static/static/ && gunicorn --bind 0.0.0.0:8000 kittygram_backend.wsgi"]
